# de4dot

A modified version to support .NET 8.0, with updated dependencies and all
deobfuscators removed except for `Unknown` target (the only one EFT targets).

## Build

`dotnet build`

## Deobfuscating `Assembly-CSharp.dll`

1. Drag-drop `Assembly-CSharp.dll` on top of `de4dot.exe`
2. Open `Assembly-CSharp-cleaned.dll` in `DnSpy`
3. Search for `AppDomain.GetData` > Analyze > Used by > GClassXXXX
4. Note down the token of `smethod_0` (example: `0x0601422C`)
5. Run the following (replace PATH-TO-ASM with the path to `Assembly-CSharp.dll` and TOKEN with your token)

```
de4dot.exe --un-name "!^<>[a-z0-9]$&!^<>[a-z0-9]__.*$&![A-Z][A-Z]\$<>.*$&^[a-zA-Z_<{$][a-zA-Z_0-9<>{}$.`-]*$" "PATH-TO-ASM" --strtyp delegate --strtok TOKEN
```

## License

GPLv3 (see LICENSE).
