---
title: "ATI or NVidia on 10.04?"
date: 2010-06-16
forum: Multimedia Software
---

### Post by Muskiet on 2010-06-16
I'm running Ubuntu 10.04 with on-board graphics atm and I'm looking for a cheap video-card to use for watching movies (HULU, DVD's, DivX etc) without the stuttering.
I'm torn between a $30 HD 4350, a $40 HD 4550 or a $35 NVidia 8400 GS (the only "proper" NVidia solution for prices ranging from $30 to $40).
All cards have 512 MB, the 4550 has DDR3.

Trying to find information on how the ATI's handle in Ubuntu only gets me threads about how troublesome they can be in older Ubuntu versions, but I'd like to know if anybody here can give me some information on whether or not 10.04 (32 bit) has a good handle on these cards by now.

Thank you.

---

### Post by Adamal on 2010-06-17
I have used nVidia cards in the past, but my current laptop has ATI.  I can tell you straight out, go nVidia.  ATI driver are terrible.  Right now I can't get dual monitors working at all with my 5730 M.

---

### Post by Linuxforall on 2010-06-17
The 8400 will let you play full screen videos via VDPAU which uses GPU to scale the movie and that way your system CPU won't be taxed, ATI is yet to implement this feature plus many other features.

---

### Post by WinterRain on 2010-06-17
Nvidia.

---

### Post by VastOne on 2010-06-17
I concur with all that has been stated

nVidia...

---

### Post by gradinaruvasile on 2010-06-17
nVidia. Has the best drivers.
Be careful with the 8400 though - only certain versions support VDPAU as far as i know (google for it, it has to have a specific chipset in it).
Better go for a G210 because it has full VDPAU support - i have one and it kicks *** video play with hardware-accelerated VDPAU (uses 1-5% CPU).

Web-based content will still have high CPU usage but that is because of the crappy Flash Player.

---

### Post by xzero1 on 2010-06-17
Before deciding on your purchase, you might want to read this:

[http://www.theinquirer.net/inquirer/news/1137385/nvidia-bad-bumps-worse]("http://www.theinquirer.net/inquirer/news/1137385/nvidia-bad-bumps-worse")

I currently use a hd 4770 with the open source drivers with 10.04 and it performs quite well for video. Flash (64 bit) was working quite well but degraded after the 10.1 upgrade.

---

### Post by Linuxforall on 2010-06-17
> **gradinaruvasile said:**
> nVidia. Has the best drivers.
Be careful with the 8400 though - only certain versions support VDPAU as far as i know (google for it, it has to have a specific chipset in it).
Better go for a G210 because it has full VDPAU support - i have one and it kicks *** video play with hardware-accelerated VDPAU (uses 1-5% CPU).

Web-based content will still have high CPU usage but that is because of the crappy Flash Player.

The issue is with 8800 and not 8400, I have the 8400 with 512mb and VDPAU is fully supported by mplayer and smplayer.

---

### Post by Linuxforall on 2010-06-17
> **xzero1 said:**
> Before deciding on your purchase, you might want to read this:

[http://www.theinquirer.net/inquirer/news/1137385/nvidia-bad-bumps-worse]("http://www.theinquirer.net/inquirer/news/1137385/nvidia-bad-bumps-worse")

I currently use a hd 4770 with the open source drivers with 10.04 and it performs quite well for video. Flash (64 bit) was working quite well but degraded after the 10.1 upgrade.

Bad as it looks, ATI is worse, I have a dual GPU ATI 4850 lying waste due to crappy drivers.

---

### Post by cascade9 on 2010-06-17
> **Linuxforall said:**
> The 8400 will let you play full screen videos via VDPAU which uses GPU to scale the movie and that way your system CPU won't be taxed, ATI is yet to implement this feature plus many other features.

Not true, there is XvBA 

[http://en.wikipedia.org/wiki/X-Video_Bitstream_Acceleration](http://en.wikipedia.org/wiki/X-Video_Bitstream_Acceleration)

[http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1)

Its not as mature, or got as many features as VDPAU AFAIK, but its there....

*edit- BTW, grandinaruvasile has got a point about the GT210, its got a better feature set than the 8400 (8400 = feature set 'a', GT210, feature set 'c')

[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

---

### Post by Muskiet on 2010-06-18
So I guess I shouldn't go for ATI then eh? :p
Well thanx everybody for weighing in on the subject.
As always it's frustrating buying a video card because "oh it's only a couple of dollars more to get a little better" and therefore I went with [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640")'s suggestion and I just ordered an [EVGA Geforce 210]("http://www.buy.com/retail/product.asp?sku=213897885") for $42 with passive cooling because I like 'em silent.
Even though the NVidia's I've owned were always rock solid I guess I've always liked ATI for its better price/performance numbers for Windows but if they suck with Ubuntu there's no sense in me buying one.

I'll keep the thread unsolved until I've installed it and I'll let you all know how well it does the job.

---

### Post by wkulecz on 2010-06-18
I swore off ATI video cards because of all the ophaned cards I ended up with when switching from Windows98 to Windows2000.

Nvidia has never given me a lick of trouble on Windows or Linux, although I've never believed in buying video cards anywhere near the "bleeding edge" of performance.

---

### Post by xzero1 on 2010-06-19
> **Linuxforall said:**
> Bad as it looks, ATI is worse, I have a dual GPU ATI 4850 lying waste due to crappy drivers.

Crappy drivers can be fixed, *defective* hardware is another problem.

---

### Post by Linuxforall on 2010-06-19
> **xzero1 said:**
> Crappy drivers can be fixed, *defective* hardware is another problem.

No fix as the cheaper nvidia would make my dual GPU card look like an ancient Riva TNT.

---

### Post by xzero1 on 2010-06-19
> **Linuxforall said:**
> No fix as the cheaper nvidia would make my dual GPU card look like an ancient Riva TNT.

I take it you did not read the link.

---

### Post by Linuxforall on 2010-06-19
> **xzero1 said:**
> I take it you did not read the link.

[http://www.theinquirer.net/inquirer/news/1137385/nvidia-bad-bumps-worse](http://www.theinquirer.net/inquirer/news/1137385/nvidia-bad-bumps-worse)

Yes I did but that don't excuse **** poor drivers, they really need to shape up their Linux drivers.

---

### Post by waynemeat on 2010-06-19
I'm running an ATI 4870 x2 with manufacturer drivers. My only problem so far is cooling. I have to manually crank up the fan speed in the terminal or else it sits idle at 84 degrees.

---

### Post by Muskiet on 2010-06-24
EVGA Geforce 210 arrived today.
I plugged it in and.... it worked beautifully.
I've installed the drivers via "Administration > Hardware Drivers".
Now I find Hulu and YouTube play full screen without a hitch even though one of the replies suggested there wouldn't be much of a change because of Flash, but I'm a little disappointed that I still cannot watch an HD x264 file as these still have a frame-rate of about 0.2 fps with both Gnome MPlayer and Totem MoviePlayer.

The computer does seem to run smoother though and regular movies play perfectly.
Thanx for all the suggestions.

---

### Post by cascade9 on 2010-06-24
> **Muskiet said:**
>  I'm a little disappointed that I still cannot watch an HD x264 file as these still have a frame-rate of about 0.2 fps with both Gnome MPlayer and Totem MoviePlayer.


Setup VDPAU for your perfered media player, then HD files should be watchable. ;)

---

### Post by Muskiet on 2010-06-24
> **cascade9 said:**
> Setup VDPAU for your perfered media player, then HD files should be watchable. ;)

I set up CoreAVC and things sped up a bit.
I thought VDPAU was something that automatically gets used on the graphics card, but you're saying I need to set it up first?
I've Googled it a bit and found three very confusing ways to set it up under Ubuntu.
Does anybody have a link to another, easier way?

---

### Post by Muskiet on 2010-06-25
Okay... final reply.
I've installed SMPlayer and it turns out that turning on VDPAU support in this program is as simple as selecting VDPAU as the output driver in stead of having to compile the program with VDPAU support as is the case with MPlayer, my previous favorite.
Together with switching on "Direct Rendering" and installing CoreAVC I've now managed to run heavy HD files incredibly smooth on my outdated low-end computer.

Like everything in Ubuntu... it can take a while and a lot of work to get it to work properly... but when it works I love it and won't want anything else.
Thanx all for your input!

---

