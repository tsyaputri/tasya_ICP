error:
tasya@WINDOWS-D1B0MV3:~/icp_bootcamp$ dfx deploy
Deploying all canisters.
Created a wallet canister on the "local" network for user "default" with ID "uqqxf-5h777-77774-qaaaa-cai"
icp_bootcamp_backend canister created with canister id: uxrrr-q7777-77774-qaaaq-cai
icp_bootcamp_frontend canister created with canister id: u6s2n-gx777-77774-qaaba-cai
Building canister 'icp_bootcamp_backend'.
Building canister 'icp_bootcamp_frontend'.
Error: Failed while trying to deploy canisters.
Caused by: Failed to build all canisters.
Caused by: Failed while trying to build all canisters.
Caused by: The post-build step failed for canister 'u6s2n-gx777-77774-qaaba-cai' (icp_bootcamp_frontend)
Caused by: Failed to build frontend for network 'local'.
Caused by: The command 'cd "/home/tasya/icp_bootcamp" && CANISTER_CANDID_PATH="/home/tasya/icp_bootcamp/.dfx/local/canisters/icp_bootcamp_frontend/assetstorage.did" CANISTER_CANDID_PATH_ICP_BOOTCAMP_BACKEND="/home/tasya/icp_bootcamp/.dfx/local/canisters/icp_bootcamp_backend/icp_bootcamp_backend.did" CANISTER_ID="u6s2n-gx777-77774-qaaba-cai" CANISTER_ID_ICP_BOOTCAMP_BACKEND="uxrrr-q7777-77774-qaaaq-cai" CANISTER_ID_ICP_BOOTCAMP_FRONTEND="u6s2n-gx777-77774-qaaba-cai" DFX_NETWORK="local" DFX_VERSION="0.26.1" "npm" "run" "build" "--workspace" "icp_bootcamp_frontend"' failed with exit status 'exit status: 1'.
Stdout:

> icp_bootcamp_frontend@0.0.0 prebuild
> dfx generate


Stderr:
<3>WSL (10 - Relay) ERROR: CreateProcessParseCommon:863: Failed to translate \\wsl.localhost\Ubuntu\home\tasya\icp_bootcamp\src\icp_bootcamp_frontend
<3>WSL (10 - Relay) ERROR: UtilTranslatePathList:2878: Failed to translate \\wsl.localhost\Ubuntu\home\tasya\icp_bootcamp\src\icp_bootcamp_frontend\node_modules\.bin
<3>WSL (10 - Relay) ERROR: UtilTranslatePathList:2878: Failed to translate \\wsl.localhost\Ubuntu\home\tasya\icp_bootcamp\src\node_modules\.bin
<3>WSL (10 - Relay) ERROR: UtilTranslatePathList:2878: Failed to translate \\wsl.localhost\Ubuntu\home\tasya\icp_bootcamp\node_modules\.bin
<3>WSL (10 - Relay) ERROR: UtilTranslatePathList:2878: Failed to translate \\wsl.localhost\Ubuntu\home\tasya\node_modules\.bin
<3>WSL (10 - Relay) ERROR: UtilTranslatePathList:2878: Failed to translate \\wsl.localhost\Ubuntu\home\node_modules\.bin
<3>WSL (10 - Relay) ERROR: UtilTranslatePathList:2878: Failed to translate \\wsl.localhost\Ubuntu\node_modules\.bin
<3>WSL (10 - Relay) ERROR: CreateProcessCommon:640: execvpe(/bin/bash) failed: No such file or directory
npm error Lifecycle script `build` failed with error:
npm error code 1
npm error path \\wsl.localhost\Ubuntu\home\tasya\icp_bootcamp\src\icp_bootcamp_frontend
npm error workspace icp_bootcamp_frontend@0.0.0
npm error location \\wsl.localhost\Ubuntu\home\tasya\icp_bootcamp\src\icp_bootcamp_frontend
npm error command failed
npm error command bash -c dfx generate


# `icp_bootcamp`

Welcome to your new `icp_bootcamp` project and to the Internet Computer development community. By default, creating a new project adds this README and some template files to your project directory. You can edit these template files to customize your project and to include your own code to speed up the development cycle.

To get started, you might want to explore the project directory structure and the default configuration file. Working with this project in your development environment will not affect any production deployment or identity tokens.

To learn more before you start working with `icp_bootcamp`, see the following documentation available online:

- [Quick Start](https://internetcomputer.org/docs/current/developer-docs/setup/deploy-locally)
- [SDK Developer Tools](https://internetcomputer.org/docs/current/developer-docs/setup/install)
- [Motoko Programming Language Guide](https://internetcomputer.org/docs/current/motoko/main/motoko)
- [Motoko Language Quick Reference](https://internetcomputer.org/docs/current/motoko/main/language-manual)

If you want to start working on your project right away, you might want to try the following commands:

```bash
cd icp_bootcamp/
dfx help
dfx canister --help
```

## Running the project locally

If you want to test your project locally, you can use the following commands:

```bash
# Starts the replica, running in the background
dfx start --background

# Deploys your canisters to the replica and generates your candid interface
dfx deploy
```

Once the job completes, your application will be available at `http://localhost:4943?canisterId={asset_canister_id}`.

If you have made changes to your backend canister, you can generate a new candid interface with

```bash
npm run generate
```

at any time. This is recommended before starting the frontend development server, and will be run automatically any time you run `dfx deploy`.

If you are making frontend changes, you can start a development server with

```bash
npm start
```

Which will start a server at `http://localhost:8080`, proxying API requests to the replica at port 4943.

### Note on frontend environment variables

If you are hosting frontend code somewhere without using DFX, you may need to make one of the following adjustments to ensure your project does not fetch the root key in production:

- set`DFX_NETWORK` to `ic` if you are using Webpack
- use your own preferred method to replace `process.env.DFX_NETWORK` in the autogenerated declarations
  - Setting `canisters -> {asset_canister_id} -> declarations -> env_override to a string` in `dfx.json` will replace `process.env.DFX_NETWORK` with the string in the autogenerated declarations
- Write your own `createActor` constructor
