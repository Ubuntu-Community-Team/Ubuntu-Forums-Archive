---
title: "Question about TV tuner card"
date: 2006-01-25
forum: Multimedia &amp; Video
---

### Post by JesCed on 2006-01-25
Hello, all

I'm sure you've probably heard this before, but I've been using Ubuntu for a few weeks now, and love most things about it so far. I do, however, have to keep Windows on my PC because of two things: first of all, due to my work I have to use very specific proprietary software for analysis instruments I use in the lab, and this is regrettably Windows-only, and probably there is no way around this. The other reason, however, I hope there will be a solution for... using my TV tuner card.

I have an Encore TV tuner/video capture card, which works via a bt878 tuner. I downloaded TVtime, but upon running, all I can see is a blue screen with "no signal" across the top. Checking my devices list, I see that the bt878 card is detected, but doesn't seem to be configured.

However, something unusual. If I boot into Windows and watch TV for a while, when I boot back into Linux, if I star up TV time, I can see the signal for whichever channel I was last tuning, with no audio. Changing channels in TVtime does nothing... I always watch the same feed.:confused: 

I'd really like to get this card working, because if I do, I would only have to use Windows when importing data from the analysis equipment, and that would only be a few times per month.

Does anyone know how to get these cards working? [-o<

---

### Post by OneWingedAngel on 2006-01-25
You have to tune it first. First, make sure .tvtime is writable (chmod -R +rw ~/.tvtime), otherwise your changes won't get stored (for some reason, it wasn't on my computer). Now click the right button in the TVTime window, and choose Channel Management -> Scan Channels For Signal.

You can renumber them once it's finished (ITV on 3 etc.). Now quit, and the channels will be there.

For the sound problem, is the sound channel you're using muted? Try holding cursor right when TVTime is active.

---

### Post by JesCed on 2006-01-31
All right, I tried doing what you suggested, and something weird happened. Tvtime scanned through the whole channel table, without finding any signal. However, due to the fact that I had recently rebooted from a windows session in which I had the card working, even though I was actually watching a muted channel, tvtime found no signal. I suppose the failure to get the card working is related to it not being completely detected by Linux (It appears as a Generic/Unknown bt878 card). Is there a way for me to manually configure the card?

---

### Post by lapsey on 2006-01-31
I have had a similar problem, and I hope this helps. It *used* to do for me

from [http://tvtime.sourceforge.net/problems.html#undetected](http://tvtime.sourceforge.net/problems.html#undetected)

> 6. Unable to tune to channels using the bttv, saa7134 or cx88 drivers

The bttv, saa7134, and cx88 drivers each support a wide variety of cards which all use the same chip. In particular, these cards differ in what tuner they use, how many inputs they have, and how it is configured.

Often, these drivers cannot autodetect the card type, or detect the incorrect card. To debug this, you must watch your kernels logs by running the "dmesg" command, potentially loading and unloading the driver with different options until the driver is successfully loaded.

Some hints:

   1. If your card appears as UNKNOWN/GENERIC, then the tuner driver will not be loaded and the card will likely not work. You will need to load the driver with the correct card number.
   2. If your tuner reports that it is using type -1, it is not loaded and you will not be able to tune any stations.
   3. If you are an NTSC user, make sure the tuner you are using announces itself as an NTSC tuner. 

For example, if you are using the bttv driver, the common procedure for setting up a card is as follows:

   1. Run "modprobe bttv" with no options.
   2. Run "dmesg". Check to see if your card is autodetected, and if the tuner is correct. If everything looks fine, you're done.
   3. If the card appears as UNKNOWN/GENERIC, find the CARDLIST file in your kernel documentation and find your card in the list.
   4. Unload bttv and tuner using "rmmod bttv" and "rmmod tuner".
   5. Run "modprobe bttv card=X" where X is the number of your card.
   6. Run "dmesg" again. See if the card loaded properly and if the tuner is correct.
   7. If not, unload bttv and tuner again, and try specifying the tuner type as well using "modprobe bttv card=X tuner=Y".
   8. Curse Linux for being so complicated. 

there is a card list at [http://www.linux.com/howtos/BTTV/cards.shtml](http://www.linux.com/howtos/BTTV/cards.shtml)



For my own part, I managed to edit the .tvtime/stationlist.xml, and after running the above instuctions, it worked quite well.

Unfortunately I have since reinstalled Ubuntu and despite following the exact guide again I still get a blue screen in tvtime, and static in xawtv.

here are the appropriate parts of dmesg, post-driver reboot.

> [4305456.504000] bttv0: unloading
[4305476.330000] bttv: driver version 0.9.15 loaded
[4305476.330000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4305476.332000] bttv: Bt8xx card found (0).
[4305476.332000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 17
[4305476.332000] bttv0: Bt849 (rev 18) at 0000:00:0e.0, irq: 17, latency: 32, mmio: 0xd7000000
[4305476.333000] bttv0: using: Modular Technology MM100PCTV [card=60,insmod option]
[4305476.333000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[4305476.337000] bttv0: using tuner=0
[4305476.337000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4305476.339000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4305476.342000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4305476.344000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4305476.388000] tuner 0-0060: chip found @ 0xc0 (bt849 #0 [sw])
[4305476.388000] tuner 0-0060: type set to 0 (Temic PAL (4002 FH5))
[4305476.395000] bttv0: registered device video0
[4305476.398000] bttv0: registered device vbi0
[4305476.398000] bttv0: PLL can sleep, using XTAL (35468950).

halp

---

### Post by JesCed on 2006-02-12
Hello.

I tried using the solution mentioned above, but encountered a problem. I got as far as typing in the rmmod bttv command, but I got a reply saying that bttv couldn't be removed because it was in use by bt878.

What is going on? How can I get this to work?

---

### Post by xgj on 2006-02-12
cd  /etc/modprobe.d
sudo vi bbtv

       options bttv card=X tuner=Y

:wq

reboot

---

### Post by eight_car on 2006-02-12
[QUOTE=xgj]cd  /etc/modprobe.d
sudo vi bbtv

       options bttv card=X tuner=Y

:wq

reboot[/QUOTE]

I was trying to get my tuner card to work and was searching posts and found this thread. My card channels were off by one or more and the picture was out of focus.

This worked real well for me. Along with another post, found the correct number for the tuner option and it worked great.

localhost kernel [4294706.482000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option] (that part was correct card=34)

Had to use tuner=42 and Now my tvtuner card works! :)

---

### Post by anitsirK on 2006-03-02
[QUOTE=JesCed]Hello.

I tried using the solution mentioned above, but encountered a problem. I got as far as typing in the rmmod bttv command, but I got a reply saying that bttv couldn't be removed because it was in use by bt878.

What is going on? How can I get this to work?[/QUOTE]

try rmmod bt878, before continuing.  This worked for me. :)

xgj, thanks for that.  I'm about to reboot to see if this works!

Edit: YAY!  I don't have to reload the bttv module every boot!

---

