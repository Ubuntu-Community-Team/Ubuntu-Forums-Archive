---
title: "[SOLVED] Youtube videos not playing automatically"
date: 2008-12-14
forum: Multimedia Software
---

### Post by sahil01 on 2008-12-14
When I open a page with a youtube video on it, I am not able to play the video automatically. There is a Play icon which I need to click on in order to play the video. I have installed the latest flash player Adobe Flash Player version 10.0.12.36. Please help. Thanks.

---

### Post by frankleeee on 2008-12-14
Are you using a blocker of flash or java.

---

### Post by ralanyo on 2008-12-14
I have the same problem. Is there a fix? Any help would be appreciated.
[:p]("http://www.weblearners.com/excel-training-albany.html")

---

### Post by frankleeee on 2008-12-14
Have you installed all of the media stuff listed in this thread, it sounds like your ether blocking flash or java or need a java install which is part of these downloads.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by sahil01 on 2008-12-15
I am not aware if I am using any blocker of Flash or Java. But when I go to Mozilla->Tools->Add-ons->Plugins , I see that Shockwave Flash 9.0 r100 has been enabled. When I disable it, none of the youtube video will play and I am being asked to get the lastest flash player to play the video. I have downloaded the player from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) , the .deb file for Ubuntu 8.04. I also notice that disabling shockwave flash causes some of the videos on the other website, where the same problem was occouring,to play perfectly.

---

### Post by frankleeee on 2008-12-15
You should look at the link I posted and see if your missing something that is where you will get the answers.

---

### Post by sahil01 on 2008-12-15
I tried the video streaming instructions on the website [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683). The problem still persists.

---

### Post by frankleeee on 2008-12-15
What add-ons do you have running in firefox, I assume that is what browser your using, and do you have java enabled in FF preferences. I am wondering why if you carefully just followed the instructions in that link you should be good to go. The problem your having could be in several areas, but the installs should fix all that. Personally I do it differently by a little bit I just install ubuntu restricted extras, all the gstreamer stuff, and vlc in add remove. but to get to these you have to tick the drop-down on all available applications.

---

### Post by sahil01 on 2008-12-15
I have Java enabled in Firefox preferences. 
Add ons that are enabled in Firefox are:
1. Default Plugin
2. Demo print plugin for unix/linux
3. DivX Web player
4. Helix DNA Plugin:Realplayer G2 Pug in compatible (compatible;Totem)
5. iTunes application detector
6. Quicktime Plug-in 7.2.0
7. Shockwave flash
8.Totem web browser plugin
9. VLC multimedia plugin (compatible totem 2.22.1)
10. windows media player plugin-10 (compatible; totem)

---

### Post by frankleeee on 2008-12-15
What your showing is the plugins, but I notice no java do you have java 6.0 or ubuntu restricted extras installed in add remove I think the extras installs the java. If this doesn't work tell me what exstentions your using in the FF add ons.

---

### Post by gandaran on 2008-12-15
> **sahil01 said:**
> When I open a page with a youtube video on it, I am not able to play the video automatically. There is a Play icon which I need to click on in order to play the video. I have installed the latest flash player Adobe Flash Player version 10.0.12.36. Please help. Thanks.
you may have adobe flash installed, but it's not adobe flash firefox is using for flash, it's swfdec flash!, you have to remove every other flash packages you installed like swfdec, gnash, libflash or adobe flash 9 and just keep adobe flash 10 so firefox can use it

---

### Post by sahil01 on 2008-12-15
I removed the swflash ( from System-> Administration-> Synaptic package manager ). All videos work fine ! Thanks for the help !

---

