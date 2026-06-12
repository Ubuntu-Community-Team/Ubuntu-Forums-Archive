---
title: "Lucid Lynx GLX broken after xserver-common and xserver-xorg-core update"
date: 2011-10-19
forum: Multimedia Software
---

### Post by norbert79 on 2011-10-19
[SIZE="3"]***Update on the 20[SIZE="1"]th[/SIZE] of October, 2011:***[/SIZE]
Ubuntu Canonical team has approached and solved the problem by releasing a new fix for the listed packages.

```
Start-Date: 2011-10-20  08:55:34
Upgrade: xserver-common (1.7.6-2ubuntu7.6, **1.7.6-2ubuntu7.9**), xserver-xorg-core (1.7.6-2ubuntu7.6, **1.7.6-2ubuntu7.9**), xnest (1.7.6-2ubuntu7.6, **1.7.6-2ubuntu7.9**)
End-Date: 2011-10-20  08:56:05
```

Based on these new packages, OpenGL (GLX) support has been restored, and is functional. For more information please see bug report of [**[color=#0000FF]Launchpad bugs[/color]**](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905).

[SIZE="3"]***Original post:***[/SIZE]

Good day everyone!

I just got informed about some latest security updates for Ubuntu Lucid 10.04.03, which came with the packages of:
```
Upgrade: xserver-common (1.7.6-2ubuntu7.6, 1.7.6-2ubuntu7.8), xserver-xorg-core (1.7.6-2ubuntu7.6, 1.7.6-2ubuntu7.8), xnest (1.7.6-2ubuntu7.6, 1.7.6-2ubuntu7.8)
```

Now since this update, as it worked before with current layout, I am unable to initialize the OpenGL support, switching to Compiz, instead of plain metacity. When doing this I am being refused by the system. Looking at the logs I have found this in .xsession-errors:
```
Nem érhet&#337; el olyan grafikus illeszt&#337;program a rendszerhez, amely támogatná a kompozit b&#337;vítményt, vagy a jelenlegi már támogatja ezt.
(**Translated:** No accessible driver available, which would support the compiz extension, or the current one already supporting it.)

compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

(gnome-appearance-properties:2962): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
```

Some details on my system:
```
**lshw:**
description: VGA compatible controller
product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
configuration: driver=i915 latency=0

**uname -a:**
Linux <name removed> 2.6.38-12-generic #51~lucid1-Ubuntu SMP Thu Sep 29 19:55:22 UTC 2011 i686 GNU/Linux

**dpkg -l | grep xserver**
xserver-xorg-core                                 2:1.7.6-2ubuntu7.8
xserver-common                                    2:1.7.6-2ubuntu7.8
xserver-xorg-video-intel                          2:2.9.1-3ubuntu5
```

When testing it using glxgears I get this:
```
glxgears:
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  17
  Current serial number in output stream:  17
```

As it seems the full OpenGL support disappeard since this new update. Anyone else experiencing similarly?

PS.: Yes, I know about ubuntu-bug, but apparently that seems having a bug too. It can't open up Firefox after collecting data, and crashes with an error message. :) And no, I haven't touched anything on X.org or around those packages, just used regular updates.

---

### Post by sybille on 2011-10-19
Hi,

I just want to confirm that I've experienced the same on my Lucid system. Also, I'll note that reverting to the prior versions of xserver-common and xserver-xorg-core restores GLX for me. So it's definitely the update.

I don't see any errors in my Xorg.0.log. It reports that GLX is loaded, with no errors:
```
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
```So that eliminates a linking error such as the one reported here:
[http://forums.debian.net/viewtopic.php?f=6&t=65667](http://forums.debian.net/viewtopic.php?f=6&t=65667)

I see that you use the i915 (intel) driver. I'm using the radeon (ati) video driver. It seems that this is not hardware or driver dependent. We are both using the same kernel, 2.6.38-12 #51~lucid1-Ubuntu SMP, although I am using the pae version.

---

### Post by norbert79 on 2011-10-19
**Sybille:** Thank you for confirming. I also wanted to confirm, that reverting to previous version (using the packages from launchpad, otherwise it was impossible getting older packages back) solved the problem, got OpenGL support again, so neither I can see any errors listed in the logs.

So basically it's the update causing the problem.

---

### Post by sybille on 2011-10-19
I was happy to find that you'd already posted! :)

To revert, I used synaptic, forced the package version (Package -> Force version...) and then, for the moment, locked the version (Package -> Lock version).

This is obviously a temporary workaround, since the problematic update is a security update that could "cause the X server to crash, leading to a denial or service, or possibly execute arbitrary code with root privileges," according to the Security Notice:
[http://www.ubuntu.com/usn/usn-1232-1/](http://www.ubuntu.com/usn/usn-1232-1/)

Any possibility of arbitrary code being executed with root privileges is not something mess with.

It looks like there is now a bug for this issue - I went to open one.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905)
I've just added a confirmation there with a link to this thread.

---

### Post by snakeplizzken on 2011-10-19
I first noticed the problem on a Ubuntu 10.04 installation running in VirtualBox.
After the upgrades of xserver-xorg-core and xserver-common (2:1.7.6-2ubuntu7.8 ) sent out yesterday it was impossible to activate desktop effects. I thought it was merely a matter of reinstalling the Virtualbox guest additions but that did not help.

So now I am running without desktop effects in that machine.

But then I updated the desktop machine (also Ubuntu 10.04) which has an ATI Radeon HD 5550 graphics card.
After restart the screen went totally black during startup...

Removing the graphics card and using the VGA native graphics on the Gigabyte motherboard did not help.
Same problem there....

Tried to revert the installation but I don't think I succeeded for some reason.

I was able to start the desktop machine in Gnome failsafe mode and disabled desktop effects.
Will have to manage without them until this has been resolved.

If it  is a problem on two totally different machines I am using it must affect many users (even if Ubuntu is a rather small community).

This bug meant several hours of investigation yesterday evening (and i lost some sleep so I am tired today) which I had preferred been spending on something more useful than annoying updates.

---

### Post by norbert79 on 2011-10-19
> **sybille said:**
> I was happy to find that you'd already posted! :)

...

It looks like there is now a bug for this issue - I went to open one.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905)
I've just added a confirmation there with a link to this thread.

Cheers for that. Any idea how you can post a bug report on Ubuntu-bug? It's not possible opening bugs, than using this tool only, but since that's broken for me, I am stuck :)

---

### Post by norbert79 on 2011-10-19
> **snakeplizzken said:**
> 
Tried to revert the installation but I don't think I succeeded for some reason.

I was able to start the desktop machine in Gnome failsafe mode and disabled desktop effects.
Will have to manage without them until this has been resolved.

Following the advice of Sybille:
> To revert, I used synaptic, forced the package version (Package -> Force version...) and then, for the moment, locked the version (Package -> Lock version).

I think using this method you would able to revert to the older versions also.

If not, here are the links I used for retrieving the older packages:
**[[color=#0000FF]xserver-common i386 1.7.6-2ubuntu7.6[/color]](http://launchpadlibrarian.net/65850865/xserver-common_1.7.6-2ubuntu7.6_all.deb)**
**[[color=#0000FF]xserver-xorg-core i386 1.7.6-2ubuntu7.6[/color]](http://launchpadlibrarian.net/65850866/xserver-xorg-core_1.7.6-2ubuntu7.6_i386.deb)**
**[[color=#0000FF]xnest i386 1.7.6-2ubuntu7.6[/color]](http://launchpadlibrarian.net/65850870/xnest_1.7.6-2ubuntu7.6_i386.deb)**

Just download them, and **dpkg -i *.deb** on all of them.

---

### Post by sybille on 2011-10-19
Oh, is Ubuntu-bug not the same as Launchpad Ubuntu bugs?

In any case, it would be helpful if anyone who's experiencing this could go to the Launchpad bug page and click on the top to confirm that the bug is affecting you.

Here's the link again:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905)

---

### Post by norbert79 on 2011-10-19
> **sybille said:**
> Oh, is Ubuntu-bug not the same as Launchpad Ubuntu bugs?

In any case, it would be helpful if anyone who's experiencing this could go to the Launchpad bug page and click on the top to confirm that the bug is affecting you.

Here's the link again:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905)

Did already. :) Ubuntu-bug is the tool using or to be used for reporting bugs into launchpad bugs, and if you click "report a bug" it leads you to a Wiki page, where you get explained how you can send in a bug using Ubuntu-bug. But I guess they never considered the possibility, that Ubuntu-bug might be broken for anyone. :lol:

---

### Post by Peeved Chemist on 2011-10-19
I noticed this bug because immediately after the update desktop effects stopped working.  

The affected system is a Toshiba Portege M700 tablet (Intel i965 video driver).  As with the other people who have reported this bug, reverting xserver-common and xserver-xorg-core back to the previous versions corrects this problem.

Is there a system this "update" actually works on? :)

---

### Post by sybille on 2011-10-19
> **norbert79 said:**
> Did already. :) Ubuntu-bug is the tool using or to be used for reporting bugs into launchpad bugs, and if you click "report a bug" it leads you to a Wiki page, where you get explained how you can send in a bug using Ubuntu-bug. But I guess they never considered the possibility, that Ubuntu-bug might be broken for anyone. :lol:

Thanks for confirming on Lauchpad.

And thank you for the info on Ubuntu-bug. It's not broken for me - I've just tried running the command. I've never used it before, that's all. I generally find that the bugs I've experienced are already reported so confirming on the web interface is enough.

---

### Post by norbert79 on 2011-10-19
> **sybille said:**
> Thanks for confirming on Lauchpad.

And thank you for the info on Ubuntu-bug. It's not broken for me - I've just tried running the command. I've never used it before, that's all. I generally find that the bugs I've experienced are already reported so confirming on the web interface is enough.

Well, basically the command also starts up, and starts collecting data, but fails when getting to the point feeding this into Firefox.
But that's unrelated to this bug, so let's focus on the xserver issues. :)

---

### Post by usreile on 2011-10-19
Same problem her but unfortunately I'm a complete noob to Ubuntu and reverting to the older versions does not come easy. I've gone to Synaptic and located x-server common and x-server-xorg-core, I then get 3 versions of each file to install:

2:1.7.6-2ubuntu7.8 (lucid-updates)
2:1.7.6-2ubuntu7 (lucid)
2:1.7.6-2ubuntu7~xup2 (lucid)

Reverting to any of these does not seem to fix my problem. Any help would be greatly appreciated. I'm running 10.04 amd64 version.

---

### Post by snakeplizzken on 2011-10-19
I managed to revert my VirtualBox installation so graphics effects are now enabled as before (back to version 2:1.7.6-2ubuntu7.6).

But my desktop machine does not work as expected.
Trying to enable the graphics effects the screen freezes (graphics are all scrambled).

What should I do? 

I recently reinstalled the machine so I am not happy about reinstalling again. Especially not due to some faulty update from Canonical :-(.

How do you know what the problem is?

---

### Post by snakeplizzken on 2011-10-19
On my VirtualBox installation I had the possibility to select 2:1.7.6-2ubuntu7.6 from the drop down list.
Selecting that and reverting and then locking to that version solved that problem.
Restarting the machine enabled the desktop effects without me doing anything specific.

Om my desktop machine that option was not available for some reason.
I manually installed the deb-packages and went through the same procedure as for the VirualBox installation but that did not help.
Trying to select enable the desktop effects made the screen scrambled.

---

### Post by sybille on 2011-10-19
OK, it looks like new, fixed packages are on the way:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905/comments/20](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905/comments/20)

It's no longer necessary to "Lock" the forced version of the packages if you've downgraded.

All things considered, this certainly was a speedy response by the developers, I think. Thank you to everyone who helped draw attention to the bug!

---

### Post by snakeplizzken on 2011-10-19
But how I fix the scrambled graphics when enabling desktop effects?
I guess updated packages wont solve that problem?

---

### Post by sybille on 2011-10-19
> **snakeplizzken said:**
> But how I fix the scrambled graphics when enabling desktop effects?
I guess updated packages wont solve that problem?

I don't know that the new packages *won't* fix the problem... 

Since the packages are building now, according to the bug, if it were me I'd just wait and install them when available, to see whether they will work for the desktop machine.

---

### Post by snakeplizzken on 2011-10-19
I looked at /etc/X11.
There is no xorg.conf. Is that how it should be?
Or has it been removed?

---

### Post by sybille on 2011-10-19
> **snakeplizzken said:**
> I looked at /etc/X11.
There is no xorg.conf. Is that how it should be?
Or has it been removed?

Yes, I believe that it is no longer necessary to have an xorg.conf.

---

### Post by norbert79 on 2011-10-20
Good morning everyone!

Sorry for not being online yesterday longer. I just want to say: Wow. Thank you all for the quick actions and such a flood of responses within the bug-report. I had to go through 57 mails since my last reply. :)
Well, new patch has been just downloaded, trying to install now. Will update this post, when updated behalf of the status.

Update: Yes, it seems having this one resolving the issue previously. It took X a bit to appear, and my screen turned white for a few seconds, but after that it seemed working well. I will update [**[color=#0000FF]the bug report[/color]**](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905) as well.

---

### Post by usreile on 2011-10-20
I seem to be the only one remaining with issues. I've upgraded but I still get OpenGL error when I try to open XBMC. I have completely removed xserver and then reinstalled but still no joy. I think maybe I really messed things up when I was attempting to downgrade yesterday.

Update: After doing all I could think of I decided to reinstall the nVidia driver...hey presto, fixed:)

Update2: Having fixed the problem I updated to xserver-common & xorg-core 7.10 only to have the same problem again so quick downgrade and reinstall of nVidia driver again. No updating for me for some time.

---

### Post by norbert79 on 2011-10-21
> **usreile said:**
> I seem to be the only one remaining with issues. I've upgraded but I still get OpenGL error when I try to open XBMC. ...

Thank you for sharing!

> While the problem from yesterday got solved by the patch for me, I have a discovered an interesting side-effect, causing minor issues: The bootsplash won't go back into graphical when shutting down, it stays in CLI mode.

Anyone else noticing this?

After last update it seems working again... This is getting very weird. Void the part in Quote please!

---

### Post by usreile on 2011-10-21
> **norbert79 said:**
> Thank you for sharing!

You're most welcome..

---

