---
title: "Video problem..."
date: 2010-03-22
forum: Multimedia Software
---

### Post by warlord360 on 2010-03-22
Hello,

I installed ubuntu and installed the "recommended" video driver 185 or something and I'm getting this problem: [http://img502.imageshack.us/img502/3985/screenshotgr.png](http://img502.imageshack.us/img502/3985/screenshotgr.png) it can't be my video card since it works on windows xp/7 fine but here it does that..

Heres my uname -a:
Linux justin-desktop 2.6.31-20-generic-pae #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 i686 GNU/Linux

I did upgrade and update with apt-get..

My video card is: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814127464&cm_re=msi_twin-_-14-127-464-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127464&cm_re=msi_twin-_-14-127-464-_-Product)

Any idea on how to fix this? thanks.

---

### Post by warlord360 on 2010-03-23
Any one? -_-

---

### Post by Yellow Pasque on 2010-03-23
What video player are you using? I would suggest you try mplayer and make sure you use the vdpau video output: [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by gradinaruvasile on 2010-03-23
> **warlord360 said:**
> Hello,

I installed ubuntu and installed the "recommended" video driver 185 or something and I'm getting this problem: [http://img502.imageshack.us/img502/3985/screenshotgr.png](http://img502.imageshack.us/img502/3985/screenshotgr.png) it can't be my video card since it works on windows xp/7 fine but here it does that..

Heres my uname -a:
Linux justin-desktop 2.6.31-20-generic-pae #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 i686 GNU/Linux

I did upgrade and update with apt-get..

My video card is: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814127464&cm_re=msi_twin-_-14-127-464-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127464&cm_re=msi_twin-_-14-127-464-_-Product)

Any idea on how to fix this? thanks.

Install the 195 series drivers. "Recommended" driver is the stock driver in Ubuntu repository and its by no means the latest. 185 series are old already.

The latest drivers are 195.36.15 - it is recommended to install these because your video card is new and this driver has many enhancements concerning newer video cards and VDPAU.

On your specific problem: the tearing is constant, meaning it tears the image at that specific spot that shows in that image or is it on random places?
Launch nvidia-settings and make sure that you have "sync to vblank" ticked.

If you use compiz (desktop effects), disable them and try that way.

Also, try smplayer (or vlc) for playback. If you do use VDPAU output, the only way of getting smooth playback without tearing (at least for me) was to disable compositing from xorg.conf.

---

