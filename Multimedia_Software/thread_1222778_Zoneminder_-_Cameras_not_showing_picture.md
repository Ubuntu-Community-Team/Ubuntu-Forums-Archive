---
title: "Zoneminder - Cameras not showing picture"
date: 2009-07-25
forum: Multimedia Software
---

### Post by LouisCribben on 2009-07-25
I installed Ubuntu today (latest and greatest edition)

Its an old p4 PC. I installed Zoneminder using some good instructions I found on the web.

It works, I can fire it up in Mozilla, and add cameras etc 

However, I cant see any output from the cameras

I've got a 4 BNC capture card which i bought on ebay.

I dont honestly know if the capture card is installed correctly

Looking at the output, below, it says its an unclassified device, does this matter ?

@p-desktop:~$ lspci | grep Bt878
02:09.0 Non-VGA unclassified device: Brooktree Corporation Bt878 Video Capture (rev 11)
02:09.1 Non-VGA unclassified device: Brooktree Corporation Bt878 Audio Capture (rev 11)




I didnt install the capture card manually, I just put it in the pci slot prior to installing ubuntu.

In Zoneminder, I configure the camera to have a location of \dev\video0 
Indeed there is a file \dev\video0 on my hard drive. What is this file, what is its purpose ?

I'm really a bit out of my depth, I would have hoped for some error/informational messages from Zoneminder to tell me if there is a problem with the camera/capture card, but there isn't

Hope someone can help me troubleshoot this..........I spent 6 hours already today trying to sort it out, and I spent 2 hours yesterday, and 2 hours the day before ! I even reinstalled Ubuntu!  

Thank you

---

### Post by LouisCribben on 2009-07-25
the pci card is the following

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=400058922322&ssPageName=ADME:B:EOIBSA:GB:1123](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=400058922322&ssPageName=ADME:B:EOIBSA:GB:1123)

---

### Post by wirepuller134 on 2009-07-26
I'm not familiar with that specific card, but am with the chipset.  What motherboard are you using the card with, there are a few known to cause irratic behavior or just not work at all.
  Even though it is being picked up, you will still need to tell it that there are 4 channels there. 
 
add the following to /etc/modprobe.conf
options bttv card=77

You can access the cameras with these settings.
/dev/video0 Channel: 0-3

I never recommend viewing the cameras directly from the server but use the web interface on another computer.  If using IE to view you will have to install a java file on the server it's self.

There is a lot of information available on the Zoneminder website/forums/FAQ.

---

### Post by LouisCribben on 2009-07-26
Thanks Wirepuller

You gave me good information, I didn't know that /dev/video0 is for all 4 Cameras. That's useful to know.

I still can't get it to work though, its a Dell Optiplex GX240, about 6 years old.

There is no etc/modprobe.conf  on my system, I added it, but it didnt solve the problem  

just googling around, I think the key file to change may be etc/modprobe.d/bttv.conf which should maybe contain the line

options bttv gbuffers=32 card=77 tuner=4 radio=0 coring=1 full_luma_range=1 chroma_agc=1 combfilter=1 autoload=0 triton1=0 vsfx=0


Bttv.conf didnt exist either, I added it, didnt work either !

It's probably something simple which is stopping it all from working, but I really don't know what it is ! In the meantime, I'll keep trying stuff !

---

### Post by wirepuller134 on 2009-07-26
There are a few live cd's available on the Zoneminder website.  The download page list a few at the bottom, and here is a post from their forums that list a few others. [http://www.zoneminder.com/forums/viewtopic.php?t=11873](http://www.zoneminder.com/forums/viewtopic.php?t=11873), there is also a Xubuntu livecd available from Bluecherry.net. 
I know Zoneminder likes a lot of ram, we wont commission a system without 1 gig. If we need resolutions set at 640x480 or above we increase the shared memory and install no less than 3 gigs of ram.  I have never set it up on Ubuntu, but you got my curiosity going, so am going to set one up tomorrow morning and see how it goes.  
I found a turtorial on the Zoneminder website for Ubuntu, [http://www.zoneminder.com/wiki/index.php/Ubuntu_9.04_Jaunty_desktop_with_graphical_interface](http://www.zoneminder.com/wiki/index.php/Ubuntu_9.04_Jaunty_desktop_with_graphical_interface)

Sorry for giving bad information on the file to edit, learned something myself today, we use Ubuntu on our desktops, but stick with what we know on production boxes.
  It could also be a bad card, or something as simply as it not being seated all the way into the slot.  Good luck and I hope you get it going.  I'll post back my install and compare notes.

---

### Post by LouisCribben on 2009-07-27
Thanks Wirepuller
 
I've tried a bit more to get it to work, no luck yet. I'll continue to try for another week or 2, and if I cant resolve it, I'll buy a dedicated embedded cctv dvr machine on ebay !!!
Hope it doesnt come to that ! I'm sure it wont. I really want to get Zoneminder working !
 
My machine has 1 gb /ram
 
 
 
Here is some output fr/om the my command prompt ! It's a bit long winded, but it may point to some problems ?
 
p@p-desktop:~$ sudo zmu -d /dev/video0 -q -v
[sudo] password for p: 
Video Capabilities
Name: BT878 video ( *** UNKNOWN/GENER
Type: 47
Can capture
Can tune
Does teletext
Overlay onto frame buffer
Can clip
Video Channels: 4
Audio Channels: 0
Maximum Width: 924
Maximum Height: 576
Minimum Width: 48
Minimum Height: 32
Window Attributes
X Offset: 0
Y Offset: 0
Width: 320
Height: 240
Picture Attributes
Palette: 4 - 24bit RGB
Colour Depth: 24
Brightness: 32768
Hue: 32768
Colour :32768
Contrast: 32768
Whiteness: 0
Channel 0 Attributes
Name: Television
Channel: 0
Flags: 1
Channel has a tuner
Type: 1 - TV
Format: 0 - PAL
Channel 1 Attributes
Name: Composite1
Channel: 1
Flags: 0
Type: 2 - Camera
Format: 0 - PAL
Channel 2 Attributes
Name: S-Video
Channel: 2
Flags: 0
Type: 2 - Camera
Format: 0 - PAL
Channel 3 Attributes
Name: Composite3
Channel: 3
Flags: 0
Type: 2 - Camera
Format: 0 - PAL
 
 
 
 
==========================================
p@p-desktop:~$ v4l-info /dev/video0
 
### v4l2 device info [/dev/video0] ###
general info
VIDIOC_QUERYCAP
driver : "bttv"
card : "BT878 video ( *** UNKNOWN/GENER"
bus_info : "PCI:0000:02:09.0"
version : 0.9.17
capabilities : 0x5010015 [VIDEO_CAPTURE,VIDEO_OVERLAY,VBI_CAPTURE,TUNER,READWRITE,STREAMING]
 
standards
VIDIOC_ENUMSTD(0)
index : 0
id : 0xb000 [NTSC_M,NTSC_M_JP,?]
name : "NTSC"
frameperiod.numerator : 1001
frameperiod.denominator : 30000
framelines : 525
VIDIOC_ENUMSTD(1)
index : 1
id : 0x1000 [NTSC_M]
name : "NTSC-M"
frameperiod.numerator : 1001
frameperiod.denominator : 30000
framelines : 525
VIDIOC_ENUMSTD(2)
index : 2
id : 0x2000 [NTSC_M_JP]
name : "NTSC-M-JP"
frameperiod.numerator : 1001
frameperiod.denominator : 30000
framelines : 525
VIDIOC_ENUMSTD(3)
index : 3
id : 0x8000 [?]
name : "NTSC-M-KR"
frameperiod.numerator : 1001
frameperiod.denominator : 30000
framelines : 525
VIDIOC_ENUMSTD(4)
index : 4
id : 0xff [PAL_B,PAL_B1,PAL_G,PAL_H,PAL_I,PAL_D,PAL_D1,PAL_K]
name : "PAL"
frameperiod.numerator : 1
frameperiod.denominator : 25
framelines : 625
VIDIOC_ENUMSTD(5)
index : 5
id : 0x7 [PAL_B,PAL_B1,PAL_G]
name : "PAL-BG"
frameperiod.numerator : 1
frameperiod.denominator : 25
framelines : 625
VIDIOC_ENUMSTD(6)
index : 6
id : 0x8 [PAL_H]
name : "PAL-H"
frameperiod.numerator : 1
frameperiod.denominator : 25
framelines : 625
VIDIOC_ENUMSTD(7)
index : 7
id : 0x10 [PAL_I]
name : "PAL-I"
frameperiod.numerator : 1
frameperiod.denominator : 25
framelines : 625
 
etc, etc

---

### Post by Steve Smith on 2009-08-01
LouisCribben

Hi - I wrote the tutorial at [http://www.zoneminder.com/wiki/index.php/Ubuntu_9.04_Jaunty_desktop_with_graphical_interface](http://www.zoneminder.com/wiki/index.php/Ubuntu_9.04_Jaunty_desktop_with_graphical_interface) though we're no experts here - just spent ages finding our way with it!

Delete the file /etc/modprobe.conf that you created.  Use only /etc/modprobe.d/bbtv.conf instead, or if you make changes in the one file the other file might override it.  After you make changes to that file you'll need to reboot to apply those changes.  The line

```
options bttv gbuffers=32 card=77 tuner=4 radio=0 coring=1 full_luma_range=1 chroma_agc=1 combfilter=1 autoload=0 triton1=0 vsfx=0

```

is something we grabbed from another forum somewhere.  Not all of those options are important, some just set if the automatic gain control etc. is switched on.

By 'not working' do you mean a black box, or garbage where the picture should be?  Could you upload a screenshot of your Zoneminder web page with the camera view on it if possible, to clarify exactly what you mean.

---

### Post by LouisCribben on 2009-08-02
Thanks Steve
 
My zoneminder installation now works.
 
Over the course of about 5 days, I tried various things, like changing the /etc/modprobe.d/bbtv.conf file and rebooting. I tried deleting /etc/modprobe.d/bbtv.conf and rebooting.
Nothing I tried worked.
Then yesterday, the cameras started working.
 
There is no bttv.conf file, it works without one. There is also no etc/modprobe.conf. 
I think the Ubuntu updates which were installed yesterday maybe did the trick.
Or it may have been something else.
 
In summary, I have zoneminder working, with absolutely no configuration changes, there is no bttv.conf file, no modprobe.conf file.

---

### Post by wirepuller134 on 2009-09-05
Its been a while, and looks like you got it working, congrats!!  But I finally had time to look at this.  We used 2 old Dell 2850 with SCSI drives, 4 gigs of ram, and a PV-155 card from Bluecherry.  We used Ubuntu desktop 9.04, fully updated before install.  
    For 1.23.3 we just installed from the repositories and had to create the following file to enable tuners 9-16.

file name: /etc/modprobe.d/options.conf
content: options bttv gbuffers=16 card=77,77,77,77

For 1.24.2 we just ran the update script supplied with it. 
So far we have 2 of these that have been up and running for a week without issues.

---

### Post by aaronLund on 2011-08-09
This still working ok?

---

