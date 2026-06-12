---
title: "Videos don't play, are blue (not tinted, I mean blue)"
date: 2012-03-05
forum: Multimedia Software
---

### Post by darrask on 2012-03-05
Hi all,
I've seen several posts about blue tinted videos so that I could never find an answer to my own, different problem.

On my Dell C400, running Lubuntu 11.10 (installed from a Dell D410 as the C400 does not have any CD-drive or USB booting capability), all videos (mp4 and flv from youtube) opened in Mplayer are blue, and I mean entirely blue like in window's screen of death. I have sound however.

It actually started with a webcam problem: I could send webcam video over Skype to others and even see it myself, but  video I received from them appeared as a blue screen in the player, and when I started moving the window, horizontal lines appeared over the whole screen, the picture disintegrated, the computer locked up and became gradually entirely white as if it was burning from the inside.

Any codecs I should install, any idea?

---

### Post by darrask on 2012-03-05
Update:
Just installed VLC, that could not play any video as well.

Videos that do not have time to show up as a blue screen show up black first, and as before, if I attempt to move the window while the screen is black, the picture disintegrates with horizontal lines on the height of the window and gradual screen whitening.

COuld it be because I installed the system for my C400 on another computer?

It looks like a basal, fatal error, as the problem now appears with ANY video opened ANYHOW.

I consider installing Xubuntu... if I don't get an idea.

---

### Post by MG&amp;TL on 2012-03-05
When you say "installed from"-you mean you removed the hard disk, then put it in the other machine for installation?

Consider Lubuntu 11.10-no reason not to update, the bug might be fixed, and if not, you get more up-to-date software.

I might suggest that you might have broken something if I am reading you right about the installation.

---

### Post by darrask on 2012-03-05
Thank you for your answer! Yes, I installed Lubuntu on my hard drive mounted on a USB-bootable computer and put it then back into my C400.

Actually I just corrected my post, I have lubuntu 11.10.

And I just found the solution myself! I mean... on another forum.

I had to select the " x11" driver or video output in Mplayer's preferences. That did not solve the VLC issue though, so I'll just unistall VLC.

Note that the other drivers, xv and gl, which are said to be more performant but less reliable, only gave a black screen.

Someone said that in 9.04, intel chipset graphic cards were not really supported, and that this may be the reason.

Could it also be that as I installed my system from another machine, the drivers don't match my changed hardware config? Actually this is a worry I had posted somewhere else on the forum, inconclusively.

---

### Post by MG&amp;TL on 2012-03-05
> **darrask said:**
> 
Could it also be that as I installed my system from another machine, the drivers don't match my changed hardware config? Actually this is a worry I had posted somewhere else on the forum, inconclusively.

Yes, quite possibly. I'm not saying your installation method is wrong (quite ingenious, actually), but ubiquity (the installer) should verify and configure the install for one particular computer. It will probably work on another, but it's not greatly reliable.

---

### Post by darrask on 2012-03-06
Alright, I'll reinstall as soon as I get an IDE cable for the CD reader.
Maybe I'll even get rid of strange screen flashes at startup and shutdown?

By the way, do you know how I could configure skype to use another video output like x11?
I only solved the issue for Mplayer, but skype, which supposedly has another video output/driver, still can't receivee any video.

---

### Post by MG&amp;TL on 2012-03-06
> **darrask said:**
> 
I only solved the issue for Mplayer, but skype, which supposedly has another video output/driver, still can't receivee any video.

It shouldn't do...when you say "receive" you mean from a webcam, or from somebody else..?

---

### Post by darrask on 2012-03-06
Yes, I mean receive webcam live video from another person.

---

### Post by MG&amp;TL on 2012-03-06
> **darrask said:**
> Yes, I mean receive webcam live video from another person.

Hm. Well, everything on Ubuntu should be routed through te X server, not anything else-I'd say it was a skype problem. What does

```
skype
```
from the command-line do/output? (I'm looking for debug output)

---

### Post by darrask on 2012-03-07
"skype" just opens the program, nothing more.

---

### Post by darrask on 2012-03-07
I read instructions here:
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
where it says:
> 
[B]Graphics Cards XV Skype and gstfakevideo
[/B]There are a couple of issues that create problems getting webcams working with skype. The gstfakevideo driver will probably get things working provided you have a suitable graphics card driver set up in xorg.conf 
There is a highly significant thing called xv this is easily overlooked in the rush to get video working. 
you need to install the gstreamer packages and try this out. 
gstreamer-properties 
go to the video tab and test your camera with the default settings if it doesn't work with the plugin 'autodetect' in 'Default output' change it to 'X Window System (No Xv)' then try again 
if that works and 'X Window System (X11/XShm/Xv)' doesn't work then you are using an incompatible graphics driver. 
That is the case, output to 'X Window System (No Xv)' works but  not 'X Window System (X11/XShm/Xv)'. Do I have an incompatible graphics  driver? Where can I download it?

---

### Post by MG&amp;TL on 2012-03-07
Linux's graphics card support is horrible. Not our fault, it's just the way it is. Have you installed a driver at all for you graphics card? You should be able to find one in "Additional Drivers". What card do you have?

---

### Post by darrask on 2012-03-07
I have an Intel 82830 CGC.
No proprietary driver installed in "additional drivers", only ubuntu's drivers?

"lshw -c video" says that I'm using the i915 driver

---

### Post by MG&amp;TL on 2012-03-07
> **darrask said:**
> I have an Intel 82830 CGC.
No proprietary driver installed in "additional drivers", only ubuntu's drivers?

"lshw -c video" says that I'm using the i915 driver

No, that should be fine then. Sorry, out of suggestions. It *is* going to the X server, otherwise you wouldn't be able to see it.

---

