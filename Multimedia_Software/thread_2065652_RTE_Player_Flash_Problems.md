---
title: "RTE Player Flash Problems"
date: 2012-10-02
forum: Multimedia Software
---

### Post by Noel Furlong on 2012-10-02
I'm running 12.04 and have a problem with the new version of the RTE player, which uses Flash. I've tried Chrome, Firefox and Opera, but all hit the same problem. Audio and Video content won't start and an error message is displayed.

I've also tried the suggested workaround on the RTE website of disabling the Pepper Flash player (/opt/google/chrome/PepperFlash/libpepflashplayer.so - version 11.3.31.331) and enabling the other version of Flash present (/usr/lib/flashplugin-installer/libflashplayer.so - version 11.2 r202), but no matter what combination I try, I can't play videos in the new version of the RTE player. This is a big problem as RTE are switching to this new player on their website at the moment and less and less audio and video content is available on the old format.

I'd be interested if anyone could try out the new version of the player ([www.rte.ie/player](www.rte.ie/player)) and see if it is working for you. A solution to my problem wouldn't be bad either! :)

Thanks,
NF.

---

### Post by Szise on 2012-10-03
Is working, Ubuntu 12.04 LTS, Adobe Flash Plugin , I tested the new player here (Live: Dail Eireann)  [http://www.rte.ie/tvplayer/ro/live/7/](http://www.rte.ie/tvplayer/ro/live/7/)

---

### Post by Noel Furlong on 2012-10-04
> **Szise said:**
> Is working, Ubuntu 12.04 LTS, Adobe Flash Plugin , I tested the new player here (Live: Dail Eireann)  [http://www.rte.ie/tvplayer/ro/live/7/](http://www.rte.ie/tvplayer/ro/live/7/)
Strangely, the live link given above using the new player worked for me, too. The problem continues, however, when trying to view other content e.g. 
[http://www.rte.ie/tvplayer/de/show/10058684/](http://www.rte.ie/tvplayer/de/show/10058684/).

This plays just fine on my windows pc at work, but I get an "uncaught exception" error at home on Ubuntu 12.04. Again, I'd appreciate it if anyone running 12.04 could try the link and, if it works, tell me which browser and flash version you are using.

---

### Post by Trevordo on 2012-10-07
I have the same problem described by the OP using 12.04. I've tried the same solution that was offered and it does not work for me either.  

The live link that was posted in the reply by Szise does work fine but can't view anything that isn't live.  When you click on a show the ads run OK but it then throws up this "UNCAUGHT" error when you'd expect the show itself to start.

---

### Post by davdo2004 on 2012-10-08
> **Noel Furlong said:**
> Strangely, the live link given above using the new player worked for me, too. The problem continues, however, when trying to view other content e.g. 
[http://www.rte.ie/tvplayer/de/show/10058684/](http://www.rte.ie/tvplayer/de/show/10058684/).

This plays just fine on my windows pc at work, but I get an "uncaught exception" error at home on Ubuntu 12.04. Again, I'd appreciate it if anyone running 12.04 could try the link and, if it works, tell me which browser and flash version you are using.

It works fine for me. There may be some sort of drm in the stream. Install 'hal' and give that a try.

---

### Post by Trevordo on 2012-10-08
> **davdo2004 said:**
> It works fine for me. There may be some sort of drm in the stream. Install 'hal' and give that a try.

WOW.  "hal" does indeed seem to fix the problem.  Many thanks. Much appreciated.

---

### Post by Mairin on 2012-10-08
I am pulling my hair out with this new RTE Player.  I get to see a bit of the programme I want to see, then it freezes.  I go back into it and it gives me the option to Resume at whatever minute I was at, which I select.  Then a circle goes around and around until I am blue in the face looking at it so I go back, reselect the programme, click on Resume at whatever minute I was at and off it goes again with the circle and around and around we go in a loop.  Spare me someone from this.  What do I need to do to solve?

---

### Post by Noel Furlong on 2012-10-10
Big thanks to davdo2004 for suggesting to install HAL. The new RTE player now works fine for me. I'm also experiencing quite a lot of buffering as Mairin said above, but I also had the same issues in Vista, so it seems not to be a Ubuntu specific problem.

---

### Post by Trevordo on 2012-10-10
> **Noel Furlong said:**
> Big thanks to davdo2004 for suggesting to install HAL. The new RTE player now works fine for me. I'm also experiencing quite a lot of buffering as Mairin said above, but I also had the same issues in Vista, so it seems not to be a Ubuntu specific problem.

Noel. I've had similar issues on windows and Ubuntu. I'm wondering if it's the stream quality that the new rte player is auto selecting. If its streaming on highest quality try manually switching to a lower stream quality to see if that helps.

---

### Post by Noel Furlong on 2012-10-11
Trevordo: I've tried lowering the stream quality to the other available option, 512K, but it still buffers every couple of minutes or so. When I watch the news on TV3's player, it never buffers for me. I'm based in Germany, but just watch the internationally available content on their player, so there is no issue with using a VPN or anything.

Maybe RTE are still perfecting this and I'm sure they've had a few complaints. Might be worth getting on to them. I'd do it myself but they might have me down as a serial complainer already due to some discussions we've had regarding their internet radio streaming.

---

### Post by Rytron on 2012-12-23
Also try this: [http://www.rte.ie/playerxl/](http://www.rte.ie/playerxl/)

---

