---
title: "Display Issues using AMD690G, 1360x768 LCD &amp; Feisty"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by HotFoot on 2007-04-07
I am having a few issues regarding video signal.  First, what I'm using:

AMD 690G chipset
DVI-HDMI cable
32" Dell LCD TV 1360x768 @ 60Hz
Feisty (beta)

I installed the restricted drivers for the onboard graphics using the new "restricted modules manager".  This worked great, and I got 3D acceleration working within minutes of my first boot.  However, I couldn't output the correct resolution for my screen, since it's a wxga format.  I followed instructions in a different thread and modified my xorg.conf file to include a modeline generated using:

```
gtf 1360 768 60
```

After restarting X, I now found I had the option of selecting 1360x768@60Hz.  This seemed promising, but when I chose this selection the TV went blank and eventually posted the "No Video Signal" message.  After a few more seconds the computer reverted to the previous display settings and I was able to see the desktop.  I was able to select the 1280x720@60Hz setting, and this works fine with the monitor.  So that's issue (1).

Issue (2) is that after not using the keyboard/mouse for 20 minutes, the screen goes blank.  I've disabled the screen saver and power saving features, so I doubt it's these.  Also, when the screen goes blank and then I move the mouse, the TV reports "HDMI" at the top of the screen as if it had just been turned back to this mode.  I believe what is happening is that the TV is going to sleep because it's not detecting activity coming from the PC.  This happens even while I'm watching .avi files or DVDs through Totem.

Issue (3) is that when I turn the TV off and leave the PC running, I'm unable to re-attain video signal when I turn the TV back on.  The screen stays blank and the notice "No Video Signal" appears.  I have to restart X and enter my user name and password without being able to see the screen.  Once the password is accepted and X returns to the desktop, I am able to get the video signal.  This behavior is very annoying, because restarting X kills all my running applications.

I believe issues (2) and (3) are related.  If the TV and graphics chip aren't communicating properly, I can see that causing these problems.  I don't know how to go about solving the issue, though.  I've updated my BIOS to the latest version (v0402).  I've tried using a different modeline at a lower refresh rate, but that didn't work.  Using a 50 Hz signal just made the 1280x720 resolution appear too tall to fit on the screen, and the 1360x768 resolution still didn't work.

In the past I've run the same TV using a different PC using a discrete nvidia 6600gt video card, also with the same DVI-HDMI cable.  I had none of these problems using the 1360x768@60Hz setting (once I doctored the xorg.conf file).

I would appreciate any help on the matter.  I don't know what else I can do to fix the problem.  I'm concerned that it's a driver support issue that might not be resolvable in the Linux environment.

---

### Post by heimo on 2007-04-07
Well, not sure about if this will work, or solve the blanking issue, but you could try these modelines, one by one (change your screen sections Modes line to include "1360x768@60"): 
```

ModeLine        "1360x768@60" 84.8 1360 1432 1568 1776 768 771 776 798 -HSync +VSync

# 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
Modeline "1360x768@60"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

Modeline "1360x768@60"      84.50  1360 1392 1712 1744    768  783  791  807

# 1360x768 @ 60Hz,  47.52 kHz hsync
Modeline "1360x768@60" 76.03 1360 1384 1464 1600 768 770 772 792

```

First one is from here:
[http://www.ubuntuusers.de/paste/8896/](http://www.ubuntuusers.de/paste/8896/)

---

### Post by HotFoot on 2007-04-07
Hi heimo,

Thanks for the help.  I tried each of those modelines, but they all gave me the same result of being able to display 1280x720 but not 1360x768.  The login screen still does not appear after ctrl-alt-backspace (I have to listen for the drum sound to know when to type user name and password).  I do see the selection for 1360x768@60Hz in the screen resolutions menu, but, as before, this mode results in no video signal being recognised by the TV.

I don't know if the new modelines will solve the screen going to sleep after 20 minutes issue.  It's too bad there's no setting on the TV to lengthen this time.

I think I'm going to try connecting with a VGA cable for now, and see if I can get that working.  I'll keep trying the DVI once in a while to see if driver updates or the official Feisty release fixes these problems.

EDIT: I'm now using a VGA cable.  All the previous issues have gone away, as in:

1) I can set the display resolution to 1360x768@60Hz.
2) I can see the login screen after restarting X.
3) I can turn the TV off and on again and it will re-acquire the video signal.
4) I expect that, because of (2) and (3), the TV will not go to sleep 20 minutes into watching a show.

Now, I'm fairly happy with the current setup, as it's completely functional.  However, I did buy this particular motherboard because of it's native DVI integration (and potential use for watching HDCP content).  I don't expect HDCP to work in Linux, but I do want to get my DVI working.  I guess I'll be testing out  the DVI-HDMI cable connection every time there's a kernel or ATi driver update.

---

### Post by faddat on 2007-04-16
hotfoot:

have you tried using Sabayon Linux?  It is generally just a little bit faster on the uptake with new kernels/packages/drivers than Ubuntu.  That said it's not the same kinda distro Ubuntu is, much more "bleeding edge".  Anyway, I'm just curious if you've tried it (particularly version 3.4) as I will be recieving my 690g from newegg this week and I am trying to choose a distro to start my new machine on.  I'd take any general-purpose 960g tips you have, as well.  

How's Sauerbraten?

Do you play Nexuiz?

(Sorry, had to ask, these two games are my "linux video benchmarks" and I am hoping that the 690g will outperform an AGP NVIDIA 5200 w/ 128MB.... here's hoping!

---

### Post by HotFoot on 2007-04-16
I haven't tried Sabayon Linux.  My only other experience with Linux is with Gentoo (dependant on a friend's expert help to maintain that system) and Suse.  I'm using Ubuntu because it seems the simplest thing for me.  I've had a lot of updates in the last couple weeks, which I think is probably typical for a Beta version.  I'll reserve final comment on the Radeon 1250 graphics until Feisty is out of Beta and a new versino of Envy has been released.

---

### Post by biker19 on 2007-04-28
I solved the no signal issue in Vista by changing the BIOS video section to have the TV as the first output. I still can't get Feisty to find a usable screen resolution at boot up on the CD.  I had a few issues with Vista but eventually solved most of those. Vista looks OK at 1280x720 so I figured I'd add that setting to the file - that should work right?

Well that didn't work. I got Feisty 64 bit installed using a regular monitor connected to the VGA output of the MB. After enabling the ATI restricted driver the only other resolution available was 720x480. I tried to edit the xorg.conf to add 1280x720 and got errors and could only get back into editing xorg.conf on the monitor - nothing shows on the TV.

One other issue - might be a deal braker. The whole reason I went with this board is to use a single HDMI cable between PC and TV. The sound doesn't work and if I can't get it to work I may just give up. Has anyone gotten sound to work via HDMI?

---

