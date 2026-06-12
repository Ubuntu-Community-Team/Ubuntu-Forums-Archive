---
title: "n00b needs help installing OpenChrome video drivers for VIA CN400"
date: 2006-06-28
forum: Multimedia &amp; Video
---

### Post by n00b@linux on 2006-06-28
I want to get my 20" Dell widescreen monitor (Dell 2005FPW) to the correct resolution.

I edited my /etc/X11/xorg.conf and added a ModeLine based on what I saw in /var/log/xorg.0.log.  This worked for me in the past when I had to add an identical ModeLine to xorg.conf when I had installed epiOS (a Gentoo derivative distro).  I had to tweak it with xvidtune but I got there in the end.

I've just installed Ubuntu 6.06 and repeated the above procedure.

The ModeLine didn't work and when I tried xvidtune I got the message "video are not settable on this chip".

I suspect this has something to do with my video driver.  My xorg.conf has the following:

```
Section "Device"
    Identifier            "Generic Video Card"
    Driver                 "vesa"
    BusID                 "PCI:1:0:0"
EndSection
``` 
Which tells me I've got a generic video driver installed.  Maybe this explains xvidtune doesn't work for me.

When I had epiOS installed (a Gentoo derivative distro), my xorg.conf file had the following:

```
Section "Device" 
    Identifier            "CardCRT" 
    Driver                 "via" 
    VendorName      "VIA" 
    BoardName        "CLE266/CN400" 
    BusID                 "PCI:1:0:0" 
    Option                "ActiveDevice"   "CRT" 
    Option                "AccelMethod"    "exa" 
EndSection
``` 
I'm pretty sure this video driver came from the OpenChrome project ([www.openchrome.org)]("http://www.openchrome.org%29").  I've looked there and can see that there are some binaries already done for Breezy, but will these work for Dapper?  Has anyone installed them and, if so, is there any additional hack work that needs to be done to get them working?

Finally, will they solve my problem?  (I'm a bit of a linux n00b and a little knowledge is a dangerous thing, so I wanted to get some advice first before I jump feet first into downloading and installing).

---

### Post by GarlicFish on 2006-06-28
I played with the openchrome drivers on a VIA SP8000 board and Debian 3.1 (Breezy didn't like the SATA controller!)
It took a lot of Googling and mucking about but you get there in the end.
It was a good few months ago and I have since replaced Debian with Suse10.1 for which I found some RPMs of the drivers.

Just take a backup and go for it.

If you have a second machine around it is useful for googling while your X server is in bits on the floor!

Good luck :-)

---

### Post by ahaslam on 2006-06-28
The via drivers with Dapper generally work quite well. I have the following in xrog.conf:

Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option		"DisableIRQ"
	Option		"EnableAGPDMA"

[B]Just changing the driver to 'via' and adding the two options should sort you out.
Make sure that the resoloution that  you want is listed in the 'screen' section.
[/B]
If this doesn't work upon reboot, start in recovery mode and use 'sudo nano /etc/X11/xorg.conf' to change back to the 'vesa' driver.

The only problem that I'm having with this driver is unstable 3D games, but then my chipset isn't officially supported (k8m800).

Tony.

PS. The openchrome drivers are the same as the X.org ones, just with a few 'experimental' additions. If these additions are proved stable, they should be added to X.org.

---

### Post by n00b@linux on 2006-06-28
Thanks guys.
Just a few more questions:
1.  Should I use the binaries or should I compile from source?
2.  Where to I install them, ie. which directory?  /? /etc?
I've never installed video drivers before so I don't know where to put them.
Thx

---

### Post by ahaslam on 2006-06-28
[QUOTE=n00b@linux]Thanks guys.
Just a few more questions:
1.  Should I use the binaries or should I compile from source?
2.  Where to I install them, ie. which directory?  /? /etc?
I've never installed video drivers before so I don't know where to put them.
Thx[/QUOTE]
Neither, literally just edit your xorg.conf with my suggestions. Have faith, the X.org Via driver in Dapper is really quite good. ;)

You don't need to change the Identifier or BusID, just change 'vesa' (generic driver) to 'via' and add the IRQ & DMA options. Don't forget to ensure that your required resoloution is shown in the 'screen' section. If it's not, add it (only edit the resoloutions it you're sure that both your graphics & display can support them). X should automatically select the highest available upon boot.

FYI: The main driver is named 'via_drv.so' and is located at ' /usr/lib/xorg/modules/drivers ' - you're currently using the 'vesa' one within the same directory.

If this doesn't work for you, feel free to try the openchrome drivers, but be aware that the only difference is a few experimental additions. If you choose this path I believe that you'll need to compile from source. I don't think that there's any Dapper binaries available yet.

Good luck,  doubt you'll need it though, the Via driver should work fine. 

Tony.

---

### Post by n00b@linux on 2006-06-28
Thanks Tony.  It worked!  I printed off my previous (Gentoo) Xorg.0.log and compared it to my Ubuntu Xorg.0.log and then matched off the modules being loaded.  I then discovered what you'd already alluded to: the modules were already in Dapper (/usr/lib/xorg/modules, /usr/xorg/modules/drivers and /usr/xorg/modules/extensions) so I only needed to edit my xorg.conf file (as you suggested).  Just a few simple lines of code, rebooted and that was it!  I then fine tuned with xvidtune and now I have my 1680x1050 screen resolution working as I wanted.

---

### Post by ahaslam on 2006-06-28
[QUOTE=n00b@linux]Thanks Tony.  It worked!  I printed off my previous (Gentoo) Xorg.0.log and compared it to my Ubuntu Xorg.0.log and then matched off the modules being loaded.  I then discovered what you'd already alluded to: the modules were already in Dapper (/usr/lib/xorg/modules, /usr/xorg/modules/drivers and /usr/xorg/modules/extensions) so I only needed to edit my xorg.conf file (as you suggested).  Just a few simple lines of code, rebooted and that was it!  I then fine tuned with xvidtune and now I have my 1680x1050 screen resolution working as I wanted.[/QUOTE]
Glad to help, you should also see a huge increase in FPS over the vesa driver. 8-) 

Tony.

---

### Post by n00b@linux on 2006-06-29
It's working fine except when it comes to video playback.  Some will play some just freeze the whole X window.  Any clues?  Do you know if these VIA drivers the ones from VIA, Xorg or OpenChrome?  I ask as the VIA produced drivers are less stable than the other two and was wondering if the instability I am experiencing is down to this.  I understand that the OpenChrome drivers are the most stable so I wanted to know if I need to actually install them separately if I want them.

---

### Post by ahaslam on 2006-06-30
[QUOTE=n00b@linux]It's working fine except when it comes to video playback.  Some will play some just freeze the whole X window.  Any clues?  Do you know if these VIA drivers the ones from VIA, Xorg or OpenChrome?  I ask as the VIA produced drivers are less stable than the other two and was wondering if the instability I am experiencing is down to this.  I understand that the OpenChrome drivers are the most stable so I wanted to know if I need to actually install them separately if I want them.[/QUOTE]
Dapper includes the ***X.org*** 'via' drivers, these are the most stable. The openchrome drivers are based upon the X.org ones, but add a few experimental features. The ones supplied by Via are known to be very buggy and may also pose a security threat. Unfortunately none of them are that good when it comes to 3D accel though.
Regarding your lock-ups, I've experienced random freezes while playing 3D games but video playback has been flawless. Try different video settings, I use Mplayer and found these settings gave me better quality & speed:
[ATTACH]11966[/ATTACH][ATTACH]11967[/ATTACH][ATTACH]11968[/ATTACH]


Tony.

PS. Dapper openchrome binaries are available, just not listed on the openchrome site (I'd forgotten all about them). Here's some links that will help with installation:
[[installation] General 6.06 - VIA Unichrome S3 display driver]("http://ubuntuforums.org/showthread.php?t=184512")
[[multimedia] Ubuntu 6.06 - Anyone find working instructions for installing UNICHROME drivers?]("http://ubuntuforums.org/showthread.php?t=203312")

If you do install the openchrome drivers, please let us know how you get on and wether it solves your problems.
Also a simple benchmark comparison (glxgears -printfps) would be useful to lots of people considering the change.


Tony.

---

### Post by n00b@linux on 2006-06-30
I haven't installed the OpenChrome drivers yet, but using the X.org drivers I get 696-697 fps when I run:

glxgears -printfps

I'll post the OpenChrome results when I've installed those drivers.

The video lock-up problem appears to be confined to Totem (the default installed video player).  When I installed and used Kaffeine I had not such lock ups.  I have no idea why though.

I'm kinda stuck installing the Win32 codes for Kaffeine from [http://www.mplayerhq.hu](http://www.mplayerhq.hu) and I could really use some help on the commands I need to type in the Terminal.

---

### Post by ahaslam on 2006-06-30
I really recommend that you try Mplayer. I experienced glitches (lines at the bottom of the screen) with totem in fullscreen. I found kaffeine to be good, but Mplayer was even better for me (better quality & used less resourses). 
To install the required codecs, follow the guide on this thread:

[[howto] Gnome 6.06 - HOWTO multimedia in Ubuntu Dapper]("http://ubuntuforums.org/showthread.php?t=186792")


Tony.

btw your fps is quite good. My laptop only gets 421 fps, though it is 2 years old.

---

### Post by ahaslam on 2006-07-19
Hi, 

I thought I'd update you on the OpenChrome Drivers, as I've just compiled & installed them.

Performance & stability is identical to the x.org 'via' driver, I still get 421fps & some 3D games/screensavers cause freezes. Picture and video quality has also remained unchanged.

The process of compiling & installing took me well over an hour as extra packages needed installing & the kernel module needed patching.  

As your direct rendering is working & you've a good frame rate, I'd stay with the stock 'via' drivers. If you want to try it anyway, I got all of my information from the threads below:

[http://ubuntuforums.org/showthread.php?t=203312](http://ubuntuforums.org/showthread.php?t=203312)
[http://ubuntuforums.org/showthread.php?t=184512](http://ubuntuforums.org/showthread.php?t=184512)


Tony.

---

### Post by ajlapp on 2006-08-21
after doing a fresh install of Ubuntu and updating, my xserver won't start.

i tried changing the driver to via in my xorg.conf and adding the options listed but the server is still not starting.  

??

via sp13000 
ubuntu 6

---

