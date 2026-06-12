---
title: "Can't mount AudioCD :("
date: 2006-10-20
forum: Multimedia &amp; Video
---

### Post by mee.six on 2006-10-20
Hello,
 Can somebody tell me how to mound audio CD? I get this code

each time I try to mount audio cd... and I wish to listen to it so much :(
```

zea@zea:~$ sudo mount /media/cdrom
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


zea@zea:~$ dmesg | tail
[17191470.544000] hdc: command error: error=0x54 { AbortedCommand 
LastFailedSense=0x05 }
[17191470.544000] ide: failed opcode was: unknown
[17191470.544000] end_request: I/O error, dev hdc, sector 64
[17191470.544000] isofs_fill_super: bread failed, dev=hdc, 
iso_blknum=16, block=16
[17191500.136000] hdc: command error: status=0x51 { DriveReady 
SeekComplete Error }
[17191500.136000] hdc: command error: error=0x54 { AbortedCommand 
LastFailedSense=0x05 }
[17191500.136000] ide: failed opcode was: unknown
[17191500.136000] end_request: I/O error, dev hdc, sector 64
[17191500.136000] isofs_fill_super: bread failed, dev=hdc, 
iso_blknum=16, block=16
[17191588.328000] usb 3-5: reset high speed USB device using ehci_hcd 
and address 2


```

---

### Post by Kateikyoushi on 2006-10-20
Sound juicer automatically starts if I put a cd in the machine.
What are yor settings in System >> Preferences >> Removable Drives and media ?

---

### Post by mee.six on 2006-10-20
I'm using Xubuntu, but... System->Disks says that there is an audiocd, and even shows its length... but when I push "Play CD" nothing happens.
Now I'm installing juicer, maybe this will help:) 

Thanks for hint.

---

### Post by rayburn on 2006-10-22
Installing 'juicer' solved the problem for me on Xubuntu, as I had the same symptoms.

Many thanks!

---

### Post by john.nicholls on 2006-10-22
You don't mount audio CDs.

John

---

### Post by insub2 on 2006-10-23
> **john.nicholls said:**
> You don't mount audio CDs.

John

what do you do, john?  please share your knowledge.  and don't be smug.

---

### Post by john.nicholls on 2006-10-25
> **insub2 said:**
> what do you do, john?  please share your knowledge.  and don't be smug.

Sorry, I wasn't trying to be smug. Any other sort of disc needs to be mounted in Linux before you can access it. This may be done automatically, or you may have to do it manually, but mounting is necessary before you can access the filesystem on the disc. However audio discs don't have a filesystem on them, and so they can't be mounted in that sense. You just put them in the CD-ROM drive and call up the appropriate software to play them. Playing them on a computer is the same as in any other CD player.

Hope that makes sense
John

---

### Post by insub2 on 2006-10-29
Thank you.

---

### Post by seshomaru samma on 2006-10-30
I have the same problem with Xubuntu
I will try the juicer
On another note - is it the same with USB keys?
Should I install a special programme to "mount" them?
At the moment when I put a USB key in , Xubuntu ignores it and I cant find it anywhere , I tried different USBs on several machines.

---

### Post by saul_2110 on 2006-12-11
Hi. I had the same problem of not being able to listen audio cd's. I **installed xmms but didn't work until I configured the audio cd plugin**. To do this, open xmms -> menu (upper left corner) -> options -> preferences:
1. In the "Audio I/O plugins" select "CD Audio Player" and make sure the "enable plugin" checkbox is checked.
2. Then select "configure". In the "Device type" type, write the correct drive and mount point (/dev/hdb and /media/cdrom for example) in "Device"
3. In "Play mode", selec the checkbox of "Analog".
4. With an audio CD inside, click the "Check drive" button to make sure everything is correct.
5. Accept everything.
6. Go to menu -> "play directory" or "play location". If "play directory", a tree will apper, then select the mount point you specified. If "play location", write the mount point you specified.
7. Off you go.

Hope this work for you. Let me know. :) 

-saul

---

