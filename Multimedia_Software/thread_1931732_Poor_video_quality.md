---
title: "Poor video quality"
date: 2012-02-26
forum: Multimedia Software
---

### Post by eb sol on 2012-02-26
Hi, I've got a major problem and I need your help :( ..

I tried upgrading my PC from ubuntu 10.10 to 11.10 using the regular way but I couldn't ..

HP all-in-one 200 ,,[** specifications are in this link ** ]("http://bit.ly/px7vbA") ..


[IMG]http://ebraheem.com/up/42BB4B4AC7D20224247D0EEAE52D51A685/4843526F19158788C1A2344023E2A10E5.gif[/IMG]



[URL="http://ubuntuforums.org/showthread.php?t=1860710"][B]So someone advised me to use 'nomodeset' which has fixed the problem.
[/B][/URL]
Now, every time I turn my PC on, I must edit the grub options and use 'nomodeset' ..

The problem is that the quality of the video is quite bad.. 

I tried downloading the latest drive and the system says there isn't..

The system cannot detect any screens, nor I can change the resolution ..

I'm an ubuntu user and I can't use other OSs :(

SO, before I sell the PC :( .. can anyone help me please ..

---

### Post by eb sol on 2012-02-27
:( .. Anyone ..

---

### Post by BicyclerBoy on 2012-02-27
The nomodeset is a hack to stop KMS (kernel mode setting) drivers from loading.
All the usable video drivers have to use KMS.
So no KMS means the fallback driver (vesa) is used, this limits resolution & has no openGL performance. 

I would guess your all-in-one uses an intel chipset GMA900/950 graphics.
This driver is part of standand *buntu...seems like there is a problem  in intel kernel module. Your h/w uses an internal LVDS link to the panel like a laptop.

See post #9:
[http://ubuntuforums.org/showthread.php?t=1866756](http://ubuntuforums.org/showthread.php?t=1866756)
which links to:
[https://bugs.freedesktop.org/show_bug.cgi?id=43171](https://bugs.freedesktop.org/show_bug.cgi?id=43171)

Looks like you would need a very up-to-date kernel..

---

### Post by eb sol on 2012-02-28
> **BicyclerBoy said:**
> The nomodeset is a hack to stop KMS (kernel mode setting) drivers from loading.
All the usable video drivers have to use KMS.
So no KMS means the fallback driver (vesa) is used, this limits resolution & has no openGL performance. 

I would guess your all-in-one uses an intel chipset GMA900/950 graphics.
This driver is part of standand *buntu...seems like there is a problem  in intel kernel module. Your h/w uses an internal LVDS link to the panel like a laptop.

See post #9:
[http://ubuntuforums.org/showthread.php?t=1866756](http://ubuntuforums.org/showthread.php?t=1866756)
which links to:
[https://bugs.freedesktop.org/show_bug.cgi?id=43171](https://bugs.freedesktop.org/show_bug.cgi?id=43171)

Looks like you would need a very up-to-date kernel..

BicyclerBoy,, thanks you very very much ..

To be honest,, I don't know what to do with the link you've given me ..

How can I have an up-to-date kernal ?

I've updated my system to the latest updates..

Do you think that this PC might run ubuntu again :(  ?

---

### Post by BicyclerBoy on 2012-02-28
I think you will have to compile the intel kernelmodule so you can apply the 'linked to' patch.

If this is not possible (I would not attempt it) you can find more up-to-date intel drivers from a ppa with 11.10 packages.

This ppa is leading/bleeding edge..but that is better than a black screen..
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric)

The kernel module is built from git 14-02-2012..

Add the ppa & then reload/update synaptic..

Then reboot without using the "nomodeset" option.

If the X server does not start you can console login:
<ctrl>+<alt>+<F1>
exactly what you could do next is a another story..

---

### Post by eb sol on 2012-02-29
> **BicyclerBoy said:**
> I think you will have to compile the intel kernelmodule so you can apply the 'linked to' patch.

If this is not possible (I would not attempt it) you can find more up-to-date intel drivers from a ppa with 11.10 packages.

This ppa is leading/bleeding edge..but that is better than a black screen..
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric)

The kernel module is built from git 14-02-2012..

Add the ppa & then reload/update synaptic..

Then reboot without using the "nomodeset" option.

If the X server does not start you can console login:
<ctrl>+<alt>+<F1>
exactly what you could do next is a another story..

Hi BicyclerBoy ,, Thanks for the respond ,,

I did add the ppa & then I updated the system the regular way..

After that, I restarted the computer,, and the BLACK SCREEN was there for the welcom :mad:

I even couldn't login as you told me ..

What do you think ? is there another way ?

Cheers mate

---

### Post by BicyclerBoy on 2012-02-29
Did the update pull down about a dozen packages ?
Synaptic package manager allows you to view packages by origin..

I guess if the latest xorg-edgers did not fix the problem then the patch must not have worked its way thru'.

The safest/easiest way is to wait & continue with "nomodeset" grub option.
Check every week or after any update from xorg-edgers (sometimes daily).

I have not compiled intel driver & can't believe it is trivial undertaking.

---

### Post by eb sol on 2012-03-01
:(

Yes, he did install a great amount of packages..

[**This picture shows the packages that are installed ..**]("http://ebraheem.com/up/42BB4B4AC7D20224247D0EEAE52D51A685/53D579DFB2347557F8A7BCFDDB2DF7CA1F.png")

As for waiting, my computer is using ubuntu 10.10 .. I've been waiting for the updates since ubuntu 11.04.. :(

I will wait more if I have to.. :) 

Thank you very much for responding man ,, I appreciate it ..

---

### Post by snafu_az on 2012-03-01
I'm basically having the same problem. I can only get it to work with  nomodeset

[http://ubuntuforums.org/showthread.php?t=1930435](http://ubuntuforums.org/showthread.php?t=1930435)

I've been trying for almost 2 months and haven't made any headway.

---

### Post by BicyclerBoy on 2012-03-01
The bugzilla link posted earlier indicates that the patch was moved to status:
"Patch is on track to -next, marking as fixed" on 15/02/2012.

This is one week after your xorg-edgers git pull date (08/02/2012) (Maverick)
I don't know if:
- xorg-edgers git pulls from freedesktop
- xorg-edgers git tracks freedesktop

The Oneiric packages are git date 23/02/2012.

*buntu 10.10 is a bad release to be left using. It is not LTS.

---

### Post by eb sol on 2012-03-02
[CENTER]:popcorn: :popcorn: :popcorn: :popcorn: 

snafu_az ,, BicyclerBoy

[SIZE="3"][COLOR="Red"]GOOD NEWS GUYS .. THIS PROBLEM HAS BEEN FIXED IN THE NEW UBUNTU 12.04 LTS (Precise Pangolin) Beta version number 1[/COLOR][/SIZE]

Download: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Picture from my PC

[IMG]http://ebraheem.com/up/42BB4B4AC7D20224247D0EEAE52D51A685/561C32054F3FB00E54B0B236C503A15ABC.png[/IMG]

What a great feeling :) ..

This post will be marked as solved..

BicyclerBoy .. Thanks again .. God bless you :)[/CENTER]

---

### Post by BicyclerBoy on 2012-03-03
No need to thank me..
D Wolff debugged the problem & proposed a patch to freedesktop.org.

---

### Post by snafu_az on 2012-03-05
It didn't fix my problem.  I still can't get it to come up correctly unless I use nomodeset.

Plus now with 12.04 my touch screen doesn't work anymore.

---

### Post by BicyclerBoy on 2012-03-05
What error messages show up in /var/log/Xorg.0.log ?
The same or different ?

Configure grub to allow KMS & intel driver to load then..
Post the whole Xorg log file as an attachment.

I think your machine uses SNA sandybridge i5 HD3000 GPU..
Have you tried xorg-edgers with 12.04 ?

---

### Post by snafu_az on 2012-03-06
It still doesn't seem to detect the monitor.  I have an HP TouchSmart 610.  I'm thinking of going back to 11.10, at least the touchscreen would work.

Here's my Xorg.0.log

---

### Post by BicyclerBoy on 2012-03-07
There was some discussion about forcing LVDS with this grub option:
video=LVDS-1:e..

Else I would try a custom /etc/X11/xorg.conf to force the LVDS output on.

You can't use xrandr from a console screen so I think we have to find the right keywords for xorg.conf to force undetected monitor connection. These keyword exist for nVidia X server driver...

---

