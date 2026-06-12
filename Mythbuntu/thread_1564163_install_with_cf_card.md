---
title: "install with cf card"
date: 2010-08-30
forum: Mythbuntu
---

### Post by blkbx on 2010-08-30
Hi 
I have to do re-install mythbuntu after it killed itself. Well I think it's a db problem that ran out of control. Anyway the sounds of the hdd where killing me so I thought I'd try a front end backend setup. I want to use a compact flash card for the frontend. I have two terabyte drives for the backend, Just wondering will a cf 4gig cf card be big enough and hat other things should I be aware of.
thank

---

### Post by ian dobson on 2010-08-30
Hi,

My frontend boots/runs from a 8Gb CF card in a SATA/CF adapter. Been running it like this for over a year now without any problems.

At the moment the frontend is using about 30-35% of the 8Gb card so a 4Gb card would be enough for a small installation without too many plugins.

Just make sure that you try and reduce the number of write cycles to the card (I'm booting ext4 with a 20 second commit, no journel etc). After going over to the CF card my frontend is now almost silent (One 120mm fan running at 300-500rpm).

The specs of my frontend are as following:-
Intel Core2Duo 5200 underclocked/undervolted to 1200MHz,0.99Volt
NVIDIA 9600GT underclocked to about 450MHz through a BIOS hack
8Gb 600x CF card for boot/root
16Gb 300x CF card for mythgames (never get time to play with it)

Regards
Ian Dobson

---

### Post by ian dobson on 2010-08-30
Hi,

Just did an apt-get update/upgrade and am now sitting at 41% on my 8Gb CF card, so 4Gb could be abit small,unless you can delete things you don't need (documentaion/man pages etc, themes).

@myth-frontend:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              7700428   2940284   4368964  41% /
none                   1024516       296   1024220   1% /dev
none                   1029028         0   1029028   0% /dev/shm
none                   1029028       300   1028728   1% /var/run
none                   1029028         0   1029028   0% /var/lock
none                   1029028         0   1029028   0% /lib/init/rw
/dev/sdb1             15512328   4346672  10377672  30% /mytharchive

Atleast the box boots really quickly (11-12 seconds).

Regards
Ian Dobson

---

### Post by blkbx on 2010-08-30
Cheers for the reply.
I've read about reducing the writes to the card. Does using ext4 do it on it's own or do I have to configure it in some way. Also are there any specs that the card should adhere to or is a generic(cheap)card. I've seen also in some old posts, 07 and 08 that udma causes some grief. I'm hoping that that's been fixed but as you have a working system does is it something I should keep in mind when I install.

---

### Post by ian dobson on 2010-08-31
Hi,

Reducing writes to the cf card just involves setting afew options in the fstab file (noatime,nodirtime) these options stop linux from updating the last read time for each file when reading.

Do you already have an adapter (SATA or IDE or CF)? Some early adapters weren't that good. But I've now used 4 different adapters (mainly 8$ jobs from ebay) and have not had any real problems. Most adapters these days support UDMA33 which limits your read/write speed to 33Mbyte/sec. The adapter I'm using at the moment supports UDMA100 and when used with a 600x CF card I get 66Mb/sec read/write speed. If use use a generic 133x card you'll be limited to about 10-20Mbyte/sec which is enough for booting linux/getting mythfrontend up and running.

Here's my fstab
```
myth-frontend:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system>                           <mount point> <type> <options>                                                                 <dump>  <pass>
proc                                      /proc         proc  defaults                                                                      0       0
# /dev/sda1
UUID=671953de-a48b-464e-ac26-1707715287bf /             ext4  noatime,nodiratime,nobh,barrier=0,errors=remount-ro,data=writeback,commit=30  0       0
/dev/scd0                                 /media/cdrom0       udf,iso9660 user,noauto,exec,utf8                                             0       0
/dev/sdb1                                 /mytharchive  ext4  noatime,nodiratime,nobh,barrier=0,errors=remount-ro,data=writeback,commit=30  0       0
```

and the relevant dmesg:-
```
[    0.359672] ata_piix 0000:00:1f.2: version 2.13
[    0.359712] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.359712] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.359758] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.359934] scsi0 : ata_piix
[    0.360091] scsi1 : ata_piix
[    0.360716] ata1: SATA max UDMA/133 cmd 0xd000 ctl 0xd400 bmdma 0xe000 irq 19
[    0.360719] ata2: SATA max UDMA/133 cmd 0xd800 ctl 0xdc00 bmdma 0xe008 irq 19
[    0.560110] ata2.00: ATA-0: ELITE PRO CF CARD 16GB, Ver2.22K, max UDMA/100
[    0.560114] ata2.00: 31522176 sectors, multi 0: LBA
[    0.560120] ata2.00: applying bridge limits
[    0.579988] ata1.00: CFA: TRANSCEND, 20091215, max UDMA/133
[    0.579990] ata1.00: 15662304 sectors, multi 0: LBA
[    0.579996] ata1.00: applying bridge limits
[    0.580007] ata1.01: ATAPI: Optiarc DVD RW AD-5240S, 1.03, max UDMA/100
[    0.580113] ata2.00: configured for UDMA/100
[    0.619989] ata1.00: configured for UDMA/100
[    0.620115] ata2.00: configured for UDMA/100
[    0.620118] ata2: EH complete
[    0.659987] ata1.01: configured for UDMA/100
[    0.700029] ata1.00: configured for UDMA/100
[    0.739997] ata1.01: configured for UDMA/100
```
Regards
Ian Dobson

---

### Post by blkbx on 2010-09-01
Bought a Sandisk extreme 8gb - 60mb/s 400x. I hope that that will allow me to install mythbuntu plus whatever I need to add. Vlc and a bit torrent client is all I can think of really and I can use a usb stick to download data to it from the client. Something to look forward too doing, well other than a stag night and a kick boxing social evening but hey it's the first day of spring.
[B]
[/B]

---

### Post by ian dobson on 2010-09-01
> **blkbx said:**
> Bought a Sandisk extreme 8gb - 60mb/s 400x. I hope that that will allow me to install mythbuntu plus whatever I need to add. Vlc and a bit torrent client is all I can think of really and I can use a usb stick to download data to it from the client. Something to look forward too doing, well other than a stag night and a kick boxing social evening but hey it's the first day of spring.
[B]
[/B]

I you need to have a look at your clock/time zone. We have Autumn in Europe. Unless your down under of course.

Regards
Ian Dobson

ps. Have fun installing, it's just like installing to a harddisk, maybe abit slower but not so loud.

---

