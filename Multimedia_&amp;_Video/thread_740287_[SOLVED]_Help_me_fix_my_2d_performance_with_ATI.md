---
title: "[SOLVED] Help me fix my 2d performance with ATI"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by db0 on 2008-03-30
Hello, all. 

I recently made the mistake of installing the newest ATI drivers on my girlfriend's laptop. Before that I was using the restricted drivers which were good enough but were lacking syspend and hibernate features so I decided to check if the newer ones would fix that.

Initially I followed the installation instructions [here](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) and I did manage to get them to work. Unfortunately, whetever I do, I can't get the system to start using the ATI renderer instead os MESA.

The major problem I am having right now is that 2D performance has dropped drastically. To the level that fullscreen videos are very choppy and performance without compiz effects is abysmal (slow scrolling and refreshing etc)

My biggest problem is obviously Video playback and this is what I've been trying to troubleshoot for the last days. 
[LIST]
[*]I've tried reverting back to the old Restricted drivers but that has proven impossible. There is simply no way I see to restore them.
[*]I've tried installing the drivers with Envy (and uninstalling them) to no avail
[*]I've tried following the instructions [here](http://forum.compiz-fusion.org/showthread.php?t=6794) but they have made no difference, even though my xorg.0.log reports that all the modules are loaded
[*]I've tried using the patched mplayer as described [here](http://forum.compiz-fusion.org/showthread.php?t=3424) but even though the playback is fine,  the aspect ratio is screwed, fullscreen does not work. I can't find how to fix that or to make it work through gnome mplayer instead.
[/LIST]

So, I'm at my wits end as nothing seems to make a difference for my video playback. Can you think of something I can try, or at least some way to rollback to the old restricted drivers?
On the restricted drivers subject, I did indeed manage to have them installed after I uninstalled ATI drivers with envy, but although the restricted manager has a checkmark on "Enabled", the Status was red. Thus compiz was unusable and 2d still horrible.

Here is my [VGA info](http://pastebin.com/f5a17b131) & [xorg.conf]("http://pastebin.com/f3314b75b") 

Last time I eventually had to reinstall Ubuntu just to restore the restricted drivers but I'd like to avoid that if at all possible :(

Any help appreciated

---

### Post by db0 on 2008-04-01
My quest continues

I've now decided that I fist need to get the ATI renderer to work instead of Mesa Indirect.

Currently my fglrxinfo returns
```

$ fglrxinfo 
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

```

And it's been like that since my first installation.

I've tried following the instructions in [various]("http://ubuntuforums.org/showthread.php?p=4358132") [threads]("http://www.linuxquestions.org/questions/slackware-14/ati-catalyst-driver-8.1-problem-on-slack-10.2-619467/") but [nothing]("http://ubuntuforums.org/showthread.php?t=702810") seems to be working.

I also tried removing all xserver-xorg-video-* packages [as described here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying") but the only one I could not remove was intel which has some insane dependencies

The problem is getting even more annying as I can't even use Google Earth currently since my X-Server will restart. 

Does anyone have any idea on what to do to manage to enable the ATI renderer?

---

### Post by db0 on 2008-04-02
Update: I tried to remove my envy installation and do it manually. It worked but I still get Mesa indirect and I now have even worse performance :(

Nobody had any idea?

---

### Post by db0 on 2008-04-02
Wooohooo! Found it in [this thread]("http://ubuntuforums.org/showthread.php?p=3635640")

Apparently I needed to remove xserver-xgl and now I have direct rendering.
W00t!

Problem is that now I cannot activate compiz anymore 
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

---

### Post by db0 on 2008-04-02
Update: Finally seems resolved

I used Envy to reinstall Ati drivers (on top of my current installation) and it configured Compiz packages for me.

Now compiz seems to work :)

I'll leave this unsolved until my next reboot

---

