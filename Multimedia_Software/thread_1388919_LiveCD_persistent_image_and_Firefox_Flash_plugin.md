---
title: "LiveCD persistent image and Firefox Flash plugin"
date: 2010-01-23
forum: Multimedia Software
---

### Post by BLANDCorporatio on 2010-01-23
Greetings,

I have a Ubuntu 9.10 LiveCD (and I plan to keep using it as just a LiveCD); this works fine.

Firefox works fine too, and installing a flash player plugin is all right.

The problem appears when I reboot and see that Firefox no longer has the flash plugin installed.

So I tried making a persistent image USB stick for this, added the persistent keyword at the end of the boot options, and Firefox still forgets that it can actually play youtube videos.

The persistent image USB seems to be doing something, at least browsing through it shows several folders, for instance /usr/lib/adobe-flashplugin which constains a file libflashplayer.so

It's just that Firefox doesn't seem to care. What else should I do?

Thanks!

---

### Post by C.S.Cameron on 2010-01-23
You are labeling the partition on your pendrive casper-rw?

That should work as long as you are typing (space)persistent.
It took me hours to figure there should be a space before persistent.

You could also add a partition to your flash drive labeled home-rw and it should save your home folder stuff.

---

### Post by BLANDCorporatio on 2010-01-23
Yes, casper-rw is the name I use, that's probably not the problem.

Should persistent come after or instead of the "--" at the end of the boot options?

Does the number of spaces matter?

Thanks for the home-rw, that sounds like a nice tip!

---

### Post by C.S.Cameron on 2010-01-23
As soon as the Try Ubuntu screen comes up I press F6 then esc, (to get rid of the expert mode menu) then (space)persistent.

---

### Post by garvinrick4 on 2010-01-23
I use USB Start-up Creator in Ubuntu and get 4 gig of persistence after I get it where I want it.
I make sure I turn all updates off after first update and upgrade and in Firefox save nothing like in private browsing always so
as not to take up any drive space. Have about 52 meg left and stays there, which is fine. Can
use as a live CD or a 9.10 karmic system. Nothing seems to get over 4 gig persistence. Had a 16 gig that did, formatted in ext3 with /boot and / and swap. 3 partitions and worked fine on own machine but you put in another machine and will install grub2 which is fine if it already has one but if in a Windows machine with out grub2 owner might freak out when he see's his boot as a grub2. 
 Any way if you want the max of 4 gig persistence in fat32 then this usb startup creator in Ubuntu repositories was sure easy to install. Just needed a .iso file tell it to use 4 gig and say
start. I believe all in fat32 are maxed out at 4 gig.

---

### Post by BLANDCorporatio on 2010-01-24
[B]C. S. Cameron:

[/B]That is exactly what I'm doing. Well, the boot options look like this at first "{...} quiet splash -- " so I delete the two minus signs and add in persistent so that it looks like "{...} quiet splash persistent".

**garvinrick4**:

Thanks, that info may well be useful later!

However the problem for now is not lack of space on the persistent image, but rather Firefox not using it.

Lets say I configure Firefox to use APT, then go to Adobe and install a Flash Player plugin (which will work, I can watch youtube for example). These kinds of things should be remembered by the persistent image, right?

Still, if I reboot with the persistent image, I find that Firefox has no Flash installed. That is the problem.

---

### Post by C.S.Cameron on 2010-01-24
BLANDCorporatio:

Do your other changes stay persistent? ie if you change your desktop background does it hold?

garvinrick4:

If you make a ext3 partition and label it casper-rw it can be any size and still work.

---

### Post by BLANDCorporatio on 2010-01-24
Aww man I didn't even check that.

... and now that I did, negative. Background changes don't stick.

Still, the USB stick has one partition, it's called casper-rw and formatted ext2.

Before booting the Live session, I press F6 and add persistent to the Boot options string. If I move with the up/down arrows through the boot menu though, the change to the Boot option string doesn't stick.

So I just add in persistent and press enter, but it's not working.

---

### Post by C.S.Cameron on 2010-01-24
I have to admit that I had been speaking from memory.
a casper-rw partition on a second flash drive works fine for me when booting from a non persistent flash drive but is no longer working for me when booting from the CD.
I have also tried an ext3 partition named casper-cow, this worked pre Gutsy but is not working for me now.
I will keep playing with this a while and let you know if I make any progress.

---

### Post by BLANDCorporatio on 2010-01-24
Thanks a lot for the time!

---

### Post by C.S.Cameron on 2010-01-24
The following thread may or may not be of help, Ubuntu version was 8.10:
[http://ubuntuforums.org/showthread.php?t=953008](http://ubuntuforums.org/showthread.php?t=953008)

---

### Post by BLANDCorporatio on 2010-01-25
It's getting better ...

I repartitioned the persistent image flash stick, this time in two partitions: casper-rw and home-rw. Afterwards, a 

sudo su 

followed by 

chown ubuntu /dev/sdb1 

(the casper-rw partition) then the same for the home-rw partition.

Persistence now works: not only does the Desktop stay the same between restarts, but Firefox remembers the tabs from last time as well.

However, the Flash issue is still there: the fact that the plugin was installed on a previous session is forgotten, so I need to reinstall it.

---

### Post by C.S.Cameron on 2010-01-25
Hmmm, wonder why?
The flash plug-in sticks when it is installed to a "persistent" thumbdrive.

---

### Post by BLANDCorporatio on 2010-01-26
I see, then how do I go around doing that?

Now I just go to the Adobe page, pick "APT install for Ubuntu 9.04" and let that do its magic. As long as the computer is not restarted, it works.

---

### Post by C.S.Cameron on 2010-01-26
Here is a link to a recent thread where we discuss the pros and cons of the various methods of installing Ubuntu to a bootable thumbdrive.

---

### Post by BLANDCorporatio on 2010-01-27
> **C.S.Cameron said:**
> Here is a link to a recent thread where we discuss the pros and cons of the various methods of installing Ubuntu to a bootable thumbdrive.

Here ... where? :)

---

### Post by C.S.Cameron on 2010-01-27
Oops.
[http://ubuntuforums.org/showthread.php?t=1389585&page=2](http://ubuntuforums.org/showthread.php?t=1389585&page=2)

---

### Post by BLANDCorporatio on 2010-01-30
It works!

I followed the instructions for a LiveUSB, and also needed to boot with the following options

[I][SIZE=2]noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash --
[/SIZE][/I]
(before, I was trying to boot from a LiveCD with the options

[I][SIZE=2]noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash persistent
[/SIZE][/I]
does the place where you put "persistent" matter?)

Thanks everyone!

---

### Post by alienkid10 on 2010-02-19
Hi I need to boot from a liveCD since none of my computers can boot from USB and my schools would need BIOS changes which I don't want to do. I use the following boot options in 9.10

*[SIZE=2]noprompt cdrom-detect/try-usb=true  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz  quiet splash -- persistent[/SIZE]*

And all that get's saved to the casper-rw file is a 12hb lost+found folder. Anything I can do?

---

### Post by RobCr on 2010-03-24
Give Puppy Linux a try, and be pleasantly surprised -
a) Runs totally in ram (and thus frees up the CD drive)
b) Very fast
c) IT KNOWS how to persist, without having to research your heart out
When you close your session, it prompts you to Persist your settings,  data, etc.

The other distro's should also try it, and learn the proper way to  provide persistence.

---

### Post by fsteve800 on 2011-07-28
You could download a deb package and save it if you do not mind installing it every time.

get the instructions here [http://fsteve800.blogspot.com/]("http://fsteve800.blogspot.com")
 How to view flash pages in Ubuntu LiveCD

---

