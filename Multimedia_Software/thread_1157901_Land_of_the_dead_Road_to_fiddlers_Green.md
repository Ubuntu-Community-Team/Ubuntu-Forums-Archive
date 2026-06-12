---
title: "Land of the dead: Road to fiddlers Green"
date: 2009-05-13
forum: Multimedia Software
---

### Post by chipfryer on 2009-05-13
Hi everyone.

I'm trying to load the above game.

There are two folders on this CD.
**Cinematic and Directx9** I cannot find the actual game folder and all are CAB files which I cannot open otherwise.

Silent Hill2 Loaded perfectly and is playable but I cannot find the exe for just the game.

I'm using the latest version ubuntu 9.0.4
Has anyone come across this please and is there a workaround?

Many thanks

---

### Post by LoloftheRings on 2009-05-13
Can you post the content of the autorun.inf file? it often contains the command to run the application.

---

### Post by chipfryer on 2009-05-14
Hi thank yo for the reply.

You know that is really odd? I wondered what was missing? There is no Autorun in either directory but in windows it loads just the same as any other CD. 

Wait a minute! I just looked and had disc 2 in. :o
Many apologies.

Ok but it asks if I want to **install DirectX 9?** I've read a lot about not doing this....

Again el stupido apologizes

---

### Post by chipfryer on 2009-10-21
Been a while I know.

Here is the AutoRun file contents
[autorun]
open=setup.exe
icon=help\dotz.ico

Here is the output from the error screen
(**No idea why it says XP? I run Ubuntu standalone**)


OS: Windows XP 5.1 (Build: 2600)
CPU: AuthenticAMD Unknown processor @ 1810 MHz with 749MB RAM
Video: No Video

Assertion failed: SUCCEEDED(CoCreateInstance( CLSID_ShellLink, NULL, CLSCTX_INPROC_SERVER, IID_IShellLink, (void**)&psl )) [File:USetupDefinitionWindows.cpp] [Line: 232]

History: USetupDefinitionWindows::ProcessExtra <- USetupDefinition::InstallTree <- (ProcessExtra SetupGroupWindows Manifest.GameGroup) <- USetupDefinition::InstallTree <- (ProcessExtra SetupGroupWindows Manifest.Setup) <- USetupDefinition::DoInstallSteps <- WFilerPageInstallProgress::OnCurrent <- WWizardDialog::RefreshPage <- WWizardDialog::Advanced <- WWizardDialog::OnNext <- WButton::InterceptControlCommand <- WWindow::WndProc <- WWindow::StaticProc <- WWindow::WndProc <- WWindow::StaticProc <- WDialog::DoModal <- Setup

---

### Post by chipfryer on 2009-11-05
I upgraded to the new 9.10 yesterday and tried again using wine 1.2 this time it installed.

It runs the opening sequence then dies just as it is about to load the game.

---

