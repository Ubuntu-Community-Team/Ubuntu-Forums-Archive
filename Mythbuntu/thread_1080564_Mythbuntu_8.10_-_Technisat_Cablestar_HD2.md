---
title: "Mythbuntu 8.10 - Technisat Cablestar HD2"
date: 2009-02-25
forum: Mythbuntu
---

### Post by sakul on 2009-02-25
My HTPC,

AMD BE2400
M3N78-EM
ASUS GT8500 (Nvidia)
=> Technisat Cablestar HD2
Mythbuntu 8.10 (combined front- & backend)

has a problem with recording and watching DVB-C TV.

I installed on a fresh (updated) Mythbuntu 8.10 system (above) the driver for Technisat Cablestar HD2:
<http://www.linuxtv.org/wiki/index.php/Technisat_CableStar_HD2>
=> S2-liplianin
after succesfull installation
- adding card to mythtv -
- channel scanning -
- Epg 
everythink ok!

But, during Live TV and Recording (Mythtv) there are:

[LIST]
[*]noises (high frequency) every aproc. 10 sec.
[/LIST]
[LIST]
[*]at same time are screen droops and sometimes squares are visible
[*](like low signal strenght but 65% should be enough)
[/LIST]
[LIST]
[*]and video and audio are no synchron. Becomes worser every second of watching recorded or live TV.
[/LIST]

I had the same experience on Mythbuntu 8.04 (same PC) after upgrading the kernel. Im don't know the version but I remember that the installation of the mantis driver (just.de) was not possible, so I had to switch to S2-liplianin. Since this point watching and recording qualitity is very bad.

dmesg mythbackend.log ... there are no contents, which point to a (internal) problem (as far as an hobby linux user can evaluate)
top indicates cpu usage about 30 % during watching 
recording ~20%

I use nvidia driver 177.

Had anybody such experience?
Moreover a solution?

---

### Post by sakul on 2009-03-01
Ok,

I found something with mplayer and myhtfrontend.

watching DVB stream width mplayer:
```
mplayer dvb://<channel>
```
returns those messages:
"too many video packets in the buffer"
and
"your system is to slow.."
after ~20 seconds (A-V increases rapidly)

mythfrontend returns cyclic

NVP: prebuffering pause

---

### Post by soucy on 2009-03-07
Hey, i'm currently searching for the CableStar HD2 driver for linux. Can you provide me a link or something?

I'm using Ubuntu 8.10 and trying to use my TV card since weeks.

---

### Post by sakul on 2009-03-08
Just follow this link:

[http://www.linuxtv.org/wiki/index.php/Technisat_CableStar_HD2](http://www.linuxtv.org/wiki/index.php/Technisat_CableStar_HD2)

summary:

```

hg clone http://mercurial.intuxication.org/hg/s2-liplianin
cd s2-liplianin
make
sudo make install
sudo reboot

```

---

### Post by simonvid on 2009-03-29
> **sakul said:**
> Ok,

I found something with mplayer and myhtfrontend.....



Did you find a way to improve quality? I am experiencing same problems (ubuntu intrepid, same motherboard, onboard graphic but sligthly faster processor PII X810).

---

### Post by sakul on 2009-03-30
In the meantime I testet the same hardware with windows XP Pro SP3 and everything works fine (smooth video and A/V are synchron)

A reinstall of Mythbuntu 8.10 did not change anything - no improvments.

From my point of view the S2-liplianin driver is the problem (mantis driver works fine at old kernel) (or the kernel?) but I have no Idea how to debug this driver and how to bring the bug to the development. 
dmesg returns only ... mantis start/stop feed etc.

Playing a DVD or .avi-files (mplayer , mythtv) works fine - the graphic card, X etc should be OK! (?) 

Dvbsnoop - checking the dvb-c stream - is to complicated for me and I would not understand the output.

A Solution could be the "normal" v4l - dvb source (its only a idea!)
[HTML]http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers[/HTML]
but until now I'm not able to load all neccesary modules!

No improvements!

---

### Post by simonvid on 2009-03-30
> **sakul said:**
> No improvements!

:(

OK. If I find a solution I will let you know...

---

### Post by Cuppa-Chino on 2009-04-14
oh I guess I will look for a different card then...

I was really contemplating buying that one... unless anyone got it working now? it looks a really sweet deal price wise

---

### Post by BatPenguin on 2009-04-16
> **Cuppa-Chino said:**
> oh I guess I will look for a different card then...

I was really contemplating buying that one... unless anyone got it working now? it looks a really sweet deal price wise

I would say that it works -- but only for free channels.

Speaking of which, does anybody know of a CA module (for pay-tv-cards) that works with this? The card itself seems to work just fine for me with the mantis driver, but once I plug a CA module (I have a technicrypt CX) into the CI slot, it stops working - for both free channels and encrypted channels. If somebody has a CA module (or other module) plugged into the CI slot and is having problems getting the card to work, I suggest you take out the module and try watching free channels. For me, those work very good.

---

### Post by simonvid on 2009-04-19
> **BatPenguin said:**
> I would say that it works -- but only for free channels.

Speaking of which, does anybody know of a CA module (for pay-tv-cards) that works with this? The card itself seems to work just fine for me with the mantis driver, but once I plug a CA module (I have a technicrypt CX) into the CI slot, it stops working - for both free channels and encrypted channels. If somebody has a CA module (or other module) plugged into the CI slot and is having problems getting the card to work, I suggest you take out the module and try watching free channels. For me, those work very good.

For me, it is not problem of CI slot, because I have not plugged it into my setup. My problem is picture quality itself.

---

### Post by sakul on 2009-04-20
Hallo,

..... i tried the same hardware on mythdora (10.21)and  mythbuntu 9.04 beta - same **** as before. On Windows XP the harware works fine. I think the S2-liplianin drives causes the problem!
According linuxtv there are further card with CU1216 ..mantis . eg. Cinergy C DVB-C

[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C](http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C)

Has anybody a problem with this dvb-c card?

hm... it is realy hard to like linux....

---

### Post by sakul on 2009-05-19
[SIZE="6"]JUHU!

I found the problem: the mainborad asus m3n78-em  has a bios setting wich is called C1E support. The parameter can be set to "disabled" or set to "automatic". Default value is "automatic" and this causes bad dvb-c video quality and unsynchron audio.

For me changing bios parameter "c1e support" from automatic to disabled, solves the problem.[/SIZE]

have fun!

---

### Post by simonvid on 2009-10-06
I've put my cablestar project on hold for while and only yesterday I've found sakul's resolution of his problem.

I've tried his solution myself and juhej:KS:KS:KS:KS:KS:KS:KS:KS I works for me also.

I can now watch dvb-c channels on my new mythtv box and (because Cablestar is HD card) I can watch HD programs also which I couldn't do before since my cable operator set-top box cannot handle HD programs.

---

### Post by JaizEdelmann on 2011-08-03
Thanks C1E stepping worked for me aswell, my god i spent alot of time on this problems, cheers.

---

