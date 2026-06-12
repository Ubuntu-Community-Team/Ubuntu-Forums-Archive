---
title: "Tv card under linux"
date: 2011-01-07
forum: Multimedia Software
---

### Post by F1lthym0nk3y on 2011-01-07
Hello fellow ubuntu users,

I know its a long shot, but I'd really love it if I could get my TV tuner card to work under ubuntu. The card I have is a Compro videomate t500f

When I use the lspci command the card is displayed as 

"Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)"

Is there anyway I could get this card to work under linux? 
By the way im using ultimate edition 2.8/Ubuntu 10.10

Thanks guys

---

### Post by Zzl1xndd on 2011-01-07
I haven't used this specific card but have you tried it to see if anything comes up? TVTime is an easy to use program (I believe its available in the software Centre). Keep in mind this will only let you View TV shows not record them, but it should at least tell you if the card is already working.

---

### Post by BicyclerBoy on 2011-01-07
That NXP semiconductor chipset has some support in some models..

You need to check LinuxTV website & video 4 linux project.

To make it work you may need latest kernel patched latest v4l2 patched etc..

---

### Post by coffeecat on 2011-01-07
> **F1lthym0nk3y said:**
> "Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)"

The driver for that chipset came in the Jaunty, Karmic and Lucid kernels so it ought to be in the Maverick/10.10 kernel. However, the firmware for it doesn't come in a default install but is easily added. Install the package linux-firmware-nonfree and you should be good to go.

If your question is about software, then you could try MeTV or Klear, two fairly straightforward TV viewers both in the repositories that can record mpeg streams.

---

### Post by BicyclerBoy on 2011-01-07
Just because there is some kernel support for that chipset does not mean his tuner card will work.
Could be that model id is not recognised.
The ancillary electronics could be very different.

The OP must check LinuxTV v4l2 project because they are the people who make it work.

---

### Post by F1lthym0nk3y on 2011-01-07
> **tweakedenigma said:**
> I haven't used this specific card but have you tried it to see if anything comes up? TVTime is an easy to use program (I believe its available in the software Centre). Keep in mind this will only let you View TV shows not record them, but it should at least tell you if the card is already working.

Yes I've tried using TvTime but just receive a no signal message...

When I use the "dmesg | grep saa7133" command I receive the following...

```
[   34.805557] saa7133[0]: found at 0000:03:07.0, rev: 209, irq: 22, latency: 64, mmio: 0xfebef800
[   34.805565] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]
[   34.805586] saa7133[0]: board init: gpio is 863f00
[   34.961507] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   34.961517] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   34.961526] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 01 03 08 ff 00 f1 ff ff ff ff
[   34.961534] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961542] saa7133[0]: i2c eeprom 40: ff 35 00 c6 96 10 05 32 ce 05 0e 06 c6 ff ff ff
[   34.961550] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961557] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961565] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961573] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961581] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961588] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961596] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961604] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961611] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961619] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.961627] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.653085] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   35.933273] saa7133[0]: dsp access error
[   35.933434] saa7133[0]: registered device video0 [v4l2]
[   35.933461] saa7133[0]: registered device vbi0
[   35.933486] saa7133[0]: registered device radio0
[   35.940117] saa7133[0]/alsa: saa7133[0] at 0xfebef800 irq 22 registered as card -2

```

---

### Post by F1lthym0nk3y on 2011-01-07
> **coffeecat said:**
> The driver for that chipset came in the Jaunty, Karmic and Lucid kernels so it ought to be in the Maverick/10.10 kernel. However, the firmware for it doesn't come in a default install but is easily added. Install the package linux-firmware-nonfree and you should be good to go.

If your question is about software, then you could try MeTV or Klear, two fairly straightforward TV viewers both in the repositories that can record mpeg streams.

Many thanks for the suggestion but..

"sudo apt-get install linux-firmware-nonfree" returns as

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

:(

---

### Post by BicyclerBoy on 2011-01-07
Check the web resource that exists for this very reason..

Ubuntu doesn't create support for devices..it may facilitate.

[http://www.linuxtv.org/wiki/index.php/Compro_Videomate_T750](http://www.linuxtv.org/wiki/index.php/Compro_Videomate_T750)

& check their mailing lists ..

---

### Post by F1lthym0nk3y on 2011-01-07
> **BicyclerBoy said:**
> Check the web resource that exists for this very reason..

Ubuntu doesn't create support for devices..it may facilitate.

[http://www.linuxtv.org/wiki/index.php/Compro_Videomate_T750](http://www.linuxtv.org/wiki/index.php/Compro_Videomate_T750)

& check their mailing lists ..


Ahhh bummer :(, Could anyone recommend me a PCI or USB Tv tuner which is fully supported inside Linux which is fairly easy to setup? Or should I just wait until they release DVB T2 devices?

---

### Post by F1lthym0nk3y on 2011-01-07
Not too sure why the "dmesg | grep saa7133" command says I have a Compro T750, when I certainly have a Compro T500f.. weird :/

---

### Post by BicyclerBoy on 2011-01-07
185b:c900, board: Compro VideoMate T750 [card=139,autodetected]

The kernel only knows what is returned & what is coded in..

185b  is the manufacturer id & is Compro VideoMate
c900  is the model id not recognised & is guessed
so it guessed wrong..

I believe a modalias package can help resolve ids to names.
But unless there is some kernel module support that can be used, it does not help here.

AFAIK Hauppauge is one of the best supported..
[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices)

I once plugged in a free Chinese USB dvb-t & was working in 5 minutes (MythTV).
So check the above web link...

---

### Post by coffeecat on 2011-01-07
> **BicyclerBoy said:**
> AFAIK Hauppauge is one of the best supported..

And my Hauppage WinTV HVR-1110 PCI card has exactly the same Philips chipset as the OP **and it works just fine**, so long as the nonfree firmware is installed.

@OP, try the Me-TV app I suggested.

---

### Post by AKADAP on 2011-01-07
> **coffeecat said:**
> And my Hauppage WinTV HVR-1110 PCI card has exactly the same Philips chipset as the OP **and it works just fine**, so long as the nonfree firmware is installed.

@OP, try the Me-TV app I suggested.

Me-TV seems to be for digital tuners only.
It does not allow selecting a specific tuner (I have 5 distributed among 3 sources).
It only seems to support OTA channels, not cable. The tuner it chose to use is connected to cable and is capable of both analog & digital reception. It found no channels when it scanned.

All five of my tuners work fine with MythTV with the exception of the analog portion of the ATI HDTV Wonder. I was hoping Me-TV would help me with debugging the analog tuner.

---

### Post by F1lthym0nk3y on 2011-01-08
> **BicyclerBoy said:**
> 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]

The kernel only knows what is returned & what is coded in..

185b  is the manufacturer id & is Compro VideoMate
c900  is the model id not recognised & is guessed
so it guessed wrong..

I believe a modalias package can help resolve ids to names.
But unless there is some kernel module support that can be used, it does not help here.

AFAIK Hauppauge is one of the best supported..
[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices)

I once plugged in a free Chinese USB dvb-t & was working in 5 minutes (MythTV).
So check the above web link...

My card is definitely a T500F, Ive just found the box to accompany it, I'm guessing its not supported one bit then, typical.

I downloaded and installed the MeTV app but was once again shown a "No DVB devices are installed" message.. :(

Looks like Ill have to get another Tuner, now would it be worth getting a cheap one from ebay I know is supported, or waiting for DVB-T2 devices to be launched?

---

### Post by jimmers on 2011-01-08
F1lthym0nk3y,
Take a trip to Maplins in Portstmouth and purchase an AverMedia Volar (A815) tuner card,
It works straight out of the box, only prob remote does'nt work.

But good value for money, even worth the ferry fare from Gosport.

Luck

---

