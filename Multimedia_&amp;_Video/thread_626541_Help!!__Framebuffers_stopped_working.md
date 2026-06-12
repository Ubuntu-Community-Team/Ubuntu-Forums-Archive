---
title: "Help!!  Framebuffers stopped working"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by dawynn on 2007-11-29
OK -- This one I may have done to myself.

Gutsy Gibbon in its current state mandates that I recompile my own kernel.  (They've chosen to keep the SIS5513 IDE module unavailable in the stock kernels -- which means the kernel does not recognize my hard drives).

Since I've had to recompile the kernel, I've started to play with several of the settings in the kernel configuration.  At this point, all of my hardware is working fine with KDE -- I have sound, the hard drives work, and the monitor seems to work fine.  But when I ask for any of the framebuffer screens (e.g., ctrl-alt-F1), all I see is a blank screen.

How can I get my framebuffers back?

I'm including a few attachments for review.  You'll find the .config file from my active kernel, the xorg.conf and Xorg.0.log, and my /boot/grub/menu.lst.

---

### Post by johnaaronrose on 2007-11-30
dawynn,

You're ahead of me! I have an extra 2 minutes boot time (in gutsy compared to feisty) due to sis5513 not being in kernel - launchpad bug . I tried to modprobe sis5513 after copying sis5513.ko from the 26.20.16 to the 2.6.22.14 lib modules. Result was module invalid format. I presume that this means that it is not acceptable to the newer kernel.

Do I therefore have to go down the kernel recompilation road. Let me show my ignorance about this: does kernel recompilation cause the ko files to be generated? If so, can I just do the sis5513.ko file?

Any guidance would be appreciated.

---

### Post by johnaaronrose on 2007-12-01
dawynn,

This may confuse things but I forgot to mention launchpad bug 122910 to fix no display of boot splash. An extract is shown below:

The original problem (black screen on tty[1-6]) is not related to nvidia or other hardware and is caused by a change in /scripts/init-top/framebuffer from Feisty to Gutsy:
 --- initrd.feisty/scripts/init-top/framebuffer 2007-02-07 10:52:34.000000000 +0100
+++ initrd/scripts/init-top/framebuffer 2007-10-22 10:10:22.000000000 +0200
@@ -82,8 +82,8 @@
 esac
  if [ -n "${FB}" ]; then
-       modprobe -q fbcon
-       modprobe -q ${FB} ${OPTS}
+       modprobe -Qb fbcon
+       modprobe -Qb ${FB} ${OPTS}
 fi
  if [ -e /proc/fb ]; then
 With this change modprobe ignores all modules listed in blacklist-framebuffer, including vesafb and fbcon, while in Feisty those modules were loaded if required by the user in grub/menu.lst, even if blacklisted.
 The change from Feisty to Gutsy in my opinion is wrong because if the user requires a particular vesa mode the modules should be loaded even if they could potentially crash the kernel.
 This problem can be solved in two ways: either the -b option is removed from the framebuffer script, like in Feisty, or the vesafb and fbcon modules are removed from the blacklist-framebuffer file. In my opinion the first option should be preferred because it would work with any graphics driver,

I've tried both options separately and together with 
no improvement.

I've also tried to fix excessive boot time (launchpad bug 155702) for sis5513 IDE using this fix:
This is all that needs to change.  In the boot/config-2.6.22.14-generic file, instead of this:
# CONFIG_BLK_DEV_SIS5513 is not set
 Use this:
CONFIG_BLK_DEV_SIS5513=m
Again with no success!

Perhaps these fixes may solve your problem?

Also, CtrAltF1 gives blank screen (after login) even though modprobe -l says that fbcon, sisfb, vesafb & vga16fb loaded!

I get the feeling that either sisfb.ko doesn't work properly or that another framebuffer .ko file is needed in order to display splash screen & have CtrlAltF1 display OK. Any ideas?

---

### Post by dawynn on 2008-02-03
*BUMP*

Now that my Hardy system is broken again, I'd like to review this problem and see if we can ever find a resolution.

I had no problems using Ctrl -Alt - F1 (etc) up through Feisty.  In Gutsy and Hardy (when its working), I just get a blank screen with a blinking underscore -- no command line.

This is especially annoying because I'm assuming its the same problem that will not allow me to sign-in via the "maintenance" options on Grub.  Doing so brings me all the way up to where I *should* see a command-line, but then just gives me a blinking cursor.

Any ideas?

---

