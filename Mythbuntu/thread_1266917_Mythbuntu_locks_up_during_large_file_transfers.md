---
title: "Mythbuntu locks up during large file transfers"
date: 2009-09-15
forum: Mythbuntu
---

### Post by dualboot on 2009-09-15
I am thinking of starting again from scratch with my Mythbuntu setup, but I would like to back up a few programs that I haven't yet watched, and also move my music and photos (this box has the primary copy of these files).

I created a NFS share to a FreeNAS server, and then used the archive options to save programs with their metadata.  It would seem to work OK, but it kept locking up.  I realised that it would usually be with files over 500M, or if I tried to do a list of files.

I then tried just copying the files using cp or rsync, but same symptoms.

I wondered if the problem was NFS, so have ditched that and tried the rsync server on FreeNAS, but still it locks up after a few minutes transfer.

There are no logs entries to speak of, and the box is just hung - doesn't even answer a ping, and only holding in the power button for 10 seconds will do.

Its a 1TB drive in Mythbuntu, and a 1TB drive in FreeNAS.

Mythbuntu is running version 8 (not sure dot what, but its telling me 9.04 is available).  Tempted to try upgrading to that, but without a way to go back if it gets toasty I'm nervous.

---

### Post by oobe-feisty on 2009-09-15
you just need to back up your / partition 

having said that the best way to do it is while the system is down

boot a live cd mount your root partition then back it up to an external source using tar

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /mnt/root


to restore it 

boot the live cd mount the target to restore make sure its empty

then copy the backup.tgz 

then unpack using tar xvpfz backup.tgz

then 

mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
mkdir tmp
chmod a+rw /tmp

---

### Post by SiHa on 2009-09-15
A couple of thoughts, what Filesystem do you have on the NAS? Some are better than others when it comes to large files, not sure if any are bad enough to cause lockups, but you never know. Of course, if the NAS already has stuff on it, then changing FS type is probably out of the question.

To remove any chance that networking is somehow causing the problem, how about temporarily removing the drive from the NAS and directly connecting it to the Mythbox for the transfer? I've just added a new 500GB drive to my Myth backend, and copying ~200MB of recordings took about 20 - 25 minutes. Both drives are SATA II and EXT3 (I think, the Mythbox is Ubuntu + MythTV, so should be EXT3 IIRC).

There's quite a good FS benchmarking article [[COLOR="Blue"]_here_[/COLOR]](http://www.debian-administration.org/articles/388)

---

### Post by dualboot on 2009-09-15
Thanks oobe-feisty.  I might try that.  The only problem is that because I started on version 7 my system is all one big partition, so its 8-900Gigs worth - was hoping to just back up a recordings and then import them later.

SiHa - the NAS is complicated - its actually a 1.5TB drive running ESXi, and 1TB of it is carved up for FreeNAS (as 5 x 200G virtual disks in a JBOD raid - (said it was complex :P )

so moving the drive over is a non-starter.

I've had a thought though - if I put a second smaller disk in (can disconnect the main one, whilst I try a fresh install), once it done, can I merge the two together - OS on the new small disk, DB and files on the old one ?

---

### Post by oobe-feisty on 2009-09-15
this is how i would want things setup dont know how you can manage it without equal sized drives to copy files over 

but i would want 

/ 20 GB for root | in future this would make backups and reinstalls feasable

/home 30GB or more if you need it

then partition the rest for media i.e /mnt/recordings /mnt/mythtvideo


> 
I've had a thought though - if I put a second smaller disk in (can disconnect the main one, whilst I try a fresh install), once it done, can I merge the two together - OS on the new small disk, DB and files on the old one ?

yes this will work 

if you can add one more drive without messing up your raid i would install a fresh install of mythbuntu probably worth wait till 9.10 as you will want to upgrade to that soon anyway as it comes with .22 mythtv

---

### Post by Mister.Vash on 2009-09-16
Just a quick thought on the lock up during file transfer -

I've seen similar issues when the network card is sharing an interrupt with another device on the system.  Can you check and see if you are sharing the IRQ of the network card with anything?
cat /proc/interrupts
should show what the are using.  Some brief points on troubleshooting them can be found here
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

---

### Post by dualboot on 2009-09-16
I've pasted my /proc/interrupts below - I think this puts it in the clear.

I will try a live CD and copy to an NFS mount as soon as I can - this will eliminate anything in the day to day setup if it works.


root@user-desktop:/home/user# cat /proc/interrupts
           CPU0       CPU1
  0:        113         15   IO-APIC-edge      timer
  1:          0          2   IO-APIC-edge      i8042
  4:          0          2   IO-APIC-edge
  8:          0        116   IO-APIC-edge      rtc0
  9:          0          3   IO-APIC-fasteoi   acpi
 12:          0          4   IO-APIC-edge      i8042
 14:      10705     526553   IO-APIC-edge      pata_atiixp
 15:          0          0   IO-APIC-edge      pata_atiixp
 16:          0        430   IO-APIC-fasteoi   ohci_hcd:usb1, HDA Intel
 17:          1         66   IO-APIC-fasteoi   ohci_hcd:usb2, ohci_hcd:usb5
 18:       4265     253013   IO-APIC-fasteoi   ohci_hcd:usb4, ohci_hcd:usb6, fglrx[0]@PCI:1:5:0
 19:       1095      46353   IO-APIC-fasteoi   ehci_hcd:usb3, HDA Intel
 20:       2697     624278   IO-APIC-fasteoi   ehci_hcd:usb7
 21:          0          3   IO-APIC-fasteoi   ohci1394
 22:       1222      57188   IO-APIC-fasteoi   ahci, uhci_hcd:usb8
 23:          0          0   IO-APIC-fasteoi   uhci_hcd:usb9
221:       3408     122953   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:   30853067    6385292   Local timer interrupts
RES:     181210     105957   Rescheduling interrupts
CAL:        412       8430   function call interrupts
TLB:       1029        577   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

---

### Post by dualboot on 2009-09-18
Tried a live linux (actually systemrescueCD) and did an rsync of my videos folder of some 30G without a hiccup, which shows that the network and the NAS at the other end are OK.

I think I will try doing an archive of my shows to a local folder, then using a live cd move them off to the NAS as a batch job on night.

got to save my pennies for a new SATA drive - all my spares are IDE : (

---

