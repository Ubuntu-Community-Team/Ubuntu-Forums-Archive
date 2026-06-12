---
title: "Rhapsody Will Not Install"
date: 2008-04-29
forum: Multimedia Software
---

### Post by Eidolons on 2008-04-29
I subscribe to Rhapsody's streaming music service.  I am trying to download their applet player.  It worked fine on earlier versions of Ubuntu that I had.  I tried now on Ubuntu 8.04 using Firefox and I get this message after it loads:

[COLOR="Red"]"Firefox could not install this item because "install-suc..rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem."
[/COLOR]
I click 'Ok' then another message comes up:
[COLOR="Red"]
"Firefox could not install the file at 
[http://forms.real.com/real/player/download.html?f=unix/rhapx/RhapsodyPlayerEngine_Inst_Linux.xpi](http://forms.real.com/real/player/download.html?f=unix/rhapx/RhapsodyPlayerEngine_Inst_Linux.xpi)

because: Unexpected installation error
Review the Error Console log for more details.
-203"[/COLOR]

I can post the error log if it is needed.

---

### Post by natrixgli on 2008-04-29
That error is pretty vendor specific, it's not gonna be easy and/or possible to diagnose.

I would do as it suggests, contact Real. Have you tried using FireFox2? 

Maybe since FF3 is beta still, Real hasn't gotten around to supporting it yet. 

Cheers,

-n8

---

### Post by Eidolons on 2008-04-29
Aha.  I didn't realize I was using Firefox 3.  Thanks, you're a trove.

---

### Post by Eidolons on 2008-04-30
I switched to Firefox 2.  I tried to install Rhapsody and now I get this message:

[COLOR="Red"]"Insufficient disk space. Error code: -235."
[/COLOR]
I click 'Ok" then it gives me another message:
[COLOR="Red"]"Firefox could not install the file at

[http://forms.real.com/real/player/download.html?f=unix/rhapx/RhapsodyPlayerEngine_Inst_Linux.xpi](http://forms.real.com/real/player/download.html?f=unix/rhapx/RhapsodyPlayerEngine_Inst_Linux.xpi)

because: Out of space
-235"[/COLOR]

---

### Post by Eidolons on 2008-04-30
Nevermind.  I figured out the problem.  Rhapsody was trying to install into a directory that didn't exist and instead of saying that it said that there was no space.  I have it installed and am listening to music now.  Thanks for the help.

---

### Post by qiepenguin on 2008-05-10
Hi Eidolons,

Where was the directory it was trying to install to?  I'm having the same problem.  I assume you just added the correct directory to fix it?

David

---

### Post by WildWillie on 2008-05-17
Hey Eidolons, I'm also on 8.04, can you write exactly what you did to fix the problem?

There was a guy on the Rhapsody forums who said he just copied the working plugins over from an older ubuntu system, but I only have the one system. He was also complaining about crashes though, so if everything's working fine for you, I'd much rather try your solution.

---

### Post by HappyUser123 on 2008-05-18
Eidolons: I'd also like to know how you fixed the "out of space" problem. Even better I'd love to know how you figured it out (what log you looked in, etc). I looked through the Firefox error console and nothing jumped out at me.

---

### Post by rainwalker on 2008-05-19
This is how the problem was reported solved on the Real forums:
> Fortunately this problem is just with the installer - if you copy nprhapengine.so to ~/.mozilla/plugins/ it should work fine. 
and
> Simply get the XPI to your 8.04 desktop, unarchive it. Copy the .so to /usr/lib/firefox-addons/plugins, and restart Firefox 3.x
However, this requires that you have access to those files, like on a Gutsy install or something.

Could someone who does have access to those files upload them here for others?

---

### Post by bigredx24x on 2008-05-21
I am running 64-bit Kubuntu 8.04 with KDE4.

This is what I had to do to get the Rhapsody Online plugin to work:

1) Make a new .mozilla directory and add a plugins directory

> >> mv ~/.mozilla ~/.mozilla_bkup
>> mkdir ~/.mozilla
>> mkdir ~/.mozilla/plugins

2) Run the script in the following post to install the 32-bit version of Firefox on your 64-bit version of Ubuntu.

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

3) Run firefox32 

> >> /usr/local/firefox32/firefox

4) Goto [www.rhapsody.com](www.rhapsody.com) and install the plugin.  You may have to restart firefox after the install.

5) It should work now.

---

### Post by Cap'n Skyler on 2008-05-21
so you guys have the subscription rahpsody music service working in linux?
show me how !!
that is one of the few things holding me to darn windows !!:guitar:

---

