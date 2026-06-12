---
title: "Jumpy ftp transfer"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by arthur2710 on 2008-12-28
I just installed vsftpd and set it up, but now when I try to upload a file it starts of fast like 7mb/s put then it goes to 0 then back up and down.... Thats over lan so whats wrong?

*EDIT*
Ok more info,
I set up port forwarding for port 21 to the system.
I have 4 harddrives

1.IDE connected to the Mobo 10gb for the file system.
2.Same as #1 but a WesternDigital 250gb
3.SATA to USB connected to a 5 port pci usb hub Maxtor 250gb
4.Same as #3 but a Segate 1.5Tb

The one connected to the mobo works at a average of 4mb/s
the 2 usb drives are the ones jumping.

---

### Post by mtopro on 2008-12-28
I use gFTP which I have never had issues with.  It is easy to use.  Wanna try it?

'Applications' pulldown 'Add/Remove' and search for gFTP.

It is pretty straight forward and also supports sftp among other things..

HTH

---

### Post by arthur2710 on 2008-12-28
You must have replayed before I finished editing!
Thanks but its probably not the program. Ill try a different hub.

*EDIT* 
Ok I just put the 2 sata drives on a powered 7 port usb hub and on a usb port on the mobo
then I tried again, but it gives me the same results. 

I will try to do one of them directly to a usb port.

*EDIT2*
Ok I tried to connect a drive directly to a usb port but it gives me the same.

*EDIT3*
transferring a 700mb video between the two IDE drives takes 2 min
and from a usb drive to a IDE takes 15min.

---

### Post by mtopro on 2008-12-28
See me jumping to conclusions?  Didn't realize you were still working on it.:D

So it appears the title to this post may not be completely accurate? It seems your problem is more related to the USB speed of your drives?

I have also had similar issues on a computer that is not so old.  Didn't see any info on the type of computer or USB hardware.

Can you take the network out of the equation as well and try to transfer a chunk of data from the local drive to the external?  Does it do the same thing?  Given the information here, my hunch tells me it's the USB port or cable?

*EDIT*
Seems you're edits are ahead of any replys I can make..  :D

---

### Post by arthur2710 on 2008-12-28
I tried 
sudo modprobe ehci_hcd
It kind of changed it... but still really slow.
It starts at like 4 min but goes up to 10,
you can see how the bar moves a bit then stops, then moves a bit more and stops and....

---

### Post by anubhavrocks on 2008-12-28
How much memory does your box have?A memory squeeze can cause slowdowns.

---

### Post by anubhavrocks on 2008-12-28
Are downloads slow too?

---

### Post by arthur2710 on 2008-12-28
> **anubhavrocks said:**
> How much memory does your box have?A memory squeeze can cause slowdowns.

I dont know:( I needed a server so I grabed a used (free) pc and put ubuntu on it. 

It should be enough because it works with the other two drives.
I just did [http://ubuntuforums.org/showpost.php?p=5447719&postcount=10](http://ubuntuforums.org/showpost.php?p=5447719&postcount=10) 
Ill reply in a few min.

*EDIT*
Humm I did a 
shutdown -r now
but now its rebooting and checking the drives kind of slow, so I unpluged the 2 usb drives before it got to them.

*EDIT2*
man im in trouble. It was either
echo 16384 > /sys/block/sdd/device/max_sectors 
or [http://ubuntuforums.org/showpost.php?p=5447719&postcount=10](http://ubuntuforums.org/showpost.php?p=5447719&postcount=10)
I undid the second with sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst
so is it the first one?
I cant boot, it keeps tring to check the disk but errors at like 47% and askes for the password, then it starts the command line. It recomended running e2fsk so I am doing it right now.

What happened? Can this be fixed? I really don't want to reinstall, spent almost 2 days setting it up.

---

