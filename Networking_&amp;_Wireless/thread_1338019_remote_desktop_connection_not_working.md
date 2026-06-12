---
title: "remote desktop connection not working"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by itilious on 2009-11-26
I have an ubuntu 9.10 installation with compiz enabled and am a fairly noob to the linux scene.

The issue is when I'm trying to remote desktop connect via windows machine using VNC viewer the screen does not refresh, I'm aware of the bug also from: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126)

 I'm sure what my work around option is and a little help in doing it :)

Any help is GREATLY appreciated

---

### Post by jonnywombat on 2009-11-26
I had the very same problem, but failed to find a satisfactory work around. The only solution I have found is to disable compiz on the remote machine (it makes no difference whether the local machine is running compiz or not).


AFIAK this has been fixed upstream in the packages for lucid, so I guess it's a game of waiting till april.

---

### Post by jocefus on 2009-11-26
Running karmic x86_64 and nvidia proprietary driver 190.42
I have been able to compile  and install latest xorg-server. vino and compiz are already latest i could find. Xorg -version:
 
X.Org X Server 1.7.1
Release Date: 2009-10-23
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-14-generic x86_64
Current Operating System: Linux htpc 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=547ef98a-2835-4752-b755-d8b916aa3655 ro
Build Date: 26 November 2009  07:35:59PM
Current version of pixman: 0.16.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.

Everything still functions with no other bugs to speak of so far, but no fix. There are also no relevant errors or warnings in xorg log. Man I wish someone could shed some light on this subject.

---

### Post by itilious on 2009-11-27
so we're basically SOL for the time being then on being able to remote desktop connect :(

---

### Post by jonnywombat on 2009-11-27
If your clever (well more clever than I) you may be able to create a script to turn of compiz and then have then create a launcher to run this from the panel/desktop.

Then when you log in to your remote machine you can click on the launcher and once it has run and turned off compiz then the screen will refresh.  Then you can do whatever you need to on the remote machine, then when your done you could toggle back on in the same way. I saw a how-to kinda post somewhere in launchpad, but can't find it again now, sorry

---

### Post by jocefus on 2009-11-29
I have been using the script workaround, just had free time to delv a bit. Btw when I did upgrade to Linux 2.6.31-15-generic kernel, among alot of other updates, x started crashing on boot. Would get flickering screen and no login window or anything. Reinstalling nvidia drivers did no good, machine was only stable again after killing gdm. Had to revert to old xorg server. Anyways... be warned.

---

### Post by jocefus on 2009-11-30
In the mean time, I added a couple of custom launchers to my top panel to kill compiz and load metacity and vica versa. It was pretty straight-forward.

First right click on the panel you wish to add the launcher and select "Add to Panel." 
Select "Custom Application Launcher" and click add, this will bring up a window to enter command information. 

You can change the name, desc, icon to your liking. The commands you want are 'metacity --replace' for default effects launcher and 'compiz --replace' for 3D effects launcher.

One could make a script to replace the "other" window manger all in one icon, but I go for simplicity. How hard is it to select either button and how much panel space is lost?

So... after installing the custom launchers, its as simple as ssh-vnc in and click the "Disable Compiz" launcher or what ever you choose to name it and wait for the refresh. You can re-enable it using the other launcher whenever you so choose. I know this isn't a new workaround, just a different approach to the whole desktop script idea.

---

