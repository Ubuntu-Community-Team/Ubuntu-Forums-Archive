---
title: "Hauppage WinTV-HVR 950Q"
date: 2010-02-08
forum: Multimedia Software
---

### Post by rflores2323 on 2010-02-08
I am thinking about buying this [B]Hauppage WinTV-HVR 950Q and putting it on my acer revo 3610 that is running ubuntu 9.10.  

I wanted to check if this will work out the box or if there is alot of configuring to do as I am a linux noob.  

I am wanting to run mythtv backend with xbmc frontend for this.  

anyone have a how to on this?  I read here [/B][http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)  that the firmware for the xc5000 is already bundled in  Ubuntu 9.10 (Karmic) includes it by default.

So what do I need to configure this???   Just want to be prepared to see what I am getting myself into.

---

### Post by rflores2323 on 2010-02-09
nobody has this tuner???

---

### Post by rflores2323 on 2010-02-15
anyone ?

---

### Post by wkulecz on 2010-03-11
I just got one.  It plugs into 9.10 and is found, automatically creating /dev/video0.

I can't get any of the HDTV to work, but I haven't tried too hard yet. My interest is capturing 720x480 video from a VCR.  That appears to work in TVtime or VLC, but....  Quality is not so good with a lot of jitter during fast action scenes or fast camera pans (clearly inferior to a BT8x8 capture card on 8.04).  Show stopper for me is in both apps the display goes nuts -- losing sync, color flashes, if I play a black and white (monochrome) tape :(

I did a limited test on Windows7 RC1 (expired, two hour limit) and was less than impressed with the over the air HDTV quality.  I try again this weekend on my "real" Win7 box at home (wanted this for work to capture SVHS & U-matic tapes recorded with a monochrome camera).

Xorg and TV player CPU % seems awfully high in top (AMD Quad core in the 7s on Win7 experience scale for CPU and RAM).  The on the motherboard Nvidia video is not top of the line though, but the 8.04 system is an old 1.4GHz Athelon with a Nvidia 6200 video card and CPU usage seems less and video display quality better :(

Unless it works really well on my real Win7 system, I'll be returning it next week.

--wally.

---

### Post by wkulecz on 2010-03-12
My advice, forget about it.

I installed the w_scan and dvbtools from the 9.10 repos and they don't do anything but throw error messages when trying to scan for ATSC channels.

--wally.

---

### Post by wkulecz on 2010-03-16
Played with it over the weekend at home and it works great in Windows 7 but the install was flakey, only one of my three front accessable USB ports will work with it.  Maybe a power issue as the device gets pretty warm in use.  There was no built-in driver for it in Win7 release, good thing, as the Win7RC1 driver ATSC quality was not very good.

The Composite/S-video inputs are very sensitive to video levels, really only usable after hooking it to my old Sima "Video Color Correction" analog processing box.  The over the air ATSC recordings are great, but it needs a much better antenna than what it comes with.

Discovered I can use it with gstreamer on our old B&W tapes, but I have to hook up via composite but set the driver to use S-video, this removes the color flashing and sync issues.

I've had no luck with it in 9.10 beyond getting images over S-video/Composite.  As I said, the w_scan and dvbtools from repos just throw unhelpful error messages.

I have coded a simple gstreamer pipeline to capture our old B&W tapes so it is useful to me even in its crippled state.  Monochrome capture quality seems good since I stumbled onto the trick to input via composite jack, but record from S-video input channel.  Audio is not used in our application.  The CPU usage in my gstreamer application is much more reasonable (<10%), obviously TVtime and VLC is doing a lot more than just dumping the captures to an Xwindow.

--wally.

---

### Post by Chronon on 2010-03-16
Have you installed linux-firmware-nonfree?  I have the vanilla WinTV-HVR 950 (which might have a different chipset in it) and installing this improved its functionality.  It might be worth a shot.

---

### Post by wkulecz on 2010-03-17
> Have you installed linux-firmware-nonfree?

No I hadn't.  Just did.  

Now I can use the Composite input with the monochrome tapes.  Thanks!

Why is broken firmware included in the 9.10 distribution?   There is nothing in the linux-firmware-nonfree description in Symantic to suggest I might need it, especially since the firmware appeared to be there out of the box.  The 950 and 950Q are different chipsets internally -- at least they changed the name slightly when they changed the chipsets.

To much voodoo here.  I put up with it because having our image processing system on Linux means we can clone it as needed and use very inexpensive hardware, but the video on Linux situation seems to be getting worse and more confused with every release.  If I just wanted to watch/capture TV on my computer I'd have more than paid for a copy of Windows with the time I've wasted dicking around to get this working.

I'm not asking a lot from the video capture driver, but its way harder than it should be.

On Windows, both this 950Q and the HVR-1950 work wondefully.  I couldn't get the 1950 to do anything on 9.10, perhaps it will with this firmware package, what I found via google for it didn't work :(   But I don't see the need to try since the 1950 costs more and the 950Q seems to do what I need.

--wally.

---

### Post by Chronon on 2010-03-19
As is often the case, it comes down to driver availability.  Hopefully the free drivers improve and make the nonfree firmware unnecessary.  To avoid as much voodoo as possible, it's always a good idea to search for hardware that is known to be supported.  ;)

---

