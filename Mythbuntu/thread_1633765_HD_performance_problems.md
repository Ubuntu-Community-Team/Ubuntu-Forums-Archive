---
title: "HD performance problems"
date: 2010-11-29
forum: Mythbuntu
---

### Post by stupots on 2010-11-29
Hi All,

I've scoured loads of Ubuntu, MythTV and Mythbuntu forums without finding any real answers.  Have got to the stage of needing someone with more experience pointing me in the right direction.

I've installed Mythbuntu 10.10 as a backend and frontend on a Dell Dimension C521.  The CPU is an Athlon 64 X2 4800 and the graphics card is an AGP Radeon X1300 Pro.  I've got a TBS 6920 as my tuner and am using a SB Audigy with an SPDIF to my DTS/DD amp.

Whenever I try to play an HD channel, such as BBC HD, it stutters every second or so.  The same thing happens with content from an HD camcorder or MKV files that are 1080i (X264 encoding).

If I try 720p content, it works just fine yet at 1080i top shows a single process running around 105% CPU.  I get the same behaviour on any version of Mythbuntu from 9.04, irrespective of 32 or 64 bit versions.  I've even tried recording HD content with Mythfrontend shutdown but get the same issue on playback.

I've experimented with the 200-line kernel patch, CPU governors and min frequency settings, tried to install the fglrx-dev package (in case open-source ATI drivers are too inefficient but cannot get it working), playback profiles etc, but no luck.  About the only thing I haven't tried is disabling Cool 'n' quiet in the BIOS.

So I have the following questions:

1) Is this hardware just not powerful enough for 1080i?

2) Would an alternative distro that would support FGLRX likely to make any difference?

3) Would ditching Mythbuntu for Gentoo make any significant difference?

4) How do you enable GDM after installing the packages (so I can install the CPU frequency scaling monitor to check I'm running the CPU at 100%)

Thanks for any advice.

Regards,
Stuart

---

### Post by ian dobson on 2010-11-29
Hi,

With regards to BBC HD or playing any 1080i material for that matter requires alot of CPU resources and I imagine your CPU isn't fast enough. That said if you can get a NVIDIA card that supports VDPAU (hardware decoding of video on the graphic card) you can get away with a slow CPU as all the processing happend on the graphic card.

My frontend in an underclocked C2D that sits at 1200MHz most of the time (even when playing back 1080i video) as the graphic card (NVIDIA 9600) does most of the processing.

I don't know if there is such a thing as a AGP NVIDIA card that supports VDPAU.

Regards
Ian Dobson

---

### Post by LowSky on 2010-11-30
Accrdoing to this link Ian this PC is equipted witha PCIe x16 

[http://www.dell.com/us/en/dfh/desktops/dimen_c521/pd.aspx?refid=dimen_c521&s=dfh&cs=22&~tab=specstab](http://www.dell.com/us/en/dfh/desktops/dimen_c521/pd.aspx?refid=dimen_c521&s=dfh&cs=22&~tab=specstab)

A low profile graphics card like a Nvidia 9400 or better would fix the playback issue at hand. Its a simple and can be very cheap fix to that aging computer.
like these
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348%20600001667%20600007321%20600007779&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=20](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348%20600001667%20600007321%20600007779&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=20)

---

### Post by ian dobson on 2010-11-30
> **LowSky said:**
> Accrdoing to this link Ian this PC is equipted witha PCIe x16 

[http://www.dell.com/us/en/dfh/desktops/dimen_c521/pd.aspx?refid=dimen_c521&s=dfh&cs=22&~tab=specstab](http://www.dell.com/us/en/dfh/desktops/dimen_c521/pd.aspx?refid=dimen_c521&s=dfh&cs=22&~tab=specstab)

A low profile graphics card like a Nvidia 9400 or better would fix the playback issue at hand. Its a simple and can be very cheap fix to that aging computer.
like these
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348%20600001667%20600007321%20600007779&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=20](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348%20600001667%20600007321%20600007779&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=20)

Hi, I just went by what stupots wrote "graphics card is an AGP Radeon X1300 Pro".

Regards
Ian Dobson

---

### Post by stupots on 2010-11-30
> **LowSky said:**
> Accrdoing to this link Ian this PC is equipted witha PCIe x16 

Great!  If you can just find me an AGP DVB-S2 card to replace the TBS 6920 that's currently in the PCIe slot I'll be set!!

So is there a really significant difference in CPU overhead between 720p and 1080i?

Regards,
Stuart

---

### Post by matt_symes on 2010-11-30
Hi

> So is there a really significant difference in CPU overhead between 720p and 1080i?Yes. 720p is progressive and 1080i is interlaced. So to display 1080i on an LCD it has to be deinterlaced and that requires using a deinterlace fiilter such as (quick but introduces artefacts) line doubling or (slower depending on the algorithm, introduces other artifacts such as ghosting) some interpolation such as yadiff.

The video needs to be converted to progressive to be displayed on any computer monitor. TV (CRT) has traditionally used interlaced. I.E. odd lines are sent and then even lines are sent. Also you might very well be looking at colour conversion from YCbCr to RGB (or other format to RGB).

Kind regards

---

### Post by LowSky on 2010-11-30
> **stupots said:**
> Great!  If you can just find me an AGP DVB-S2 card to replace the TBS 6920 that's currently in the PCIe slot I'll be set!!

So is there a really significant difference in CPU overhead between 720p and 1080i?

Regards,
Stuart
> 
Expansion Slots
PCI: 1 Slots
PCIe x1: 1 Slot
PCIe x16 (Graphics): 1 Slots
let me explain this better from the model you stated and i looked up
you dont have a agp slot. you have a pci, pcie x16 and pcie x1
your video card is in the pcie x16
your tuner is in the pci
im guessing nothing is in the pcie x1

and if you wanted to replace you tuner many are now pcie x1

---

### Post by rykel on 2010-12-01
The funny thing is, when I use the official NVIDIA driver in Maverick, .mkv files play choppy. But when I remove the driver and use the non-3D open source driver instead, I have no more problem with the files.

---

### Post by stupots on 2010-12-01
> **LowSky said:**
> let me explain this better from the model you stated and i looked up
you dont have a agp slot. you have a pci, pcie x16 and pcie x1
your video card is in the pcie x16
your tuner is in the pci
im guessing nothing is in the pcie x1


Well, I have to eat humble pie.  You are correct that the Radeon is PCIe 16x and not AGP.

Ordinarily, I'd be pissed that the machine was described wrong on eBay, but under the circumstances, this is a slight blessing in disguise.  Because it already had the Audigy (in PCI slot) and the TBS card (in PCIe 1x slot), I haven't had to open the case, so genuinely believed this was correct.

I *had* already researched AGP Nvidia graphics cards for the hardware offloading, but from memory, I think they only go up to the 7xxx series, which are not supported, plus this is a SFF case which limits the choice of card.

Thanks for all the advice.

Regards,
Stuart

---

### Post by Lem on 2010-12-01
To put this into context;

I have a Nvidia Ion board with a single core Atom CPU.
Plays BBC HD perfectly.

Nvidia + VDPAU is the way to go.

---

