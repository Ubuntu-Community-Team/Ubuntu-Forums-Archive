---
title: "bttv problems at boot"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by midnight2036 on 2007-06-17
I have a Pinnacle Pro/Rage TV card that works using older Linux Kernels/OS. Having scanned the forums I've yet to find the answer needed. Running Fiesty X86-64. The problem is common, the card audio output is white noise. Picture and tuner are working fine. The parameters are card=39 tuner=33 and the card uses MT2032. I have not been able to determine where the initial boot parameters are coming from.

If I perform
sudo rmmod bt878
and, 
sudo rmmod bttv

and then,
sudo modprobe bttv radio=0 tuner=33 card=39 

The card functions in TVtime and XAWTV perfectly. 

Editing (/ect/modules) has no effect. I've found very little information on editing (modprobe.d)

2.6.20 kernel help would be appreciated.

Thanks........

dmesg
[   46.193025] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   46.193063] bttv: Bt8xx card found (0).
[   46.193084] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 18
[   46.193095] bttv0: Bt878 (rev 17) at 0000:00:07.0, irq: 18, latency: 32, mmio: 0xcddfe000
[   46.193104] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   46.193107] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[   46.193139] bttv0: gpio: en=00000000, out=00000000 in=00ffefff [init]
[   46.193561] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   46.194244] bttv0: pinnacle/mt: id=5 info="NTSC / mono" radio=no
[   46.194247] bttv0: using tuner=33
[   46.194251] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   46.194933] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   46.195621] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   46.232069] tuner 1-0043: chip found @ 0x86 (bt878 #0 [sw])
[   46.232105] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   46.234554] tuner 1-0060: Chip ID is not zero. It is not a TEA5767
[   46.234556] tuner 1-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   46.237290] tuner 1-0060: microtune: companycode=4d54 part=04 rev=04
[   46.282980] tuner 1-0060: microtune MT2032 found, OK
[   46.285667] tuner 1-0060: microtune: companycode=4d54 part=04 rev=04
[   46.331333] tuner 1-0060: microtune MT2032 found, OK
[   46.341726] bttv0: registered device video0
[   46.341752] bttv0: registered device vbi0
[   46.341772] bttv0: PLL: 28636363 => 35468950 .<6>input: PC Speaker as /class/input/input2
[   46.359955] . ok
[   46.636286] bt878: AUDIO driver version 0.0.0 loaded
[   46.636322] bt878: Bt878 AUDIO function found (0).
[   46.636338] ACPI: PCI Interrupt 0000:00:07.1[A] -> GSI 18 (level, low) -> IRQ 18
[   46.636344] bt878_probe: card id=[0x1211bd], Unknown card.
[   46.636345] Exiting..
[   46.636349] ACPI: PCI interrupt for device 0000:00:07.1 disabled
[   46.636354] bt878: probe of 0000:00:07.1 failed with error -22

The card is identified at boot

---

### Post by smf28e on 2007-07-04
funny, I met the same problem!
I have a Pinnacle PCTV card and tvtime. Everytime I run tvtime it just flashes once and then exits. The DMESG shows:
[ 39.599014] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[ 39.618665] Linux video capture interface: v2.00 
[ 39.671927] agpgart: AGP aperture is 128M @ 0xe8000000 
[ 39.699282] bttv: driver version 0.9.16 loaded 
[ 39.699287] bttv: using 8 buffers with 2080k (520 pages) each for capture 
[ 39.699344] bttv: Bt8xx card found (0). 
[ 39.699371] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 21 (level, low) -> IRQ 21 
[ 39.699383] bttv0: Bt878 (rev 17) at 0000:01:00.0, irq: 21, latency: 64, mmio: 0xf8001000 
[ 39.699393] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012 
[ 39.699396] bttv0: using: [COLOR="Red"]Pinnacle PCTV Studio/Rave [card=39,autodetected][/COLOR] 
[ 39.699426] bttv0: gpio: en=00000000, out=00000000 in=00fffbff [init] 
[ 39.699911] bttv0: i2c: checking for MSP34xx @ 0x80... found 
[ 39.700240] bttv0: pinnacle/mt: id=2 info="PAL+SECAM / stereo" radio=yes 
[ 39.700243] bttv0: using tuner=33 
[ 39.700245] bttv0: i2c: checking for MSP34xx @ 0x80... found 
[ 39.761072] msp3400 0-0040: MSP3410G-B11 found @ 0x80 (bt878 #0 [sw]) 
[ 39.761076] msp3400 0-0040: MSP3410G-B11 supports nicam and radio, mode is autodetect and autoselect 
[ 39.762067] bttv0: i2c: checking for TDA9875 @ 0xb0... not found 
[ 39.762878] bttv0: i2c: checking for TDA7432 @ 0x8a... not found 
[ 39.883065] tuner 0-004b: chip found @ 0x96 (bt878 #0 [sw]) 
[ 39.883100] tda9887 0-004b: tda988[5/6/7] found @ 0x4b (tuner) 
[ 39.896219] bttv0: registered device video0 
[ 39.896254] bttv0: registered device vbi0 
[ 39.896299] bttv0: registered device radio0 
[ 39.930643] input: PC Speaker as /class/input/input2 
[ 40.096819] bttv0: PLL: 28636363 => 35468950 .. ok 
[ 40.322676] bt878: AUDIO driver version 0.0.0 loaded 
[ 40.322720] bt878: Bt878 AUDIO function found (0). 
[ 40.322739] ACPI: PCI Interrupt 0000:01:00.1[A] -> GSI 21 (level, low) -> IRQ 21 
[ 40.322747] [COLOR="red"]bt878_probe: card id=[0x1211bd], Unknown card[/COLOR]. 
[ 40.322748] Exiting.. 
[ 40.322752] ACPI: PCI interrupt for device 0000:01:00.1 disabled 
[ 40.322756] [COLOR="red"]bt878: probe of 0000:01:00.1 failed with error -22 [/COLOR]

And I have Windfast TV2000 card too, which also uses bt878 chipset, and with same problem. Both cards work fine under Windows.

I wonder what's the problem???

---

### Post by RayVad on 2007-07-22
I have had this error in Gentoo and solved it by loading the tuner driver befor the bttv driver.
But how is this been done in Ubuntu?
I have put it in /etc/modules but seems it is not working. Is it realy loaded befor the bttv driver?

[http://forums.gentoo.org/viewtopic-t-545592-highlight-tvtime+sound.html]("http://forums.gentoo.org/viewtopic-t-545592-highlight-tvtime+sound.html")


I can confirm this by doing(in exactly this order!!):

rmmod bt878
rmmod bttv
rmmod tuner

then do:
modprobe tuner
modprobe bt878
modprobe bttv

End then the sound works! :)

Now we just need to find out how it can be done in Ubuntu automaticly....

---

### Post by brainformat on 2007-07-29
ok, i'm a noob, so could anyone post the exact commands for asus my cinema p7131 dual tv card.
it works on philips saa7134 chip...
10x a lot!

---

### Post by MsChevyKat on 2007-07-29
My tv card is the same way.  I know there is a fix, but considering how rarely I have to reboot. :D  it's not really a big deal to me to have to type those commands at boot up.

---

### Post by MADcat1990 on 2007-10-18
God I could kiss you right now!!! IT MADE MY CARD WORK!

I WILL NAME MY FIRST BORN CHILD AFTER YOU!! (If I reproduce XD)

THANK YOU!!!!!!!!!!!!!!!!

---

### Post by Milv8 on 2007-11-10
Hi all
im running the latest Ubuntu, I love it and it wont be long before i dont even run windoz.
guys my problem i cant change the bttv 4 port capture card (pico2000). 

[   57.744749] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 17, latency: 32, mmio: 0xe7104000
[   57.744776] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   57.744827] bttv0: gpio: en=00000000, out=00000000 in=00f360ff [init]
[   58.034978] usb 3-1: new full speed USB device using ohci_hcd and address 2
[   58.251985] usb 3-1: configuration #1 chosen from 1 choice
[   70.572169] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   70.572179] bttv0: using tuner=-1
[   70.572183] bttv0: i2c: checking for MSP34xx @ 0x80... <7>ieee80211_init: failed to initialize WME (err=-17)

when i use the command in this thread i can change the card number and then xawtv will work correctly. i have been trying to get this to run for weeks know,still no go. vevry time i reboot i then have to use the command lines again.

can someone explain to me how to change the card number in the auto detect.

the main reason i need this i to set up zoneminder.

regards
Milav8

---

### Post by mister_mm on 2007-11-11
My thanks to midnight2036....your script works with my ProVideo 951 card. Well at least tvtime works. I have never had xawtv work with this card, and Ive had it a long time. Used it in Mandrake and Mandriva for years.  I just wish it was a persistent fix. But it's a short script to type after boot. Thank you again.

---

