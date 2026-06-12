---
title: "fglrx, Ubuntu 10.04.2 x64, 1080p and vaapi ?"
date: 2011-07-20
forum: Multimedia Software
---

### Post by HolgerB on 2011-07-20
Hi all,

I've attached my old Ubuntu 10.04.2 server to my 32" TV. Mainly to watch HDTV but also for gaming.

This are the hardware specs:
Opteron 170 (2x2GHz)
3 GB RAM
ATI HD4670 with fglrx V11.x

When watching 720p content everything is fine. When I playback 1080p content (youtube downloads, shrinked bluerays, etc) there is some "tearing" effect. It's hard to explain but it looks as some parts of the image are rendered from the previous frame. The CPU load does not show "overload". To my best understanding the CPU should not be the limiting factor here. Any desktop effects are disabled.

I tried Mplayer as well as VLC but the effect stays the same. After some googling I found several pages / threads referencing va-api / libva. I found several deb packages of lib in the www but none of them matched my fglrx version. I upgraded to a newer fglrx version via xorg edgers ppa. The effect stayed the same: No installaion of libva.

I guess using libva together with VLC would fix my tearing issues. Has anyone of you got fglrx running up nicely in Ubuntu 10.04 together with libva for GPU-based decoding of h264 content ?
Is an ATI card an option at all or should I grab a NVidia card from the bay to use VPDAU ?

TIA,
Holger

---

### Post by Grenage on 2011-07-20
> **HolgerB said:**
> Hi all,

I've attached my old Ubuntu 10.04.2 server to my 32" TV. Mainly to watch HDTV but also for gaming.

This are the hardware specs:
Opteron 170 (2x2GHz)
3 GB RAM
ATI HD4670 with fglrx V11.x

When watching 720p content everything is fine. When I playback 1080p content (youtube downloads, shrinked bluerays, etc) there is some "tearing" effect. It's hard to explain but it looks as some parts of the image are rendered from the previous frame. The CPU load does not show "overload". To my best understanding the CPU should not be the limiting factor here. Any desktop effects are disabled.

I tried Mplayer as well as VLC but the effect stays the same. After some googling I found several pages / threads referencing va-api / libva. I found several deb packages of lib in the www but none of them matched my fglrx version. I upgraded to a newer fglrx version via xorg edgers ppa. The effect stayed the same: No installaion of libva.

I guess using libva together with VLC would fix my tearing issues. Has anyone of you got fglrx running up nicely in Ubuntu 10.04 together with libva for GPU-based decoding of h264 content ?
Is an ATI card an option at all or should I grab a NVidia card from the bay to use VPDAU ?

TIA,
Holger

I have a similar configuration with XBMC, and I initially encountered the tearing problem.  Thankfully the problem went away after forcing Vsync.  The VAAPI isn't great, but it does work for the most part; the only reason I'm using the ATI card is because it was free.

Failing that, the open source drivers may be an option.  You'll lose hardware acceleration, but your CPUs should be man enough for 1080, I think.

---

### Post by inobe on 2011-07-20
i don't use ati cards, after a quick search, i found that the control center has a tear free function.

[http://ubuntuforums.org/showpost.php?p=10566446&postcount=1](http://ubuntuforums.org/showpost.php?p=10566446&postcount=1)

in my honest opinion, why would anyone want such a feature, just a thought.

---

### Post by HolgerB on 2011-07-20
Thanks for all replies so far.

@Grenage: 
Ok, that confirms the impression I got from reading various websites on VAAPI. It somewhat works but is not perfect. A Debian wiki article on building a HTPC mentioned that one should get a more recent NVidia card in order to use VPDAU which seems to work much better than VAAPI. Yes, to my best understanding my CPU should be sufficent to decode 1080p stuff without hickup and GPU supported decoding. The "only" thing which hurts is this "tearing". Using radeon as driver is unfortunately no option since I rely on 3D acceleration for gaming (both native and WINE). I have experimented a lot with the radeon under arch64 and it is much more mature than nouveau currently is but unfortunately still no match to fglrx.

@inobe: Thanks for pointing out. I have read about this "tear free" function in the arch wiki but as it seems one needs to have the catalyst version 11.1 for this. Mine is a bit older. I will try out the most recent version.
Another hint was to enable 3D vsync and use OpenGL video output (didn't help here). 

After reading the last two days I guess my options are clear:
- Install the latest Catalyst from the ATI/AMD page and see if tear free helps
- If the newest catalyst does not help out I could crosscheck with my old GeForce 7900GS if the tearing is gone
- If neither of the above helps I need to go out and buy a newer GeForce (> 8800 GT) used at the bay.

I will report back.

Thanks again to everyone.

Edit: OK, I installed the latest catalyst to get this tearing fix entry.
Hm, the results are mixed: 
Enable the tearing fix gives me...well...tearing free video in 1080p played back in VLC **but** now the video seems to stutter. I checked both cores and there still seems to be enough CPU power left. Disabling the tearing fix, enabling 3D vsync and switching VLC to OpenGL video output gives tearing free video in 1080p but there are decoding issues. I guess I will dust off my old GeForce 7900GS and see if this card works. 

To my best knowledge I will never give someone the advice to get an ATI card under Linux for anything beside 2D :(

---

### Post by inobe on 2011-07-20
a thread that may interest you.

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)


the last few posts talks a lot of tear free.

thought it would shed light on the matter, at least what folks think and the recent changes.

---

### Post by HolgerB on 2011-07-21
@Inobe: Thanks for pointing out the thread.

After (some more) investigation it looks like this:
fglrx lacks vsync-synchronisation for xv (= X-Windows Video extensions). I found two years old thread on this topic. If ones googles for "ATI fglrx tearing" there are a lot of peoples complaining. OpenGL video output in VLC and VSync enabled gives tearing-free video (obvious since we enabled vertical synchronisation which is causing the issue) but OpenGL video performs somewhat worse compared to standard xv.

I swapped my HD4670 against my old GeForce 7900GS et voilà: No tearing anymore.
CPU-load hovers around 70-90% when using VLC for 1080p videos. If my 7900GS is able to cope with my latest games (e.g. Shadowground Survivors, Amnesia, Torchlight under WINE) in a moderate 16:9 resolution I can life with this solution. Otherwise I will watch out for a GeForce 250 at the bay.

Really "great" that ATI/AMD is still not able to fix stuff. Esp. since this issue exists since 2-3 years. That is really the biggest disappointment since they decided to drop support for my old but performant X1900XTX. Unless the radeon driver get more mature 3D functionality which allows to play both native and Windows-based games under WINE, I will clearly stay away from ATI under Linux.

The radeon driver has really made big progress in the last year but unfortunately they are still not up with fglrx. Neither performancewise, nor from a feature set standpoint.

---

### Post by Grenage on 2011-07-21
> **HolgerB said:**
> I will clearly stay away from ATI under Linux.

That's what I now do.  It's currently a question of go ATI and probably get headaches, or Nvidia and probably be fine.  ATI fanboys will obviously disagree and champion the open driver.

Out of curiosity, where are you based?  I might have an old 9600GTX knocking around.

---

### Post by HolgerB on 2011-07-21
> **Grenage said:**
> That's what I now do.  It's currently a question of go ATI and probably get headaches, or Nvidia and probably be fine.  ATI fanboys will obviously disagree and champion the open driver.

Well, ATI often has had cards which are either cheaper than the NVidia pendant or provide better performance (e.g. HD4670 vs. GeForce 9600GSO/GT). On the negative side for Linux we have: 
- Sometimes cumbersome installation of fglrx
- Delayed fglrx updates in order to support the latest kernel, xserver and so on
- No vsync support for XV since several years
- Mediocre GPU-decoding acceleration for h264 versus a well working open source part for NVidia (VPDAU)

As I pointed out I really spent a lot of time testing my HD4670 with the radeon driver under arch64. It is impressive to see the progress but one does not need to be a rocket scientist to see that they will have to battle newer chip feature versus enhancing the stuff for older chips.

> **Grenage said:**
> 
Out of curiosity, where are you based?  I might have an old 9600GTX knocking around.
Thanks for the offer but I guess sending a package from UK to Germany is a bit expensive, isn' t it ? :)

---

### Post by Grenage on 2011-07-21
> **HolgerB said:**
> Thanks for the offer but I guess sending a package from UK to Germany is a bit expensive, isn' t it ? :)

Well as it wouldn't need to be registered, nor next day, I can't imagine it being much more than a £2.60 or so.  It's only going to die a lingering death in a draw, so the offer is there. :)

---

### Post by inobe on 2011-07-21
> **HolgerB said:**
> @Inobe:

I swapped my HD4670 against my old GeForce 7900GS et voilà: No tearing anymore.
CPU-load hovers around 70-90% when using VLC for 1080p videos.

that isn't bad at all considering vdpau is only supported on 8xx series gpu's and up.

prior to my gtx 460 2gig card the system sported a pny 9800gt, which was an upgrade from a 6 series card, the difference in video quality and performance were night and day.

as for ati, something isn't quite rite, it's always, from day one given problems, it's reputation has prevented me from even considering to a purchase.

---

### Post by .... on 2011-07-22
For va-api on Lucid, you'll need libva and xvba-video from: [http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)
Then you need to rebuild VLC or some other player like mplayer-vaapi. There's a PPA with all of this done, but it doesn't have Lucid versions. I e-mailed the maintainer a while back, but no response. I'll try again.

---

### Post by .... on 2011-07-22
I guess libva is in the middle of merging the work from SDS, so that is holding things up.. [https://bugs.freedesktop.org/show_bug.cgi?id=37656](https://bugs.freedesktop.org/show_bug.cgi?id=37656)

---

