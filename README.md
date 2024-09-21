# Create your custom Powershell prompt in Windows 

## Step 1: Check the current execution policy in Windows Terminal (Admin):

```
Get-ExecutionPolicy -List
```

This will show the execution policy for different scopes (e.g., LocalMachine, CurrentUser, etc.).

## Step 2: Set the Execution Policy for the Current User:

```
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

This command modifies the policy for the current user, allowing scripts created locally (like the profile script) to run without needing to be digitally signed.

## Step 3: In your Windows Terminal (without admin privilege) check whether you have a profile file or not:

```
Test-Path $PROFILE
```

If it returns <b>False</b>, create a profile by running:

```
New-Item -Path $PROFILE -ItemType File -Force
```

## Step 4: Open the profile for editing

```
notepad $PROFILE
```

## Step 5: Add this to the file opened

```
function Prompt {
    $currentDir = Split-Path -Leaf (Get-Location)
    return "(Sparsh) $currentDir > "
}
```

## Step 6: Restart or reopen your powershell.

![Screenshots](<powershell.png>)