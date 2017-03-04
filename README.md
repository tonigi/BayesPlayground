# InferNetPlayground
Test sandbox

```fsharp
I=/Users/toni/Apps/infer.net/Bin
fsharpi /r:$I/Infer.Runtime.dll /r:$I/Infer.Compiler.dll /r:$I/Infer.FSharp.dll 

open System
open MicrosoftResearch.Infer
open MicrosoftResearch.Infer.Models
open MicrosoftResearch.Infer.Distributions
open MicrosoftResearch.Infer.Factors
open MicrosoftResearch.Infer.FSharp
;;

let a=Variable.Bernoulli(0.5);;     
let b=Variable.Bernoulli(0.5);;     

let ie=InferenceEngine();;
let o=ie.Infer(a &&& b);;



let g1=Variable.GaussianFromMeanAndVariance(0.0,1.0);;
let g2=Variable.GaussianFromMeanAndVariance(0.0,1.0);;

let ieg=InferenceEngine(GibbsSampling());; 
let o=ieg.Infer<seq<double>>(g1*g2,QueryTypes.Samples);;  
Seq.iter (printfn "%A") o;;            

```
