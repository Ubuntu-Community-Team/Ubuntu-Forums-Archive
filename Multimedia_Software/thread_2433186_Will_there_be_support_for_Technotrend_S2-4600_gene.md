---
title: "Will there be support for Technotrend S2-4600 generation 2018+ in Ubuntu 18.04?"
date: 2019-12-15
forum: Multimedia Software
---

### Post by jms-1 on 2019-12-15
I've a couple of Technotrend S2-4600 USB boxes successfully working on a current Ubuntu 18.04. Now I bought an additional one which is not working (/dev/dvb/adapterX/frontend0 is missing). As far as I understand this is a new brand with a new chipset - at least for windows you have to use different drivers pre and post 2018.

Ubuntu gives me the following information on boot (dmesg):

```
[    1.726433] usb 1-6: Product: dvb-s2
[    3.836725] dvb-usb: found a 'TechnoTrend TT-connect S2-4600' in warm state.
[    3.836909] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    3.838057] dvbdev: DVB: registering new adapter (TechnoTrend TT-connect S2-4600)
[    3.841996] dvb-usb: MAC address: 00:18:bd:5b:dc:70
[    4.166384] **m88ds3103 0-0068: Unknown device. Chip_id=38**
[    4.166398] **dvb-usb: no frontend was attached by 'TechnoTrend TT-connect S2-4600'**
[    4.229613] dvb-usb: schedule remote query interval to 250 msecs.
[    4.229616] dvb-usb: TechnoTrend TT-connect S2-4600 successfully initialized and connected.

```


[INDENT][SIZE=1]Funny but eventually just random: the Chip_id from the original hardware is expected to be 70 (M88DS3103_CHIP_ID) which is calculated from the hardware registry by a division of 2 (dev->chip_id = utmp >> 1; drivers/media/dvb-frontends/m88ds3103.c Line 1395). 0x70 is exacly the double of 0x38, so without the shift (which IS correct for pre-2018 chips)...[/SIZE][/INDENT]

Is there any chance there will be a fix for this? In fact: does anyone know the difference in hardware (Technotrend Support won't tell me :().

Thanks

Jochen

---

### Post by mörgæs on 2019-12-15
Maybe the fix is already out there. You could try a live boot of 19.10 to see.

---

### Post by jms-1 on 2019-12-15
Nope, exactly the same. What made you believe that this could already be fixed?

---

### Post by mörgæs on 2019-12-15
When hardware support is developed it's done in the development version. Some time in the future the code might be backported to old releases like 18.04. Hence, always begin testing in the new releases. 

Did you get the same dmesg error?

---

### Post by jms-1 on 2019-12-16
The important part was definitly the same (Chip_id=38 and no frontend) the others looked very alike - didn't check in detail. In addtion the frontend0 driver file was still missing.

Where could I peek in the current sources for the kernel driver? At least [https://github.com/torvalds/linux/blob/master/drivers/media/dvb-frontends/m88ds3103.c](https://github.com/torvalds/linux/blob/master/drivers/media/dvb-frontends/m88ds3103.c) seems not to be under maintenance (7 months).

Thanks

Jochen

---

### Post by jms-1 on 2019-12-18
Find quite a long discussion in LibreELEC: [https://forum.libreelec.tv/thread/11784-does-this-dvb-s2-tuner-work](https://forum.libreelec.tv/thread/11784-does-this-dvb-s2-tuner-work). Looks that after around 8 months (in 2018) they got it working - somehow. But I'm a bit worried if this really is the same issue because the Chip_id they are talking about is not 38 (but 52 or 7f).

PS: Opened my box, it's indeed M88DS3103**B**.

PPS: LibreELEC 9.2 will not detect the box either - at least not in vanilla installation. :cry:

---

### Post by mörgæs on 2019-12-18
> **jms-1 said:**
> 
Where could I peek in the current sources for the kernel driver? At least [https://github.com/torvalds/linux/blob/master/drivers/media/dvb-frontends/m88ds3103.c](https://github.com/torvalds/linux/blob/master/drivers/media/dvb-frontends/m88ds3103.c) seems not to be under maintenance (7 months).

Within Ubuntuforum I guess the best you can do is to discuss it in the [development forum]("https://ubuntuforums.org/forumdisplay.php?f=427").

---

### Post by jms-1 on 2019-12-18
Yes, maybe. But at least there is some development going on: [https://git.linuxtv.org/brad/media_tree.git/?h=Montage-3103b.v2](https://git.linuxtv.org/brad/media_tree.git/?h=Montage-3103b.v2) Perhaps this will someday find its path into the main stream version - hopefully in the still current LTS.

---

### Post by jms-1 on 2019-12-19
Sorry but after quite a bit of wandering around in different forums I can still not find a place to ask the question "*Will the Montage-3103b.v2 branch of media_tree [[https://git.linuxtv.org/brad/media_tree.git/?h=Montage-3103b.v2](https://git.linuxtv.org/brad/media_tree.git/?h=Montage-3103b.v2)]* *find it's way into Ubuntu and if so in what version?*" and expect some helpful answer. Can anyone give me a pointer? Well: some answer of this type right here would be fine as well ;-)

Thanks in advance

Jochen

---

### Post by mörgæs on 2019-12-20
What holds you back from installing 20.04 and asking in the development forum?

---

### Post by jms-1 on 2020-02-01
FYI: I contacted the developer of the above media_tree branch and of today there is at least a patch request visible in media_tree.git: [https://patchwork.linuxtv.org/project/linux-media/list/?submitter=7220](https://patchwork.linuxtv.org/project/linux-media/list/?submitter=7220). Maybe it will make it's way into some future kernel version (hopefully 5.6 or before).

---

### Post by jms-1 on 2020-03-31
FYI: The fix seems not to make it into 5.6 but it appears in 5.7. I'll test it as soon as a stable-enough version is available.

---

### Post by jms-1 on 2020-04-13
FYI: I installed kernel 5.7rc1 (Ubuntu 20.04 but I don't think that this version matters) and the 2018+ version of the box is now automatically detected and can be used e.g. with kaffeine (may need to add the corresponing firmware file manually). Many thanks to [https://github.com/b-rad-NDi](https://github.com/b-rad-NDi)!

---

### Post by mörgæs on 2020-04-13
Congratulations and thanks for keeping us posted.

---

