---
title: "Mythtv"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by scottishnarn on 2007-01-28
I have a mythtv system with two capture cards (a WinTV PVR 150 and an Avermedia DVB-T 777) and an nvidia 4MX AGP. 

Using 6.06 it all works perfectly apart from the fact that if I try to record on both devices at once the DVB card cuts out after around 5mins (same thing happens with picture in picture). I believe this issue is a driver one that is specific to either that version of IVTV or the kernel. I get the same issue with PCLinuxOS which uses the same kernel version.

When using 6.10 both cards will record quite happily at the same time, however, when playing back video it is jerky. I get short pauses around every 1-3 seconds. This is using exactly the same settings as for 6.06 where it worked perfectly. (I use XvMC, with BOB antialiasing but the effect is there to a greater or lesser extent and sometimes with lip sync issues for all the options). The effect is more pronouced when using TV out then when on a monitor, so I assumed it was graphic card related so I tried it with a GeForce 6600 GT AGP from another computer I had, with the same results. 

Any ideas?

Thanks

---

### Post by Dubstar_04 on 2007-01-30
I am suffering the same issues at the moment. I am just using on board video which sounds crazy i know but it played perfectly in mythdora so it must be a driver or setting issue!!

Someone help us!!

---

### Post by Dubstar_04 on 2007-01-31
Please can anyone offer any advice??   I'm really stuck with it now and im desperate to move on in my mythtv box development!!

I can see the tv show its just that they are really jumpy and jerky!! I think I need to 

> sudo dpkg-reconfigure xserver-xorg

and remove the video buffer option or attempt to use different drivers, but I'm not sure what difference this will make.

If anyone can offer any advice at all I will be truely grateful!!

P.S. I'm a long time user of windows mce, and windows xp + media portal and im ready for a change. Anyone know if there will be any new animations / rendering effects / eye candy in the mythtv 0.21 release?

---

### Post by Vincent_Lin on 2007-01-31
I am using NVidia driver on a 6800 card, connected to a TV via component cable to the TV out port.  When xvmc is enabled along with bob deinterlacing, I have jumppy audio and video on both live TV and recorded TV, all ATSC at 1920x1080.

For me, I simply disable xvmc and use Standard for TV play-back, and use kernel deinterlacing option, which gives me a very good 1920x1080 picture.

I am not sure who is to blame, but most likely it is caused either by NVidia driver, or mythtv codes, since I can enable xvmc in mplayer for smooth mpeg2 playing.

If you enable OpenGL rendering for myth, you can have picture slideshow with an amazing transision effect, if this what you are looking for.

So far so good, I can confidently say so.  When new mythtv comes out, I am sure I will upgrade it in no time.

Vincent Lin

---

### Post by majoridiot on 2007-01-31
> **Vincent_Lin said:**
> I am not sure who is to blame, but most likely it is caused either by NVidia driver, or mythtv codes, since I can enable xvmc in mplayer for smooth mpeg2 playing.

it could very well be that you are overloading your processor.  bob deinterlacing takes quite
a bit of horsepower to run smoothly.

---

### Post by Dubstar_04 on 2007-01-31
> **Vincent_Lin said:**
> 

For me, I simply disable xvmc and use Standard for TV play-back, and use kernel deinterlacing option

How do I do this?? 

I am currently installing ubuntu on another old machine a P3 1.7GHz with 512mb ram
I am hoping for some success with this one although I still can use my video card as the motherboard has no AGP slot!!! 

Looks like I will have to nuy some now hardware before I can truely meet the potential of mythtv!!

---

### Post by Vincent_Lin on 2007-01-31
To setup what I was talking about, go to General TV playback setup, the first page is where you can specify Preferred MPEG2 Decoder as either xvmc, standard, or libmpeg2.  The same page also gives you options to enable and specify which method/algorithm for deinterlace playback.

I do have the feeling that bob deinterlace is heavy, but the problem is that even if I don't enable deinterlace, using xvmc as my Preferred MPEG2 Decoder already causes autdio stutter and video pause, which are never there when standard decoder or libmpeg2 decoder are used.  

My mythtv setup is on Core Duo 2.13GHz with 2 GB ram and NVidia 6800 vga card.  So I think if the use of bob deinterlace for ATSC/1920x1080 playing brings the quality down to audio stutter and video pauses, especially for my hardware, this is not a practical method at all.  I would rather think that there might be errors somewhere in my system setup, either mythtv, NVidia driver(xorg.conf),or even hidden down there in kernel configurations. 

As I said before, I am currently very happy to have everything working, even not to the possible ultimate setup.  I am not going to spend much more time to figure out why xvmc is not working.  But, I am sure I will jump on the upgrade when mythtv 0.21 is released.  Well, after reading some posts of initial impressions, that is.

Cheers,

Vincent Lin

---

### Post by scottishnarn on 2007-02-01
Just thought I'd fill you in on my next steps. I have a number of ideas to try and thought I might share them since I've run into a little difficulty (my main PC's motherboard stopped working and I don't even want to think about getting mythtv working till that's back up and running) and my mythtv box is used as a mythtv box (despite not being able to use both capture cards at the same time) and therefore I can't reboot and play around all the time, so someone else might try them before I can get to. 

Anyway enough of my woes, here's my ideas.

1. Assume it's some sort of kernel issue either with DVB or IVTV. Rather than wait for a new version of ubuntu or compile my own kernel I'll just try the 64 bit edition and see if that has any luck (not holding out much hope here, but it's worth a try).

2. Assume it's a mythtv problem caused by the particular build from the fixes branch of SVN that was used to build the ubuntu packages (don't even know if it was built from SVN) and so I'll try compiling from source according to the [mythtv website ]("http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation")

I have no idea whether either of these will work but I'll post here with the results, when I eventually get round to doing it.

---

### Post by Dubstar_04 on 2007-02-01
> **scottishnarn said:**
> 

2. Assume it's a mythtv problem caused by the particular build from the fixes branch of SVN that was used to build the ubuntu packages 

Thats a fair point actually. Is everyone who uses mythtv using the ubuntu one, or compiled their own??

---

### Post by scottishnarn on 2007-02-02
OK, the 64 bit solution didn't work. The wintv device appears to work fine but I couldn't get both cards working at the same time. I'm going to try the compiling from source option next.

---

### Post by scottishnarn on 2007-02-03
OK recompiling mythtv didn't work either. I still get jumpy video no matter what settings I use (XvMC or not). It's frustrating I know the hardware is up to it because I have it working using the same version of mythtv using PCLinuxOS and ubuntu 10.4 but they both use the same kernel and I can't get my WinTV card and DVB card to both record at the same time.

---

### Post by Dubstar_04 on 2007-02-04
Let me know how you get on because im still struggling!!

---

### Post by scottishnarn on 2007-02-04
I think it's a kernel version thing, as it all works fine in 6.06 (if you don't want a DVB and an IVTV card working at the same it). So at the moment I'm looking at other distributions using different kernels as I don't want to wait for Feisty Faun. (At the moment it's not going great trying to get my wireless card working, which works perfectly in Ubuntu. It is very frustrating to have to have a network connection to get your network working.)

---

### Post by Dubstar_04 on 2007-02-04
have you tried mythdora? 

[http://g-ding.tv/](http://g-ding.tv/)

My tuners hauppauge hvr 1300s worked fine. The only problem I had was getting the sound working because alsa latched on to the tv tuners input thinking it was a sound card and I could never change it. I even tried installing and configuring with no tv cards in!!

Its always and option!!

---

### Post by barney_1 on 2007-02-05
It is my understanding that for each video encoder card that you have in you mythbox you need to have at least 1ghz of procession power and 512mb of ram.  This means to run two encoders you should have 2ghz and 1gig or ram.  Of course this us just an estimate, but are you on the low side of either of those marks?

If you are, and you have a second box, you can set that up with one card and use it as a slave backend to your master backend.

---

### Post by Erlander on 2007-02-06
> **barney_1 said:**
> It is my understanding that for each video encoder card that you have in you mythbox you need to have at least 1ghz of procession power and 512mb of ram.  This means to run two encoders you should have 2ghz and 1gig or ram.  Of course this us just an estimate, but are you on the low side of either of those marks?


I can't speak for other formats but that formula certainly is not accurate for DVB.  It is broadcast as a mpeg stream and all the capture card and pc does is to copy it requiring very little processing power or memory.  I know of people running 4 or 5 tuners on moderate spec pc's.  A graphics card with hardware acceleration takes care of the decoding for display.

Rob

---

### Post by scottishnarn on 2007-02-06
The hardware is certainly up to it. I used the same setup before I had my WinTV PVR 150 with a software encoder card and used that with my DVB card at the same successfully. In fact with the current setup it works for around 5mins before the DVB card cuts out.

---

### Post by scottishnarn on 2007-02-16
OK, I've finally (after too many reinstalls and other distros and different versions of distros) fixed the problem, I think. I've still got one or two issues to work out before I'm up and running the way I want to be but I fixed the jerkiness problem. So here's how I did it. Now I did a few things and the combination appears to work, but all of them may not be neccessary (it was late, I couldn't be bothered checking one thing at I time, I threw it all at it and hoped for the best). I got help from the [mythtv wiki]("http://www.mythtv.org/wiki/index.php/XvMC"). I'm using edgy.

First up I installed the NVIDIA driver from [NVIDIA's site]("http://www.nvidia.com/object/unix.html") and let the installer reconfigure my /etc/X11/xorg.conf file. I installed the 8776 version from the archive section. [INDENT]*(At the moment, I need to reinstall the driver at every reboot, I think this is because I didn't uninstall the ubuntu NVIDIA drivers first. My next step is to uninstall those drivers and hope that doesn't break anything, if it does I'll run the NVIDIA installer in silent mode in a startup script. I'll let you know how it works when I try it later).*[/INDENT]


Next I edited /etc/X11/XvMCConfig to read ```
libXvMCNVIDIA_dynamic.so.1
``` to use the NVIDIA XvMC. 

Then I edited the /etc/X11/xorg.conf file to add ```
    Option         "NVAGP" "2"
``` The mythtv wiki suggests you may want to try 1 or 2 depending on motherboard but start with 1.

Finally, I ran nvidia-settings and disabled video Texture Adapter and Video Blitter Adapter "Sync to VBlank". However, I don't think this was what did it, I enabled it afterwards and still appears to work, but I mention it just in case it helps anyone else.

---

### Post by Erlander on 2007-02-16
Congratulations.

I've had some success too.

Did another clean install tonight.  About the 5th.

And lo and behold Myth is working.

Video and sound quality seem excellent and my remote that came with the tuner has some functions working.

Don't know what I did that was different.  I guess I just didn't make so many mistakes.

Now to work out what settings I need to change for some customisation

Rob

---

### Post by scottishnarn on 2007-02-20
oops looks like I spoke to soon. In trying to fix the need to reinstall the NVIDIA drivers every time I reboot I installed envy and now it doesn't work again. I've used envy to uninstall the drivers, uninstalled envy and reinstalled the kernel, the restricted modules and glx and then the binary NVIDIA drivers and I still can't get it too work. 

This is so frustrating, it easily works in Dapper (but with only one TV card at a time) but it just will not work in Edgy. Yes, I've tried an upgrade and that didn't work either.

---

### Post by Erlander on 2007-02-20
I will be interested to hear how you get on with this.

I'm planning on replacing my old TNT2 graphics card with a 7600GS.

One of the things holding me back is the worry that I might not be able to get it all going correctly.

Rob

---

### Post by scottishnarn on 2007-02-21
OK, no solution as yet, but a promising lead I hope. Reading the mythtv mailing list and looking at what linux versions I can get to work, I'm wondering if the problem is with xorg 7.1 . However, I've no idea if it is possible to install xorg 6.9 or 7.0 on edgy.

---

### Post by scottishnarn on 2007-02-24
OK, I kind of fixed my problem. "kind of" because although I now have a jerky free bob deinterlaced picture I'm not using XvMC. I discovered on my old system that I wasn't using XvMC at all so I tried disabling it and just using the default decoder. It didn't work immediately but I found a forum which did suggest the fix [http://www.pchdtv.com/forum/viewtopic.php?t=90&sid=8eecea97617fb080a186529154eb04a5](http://www.pchdtv.com/forum/viewtopic.php?t=90&sid=8eecea97617fb080a186529154eb04a5)

Basically I run mythfrontend with nice using ```
nice -1 mythfrontend
``` and it works. As the forum I read mentioned I can see no reason why this should work, but it does. (It suggets nice -10 rather than -1 but I both seem to work and -1 is running at a higher priority so I've gone with that). 

I still can't get XvMC to work properly but then it may just be my GeForce 4MX isn't up to the job and if I can get smooth playback without, then I don't really care other than for pure curiosity and that little bug that knows something is possible and wants to get it working even though I don't need to. 

Anyway, I'll need to run for a few days or so to see if it's stable or not, so I'll post again in a couple of days to let you now.

---

