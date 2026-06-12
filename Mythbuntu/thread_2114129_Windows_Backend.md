---
title: "Windows Backend?"
date: 2013-02-09
forum: Mythbuntu
---

### Post by Cebi on 2013-02-09
Hello!

I'm currently running WMC with a BlackGold quad tuner. I want to try out Mythbuntu but I am quite a novice to linux, and the complexity of the tuner driver installation is a step too far. :(

So I thought that running the tuner on a Windows based backend server could be an option, then using Myth as my frontend. 

Am I mad, or is this workable? :confused:

I would really appreciate any help!

Thanks,

Cebi

---

### Post by AlecJ on 2013-02-10
[HTML]http://www.mythtv.org/wiki/MythTV_on_Windows[/HTML]

---

### Post by Cebi on 2013-02-12
> **AlecJ said:**
> [HTML]http://www.mythtv.org/wiki/MythTV_on_Windows[/HTML]

Thanks but from the sounds of it that wouldn't solve the tuner issue I have. I was hoping to use something like XBMC as the backend, and then Mythbuntu as the frontend.

---

### Post by AlecJ on 2013-02-12
> **Cebi said:**
> Thanks but from the sounds of it that wouldn't solve the tuner issue I have. I was hoping to use something like XBMC as the backend, and then Mythbuntu as the frontend.

I know it works the other way, mythbackend, xmbc frontend, even on a Rasberry Pi now.

Installing tuner firmware is quite easy, I have to install firmware for my TBS cards.

is there firmware/driver for Blackgold cards? I still have an old DVB-T somewhere gave up as no firmware for it.

---

### Post by Cebi on 2013-02-12
> **AlecJ said:**
> I know it works the other way, mythbackend, xmbc frontend, even on a Rasberry Pi now.

Installing tuner firmware is quite easy, I have to install firmware for my TBS cards.

is there firmware/driver for Blackgold cards? I still have an old DVB-T somewhere gave up as no firmware for it.

It's the driver that's the issue. Blackgold are well known for their poor linux driver support, apparently. I have to build the entire driver myself, which is difficult enough given my limited experience, and I'm not even sure it will work with my exact version. Then there is all the hassle of updates messing them up even if I DO get them working. I have tried, no luck. 

On the other hand the Win drivers are just a couple of clicks.

---

### Post by AlecJ on 2013-02-12
[http://shop.blackgold.tv/epages/BT3159.sf/en_AU/?ObjectPath=/Shops/BT3159/Categories/Support/Current_Drivers](http://shop.blackgold.tv/epages/BT3159.sf/en_AU/?ObjectPath=/Shops/BT3159/Categories/Support/Current_Drivers)

don't look to bad, if you have a spare hard drive you can swap out and try with mythbuntu 12.04 .25

once working don't update, until the kernel has the firmware, which looks like it could be soon?

---

### Post by nickrout on 2013-02-12
> **Cebi said:**
> Thanks but from the sounds of it that wouldn't solve the tuner issue I have. I was hoping to use something like XBMC as the backend, and then Mythbuntu as the frontend.xbmc does not record tv, it has no recording facilities. 

blackgold linux drivers I think are not compatible with mythtv.

---

### Post by klc5555 on 2013-02-12
> **nickrout said:**
> xbmc does not record tv, it has no recording facilities. 

blackgold linux drivers I think are not compatible with mythtv.

XBMC 12.0 has newly incorporated PVR frontend support for a variety of backends. In Linux, for example, TVheadend and VDR are supported as well as Mythbackend. There are at least four Windows backends supported, including ArgusTV, NextPVR, DVBLink and MediaPortal. Check the XBMC wiki for [http://wiki.xbmc.org/index.php?title=PVR](http://wiki.xbmc.org/index.php?title=PVR) and [http://wiki.xbmc.org/index.php?title=PVR/Backend](http://wiki.xbmc.org/index.php?title=PVR/Backend)

I find the integrated PVR interface in XBMC Frodo to be more than a bit primitive, not only compared to the (evidently discontinued) Mythbox addon, but also even with plain vanilla Mythfrontend. But the devs have to start somewhere, and the OP might find something here that's functional enough to meet his needs.

---

### Post by nickrout on 2013-02-12
I am aware of the xbmc pvr addons, but none of them detract from the propositin that xbmc doesn't record anything. It is merely a frontend.

---

### Post by klc5555 on 2013-02-13
> **nickrout said:**
> I am aware of the xbmc pvr addons, but none of them detract from the propositin that xbmc doesn't record anything. It is merely a frontend.

Agreed. But the point is that the OP can have a Windows backend using Windows drivers for his tuners and have Linux frontends if he really wants to. Just not with Mythtv.

---

### Post by nickrout on 2013-02-13
Sure if any of the windows backend software works with those cards - I have simply no idea!

---

### Post by Cebi on 2013-02-15
> **klc5555 said:**
> XBMC 12.0 has newly incorporated PVR frontend support for a variety of backends. In Linux, for example, TVheadend and VDR are supported as well as Mythbackend. There are at least four Windows backends supported, including ArgusTV, NextPVR, DVBLink and MediaPortal. Check the XBMC wiki for [http://wiki.xbmc.org/index.php?title=PVR](http://wiki.xbmc.org/index.php?title=PVR) and [http://wiki.xbmc.org/index.php?title=PVR/Backend](http://wiki.xbmc.org/index.php?title=PVR/Backend)

I find the integrated PVR interface in XBMC Frodo to be more than a bit primitive, not only compared to the (evidently discontinued) Mythbox addon, but also even with plain vanilla Mythfrontend. But the devs have to start somewhere, and the OP might find something here that's functional enough to meet his needs.

Any idea if these backends would then be compatible with a Mythbuntu frontend? I have no idea how they go about talking to each other... is their a standardized protocol for backend-frontend interaction?

---

### Post by klc5555 on 2013-02-15
Mythfrontend only talks to Mythbackend. It was never intended to be independent. A description of the Myth Protocol may be found here: [http://www.mythtv.org/wiki/Myth_Protocol/Guide](http://www.mythtv.org/wiki/Myth_Protocol/Guide) 

If you use a backend other than Mythbackend, you'll need to use another frontend that supports that backend. Mythfrontend by itself will not be an option.

---

### Post by Cebi on 2013-02-15
> **klc5555 said:**
> Mythfrontend only talks to Mythbackend. It was never intended to be independent. A description of the Myth Protocol may be found here: [http://www.mythtv.org/wiki/Myth_Protocol/Guide](http://www.mythtv.org/wiki/Myth_Protocol/Guide) 

If you use a backend other than Mythbackend, you'll need to use another frontend that supports that backend. Mythfrontend by itself will not be an option.

Thanks!

---

