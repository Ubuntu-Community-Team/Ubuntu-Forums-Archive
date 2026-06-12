---
title: "PCTV 110i isn't detected"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by fabio.nb on 2007-02-22
Hi all,

I'm having a problem with my Pinnacle PCTV 110i. It isn't detected by the kernel, I executed the command dmesg or lspci and my card is not showed.

In the /var/log/kern.log:
PCI: device 0000:00:0b.0 has unknown header type 7f, ignoring.

The others pci cards were detected and are working.
I ever tried to load saa7134 modules, but in dmesg appears:
[17180656.644000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17180656.680000] saa7134 ALSA driver for DMA sound loaded
[17180656.680000] saa7134 ALSA: no saa7134 cards found

I don't know what is happening.

Thanks for any help.
Fabio

---

### Post by vemon on 2007-02-22
Hi,

I'm using Ubuntu Edgy (6.10) and a pinnacle DVB-T card. I have exactly the same problem as you do with almost the same error messages (lspci not showing the card, modprobe saa7134_dvb not finding the card and the unknown header message in boot).

The problem could possibly be that the kernel isn't new enough to recognize the card. There seems to be a patch in [www.linuxtv.org](www.linuxtv.org) for kernel 2.6.20 but I haven't had the time to test it yet. It could be the answer to this problem. Of course to use it one would have to download kernel sources, apply the patch & compile the kernel.

The patch can be found from:
[http://www.linuxtv.org/downloads/patches_to_2.6.20/v4l_dvb_hg_4726_add_support_for_pinnacle_310i.patch](http://www.linuxtv.org/downloads/patches_to_2.6.20/v4l_dvb_hg_4726_add_support_for_pinnacle_310i.patch)

I'm probably going to try this tomorrow myself and let you know if it works.

btw. I already compiled & installed v4l drivers from linuxtv.org on top of Edgys defaut kernel (2.6.17-10-generic) and it didn't make any difference.

---

### Post by fabio.nb on 2007-02-22
Hi vemon,

Thanks for you answer, I'll try this night (well is almost 23 here in brazil, maybe when will be 01).

But one strange thing happens hear, now, when I turned my pc on, the message ... has unknown header... isn't appearing in the logs. I don't know what could be caused  this.

Well, when I update the kernel, I'll let you know if it works.

Thanks again.

---

### Post by fabio.nb on 2007-02-23
Hi,

I tried to use the kernel 2.6.20, but I wasn't successful. I didn't use any patch, but I saw in the source code (kernel 2.6.17) that it have support for pinnacle 110i.

I'll try something else!!! 

Thanks

---

### Post by david_2001 on 2007-02-23
According to the [COLOR="SandyBrown"][LinuxTV wiki]("http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_110i")[/COLOR], this card is the same as the Pinnacle PCTV 50i and is supported.  If it's not being detected then try the following, followed by a reboot:
```
sudo sh -c 'echo "options saa7134 card=77" > /etc/modprobe.d/saa7134'
```
All it does is create a file in /etc/modprobe.d containing the card identity number to be passed to the saa7134 driver when it is loaded.

---

### Post by fabio.nb on 2007-02-23
Hi...

I tried this with kernel 2.6.17, but I wasn't successful. I'll try again with kernel 2.6.20.

I'm thinking if my card isn't properly connected. I'll try to open my pc and check out if it's ok.

Thanks.

---

### Post by vemon on 2007-02-24
For me the problem was (also?) that the card wasn't properly connected. I removed and re-inserted the pci card and almost all the modules loaded automatically in next boot :). The only module I had to load manually was saa7134_dvb which is a driver for the dvb frontend.

For the record: I'm running ubuntu edgy 6.10 and have downloaded and compiled the v4l drivers myself.

---

### Post by fabio.nb on 2007-02-24
Thanks guys, I removed the card and inserted them again and it's working now (the card was with a little part disconnected)...

Thanks again!

---

