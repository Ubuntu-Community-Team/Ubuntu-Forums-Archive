---
title: "America's Army Problem"
date: 2009-07-28
forum: Multimedia Software
---

### Post by VirginLinux on 2009-07-28
So I installed America's Army.
And I run it. Watermark, then the screen shuts off, and I see "Input not supported" floating around my screen. 
I move the mouse, and I hear background music, and a clicking sound as if I were hovering over something. Eventually I click on the right 'click' and manage to exit back to my desktop. When I run it in console, I get this:

$ sudo armyops
[sudo] password for dalton: 
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change

When I exit, it displays a new window that says:

/usr/bin/xterm: Can't execvp links: No such file or directory

and that's it.
It used to say

Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

but I fixed that with a copy and paste lib file idea. 

Other than that, I'm clueless. I changed my resolutions and the refresh rate on my monitors, to no avail.

Not really expecting an answer, considering this is third time I've posted, and yet I have never had a response. I'm going to keep looking.

---

### Post by igorzwx on 2009-07-28
have you read this:
**[AmericasArmy - Community *Ubuntu* Documentation]("https://help.ubuntu.com/community/AmericasArmy")**

27 Jun 2008 **...** *America's Army* is a First Person Shooter (commonly called FPS) created by **...** If *Americas Army* is already installed, an upgrade match may be **...**
[https://help](https://help).**ubuntu**.com/community/**AmericasArmy** - [Cached]("http://209.85.135.132/search?q=cache:2Hb4ixd8GngJ:https://help.ubuntu.com/community/AmericasArmy+ubuntu+America%27s+Army+howto&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:https://help.ubuntu.com/community/AmericasArmy")

---

### Post by VirginLinux on 2009-07-28
Yes, I have. that just tells me how to install and run the file. I can do that, that's how I know there's errors. lol

=/

---

### Post by igorzwx on 2009-07-28
[B]do you mean this patch or what?
[/B]

**Patch**

 If Americas Army is already installed, an upgrade match may be available from [FileFront]("http://americasarmy.filefront.com/files/Americas_Army/Official_Releases/Patches;949"). Download armyops-lnx-patch-<version>.run. 
 
**Installation**

 Run the file from where you have downloaded 
sudo sh ./armyops-lnx-patch-<version>.run

---

### Post by igorzwx on 2009-07-28
Why do you run it with sudo?

---

### Post by VirginLinux on 2009-07-28
I have the new one, and sudo is force of habit. When I don't run it sudo, I get the same errors. Idk. 
And I have the newest patch, I believe.

---

