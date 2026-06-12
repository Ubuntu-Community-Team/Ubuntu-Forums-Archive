---
title: "Want to run RipIt4Me? Here's how..."
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by Trespasser on 2007-01-03
At least I hope so.

If you're one of the few who's distro runs RipIt4Me under Wine with no issues then count yourself lucky. There have been quite a few who have received the "Failed to Copy" and "No DVD" message when clicking either Wizard Mode or 1-Click Mode. Hopefully, that's a thing of the past.

I've tried this info on three different distros (Ubuntu Edgy...a debian based distro, Blag 59999.22224...a Fedora based distro, and VectorLinux 5.8 Standard Gold...a Slackware based distro) with the latest Wine version available and it worked every time.

First of all, follow Miss Marple's guide on how to set up Wine and install DVD Shrink, DVD Decrypter, RipIt4Me Installer, and mfc42.dll... found here:
[http://forum.digital-digest.com/showthread.php?t=74727](http://forum.digital-digest.com/showthread.php?t=74727)

Ok, after all that is done...open up Text Editor and type "Welcome to RipIt4Me". Now click save and title it as "RipIt4Me". Now right click in an open space (either in Desktop or /home/user) and select Create Folder and name that folder "TempIFOs" (it has to be named exactly that or it will not work!). Now move your RipIt4Me text file into the TempIFOs folder you just created. The last thing I want you to do is copy and paste this TempIFOs folder into /home/your-user-name/.wine/drive_c/windows/temp folder. And you're done.

*You can download a copy of my TempIFOs folder at the bottom of this post. Just unzip and save it to /home/your-user-name/.wine/drive_c/windows/temp folder.

No this is not a joke. It actually works...at least for me...and hopefully for you. I discovered this bit of information quite by accident. It seems that TempIFOs folder needs to exist (at least for some distros), with a file inside of it...hence the RipIt4Me text file (shameless promotion of RipIt4Me on my part...Ha!), before RipIt4Me can detect the DVD properly. This could be due to a flaw in a given distro, a flaw in a given distro's Wine version, or RipIt4Me (at least with reference to Linux). Who knows...who cares...but this fixed it for me.

Hope it works for you, and good luck.

---

### Post by Trespasser on 2007-01-03
BTW, post if it works for you for it might encourage someone else to try this method. My other thread on RipIt4Me has its usefulness but this method should work for everyone without using an older version of Wine. Again, at least I hope so.

Thanks.

---

### Post by PilotJLR on 2007-01-06
Thanks! This works well for me, even using the current .22 version of Wine on Edgy.
Good find!

May I also suggest establishing this file / folder by pasting the following into a terminal:
```

cd ~/.wine/drive_c/windows/temp && mkdir TempIFOs && echo "Welcome to RipIt4Me" > TempIFOs/RipIt4Me

```

---

### Post by Trespasser on 2007-01-07
Thanks, PilotJLR. That little bit of code of yours worked like a charm. It's a whole lot more simple than my method and works just as well. Again, thanks. :).

---

### Post by MetalMusicAddict on 2007-01-07
Along these sames lines I wonder if I could get all of Gordian Knot running in WINE. :-k Its about the only reason I use XP still.

---

### Post by lime4x4 on 2007-01-08
what is the correct syntax to start this app?? It never installed a desktop icon

---

### Post by PilotJLR on 2007-01-08
Just navigate to the installed directory (such as ~/.wine/drive_c/Program Files/RipIt4Me) and run it:
```

wine RipIt4Me.exe

```

---

### Post by Trespasser on 2007-01-09
Or, on Desktop, right click in an open space...go down to Create Launcher...name it RipIt4Me...in the Command line copy and paste this...

wine "c:/Program Files/RipIt4Me/RipIt4Me.exe"

...choose an icon...and click OK.

---

### Post by fsman on 2007-01-30
anyone managed to add a menu item for ripit4me. Mine doesn't run.

---

### Post by PapaWiskas on 2007-02-18
I have followed this guide to the exact "T", and no dice, it does not work.

It opens Ripit4me, but when I click on the one click wizard button, it disappears and dvd decrypter does not ever open.

Can anyone help, for instance I put those .dlls in the system32 folder, but that is all I did.  How do you actually install them.  I used the libraries tab in winecfg and set them to windows native only.

Anything else I am missing?

---

### Post by goonies on 2007-04-24
I get the same problem, can someone please help us

---

### Post by calraith on 2007-05-07
It seems that mfc42.dll offered by [www.driverfiles.net](www.driverfiles.net) (first returned result from Google) must be an older version.  I tried using it, no dice.  So I grabbed an mfc42.dll from a Windows XP SP2 installation, and Ripit4Me works now.  For what it's worth, the version of mfc42.dll I'm using is 6.2.4131.  I also set RipIt4Me.exe in a Windows 2000 environment using winecfg, but I don't know whether that was necessary or not.  DVD Decrypter is still in an NT4 environment.

I had also tried mfc42.dll from Vista, to no avail.  With the current version of Wine it looks like your best bet is to get the DLL from a WinXP SP2 installation.  (You could probably also download SP2 in its entirety from Microsoft and extract its contents to get the DLL, but a 250 meg download just to get a one meg DLL is a pain in the butt.)  Also, for what it's worth, [www.filesearching.com](www.filesearching.com) is a good place to find multiple versions of the same DLL.  If one doesn't work, try downloading another with a different byte size.  I strongly suggest that you pass whatever you download from there through ClamAV or your virus scanner of choice, though, since the site is basically just a search engine for Russian FTP sites, and shouldn't be blindly trusted.

---

### Post by wild77 on 2007-06-05
Anyone interested in a guide on running Ripit4Me using Wine can find it here

[http://forum.doom9.org/showthread.php?p=948220#post948220](http://forum.doom9.org/showthread.php?p=948220#post948220)

Or here with screenshots
[http://forums.afterdawn.com/thread_view.cfm/478357](http://forums.afterdawn.com/thread_view.cfm/478357)

Ripit4Me still has worked on every DVD i have tried, so it's not dead.

I have been working on DVDfabHDDecrypter under Wine no luck as of yet.

---

