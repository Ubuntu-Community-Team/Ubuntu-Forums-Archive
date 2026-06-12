---
title: "Configure ALSA for Crystal 4237B"
date: 2005-11-16
forum: Multimedia &amp; Video
---

### Post by Manzabar on 2005-11-16
After much reading through these forums and across the internet, I finally got sound working on my laptop.  Since it was such a pain to do so and I saw posts by other users having problems getting it to work; I decided to post what worked for me.

I'm running Ubunut 5.10 on a Dell Latitude CPi D300XT which uses the Crystal 4237B chip for sound.  I know it's an ancient piece of junk, but it still works (even if it does take forever to boot up).
[LIST=1]
[*]Edit /boot/grub/menu.lst and add acpi=off to the end of the options for the kernel.
[*]Install libsdl.2debian-alsa via Synaptic.
[*]Removed /etc/modprobe.d/alsa-base.
[*]Created /etc/modprobe.d/alsa.
[*]Added snd-cs4236 to the bottom of /etc/modules.
[/LIST]

/boot/grub/menu.lst should look something like this:
```
title    Ubuntu, kernel 2.6.12-9-386
root    (hd0,0)
kernel    /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash acpi=off
initrd    /boot/initrd.img-2.6.12-9-386
savedefault
boot
```

/etc/modprobe.d/alsa looks like:
```
alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 port=0×530 cport=0×210 isapnp=0 dma1=1 dma2=0 irq=5
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1
 
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
 
alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss
 
options snd cards_limit=1
```

---

### Post by jonthysell on 2006-07-14
Finally!

Worked flawlessly on a CPi D266XT running Xubuntu 6.06!

---

### Post by thaswiftness on 2006-07-30
I've got a Dell Latitude cpi D266xt also, but can't seem to get it to play any mp3's. Is there something I'm missing?

---

### Post by Manzabar on 2006-07-31
What have you done in trying to get it to work?
Do any of the following commands give you information about your soundcard?
```
lspci -v
lspnp -v
lsmod | grep snd
cat /proc/asound/cards
alsamixer
dmesg | grep -i "isa\|multi\|sound\|audio"
pnpdump
```

---

### Post by jonthysell on 2006-08-19
There's a typo above (at least if you want this to work in Dapper):

2. Install **libsdl1.2debian-alsa** via Synaptic

---

### Post by Campitor on 2006-08-25
> **Manzabar said:**
> 
[LIST]
[*]Edit /boot/grub/menu.lst and add acpi=off to the end of the options for the kernel.
[*]Install libsdl.2debian-alsa via Synaptic.
[*]Removed /etc/modprobe.d/alsa-base.
[*]Created /etc/modprobe.d/alsa.
[*]Added snd-cs4236 to the bottom of /etc/modules.
[/LIST]
I am trying to set sound on a Dell Insprion 3000 which also has the crystal
4237B.  I followed the list above, but my sound is still not
working.  Do you mind posting your sound settings in BIOS
I think I have to change somethings.  My card just doesnt
get detected at boot time...I always get a: sound-card not detected or device busy.
hope you guys are still active.

BTW I-m running Dapper.

---

### Post by negativerad on 2008-02-14
I've got a Dell Cpi D266XT
Bios Version A12
Crystal 4237B
Ubuntu 7.10

**I did all the steps you suggested, and this is what I get...**

During boot it says Detecting Hardware... and i get this error.

CS4232 WSS PnP manual resources are invalid, using auto config
CS4232 WSS PnP configure failed for WSS (out of resource?)
PnP BIOS detection failed for CS4232
pnp: Device 00:10 disabled
cs4232-pnpbios: probe of 00:10 failed with error -16

---

### Post by tgalati4 on 2008-02-14
If you are running Gutsy, some ISA sound card support got messed up.  A work-around is to add a magic line to the bottom of your /etc/modules file.  First backup your existing file:

sudo cp /etc/modules /etc/modules.bak
sudo nano /etc/modules

Add this line to the bottom of /etc/modules:

#  Added Valentine's Day 2008 to get sound to work on my Dell
snd-cs4236 port=0×530 cport=0×210 isapnp=0 dma1=1 dma2=0 irq=5

---

### Post by negativerad on 2008-02-14
> **tgalati4 said:**
> If you are running Gutsy, some ISA sound card support got messed up.  A work-around is to add a magic line to the bottom of your /etc/modules file.  First backup your existing file:

sudo cp /etc/modules /etc/modules.bak
sudo nano /etc/modules

Add this line to the bottom of /etc/modules:

#  Added Valentine's Day 2008 to get sound to work on my Dell
snd-cs4236 port=0×530 cport=0×210 isapnp=0 dma1=1 dma2=0 irq=5

Thanks for the quick reply, but it didn't seem to work. I still get the same error on boot. I dont understand why its saying cs4232 anyways. Where is trying to load that from? It's almost like its completely ignoring the /etc/modprobe.d/alsa file

Thanks again for trying, any other suggestions would be much appreciated!

---

### Post by negativerad on 2008-02-14
I figured they may help. If you need anything else let me know!

**dmesg | grep PnP**
[  931.862288] pnp: PnP ACPI: disabled
[  931.862319] PnPBIOS: Scanning system for PnP BIOS support...
[  931.862568] PnPBIOS: Found PnP BIOS installation structure at 0xc00fe2d0
[  931.862596] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xe2f4, dseg 0x40
[  931.874715] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[  936.634811] isapnp: Scanning for PnP cards...
[  987.760047] CS4232 WSS PnP manual resources are invalid, using auto config
[  987.760153] CS4232 WSS PnP configure failed for WSS (out of resources?)
[  987.760227] PnP BIOS detection failed for CS4232

**lspci -v**
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
	Flags: bus master, medium devsel, latency 32
	Memory at d0000000 (32-bit, prefetchable) [size=256M]

00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01) (prog-if 00 [VGA])
	Subsystem: Dell MagicGraph 128XD
	Flags: medium devsel, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=16M]
	Memory at fde00000 (32-bit, non-prefetchable) [size=2M]
	Memory at fdd00000 (32-bit, non-prefetchable) [size=1M]

00:03.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Subsystem: Dell Unknown device 0074
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 30000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001

00:03.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Subsystem: Dell Unknown device 0074
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 30001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 28000000-2bfff000 (prefetchable)
	Memory window 1: 2c000000-2ffff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 0860 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at ece0 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
	Flags: medium devsel, IRQ 9

05:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
	Subsystem: Atheros Communications, Inc. DWL-G650B2 Wireless CardBus Adapter
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 2c000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

**lsmod | grep snd**
snd_cs4236             19212  0 
snd_cs4236_lib         17280  1 snd_cs4236
snd_cs4232             17684  0 
snd_opl3_lib           11520  2 snd_cs4236,snd_cs4232
snd_hwdep              10244  1 snd_opl3_lib
snd_cs4231_lib         26112  3 snd_cs4236,snd_cs4236_lib,snd_cs4232
snd_pcm                80388  2 snd_cs4236_lib,snd_cs4231_lib
snd_timer              24324  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd_page_alloc         11400  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart         9600  2 snd_cs4236,snd_cs4232
snd_rawmidi            25728  1 snd_mpu401_uart
snd_seq_device          9228  2 snd_opl3_lib,snd_rawmidi
snd                    54660  11 snd_cs4236,snd_cs4236_lib,snd_cs4232,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               8800  1 snd

**cat /proc/asound/cards**
--- no soundcards ---

**dmesg | grep -i "isa\|multi\|sound\|audio"**
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[  929.374661] SELinux:  Disabled at boot.
[  931.862181] ACPI: Interpreter disabled.
[  931.862288] pnp: PnP ACPI: disabled
[  936.611213] audit: initializing netlink socket (disabled)
[  936.634811] isapnp: Scanning for PnP cards...
[  936.989108] isapnp: No Plug & Play device found
[  937.269411] EISA: Probing bus 0 at eisa.0
[  943.468356] ata1.00: 19640880 sectors, multi 8: LBA 
[  987.771837] pnp: Device 00:0f disabled.

Couldnt execute, lspnp -v or pnpdump.

---

### Post by tgalati4 on 2008-02-15
If you followed the steps posted above your original post, that was dated Aug 2006 and applied to Dapper Drake.  You are running Gutsy Gibbon (7.10).  If you deleted /etc/modprobe.d/alsa-base, that contains several options that are needed (work-arounds) to get sound to work in Gutsy.  So, you are better served by putting the original file back.  You can put the snd-cs4236 options in that file, then you only need to put snd-cs4236 in /etc/modules file.  Either way, sound generally works in Dell hardware of this vintage, it just requires a little tweaking.

On my Dell GX1 (PIII, 500 MHz) with Gutsy, the kernel tries to load snd-4231 and fails so there is no sound.  But once the magic line is loaded, it works.

Try loading it from the terminal and post any errors.  Don't forget to turn on/unmute all the channels in Volume Mixer--they are usually turned off by default. (Look in Edit-->Preferences, then click on all channels).

sudo modprobe snd-cs4236 port=0×530 cport=0×210 isapnp=0 dma1=1 dma2=0 irq=5

Finally, make sure that sound is enabled in BIOS. (F2 on boot typically)

Good luck.

---

### Post by negativerad on 2008-02-15
Alright thanks I will give that a try, although I was stupid and deleted the file without backing it up, is there an easy way to retrieve it from the CD or somewhere safe online?

---

### Post by tgalati4 on 2008-02-15
Gutsy /etc/modprobe.d/alsa-base (with my modification at the end)

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# added for Dell GX1 sound since autodetect doesn't work correctly
options snd-cs4236 isapnp=0 port=0x530 cport=0xf00 irq=5 dma1=1 dma2=0

---

### Post by negativerad on 2008-02-16
Well I tried it and still nothing, same errors.

I still don't understand why its trying to load the CS4232 PnP stuff during hardware detection, shouldnt it trying to load the new stuff? I dont get it...

It's weird cause when i was on 6.04 my sound worked right out of the box.

:confused:

---

### Post by Talkless on 2008-02-16
> **jonthysell said:**
> Finally!

Worked flawlessly on a CPi D266XT running Xubuntu 6.06!

Sadly, I can't get it working on 7.10 (Fluxbuntu for instance).

---

### Post by tgalati4 on 2008-02-17
The newer kernel in Gutsy dropped support for ISA devices.  The CS-series sound chips are on the ISA bus.  It's not that they won't work, you just need to load special switches to get them to work.  The hardware detection is broken so the wrong driver gets loaded or the default switches don't work.

Also, check for an interrupt conflict.  Post the output of /proc/interrupts.

---

### Post by weirdfate on 2008-04-07
new here and am having the same problem

i did what was said in the first post and in the post dated February 15th, 2008 11:07 AM 
tgalati4 

and i still have no sound at all(well sysbeep but thats it)
i have searched all around and it looks like there is no real fix or patch for this issue

i switched this laptop from windows2000 to xubuntu 7 in hopes of getting to know linux but if the sound wont work im gona have to go back to windows 

any other help would be great

also is ther a way to redetect hardware,like in windows
my soundcarde was displayed as not detected but i know its there cause it worked with windows....:-k:popcorn::cry:[-o<

i hope to get this working soon so i can see what linux has to offer
thankyou

---

### Post by james_vanb on 2008-04-07
You may have already tried this.  Worked on an old Dell Latitude CP M233st using the Crystal Audio cs4237b.

When you're ready, open a terminal and enter the following command:

cat /sys/devices/pnp0/00:0f/resources

You should get something like this:

state = active
io 0x210-0x217

The 0x210 is the cport number. If your's is different, write it down, it's significant to the last command you're going to enter.

Enter the following command:

cat /sys/devices/pnp0/00:10/resources

You should get something like this:

state = disabled
io 0x530-0x537
io 0x388-0x38b
io 0x220-0x22f
irq 5
dma 1
dma 0

The 0x530 is the port. If your's is different, write it down. You'll see why when we get to the final command. Also note that the status is "Disabled". This has to be activated for the sound card to work. to activate, you have to have Super User privileges (Whatever that means).

To do that type the following command:

sudo -s

You'll be prompted to enter your password.

Now, to activate pnp0/00:10, use the following command:

echo activate > /sys/devices/pnp0/00:10/resources

This should activate the device. to check, type the following again:

cat /sys/devices/pnp0/00:10/resources

The status should now =Active.

Now that it's active, you need to load the driver. Type the following:

sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

Note the port and cport numbers I mentioned above, If yours were different, modify the command appropriately (As well as the irq, dma1 and dma2). If everything is the same as mine was - great. 

When you hit enter, you should hear your speakers "pop". You now have sound. Now enter the following:

alsamixer

when it opens, make sure nothing is muted (Keep the Mic muted as you'll just get feedback). Put an audio cd in and mess with the levels until it sounds right.

As a final note, I installed mplayer and set that as default. Totem just didn't work for me.

The following is a link to a great guide that helped me set things so I could listen to internet radio and view video, etc. You have to install flash plugin and a bunch of codecs:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

If you shut down and need to get sound again, you only have to enter the following 3 commands:

sudo -s
echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0


To activate at start up:

sudo mousepad /etc/rc.local

Add the following after the last commented out line and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

---

### Post by weirdfate on 2008-04-07
ok ill give it a shot but its not even showing the audio card is attached to the system when i run the script provided on this forum to detect devices?>???
i hope i didnt blow it out installing linus on this olde laptop
that would suck

---

### Post by weirdfate on 2008-04-08
> **james_vanb said:**
> You may have already tried this.  Worked on an old Dell Latitude CP M233st using the Crystal Audio cs4237b.

When you're ready, open a terminal and enter the following command:

cat /sys/devices/pnp0/00:0f/resources

You should get something like this:

state = active
io 0x210-0x217

The 0x210 is the cport number. If your's is different, write it down, it's significant to the last command you're going to enter.

Enter the following command:

cat /sys/devices/pnp0/00:10/resources

You should get something like this:

state = disabled
io 0x530-0x537
io 0x388-0x38b
io 0x220-0x22f
irq 5
dma 1
dma 0

The 0x530 is the port. If your's is different, write it down. You'll see why when we get to the final command. Also note that the status is "Disabled". This has to be activated for the sound card to work. to activate, you have to have Super User privileges (Whatever that means).

To do that type the following command:

sudo -s

You'll be prompted to enter your password.

Now, to activate pnp0/00:10, use the following command:

echo activate > /sys/devices/pnp0/00:10/resources

This should activate the device. to check, type the following again:

cat /sys/devices/pnp0/00:10/resources

The status should now =Active.

Now that it's active, you need to load the driver. Type the following:

sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

Note the port and cport numbers I mentioned above, If yours were different, modify the command appropriately (As well as the irq, dma1 and dma2). If everything is the same as mine was - great. 

When you hit enter, you should hear your speakers "pop". You now have sound. Now enter the following:

alsamixer

when it opens, make sure nothing is muted (Keep the Mic muted as you'll just get feedback). Put an audio cd in and mess with the levels until it sounds right.

As a final note, I installed mplayer and set that as default. Totem just didn't work for me.

The following is a link to a great guide that helped me set things so I could listen to internet radio and view video, etc. You have to install flash plugin and a bunch of codecs:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

If you shut down and need to get sound again, you only have to enter the following 3 commands:

sudo -s
echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0


To activate at start up:

sudo mousepad /etc/rc.local

Add the following after the last commented out line and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

you are the man!!!!!  that worked great......only one problem,i cant create the file for this  ```
To activate at start up:

sudo mousepad /etc/rc.local

Add the following after the last commented out line and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0
```
i type it all in and save and it gives me error can not create file to write

ive had tis before and cant remember the command to create it and save it

---

### Post by james_vanb on 2008-04-08
Glad it worked for you.  If you're using Xubuntu 7.10, you should be able to modify rc.local through mousepad.  Please note however, that I used sudo in the second command.  Sudo is not necessary.  Try again without the sudo command as follows:

In terminal:

sudo mousepad /etc/rc.local

Add the following after the last commented out line (Put cursor at end of last commented line and hit enter) and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

To minimize typos, I copy and paste the commands.

Hope this works.

---

### Post by weirdfate on 2008-04-08
> **james_vanb said:**
> Glad it worked for you.  If you're using Xubuntu 7.10, you should be able to modify rc.local through mousepad.  Please note however, that I used sudo in the second command.  Sudo is not necessary.  Try again without the sudo command as follows:

In terminal:

sudo mousepad /etc/rc.local

Add the following after the last commented out line (Put cursor at end of last commented line and hit enter) and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

To minimize typos, I copy and paste the commands.

Hope this works.
ok but when i try to edit any file in the system it gives me an error can not open file to write

checking permisions i cant change them to allow me to edit the files 
am i missing a setting or command??
I even tried sudo nano and when the file opens it says its a new file but i know its there

:confused:

---

### Post by james_vanb on 2008-04-08
Never encountered the problem you're now experiencing.  rc.local is a dummy script.  You shouldn't have to create it.  The first command should open the file in mousepad for editing.  Afraid I can't help you with this one.  Hopefully someone else will see this and give you some guidance.

---

### Post by james_vanb on 2008-04-08
> **tgalati4 said:**
> If you are running Gutsy, some ISA sound card support got messed up.  A work-around is to add a magic line to the bottom of your /etc/modules file.  First backup your existing file:

sudo cp /etc/modules /etc/modules.bak
sudo nano /etc/modules

Add this line to the bottom of /etc/modules:

#  Added Valentine's Day 2008 to get sound to work on my Dell
snd-cs4236 port=0×530 cport=0×210 isapnp=0 dma1=1 dma2=0 irq=5

Did you try this from tgalati4?

---

### Post by weirdfate on 2008-04-08
> **james_vanb said:**
> Did you try this from tgalati4?

please elaberate on this  im a noob....

also i noticed that my permissions are set like this

```
Owner:  root(root)
Access:  Read& write

Group: root
Access: Read only

Others: Read only
```

why is this and how do i get access to the files
and i cant log in as root

using xubuntu 7

---

### Post by james_vanb on 2008-04-08
Try going into Super User:

sudo -s
sudo mousepad /etc/rc.local

Add the following after the last commented out line and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

---

### Post by weirdfate on 2008-04-08
I think i tried that also but i will try it again...

this ticks me off cause its a fresh install and i dont know why i was able to do it once when i installed it before but now i cant do it


I think i should break out the windows format disk and wipe the hard disk then do a compleat reinstall of xubuntx but i choose to use full hard disk and i would ASSuME it clears the HD all the way so no settings that may have been changed woud have been gone.

:confused::lolflag::confused:

---

### Post by james_vanb on 2008-04-09
> **weirdfate said:**
> please elaberate on this  im a noob....

also i noticed that my permissions are set like this

```
Owner:  root(root)
Access:  Read& write

Group: root
Access: Read only

Others: Read only
```

why is this and how do i get access to the files
and i cant log in as root

using xubuntu 7

FYI - My permissions for mousepad are set the same.

---

### Post by weirdfate on 2008-04-10
thankyou for your help
combined with your info and [http://ubuntuforums.org/showpost.php?p=4687093&postcount=8](http://ubuntuforums.org/showpost.php?p=4687093&postcount=8) I got it working

again thankyou for your help  there is hope for me and ubuntu after all :)

---

### Post by gliberatore on 2008-04-30
OK ... I have a Dell Latitude Cpi that I just installed Hardy (8.04LTS) on to and have no sound. I have been following the steps for Gutsy but, at a terminal prompt/  However, when I enter:
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0
I hear a click from the speakers and then the terminal locks up and does not return to the prompt.  I've added this line (sans "sudo") to /etc/modprobe and the system locks up during boot when reading this file at this line.  Any ideas?

---

### Post by james_vanb on 2008-04-30
Just updated to Hardy myself.  I'm not getting terminal lock up although the Xfce terminal is FUBAR on my Dell (There is currently a Bug Report on the issue).  So, I'm using Xterm as a workaround.  If you are having trouble with terminal, navigate to File > usr > bin - scroll down to Xterm and open.  So far I've found that once pnp 00:10 is activated, it stays activated in Hardy.  To confirm that it is active issue the following command:

cat /sys/devices/pnp0/00:10/resources

If it's not active, issue the following command:

echo activate > /sys/devices/pnp0/00:10/resources

If it's active, edit rc.local by adding the following after the last commented line and before "exit=0":

modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

reboot

You should hear the "pop" when it loads.

I've found that when I open sound through Applications, it shows the sound driver but all is muted.  When I unmute and close, everything returns to muted when I open again.  Alsamixer gives me an error and will not open to let me unmute.

It seems there is a problem with Alsa and Pulseaudio. Speakers are on, but Alsa can't seem to find them. Have read that there is a Bug Report somewhere, but I have not found it.  Also have read that loading the linux-386 kernell is a fix.  I was just about to try same to see if it works

That's as far as I have gotten.

---

### Post by james_vanb on 2008-04-30
If above worked for you, execute following command:

asoundconf set-default-card CS4237B

alsamixer will now come up and you will have sound.  Just got an "Update information" notification when I rebooted advising to do same.

---

### Post by OZFive on 2008-06-06
> **james_vanb said:**
> You may have already tried this.  Worked on an old Dell Latitude CP M233st using the Crystal Audio cs4237b.

When you're ready, open a terminal and enter the following command:

cat /sys/devices/pnp0/00:0f/resources

You should get something like this:

state = active
io 0x210-0x217

The 0x210 is the cport number. If your's is different, write it down, it's significant to the last command you're going to enter.

Enter the following command:

cat /sys/devices/pnp0/00:10/resources

You should get something like this:

state = disabled
io 0x530-0x537
io 0x388-0x38b
io 0x220-0x22f
irq 5
dma 1
dma 0

The 0x530 is the port. If your's is different, write it down. You'll see why when we get to the final command. Also note that the status is "Disabled". This has to be activated for the sound card to work. to activate, you have to have Super User privileges (Whatever that means).

To do that type the following command:

sudo -s

You'll be prompted to enter your password.

Now, to activate pnp0/00:10, use the following command:

echo activate > /sys/devices/pnp0/00:10/resources

This should activate the device. to check, type the following again:

cat /sys/devices/pnp0/00:10/resources

The status should now =Active.

Now that it's active, you need to load the driver. Type the following:

sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

Note the port and cport numbers I mentioned above, If yours were different, modify the command appropriately (As well as the irq, dma1 and dma2). If everything is the same as mine was - great. 

When you hit enter, you should hear your speakers "pop". You now have sound. Now enter the following:

alsamixer

when it opens, make sure nothing is muted (Keep the Mic muted as you'll just get feedback). Put an audio cd in and mess with the levels until it sounds right.

As a final note, I installed mplayer and set that as default. Totem just didn't work for me.

The following is a link to a great guide that helped me set things so I could listen to internet radio and view video, etc. You have to install flash plugin and a bunch of codecs:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

If you shut down and need to get sound again, you only have to enter the following 3 commands:

sudo -s
echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0


To activate at start up:

sudo mousepad /etc/rc.local

Add the following after the last commented out line and before "exit=0":

echo activate > /sys/devices/pnp0/00:10/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0

I did this here,

I did the..
cat /sys/devices/pnp0/00:0f/resources

and got this one...
state = disabled
io 0x530-0x537
io 0x388-0x38b
io 0x220-0x22f
irq 5
dma 0
dma disabled

I then went on to this...
cat /sys/devices/pnp0/00:10/resources

and got...
No such file or directory

What am I doing wrong?

---

### Post by james_vanb on 2008-06-06
Try activating pnp 00:0f as follows:

```
sudo -s
echo activate > /sys/devices/pnp0/00:0f/resources
sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0
```

I remember reading a long time ago that some older IBM Thinkpads required pnp 00:0f to be activated and not 00:10.  If it doesn't work, post output of dmesg.

---

### Post by OZFive on 2008-06-12
Okay so I tried that too and got it avtivated.  YAY!  But i am still having issues, I cannot launch Alsamixer and if I try to launch Alsaconf, it asks me for my root password which I enter but it will not accept it and ask me if I want to try again.  Oddness.  I will get a screenshot of it soon whenI get a screenshot progrma installed and or a termainal that I can copy paste into.  Fluxbox is fast but it is stripped down in a few items I am used to.

---

### Post by james_vanb on 2008-06-12
If you are using Hardy, type the following:

```
asoundconf set-default-card CS4237B
```

Alsamixer should come up.

---

### Post by OZFive on 2008-06-13
"Please note that you are attempting to run asoundconf as a privlidged superuser, which may have unintended consequences"

Soooo depressing.  Please keep on helping if you can I would really like to kick this piece of .... into service.

---

### Post by james_vanb on 2008-06-13
EDIT:  Since it won't take your root password, try going Super User fist:

```
sudo su
```

Then try to set default as above.

Make sure that 00:0f is still activated.  If it isn't you have to edit rc.local as stated previously in this post for the driver to load when you boot (replace 00:10 with 00:0f for your particular situation).

Otherwise,when you run:

```
sudo asoundconf list
```

You should get that same warning followed by a list of available sound cards.  If it lists the sound card, try setting default again using the sound card written exactly as listed in the output (The command is case sensitive - try both with and without sudo if necessary).

A quick search for this warning didn't bring up issues in Hardy, but definitely in Gutsy.

If you're using Gutsy, see this thread with known bugs and workarounds (Particularly sound):

[http://ubuntuforums.org/showthread.php?t=595825](http://ubuntuforums.org/showthread.php?t=595825)

See also this thread:

[http://ubuntuforums.org/archive/index.php/t-620348.html](http://ubuntuforums.org/archive/index.php/t-620348.html)

If you have a recently upgraded kernel, does sound come up if you boot into an older one?

---

