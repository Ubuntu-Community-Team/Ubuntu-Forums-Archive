---
title: "HTPC Build"
date: 2009-02-12
forum: Mythbuntu
---

### Post by phismith on 2009-02-12
Greetings All,

After playing around with mythbuntu on an old PC, I've developed an itch for something better.
I'm thinking about using the gigabyte GA-EG43M-S2H
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128354](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128354)

I also like the look of 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237)

or

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813186140](http://www.newegg.com/Product/Product.aspx?Item=N82E16813186140)

Has anyone had any experience with these boards? My goal is video and sound over hdmi to my receiver.

I'm open to other suggestions.I already have an intel 631 P4 that I'd like to make use of. 

Thank!

---

### Post by nicoloks on 2009-02-13
By the looks you are wanting HDMI on board? Do you plan on watching 1080p content? If so, then you'll probably need to get a board with a Nvidia Geforce 8 or better on it so you can take advantage of VDPAU. I have a AMD X2 3800+ (dual core 2Ghz) system and got myself a 8400GS the other day, and when using mplayer compiled to use VDPAU it is like chalk and cheese. Beforehand 1080p content was like watching a slideshow with 95% CPU usage, now it plays perfectly and rarely gets above 20% CPU usage.

With sound it might be an idea to check the list of supported hardware in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz. You *should* be ok with most Realtek chips I think, but I have had issues with support for VIA sound chipsets. I see the boards you picked out had ALC883/888 chipsets which I'm almost certain are supported by ALSA.

---

### Post by phismith on 2009-02-13
Thanks! 
Yes, you are correct, I'd like to out put 1980p to my tv.

Do you know how the Geforce 9300/9400 chipset do? I was hoping to make use on the on board graphics.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128363](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128363)

Looks like a great option if the 9400 is supported. 1080p would be nice but at the same time, i'd like to be able to have it "just work"

---

### Post by newlinux on 2009-02-13
According to:

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

the 9400 is supported by VDPAU. 

Please note that displaying content at 1080p is different than decoding 1080p content. You won't have any problem displaying content at 1080p with much lesser graphics cards and that CPU (so you could playback regular dvds and mpeg-2 720p/1080i recordings at an upscaled resolution of 1080p with no problem) . It is the decoding of content that needs more processor power. 

I have a P4 3.0 with a nvidia 7100 card can output a resolution of 1080p for various content, but it would not have enough power to decode material that is 1080p h.264 encoded. It can playback up to 1080i encoded Mpeg-2 content and even 720p h.264 encoded content. If it had a VDPAU supported video card it would be able to playback 1080p h.264 content (you have to use software players that support VDPAU to take advantage of this as well).

So if you get the board with the 9400, I think you'll have all your bases covered.

---

### Post by phismith on 2009-02-13
Great! Thanks for the link, seems to have all the information I need. Displaying is what I'm currently intrested in. Decoding will be a "down the road" project. Right now 1080 video and sound over HDMI will make me a very happy camper.  
Is VDPAU built into mythbuntu 8.10 or do will I need to enable a special repository?

---

### Post by newlinux on 2009-02-13
I'm not sure of the default nvidia driver version in 8.10 (Most of my machines are still on 8.04), but I believe you will need to download the latest nvidia drivers and install them (it's easy to find directions, and it isn't that difficult when you get to it), and you will probably have to compile your own mplayer to support VDPAU - and there are ubuntu packages for mythtv that have VDPAU support that you can just install - if you are going that route - I'd recommend you install ubuntu instead of mythbuntu and then install the VDPAU enabled myth packages so there are no conflicts.

---

### Post by phismith on 2009-02-13
Wow thanks for all the help!:grin: I'm starting to feel like I can actually get this to work. here's what I'm thinking

The gigabyte GA-E7AUM-DS2H which has the geforce 9400. I'll install 8.10, update the driver (I found some pretty solid looking instructions here: [http://ubuntuforums.org/showpost.php?p=6426397&postcount=7](http://ubuntuforums.org/showpost.php?p=6426397&postcount=7) ) Then install the mythtv and mplayer enabled VDPAU from here: [http://www.avenard.org/files/mythtv-vdpau/](http://www.avenard.org/files/mythtv-vdpau/)

Are there any differences between Ubuntu with mythtv vs. mythbuntu? I like a lot of the extra plugins like mythweb, mythweather and so on. 

So will the VDPAU get me all set for HDMI video and sound? Or do I need to add some more steps for that to work smoothly?

Additionally, if I just wanted to go with regular 720 over HDMI would I still need to do everything above or is that just for 1080p?

Thanks!

---

### Post by nicoloks on 2009-02-13
Not sure what the exact difference between Ubuntu + Mythtv Vs Mythbuntu are, however I get the impression Mythbuntu is an easier transition for those migrating from the M$ camp.

VDPAU is for video only. For audio you'll use a package called ALSA. That last motherboard you linked to is using the Realtek ALC889A codec which I'm not 100% sure is supported, but you should be right.

VDPAU also does not care about the resolution, only the video codec used for encoding. VDPAU supports h264, VC1, WMV, Mpeg 1 and Mpeg2.

---

### Post by phismith on 2009-02-13
Thanks for that info. As far as I can tell I'll have to update the alsa driver to .19, I'm sure direction are out there. It sounds like the vdpau should be an easy upgrade. I'm going to order the parts I need. I'll keep everyone posted with my results.

---

### Post by newlinux on 2009-02-13
One of the main differences is one comes with mythtv installed (mythbuntu) and one doesn't.  Of course you can always install myth packages in regular ubuntu. Also, by default mythbuntu uses XFCE, whereas ubuntu uses gnome. 


The reason I was saying you might want to go with regular ubuntu is if you want VDPAU support, since the version of myth by default in mythbuntu currently doesn't support - so you would end up installing your own version (either compiling it, or installing the VDPAU enabled packages you can get from a third party repository). IF you do this with myth already installed (as is the case with mythbuntu) you will most likely run into conflicts. 

Installing VDPAU is fairly easy, but to use it, you have to use software that supports it. You can patch mplayer to use it, but for myth's internal player to use it, you will have to install a version of myth not in ubuntu's standard repos - at least last I checked. After you install vDPAU enabled myth, be sure to configure your playback profiles to use VDPAU as specified below.

[http://www.mythtv.org/wiki/VDPAU#MythTV_0.21-fixes_and_Ubuntu_repository](http://www.mythtv.org/wiki/VDPAU#MythTV_0.21-fixes_and_Ubuntu_repository)

---

### Post by phismith on 2009-02-13
My understanding is the VDPAU just allows me to move some of the decoding load to the GPU, is this correct? If I just installed ubuntu and mythtv (or just went right to mythbuntu), upgraded my ALSA to .19 what output would I get on HDMI? 720?

---

### Post by newlinux on 2009-02-14
> **phismith said:**
> My understanding is the VDPAU just allows me to move some of the decoding load to the GPU, is this correct? If I just installed ubuntu and mythtv (or just went right to mythbuntu), upgraded my ALSA to .19 what output would I get on HDMI? 720?


I gave an idea of what you will be able to do without VDPAU earlier in this thread (my system with the p4 3.0 is basically the same CPU you will be using - I believe it's a p4 630)

You can always output 1080p. The issue is whether or not you can decode different files with various formats (h.264/mpeg-2, etc.) and resolutions (720p 1080i/p).

---

### Post by phismith on 2009-02-14
My apologies I didn't look back before I posted. I placed my order with newegg last night. Once everything arrives,k I'll let everyone know how it goes. For fun here are my specs:

Gigabyte GA-E7AUM-DS2H (Geforce 9400)
P4 631 3.0 GHz
2 GB Gskill DDR2 800
Samsung 500GB Sata drive
SATA DVD/ CD-RW ROM
USB Card reader
Streamzap PC Remote Control
Hauppauge PVR-250

Again, thanks for all the help the ubuntu community is nothing short of amazing.

---

### Post by ebe326 on 2009-04-05
How is this project going? I am looking at the same motherboard and would like to use the hdmi audio/video output.

---

### Post by phismith on 2009-04-05
> **ebe326 said:**
> How is this project going? I am looking at the same motherboard and would like to use the hdmi audio/video output.

I just completed it the other night. Everything is working well. How I got HDMI audio working is listed here: [http://ubuntuforums.org/showthread.php?p=6765383#post6765383](http://ubuntuforums.org/showthread.php?p=6765383#post6765383)
HDMI video worked "put of the box" with the nvidia driver. I would highly recommend that motherboard.

---

