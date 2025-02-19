---
description: Cmdlet Singular Noun
ms.custom: PSSA v1.22.0
ms.date: 06/28/2023
ms.topic: reference
title: UseSingularNouns
---
# UseSingularNouns

**Severity Level: Warning**

## Description

PowerShell team best practices state cmdlets should use singular nouns and not plurals.

Suppression allows to suppress just specific function names, for example

```
function Get-Elements {
    [System.Diagnostics.CodeAnalysis.SuppressMessageAttribute('PSUseSingularNouns', 'Get-Elements')]
    Param()
}
```

## Configuration

```powershell
Rules = @{
    UseSingularNouns = @{
        NounAllowList    = 'Data', 'Windows', 'Foos'
        Enable           = $true
    }
}
```

### Parameters

#### `UseSingularNouns: string[]` (Default value is `{'Data', 'Windows'}`)

Commands to be excluded from this rule. `Data` and `Windows` are common false positives and are excluded by default

#### Enable: `bool` (Default value is `$true`)

Enable or disable the rule during ScriptAnalyzer invocation.

## How

Change plurals to singular.

## Example

### Wrong

```powershell
function Get-Files
{
    ...
}
```

### Correct

```powershell
function Get-File
{
    ...
}
```
