---
title: "Ubuntu Gutsy 7.10 fresh install, black screen on login"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by SMix on 2007-10-30
Ok so I am a sort of newb to Linux but I have some pretty good baseline understanding.  I have searched all over these posts ... until about 3 am last night.  It drove me mad but here is the problem.  I decided to setup a dual-boot windows/linux.  Got Vista Ultimate running on its happy partition and and Ubuntu Gutsy on its.  Now when I enable the restricted drivers and restart I run into issues.  The splash screen does not display and the monitor (Which is a Magnavox 32" LCD TV) pops up the message about change resolution inside range of 1366x768@60Hz.  Then the screen changes again to blinking cursor, and then disappears again and shows this same screen again.  Now I thought I was screwed and attempted installing older legacy drivers, attempted the Envy program install, even tried installing the drivers from NVIDIA site myself.  None of these options worked.  I finally decided to pretend as a last resort that the login screen was there and I just couldn't see it.  Well I was right.  I typed username/pass and then the screen came on and loaded the desktop.  Now after being so frustrated I went back to windows today and finished customizing my system, and got the display set at 1360x768.  It's perfect for this screen.  When I tried choosing 1024x768 however it didn't work so well.  This is the res that Ubuntu was on before I installed the restricted driver and worked fine.  Now I am not sure what the problem is now, but I have a feeling it may be that the login/boot screens are set to display 1024x768 and possibly that is the prob.  I am not sure if it is just the monitor as I have read in another post.  I also don't know if it could be the EDID's? Not sure what these are but apparently this has been the issue in some cases as well with the monitor actually being the problem.  I fear it is the monitor being the issue as like I said I finally got into my desktop and all the nice 3d effects worked too.  Does anyone have any better knowledge or any good ideas?  The computer info is as follows:

HP Pavilion a1483w 
Onboard NVIDIA GeForce 6150LE
Magnavox 32" LCD TV

On a second note, I am also setting up a dual-boot on my laptop with the same setup.  Vista Ultimate and Ubuntu Gutsy.  Amazingly I am having the same exact issue on the laptop as the desktop.  Not my day as you could imagine.  The only difference in the laptop setup, is that it is a Tablet PC that has been reported to work fine, but does have the external VGA option.  I have read in some laptop setups that this may be causing issue as the display is turning on the VGA.  I have this laptop hooked up to a KVM which displays on the same Magnavox Monitor.  When I switch it to the laptop, it displays all sorts of color and scramble on the screen.  Any help for either situation would be greatly appreciated!! Laptop info as follows:

Compaq TC1100 Tablet PC
Onboard NVIDIA GeForce4 420 Go
15" Screen (1024x768 Max supported Res)

---

### Post by him610 on 2008-02-24
After the black screen appears, have you timed how long it stays black, or do you just reboot, or turn it off.
When I originally installed Xubuntu 6.04 on circa 1999 Dell GX1 with a PII, it would begin the boot process then the monitor would just black out. I thought something was wrong with my graphics card. Then I installed Kubuntu 6.04 on another machine, much newer, an Athlon 850MHz on a homebuilt from about 2001; same problem - black screen on the monitor. By the way it is a Planar 15 inch monitor with maximum resolution of 1024 X 768, and I have both computers connected to the monitor with a 4 port KVM switch.
To make a long story short, one day after I tried for the Nth time to boot up, I got distracted  and was away from the computer for awhile - maybe 5, 10, or even 20 minutes. When I came back, lo and behold, wonder of wonders, there was a login screen on the monitor!
I don't know if this is right or not, but it seems like some of the early LCD monitors when paired with older graphics cards don't initially display at the correct resolution for the monitor, but eventually if one waits long enough something in the boot process selects and configures the correct combination of resolution and vertical and horizontal sync rates.
Maybe this will help.

---

### Post by opusIV on 2008-02-26
Regarding the Tablet - tc1100 setup - I just started putting Ubuntu Gutsy on a tc1100.  I opted to swap out the HD and go entirely with Ubuntu.  I was installing via a USB CDROM. I found that if I tried to choose the top line of the install. I would end up with a scrambled unreadable screen.  I choose the "safe graphics mode" - line 2 of the install and everything went well.  I have not tried attaching an external monitor to the tablet yet.

Have you seen the following site?  It has quite a bit of detailed info on Ubuntu on the tc1100.

[http://ubuntuforums.org/showthread.php?t=563736](http://ubuntuforums.org/showthread.php?t=563736)

---

### Post by erginemr on 2008-02-26
Seems a Usplash screen issue to me. Please refer to the following howto, to see if the symptoms match:

[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

---

