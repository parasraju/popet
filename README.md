# popet

popet is a Windows utility that keeps an eye on local AI coding agents (Claude Code, Codex, Cursor) and flags the shell commands they try to run — remote downloads piped into a shell, credential access, obfuscation, and similar patterns. Each command is scored and shown in a small tray UI.

## Status: Maintenance

This is an experimental `v0.1.0`. The project is in **maintenance**: the UI, scoring rules, and installer work, but the live process/command telemetry component is being rebuilt, so detection against real agent activity is a work in progress. Anyone is welcome to try it out — just don't rely on it yet.

## Not open source (for now)

Precompiled Windows binaries only. The source is not public at this time.

## Requirements

- Windows 10/11 x64
- WebView2 runtime (included with Windows 11; on Windows 10 you'll be prompted to install it)

## Try it

1. Download `popet_0.1.0_x64-setup.exe` from the [Releases](https://github.com/parasraju/popet/releases) page and run the installer.
2. Launch popet from the Start menu.

Everything runs locally; nothing is uploaded. Requires the WebView2 runtime; x64 only for now.

### Optional background service (live telemetry)

For live agent detection the app talks to a background service, `popet-sentinel-service-x64.exe` (also in Releases). From an elevated (Administrator) prompt:

```
popet-sentinel-service-x64.exe install
```

The service is installed to run at startup and must run as LocalSystem to use ETW.