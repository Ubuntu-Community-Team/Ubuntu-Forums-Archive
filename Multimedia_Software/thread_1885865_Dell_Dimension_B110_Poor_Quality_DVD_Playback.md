---
title: "Dell Dimension B110 Poor Quality DVD Playback"
date: 2011-11-24
forum: Multimedia Software
---

### Post by aem0512 on 2011-11-24
Hello,

I just installed Xubuntu 11.10 on my mom's dell dimension b110, installed restricted extras, installed libdvdcss2. But the dvd playback is grainy and pinkish (it also looks like there are thin, black horizontal lines across the screen). It definitely doesn't look right.

I've played a couple of youtube videos without the same symptoms so I'm not sure what the problem is. (however, flash videos have slight tearing and 'blinking' effect as though frames are being dropped. I have flash 11.1.102.55.)

I'm somewhat new to linux so please be thorough with instructions if anyone has any ideas on how to fix these ailments Thanks!

lspci:
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by wolfen69 on 2011-11-24
That computer is using a very inadequate video card to begin with. After reading reviews from 6 yrs ago, people were complaining about it back then, running xp. Chances are you will need to add a decent PCI video card to get better graphics performance.

---

### Post by aem0512 on 2011-11-24
Yeah, I figured the integrated graphics card itself would be kinda poor quality. But why would I be getting better video playback in youtube/hulu versus dvd playback? Could it be the dvd drive driver?

Also, I plan to give it a RAM upgrade for Christmas. It's RAM max is only 2gb (according to dell) but it should increase the system speed significantly over the 512 gb it has currently (right?)

Dell also recommends the ATI Radeon™ HD 3450 PCI 512mb DMS59 Graphics card from Visiontek®, but it seems overpriced to me ($140). I also want to make sure I'm getting a card that would be better compatible with Linux. NewEgg has some PCI cards that are more reasonably priced. Have any suggestions? I'd like to stay between $50-75 if it would be worth the upgrade at all for that price.

---

### Post by wolfen69 on 2011-11-24
I would go with [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187041") card. It is only $39. Nvidia generally works well in linux. And yeah, a ram upgrade wouldn't hurt either.

---

### Post by aem0512 on 2011-11-24
Thanks! Appreciate the help.

So somehow my video card is making my dvd playback pinkish in color?

I'm just wondering if the video card will be the fix for that or if it is a dvd drive issue. I'm just confounded as to how video streaming playback could be better quality.

---

### Post by wolfen69 on 2011-11-24
It *could* be an issue with your DVD drive, but the only way to find out would be to swap it out with another one you know works well. DVD playback and streaming videos are *not* the same technically, but you'll just have to try something else. You are already using the best video driver available.

---

