### Expected Behaviour
I expect that cargo will compile dependencies of the currently tested crate so that code that is only compiled during
dependencies is available to the dependent crate.

### Observed behaviour
Cargo does not compile code annotated with `cfg(test)` when running a dependent crates tests.

### Recreation
To make this error occur, run `cargo test` and the error will be produced.

Notes: 
 - The rust toolchain needs to be installed.
 - This was created with the "rustc 1.87.0-nightly (78948ac25 2025-03-20)" & "cargo 1.87.0-nightly (6cf826701 2025-03-14)" toolchain versions.

### Helping Remarks
The `conditional` crate contains the conditionally compiled data structure, with the `test_crate` crate having a unit test
trying to use this conditionally compiled code.
