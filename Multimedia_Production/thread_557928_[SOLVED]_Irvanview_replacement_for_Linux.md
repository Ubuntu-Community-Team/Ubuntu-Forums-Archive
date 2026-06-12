---
title: "[SOLVED] Irvanview replacement for Linux"
date: 2007-09-23
forum: Multimedia Production
---

### Post by weblordpepe on 2007-09-23
Hiya Guys.

Don't get me wrong - Irfanview runs under Wine. And it is the single-most insanely useful app on the entire planet.

But as far as I can tell, half of the 'good' image viewers in Linux don't support animated GIFs. Or not half the features. Or even be as simple/leet.

Can anyone recommend me a small, fast view which can be used like Irfanview? For example - being only a simple single window? And yes one that supports formats like multiple gif support.

I already emailed Irfan suggesting a native port but dunno if he'll be free to reply to my email.

---

### Post by 505 on 2007-09-23
Have you tried gThumb? It supports animated GIFs.

---

### Post by weblordpepe on 2007-09-23
Holy cow it does too! SOLVED.

---

### Post by videodrome on 2007-09-24
Gthumb is HARDLY a replacement for Irfanview. There is no replacement for Irfanview. In fact, only xnview comes close, and it is closed source and outdated.

The reality is that the lack of a decent lightweight picture editor that can crop, resize, do brightness/contrast and sharpen, etc is a stumblingn block for many to switch over completely to Linux. Same with a decent FTP client; fact is, neither exist.

---

### Post by MSchenker on 2007-11-02
I just wanted to add my voice to this discussion.  I have been using Irfanview for years for simple image work:[LIST]
[*]Cropping
[*]Resizing and resampling
[*]Image conversion
[*]Batch processing
[*]Reviewing image directories[/LIST]I don't see anything in the Linux directories that truly replaces it.  In fact, the absence of Irfanview in Linux is the single reason I cannot switch completely over from Windows to Linux!

One of the best examples of Irfanview's strengths is cropping.  I like the way Irfanview allows me to just select the portion of a photo I want to use, and crop out the rest.  All other programs I have used turn this simple activity into a complicated set of steps.

Anyway, if anyone knows of a true Linux replacement for Irfanview, please let me know!

Thanks,
Matt

---

### Post by weblordpepe on 2007-11-03
Why has it taken like weeks for someon to reply to my thread? I run IrfanView flawlessly in Wine. In fact I even wrote a script which allows you to associate filetypes with Irfanview, and lets you drop files onto Irfanview's icon.
This basically lets you do everything you could do in Windows.

Refer to: [http://ubuntuforums.org/showthread.php?t=565571](http://ubuntuforums.org/showthread.php?t=565571)

---

### Post by MSchenker on 2007-11-03
> **weblordpepe said:**
> Why has it taken like weeks for someon to reply to my thread? I run IrfanView flawlessly in Wine. In fact I even wrote a script which allows you to associate filetypes with Irfanview, and lets you drop files onto Irfanview's icon.
This basically lets you do everything you could do in Windows.

Refer to: [http://ubuntuforums.org/showthread.php?t=565571](http://ubuntuforums.org/showthread.php?t=565571)

I'm glad to hear you got Irfanview running with Wine.  I can't seem to get it working.  I downloaded the iview410_setup.exe installation file from Tucows, and I put it on my desktop.  I right-click on the *.exe file and I see the option "open with Wine windows emulator" but nothing happens.

This is actually my first time using Wine, so maybe I'm doing something wrong.

Thanks for your help,
Matt

---

### Post by weblordpepe on 2007-11-03
What you'll want to do is try running the install file from the terminal:
[LIST]
[*]Open a terminal by clicking the icon under the applications menu, or hit Alt-F2 & type **gnome-terminal**

[*]Switch to the directory where you have the install exe. For example **cd /home/dork/Downloads**

[*]Type **wine** into the terminal, and put a space after it, then the name of the file. E.g. **wine irfanviewinstaller.exe**
[/LIST]

Now if there's any errors or problems, it should spit it out in the terminal. It will either work or tell you why not.

---

### Post by MSchenker on 2007-11-04
weblordpepe,
Thanks for your help.  It really means a lot to someone like me, who is still learning about Linux.

OK, I did what you said.  Here's the transaction that took place in the terminal:
[COLOR=Blue]matthew@Main:~$ cd /home/matthew/Desktop/
matthew@Main:~/Desktop$ wine iview410_setup.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\matthew\
\Desktop\\iview410_setup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\matthew\\Desktop\\iview410_setup.exe" failed, status c0000135
matthew@Main:~/Desktop$
[COLOR=Black]
Does that help?

Thanks,
Matt
[/COLOR][/COLOR]

---

### Post by weblordpepe on 2007-11-04
You're welcome - and yes that helps a lot! 

That error is actually one which you'll find even in Windows. You're missing a DLL file. Specifically the file MFC42.DLL. This is a Windows thing, beleive it or not. Many programs need the file MFC42.DLL and can bark at you if you don't' have the file.

If you've got a Windows installation somewhere, search for the MFC42.DLL file and then copy it to Wine's **windows** folder. I don't know much about the licencing terms implications of doing that. But it's Microsoft so who cares.

Wine's **windows** folder (the virtual one) is hidden in your home folder. It should be **/home/foo/.wine/drive_c/windows** where **foo** is your username. 

If you don't have a Windows installation handy, you can google search for it. I usually get DLL files from the site [http://www.dll-files.com](http://www.dll-files.com)
The download link for MFC42.DLL is [http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42)

---

### Post by disraeli on 2007-11-05
Hey this post makes me wanna go and install Irfanview under Wine asap. Thanks!

---

### Post by weblordpepe on 2007-11-05
:guitar: Heh cheers :D

But don't thank me, thank the Wine dudes!! You can thank me by signing up to the Wine AppDB and adding your experience with Irfanview & other apps.

---

### Post by mjpatey on 2007-11-05
I realize the thread is marked "solved" already, but I wanted to put in my $.02.  My favorite light-weight image editor is Picasa for Linux.

You should know it's not a FOSS program, and it uses its own internal build of Wine to run on Linux.  But the user doesn't have to deal with Wine at any point; it's handled under the hood by the installer and launcher.

The intuitive cropping you mentioned is there, each photo has unlimited undo/redo, and you can even do some more advanced image manipulation (color, white balance, levels/contrast) and apply effects if that's what you want.t.

The only thing you mention that it doesn't do is display animated GIFs.  HTH!

-Mark

---

### Post by MSchenker on 2007-11-05
I give up on trying to install Irfanview on Kubuntu.  I installed GThumb, which is in the repository.  I am happy to report it does everything I need.  Not quite as smooth as Irfanview, but it works for me!
Matt

---

