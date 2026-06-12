---
title: "AVerMedia AVerTV Super 007 Setup"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by HighSide on 2007-10-22
After unsuccessfully trying to get a Compro T220 DVB card to work in 7.04 I decided to buy another card. However l struggled to find a compatible low-profile card in the UK.

 I eventually purchased an AVerMedia AVerTV Super 007 and according to the DVB Wiki requires a patch and firmware to enable it, but it should work.

[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007](http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007)

I removed the Compro T220 card and plugged the AVerMedia card in and powered up. 

The DVB folders I was missing are now there and Kaffine recognises the card however I cannot scan for channels, yet. I tried a scan from terminal which was also unsuccessful. 

I download some firmware for the card and placed it into the firmware folder and rebooted.
Problem, it will now only boot up when in recovery mode and takes 10 minutes, it can’t load the firmware and times-out after the 10mins. Will loading the firmware only be successful once I have done the patch? Could you give some more detailed instructions how to do the patch?

There is also another issue which I was quite surprised at, I have the aerial for my TV also connected to the DVB Card, when the PC is off the picture on the TV is good, signal strength is high. However when I turn on the PC the picture on the TV is corrupted and impossible to watch.

I did notice that the AVerMedia card is 75ohms (I think the TV is 50ohms), I was under the impression that 50ohms was usual for TV aerials. Even though there is an impedance mis-match I would have thought if there was any adverse affects it would always be apparent as it is always connected. I think a signal amplifier would isolate the inputs. But one step at a time, need to get the card working first.
 
Cheers 
Stu

---

### Post by steefjeqv on 2007-10-22
Hi Stu,

First some questions about the firmware file which you've probably already covered :

- the file is renamed and is in /lib/firmware
- the permissions for the firmware file are good

I've attached the firmware file needed for this card.
You can give it a second try, if you like. Unpack it and copy it to /lib/firmware.
Change the permissions (to be sure) using terminal :

sudo chmod 777 /lib/firmware/dvb-fe-tda10046.fw

I've had a quick read of the LinuxTv wiki concerning this card.
Before applying the needed patch you can give it a test using the following command :

sudo rmmod saa7134
sudo modprobe saa7134 card=109

Greetings,
Steven

---

### Post by HighSide on 2007-10-30
Hi Steven

I followed your instructions but I'm not sure that the Firmware file is correct. 
Once I copied your file to the /lib/firmware folder it does boot up at the normal speed.

I tried the commands  and got this:
stuart@stuart-desktop:~$ rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_dvb,saa7134_alsa

modprobe  returns nothing

a dmesg still shows that the firmware is not loaded.
[   34.410809] tda1004x: timeout waiting for DSP ready
[   34.462744] tda1004x: found firmware revision 0 -- invalid
[   34.462746] tda1004x: trying to boot from eeprom
[   35.209811] tda1004x: found firmware revision 0 -- invalid
[   35.209816] tda1004x: waiting for firmware upload...
[   36.132811] usb-storage: device scan complete

---

### Post by HighSide on 2007-10-30
Hi Steven

For some reason I had to unzip the file twice, it is now 10kb, however on boot up it still reports the firmware is invalid.

---

### Post by steefjeqv on 2007-10-30
Hi Stu,

The firmware file attached in my previous post worked for my tda10046 tuner card.
This card was a Terratec which maybe the reason why it's not working for you.

I've attached the same firmware file, but this one is extracted from the linuxtv link which you've mentioned in your first post.

Before you try out this version it may be best to remove the files you've added to your /lib/firmware directory.

- Unzip the attached file to /lib/firmware
- Then in terminal : sudo chmod 777 /lib/firmware/dvb-fe-tda10046.fw
- Then in terminal : sudo modprobe saa7134 card=109


After this, just have a look if your card is able to do a channel scan with Kaffeine.

Greetings,
Steven

---

### Post by NT4usB on 2007-10-30
Don't know if this applies...
When I configured my Aver A180, I had to blacklist saa7134_something... alsa, maybe? before I could get the drivers to load.
ymmv.

---

### Post by HighSide on 2007-10-31
Hi Steven

I tried the new firmware, I still get the delayed boot up and kaffine now takes a long time to launch. 
I tried to do a channel scan but kaffine stops responding!

I have a feeling that this card too is not quite the same as the one tested on the DVB Wiki.

---

### Post by steefjeqv on 2007-11-01
Hello Stu,

It may help to edit your /etc/modules.

Add the line : saa7134 card=109

Also check if the firmware file used is set to "executable". Rightclick on it, then click on the "permissions" tab. There should be a little box which you can check by clicking on it.

Restart your PC and see what happens. You can try this out with both the firmware versions I attached earlier on.

If this doesn't do the trick, the following may.

I've tried out the "get_dvb_firmware" script which downloads the firmware needed. I've attached the script to this post.
There's three versions of the tda10046 firmware available for download with the script :
1. tda10045
2. tda10046
3. tda10046lifeview

Unzip this script to your Desktop.
Then in terminal :

cd Desktop

sudo ./get_dvb_firmware tda10045
sudo ./get_dvb_firmware tda10046
sudo ./get_dvb_firmware tda10046lifeview

You should now have three different firmware versions of the tda10046 tuner on your desktop.
Change the permissions in terminal : 

sudo chmod 777 dvb-fe-tda10045.fw
sudo chmod 777 dvb-fe-tda10046.fw
sudo chmod 777 dvb-fe-tda10046lifeview.fw

Also check if these files are marked "executable".

Then give these a try in your /lib/firmware directory (I suggest one at a time).

Greetings,
Steven

---

### Post by HighSide on 2007-11-02
:KS

Steven you are a star! 

The firmware is now loaded correctly and Kaffine attempts to do a scan but is unable to find any channels yet.

---

### Post by steefjeqv on 2007-11-02
Hello Stu,

Glad to here your card is working.

Did you try the auto-scan function in Kaffeine ?

If the auto-scan doesn't work, you'll have to create your channels.conf using dvb-utils (or w-scan).

In terminal :

sudo apt-get install dvb-utils

sudo scan -x 0 /usr/share/doc/dvb-utils/examples/scan/dvb-t/yourlocation > channels.conf

You'll have to replace "yourlocation" with the corresponding transmitter in the Lancashire region, which hopefully you'll find in the /usr/share/doc/dvb-utils/examples/scan/dvb-t directory.
Copy the created channelsconf to /yourhomefolder/.kde/share/apps/kaffeine/dvb/channels.conf (I'm not to sure about the correctness of the last bit in the path but it should be there somewhere).


You can also try out the channel settings for other countries/regions in Kaffeine, sometimes they are the same.

Hope you can watch some digital TV on your computer tonight !

Greetings,
Steven

---

### Post by HighSide on 2007-11-05
Oh dear, still not working!

When i do the scan i get the following....
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754166670 0 3 9 1 0 0 0
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

also when i do dmesg I get the following line repeated numerous times
590.517055] tda827xo_set_params: could not write to tuner at addr: 0xc2

Any ideas??

---

### Post by NT4usB on 2007-11-05
looks like you need to be chowning or chmoding something... don't ask me what, haven't a clue. /dev/dvb0/ maybe?
Might try running the scan as root... sudo. If it writes, then it's a permissions problem. On to discover what file(s) need chmod.
I never got my A180 to scan anything. Only way I got a lineup was what MythTv found when it scanned.

---

### Post by steefjeqv on 2007-11-06
Hello Stu,

Sorry I wasn't able to reply yesterday evening (already asleep).

The dmesg output you've posted seems to point to a tuner chip (tda827).

There's a few things you could try :

Edit your /etc/modules :
saa7134 card=109 tuner=54

The tuner=54 points to the tda827.

If this doesn't work edit /etc/modules to :
saa7134

Also, if there's anyone who can help explain how to apply the patches mentioned in the inital post, please do.

Greetings,
Steven

---

### Post by HighSide on 2007-11-12
Hi Steven,

Still not had any joy with the card. I have been trying to sort out the patch.
I download the sources
Edited the file saa7134-cards.c
However I was not sure how to disable the v4l stuff.

Can anyone help us with some info on compiling the v4l/dvb sources, as described here..

[http://lists.zerezo.com/video4linux/msg19205.html](http://lists.zerezo.com/video4linux/msg19205.html)

---

### Post by steefjeqv on 2007-11-12
Hello Stu,

Some good news :

Your card has been added to the v4l cardlist (card=117).

[http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.saa7134]("http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.saa7134")

This should mean full support if you apply the newest version of their drivers to your kernel.
I've never done this, but maybe this link will help you :

[http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial]("http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial")

Greetings,
Steven

---

### Post by HighSide on 2007-11-13
Hi Steven,

I actually saw the card listed last night, but it was too late for me to try. Hopefully i will get some time to try it tonight.

I will keep you posted...

---

### Post by HighSide on 2007-11-13
Hi Steven,

I followed the instructions but got errors on compiling (ie make)

  CC [M]  /home/stuart/v4l-dvb/v4l/v4l1-compat.o
/home/stuart/v4l-dvb/v4l/v4l1-compat.c:149: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'palette_to_pixelformat'
/home/stuart/v4l-dvb/v4l/v4l1-compat.c: In function 'v4l_compat_translate_ioctl':
/home/stuart/v4l-dvb/v4l/v4l1-compat.c:661: warning: implicit declaration of function 'palette_to_pixelformat'
make[3]: *** [/home/stuart/v4l-dvb/v4l/v4l1-compat.o] Error 1
make[2]: *** [_module_/home/stuart/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/stuart/v4l-dvb/v4l'
make: *** [all] Error 2

Any clues?

I'm sure that i complied this last night but I didn't realise that the latest sources included my card. i then removed the compiled files and now i can't get it to work!!!

Maybe i should try it  against 2.6.20-15 headers?

---

### Post by steefjeqv on 2007-11-13
Hello Stu,

I'm not an expert in compiling (more like a newbie). 

I've just tried out the howto myself, and the compilation went quite good (some errors).
All this against the Gutsy kernel 2.6.22-14.

One thing I've noticed :

Don't forget "sudo" when you're in terminal.
I've tried to compile without "sudoing" and that didn't work out.

As you said, give it a go against 2.6.20-15 headers.

Greetings,
Steven

---

### Post by blahmartinblah on 2007-11-15
> **HighSide said:**
> 
I followed the instructions but got errors on compiling (ie make)


HighSide, any progress? I need some help too, I'm getting the same issue. Ubuntu feisty 7.04, 2.6.20-16-generic. Amd64. Trying to get my Nova T-500 card working.

Martin.

---

### Post by HighSide on 2007-11-16
Hi 

I tried to compile it again last night but still no joy.

I downloaded the kernel source code too (2.6.20), just to make sure and got the same errors.

Maybe I should upgrade to Gutsy first? Or could it be a 64 bit issue?

I have done some searching and havent found anything yet. I think I may start a new thead asking for some help on this, but I will keep this one updated.

---

### Post by steefjeqv on 2007-11-16
Hi Stu,

Did you see this thread :

[http://ubuntuforums.org/showthread.php?t=566542]("http://ubuntuforums.org/showthread.php?t=566542")

The post made by MattiViljanen may solve your compiling problems.

You can also try upgrading to Gutsy, but the upgrade process isn't bulletproof.
In my case the upgrade stalled about halfway (luckily not breaking the system) and I had to opt for a fresh install.

Greetings,
Steven

---

### Post by HighSide on 2007-11-26
Hi Steven

I tried your suggestion but to no avail. It still would not compile without errors.
I tried it again a few days later, a number of files were updated. This produced some slightly different errors.

I did some searching and found other another potential solution by using some experimental v4l-dvb code.
This time it actually compiled! I tried the 'make install' (also with no errors). 

I checked to see if my card was recoginsed as card 117, but still showed 109. I tried a scan, but as expected it did not work.

By the way, I had removed 'saa7134 card = 109 tuner = 54' from /etc/modules and just left the line 'saa7134'. I then tried to list the card as 117, but it reverted back to card 109.

I had a quick look at the saa7134_cards.c file but could not see my card listed in there. 

I think I may try to recompile with the saa7134_cards.c that does  contain the details of my card and see what happens....

---

### Post by HighSide on 2007-11-27
Hi Steven

Last night I edited the file that was halting the compilation, 'v4l1-compat.c' i think.
I compared it to the file in the experimental folder, I moved a semi-colon and added a comma. 

I then tried to compile it again and it worked!! I did the 'sudo make install' and rebooted.

And now, my card is not recognised at all!!

Have I broken it or have i missed somthing?

Just had a quick search and I think i may need to add 'card=117' to /etc/modules again, since it wasn't autodetected.

---

### Post by steefjeqv on 2007-11-27
Hi Stu,

Sorry for my late reply.

Have you tried modprobe in terminal ?

sudo modprobe saa7134

or

sudo modprobe saa7134 card=117

Greetings,
Steven

---

### Post by HighSide on 2007-12-05
Hi Steven 

Sorry for the late reply, Im having trouble spending time on this at the moment. 

I tried your suggestions, but didnt work. I think I may need to edit /etc/modules again to remove any references to saa7134 and then do as you suggest. From memory I think another module requires the saa7134 module (alsa sound module?) and is currently inserted by the file. 

If I have no joy soon I am thinking of buying a Hauppauge USB reciever. Any thoughts on this device.

Thanks for the help

---

### Post by SquiffSquiff on 2007-12-08
Hi

After reading through the stuff so far on this thread and other sites and some false starts I have got this card working on my Gutsy x86 install. There have been a number of non-obvious steps and issues which delayed me considerably. I am detailing these here for this reason. I am using Kubuntu Gutsy with the Kubuntu studio (rt) kernel.

**Non-obvious issues:**

[LIST]
[*]Many TV applications won't even find the card until you have already tuned it for your local region using a separate utility and imported the configuration file.

[*]The majority of the TV applications are intended for analogue TV rather than DVB and the interfaces and instructions for these can be confusing or incorrect for DVB setup.

[*]MythTV doesn't play nice with this card and creates severe problems for other applications trying to use it. On my setup, it was extremely complex and confusing to locate and configure the card from within MythTV. When I had done this, I could get sound but no real picture and could not change or browse channels in MythTV. I also discovered that the Myth backend locked other applications out from using the card  and because it started at boot, the card would appear to be absent in many of my TV applications.
[/LIST]

**For successful setup:**

These are intended for a non-expert, follow_the_dots user.

Physically install your card and connect an antenna to it.

Uninstall MythTV if present and restart your computer to ensure no MythTV daemons are running

Although the core hardware for this card is common to this card and it does appear to be recognised with the current apt version of video4linux (v4l), it is actually not recognised properly and will not work with it.

You will NOT need to edit /etc/modules so undo any edits that you have made for this card

You will not need to worry about autodetection which you may see mentioned on other websites.

You WILL be using the latest v4l direct from the developers, i.e. non-packaged.

You will also need some development tools installed on your box. I already had mine installed but you could begin by ```
sudo apt-get install kernel-package
``` to pull in the core tools you will likely need.

(This section based on the instructions at [http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial](http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial))

```
sudo apt-get install mercurial 
```
Mercurial is a distributed version control system that you will need to install in order to get the latest code. You will also need the source for your running kernel. I don't know if the kernel headers are sufficient, I installed the full source. Be aware that you will need to unzip the (full) source installed by apt before you can use it here. I do this by ```
alt+f2 kdesu konqueror
``` to get a root file browser and then unzip in /usr/src/. 

Create a working directory somewhere to compile your code and open a terminal there

Retrieve v4l-dvb sources

```
hg clone http://linuxtv.org/hg/v4l-dvb
```

Change into the v4l-dvb directory:

```
cd v4l-dvb
```

(This section based on the instructions at [http://lists.zerezo.com/video4linux/msg19205.html](http://lists.zerezo.com/video4linux/msg19205.html))
Here you need to edit one of the files you downloaded with Mercurial manually:

Open your-working-directory/v4l-dvb/linux/drivers/media/video/saa7134/saa7134-cards.c with a text editor and insert the following section. There are a number of card definitions already there so you can see how one follows another in the list. Be very careful to paste this section into the file just after another definition so that it follows the same pattern and doesn't disrupt or interrupt the other definitions or other text before or after it. It doesn't matter where you put it in the file, I put mine between the first and the second definitions.
        ```

        [SAA7134_BOARD_PHILIPS_TIGER_S] = {
                .name           = "Philips Tiger - S Reference design",
                .audio_clock    = 0x00187de7,
                .tuner_type     = TUNER_PHILIPS_TDA8290,
                .radio_type     = UNSET,
                .tuner_addr     = ADDR_UNSET,
                .radio_addr     = ADDR_UNSET,
                .tuner_config   = 2,
                .mpeg           = SAA7134_MPEG_DVB,
                .gpiomask       = 0x0200000,
                .inputs = {{
                        .name   = name_tv,
                        .vmux   = 1,
                        .amux   = TV,
                        .tv     = 1,
                        .gpio   = 0x0200000,
                },{
                        .name   = name_comp1,
                        .vmux   = 3,
                        .amux   = LINE1,
                },{
                        .name   = name_svideo,
                        .vmux   = 8,
                        .amux   = LINE1,
                }},
                .radio = {
                        .name   = name_radio,
                        .amux   = TV,
                        .gpio   = 0x0000000,
                },
        },

```
Now you are ready to compile the modules (driver) for your card:

```
sudo make
```

Then install them. This is a manual install which sidesteps the apt packaging system. This will install the modules for the current running kernel only.

```
sudo make install
```

You are almost ready but the card still needs firmware in order to work. I am not so familiar with firmware loading in Ubuntu and so I  put my firmwares in two places. The files aren't big so this shouldn't matter.

(This section based on the instructions at [http://linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007](http://linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007))

Download [http://technotrend-online.com/download/software/219/TT_PCI_2.19h_28_11_2006.zip](http://technotrend-online.com/download/software/219/TT_PCI_2.19h_28_11_2006.zip) and unzip it.

Locate the file TT_PCI_2.19h_28_11_2006/software/OEM/PCI/App/ttlcdacc.dll Yes, this looks like a windows binary and rename it to dvb-fe-tda10046.fw Move this to /lib/firmware and link or copy to /lib/firmware/your-current-kernel. 

I also added  all the files from [http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/) to /lib/fimware/ and /lib/firmware/my-current-kernel but this is probably unneccessary.

Make sure that you have all needed DVB utilities installed ```
sudo apt-get install dvb-utils
```

Reboot your computer to ensure all needed modules are loaded for your card.

Open Kaffeine. We are using Kaffeine because it will automatically recognise your card and let you configure it with a nice GUI. If your installation was successful, you should see a configuration dialogue for your TV card. Choose a transmitter near to you, then goto DVB/Channels scan and add channels.

If you would like to use Xine or Oxine with your card you need to do this:

```
sudo scan -x 0 /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace > channels.conf
```

the '>' part way through dumps the output to a text file in your home directory. You can copy this to ~/.xine and then access these channels via 'DVB' in xine toolbar.

I haven't yet got my remote control working :( Any assistance with this gratefully received.

---

### Post by HighSide on 2007-12-10
Hi 

I followed the instructions to the dot! But it still does not want to work.

Here is the dmesg output for my card, could you paste the output of yours to compare.

[   31.922794] Linux video capture interface: v2.00
[   31.976845] saa7130/34: v4l2 driver version 0.2.14 loaded
[   31.976931] ACPI: PCI Interrupt 0000:05:06.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.976939] saa7133[0]: found at 0000:05:06.0, rev: 209, irq: 16, latency: 64, mmio: 0xfbfff800
[   31.976946] saa7133[0]: subsystem: 1461:f01d, board: Philips Tiger - S Reference design [card=109,insmod option]
[   31.976955] saa7133[0]: board init: gpio is 40000
[   32.151247] saa7133[0]: i2c eeprom 00: 61 14 1d f0 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   32.151256] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   32.151263] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 55 ff ff ff ff
[   32.151270] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151276] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 03 02 15 16 ff ff ff ff ff ff
[   32.151283] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151289] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151296] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151302] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151309] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151315] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151322] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151329] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151335] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151342] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.151348] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.159634] usbcore: registered new interface driver hiddev
[   32.204439] nvidia: module license 'NVIDIA' taints kernel.
[   32.499815] input: MOSART Semi. Wireless Keyboard & Mouse as /class/input/input2
[   32.499855] input: USB HID v1.10 Keyboard [MOSART Semi. Wireless Keyboard & Mouse] on usb-0000:00:10.0-2
[   32.528881] input: MOSART Semi. Wireless Keyboard & Mouse as /class/input/input3
[   32.528978] input,hiddev96: USB HID v1.10 Mouse [MOSART Semi. Wireless Keyboard & Mouse] on usb-0000:00:10.0-2
[   32.528994] usbcore: registered new interface driver usbhid
[   32.528998] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   32.570546] tuner' 1-004b: chip found @ 0x96 (saa7133[0])
[   32.654452] tda8290 1-004b: setting tuner address to 60
[   32.786266] tda8290 1-004b: type set to tda8290+75a
[   34.055019] saa7133[0]: registered device video0 [v4l2]
[   34.055042] saa7133[0]: registered device vbi0
[   34.055067] saa7133[0]: registered device radio0
[   34.120675] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 24
[   34.120688] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   34.120845] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9631  Thu Nov  9 17:35:27 PST 2006
[   34.120869] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   34.121284] PCI: Setting latency timer of device 0000:04:01.0 to 64
[   34.142827] saa7134 ALSA driver for DMA sound loaded
[   34.142862] saa7133[0]/alsa: saa7133[0] at 0xfbfff800 irq 16 registered as card -2
[   34.236507] DVB: registering new adapter (saa7133[0])
[   34.236513] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   34.308333] tda1004x: setting up plls for 48MHz sampling clock
[   34.324346] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   34.570652] fuse init (API version 7.8)
[   34.591977] tda1004x: found firmware revision 20 -- ok

Also when I try to scan for channels i get this message....

[  267.177789] tda1004x: setting up plls for 48MHz sampling clock
[  267.312855] tda1004x: found firmware revision 20 -- ok
[  267.419452] tda827x_probe_version: could not read from tuner at addr: 0xc2
[  267.501252] tda827xo_set_params: could not write to tuner at addr: 0xc2
[  268.079565] tda827xo_set_params: could not write to tuner at addr: 0xc2
[  268.657878] tda827xo_set_params: could not write to tuner at addr: 0xc2

Thanks for the help

---

### Post by SquiffSquiff on 2007-12-11
Here's the relevant sections of my dmesg (below). Let me know if you need the full dmesg output. New devices created at /dev/dvb/adapter0 by the installation I described are: demux0;  dvr0 ; frontend0 and  net0 (I think net0 has appeared since I tuned the card, i.e. not directly as a result of installation. From comparing the output of your dmesg to my previous post, this line looks to me like a problem:

> 
[ 31.976946] saa7133[0]: subsystem: 1461:f01d, board: Philips Tiger - S Reference design [card=109,insmod option]

Are you sure you have deleted or commented out everything in /etc/modules relating to this card?

My dmesg:

snip

[   32.694977] ACPI: PCI Interrupt 0000:05:05.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[   32.694984] saa7133[0]: found at 0000:05:05.0, rev: 209, irq: 21, latency: 32, mmio: 0xd0011000
[   32.694989] saa7133[0]: subsystem: 1461:f01d, board: Avermedia Super 007 [card=117,autodetected]
[   32.695002] saa7133[0]: board init: gpio is 40000
[   32.898559] saa7133[0]: i2c eeprom 00: 61 14 1d f0 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   32.898567] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   32.898573] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 55 ff ff ff ff
[   32.898580] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898586] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 03 02 15 16 ff ff ff ff ff ff
[   32.898591] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898597] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898603] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898609] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898615] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898621] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898627] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898633] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898639] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898645] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.898650] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.999560] tuner' 2-004b: chip found @ 0x96 (saa7133[0])
[   33.034558] tda8290 2-004b: setting tuner address to 60
[   33.097560] tda8290 2-004b: type set to tda8290+75a

snip

[   34.084531] saa7133[0]: registered device video0 [v4l2]
[   34.084680] saa7133[0]: registered device vbi0

Snip

[   34.115663] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[   34.115672] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   34.115859] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   34.116717] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   34.116723] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   34.116746] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   34.148634] DVB: registering new adapter (saa7133[0])
[   34.148641] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   34.182044] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   34.182049] saa7134_alsa: Unknown symbol snd_ctl_add
[   34.182075] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   34.182077] saa7134_alsa: Unknown symbol snd_pcm_new
[   34.182123] saa7134_alsa: disagrees about version of symbol snd_card_register
[   34.182125] saa7134_alsa: Unknown symbol snd_card_register
[   34.182172] saa7134_alsa: disagrees about version of symbol snd_card_free
[   34.182173] saa7134_alsa: Unknown symbol snd_card_free
[   34.182214] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   34.182216] saa7134_alsa: Unknown symbol snd_pcm_stop
[   34.182271] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   34.182273] saa7134_alsa: Unknown symbol snd_ctl_new1
[   34.182379] saa7134_alsa: disagrees about version of symbol snd_card_new
[   34.182381] saa7134_alsa: Unknown symbol snd_card_new
[   34.182406] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   34.182408] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   34.182450] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   34.182452] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   34.182518] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   34.182520] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   34.182631] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   34.182633] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   34.182654] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   34.182656] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[   34.186582] tda1004x: setting up plls for 48MHz sampling clock
[   34.353579] tda1004x: found firmware revision 20 -- ok

snip

[31199.917579] tda1004x: setting up plls for 48MHz sampling clock
[31200.079468] tda1004x: found firmware revision 20 -- ok
[17284.353274] tda1004x: setting up plls for 48MHz sampling clock
[17284.515250] tda1004x: found firmware revision 20 -- ok
[17363.859313] tda1004x: setting up plls for 48MHz sampling clock
[17364.024306] tda1004x: found firmware revision 20 -- ok

snip

[82238.484328] tda1004x: setting up plls for 48MHz sampling clock
[82238.646170] tda1004x: found firmware revision 20 -- ok
[82259.231969] tda1004x: setting up plls for 48MHz sampling clock
[82259.392859] tda1004x: found firmware revision 20 -- ok
[82266.748780] tda1004x: setting up plls for 48MHz sampling clock
[82266.909666] tda1004x: found firmware revision 20 -- ok
[82272.790609] tda1004x: setting up plls for 48MHz sampling clock
[82272.951499] tda1004x: found firmware revision 20 -- ok
[82277.411415] tda1004x: setting up plls for 48MHz sampling clock
[82277.572304] tda1004x: found firmware revision 20 -- ok
[82288.196017] tda1004x: setting up plls for 48MHz sampling clock
[82288.356861] tda1004x: found firmware revision 20 -- ok
[82317.271910] tda1004x: setting up plls for 48MHz sampling clock
[82317.435812] tda1004x: found firmware revision 20 -- ok
[82408.712793] tda1004x: setting up plls for 48MHz sampling clock
[82408.873683] tda1004x: found firmware revision 20 -- ok
[82502.704146] tda1004x: setting up plls for 48MHz sampling clock
[82502.867032] tda1004x: found firmware revision 20 -- ok
[82527.997740] tda1004x: setting up plls for 48MHz sampling clock
[82528.158628] tda1004x: found firmware revision 20 -- ok
[82690.536621] tda1004x: setting up plls for 48MHz sampling clock
[82690.697507] tda1004x: found firmware revision 20 -- ok
[82716.750589] tda1004x: setting up plls for 48MHz sampling clock
[82716.911471] tda1004x: found firmware revision 20 -- ok
[82737.832091] tda1004x: setting up plls for 48MHz sampling clock
[82737.993976] tda1004x: found firmware revision 20 -- ok
[82750.070643] tda1004x: setting up plls for 48MHz sampling clock
[82750.231529] tda1004x: found firmware revision 20 -- ok
[82789.066778] tda1004x: setting up plls for 48MHz sampling clock
[82789.227665] tda1004x: found firmware revision 20 -- ok
[82812.246832] tda1004x: setting up plls for 48MHz sampling clock
[82812.407720] tda1004x: found firmware revision 20 -- ok
[82875.076530] tda1004x: setting up plls for 48MHz sampling clock
[82875.237414] tda1004x: found firmware revision 20 -- ok
[82933.508216] tda1004x: setting up plls for 48MHz sampling clock
[82933.669106] tda1004x: found firmware revision 20 -- ok
[82974.017307] tda1004x: setting up plls for 48MHz sampling clock
[82974.178199] tda1004x: found firmware revision 20 -- ok
[83057.076145] tda1004x: setting up plls for 48MHz sampling clock
[83057.239033] tda1004x: found firmware revision 20 -- ok
[83064.389079] tda1004x: setting up plls for 48MHz sampling clock
[83064.551411] tda1004x: found firmware revision 20 -- ok
[83630.545143] tda1004x: setting up plls for 48MHz sampling clock
[83630.706112] tda1004x: found firmware revision 20 -- ok
[83839.601945] tda1004x: setting up plls for 48MHz sampling clock
[83839.766832] tda1004x: found firmware revision 20 -- ok
[84233.877718] tda1004x: setting up plls for 48MHz sampling clock
[84234.044557] tda1004x: found firmware revision 20 -- ok
[85123.365407] tda1004x: setting up plls for 48MHz sampling clock
[85123.526293] tda1004x: found firmware revision 20 -- ok
[85129.743055] tda1004x: setting up plls for 48MHz sampling clock
[85129.904005] tda1004x: found firmware revision 20 -- ok
[130978.795752] tda1004x: setting up plls for 48MHz sampling clock
[130978.957643] tda1004x: found firmware revision 20 -- ok
[72712.470996] tda1004x: setting up plls for 48MHz sampling clock
[72712.632724] tda1004x: found firmware revision 20 -- ok

I also forgot to mention in my previous post that the line re scanning was specific to my transmitter. You should replace uk-CrystalPalace in the below line with your appropriate transmitter- listed at /usr/share/doc/dvb-utils/examples/scan/dvb-t/

```
sudo scan -x 0 /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace > channels.conf
```

The output of this on my box begins

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 505833333 0 3 9 1 0 0 0
>>> tune to: 505833333:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
0x0000 0x1044: pmt_pid 0x1044 BBC -- BBC ONE (running)

Then further channels listed one per line with a few ...NONE lines in between, ending 

Network Name 'Crystal Palace'
dumping lists (77 services)
Done.

It looks to (naive) me that your tuner isn't even being recognised by scan in your case, i.e. it isn't installed or loaded correctly.

Let us know if you are successful or not

---

### Post by steefjeqv on 2007-12-11
Hi Stu & SquiffSquiff,

Great to see that the Avermedia is working (thanks to SquifSquif).

As SquifSquif mentions, your card isn't autodetected.

The "insmod option" means that detection is forced (by /etc/modules ?) to use card 109.

Greetings,
Steven

---

### Post by HighSide on 2007-12-11
Hi 

There are no references to saa7134 in /etc/modules, I did find a file modprobe.conf that listed the card as card=109.

---

### Post by HighSide on 2007-12-11
Hey Steve, SquiffSquiff

I'm now watching TV on my PC!!!:):):):):):)

I edited the file modprobe.conf to read card=117 and it now works, the card is not autodetected but hey, its working. Also the scan doesn't work yet but kaffine is nice enough for me.

Thanks for all the help, I really appreciate it. I was close to giving up!

---

### Post by steefjeqv on 2007-12-11
Hello Stu,

Very pleased to hear your card is working.

When you've recovered from all the modprobing, dmesg and so on, you may want to take a look at this (only if you're interested in a multi-media center) :

[http://www.linuxtv.org/vdrwiki/index.php/Introduction]("http://www.linuxtv.org/vdrwiki/index.php/Introduction")

Greetings,
Steven

---

### Post by SquiffSquiff on 2007-12-11
@HighSide I'm so pleased that you finally got it working for TV reception, thank you for letting us know. It seems to me from your dmesg  that you are running x86_64 so perhaps autodetection is not working in 64 bit? Alternatively, are you still running Feisty, as per your profile? @steefjeqv Thanks also for your support.

Hopefully, this thread will help take this card into mainstream Ubuntu support maybe from April. As it is so inexpensive (mine was £20GBP in Maplin last week) it's a really nice perk for even a budget system. Maybe some wizard will help us with the remote- since it works via a IR Sensor dongle on the card itself, I can't even begin with LIRC. As it is I'm considering getting a separate remote, maybe even a (shudder) MS Media centre remote since it's so common and supposedly supported.

---

### Post by steefjeqv on 2007-12-11
Hi SquifSquif,

VDR will most likely work with the remote.

It uses a wide range of plugins (including one called vdr-remote).

It's available through synaptic, but it may take some tinkering to get it working.

I'm using VDR as a multi-media server (based on a Debian Etch system).


Greetings,
Steven

---

### Post by gorsh on 2007-12-30
Thanks this thread, i get my AVerTV Super 007 ready!!!, using TvTime.

Any idea about the remote control??
the output of "cat /proc/bus/input/devices" is not showing any entry related to this... :confused:

thanks!!!

---

### Post by sam028 on 2007-12-31
Hi all.

I have an AVerTV **Hybrid** Super 007, try few things, and it seems to work with **card=109**.
As I have not already get an antenna, i'm not sure it will works, but my dmesg seems fine.


But with **card=117**, 

[   15.596000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   15.596000] ACPI: PCI Interrupt 0000:04:05.0[A] -> GSI 20 (level, low) -> IRQ 21
[   15.596000] saa7133[0]: found at 0000:04:05.0, rev: 209, irq: 21, latency: 64, mmio: 0xfdbff000
[   15.596000] saa7133[0]: subsystem: 1461:f01d, board: AVerMedia Cardbus TV/Radio (E506R) [card=117,insmod option]
[   15.596000] saa7133[0]: board init: gpio is 40000
[   15.836000] saa7133[0]: i2c eeprom 00: 61 14 1d f0 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   15.836000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   15.836000] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 55 ff ff ff ff
[   15.836000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.836000] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 05 32 15 76 8b 0c ff ff ff ff
[   15.836000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.836000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.836000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.900000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   15.936000] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   15.936000] BUG: unable to handle kernel paging request at virtual address fffefffe
[   15.936000]  printing eip:
[   15.936000] c01fdf3e
[   15.936000] *pde = 00004067
[   15.936000] *pte = 00000000
[   15.936000] Oops: 0000 [#1]
[   15.936000] SMP
[   15.936000] Modules linked in: snd_hda_intel snd_pcm_oss snd_mixer_oss tuner snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device saa7134 wlan_scan_sta video_buf compat_ioctl32 ir_kbd_i2c ir_common ath_rate_sample videodev parport_pc parport ath_pci snd soundcore v4l2_common v4l1_compat psmouse wlan ath_hal(P) i2c_piix4 i2c_core pcspkr k8temp serio_raw snd_page_alloc ati_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache sg sd_mod ide_cd cdrom ata_generic usbhid hid ahci libata scsi_mod ohci1394 ieee1394 atiixp ide_core ehci_hcd r8169 ohci_hcd usbcore thermal processor fan fuse apparmor commoncap
[   15.936000] CPU:    1
[   15.936000] EIP:    0060:[<c01fdf3e>]    Tainted: P       VLI
[   15.936000] EFLAGS: 00010097   (2.6.22-14-generic #1)
[   15.936000] EIP is at vsnprintf+0x42e/0x630
[   15.936000] eax: fffefffe   ebx: c044e8e1   ecx: fffefffe   edx: fffffffe
[   15.936000] esi: f8bb2700   edi: fffefffe   ebp: c044ecc0   esp: f799fcc4
[   15.936000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
[   15.936000] Process modprobe (pid: 3971, ti=f799e000 task=f7a54f90 task.ti=f799e000)
[   15.936000] Stack: ffffffff ffffffff 0000000a fffffffe ffffffff 00000002 0000a1ff 00000400
[   15.936000]        c044e8c0 00000000 ffffffff ffffffff ffffffff fffffffe f8bb27d8 00000400
[   15.936000]        f7a42c00 00000000 f7cd3c00 c01fe294 f799fdb4 f7a42c00 c012891c f799fda0
[   15.936000] Call Trace:
[   15.936000]  [<c01fe294>] vscnprintf+0x14/0x20
[   15.936000]  [<c012891c>] vprintk+0x5c/0x370
[   15.936000]  [<c0135457>] blocking_notifier_call_chain+0x17/0x20
[   15.936000]  [<c02f182e>] klist_node_init+0x2e/0x50
[   15.936000]  [<c02f186e>] klist_add_tail+0x1e/0x50
[   15.936000]  [<c026123e>] device_bind_driver+0x1e/0x30
[   15.936000]  [<c026128d>] device_attach+0x3d/0x90
[   15.936000]  [<c01fa1ff>] kobject_get+0xf/0x20
[   15.936000]  [<c0128c4b>] printk+0x1b/0x20
[   15.936000]  [<f8babb94>] default_tuner_init+0x54/0xb0 [tuner]
[   15.936000]  [<f8ba9c27>] set_type+0xd7/0x400 [tuner]
[   15.936000]  [<f89f103e>] i2c_attach_client+0xee/0x190 [i2c_core]
[   15.936000]  [<f8baa2fa>] tuner_attach+0x12a/0x330 [tuner]
[   15.936000]  [<f89f0bbe>] i2c_probe_address+0x3e/0x130 [i2c_core]
[   15.936000]  [<f89f1d1b>] i2c_probe+0x21b/0x230 [i2c_core]
[   15.936000]  [<f8baa1d0>] tuner_attach+0x0/0x330 [tuner]
[   15.936000]  [<c02615e3>] driver_create_file+0x33/0x50
[   15.936000]  [<f8baa1d0>] tuner_attach+0x0/0x330 [tuner]
[   15.936000]  [<f89f1805>] i2c_register_driver+0xd5/0x120 [i2c_core]
[   15.936000]  [<c014a7d1>] sys_init_module+0x151/0x1a00
[   15.936000]  [<c01fb39f>] prio_tree_insert+0x1f/0x250
[   15.936000]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   15.936000]  =======================
[   15.936000] Code: fd ff ff c6 03 25 e9 39 fd ff ff 8d 47 04 89 44 24 50 8b 3f 81 ff ff 0f 00 00 77 05 bf c4 22 38 c0 8b 54 24 2c 89 f9 89 c8 eb 06 <80> 38 00 74 07 40 4a 83 fa ff 75 f4 29 c8 89 c6 8b 44 24 28 f6
[   15.936000] EIP: [<c01fdf3e>] vsnprintf+0x42e/0x630 SS:ESP 0068:f799fcc4
[   15.936000] saa7133[0]: registered device video0 [v4l2]
[   15.936000] saa7133[0]: registered device vbi0
[   15.936000] saa7133[0]: registered device radio0
[   15.956000] saa7134 ALSA driver for DMA sound loaded
[   15.956000] saa7133[0]/alsa: saa7133[0] at 0xfdbff000 irq 21 registered as card -2
[   16.116000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   16.128000] mt352_read_register: readreg error (reg=127, ret==-5)
[   16.128000] saa7133[0]/dvb: frontend initialization failed


Does anyone here has tested the Hybrid version of the Super 007 ?

---

### Post by sam028 on 2007-12-31
Well, with an Hybrid Super 007, it's not working:


 sudo scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/fr-Rennes 
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/fr-Rennes
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 562000000 0 1 9 1 1 0 0
initial transponder 586000000 0 1 9 1 1 0 0
initial transponder 650000000 0 1 9 1 1 0 0
initial transponder 674000000 0 1 9 1 1 0 0
initial transponder 626000000 0 1 9 1 1 0 0
>>> tune to: 562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 586000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 586000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 650000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 650000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 674000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 674000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 626000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 626000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

My dmesg:

[   13.964000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   13.964000] ACPI: PCI Interrupt 0000:04:05.0[A] -> GSI 20 (level, low) -> IRQ 21
[   13.964000] saa7133[0]: found at 0000:04:05.0, rev: 209, irq: 21, latency: 64, mmio: 0xfdbff000
[   13.964000] saa7133[0]: subsystem: 1461:f01d, board: Philips Tiger - S Reference design [card=109,insmod option]
[   13.964000] saa7133[0]: board init: gpio is 40000
[   14.100000] saa7133[0]: i2c eeprom 00: 61 14 1d f0 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   14.100000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   14.100000] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 55 ff ff ff ff
[   14.100000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.100000] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 05 32 15 76 8b 0c ff ff ff ff
[   14.100000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.100000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.100000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.268000] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   14.268000] /home/sam/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[   14.268000] tuner 0x4b: Configuration acknowledged
[   14.268000] /home/sam/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[   14.320000] tuner 1-004b: setting tuner address to 60
[   14.324000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   14.360000] tuner 1-004b: type set to tda8290+75a
[   14.532000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   15.212000] NET: Registered protocol family 17
[   15.700000] saa7133[0]: registered device video0 [v4l2]
[   15.700000] saa7133[0]: registered device vbi0
[   15.700000] saa7133[0]: registered device radio0
[   15.804000] saa7134 ALSA driver for DMA sound loaded
[   15.804000] saa7133[0]/alsa: saa7133[0] at 0xfdbff000 irq 21 registered as card -2
[   15.924000] DVB: registering new adapter (saa7133[0])
[   15.924000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   15.996000] tda1004x: setting up plls for 48MHz sampling clock
[   16.060000] lp0: using parport0 (interrupt-driven).
[   16.104000] it87: Found IT8716F chip at 0x228, revision 1
[   16.104000] it87: in3 is VCC (+5V)
[   16.104000] it87: in7 is VCCH (+5V Stand-By)
[   16.284000] tda1004x: found firmware revision 29 -- ok
[   16.564000] tda827x_probe_version: could not read from tuner at addr: 0xc2
[   16.284000] tda1004x: found firmware revision 29 -- ok
[   16.564000] tda827x_probe_version: could not read from tuner at addr: 0xc2

My /etc/modprobe.d/saa7134 :

sam@mce:~$ more /etc/modprobe.d/saa7134 
options saa7134 card=109 

lspci -v:

04:05.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
        Subsystem: Avermedia Technologies Inc Unknown device f01d
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at fdbff000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [40] Power Management version 2

lspci -vn:

04:05.0 0480: 1131:7133 (rev d1)
        Subsystem: 1461:f01d
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at fdbff000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [40] Power Management version 2



I spent few days on all that stuff, it still not working, I'm going to be mad !!!

Help welcome :)

An an happy new year !!!

---

### Post by HighSide on 2008-01-02
Sam028,

I could not get a the scan command  to work in terminal, I can only use Kaffine to view TV. Also my card is listed as 117 not 109.

---

### Post by dpailler on 2008-01-16
Hello,
AverTV Hybrid Super 007 works just fine  :guitar:

1) You must have sources of your Kernel (mine is 2.6.23.12)
Good site for compiling Debian way:
[http://pyfourmond.free.fr/Compilation-Noyau-Linux.htm](http://pyfourmond.free.fr/Compilation-Noyau-Linux.htm)

2)Get v4l-dvb from [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) but latest bug for me , so don't use hg as it says ons this forum, but take revision 6872 (clic on changelog)

3) You don(t have to recompile your kernel because v4l-dvb Makefile have really nice option:
cd v4l-dvb-0cd7bf1cf2c3/
As root :
make rmmod  #-----> v4l-dvb get off everything that was charged by previous v4l-dvb  (like those of your Kernel)

make rminstall  #------> v4l-dvb uninstall all previous version

3)Modified file saa7134-cards.c as it said in this forum (Insert it  after :
struct saa7134_board saa7134_boards[] = {
but I'm not sure it is really necessary)

4)then make  make install

5) Install the firmware as it said on this forum,

6) Reboot and every thing works fine.

7) analogic and numeric tv seem to work I don't have tested radio neither capture with SVHS

Some thing funny:
With vlc , Timeshift is possible and very easy:
I record one french TV with out reencoding:

 vlc --ttl 12 dvb:// --dvb-frequency=586167000 --dvb-adapter=0 --dvb-bandwidth=8 --program=257  --sout '#standard{access=file, mux=ps,url=/home/david/films/france2.mpg}

And even if france2.mpg is not finished, I can watch it with Totem (for exemple) , I can jump what I don't want to see , make pause , stop , When I want.

Nice isn't it ?

I think it's important to record the flux and not modified it (just PS)

Bye
David P

:guitar:

---

### Post by wil-m on 2008-02-23
i have bought this card about month ago and made it work with big a help of this forum. thank you!

anybody luck with remote? i didnt found any solution

sudo cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input1
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd mouse1 event5 
B: EV=1f
B: KEY=37fff 4ac332f bf084444 0 0 ff0001 1f84 8a37cc00 667bfa dd71dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0
B: MSC=10

sudo lsmod | grep ir
ir_kbd_i2c             10896  1 saa7134
ir_common              36484  2 saa7134,ir_kbd_i2c

the input device doesnt exist :(

---

### Post by HighSide on 2008-03-03
Hi Wil M

I have not tried to get the card working with a remote yet, but it is next on my list.

If you have any luck please let us know.

---

### Post by Indus on 2008-05-01
Big thanks to all of you, my AVerTV Super 007 works fine on 7.10. Folowing the steps in this forum I was able to make it work although I am quite new to Linux.:)

---

### Post by nowinter on 2008-05-07
> **dpailler said:**
> Hello,
AverTV Hybrid Super 007 works just fine  :guitar:
Sure you have a **Hybrid**? You then seem the only one to have success so far. I have Hybrid 007 and feel I f..ed up myself when I preferred it to regular Super 007.
I did all the stuff you described (not exact stuff, I'm actually on gentoo), except for adding one more struct to .c file in the v4l-dvb compilation - it's just irrelevant, and: 
1) v4l modules (from Mercurial) are compiled and loaded smoothly, 
[I]saa7130/34: v4l2 driver version 0.2.14 loaded
[13917.006724] saa7133[0]: found at 0000:00:06.0, rev: 209, irq: 20, latency: 32, mmio: 0xe2000000
[13917.007693] saa7133[0]: subsystem: 1461:f01d, board: Avermedia Super 007 [card=117,autodetected][/I]

2) the firmware is loaded atomatically..
[I][13920.403769] tda1004x: setting up plls for 48MHz sampling clock
[13920.570531] tda1004x: found firmware revision 20 -- ok
[16452.271319] tda1004x: setting up plls for 48MHz sampling clock
[16452.443623] tda1004x: found firmware revision 20 -- ok[/I]

_But, I have no signal_. The card is connected to a digibox (IRD, satellite receiver) composite video output with composite-svideo cable.

So, it is either my card is not same as yours (both Super 007 and Hybrid Super 007 seem to have same PCI id1461:f01d), or it is> I don't have tested radio neither capture with SVHS "capture" that is not working for me with this card..

David, can you please cooperate on the following:
1) see if you can capture any "non-TV" S-Video output? Camera, VHS, PVR, game console..
2) dmesg|egrep '(saa)|(tda)|(tuner)' after you boot up

Thanks!

---

### Post by amitrke on 2008-05-30
Mercurial helped me get my Avertv Super 007 working, but does anyone know how to get FM Radio working on this card. also has any one been successfully been able to use the Remote control provided with the card.

---

### Post by steefjeqv on 2008-05-31
Hi,

I'm not sure if I can help you with the FM radio part.

Do you want to use the remote to control your OS or do you want to use it to control a multimedia application ?

First you'll have to check if the remote is recognized using dmesg (terminal).

sudo dmesg | grep remote


Greetings,
Steven

---

### Post by amitrke on 2008-06-13
I tried dmesg|grep remote but no results.
then I tried  dmesg|grep radio I got the following response
[   74.966557] videodev: "SF16FMR2 radio" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[   74.966562] SF16FMR2 radio card driver at 0x384.
[   75.225859] /home/amit/v4l-dvb/v4l/dsbr100.c: v0.41:D-Link DSB-R100 USB FM radio driver
[   78.564025] radio-typhoon: You must set an I/O address with io=0x316 or io=0x336
[   78.665571] USB radio driver for Si470x FM Radio Receivers, Version 1.0.7
[   78.665622] usbcore: registered new interface driver radio-si470x
[   78.903308] radio-sf16fmi: No PnP card found.
[113743.144299] radio-typhoon: You must set an I/O address with io=0x316 or io=0x336
[113743.347684] radio-sf16fmi: No PnP card found.


does it mean that I should keep the faith that radio will be working !

---

### Post by spaceoff on 2008-07-19
Hi guys, i've recently bought avertv super 007 tuner and I got a problem. I plugged it in, then i began to install the cd, at 3/4 of the installation it gave me tab for "found new hardware", after that an error comes out - "Cannot update plugandplay driver" ? What could be the cause of that ?

---

