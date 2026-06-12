---
title: "Laptop Media Reader Nonfunctonal"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by narnie on 2007-05-19
I have tried both SD and xD cards in my media reader on my Acer Aspire 5610. Neither mount when I insert them.

lspsc gives

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

```

When I insert a card, nothing happens.

I checked /var/log/messages and nothing is there relating to this (I don't know if that is really the right place to look, though.

I have nothing in /etc/fstab that seems to be related to the reader(s). Does it need mounted somehow? What about pmount? When I plug in a usb drive, it mounts automatically.

Any ideas?

Thanks,
Narnie

---

### Post by narnie on 2007-05-19
BTW, I see no potential things to mount under /dev (but I'm a bit of a noob)

here is a listing
```

acpi       ptyc7  ptyr3  ptyvf  ram5        tty52  ttydc  ttys4  ttyx0
adsp       ptyc8  ptyr4  ptyw0  ram6        tty53  ttydd  ttys5  ttyx1
agpgart    ptyc9  ptyr5  ptyw1  ram7        tty54  ttyde  ttys6  ttyx2
audio      ptyca  ptyr6  ptyw2  ram8        tty55  ttydf  ttys7  ttyx3
bus        ptycb  ptyr7  ptyw3  ram9        tty56  ttye0  ttys8  ttyx4
cdrom      ptycc  ptyr8  ptyw4  random      tty57  ttye1  ttys9  ttyx5
cdrw       ptycd  ptyr9  ptyw5  rtc         tty58  ttye2  ttysa  ttyx6
console    ptyce  ptyra  ptyw6  scd0        tty59  ttye3  ttysb  ttyx7
core       ptycf  ptyrb  ptyw7  sda         tty6   ttye4  ttysc  ttyx8
disk       ptyd0  ptyrc  ptyw8  sda1        tty60  ttye5  ttysd  ttyx9
dri        ptyd1  ptyrd  ptyw9  sda2        tty61  ttye6  ttyse  ttyxa
dsp        ptyd2  ptyre  ptywa  sda3        tty62  ttye7  ttysf  ttyxb
dvd        ptyd3  ptyrf  ptywb  sda4        tty63  ttye8  ttyt0  ttyxc
dvdrw      ptyd4  ptys0  ptywc  sda5        tty7   ttye9  ttyt1  ttyxd
fb0        ptyd5  ptys1  ptywd  sda6        tty8   ttyea  ttyt2  ttyxe
fd         ptyd6  ptys2  ptywe  sequencer   tty9   ttyeb  ttyt3  ttyxf
full       ptyd7  ptys3  ptywf  sequencer2  ttya0  ttyec  ttyt4  ttyy0
fuse       ptyd8  ptys4  ptyx0  sg0         ttya1  ttyed  ttyt5  ttyy1
hpet       ptyd9  ptys5  ptyx1  sg1         ttya2  ttyee  ttyt6  ttyy2
initctl    ptyda  ptys6  ptyx2  shm         ttya3  ttyef  ttyt7  ttyy3
input      ptydb  ptys7  ptyx3  snapshot    ttya4  ttyp0  ttyt8  ttyy4
kmem       ptydc  ptys8  ptyx4  snd         ttya5  ttyp1  ttyt9  ttyy5
kmsg       ptydd  ptys9  ptyx5  sndstat     ttya6  ttyp2  ttyta  ttyy6
log        ptyde  ptysa  ptyx6  sr0         ttya7  ttyp3  ttytb  ttyy7
loop0      ptydf  ptysb  ptyx7  stderr      ttya8  ttyp4  ttytc  ttyy8
MAKEDEV    ptye0  ptysc  ptyx8  stdin       ttya9  ttyp5  ttytd  ttyy9
mem        ptye1  ptysd  ptyx9  stdout      ttyaa  ttyp6  ttyte  ttyya
mixer      ptye2  ptyse  ptyxa  tty         ttyab  ttyp7  ttytf  ttyyb
net        ptye3  ptysf  ptyxb  tty0        ttyac  ttyp8  ttyu0  ttyyc
null       ptye4  ptyt0  ptyxc  tty1        ttyad  ttyp9  ttyu1  ttyyd
nvidia0    ptye5  ptyt1  ptyxd  tty10       ttyae  ttypa  ttyu2  ttyye
nvidiactl  ptye6  ptyt2  ptyxe  tty11       ttyaf  ttypb  ttyu3  ttyyf
port       ptye7  ptyt3  ptyxf  tty12       ttyb0  ttypc  ttyu4  ttyz0
ppp        ptye8  ptyt4  ptyy0  tty13       ttyb1  ttypd  ttyu5  ttyz1
psaux      ptye9  ptyt5  ptyy1  tty14       ttyb2  ttype  ttyu6  ttyz2
ptmx       ptyea  ptyt6  ptyy2  tty15       ttyb3  ttypf  ttyu7  ttyz3
pts        ptyeb  ptyt7  ptyy3  tty16       ttyb4  ttyq0  ttyu8  ttyz4
ptya0      ptyec  ptyt8  ptyy4  tty17       ttyb5  ttyq1  ttyu9  ttyz5
ptya1      ptyed  ptyt9  ptyy5  tty18       ttyb6  ttyq2  ttyua  ttyz6
ptya2      ptyee  ptyta  ptyy6  tty19       ttyb7  ttyq3  ttyub  ttyz7
ptya3      ptyef  ptytb  ptyy7  tty2        ttyb8  ttyq4  ttyuc  ttyz8
ptya4      ptyp0  ptytc  ptyy8  tty20       ttyb9  ttyq5  ttyud  ttyz9
ptya5      ptyp1  ptytd  ptyy9  tty21       ttyba  ttyq6  ttyue  ttyza
ptya6      ptyp2  ptyte  ptyya  tty22       ttybb  ttyq7  ttyuf  ttyzb
ptya7      ptyp3  ptytf  ptyyb  tty23       ttybc  ttyq8  ttyv0  ttyzc
ptya8      ptyp4  ptyu0  ptyyc  tty24       ttybd  ttyq9  ttyv1  ttyzd
ptya9      ptyp5  ptyu1  ptyyd  tty25       ttybe  ttyqa  ttyv2  ttyze
ptyaa      ptyp6  ptyu2  ptyye  tty26       ttybf  ttyqb  ttyv3  ttyzf
ptyab      ptyp7  ptyu3  ptyyf  tty27       ttyc0  ttyqc  ttyv4  urandom
ptyac      ptyp8  ptyu4  ptyz0  tty28       ttyc1  ttyqd  ttyv5  vcs
ptyad      ptyp9  ptyu5  ptyz1  tty29       ttyc2  ttyqe  ttyv6  vcs1
ptyae      ptypa  ptyu6  ptyz2  tty3        ttyc3  ttyqf  ttyv7  vcs2
ptyaf      ptypb  ptyu7  ptyz3  tty30       ttyc4  ttyr0  ttyv8  vcs3
ptyb0      ptypc  ptyu8  ptyz4  tty31       ttyc5  ttyr1  ttyv9  vcs4
ptyb1      ptypd  ptyu9  ptyz5  tty32       ttyc6  ttyr2  ttyva  vcs5
ptyb2      ptype  ptyua  ptyz6  tty33       ttyc7  ttyr3  ttyvb  vcs6
ptyb3      ptypf  ptyub  ptyz7  tty34       ttyc8  ttyr4  ttyvc  vcs7
ptyb4      ptyq0  ptyuc  ptyz8  tty35       ttyc9  ttyr5  ttyvd  vcs8
ptyb5      ptyq1  ptyud  ptyz9  tty36       ttyca  ttyr6  ttyve  vcsa
ptyb6      ptyq2  ptyue  ptyza  tty37       ttycb  ttyr7  ttyvf  vcsa1
ptyb7      ptyq3  ptyuf  ptyzb  tty38       ttycc  ttyr8  ttyw0  vcsa2
ptyb8      ptyq4  ptyv0  ptyzc  tty39       ttycd  ttyr9  ttyw1  vcsa3
ptyb9      ptyq5  ptyv1  ptyzd  tty4        ttyce  ttyra  ttyw2  vcsa4
ptyba      ptyq6  ptyv2  ptyze  tty40       ttycf  ttyrb  ttyw3  vcsa5
ptybb      ptyq7  ptyv3  ptyzf  tty41       ttyd0  ttyrc  ttyw4  vcsa6
ptybc      ptyq8  ptyv4  ram0   tty42       ttyd1  ttyrd  ttyw5  vcsa7
ptybd      ptyq9  ptyv5  ram1   tty43       ttyd2  ttyre  ttyw6  vcsa8
ptybe      ptyqa  ptyv6  ram10  tty44       ttyd3  ttyrf  ttyw7  video
ptybf      ptyqb  ptyv7  ram11  tty45       ttyd4  ttys0  ttyw8  video0
ptyc0      ptyqc  ptyv8  ram12  tty46       ttyd5  ttyS0  ttyw9  xconsole
ptyc1      ptyqd  ptyv9  ram13  tty47       ttyd6  ttys1  ttywa  zero
ptyc2      ptyqe  ptyva  ram14  tty48       ttyd7  ttyS1  ttywb
ptyc3      ptyqf  ptyvb  ram15  tty49       ttyd8  ttys2  ttywc
ptyc4      ptyr0  ptyvc  ram2   tty5        ttyd9  ttyS2  ttywd
ptyc5      ptyr1  ptyvd  ram3   tty50       ttyda  ttys3  ttywe
ptyc6      ptyr2  ptyve  ram4   tty51       ttydb  ttyS3  ttywf


```

---

### Post by pebo on 2007-05-19
I've got the same ENE card reader set up on my laptop and I've been looking round for drivers for a while - I don't think there are any available. I've only tried the xD card - you might be able to get the SD card to work - see [this]("http://ubuntuforums.org/showthread.php?t=420721&highlight=sd+card+reader") thread. Good luck!

---

### Post by narnie on 2007-05-19
according the this website
[http://www.freewebs.com/gkiagia/linuxonaceraspire9113.htm](http://www.freewebs.com/gkiagia/linuxonaceraspire9113.htm)

it should be recognized by edgy on up.

says something about the yenta module, but I tried a modprobe and it didn't find it. I'll do some looking around.

---

### Post by narnie on 2007-05-19
This site may be helpful to us
[http://advhertz.altervista.org/install-debian-gnulinux-on-acer-aspire-9113-wlmi/](http://advhertz.altervista.org/install-debian-gnulinux-on-acer-aspire-9113-wlmi/)

It shows the follow modules as needed:
sdhci
mmc_core
mmc_block
pcmcia
pcmcia_core
yenta_socket
rsrc_nonstatic

I loaded (or they were already loaded) all except for mmc_block. It is not present on my system. I read somewhere about compiling it into mmc_core, so this may be why. But I also found mmc_block for 2.6.17 listed but it has 500 lines with the numbers of the lines before the code and I don't want to hand edit out each and try to compile it. So far, can't find the source code for mmc_block.

I'm not even sure I'd know how to compile the module if I found the code. Is it:
gcc -c mmc_block.c
???

Sure would like to get this working.

---

