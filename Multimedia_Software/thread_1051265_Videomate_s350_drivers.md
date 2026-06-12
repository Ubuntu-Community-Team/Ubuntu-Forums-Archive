---
title: "Videomate s350 drivers"
date: 2009-01-26
forum: Multimedia Software
---

### Post by Purple8 on 2009-01-26
Does anyone know if there is any drivers for this satellite card. Ive tried using MYtv but it picks it up as  standard TV card.
Bit of a newbie

---

### Post by Purple8 on 2009-02-15
bump somebodys got to know. should have checked compatible cards first i know:redface:

---

### Post by sijeffrey on 2009-03-12
Hi, I'm also interested in this card. I have found alot on the Compro T750, but nothing on the satellite DVB-S cards. I see also that the Compro website lists the Linux driver as available in Q3 2008, which has well passed now. Let me know if you get anywhere.

---

### Post by RoboNuggie on 2009-05-24
Hi

Just to revive this thread a little......

I don't think that there will ever be a driver for the Videomate S350....

There was one briefly that appeared for Mandriva/Mandrake, but it quickly went as it violated the GPL.... Compro stated that one would come Q3 2008, but I think that was just wishful thinking...... oh, well.....

---

### Post by Jimbley on 2009-05-24
Have a look at:

[http://linuxtv.org/wiki/index.php/Talk:Compro_VideoMate_S350]("http://linuxtv.org/wiki/index.php/Talk:Compro_VideoMate_S350")

Follow the link to the patch page. Everything other than 2 way diseqc should work.

Cheers

Jim

---

### Post by RoboNuggie on 2009-05-25
Wow, thanks Jim, I will have to try it out....

---

### Post by eldo on 2009-06-05
> **sijeffrey said:**
> Hi, I'm also interested in this card. I have found alot on the Compro T750, but nothing on the satellite DVB-S cards. I see also that the Compro website lists the Linux driver as available in Q3 2008, which has well passed now. Let me know if you get anywhere.
Hi,sijeffrey
And what did you about work Compro t750 on Ubuntu? I have this card, but it didn't work on any Linux distros... :( Please help. Thanks for any information.

---

### Post by Jimbley on 2009-06-07
Hi folks. I've been contributing to the LinuxTV wiki for a while now. I also have a T750 but the support for it is very limited (analog only AFAIK). I check the mailing lists regularly but despite several attempts by different people, DVB is still not working properly. I'm hoping to speak to one of the developers via IRC and I'll post results from that as soon as I know.

Cheers

Jim

---

### Post by Purple8 on 2009-06-10
Err probably a dumb question, but how do you use load the new driver.

Thanks

---

### Post by eldo on 2009-06-11
> **Jimbley said:**
> Hi folks. I've been contributing to the LinuxTV wiki for a while now. I also have a T750 but the support for it is very limited (analog only AFAIK). I check the mailing lists regularly but despite several attempts by different people, DVB is still not working properly. I'm hoping to speak to one of the developers via IRC and I'll post results from that as soon as I know.

Cheers

Jim

Hi, Jim
Analog TV work on your t750? Because on my Ubuntu it don't work. I have compiled the latest v4l-dvb, make latest kernel , but nothing happend. If you have any information please help me.

---

### Post by rbsdude on 2009-07-13
Hello Guys,

There has been some real movement on the support for S350 Compro DVB-S card . Working drivers have been made available at :
[http://mercurial.intuxication.org/hg/v4l-dvb-commits/v4l-dvb-commits?cmd=](http://mercurial.intuxication.org/hg/v4l-dvb-commits/v4l-dvb-commits?cmd=)

You can see the test report from the people that have tried it here :

[http://patchwork.kernel.org/patch/31987/](http://patchwork.kernel.org/patch/31987/)

BR/

RD

---

### Post by chumps on 2009-07-18
Can someone please tell me how to install this driver. I can see the patch as text on the website at [http://patchwork.kernel.org/patch/31987/](http://patchwork.kernel.org/patch/31987/) dont know what to save this as or how to install it

---

### Post by DominicF on 2009-11-20
hi,

Just got one of these cards compro s350 today but having problems (as usual).  I'm using mythbuntu 9.10, but got a feeling it's not being picked properly.

I'm starting to follow these instruction to tune the card but fails with the message below.

[http://parker1.co.uk/mythtv_freesat.php](http://parker1.co.uk/mythtv_freesat.php)

using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

My question: is the patch for the s350 incorporated in this release of Mythbuntu?  If not, I need some instructions to apply the patch.

Many thanks.

---

### Post by DominicF on 2009-11-20
ok, found some more info.... apparently I have a newer version of the compro s350 card (using Philips SAA7135) and someone has got it to work:

 [http://osdir.com/ml/linux-media/2009-06/msg01256.html](http://osdir.com/ml/linux-media/2009-06/msg01256.html)

He modifies the patch and applies it.  

I still don't yet how to apply the patch.

---

### Post by DominicF on 2009-11-22
My Compro videomate S350 is detected as a T750 card:

 5.750330] saa7130/34: v4l2 driver version 0.2.15 loaded
[    5.750400] saa7134 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.750408] saa7133[0]: found at 0000:03:01.0, rev: 209, irq: 17, latency: 64, mmio: 0xcfcff000
[    5.750415] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]
[    5.750432] saa7133[0]: board init: gpio is 843f00
[    5.750438] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.901771] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    5.901784] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[    5.901795] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 03 01 08 ff 00 87 ff ff ff ff
[    5.901882] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.901894] saa7133[0]: i2c eeprom 40: ff d6 00 c0 86 1c 02 01 02 ff ff ff ff ff ff ff
[    5.901905] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[    5.901916] saa7133[0]: i2c eeprom 60: 35 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.901928] saa7133[0]: i2c eeprom 70: 00 00 00 01 4e c1 ff ff ff ff ff ff ff ff ff ff
[    5.901939] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.901950] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.901962] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.901973] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.901984] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.901996] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.902007] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.902018] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.902032] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[    6.019608] saa7133[0]: dsp access error
[    6.019611] saa7133[0]: dsp access error
[    6.019636] saa7133[0]: dsp access error
[    6.019638] saa7133[0]: dsp access error
[    6.019703] saa7133[0]: registered device video0 [v4l2]
[    6.019727] saa7133[0]: registered device vbi0
[    6.019751] saa7133[0]: registered device radio0


I'm trying to follow instructions to modify the drivers from v4l but not sure if my changes are taken, this is what I do:

$ sudo aptitude install mercurial

$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

Now I have a local copy.  I cd into v4l-dvb/linux/drivers/media/video/saa7134

from the patch file it adds a number of lines to numerous file.  According from the link :

Changing the PCI Vendor ID to 0x7133 in the S350 patch fixed this, but unfortunately this is
the same PCI Vendor / Device / subvendor / subdevice as the Compro
Videomate T750 - an entirely different, DVB-T board.

from the link Next mod was:
by trial and error found a GPIO bit that appears to turn LNB voltage on and off. Instead of 0x8000 used in Jan's patch, use 0xC000 for GPIO setup.

Where do I find where to change these settings?  I thought I found it and changed it.  I tried other things too by commenting out references to the T750 board.

In the /v4l-dvb top-level directory I had run (I'm not sure if this is all I have to do):

make all

sudo make install

I then ran dmesg again but the card still comes up as a compro T750 and not the S350.

So, I'm not sure how to apply the changes once I edit these files, am I missing a step?

---

### Post by DominicF on 2009-11-22
Getting a little further.  Realised that the make all command fails to build some of the other drivers before it gets to the ones I have edited.

Need to as a workaround:

disable the firedtv driver by modifying the
./v4l/.config file and changing '=m' to '=n' on the firedtv line.


Once I did this the make all command got further in building more of the driver and stopped at the saa7134-inputs.o as there is a error in the code with some of the declarations.  I didn't touch this file so I don't know why it has crashed out here.  I'm thinking from ready another thread that it may need the kernel source to be present instead of the headers.... I will try this next.

---

### Post by DominicF on 2009-12-01
I started again with a fresh copy of the v4l-dvb drivers:

$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

disable the firedtv driver by modifying the
v4l-dvb/v4l/.config file and changing '=m' to '=n' on the firedtv line.

In the v4l-dvb top level directory
$ make
$ sudo make install

I'm back to where I started - the card is recongnised incorrectly as T750, so we need to force to card=169 which is the S350.  When I do this the system complains that one of the modules is still in use.  I tried various things but found if I put it into the blacklist it doesn't get loaded.

edit:
/etc/modprobe.d/blacklist.conf

add a new line with the text:
saa7134-alsa 

Reboot the system

To unload the current driver (T750):
$ modprobe -vr saa7134-alsa saa7134-dvb

At this point edit /etc/modprobe.d/blacklist.conf and comment out the line you put in:
#saa7134-alsa

Then force the card 169 to be loaded:
modprobe -v saa7134 card=169 gpio_tracking=1

At the point the card is recognised as the S350 !!! type dmesg to show the status.

Now to scan for some channels:

sudo apt-get update
sudo apt-get install dvb-apps mplayer

scan -x0 /usr/share/dvb/dvb-s/Astra-19.2E | tee channels.conf

This is where I'm stuck!  It starts to scan but soon stops saying tuning failed.  Typing dmesg shows:

[ 2195.908528] DVB: adapter 0 frontend 0 frequency 7401500 out of range (950000..2150000)
 
Not sure how to progress from here.

---

### Post by Graham17655 on 2009-12-21
I'm getting this card in about 4 days time.  Have you got it to work yet?

---

### Post by DominicF on 2009-12-21
No, I haven't managed to get it to work.  I think it's going to need another re-write of the driver to get my version of the S350 card to work.  It tried all the suggestions and managed to get recongnised as the S350 with firmware loaded correctly but fails to tune to channels.

So, at the moment the card is sitting around gathering dust.

---

### Post by Tradeout on 2009-12-30
Has anyone had any joy with this card yet? I have also made the mistake of purchasing it for a mythtv setup, and am trying to get it working!

---

### Post by Graham17655 on 2009-12-31
Not yet.  I think I have a newer version of the card.  lspci -vvnn gives this:
00:0b.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1) 
(snip)
Whereas those people who have reported it working seem to have rev d0.
My card is recognised as a T750 although it is a S350.  When  I try to force it to card = 169 the machine won't boot.
So far I've tried to recompile and alter the code. The closest I got it said it was initialising the dvb front end only to fail.   I have emailed a few people who have their names in the code but had no reply yet.  Not sure if this is the right approach.
If you get it working let me know what you did please.
Many thanks and a Happy New Year!

---

### Post by Tradeout on 2010-01-01
Graham,
have u tried  installing the vl4-dvb drivers with
 the s350 patch applied?

Happy new year

---

### Post by cookstar on 2010-01-01
I've managed to get my Compro S350 working but thats on Fedora 12 with a 2.6.32 kernel. I also had to change 0x8000 to 0xC000 for the LNB voltage on.

---

### Post by Tradeout on 2010-01-01
That's some good news, cookstar.

Can you give us a run down on what you did?
I'm pretty new to Linux so all help is much apreciated.

---

### Post by cookstar on 2010-01-02
Sure,

Well at first I tried just getting the latest v4l-dvb source, but everytime i built the new saa7134 modules i kept getting a oops occuring on boot at the udev stage. This was on a stock Fedora 12 build. The way i got it to work was to install the 2.6.32 fedora kernel source. From there I changed the kernel source module code for the saa7134 driver (linux/drivers/media/video/saa7134/saa7134-dvb.c) and changed:-

[I]    case SAA7134_BOARD_VIDEOMATE_S350:
        dev->has_remote = SAA7134_REMOTE_GPIO;
        saa_andorl(SAA7134_GPIO_GPMODE0 >> 2,   0x00008000, 0x00008000);
        saa_andorl(SAA7134_GPIO_GPSTATUS0 >> 2, 0x00008000, 0x00008000);
        break;
[/I] 

to

[I]    case SAA7134_BOARD_VIDEOMATE_S350:
        dev->has_remote = SAA7134_REMOTE_GPIO;
        saa_andorl(SAA7134_GPIO_GPMODE0 >> 2,   **0x0000C000, 0x0000C000**);
        saa_andorl(SAA7134_GPIO_GPSTATUS0 >> 2, **0x0000C000, 0x0000C000**);
        break;[/I]

From here it was a case of just builiding the new kernel and installing it. 
After booting this kernel the S350 was working and was able to scan for channels.
I have mythtv running and managed to scan with this as well. Only problem I have is no
sound on myth, but I should get to the bottom of this soon.

Fair enough this is on fedora and not ubuntu but the instructions in the post
earlier about getting v4l-dvb drivers making the source code change and building
 should work just fine.

Hope it helps.

---

### Post by Tradeout on 2010-01-02
Thanks cookstar.

You think you'll get the sound running in myth?

---

### Post by DominicF on 2010-01-03
Hi Cookstar,

On your Compro S350 what does running lspci -vvnn give you and also dmesg for the saa7133 eprom content?  Just want to check we have same version of the card.

Thanks.

---

### Post by cookstar on 2010-01-04
Hi 

How are you getting on?

$ lspci -vvnn

03:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder [1131:7134] (rev 01)
    Subsystem: Compro Technology, Inc. Videomate DVB-T300 [185b:c900]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (21000ns min, 8000ns max)
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at fdcff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134


dmesg:-
Linux video capture interface: v2.00
saa7130/34: v4l2 driver version 0.2.15 loaded
saa7134 0000:03:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
saa7134[0]: found at 0000:03:00.0, rev: 1, irq: 20, latency: 32, mmio: 0xfdcff000
saa7134[0]: subsystem: 185b:c900, board: Compro VideoMate S350/S300 [card=169,insmod option]
saa7134[0]: board init: gpio is 843f00
input: saa7134 IR (Compro VideoMate S3 as /devices/pci0000:00/0000:00:1e.0/0000:03:00.0/input/input6
IRQ 20/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: 01 40 01 02 02 01 03 01 08 ff 00 87 ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 40: ff d6 00 c0 86 1c 02 01 02 ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
saa7134[0]: i2c eeprom 60: 35 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 70: 00 00 00 11 03 a7 ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
i2c i2c-6: Invalid 7-bit address 0x7a
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
dvb_init() allocating 1 frontend
DVB: registering new adapter (saa7134[0])
DVB: registering adapter 0 frontend 0 (Zarlink ZL10313 DVB-S)...
device-mapper: multipath: version 1.1.0 loaded
saa7134 ALSA driver for DMA sound loaded
IRQ 20/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
saa7134[0]/alsa: saa7134[0] at 0xfdcff000 irq 20 registered as card -1

---

### Post by Tradeout on 2010-01-09
Did you get the sound working cookstar?
 
I'm looking to have another try with installing tomorrow and thinking about taken the fedora route.

---

### Post by Tradeout on 2010-01-11
Well I can't even force the card in mythbuntu.
I've tried adding 'options saa7134 card=169' into modprobe.d as advised on the vl4-dvbwiki, but that stops ubuntu from booting.

Anyone else any futher?

---

### Post by Graham17655 on 2010-01-12
I've got it working (the rev d1 version) with help from one of the developers. 
Tradeout,
You are almost there with the options saa7134 card=169 but you also need to compile the v4l-dvb code with a patch to *remove* the IR which is what is causing the crash. I'll post the code in a minute when I get access to my email (along with instructions).

---

### Post by Graham17655 on 2010-01-12
Instructions to get it working (install mercurial first)
hg clone [http://linuxtv.org/hg/v4l-dvb]("https://netmail.uk.agcocorp.com/exchweb/bin/redir.asp?URL=http://linuxtv.org/hg/v4l-dvb")
This will download the latest source code now go into the directory v4l-dvb and save the following as remove-ir.patch
 
> diff -r 59e746a1c5d1 linux/drivers/media/IR/ir-keymaps.c
--- a/linux/drivers/media/IR/ir-keymaps.c Wed Dec 30 09:10:33 2009 -0200
+++ b/linux/drivers/media/IR/ir-keymaps.c Fri Jan 08 01:04:53 2010 +0200
@@ -3205,57 +3205,7 @@
};
EXPORT_SYMBOL_GPL(ir_codes_evga_indtube_table);
 
-static struct ir_scancode ir_codes_videomate_s350[] = {
- { 0x00, KEY_TV},
- { 0x01, KEY_DVD},
- { 0x04, KEY_RECORD},
- { 0x05, KEY_VIDEO}, /* TV/Video */
- { 0x07, KEY_STOP},
- { 0x08, KEY_PLAYPAUSE},
- { 0x0a, KEY_REWIND},
- { 0x0f, KEY_FASTFORWARD},
- { 0x10, KEY_CHANNELUP},
- { 0x12, KEY_VOLUMEUP},
- { 0x13, KEY_CHANNELDOWN},
- { 0x14, KEY_MUTE},
- { 0x15, KEY_VOLUMEDOWN},
- { 0x16, KEY_1},
- { 0x17, KEY_2},
- { 0x18, KEY_3},
- { 0x19, KEY_4},
- { 0x1a, KEY_5},
- { 0x1b, KEY_6},
- { 0x1c, KEY_7},
- { 0x1d, KEY_8},
- { 0x1e, KEY_9},
- { 0x1f, KEY_0},
- { 0x21, KEY_SLEEP},
- { 0x24, KEY_ZOOM},
- { 0x25, KEY_LAST}, /* Recall */
- { 0x26, KEY_SUBTITLE}, /* CC */
- { 0x27, KEY_LANGUAGE}, /* MTS */
- { 0x29, KEY_CHANNEL}, /* SURF */
- { 0x2b, KEY_A},
- { 0x2c, KEY_B},
- { 0x2f, KEY_CAMERA}, /* Snapshot */
- { 0x23, KEY_RADIO},
- { 0x02, KEY_PREVIOUSSONG},
- { 0x06, KEY_NEXTSONG},
- { 0x03, KEY_EPG},
- { 0x09, KEY_SETUP},
- { 0x22, KEY_BACKSPACE},
- { 0x0c, KEY_UP},
- { 0x0e, KEY_DOWN},
- { 0x0b, KEY_LEFT},
- { 0x0d, KEY_RIGHT},
- { 0x11, KEY_ENTER},
- { 0x20, KEY_TEXT},
-};
-struct ir_scancode_table ir_codes_videomate_s350_table = {
- .scan = ir_codes_videomate_s350,
- .size = ARRAY_SIZE(ir_codes_videomate_s350),
-};
-EXPORT_SYMBOL_GPL(ir_codes_videomate_s350_table);
+
 
/* GADMEI UTV330+ RM008Z remote
Shine Liu <shinel@foxmail.com>
diff -r 59e746a1c5d1 linux/drivers/media/video/saa7134/saa7134-cards.c
--- a/linux/drivers/media/video/saa7134/saa7134-cards.c Wed Dec 30 09:10:33 2009 -0200
+++ b/linux/drivers/media/video/saa7134/saa7134-cards.c Fri Jan 08 01:04:53 2010 +0200
@@ -7036,9 +7036,9 @@
saa_andorl(SAA7134_GPIO_GPSTATUS0 >> 2, 0x80040100, 0x00040100);
break;
case SAA7134_BOARD_VIDEOMATE_S350:
- dev->has_remote = SAA7134_REMOTE_GPIO;
- saa_andorl(SAA7134_GPIO_GPMODE0 >> 2, 0x00008000, 0x00008000);
- saa_andorl(SAA7134_GPIO_GPSTATUS0 >> 2, 0x00008000, 0x00008000);
+ 
+ saa_andorl(SAA7134_GPIO_GPMODE0 >> 2, 0x0000C000, 0x0000C000);
+ saa_andorl(SAA7134_GPIO_GPSTATUS0 >> 2, 0x0000C000, 0x0000C000);
break;
}
return 0;
diff -r 59e746a1c5d1 linux/drivers/media/video/saa7134/saa7134-input.c
--- a/linux/drivers/media/video/saa7134/saa7134-input.c Wed Dec 30 09:10:33 2009 -0200
+++ b/linux/drivers/media/video/saa7134/saa7134-input.c Fri Jan 08 01:04:53 2010 +0200
@@ -723,11 +723,7 @@
mask_keycode = 0x7f;
polling = 40; /* ms */
break;
- case SAA7134_BOARD_VIDEOMATE_S350:
- ir_codes = &ir_codes_videomate_s350_table;
- mask_keycode = 0x003f00;
- mask_keydown = 0x040000;
- break;
+ 
case SAA7134_BOARD_LEADTEK_WINFAST_DTV1000S:
ir_codes = &ir_codes_winfast_table;
mask_keycode = 0x5f00;Now enter
patch -p1 <remove-ir.patch
This should apply the patch and should not ask for any filenames. Make sure the patch is in the same directory and it should all work.
Now compile.
Make
Ctrl-C once the compile has started (about 15 seconds)
modify the following file v4l/.config and change config_dvb_firedtv=n (it used to say =m)
Now let the compile finish.
make
Remove the exiting drivers with
sudo make rminstall
Put the new drivers in place with
sudo make install
reboot and it should still detect it wrongly as T750. Final step is to create a file (any name will do ending in .conf) in /etc/modprobe.d/ with the following in it:
> options saa7134 card=169reboot and it should now be detected correctly and if it is the same as mine it should now work with Ubuntu and Mythbuntu even with BBC HD (if only my computer was more powerful I'd be able to watch it without breakup). Standard definition works fine.
 
Maybe somebody can tell me what to do when the kernel gets updated. The 'make' command always seems to go back to the original kernel, there must be a setting somewhere or a file to delete.
 
Please report if you get it working.

---

### Post by Tradeout on 2010-01-12
Good work, Graham.
I'm going to follow your guide now.

I had seen the thread about the IR core being down and causing problems and wondered if this was related.

Does this mean the supplied IR remote doesn't work?

---

### Post by harryzimm on 2010-04-08
I have been trying for a few hours now to get this card to work. The patch above fails to apply to a recent v4l-dvb pull. I also have the newer (d1) version of the card. I really don't want to have to use windows for my backend. Any help is much appreciated.

cheers

---

### Post by DominicF on 2010-05-11
Hi,

Has anyone tried the videomate S350 (rev. d1) with the latest Mythbuntu 10.04 from a fresh install? Did it work for you?  I'm trying my card again without much success.

I created a file compro_s350.conf in /etc/modprobe.d/ with the following:

options saa7134 card=169 

which helped to force the card to be recognised as the S350.  

I'll add my dmesg output in my next posting.

---

### Post by DominicF on 2010-05-11
Extract from output of dmesg (running Mythbuntu 10.04, fresh install + updates):

[    5.800053] saa7130/34: v4l2 driver version 0.2.15 loaded
[    5.800114] saa7134 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.800121] saa7133[0]: found at 0000:03:00.0, rev: 209, irq: 16, latency: 64, mmio: 0xcfcff800
[    5.800128] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate S350/S300 [card=169,insmod option]
[    5.800147] saa7133[0]: board init: gpio is 843f00
[    5.800316] input: saa7134 IR (Compro VideoMate S3 as /devices/pci0000:00/0000:00:1e.0/0000:03:00.0/input/input5
[    5.800429] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.810046] vga16fb: initializing
[    5.810051] vga16fb: mapped to 0xffff8800000a0000
[    5.810055] vga16fb: not registering due to another framebuffer present
[    5.990035] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    5.990054] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[    5.990070] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 03 01 08 ff 00 87 ff ff ff ff
[    5.990086] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990102] saa7133[0]: i2c eeprom 40: ff d6 00 c0 86 1c 02 01 02 ff ff ff ff ff ff ff
[    5.990118] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[    5.990134] saa7133[0]: i2c eeprom 60: 35 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990152] saa7133[0]: i2c eeprom 70: 00 00 00 01 4e c1 ff ff ff ff ff ff ff ff ff ff
[    5.990161] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990171] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990180] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990189] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990199] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990208] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990217] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990226] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.990238] i2c i2c-1: Invalid 7-bit address 0x7a
[    5.991180] saa7133[0]: registered device video0 [v4l2]
[    5.991213] saa7133[0]: registered device vbi0[    7.025438] DVB: registering new adapter (cx88[0])
[    7.025444] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[    7.171303] DVB: registering new adapter (saa7133[0])
[    7.171311] DVB: registering adapter 1 frontend 0 (Zarlink ZL10313 DVB-S)...
[    7.630122] saa7133[0]: dsp access error
[    7.630128] saa7133[0]: dsp access error

Note the dsp access error... not sure what this means.

I have two different DVB cards installed in the machine, the S350 seems to be registered adapter1:

ls /dev/dvb shows 
adapter0  adapter1

I use the following command to scan for channels:

scan -a1 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf

where -a1 refers to adapter1.



The result of this is WARNING:>>> tuning failed!!! messages being displayed.

---

### Post by tatt on 2010-07-26
did you get this too work??  HOW


bleeding now from my eye sockets!!

---

### Post by crookingfackedit on 2010-10-20
> **tatt said:**
> did you get this too work??  HOW


bleeding now from my eye sockets!!

Yes!  Have just spent a good few hours fiddling around, and have got DVB-S working through the Compro Videomate S-350.  I need to go over it all again and figure out exactly what worked - I have two(identical) cards, and I've got one working correctly but not the other.

May be able to have a stab at it over the next day or two.  If I can't, then it'll not be for another week, as I'm away all of next week.

But yes, it certainly works!  Currently using Ubuntu 10.10 on this box.

---

### Post by crookingfackedit on 2010-10-20
Few more pictures...  I'm *thrilled* at the prospect of getting rid of that dreadful Windows Media Center.  Hate, hate, hate...

Going to bed on a happy note.  It's 1.46am here and I've got to rebuild the HTPC yet, as I need it to record my scheduled stuff tomorrow. :(

---

### Post by dryliketoast on 2010-10-24
also v interested to know how you managed it - i've tried all manor of things; i keep getting errors when executing 'modprobe -v saa7134'... my S350 has never been successfully detected. 

dmesg shows lots of errors in relation to the IR modules when using out of the box kernal and when using latest build of V4L... trying now to recompile with custom .config settings (trying to disable the infrared parts to see if i have any joy)

---

### Post by thebignose on 2010-10-25
Hi all, I've been dipping in and out of this thread since about April for my attempts to get this card properly detected. 

I originally tested the card in Kubuntu and XP and was rather disappointed to find XP ran it without any problems and Kubuntu wouldn't even acknowledge it's existence. My next step was to try a Mythbuntu live setup and see if I could get anywhere but it wouldn't detect it either. After a couple of weeks trying to work out how to install the driver, I eventually gave up and diverted my attentions for a while.

Last week I finally decided I had wrecked my Kubuntu install beyond use with all the farting about I've been doing since and so decided to try something different. After several failed installations (3 completely distinct distros!) and with the PC beginning to resemble a brick, I finally decided to fall back on Mythbuntu 10.04 since I had a disk lying around. Lo and behold: worked first time **and** detected the card. As a T750 admittedly, but at last I found my situation beginning to resemble some of those described above.

Now after yet more farting around, I'm beginning to reach melting point again and was hoping to ask some of you nice folk to clarify how you've got as far as you have.

So far, I've managed to follow a lot of DominicF's steps (much appreciated - cheers) and now have managed to force the backend to detect the card as an S300/S350. Great stuff.

I then tried to apply Jan's patch, but got a series of errors listing "hunk" failures. Some succeeded, but the majority failed. I've saved the output locally in case it's of any relevance. I now don't know if any of the patch will have affected anything but I haven't issued the "make" command so I'm thinking the PC should still boot at least. Have I done the right thing by pasting the text from Jan's patch into a file in /v4l-dvb, naming it "s350.patch" and issuing the following command? ```
patch -p1 <s350.patch
```Finally, I've tried applying the remove-ir.patch as Graham was directed to do (thanks for posting that, Graham), but the output showed ```
patch: **** malformed patch at line 5: };
```Can anyone suggest what might be wrong with this patch? I'm taking it  the line beginning with "};" isn't right, but I've no idea how it should read, being as I am rather a novice.

Despite these failures, I'm going to perform a channel scan in the morning since I've at least got the card detected properly and I'll report back if somehow it works.

Crookingfackedit - I'm looking forward to hearing how you got it all going!

---

### Post by thebignose on 2010-10-26
Ok, sure enough the PC booted fine, but I've now realised I can't scan for channels. I've tried doing it through the channel editor in the MythTV Backend Setup utility but the cursor just skips the scan option altogether - I assume it's disabled for some reason. I did try a "scan" command in terminal but I don't have much clue about the syntax and think I may have missed a step since my directory structure isn't as others have described.

I also found forcing the card to be detected as the S350 was not persistent after reboot, again I'm thinking this will be due to me probably missing out a range of fundamental steps. So I did have to force that again before even trying a scan.

Is anything I've said indicating any glaring errors to anyone? Any assistance would be much appreciated.

---

### Post by Keppy on 2010-11-27
I'm a linux noob and I've been wanting to get my videomate s350 working in mythbuntu 10.10 but do not understand what steps I should be taking.
Can anyone help me?

I think I should have the d1 revision as the card is only a couple of months old.

---

### Post by crookingfackedit on 2010-11-27
Sorry lads, I've had a really dreadful lack of free time lately.  Had another stab this evening, with mixed results.  Wanted to try a different approach, as last time I could only get one of my cards working.  Bodging my way through this evening, I've got both working successfully... :)

This is in the UK, using Freesat, and the d1 revision of the card.

##Obvious...
1.  Install Ubuntu.  I'm using x64 10.4.1, as I like the idea of LTS.
2.  ```
sudo apt-get update
```3.  ```
sudo apt-get upgrade
```##Grab latest v4l source
4.  ```
sudo apt-get install mercurial
```5.  ```
hg clone http://linuxtv.org/hg/v4l-dvb
```##Bodge the file
6.  ```
cd ~/v4l-dvb/linux/drivers/media/video/saa7134
```7.  ```
nano saa7134-cards.c
```8.  CTRL-W - search for "SAA7134_BOARD_VIDEOMATE_T750,", complete with comma.

You're looking for this section...

```
        }, {
                .vendor       = PCI_VENDOR_ID_PHILIPS,
                .device       = PCI_DEVICE_ID_PHILIPS_SAA7133,
                .subvendor    = 0x185b,
                .subdevice    = 0xc900,
                .driver_data  = SAA7134_BOARD_VIDEOMATE_T750,
        }, {
```Change it to this...

```
        }, {
                .vendor       = PCI_VENDOR_ID_PHILIPS,
                .device       = PCI_DEVICE_ID_PHILIPS_SAA7133,
                .subvendor    = 0x185b,
                .subdevice    = 0xc900,
                .driver_data  = SAA7134_BOARD_VIDEOMATE_S350,
        }, {
```All this does is prevent the card from being detected as the T750.  I initially tried changing the subdevice to "0xc999" for the T750, but the S350 still wasn't automatically detected.  Now, both my cards are properly autodetected, saving having to faff about in modprobe.d.  Didn't need to set the gpio_tracking flag or anything.  :)

9.  Write out the changes(CTRL-O), then quit(CTRL-X).  Drop back to the base directory(/v4l-dvb) - a few "cd .." commands should do it.
10.  ```
make
```11.  The above will fail on "firedtv".  Edit ".config" , search for "firedtv" and change it from M(module) to N(not compiled).
12.  ```
make all
```13.  ```
sudo make install
```14.  Reboot and cross your fingers!

Card should now be sucessfully detected on boot.  Geeky details from my system...

lspci -vvnn:
```
03:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
    Subsystem: Compro Technology, Inc. Device [185b:c900]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (21000ns min, 8000ns max)
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at febff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

03:01.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
    Subsystem: Compro Technology, Inc. Device [185b:c900]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (21000ns min, 8000ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at febff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134
```dmesg:
```
[   24.765109] Linux video capture interface: v2.00
[   24.765113] WARNING: You're using an experimental version of the V4L stack. As the driver
[   24.765115]          is backported to an older kernel, it doesn't offer enough quality for
[   24.765117]          its usage in production.
[   24.765118]          Use it with care.
[   24.786740] ppdev: user-space parallel port driver
[   24.786892] saa7130/34: v4l2 driver version 0.2.16 loaded
[   24.786945] saa7134 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   24.786953] saa7133[0]: found at 0000:03:00.0, rev: 209, irq: 19, latency: 64, mmio: 0xfebff800
[   24.786961] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate S350/S300 [card=169,autodetected]
[   24.787011] saa7133[0]: board init: gpio is 84bf00
[   24.836378] IR NEC protocol handler initialized
[   24.845453] IR RC5(x) protocol handler initialized
[   24.855565] Console: switching to colour frame buffer device 80x30
[   24.858711] IR RC6 protocol handler initialized
[   24.869661] IR JVC protocol handler initialized
[   24.873620] IR Sony protocol handler initialized
[   24.880078] Registered IR keymap rc-videomate-s350
[   24.880212] input: saa7134 IR (Compro VideoMate S3 as /devices/pci0000:00/0000:00:1e.0/0000:03:00.0/rc/rc0/input6
[   24.880282] rc0: saa7134 IR (Compro VideoMate S3 as /devices/pci0000:00/0000:00:1e.0/0000:03:00.0/rc/rc0
[   24.880287] IRQ 19/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   25.070052] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   25.070063] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   25.070071] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 03 01 08 ff 00 87 ff ff ff ff
[   25.070079] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.070087] saa7133[0]: i2c eeprom 40: ff d6 00 c0 86 1c 02 01 02 ff ff ff ff ff ff ff
[   25.070095] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   25.070103] saa7133[0]: i2c eeprom 60: 35 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.070111] saa7133[0]: i2c eeprom 70: 00 00 00 01 4e 0a ff ff ff ff ff ff ff ff ff ff
[   25.070119] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.070127] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.070135] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.070143] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.070151] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.070159] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.070186] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.070194] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.072314] saa7133[0]: registered device video0 [v4l2]
[   25.072352] saa7133[0]: registered device vbi0
[   25.072395] saa7134 0000:03:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.072404] saa7133[1]: found at 0000:03:01.0, rev: 209, irq: 16, latency: 64, mmio: 0xfebff000
[   25.072412] saa7133[1]: subsystem: 185b:c900, board: Compro VideoMate S350/S300 [card=169,autodetected]
[   25.072447] saa7133[1]: board init: gpio is 84bf00
[   25.072469] Registered IR keymap rc-videomate-s350
[   25.072580] input: saa7134 IR (Compro VideoMate S3 as /devices/pci0000:00/0000:00:1e.0/0000:03:01.0/rc/rc1/input7
[   25.072628] rc1: saa7134 IR (Compro VideoMate S3 as /devices/pci0000:00/0000:00:1e.0/0000:03:01.0/rc/rc1
[   25.072633] IRQ 16/saa7133[1]: IRQF_DISABLED is not guaranteed on shared IRQs
[   25.155226] EXT4-fs (sdc3): mounted filesystem with ordered data mode
[   25.261659] saa7133[1]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   25.261674] saa7133[1]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   25.261687] saa7133[1]: i2c eeprom 20: 01 40 01 02 02 01 03 01 08 ff 00 87 ff ff ff ff
[   25.261699] saa7133[1]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.261711] saa7133[1]: i2c eeprom 40: ff d6 00 c0 86 1c 02 01 02 ff ff ff ff ff ff ff
[   25.261724] saa7133[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   25.261736] saa7133[1]: i2c eeprom 60: 35 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.261748] saa7133[1]: i2c eeprom 70: 00 00 00 01 4e 0c ff ff ff ff ff ff ff ff ff ff
[   25.261761] saa7133[1]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.261773] saa7133[1]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.261785] saa7133[1]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.261809] saa7133[1]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.261822] saa7133[1]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.261834] saa7133[1]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.261846] saa7133[1]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.261859] saa7133[1]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   25.262367] saa7133[1]: registered device video1 [v4l2]
[   25.262405] saa7133[1]: registered device vbi1
[   25.274269] saa7134 ALSA driver for DMA sound loaded
[   25.274286] IRQ 19/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   25.274315] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 19 registered as card -2
[   25.275173] IRQ 16/saa7133[1]: IRQF_DISABLED is not guaranteed on shared IRQs
[   25.275199] saa7133[1]/alsa: saa7133[1] at 0xfebff000 irq 16 registered as card -1
[   25.295992] WARNING: You're using an experimental version of the DVB stack. As the driver
[   25.295995]          is backported to an older kernel, it doesn't offer enough quality for
[   25.295997]          its usage in production.
[   25.295998]          Use it with care.
[   25.315732] dvb_init() allocating 1 frontend
[   25.460025] DVB: registering new adapter (saa7133[0])
[   25.460033] DVB: registering adapter 0 frontend 0 (Zarlink ZL10313 DVB-S)...
[   25.526610] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input8
[   25.720985] type=1505 audit(1290892051.742:6):  operation="profile_load" pid=986 name="/usr/share/gdm/guest-session/Xsession"
[   25.723488] type=1505 audit(1290892051.742:7):  operation="profile_replace" pid=987 name="/sbin/dhclient3"
[   25.724447] type=1505 audit(1290892051.742:8):  operation="profile_replace" pid=987 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.724989] type=1505 audit(1290892051.742:9):  operation="profile_replace" pid=987 name="/usr/lib/connman/scripts/dhclient-script"
[   25.729113] type=1505 audit(1290892051.742:10):  operation="profile_load" pid=988 name="/usr/bin/evince"
[   25.741440] type=1505 audit(1290892051.762:11):  operation="profile_load" pid=988 name="/usr/bin/evince-previewer"
[   25.792215] r8169: eth0: link up
[   25.792225] r8169: eth0: link up
[   25.900011] dvb_init() allocating 1 frontend
[   26.020013] DVB: registering new adapter (saa7133[1])
[   26.020020] DVB: registering adapter 1 frontend 0 (Zarlink ZL10313 DVB-S)...
```I was able to scan for channels using the following:-

```
sudo apt-get update
sudo apt-get install dvb-apps mplayer
scan -x0 -a0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scan -x0 -a1 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf

```Output from doing the channel scan:
```
EPG Background Audio.:11778:v:0:27500:0:648:4152
Portal Video 5:11778:v:0:27500:3177:3176:8183
[1c02]:11778:v:0:27500:0:0:7170
Sky Intro:11934:v:0:27500:516:644:4515
Sky Intro:11934:v:0:27500:516:644:4525
Sky Intro:11934:v:0:27500:516:644:5004
Chl Line-up:11934:v:0:27500:0:664:5007
Sky Intro Active:11934:v:0:27500:2306:2307:9321
BBC NEWS:11953:h:0:27500:5000:5001:6704
BBC PARL'MNT:11953:h:0:27500:5301:5311:6705
BBC ALBA:11953:h:0:27500:5500:5501:6736
BBC R1:11953:h:0:27500:0:5401:6751
BBC R2:11953:h:0:27500:0:5402:6752
BBC R3:11953:h:0:27500:0:5403:6753
BBC R4 FM:11953:h:0:27500:0:5404:6754
BBC R4 LW:11953:h:0:27500:0:5405:6755
BBC R Scot.:11953:h:0:27500:0:5407:6757
BBC R Wales:11953:h:0:27500:0:5408:6758
BBC R Ulster:11953:h:0:27500:0:5409:6759
BBC Asian:11953:h:0:27500:0:5410:6760
BBC WS:11953:h:0:27500:0:5411:6761
ETV3:11953:h:0:27500:0:5401:6762
BBC R Cymru:11953:h:0:27500:0:5444:6763
BBC R1X:11953:h:0:27500:0:5412:6766
BBC 6 Music:11953:h:0:27500:0:5413:6767
BBC Radio 7:11953:h:0:27500:0:5442:6768
BBC R n Gael:11953:h:0:27500:0:5443:6769
BBC  London:11953:h:0:27500:0:5441:6770
T7 STRM-0:11953:h:0:27500:5100:5101:6780
T7 STRM-1:11953:h:0:27500:5200:5201:6781
ETV1:11953:h:0:27500:5000:5001:6790
6780:11953:h:0:27500:0:0:9995
6781:11953:h:0:27500:0:0:9996
CNN:12051:v:0:27500:2320:2321:7140
5606:12051:v:0:27500:0:0:7141
S4C:12129:v:0:27500:2305:2306:7301
7308:12129:v:0:27500:2305:2306:7308
S1Test:12148:h:0:27500:513:641:5308
Vegas Video Poker:12148:h:0:27500:0:0:8049
ITV1 Central S:11973:v:0:27500:2336:2337:7450
ITV1 Central E:11973:v:0:27500:2339:2340:7451
QVC:12031:h:0:27500:2311:2312:7230
QVC Test:12031:h:0:27500:2311:2312:7231
QVC Mirror:12031:h:0:27500:2311:2312:7234
QVC Mosaic Test:12031:h:0:27500:2326:2327:7235
QVC MOSAIC:12031:h:0:27500:2326:2327:7236
bid tv:12031:h:0:27500:2313:2314:7250
QVC:12031:h:0:27500:0:0:7232
QVC IMM Test:12031:h:0:27500:0:0:7233
Sky Active Ads:12109:h:0:27500:519:647:5048
SBL:12109:h:0:27500:0:0:4227
Vegas Cluedo:12187:h:0:27500:0:3072:8080
Vegas Monty Python:12187:h:0:27500:0:2542:8399
Sky News:12207:v:0:27500:512:640:4704
Sky News:12207:v:0:27500:513:641:4706
Sky News:12207:v:0:27500:514:642:4707
Sky Bet Reg:12207:v:0:27500:0:0:8007
Sky Bingo:12207:v:0:27500:0:0:8032
Sky News Active iText Quad:12207:v:0:27500:514:642:8218
Vegas Wanted DOA:12285:v:0:27500:0:2554:8023
Vegas Hit It Poker:12285:v:0:27500:0:3592:8069
Portal Video 6:12304:h:0:27500:4162:4163:8088
1429:12304:h:0:27500:516:644:9345
12198:12402:v:0:27500:0:0:12198
12199:12402:v:0:27500:3348:3349:12199
ITVi Quad:12402:v:0:27500:3352:3353:12150
STREAM-0:12441:v:0:27500:5000:5001:6880
STREAM-1:12441:v:0:27500:5100:5101:6881
STREAM-2:12441:v:0:27500:5200:5201:6882
STREAM-3:12441:v:0:27500:5300:5301:6883
STREAM-4:12441:v:0:27500:5400:5401:6884
STREAM-5:12441:v:0:27500:5500:5501:6885
STREAM-6:12441:v:0:27500:5600:5601:6886
Channel 4:10714:h:0:22000:2315:2316:9211
Channel 4:10714:h:0:22000:2327:2328:9212
Channel 4:10714:h:0:22000:2332:2333:9213
Channel 4:10714:h:0:22000:2337:2338:9214
Channel 4:10714:h:0:22000:2342:2343:9215
Channel 4:10714:h:0:22000:2347:2348:9216
Film4:10714:h:0:22000:2353:2354:9220
Film4 +1:10714:h:0:22000:2359:2360:9225
More4 +1:10714:h:0:22000:2367:2368:9230
c4 l:10714:h:0:22000:2315:2316:9281
E4+1:10729:v:0:22000:2347:2348:8300
E4:10729:v:0:22000:2305:2306:8305
Channel 4 +1:10729:v:0:22000:2316:2317:8311
Channel 4 +1:10729:v:0:22000:2322:2323:8312
Channel 4 +1:10729:v:0:22000:2327:2328:8313
Channel 4 +1:10729:v:0:22000:2332:2333:8314
Channel 4 +1:10729:v:0:22000:2337:2338:8315
Channel 4 +1:10729:v:0:22000:2342:2343:8316
More4:10729:v:0:22000:2359:2360:8340
e4:10729:v:0:22000:2305:2306:9208
Sky Games:10743:h:0:22000:0:2630:8107
Game Slot 20:10743:h:0:22000:0:2630:8115
Game Slot 18:10743:h:0:22000:0:2630:8118
Game Slot 22:10743:h:0:22000:0:2630:8128
Game Slot 26:10743:h:0:22000:0:2630:8140
Game Slot 17:10743:h:0:22000:0:2630:8146
Movies Xmas Vote:10743:h:0:22000:0:2542:8152
Portal Video 2:10743:h:0:22000:3168:3167:8199
Sky Hub Video:10743:h:0:22000:3165:3164:8200
RTE Radio 1:10743:h:0:22000:0:2320:9611
RTE 2FM:10743:h:0:22000:0:2321:9612
RTE R na G:10743:h:0:22000:0:2322:9613
RTE Lyric fm:10743:h:0:22000:0:2323:9614
ITV1 London:10758:v:0:22000:3328:3329:10060
ITV2:10758:v:0:22000:3332:3333:10070
ITV4:10758:v:0:22000:3340:3341:10072
ITVi Stream 44:10758:v:0:22000:3336:3337:10079
ITV1 Granada:10758:v:0:22000:3348:3349:10080
ITV1 Anglia E:10758:v:0:22000:3352:3353:10090
ITV1 Central W:10758:v:0:22000:3356:3357:10100
ITV Preview 1:10758:v:0:22000:3336:3337:10110
ITV Preview 2:10758:v:0:22000:0:0:10111
CITV:10758:v:0:22000:0:0:10071
BBC 1 London:10773:h:0:22000:5000:5001:6301
BBC 2 England:10773:h:0:22000:5100:5101:6302
BBC TES 3:10773:h:0:22000:5200:5201:6315
BBC THREE:10773:h:0:22000:5200:5201:6319
FIVE:10773:h:0:22000:5400:5401:6335
BBC 1 West:10773:h:0:22000:5900:5901:6341
BBC 1 East (W):10773:h:0:22000:5700:5701:6351
BBC 1 CI:10773:h:0:22000:5800:5801:6361
BBC TES 2:10773:h:0:22000:0:0:6309
CBBC Channel:10773:h:0:22000:0:0:6317
BBC 1 W Mids:10788:v:0:22000:5000:5001:10301
BBC 1 Yrks&Lin:10788:v:0:22000:5200:5201:10303
BBC 1 E Mids:10788:v:0:22000:5401:5402:10305
BBC 1 East (E):10788:v:0:22000:5500:5501:10306
BBC 1 Wales:10788:v:0:22000:5600:5601:10311
BBC 2 Wales:10788:v:0:22000:5700:5701:10312
ETV5:10788:v:0:22000:5000:5001:10321
BBC R5L:10802:h:0:22000:0:6001:6401
ETV2:10802:h:0:22000:5000:5001:6407
BBC FOUR:10802:h:0:22000:5600:5601:6416
BBC 1 Scotland:10802:h:0:22000:5000:5001:6421
BBC 2 Scotland:10802:h:0:22000:5100:5101:6422
BBC 1 N West:10802:h:0:22000:5700:5701:6441
BBC 1 Yorks:10802:h:0:22000:5800:5801:6451
BBC 1 S East:10802:h:0:22000:5900:5901:6461
BBC R5SX:10802:h:0:22000:0:6101:6464
ETV3:10802:h:0:22000:0:0:6462
CBeebies:10802:h:0:22000:0:0:6418
BBC 1 South:10817:v:0:22000:5200:5201:10353
BBC 1 S West:10817:v:0:22000:5300:5301:10354
BBC 1 NE & C:10817:v:0:22000:5400:5401:10355
BBC 1 Oxford:10817:v:0:22000:5500:5501:10356
BBC 1 NI:10817:v:0:22000:5600:5601:10361
BBC 2 NI:10817:v:0:22000:5700:5701:10362
ETV6:10817:v:0:22000:5200:5201:10371
ITV1 HD:10832:h:0:22000:2362:2369:10000
ITV4+1:10832:h:0:22000:2364:2365:10015
ITV1 Wales:10832:h:0:22000:3336:3337:10020
ITV1 West:10832:h:0:22000:3340:3341:10030
ITV1 W Country:10832:h:0:22000:3344:3345:10040
ITVi tp49:10832:h:0:22000:0:0:10098
G49:10832:h:0:22000:3336:3337:10099
ITVi Stream 2:10832:h:0:22000:0:0:10005
BBC HD:10847:v:0:22000:5500:5502:6940
BBC One HD:10847:v:0:22000:5400:5402:6941
6945:10847:v:0:22000:5500:5502:6945
TV Picks 2009:10861:h:0:22000:0:0:8012
FAQ Development:10861:h:0:22000:3756:3757:8015
Vegas Golden Doubloons:10861:h:0:22000:0:3681:8026
Vegas Diamond Compass:10861:h:0:22000:0:3597:8097
ITV1 Border:10891:h:0:22000:3328:3329:1015
ITV1 Border:10891:h:0:22000:3328:3329:10120
ITV1 TT N:10891:h:0:22000:3339:3340:10130
ITV1 Meridian S:10891:h:0:22000:3336:3337:10140
ITV1 Meridian E:10891:h:0:22000:3332:3333:10141
ITV1 Anglia S:10891:h:0:22000:3344:3345:10150
ITV1 Yorks W:10891:h:0:22000:3348:3349:10160
ITV2+1:10891:h:0:22000:3352:3353:10165
G53:10891:h:0:22000:3328:3329:10169
10135:10891:h:0:22000:0:0:9999
10125:10891:h:0:22000:0:0:10125
Men & Motors:10891:h:0:22000:0:0:10135
10145:10891:h:0:22000:0:0:10145
10155:10891:h:0:22000:0:0:10155
ITV Channel Is:10906:v:0:22000:3328:3329:10200
STV:10906:v:0:22000:3332:3333:10210
STV:10906:v:0:22000:3336:3337:10220
STV:10906:v:0:22000:3340:3341:10221
UTV:10906:v:0:22000:3344:3345:10230
talkSPORT:10906:v:0:22000:0:3355:10238
ITV3:10906:v:0:22000:3348:3349:10260
ITV3+1:10906:v:0:22000:3352:3353:10261
G54:10906:v:0:22000:3348:3349:10269
10225:10906:v:0:22000:0:0:10225
10255:10906:v:0:22000:0:0:10255
10265:10906:v:0:22000:0:0:10265
ITV1 HD:10935:v:0:22000:513:641:3851
UCB TV:11222:h:0:27500:2336:2337:52001
horror ch+1:11222:h:0:27500:2330:2331:52002
UMMAH CHNL:11222:h:0:27500:2332:2333:52004
Clubland TV:11222:h:0:27500:2334:2335:52005
Jewelry Maker:11222:h:0:27500:2316:2317:52006
Fashion TV:11222:h:0:27500:2305:2306:52007
Get Lucky TV:11222:h:0:27500:2338:2339:52008
Lava:11222:h:0:27500:2340:2341:52010
Chat Box:11222:h:0:27500:2319:2320:52013
Sunrise:11222:h:0:27500:0:2313:52027
BFBS Radio:11222:h:0:27500:0:2318:52028
LBC 97.3:11222:h:0:27500:0:2314:52029
Heart:11222:h:0:27500:0:2312:52030
LBC News:11222:h:0:27500:0:2315:52031
Northern Birds:11222:h:0:27500:2323:2324:52050
Controversial tv:11222:h:0:27500:2321:2322:52056
BET +1:11222:h:0:27500:2327:2328:52060
Press TV:11222:h:0:27500:2325:2326:52070
Just4us:11222:h:0:27500:0:0:52015
The Other Side:11222:h:0:27500:0:0:52016
movies4men:11223:v:0:27500:2350:2352:53109
movies4men 2:11223:v:0:27500:2357:2358:53110
PTV Global:11223:v:0:27500:2319:2320:53116
jazeerachildren:11223:v:0:27500:2317:2318:53118
Absolute CR:11223:v:0:27500:0:2371:53120
Absolute:11223:v:0:27500:0:2369:53121
Absolute80s:11223:v:0:27500:0:2372:53122
Amrit Bani:11223:v:0:27500:0:2366:53123
InsightRadio:11223:v:0:27500:0:2370:53124
CC Radio:11223:v:0:27500:0:2368:53125
Desi Radio:11223:v:0:27500:0:2367:53126
Abs Rad 90s:11223:v:0:27500:0:2382:53127
RdioCaroline:11223:v:0:27500:0:2377:53128
Rainbow:11223:v:0:27500:0:2379:53129
Free & Prize PlayJam Games:11223:v:0:27500:2321:2322:53130
Liberty:11223:v:0:27500:0:2378:53131
Spectrum 1:11223:v:0:27500:0:2380:53132
TWR:11223:v:0:27500:0:2373:53133
FWR:11223:v:0:27500:0:2381:53134
WRN Europe:11223:v:0:27500:0:2374:53135
Yorkshire R:11223:v:0:27500:0:2383:53136
Gaydarradio:11223:v:0:27500:0:2384:53137
RTE R1 Extra:11223:v:0:27500:0:2387:53138
Family Radio:11223:v:0:27500:0:2386:53139
NME:11223:v:0:27500:0:2375:53140
RCR:11223:v:0:27500:0:2385:53141
Jazz FM:11223:v:0:27500:0:2376:53142
Venus TV:11223:v:0:27500:2359:2360:53144
Vintage TV:11223:v:0:27500:2389:2390:53145
Travel Ch +1:11261:h:0:27500:2342:2343:52100
CBS Reality+1:11261:h:0:27500:2311:2312:52102
Olive TV:11261:h:0:27500:2313:2314:52104
horror channel:11261:h:0:27500:2315:2316:52105
Gay Network :11261:h:0:27500:2322:2323:52106
Wonderful:11261:h:0:27500:2336:2337:52107
Thane Direct:11261:h:0:27500:2338:2339:52109
DM Digital:11261:h:0:27500:2324:2325:52110
Panjab Radio:11261:h:0:27500:0:2308:52132
Jackpot Games:11261:h:0:27500:2309:2310:52170
Travel Ch +1:11261:h:0:27500:2342:2343:52100
CBS Reality+1:11261:h:0:27500:2311:2312:52102
Olive TV:11261:h:0:27500:2313:2314:52104
horror channel:11261:h:0:27500:2315:2316:52105
Gay Network :11261:h:0:27500:2322:2323:52106
Wonderful:11261:h:0:27500:2336:2337:52107
Thane Direct:11261:h:0:27500:2338:2339:52109
DM Digital:11261:h:0:27500:2324:2325:52110
Panjab Radio:11261:h:0:27500:0:2308:52132
Jackpot Games:11261:h:0:27500:2309:2310:52170
ComedyCtralX:11307:v:0:27500:2305:2306:52231
propeller:11307:v:0:27500:2332:2333:52250
S4C2:11307:v:0:27500:2335:2336:52280
Premier:11307:v:0:27500:0:2307:52299
Disha:11307:v:0:27500:2319:2320:53305
Ideal World:11307:v:0:27500:2339:2340:53310
High Street TV:11307:v:0:27500:2331:2332:53315
Ideal Extra:11307:v:0:27500:2335:2336:53320
Create & Craft:11307:v:0:27500:2337:2338:53325
Club Paradiso:11307:v:0:27500:2321:2322:53330
Motors TV:11307:v:0:27500:3329:3330:53335
Jewellery Ch.:11307:v:0:27500:2333:2334:53350
Ideal & More:11307:v:0:27500:2317:2318:53360
CBS Drama:11343:v:0:27500:3080:3081:50903
Starz TV:11343:v:0:27500:2318:2319:55202
Lucky Star:11343:v:0:27500:2336:2337:55204
Babestation:11343:v:0:27500:2309:2310:55207
NDTV Imagine:11343:v:0:27500:2332:2333:55209
Babeworld.tv:11343:v:0:27500:3082:3083:55212
Takbeer TV:11343:v:0:27500:2334:2335:55213
My Channel:11343:v:0:27500:2326:2327:55214
WatchmeTV.TV:11343:v:0:27500:2328:2329:55221
Psychic TV:11343:v:0:27500:2316:2317:55226
Ahlulbayt TV:11343:v:0:27500:2324:2325:55228
House Of Fun:11343:v:0:27500:0:0:55201
BET:11344:h:0:27500:2320:2321:53230
Elite TV 2:11344:h:0:27500:2339:2340:53255
Food Network:11344:h:0:27500:2309:2310:53260
Food Netwrk+1:11344:h:0:27500:2316:2317:53270
Blue Kiss TV:11344:h:0:27500:2325:2326:53275
wedding tv:11344:h:0:27500:2333:2334:53280
Hidayat TV:11344:h:0:27500:2331:2332:53290
LivexxxBabes:11344:h:0:27500:3086:3087:53295
Essex Babes:11344:h:0:27500:2307:2308:53297
53230:11344:h:0:27500:0:0:1014
Sumo TV:11344:h:0:27500:0:0:53210
DMAX+2:11390:h:0:27500:2337:2338:52425
ARY News:11390:v:0:27500:2306:2307:53510
The Word:11390:v:0:27500:0:0:53567
CelebrityShop:11390:v:0:27500:2341:2342:53589
ChatGirl TV2:11390:v:0:27500:2343:2344:53590
40 n Naughty:11390:v:0:27500:2339:2340:53598
Pulse Rated:11390:v:0:27500:0:0:53564
price-drop tv:11426:v:0:27500:2334:2335:52510
OBE:11426:v:0:27500:2324:2325:52525
speedauctiontv:11426:v:0:27500:2318:2319:52546
Bloomberg:11426:v:0:27500:2308:2309:52550
Glory TV:11426:v:0:27500:2330:2331:52555
Screenshop2:11426:v:0:27500:0:0:52545
price-drop tv:11426:v:0:27500:2334:2335:52510
OBE:11426:v:0:27500:2324:2325:52525
speedauctiontv:11426:v:0:27500:2318:2319:52546
Bloomberg:11426:v:0:27500:2308:2309:52550
Glory TV:11426:v:0:27500:2330:2331:52555
Screenshop2:11426:v:0:27500:0:0:52545
CommunityChnl:11469:h:0:27500:518:646:5802
Remote Control Look Up App:11469:h:0:27500:0:4204:8020
Vegas Elvis:11507:h:0:27500:3568:3567:8035
Pin Reminder Service:11507:h:0:27500:0:0:8184
___4109:11507:h:0:27500:0:0:47000
___4110:11507:h:0:27500:0:0:48000
___99:11507:h:0:27500:0:0:48099
 (sub b +1000):11507:h:0:27500:0:0:49000
49500:11507:h:0:27500:0:0:49500
GayDateTV:11526:v:0:27500:2332:2333:50310
Channel M:11526:v:0:27500:2338:2339:50315
Dating Channel:11526:v:0:27500:2335:2336:50330
Islam Channel:11526:v:0:27500:2318:2319:50335
TMTN1:11526:v:0:27500:2320:2321:50360
TMTN2:11526:v:0:27500:2322:2323:50370
Shop on TV:11546:h:0:27500:2346:2347:50400
Gala TV:11546:h:0:27500:2348:2349:50410
AVAGO (Cable):11546:h:0:27500:2348:2349:50411
V Channel:11546:h:0:27500:2362:2363:50425
Monte Carlo TV:11546:h:0:27500:2332:2333:50445
AvaTest:11546:h:0:27500:2348:2349:50446
Zing:11546:h:0:27500:2315:2316:50470
Mirada:11546:h:0:27500:0:0:50481
Life:11546:h:0:27500:0:0:50435
cso:11546:h:0:27500:0:0:50440
Sky Preview:11565:v:0:27500:514:642:4505
DVD  Extras:11565:v:0:27500:517:645:5287
Movies Active:11565:v:0:27500:0:0:5288
SupremeMastr:11584:h:0:27500:2327:2328:50605
Sikh Channel:11584:h:0:27500:2325:2326:50610
Film24:11584:h:0:27500:2313:2314:50615
Channel AKA:11584:h:0:27500:2315:2316:50630
Entrepreneur:11584:h:0:27500:2317:2318:50635
Russia Today:11623:h:0:27500:2322:2323:50847
InTune:11623:h:0:27500:0:2339:50851
Kiss:11623:h:0:27500:0:2340:50856
Magic:11623:h:0:27500:0:2341:50860
PTV Prime:11623:h:0:27500:2318:2319:50865
Abu Dhabi TV:11623:h:0:27500:2320:2321:50866
PCNE Chinese:11623:h:0:27500:2329:2330:50878
Information TV:11623:h:0:27500:2334:2335:50880
WTF:11623:h:0:27500:2347:2348:50882
Flava:11642:v:0:27500:2323:2324:52300
Bliss:11642:v:0:27500:2327:2328:52305
Scuzz:11642:v:0:27500:2329:2330:52310
DanceNationTV:11642:v:0:27500:2331:2332:52315
True Movies 1:11642:v:0:27500:2313:2314:52320
True Movies 2:11642:v:0:27500:2317:2318:52325
Tiny Pop:11642:v:0:27500:2321:2322:52330
NME TV:11642:v:0:27500:2319:2320:52335
POP:11642:v:0:27500:2315:2316:52340
Tiny Pop +1:11642:v:0:27500:2335:2336:52345
Kix!:11642:v:0:27500:2337:2338:52351
The Vault:11642:v:0:27500:2325:2326:52355
PopGirl:11642:v:0:27500:2339:2340:52361
Chart Show TV:11642:v:0:27500:2306:2307:52365
PopGirl +1:11642:v:0:27500:2333:2334:52370
True Ent:11642:v:0:27500:2341:2342:52375
mta-muslim tv:11661:h:0:27500:2309:2310:51001
Word Network:11661:h:0:27500:2319:2320:51005
SuperCasino:11661:h:0:27500:2321:2322:51006
CCTV News:11661:h:0:27500:2328:2329:51011
Inspiration:11661:h:0:27500:2330:2331:51019
FRANCE 24:11661:h:0:27500:2345:2346:51032
TBN Europe:11661:h:0:27500:2307:2333:51033
GOD Channel:11661:h:0:27500:2334:2335:51035
Al Jazeera Eng:11680:v:0:27500:2322:2323:51107
NHK World TV:11680:v:0:27500:2314:2315:51108
Newstalk:11680:v:0:27500:0:2331:51114
TV SHOP:12523:v:0:27500:2323:2324:9531
CBS Reality:12523:v:0:27500:2325:2326:9532
Rocks & Co 1:12523:v:0:27500:2327:2328:9533
Record TV:12523:v:0:27500:2346:2347:9535
Sangat:12523:v:0:27500:2330:2331:9536
JML Home&DIY:12523:v:0:27500:2332:2333:9537
Recordbrazil:12523:v:0:27500:0:2336:9546
Amar Radio:12523:v:0:27500:0:2337:9547
Sukh Sagar:12523:v:0:27500:0:2338:9548
Choice FM:12523:v:0:27500:0:2320:9549
UCB UK:12523:v:0:27500:0:2305:9551
UCB Insp:12523:v:0:27500:0:2306:9552
UCB Bible:12523:v:0:27500:0:2307:9553
UCB Gospel:12523:v:0:27500:0:2308:9554
Solar Radio:12523:v:0:27500:0:2339:9557
XFM:12523:v:0:27500:0:2316:9559
Capital:12523:v:0:27500:0:2318:9560
Gold:12523:v:0:27500:0:2310:9561
Khushkhabri:12523:v:0:27500:0:2340:9563
Kismat:12523:v:0:27500:0:2341:9566
Chill:12523:v:0:27500:0:2319:9568
Classic FM:12523:v:0:27500:0:2348:9570
Planet Rock:12523:v:0:27500:0:2349:9575
GemCollector:12523:v:0:27500:2342:2343:55104
Brit Asia TV:12523:v:0:27500:2352:2353:55108
Sunrise TV:12523:v:0:27500:2344:2345:55109
Gems TV:12523:v:0:27500:2321:2322:55110
DBN:12523:v:0:27500:2334:2335:55111
Stop + Shop:12523:v:0:27500:2350:2351:55112
UCB Ireland:12523:v:0:27500:0:2309:55128
punjabi radio:12523:v:0:27500:0:2317:55132
TV SHOP:12524:v:0:27500:2323:2324:9531
CBS Reality:12524:v:0:27500:2325:2326:9532
Rocks & Co 1:12524:v:0:27500:2327:2328:9533
Record TV:12524:v:0:27500:2346:2347:9535
Sangat:12524:v:0:27500:2330:2331:9536
JML Home&DIY:12524:v:0:27500:2332:2333:9537
Recordbrazil:12524:v:0:27500:0:2336:9546
Amar Radio:12524:v:0:27500:0:2337:9547
Sukh Sagar:12524:v:0:27500:0:2338:9548
Choice FM:12524:v:0:27500:0:2320:9549
UCB UK:12524:v:0:27500:0:2305:9551
UCB Insp:12524:v:0:27500:0:2306:9552
UCB Bible:12524:v:0:27500:0:2307:9553
UCB Gospel:12524:v:0:27500:0:2308:9554
Solar Radio:12524:v:0:27500:0:2339:9557
XFM:12524:v:0:27500:0:2316:9559
Capital:12524:v:0:27500:0:2318:9560
Gold:12524:v:0:27500:0:2310:9561
Khushkhabri:12524:v:0:27500:0:2340:9563
Kismat:12524:v:0:27500:0:2341:9566
Chill:12524:v:0:27500:0:2319:9568
Classic FM:12524:v:0:27500:0:2348:9570
Planet Rock:12524:v:0:27500:0:2349:9575
GemCollector:12524:v:0:27500:2342:2343:55104
Brit Asia TV:12524:v:0:27500:2352:2353:55108
Sunrise TV:12524:v:0:27500:2344:2345:55109
Gems TV:12524:v:0:27500:2321:2322:55110
DBN:12524:v:0:27500:2334:2335:55111
Stop + Shop:12524:v:0:27500:2350:2351:55112
UCB Ireland:12524:v:0:27500:0:2309:55128
punjabi radio:12524:v:0:27500:0:2317:55132
wedding tv asia:12560:v:0:27500:2325:2326:54101
Travel Channel:12560:v:0:27500:2347:2348:54102
Rocks TV:12560:v:0:27500:2339:2340:54103
Euronews:12560:v:0:27500:2327:2328:54104
JML Cookshop:12560:v:0:27500:2308:2310:54106
CBS Action:12560:v:0:27500:2305:2306:54110
Best Direct:12560:v:0:27500:2321:2322:54112
QVC Beauty:12560:v:0:27500:2323:2324:54113
JML Choice:12560:v:0:27500:2345:2346:54120
Believe TV:12560:v:0:27500:2350:2351:54135
Horse & Country:12560:v:0:27500:2341:2342:54140
JML Direct:12560:v:0:27500:2337:2338:54150
Fitness TV:12560:v:0:27500:2314:2315:54165
O'seasproperty:12560:v:0:27500:0:0:54109
wedding tv asia:12560:v:0:27500:2325:2326:54101
Travel Channel:12560:v:0:27500:2347:2348:54102
Rocks TV:12560:v:0:27500:2339:2340:54103
Euronews:12560:v:0:27500:2327:2328:54104
JML Cookshop:12560:v:0:27500:2308:2310:54106
CBS Action:12560:v:0:27500:2305:2306:54110
Best Direct:12560:v:0:27500:2321:2322:54112
QVC Beauty:12560:v:0:27500:2323:2324:54113
JML Choice:12560:v:0:27500:2345:2346:54120
Believe TV:12560:v:0:27500:2350:2351:54135
Horse & Country:12560:v:0:27500:2341:2342:54140
JML Direct:12560:v:0:27500:2337:2338:54150
Fitness TV:12560:v:0:27500:2314:2315:54165
O'seasproperty:12560:v:0:27500:0:0:54109
Filth:12606:v:0:27500:2313:2314:55242
Dirty Talk:12606:v:0:27500:2308:2315:55246
The Active Ch:12606:v:0:27500:2327:2328:55247
MATV National:12643:v:0:27500:2339:2340:54300
Pitch TV:12643:v:0:27500:2343:2344:54315
Elite TV:12643:v:0:27500:2341:2342:54330
OceanFinance:12643:v:0:27500:5001:5002:54345
54350:12643:v:0:27500:5004:5005:54350
Pitch World :12643:v:0:27500:2345:2346:54360
54365:12643:v:0:27500:2309:2310:54365
```So both adapters are now working.  But... and it's a big but... I can't get the cards working in Myth-TV - possibly something to do with the "Zarlink" detection?  I've now had enough for tonight, and don't know when I'll be able to have another go.  Hopefully there is enough information above for some of you to make some progress? :)

Next time I try this, I think it'll be on Fedora.  I'm wondering whether it'll be easier to get working, and whether this is just problematic on Ubuntu?

---

### Post by Keppy on 2010-11-28
On attempting #10 I get ```
:~/v4l-dvb/linux/drivers/media/video/saa7134$ make
make: *** No targets.  Stop.
```
Can anyone offer any suggestions?

EDIT: Have just discovered I think I was in the wrong directory, went up to v4l-dvb/ and ran it and it appears to be doing things :)

---

### Post by crookingfackedit on 2010-11-28
Sorry, it was really late when I wrote that and my eyes were zonked from messing around for a few hours. :)  Let me know how it goes!

---

### Post by Keppy on 2010-11-28
> **crookingfackedit said:**
> Sorry, it was really late when I wrote that and my eyes were zonked from messing around for a few hours. :)  Let me know how it goes!

No worries, I'm very grateful for your help. It got upset about firetv but I cannot seem to find a '.config' file if you can offer any guidance?

---

### Post by crookingfackedit on 2010-11-28
Crap, I can't remember.  If it's not in v4l-dvb, try v4l-dvb/linux...

This is a ballache for me, as I have to keep popping the hard drive out of my USB enclosure and dangle it from the case of my HTPC, as the board won't boot from USB.  Hence why I don't get much of a chance to fiddle - trying to find free time is hard, free time + empty recording schedule is harder... and the motivation to gut the case is harder still! ;)

---

### Post by crookingfackedit on 2010-11-28
Try this:-

```
nano ~/v4l-dvb/v4l/.config
```Find this line:-

```
CONFIG_DVB_FIREDTV=m
```Change it to:-

```
CONFIG_DVB_FIREDTV=n
```

---

### Post by Keppy on 2010-11-28
Yep thats where it was thanks, I realise now I shouldn't have been using a file manager to find it since it doesn't show up.

It's busy chugging away at the moment, I'll report back how I get on (or come back for more help ;))

---

### Post by crookingfackedit on 2010-11-28
How's it going, Keppy?

---

### Post by Keppy on 2010-11-28
Followed your steps and mythTV has found it to be the s350 etc. currently trying to get it to scan for channels. The scanner in mythtv seems to error constantly about me not putting a frequency in (does it have a 'scan everything' mode?), using the scan command in the terminal I'm having the following errors:

```

3000:~$ scan -x0 -a0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

3000:~$ scan -x0 -a1 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter1/frontend0': 2 No such file or directory

3000:~$ scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

```

---

### Post by crookingfackedit on 2010-11-28
I had that.  If I rebooted, and tried the scan without starting MythTV, then I could successfully scan for channels.  Don't worry about the second scan command, it seems you only have the one card... :)

That's pretty much where I drew a blank, sadly.  I hate these cards, I wish I'd never parted with money for them.  I'll be sure to do more research in future, rather than seeing the driver referenced on the Compro site and assuming all was good.

---

### Post by Keppy on 2010-11-28
Yeah I ran the mythTV backend setup which stops mythTV and the scan is underway.

Under windows these cards seem to be fine, just trying linux to see if I can get any more performance as my HTPC is somewhat crap...

---

### Post by thebignose on 2010-11-28
Chuffing hell, cfe - this might be exactly the breakthrough I needed to get me going! Cheers!

[SIZE=1](Now I don't suppose anyone has any ideas how to prise control of the TV off the wife? Bloody X-Factor...)[/SIZE]

---

### Post by Keppy on 2010-11-28
Since my last post I've been trying to get mythTV to scan for channels, I gave up on the one in mythTV's settings as frankly it's almost useless, but I cannot find any still correct/still working methods of getting all available channels in mythTV. 

The scan I ran (from the terminal) found all the channels available with no problems, but I can't find the channels.conf it came up with to try and import it into mythTV. From what I've read however it's in the wrong format anyway.

If anyone can help it would be appreciated but I'm edging very close to giving up and going back to windows.

Big thanks to crookingfackedit for the help so far.


EDIT: I've tried the myth_scanner perl script (from the mythTV wiki?) but that doesn't seem to work either.

EDIT2: I've given up, going back to windows.

---

### Post by masterluke on 2011-01-01
crookingfackedit - thank you so much for your helpful post. I followed your instructions and have a fully working D1 revision S350. I have Mythtv scanning and as far as I can tell its working 100%. The remote even works :-)

I'm a bit of a newbie but I'll be happy to help if anyone else is having trouble.

FYI - although Mythtv worked fine I have since discovered TVheadend and XBMC which I found a better alternative.

EDIT - when i got stuck with mythtv scanning i used this guide for help 
[http://parker1.co.uk/mythtv_freesat.php](http://parker1.co.uk/mythtv_freesat.php)

Thanks again.

---

### Post by crookingfackedit on 2011-01-04
Glad it helped.  I'll be sure to have a look at tvheadend, it looks quite interesting!  Just need to find a conveniently quiet couple of days so I can have a fiddle...

Keppy - I'm sorry you didn't manage to sort it.  Even though I got mine scanning, I'll never touch anything manufactured by Compro again.

---

### Post by thebignose on 2011-01-06
Hi all,
Thanks for all the guidance above, particularly crookingfackedit.

Is it normal that MythTV seems to recognise this card as an "Analog V4L capture card" with a "Zarlink ZL10313 DVB-S" frontend? I take it the channel scan needs to be done against the frontend.

I've been struggling my way onward with it and feel I may have made some progress, although I didn't have time to test it after this morning's breakthrough.

---

### Post by thebignose on 2011-01-11
Success! I got it working! Recording plenty over the weekend and watching LiveTV through the MythTV frontend and XBMC - awesome stuff. In my excitement I then let the system perform a kernel update which got me back to square one - detecting the card as the T750 again. Oops!

I'm currently running back through everything now to see if I can pick up where I left off. Hopefully it'll be done in time for tonight's recordings!

 CFE - apologies if what I'm about to say is "teaching granny to suck eggs", as it were, but what I'm about to type could have saved me a lot of time if I had been able to find it somewhere earlier. I noticed you asked earlier on about "Zarlink detection" and I think that was another crucial point for getting it all running after following through the advice you had posted. 

When adding the capture card in the backend setup utility, you can add it as a V4L device (detected as S350) or a DVB device (detected as the Zarlink frontend thing). I think the V4L component is analog and is for capturing stuff through the S-Video and Composite inputs. To scan for channels you need to set the card type as "DVB...<whatever the rest of that item says>" and go into the DiSEqC menu there. I can't do a step-by-step right now (since I'm only halfway through repairing the damage of the kernel update) but that might be enough to get you going in the right direction. Setting the LNB option in there and then following through the rest of the wizard got me sorted.

If I remember anything else while I'm going through it myself I'll come back and post more.

---

### Post by crookingfackedit on 2011-01-11
Ace, I'm glad people have managed to make some progress. :)  Sadly, I've ditched Linux for a bit, and installed W7 on my main box.  I've used Linux full-time since 2002 or so, and fancy a break.  I'll keep this page bookmarked for future reference - chances are Windows will annoy me very much over just a few weeks, and I'll be coming back... ;)

Much of the motivation behind dumping Linux was so I could watch recordings from my HTPC on the laptop, so I'll be watching this very keenly.  It'd be nice to figure how to get everything working smoothly - it seems all the keys are in place, they're just not talking to each other properly.

I still hate, and blame, Compro.  Useless company.

---

### Post by masterluke on 2011-01-15
> **crookingfackedit said:**
> 
Much of the motivation behind dumping Linux was so I could watch recordings from my HTPC on the laptop, so I'll be watching this very keenly.

What I really love about tvheadend is that it saves recorded tv as properly named .MKV's from the EPG for example "The Godfather.MKV" which makes it really easy to view recordings on other devices.

I had reason to go back to Win7 recently but didnt last long :p

Thanks again for your help.

EDIT - Mine is detected as a "Zarlink ZL10313 DVB-S" too in mythtv and tvheadend. Agreed that the V4L device is probably the analog input and the Zarlink device is the one we are interested in. Maybe I'll test the other input at some point.

EDIT 2 - For folks with nvidia graphics cards dont forget to enable vdpau. Gives very nice hardware HDTV decoding and deinterlacing. Works nicely in mplayer, mythtv or XBMC.

---

### Post by crookingfackedit on 2011-01-15
What's the EPG like?  Can it capture over the air on Freesat, or does it take the information from other sources?

Very tempted to have a look.  I miss Linux already. ;)

---

### Post by masterluke on 2011-01-15
Tvheadend uses XMLTV to grab the listings. It seems to find all of the uk freesat channel listings. Unfortunately it only gets now and next over the air and not the full 7 days. Tvheadend has a very easy to use web-based epg. You can also see the epg from within XBMC which looks quite polished. I can use my laptop to schedule recordings from the web interface and then stream the recording to the laptop once its complete. If you are so inclined tvheadend also has built-in cardsharing support. I only really wanted a good setup to watch the freesat hd channels as i have sky+ already, but im trying to convince the wife that we can move over to this full-time.

One big flaw with the Videomate s350.. i cant seem to get the passthrough loop jack to work. Certainly my sky box will not lock on or show any signal strength daisy-chained via this port. Does this work ok on windows?

---

### Post by crookingfackedit on 2011-01-15
Bummer, I was hopeful it would collect the week ahead using over-the-air.  I'll have to look into any alternative configurations possible. :)

---

### Post by GerMulvey on 2011-04-09
Having followed and finally got this working I thought I'd post my method for anyone struggling. This is the info gathered from this thread and a few others. I hope it helps someone!

To get the card working:

1 ```
sudo apt-get install mercurial
```

2 ```
sudo hg clone http://linuxtv.org/hg/v4l-dvb
```

3 ```
cd ~/v4l-dvb/linux/drivers/media/video/saa7134
```

4 ```
sudo nano saa7134-cards.c
```

CTRL-W - search for SAA7134_BOARD_VIDEOMATE_T750,

change T750 >> S350

Write out the changes(CTRL-O), then quit(CTRL-X). Drop back to the base directory(/v4l-dvb) using cd ..

5 ```
make
```

ignore fail message and

6 ```
nano ~/v4l-dvb/v4l/.config
```

ctrl-W - search for CONFIG_DVB_FIREDTV=m  <<change m to n
Write out the changes(CTRL-O), then quit(CTRL-X).

7 ```
make all
```

8 ```
sudo make install
```

9 Next we need to reboot so save any work before continuing!
  ```
sudo reboot
```

TvHeadend to see TV:

Tvheadend is a lightweight TV tuning backend that supports DVB-C, DVB-T, DVB-S, DVB-S2, ATSC, IPTV and PAL analog TV. It has an integrated web frontend that can be used to configure the backend, view the EPG and start and view live TV or recordings.

1 ```
sudo apt-get install -y python-software-properties
```

2 ```
sudo add-apt-repository ppa:lars-opdenkamp/xbmc-pvr
```

3 ```
sudo apt-get update
```

4 ```
sudo apt-get -y install tvheadend xbmc
```

This will install Tvheadend and the PVR version of XBMC.

Configure TvHeadend:

Go to the TVheadend GUI by visiting [http://yourmachine:9981/](http://yourmachine:9981/)
Go to configuration -> tv adapters and select zarlink (only option unless you have other cards)

Enable "Autodetect muxes" and "Idle scanning" Then select "Add DVB Network by location"
Click "save"
Tvheadend will now start to detect multiplexes and services. Wait for "Muxes awaiting initial scan" to become 0.
Then click "Map DVB Services to channels". TVheadend will now try to open each channel and will add each channel that can be opened.
Once completed you should have a channel list. 

(This is as far as I have got so far. Currently I'm able to open channels in vlc, not a perfect solution but so far so good.)

[I]"Configuring XBMC

After installing, you can head to [http://yourserver:9981/](http://yourserver:9981/) to access the web interface and configure the backend.

After you configured the backend, start up XBMC and go to System -> Addons -> Installed -> PVR clients -> Tvheadend HTSP Client. Choose "configure" and fill in the requested information. Then choose "enable" to enable the PVR client.

Go back to System and choose TV -> General -> Activate.

Now you can start using Tvheadend from within XBMC by accessing the LiveTV in the main menu."[/I]

Can't seem to get there with this last bit.

---

### Post by rmil on 2011-04-30
After the kernel 2.6.36.? (Ubuntu 11-04) it become very difficult to compile v4l dvb drvers.

Anyway this worked for me without compiling the driver or module it self

#:>sudo bash (enter your password)
root:>echo "options saa7134 card=169" > /etc/modprobe.d/saa7134

now reboot 
check dmesg if your card is recognized well

---

### Post by thebignose on 2011-05-01
Hi rmil,
Having just properly made a mess of my Myth box, I'm about to give 11.04 a wee go now, so I'm glad to see it looks like things might get a bit simpler when it comes to getting the card going.

Can I just ask if there's a carriage return after [root:>echo "options saa7134 card=169"] or did you type [echo "options saa7134 card=169" > /etc/modprobe.d/saa7134] after the prompt?

---

### Post by rmil on 2011-05-01
Hi thebignose,

as root just type:

**echo "options saa7134 card=169" > /etc/modprobe.d/saa7134**


it will make file saa7134 at the location /etc/modprobe.d/ telling kernel to load driver for s350 instead of autodetected card. 

Not sure if mythtv will work but Me TV should work.

---

### Post by thebignose on 2011-05-02
Thanks for that, rmil - worked a treat!

This makes the card pretty easy to set up now. I'm thinking updates should now work without causing the card to be misdetected but time will tell...

---

### Post by pgthegr01 on 2011-05-30
I have two of these cards, and had upgraded to 11.04, the echo options command will only force the first card to be recognised as the S350. under 11.04 I couldnt compile the v4l drivers so I reverted back to 10.04.2 - with a recent upgrade I see it seems to have implicated the same changes. IE both cards are autodetected as T750's. I tried to recompile the V4l driver, which looked to do so cleanly but still autodetects.

At this point the echo options command is giving me one card as with 11.04.

[   13.465312] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate S350/S300 [card=169,insmod option]

[   13.793679] saa7133[1]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]

I do not understand how it seems to compile clean but then get autodetected. 

Anyone got any ideas?

Thanks in Advance.

Paul :)

---

### Post by GerMulvey on 2011-06-11
I'm currently using kubuntu 11.04 after 
```
echo "options saa7134 card=169" > /etc/modprobe.d/saa7134.conf
```
and installing me-tv I have a useable S350 which recieves and records fine.
No compiling of drivers was required at all.
works in opensuse 11.4 also

---

### Post by jpdamigaman on 2011-08-06
HI me tv recognises card but how do I scan channels?

I'm from UK

---

### Post by GerMulvey on 2011-09-10
> **jpdamigaman said:**
> HI me tv recognises card but how do I scan channels?

I'm from UK

When you first start me-tv it should start the wizard to do this. Now I am using mint 11 which does just that. Otherwise you should be able to start it from the view menu -- view/channels then select scan and choose the Astra 28.2 from the drop down list for freesat in the uk. You might then want to edit the lineup as this pulls in everything from the sats most of which is encrypted.. Once done save and view. Also after which you can save the channels.conf for future use, in case you re-install it makes setup a whole lot qicker!

---

### Post by GerMulvey on 2012-04-21
If anyone is still having issues as of opensuse 12.2 M3 using kaffeine 1.2.2 and kernel 3.3.0-2 the compro S350 now works 100% using kaffeines digital tv feature.
You still need to add 

echo "options saa7134 card=169" > /etc/modprobe.d/saa7134.conf

in the terminal and reboot

but in opensuse the tv card setup now lists the S350/300 as supported although it does detect the card as the S750 still hence the need for the above code to be added.
I haven't tested using ubuntu or kubuntu but just thought the info might help someone who's stuck!

---

### Post by ktbs on 2013-01-16
If anyone else is struggling to get two of these cards working together you need to change the line to:

options saa7134 card=169,169

That took me all morning to figure out!

---

