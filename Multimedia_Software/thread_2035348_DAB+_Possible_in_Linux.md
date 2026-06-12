---
title: "DAB+: Possible in Linux?"
date: 2012-07-30
forum: Multimedia Software
---

### Post by Bucky Ball on 2012-07-30
Hi all,

As per the title. Tell it to me straight; I can take it ... I think. I've searched high and low and seems to me there is nothing convincing out there. In fact, there is nothing out there ...

I recently purchased an EZCap 646 USB TV tuner/DAB+ dongle. TV works great using Me-TV. As for getting DAB going, though, I don't like my chances. 

If anyone is successfully listening to DAB+ stations in Ubuntu, please, tell me how. ;)

* Please don't get this confused with streaming internet radio. I am talking about digital radio, not from the internet, but via the DAB+ USB dongle. (Rhythmbox works fine for http:// stations but can't work out how to do DAB ... is there something like a channels.conf involved, as with TV channels in Xine and many others???).

Cheers and all comments welcome and appreciated. Tnx in advance.

PS: I am new to all things DVB/DAB+, though far from new to Ubuntu, so assume nothing re: my prior DAB knowledge. ;)

---

### Post by Bucky Ball on 2012-07-30
As I thought ... hopes are fading ... ;(

---

### Post by Bucky Ball on 2012-07-31
I'm wondering if the driver I have for my DAB+ dongle only handles DVB-T, not DAB. Might try a few things ...

Anyone know how I would check the capabilities of the driver? (It is installed.) Apparently it might be missing the 'crystal' patch which sounds suspiciously like radio. As I mentioned, all new to me. ;)

---

### Post by kingtiger01 on 2012-07-31
For some reason DAB+ sounds Vaguely Familiar... I think i remember seeing something about it recently...

(Searching...)

Edit:

According to ([http://forums.whirlpool.net.au/archive/1642619]("http://forums.whirlpool.net.au/archive/1642619")) 

it should work under BDA, VLC has BDA support. BUT there is a Cache, its model Dependent...

Certian DBA+ Adapters (Chipsets made by Realtek) are not yet (Fully/partially)supported under Linux. There is although Opendab([http://opendab.sourceforge.net/]("http://sourceforge.net/projects/opendab/")) But its specifically for OpenDAB Compliant Chipsets...

Not the one's you find Made by Realtek(Dabby like)...

Quick search turned up this > [CVMK-K84]("http://www.aliexpress.com/product-fm/552914429-DVB-T-USB-Dongle-Free-Digital-TV-and-DAB-on-Computer-wholesalers.html") By a Chineese Maker/Vendor... Cant speak Quality wise, but it should get you started...

---

### Post by Bucky Ball on 2012-07-31
Thanks for that, informative and I'll check some of the links, but just one thing:

[QUOTE=Me, Bucky]I recently purchased an EZCap 646 USB TV tuner/DAB+ dongle. 
[/QUOTE]

... from my first post. I'm already started, I don't need to buy one. Not what I'm asking. ;)

---

### Post by sanderj on 2012-11-17
I'm joining this (old) thread.

The complex way to do DAB radio on Linux, is to use GNUradio combined with the stuff from Osmocom ([http://sdr.osmocom.org/trac/wiki/rtl-sdr](http://sdr.osmocom.org/trac/wiki/rtl-sdr)). Using a rtl-tool, I was able to capture a capture.bin. I still have to process that capture.bin using gnuradio.
My hope is there are predefined process flow for gnuradio for DAB.

I'm still looking for a simple way. :(

FWIW: the technical stuff from my USB stick:

```
[ 3556.007259] usb 2-1.5: new high-speed USB device number 3 using ehci_hcd
[ 3556.111201] usb 2-1.5: New USB device found, idVendor=0bda, idProduct=2838
[ 3556.111208] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3556.111211] usb 2-1.5: Product: RTL2838UHIDIR
[ 3556.111214] usb 2-1.5: Manufacturer: Realtek
[ 3556.111217] usb 2-1.5: SerialNumber: 00000013
sander@R540:~$ 
sander@R540:~$ 
sander@R540:~$ lsusb
...
Bus 002 Device 003: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T
sander@R540:~$
```

---

### Post by sanderj on 2012-11-17
PS: it the last line bad?

```
sander@R540:~$ sudo rtl_test -t
Found 1 device(s):
  0:  ezcap USB 2.0 DVB-T/DAB/FM dongle

Using device 0: ezcap USB 2.0 DVB-T/DAB/FM dongle
Found Rafael Micro R820T tuner
Supported gain values (29): 0.0 0.9 1.4 2.7 3.7 7.7 8.7 12.5 14.4 15.7 16.6 19.7 20.7 22.9 25.4 28.0 29.7 32.8 33.8 36.4 37.2 38.6 40.2 42.1 43.4 43.9 44.5 48.0 49.6 
No E4000 tuner found, aborting.
sander@R540:~$


```

Strange: it says "Rafael Micro R820T tuner". Good. The "No E4000 tuner found, aborting." is then a bit obvious, isn't it?


[http://inst.eecs.berkeley.edu/~ee123/fa12/rtl_sdr.html](http://inst.eecs.berkeley.edu/~ee123/fa12/rtl_sdr.html) is nice info, BTW

---

### Post by sanderj on 2012-11-18
FWIW: rtl_fm is a tool that can do FM demodulation by itself.

Alas, I only get white noise.

```
sander@R540:~$ sudo rtl_fm -f 98648000 -s 12000 -g10 -l10  - | play -t raw -r 12k -e signed-integer -b 16 -c 1 -V1 -
Found 1 device(s):
  0:  Realtek, RTL2838UHIDIR, SN: 00000013

Using device 0: ezcap USB 2.0 DVB-T/DAB/FM dongle

-: (raw)

  Encoding: Signed PCM    
  Channels: 1 @ 16-bit   
Samplerate: 12000Hz      
Replaygain: off         
  Duration: unknown      

In:0.00% 00:00:00.00 [00:00:00.00] Out:0     [      |      ]        Clip:0    Found Rafael Micro R820T tuner
Oversampling input by: 84x.
Oversampling output by: 1x.
Buffer size: 8.13ms
Tuned to 98900000 Hz.
Sampling at 1008000 Hz.
Output at 12000 Hz.
Exact sample rate is: 1008000.009613 Hz
Tuner gain set to 10.00 dB.
In:0.00% 00:00:08.19 [00:00:00.00] Out:90.1k [     -|-     ]        Clip:0    ^CSignal caught, exiting!

User cancel, exiting...
In:0.00% 00:00:08.34 [00:00:00.00] Out:98.3k [     -|-     ]        Clip:0    
Aborted.
sander@R540:~$

```

---

### Post by TazX on 2013-02-28
I have been beating my head against a brick wall for the last day or so.  Please, please, please, how did you get it working?

I've tried all the how-tos I can find, and so far none of them have given me any joy.  I have the same card, and am running Xubuntu 12.10, with kernal 3.5.0-25-generic.

Thanks a bunch.

---

### Post by picbits on 2013-04-13
> **TazX said:**
> I have been beating my head against a brick wall for the last day or so.  Please, please, please, how did you get it working?

I've tried all the how-tos I can find, and so far none of them have given me any joy.  I have the same card, and am running Xubuntu 12.10, with kernal 3.5.0-25-generic.

Thanks a bunch.

I too have been researching this for a bit. I've got the R820T tuner which doesn't seem to be supported by Linux as yet.

I can test the stick using various custom written applications that talk directly to it but I've not come across any driver support as yet for it in 12.04

On the plus side, it's great fun using it for SDR - we were listening to the local air traffic control and some foreign sounding chap broadcasting on a pirate station around the 454Mhz range telling people to sell their clothes and reap the rewards from Allah. The Windoze version works nicely but the Linux port is too slow on my machine to be worthwhile at the moment.

---

