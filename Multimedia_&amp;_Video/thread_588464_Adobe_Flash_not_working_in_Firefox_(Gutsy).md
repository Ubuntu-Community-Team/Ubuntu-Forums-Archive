---
title: "Adobe Flash not working in Firefox (Gutsy)"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by kOna on 2007-10-23
Hi guys (and gals)

I have just gave Ubuntu another go and so far so good except one small problem, Adobe Flash (Youtube, etc) doesn't work! I have it installed, and even Firefox says it is installed but Youtube is telling me I don't have it installed, can anyone shed some light on this?

Cheers,

Kona.

---

### Post by breakk on 2007-10-24
Yeah,  I got the same problem. I tried reinstaling all flash packages, even firefox, but nothing helps. Strange is, that in Opera everything is working perfectly. Problems started after upgrading to 7.10.

---

### Post by Marc Hoffman on 2007-10-24
I have the same problem, Opera is all good but not firefox and flock - could it be because Adobe and Gnash are conflicting with each other?

The flash player shows but the controls are all squiffy and then it turns grey.

---

### Post by n1ppon on 2007-10-24
I've got the same problem with Firefox and Flash, got picture but no sound ...

---

### Post by kOna on 2007-10-24
Cheers for the replies, I have managed to fix the problem. What I done was:

Uninstall Adobe Flash / Gnash (make sure both are uninstalled) through Synaptic
Go to Youtube.com and try to view a video, when you get the prompt to get the add-on, select Adobe Flash and run the installer through Firefox.
Restart Firefox

Hopefully this works for the rest of you. Let me know.

Cheers,

Craig

---

### Post by Marc Hoffman on 2007-10-24
It would appear Gnash is not quite ready to replaye Adobe player yet as far as Firefox is concerned.

---

### Post by Endolith on 2007-10-27
> **kOna said:**
> Uninstall Adobe Flash / Gnash (make sure both are uninstalled) through Synaptic
Go to Youtube.com and try to view a video,

I did this, but the video still plays.

When I go to about:plugins, it says:

> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


So Flash 7 is still installed somehow?  And was overriding Flash 9, which is why it kept saying to upgrade?

---

### Post by Endolith on 2007-10-27
> **kOna said:**
> Uninstall Adobe Flash / Gnash (make sure both are uninstalled) through Synaptic
Go to Youtube.com and try to view a video,

I did this, but the video still plays.

When I go to about:plugins, it says:

> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


So Flash 7 is still installed somehow?  And was overriding Flash 9, which is why it kept saying to upgrade?

Edit: 

I fixed it by: 

1. Removing flashplugin-nonfree completely
2. Remove libflashplayer.so and flashplayer.xpt from ~/.mozilla/plugins
3. Reinstalling flashplugin-nonfree

---

### Post by amirmah on 2007-12-06
It still doesnt work with me ... I couldnt even find a flashplayer.xpt file in my mozilla folder ... I completely removed gnash and flash non free the reinstalled flash alone, but firefox still behaves as if flash isnt installed, and when I try to install it from FF, it says it's already installed! this is crappy ... I love gusty and this is just ruining the experience ...

---

### Post by wolfen69 on 2007-12-06
go here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)  download the tar.gz file. unpack it.
then do in terminal:
```
sudo nautilus /usr/lib/firefox/plugins
```
place the libflashplayer.so file that was unpacked into the plugins folder.

---

### Post by Luis-for-um33 on 2007-12-09
I have been trying to view the dishnetwork website and all of it needs the Flash Player.

I downloaded version 9 of the player (install_flash_player_9_linux.tar.gz) and managed to unzip it. Only one file shows on the desktop: "install_flash_player_9_linux".

I have gone through "Applications>Add/Remove" and through the Synaptic Package Manager to no avail. I have also used the Terminal; no go either.

I'm not a techie and, really, I don't know what I'm doing.

I can understand that security matters a lot in Linux; but why is it so hard to install a plugin???

If anybody has a simple answer, please, let me know.

Luis

---

### Post by daradib on 2007-12-09
See [http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

---

### Post by rlsimpso on 2007-12-27
> **wolfen69 said:**
> go here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)  download the tar.gz file. unpack it.
then do in terminal:
```
sudo nautilus /usr/lib/firefox/plugins
```
place the libflashplayer.so file that was unpacked into the plugins folder.

This worked for me on xubuntu 7.10 for i386.

Don't both with the installer that is in the gzip file, just type "sudo cp libflashplayer.so /usr/lib/firefox/plugins/" in a terminal window.

Thanks

---

### Post by alexebird on 2007-12-28
> **wolfen69 said:**
> go here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)  download the tar.gz file. unpack it.
then do in terminal:
```
sudo nautilus /usr/lib/firefox/plugins
```
place the libflashplayer.so file that was unpacked into the plugins folder.

This also worked for me in Ubuntu 7.10.

---

### Post by Justin2 on 2008-01-08
Ignore my previous message. I managed to fix my Flash plugin by manually installing the Adobe Flash package from their website.

---

### Post by isparkes on 2008-01-08
I tried all of the other things (uninstall and reinstall all packages, play around with the settings, install via firefox extensions etc). It might not be the only way, but it worked for me.

In the end, the thing that worked for me was to download and install manually the flash plug in from the Adobe site.

Go to: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)  and download the tar.gz file. I downloaded to the desktop.

Open a terminal and install it. Here's what I did (my contributions in bold):

ian@ian-laptop:~/Desktop$ **tar xvfz install_flash_player_9_linux.tar.gz**
install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
ian@ian-laptop:~/Desktop$ **cd install_flash_player_9_linux/**
ian@ian-laptop:~/Desktop/install_flash_player_9_linux$ **sudo ./flashplayer-installer** 
[sudo] password for ian:

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 
**/usr/lib/firefox**


----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Browser installation directory = /usr/lib/firefox

Proceed with the installation? (y/n/q): **y**

Installation complete.


Perform another installation? (y/n): **n**


Please log out of this session and log in for the changes to take effect.


The Adobe Flash Player installation is complete.

---

### Post by azbarcea on 2008-01-08
follow this updated thread: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

[Kilz]("http://ubuntuforums.org/member.php?u=78588") made a great job ... and his script should install Flash flawlessly

---

