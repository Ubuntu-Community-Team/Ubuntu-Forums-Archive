---
title: "Firefox and SWF files"
date: 2014-04-23
forum: Multimedia Software
---

### Post by N1GHTS on 2014-04-23
I installed a fresh installation of **Kubuntu 14.04** a few days ago. One of my problems has been that when I drag an SWF adobe flash file into firefox a download dialog appears instead of playing the flash document. In 13.10 this was not a problem but it seems something has changed in 14.04.

To be clear, I have checked Edit -> Preferences -> Applications -> SWF File and it is currently set to "Use Shockware Flash (in Firefox)". Also I can view SWF files from the web just fine. This includes getting the link location, copying it to the URL bar, and seeing it play correctly from that web location. What Firefox doesn't seem to like is playing an SWF from the local disk. 

I have quite a collection of SWF files which I have downloaded over the years, most of them interactive flash documents which would not be playable on movie players, so I need to find a way to play my flash files on Firefox as I used to be able to do in Kubuntu.

---

### Post by N1GHTS on 2014-04-24
Here is the only way I have been able to get flash files to run on Kubuntu 14.04. **Note that this is just a workaround**.

- Download the Windows Installer for Firefox.
- Install it on Wine
- Install Adobe Flash Player for Windows on Wine
- In KDE, right click on an SWF file -> Open With.. -> other -> Wine / Programs / Mozilla Firefox. Append to the end of the command line at the top **file:///Z:/%U **so that it looks kind of like this:

env WINEPREFIX="/home/username/.wine" wine C:\\windows\\command\\start.exe /Unix /home/username/.wine/dosdevices/c:/users/Public/Start\ Menu/Programs/Mozilla\ Firefox.lnk file:///Z:/%U

If you copy that line, replace "username" with your user name.

Now when I click on an SWF file, Firefox for Windows will play it. The only downside is that it is a little buggy and laggy. I am anxiously waiting for some feedback from someone who could find a solution that involves Firefox for Linux.

---

### Post by monkeybrain20122 on 2014-04-24
If you can rdo that by running Firefox in wine can just use pipelight to install Windows flash in Firefox (linux)
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)
Scroll down to section 2.3

---

### Post by N1GHTS on 2014-04-24
I am aware of Pipelight, but using Adobe Flash via Wine is not exactly a solution, just another workaround. You see Firefox for Linux plays all Flash perfectly well, its just that it doesn't want to play local flash files on disk. It seems like Pipelight would be alot of files installed just to bypass what seems to be a seemlingly simple configuration-style issue. 

I may try this anyways just to see how it behaves, but again its not a solution, especially not an elegant one.

But thank you very much for your suggestion. I highly appreciate it.

---

### Post by monkeybrain20122 on 2014-04-24
Well there is no elegant solution to this problem. :) But the way I see it installing just the flash plugin in wine is simpler and more elegant than installing the whole browser AND the plugin in wine. :) You can always use update-alternatives to switch between native flash and pipelight-flash, so if you don't need pipelight-flash it won't even be loaded.

---

### Post by Niverton on 2014-04-25
Hey, I have the same problem, solved it like this: Adobe provides a standalone player for playing SWF files outside a navigator, you can find it [here (flash player 11, last version for linux)]("http://fpdownload.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_sa.i386.tar.gz"), unfortunately, it's only for i386. If you have a 64 bits system like me, you can download the [Windows version (flash player 13, latest version for Windows at the moment)]("http://download.macromedia.com/pub/flashplayer/updaters/13/flashplayer_13_sa.exe") and run it with Wine. It works perfectly for me, no need to install, but that's not really using Firefox. [Link where I found the downloads]("http://www.adobe.com/support/flashplayer/downloads.html")

---

