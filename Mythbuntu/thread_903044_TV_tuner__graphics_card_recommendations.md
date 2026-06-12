---
title: "TV tuner / graphics card recommendations???"
date: 2008-08-27
forum: Mythbuntu
---

### Post by kwilliam on 2008-08-27
Hi, I'm building a low-budget MythTV box for college. I got an ATI HDTV Wonder card, but have been completely unable to get it to work. Therefore, I'm in the market for a new one. This time, I'd like to get one that works "out-of-the-box" with Mythbuntu, with no firmware downloading/kernel hacking/compiling anything. I need a card that does analog cable channels (United States), preferably with digital cable ability too, but that's not a must. Also, I've decided I need a graphics card with TV out so it can work with normal TVs that don't have a VGA or DVI input. (Preferably ATI, since they've been more Linux friendly than Nvidia lately.)

Here is my current build: 
ECS 761GX-M754 motherboard w/ (crappy) onboard SiS graphics
2GHz AMD64 3000+ CPU
1 GB RAM
1 450W power supply
1 DVD-ROM drive
2 80GB Western Digital IDE hard drives
1 ATI HDTV Wonder tv capture card (can't get it to work)

I've got one PCI-Express slot, 4 PCI slots, and several USB slots available.  Any and all suggestions are welcome. (But I really want it to "just work" this time.)

---

### Post by Meph1st0 on 2008-08-27
The TV tuner card that I use is the PcHDTV 5500 tuner card.  In my experience this card just works.  I don't have to do anything to get it to work.  This card was built specifically for linux and the drivers are built into Ubuntu.  You can get it at [www.pchdtv.com](www.pchdtv.com).

---

### Post by sloggerkhan on 2008-08-27
I agree with above poster. pcHDTV is probably way to go, I'd say stick with ATI, but your video playback of stuff encoded in divx or mpg4 or ogg/theora and h.264 and similar will depend much more on cpu currently as decode will be done by CPU. Still, once decoded, IMO ATI video is better than nVidia's.

---

### Post by saxuntu on 2008-08-28
If your looking for lowbudget the Hauppauge 150 worked for me. But with the digital broadcasts you might wanna look into the HDHomerun from Silicon Dust. Doesn't do analog, but hook an antenna up to it and you have digital tv.

---

### Post by kwilliam on 2008-08-28
Wow, that's cool that it's specially made for Linux and the company is founded by Linux hobbiests for Linux hobbiests... I really like that idea, but my wallet is out-voting my idealism at the moment. The price on the website, $129, is a bit steep for this college student. I got the ATI card for $40 from a relative, and by reusing the hard drives and dvd drive of an old computer, I've put together the whole build listed above so far for only $170 USD. At $130+shipping, that tuner card practically doubles the cost of my box. And more than likely I'll still have to buy a graphics card on top of that! Are there any tuner cards in the $40-$70 dollar range? Like I said, it doesn't have to do digital or HD, just analog.

---

### Post by kwilliam on 2008-08-28
saxuntu: Did you have to do anything extra to get the Hauppauge 150 to work? What version of Mythbuntu did you use? I'm fine with tweaking config files but would rather avoid hours of trial and error frustration.

Edit: the [Issues and Problems]("http://mythtv.org/wiki/index.php/Hauppauge_PVR-150#Issues_and_Problems") section of the mythtv wiki page for this card scares me a little.

---

### Post by anonymousdog on 2008-08-28
I've had zero issues with the PVR-500 which linux treats like two PVR-150s.  It just works out of the box.  There's probably a long list of probs/resolutions b/c the card is so widely used with MythTV.

---

### Post by slickware on 2008-08-28
The alpha release of MB 8.1x supports the Happaugue HVR-950 (USB Tuner).
It's $50 at your local Radio Shack.

I haven't gotten it *working* yet, but at least it autoconfigures which is more than I can say for the earlier releases of MB.

---

### Post by kwilliam on 2008-08-28
> **slickware said:**
> The alpha release of MB 8.1x supports the Happaugue HVR-950 (USB Tuner).
It's $50 at your local Radio Shack.

I haven't gotten it *working* yet, but at least it autoconfigures which is more than I can say for the earlier releases of MB.

Hey, now that's more like it (price wise)! Unfortunately, [some]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_HVR-950") [googling]("http://u32.net/MythTV/WinTV-HVR-950/") [seems]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html") to indicate that getting the analog tuner to work is next to impossible. If you get it working with NTSC analog and write a How To, I could certainly buy one, try it, and if it doesn't work, take it back. I've got a Radio Shack not 10 minutes from my house.

---

### Post by newlinux on 2008-08-28
these are probably harder to find now as most places don't sell them anymore but I use the dvico fusion 5 lite (for analog and digital - but for analog sound you have to connect it to the sound card) and I have 3 kworld aTSC 110/115s (analog and digital as well). Those used to be $40 at newegg but they don't sell them anymore...

---

### Post by kwilliam on 2008-08-28
So far from what I've read, I'm leaning toward a Hauppauge PVR-150, like saxuntu suggested. They seem to be quite popular in the [Please post your Functional/Non Functional Hardware]("http://ubuntuforums.org/showthread.php?t=566529") thread. It's analog only, but has a hardware MPEG-2 encoder, and there's a ton of them on Ebay.

---

### Post by newlinux on 2008-08-28
If what you want is analog only they are pretty much the defacto standard. I have one of those too.

---

### Post by slickware on 2008-08-28
> **kwilliam said:**
> Hey, now that's more like it (price wise)! Unfortunately, [some]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_HVR-950") [googling]("http://u32.net/MythTV/WinTV-HVR-950/") [seems]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html") to indicate that getting the analog tuner to work is next to impossible. If you get it working with NTSC analog and write a How To, I could certainly buy one, try it, and if it doesn't work, take it back. I've got a Radio Shack not 10 minutes from my house.

Do you know how long I googled for to find that it was even supported? Why the hell didn't I find any of those links yesterday before I bought the frigging thing! Ugh. 
You're right, I'm trying desperately to get it to tune now, and failing everywhere.
I just get "no signal" timeouts on every scan.

---

### Post by kwilliam on 2008-08-28
> **slickware said:**
> Do you know how long I googled for to find that it was even supported? Why the hell didn't I find any of those links yesterday before I bought the frigging thing! Ugh. 
You're right, I'm trying desperately to get it to tune now, and failing everywhere.
I just get "no signal" timeouts on every scan.

That's what happens to me every time with my ATI HDTV Wonder card. (And I was bummed, because before I bought it, I googled to check Linux compatibility too.) I just didn't google enough!

Well, I've bought a Hauppauge PVR-150 from ebay. I got one new for $32.50 USD, which fits my budget pretty well. In case anybody else wants one, just search "PVR-150" on ebay. At least [one vendor]("http://cgi.ebay.com/Hauppauge-WinTV-PVR-150-MCE-NTSC-TV-FM-card-XP-Vis_W0QQitemZ160276993027QQcmdZViewItem") has seven used cards that he's selling "Buy it Now" for $30. (I opted to bid on a new one that was factory sealed, but I would have bought a used one if I was out-bid.) Hopefully it'll work!!! 

Now, can anybody recommend a video card? Using the "sis" driver I get black fuzzy lines, so I don't think the onboard graphics are an option. Using the "vesa" driver, MythTV's internal DVD player is unbearably choppy, and VLC seems to reduce the color quality in order to play smoothly. It would be *really* nice if the video card had a coax output that I could connect directly to an old TV screen. If not, maybe they make VGA to coax adaptors?

---

### Post by sloggerkhan on 2008-08-29
I've see if you can get a  graphics card for $20 or so on the cheap (You can get quite decent new one for $50-100). Anything ati x series or nvidia 7000 series and newer or so will probably help drastically.

If you get a newer card, for a desktop, and you value vid playback, I endorse ATI cards. Open driver will be okay, and fglrx driver can be quite good depending on overlay chosen. Plus ATI is now putting quite a bit of work in their cards and nVidia doesn't seem to be.

---

### Post by kwilliam on 2008-09-05
The Hauppauge PVR-150 card works great after I reinstalled Mythbuntu. (I'd screwed it up too much compiling kernels, etcetera.) Was recognized out-of-the-box, although I tried to configure it as a V4L card first and got worried when that didn't work, until I realized it's a DVB card. Then it worked right away. Easy as pie to set it to record shows!

I got an ATI X700 from Ebay, and that works well with the open source driver, but the video playback freezes after 1/2 second when using the proprietary driver. Go figure. Since I don't need 3D for MythTV, I guess the open source driver suits my needs. Plus, maybe I'll have a better chance of suspend working by eschewing those proprietary drivers.

I found a 20" CRT monitor for $15 on Craigslist. (Great place to find stuff. People are selling their old computers for like $50. Wish I'd looked there earlier - I paid that much just for a new case and power supply!) Now, I'm just waiting for my MCE remote, and it'll be done!

---

### Post by sloggerkhan on 2008-09-06
Hey, I've got an x700 and if configured right, it should work great for video playback.

The way I usually do this is to install the proprietary driver (which isn't to say open source won't work, for all I know open source is quite decent), which does work if installed correctly and you have the correct video overlay set (important).

The correct way to do a good ATI fglrx install is to take a fresh install, or an ubuntu with the open source driver after purging the installed repo fglrx, and then download the fglrx driver from ATI's website.

Run the installer with the --buildpkg ubuntu/hardy (this might be slightly wrong, but if you look it up, it will build *.deb files that you then click to install.) In order to install properly, you will also need to install a number of dependancies from synaptic (look this up, too). Once installed, run aticonfig initial command (anticonfig help will give you more info). After you've verified that you I using the driver, you should have decent video playback. 

Set the video overlay in your player to use xv (decent) or opengl (must have compiz off, and requires more CPU but has nearly perfect upscaling).

---

### Post by kwilliam on 2008-09-06
> **sloggerkhan said:**
> Hey, I've got an x700 and if configured right, it should work great for video playback.

The way I usually do this is to install the proprietary driver (which isn't to say open source won't work, for all I know open source is quite decent), which does work if installed correctly and you have the correct video overlay set (important).

The correct way to do a good ATI fglrx install is to take a fresh install, or an ubuntu with the open source driver after purging the installed repo fglrx, and then download the fglrx driver from ATI's website.

Run the installer with the --buildpkg ubuntu/hardy (this might be slightly wrong, but if you look it up, it will build *.deb files that you then click to install.) In order to install properly, you will also need to install a number of dependancies from synaptic (look this up, too). Once installed, run aticonfig initial command (anticonfig help will give you more info). After you've verified that you I using the driver, you should have decent video playback. 

Set the video overlay in your player to use xv (decent) or opengl (must have compiz off, and requires more CPU but has nearly perfect upscaling).

Hey, I'll look into that tomorrow. In the mean time, I've found that DVD playback is pretty poor - I tried watching a DVD with my family and they finally forced me to put it in our old DVD player because there were too many random freezes and glitches. I think the "Internal" MythTV player is to blame here, as playing the DVD with VLC or Xine works well (mplayer crashes for some reason). Perhaps the Internal player is optimized for high end media machines, with the proprietary graphics driver and OpenGL? I wouldn't blame them. I'll try installing the driver the way you suggested and see if the helps. If not, I'll configure Xine to be the DVD player for MythTV.

---

### Post by sloggerkhan on 2008-09-07
xine is easily the best DVD player for linux IMO. Great support for menus and everything. On my comp, I use xine for dvd, smplayer for everything else. I find that the normal mplayer gui doesn't function very well, though the smplayer gui does.

One other thing worth mentioning is that if you have to upscale, the gstreamer framework seems to work rather poorly.

---

### Post by kwilliam on 2008-09-08
I installed the ATI driver again from the Mythbuntu Control Centre, and this time, followed the instructions on [http://www.mythtv.org/wiki/index.php/ATI_Proprietary_Driver](http://www.mythtv.org/wiki/index.php/ATI_Proprietary_Driver) to add
```
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
```
to the Device section of xorg.conf and now video playback works. However, DVD playback is identical to using the open driver, leading me to conclude that the Internal player just isn't up to par with Xine. In fact, of the internal player, VLC, and Xine, Xine is the only one that gets the DVD menu structure of *Taxi Driver* correct. (Taxi Driver is just some DVD from blockbuster, and I suspect is inefficiently encoded and possibly has a quirky menu structure - nontheless just as web browsers must deal with poorly coded web pages, DVD players must work with real world DVD's.) Therefore, I'll just configure Xine for DVD playback - a small price to pay I suppose.

---

### Post by sloggerkhan on 2008-09-08
Yeah, I have no idea about myth's dvd library, but in my experience xine is the only player that does a good job of dvd menus.

What quality of playback do you get using the opengl overlay and not the xv overlay (compositing/compiz must be off for this.)?

---

### Post by kwilliam on 2008-09-10
> **sloggerkhan said:**
> Yeah, I have no idea about myth's dvd library, but in my experience xine is the only player that does a good job of dvd menus.

What quality of playback do you get using the opengl overlay and not the xv overlay (compositing/compiz must be off for this.)?

I'm not sure what you mean, is the xv overlay the same as video overlay? Compiz isn't installed, by the way, since Mythbuntu just installs a basic XFCE desktop by default. Since I'm not playing any HD content at this point, I don't notice any performance difference between the open driver, the proprietary driver, or any of the overlay settings - they all look good (with xine). Might be more noticeable with HD, but I don't know.

---

### Post by sloggerkhan on 2008-09-10
xv and video overlay are probably the same.

The biggest performance differences (IMO) aren't so much in playback as upscaling quality. If you don't have a monitor bigger than 1440x900, you will probably not notice the vast differences in upscale quality.

When it gets to HD, it doesn't matter what you use because the bottleneck will be your cpu's stream decode, not the gpu's render + upscale.

---

