# View Binding DFM Bug

Sample project demonstrating how you cannot enable view binding on more than one DFM in an app.

Repro:
```
./gradlew assembleDebug
```

Output:
```
* What went wrong:
Execution failed for task ':app:checkDebugLibraries'.
> [:dynamicfeature, :dynamicfeature2] all package the same library [androidx.databinding:viewbinding].
  
  Multiple APKs packaging the same library can cause runtime errors.
  Placing each of the above libraries in its own dynamic feature and adding that
  feature as a dependency of modules requiring it will resolve this issue.
  Libraries that are always used together can be combined into a single feature
  module to be imported by their dependents. If a library is required by all
  feature modules it can be added to the base module instead.
```