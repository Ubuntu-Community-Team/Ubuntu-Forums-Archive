---
title: "Help AverMedia Trinity A707 ?"
date: 2012-09-17
forum: Multimedia Software
---

### Post by crnipauk on 2012-09-17
Ubuntu 12.04.1  problem drivers!
Hi does anybody have idea how to make the drivers for AverMedia Trinity A707 chips on board Gygabite GA-H61M-S2PV (rev. 2.0).


Tv tuner chip is to picture!



Thanks in advance!!

---

### Post by crnipauk on 2012-09-18
> **crnipauk said:**
> Ubuntu 12.04.1  problem drivers!
Hi does anybody have idea how to make the drivers for AverMedia Trinity A707 chips on board Gygabite GA-H61M-S2PV (rev. 2.0).


Tv tuner chip is to picture!



Thanks in advance!!

I think that this is not an OS that I imagined, on Windows everything works OK!

 on Linux does not work half the hardware

Thanks for your help!!

Edit::
He he 
Avermedia never in my PC!

[FONT=Arial][B]Hello Mr./Ms. 
[/B][/FONT] [FONT=Arial]Thank you for choosing AVerMedia.[/FONT] [FONT=Arial]Dear customer, 

Thank you for contacting us. Regarding your inquiry, we're sorry  that we don't have plan to develop Linux driver for A707 to make it work  on ubuntu linux 12.04 currently. We apologize for the inconvenience.  Please let us know if any other query. Thank you and wish you a good  day! 

Best Regards, 
AVerMedia Technical Support Team[/FONT]


:lolflag:

---

### Post by crnipauk on 2012-09-20
It is sad that no one knows the solution to the problem :?:

No one has such a TV card :(

No support or Fedora E17 or Ubuntu!

):P

---

### Post by crnipauk on 2012-09-24
> **crnipauk said:**
> ubuntu 12.04.1  problem drivers!
Hi does anybody have idea how to make the drivers for avermedia trinity a707 chips on board gygabite ga-h61m-s2pv (rev. 2.0).


Tv tuner chip is to picture!



Thanks in advance!!
lspci
02:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 03)
):p):p

---

### Post by crnipauk on 2012-09-25
AverMedia Trinity A707!!
People do have some sort of solution for this card?

:popcorn:

---

### Post by BicyclerBoy on 2012-09-25
All tuner support comes thru' v4l-dvb..
Don't buy h/w without checking it has support..
[http://linuxtv.org/wiki/index.php/AVerMedia](http://linuxtv.org/wiki/index.php/AVerMedia)

scroll down to 707 & see no kernel support.

[http://linuxtv.org/wiki/index.php/NXP_SAA716x](http://linuxtv.org/wiki/index.php/NXP_SAA716x)
looks very bad for the NXP SAA7160/2.. development stopped & then removed..

[http://linuxtv.org/wiki/index.php/Saa7162_devices](http://linuxtv.org/wiki/index.php/Saa7162_devices)
there are no supported cards...

---

### Post by crnipauk on 2012-09-26
> **BicyclerBoy said:**
> All tuner support comes thru' v4l-dvb..
Don't buy h/w without checking it has support..
[http://linuxtv.org/wiki/index.php/AVerMedia](http://linuxtv.org/wiki/index.php/AVerMedia)

scroll down to 707 & see no kernel support.

[http://linuxtv.org/wiki/index.php/NXP_SAA716x](http://linuxtv.org/wiki/index.php/NXP_SAA716x)
looks very bad for the NXP SAA7160/2.. development stopped & then removed..

[http://linuxtv.org/wiki/index.php/Saa7162_devices](http://linuxtv.org/wiki/index.php/Saa7162_devices)
there are no supported cards...

I can not believe that there is absolutely no solution:(

---

### Post by BicyclerBoy on 2012-09-26
Why not?
There is no economic imperative; linux base is small & uses open/free apps.

A lot of devices get support because of sheer volume & common hardware base.
Realise almost all the drivers are created by reverse engineering by unpaid work.

Obscure mobo tuner/encoder are never going to happen unless the unpaid driver developer has some motivation. 

The (linux) drivers that come from vendors seem to be bad & often built for one kernel release.

TBS & Haupauuge could be exceptions.

---

### Post by crnipauk on 2012-10-06
Unfortunately this is not the only problem with the new Ubuntu 12.04:confused:

Does not work com port and  CP21xx USB to UART bridge :confused:

MB:gigabyte h61m-s2pv :(

---

### Post by BicyclerBoy on 2012-10-07
The 2 most widely used USB serial ports are: FTDI & Prolific based.

The FTDI parts are used in a very wide range of devices..
I have used the prolific adapter to program micros & test other devices.

The Silabs part could be different story.
They have provided drivers but the archive has errors. Good start..

---

### Post by crnipauk on 2012-10-21
MB:gigabyte h61m-s2pv ,proc.. Intel G630 !
I do not know why but the PC does not work either ubuntu 12.xx 64 bit?

:(

---

### Post by BicyclerBoy on 2012-10-22
That mobo is very new ?? It is an ivybridge iCPU mobo?

The default kernel in 12.04 is prob about 1 year old (with bug fixes)..

I'm not surprised some h/w devices are not recognised/supported.

---

