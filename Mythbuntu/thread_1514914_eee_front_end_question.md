---
title: "eee front end question"
date: 2010-06-21
forum: Mythbuntu
---

### Post by el_heffe on 2010-06-21
Before I get flamed for not doing research, let me preface this with a short reason for this: I am forward deployed to Afghanistan on a crappy little FOB where I am lucky if I get a)time on the net and b)good transfer rates.

That being said, I purchased a refurb eeeBox b202 for 200 w/s&h for schoolwork.  It came with a Vesa mount and I was thinking that when I get home and back to internet access that it would make a far better front end than having my big media center under the tv.

As such I had a few questions- can I, should I, get an SD card and boot from that using the slightly meager 160g inside for a music/photo repo or should I just partition the hd and use the damned thing?  Also- I know that under linux 720p is out of the question, but can I stream video that are standard def reliably with an Atom processor?  The backend is more than capable, and probably can even transcode on the fly(possible?) if needed.  Any thoughts are much appreciated as this will give me something to look forward too.  

Thank you for your help!

SSG Heffron, B
US Army Signal Corps

---

### Post by Furry_Fighter_20x66 on 2010-06-22
hi el_heffe:

If I understand your question correctly, you want to just use it as a frontend when you are home on your internal network, right?

I have about three frontends here, and one of them is my eeepc 700 that runs the netbook remix 10.04. Just on my internal network I am able to walk around with the little thing and be able to watch live TV throughout the house. I have even taken the machine across the street and used it at the nearby community hall to stream live games from the satellite dish to the projector. By that point the signal strength was very weak (30-40%) but still worked flawlessly. (P.S. You should have seen my neighbors when they saw this setup. Lots of jaw dropping for sure.)

Now the processor in the 700 was still a celeron (running at 700mhz). I don't know how well that stacks up to the atom, but if I am able to get away with streaming a SD signal, then it should be feasible on your setup as well, pending any problems with your internal network.

Hope this helps.

---

### Post by el_heffe on 2010-06-24
That is exactly what I was hoping to hear.  Now I just wonder if I should run mythbuntu on the internal HD or use a SD card.

---

### Post by ian dobson on 2010-06-25
Hi,

As long as the SD card looks like a normal harddisk, you can install/run mythbuntu from a flash card.

I've been running my frontend from a "small" 8Gb CF card (40% full) in a CF to SATA adapter for about 18months now without any problems.

If you do use a flash based card for your system, make sure you setup your fstab to that the number of writes to the flash are limited as much as possible (noatime,nodirtime). This won't effect mythtv but it stops linux from updating the directory everytime you read a file.

Regards
Ian Dobson

---

### Post by el_heffe on 2010-06-25
> **ian dobson said:**
> Hi,

As long as the SD card looks like a normal harddisk, you can install/run mythbuntu from a flash card.

I've been running my frontend from a "small" 8Gb CF card (40% full) in a CF to SATA adapter for about 18months now without any problems.

If you do use a flash based card for your system, make sure you setup your fstab to that the number of writes to the flash are limited as much as possible (noatime,nodirtime). This won't effect mythtv but it stops linux from updating the directory everytime you read a file.

Regards
Ian Dobson

Good to know.  I was actually looking into one of those CF to IDE adapters to run a dual 8g raid for my aging PowerBook G4.  Good point on the fstab, would not have thought of that.  Thank you for your input!

---

### Post by larsolav on 2010-06-25
> **ian dobson said:**
> Hi,

As long as the SD card looks like a normal harddisk, you can install/run mythbuntu from a flash card.

I've been running my frontend from a "small" 8Gb CF card (40% full) in a CF to SATA adapter for about 18months now without any problems.

If you do use a flash based card for your system, make sure you setup your fstab to that the number of writes to the flash are limited as much as possible (noatime,nodirtime). This won't effect mythtv but it stops linux from updating the directory everytime you read a file.

Regards
Ian Dobson
Not to hijack the thread or anything, but Ian, I recently followed your lead and installed 10.04 to a CF drive, and I am not quite sure where to put those two options in fstab. Could you pretty please share the lines of fstab that have those options in your fstab? 

Sincerely,
Lars

---

### Post by ian dobson on 2010-06-26
> **larsolav said:**
> Not to hijack the thread or anything, but Ian, I recently followed your lead and installed 10.04 to a CF drive, and I am not quite sure where to put those two options in fstab. Could you pretty please share the lines of fstab that have those options in your fstab? 

Sincerely,
Lars

Hi,

Just edit you /etc/fstab with an editor of choice. Here's my fstab:-

```

# /etc/fstab: static file system information.
#
# <file system>                           <mount point> <type> <options>                                                    <dump>  <pass>
proc                                      /proc         proc  defaults                                                      0       0
# /dev/sda1
UUID=671953de-a48b-464e-ac26-1707715287bf /             ext4  noatime,errors=remount-ro,data=writeback,commit=15,barrier=0  0       0
/dev/scd0                                 /media/cdrom0       udf,iso9660 user,noauto,exec,utf8                             0       0
/dev/sdb1                                 /mytharchive  ext4  noatime,errors=remount-ro,data=writeback,barrier=0            0       0

```

/dev/sda is my CF card, note the options line starting with noatime. The filesystem on the cf card is ext4 (I converted it from ext3 yesterday, including updating to grub2).

I lars could you supply me with a dump of hdparm -I /dev/sdX (x is your CF card), my adapter seems to be stuck at udma33 when the CF card says is can transfer up to 90mb (udma100).
 
Regards
Ian Dobson

---

### Post by larsolav on 2010-06-28
Thanks Ian!
I'll try this tonight (in about 11 hours or so....) Did not have a chance to visit the forums over the weekend. Will post the result of the command you requested as well. Stay tuned!

---

### Post by larsolav on 2010-06-28
Ian,
here is the output of the command (what part are you looking at?):
> Lars@Mythbox:/etc/lirc$ sudo hdparm -I /dev/sda1

/dev/sda1:

CompactFlash ATA device
        Model Number:
        Serial Number:      CF CARD     A0202A5A
        Firmware Revision:  20090728
Standards:
        Likely used: 6
Configuration:
        Logical         max     current
        cylinders       31045   31045
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   31293360
        LBA    user addressable sectors:   31293360
        Logical/Physical Sector size:           512 bytes
        device size with M = 1024*1024:       15279 MBytes
        device size with M = 1000*1000:       16022 MBytes (16 GB)
        cache/buffer size  = 1 KBytes (type=DualPort)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 4
        Standby timer values: spec'd by Vendor
        R/W multiple sector transfer: Max = 1   Current = 0
        Advanced power management level: disabled
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                Power Management feature set
           *    Write cache
                WRITE_BUFFER command
                READ_BUFFER command
                NOP cmd
                CFA feature set
                Advanced Power Management feature set
           *    Mandatory FLUSH_CACHE
           *    CFA advanced modes: pio5 pio6 mdma3 mdma4
           *    CFA Power Level 1  (max 500mA)
HW reset results:
        CBLID- above Vih
        Device num = 0
Integrity word not set (found 0x0000, expected 0x1fa5)


el_heffe, sorry to so blatantly have hijacked your thread...

---

### Post by ian dobson on 2010-06-29
Hi larsolav,

OK it looks as if your CF adapter supports udma100:-

DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4

while my card is stuck at udma2 (udma33):-
DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2

OK 32Mbyte/sec for read/write isn't too bad but I'm using a 600x card which supports udma133.

What adapter are you using? Mine is a bog standard SATA->CF adapter with a Marvell 88SA8040-TBC1 bridge chip.

Regards
Ian Dobson

---

### Post by larsolav on 2010-06-29
I picked up one at Fry's. I believe it is this one:
[http://www.frys.com/product/5962414?](http://www.frys.com/product/5962414?)

I think this is the CF card:
[http://www.frys.com/product/6111459](http://www.frys.com/product/6111459)

---

