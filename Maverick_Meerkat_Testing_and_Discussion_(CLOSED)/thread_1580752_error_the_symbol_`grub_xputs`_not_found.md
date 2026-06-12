---
title: "error: the symbol `grub_xputs` not found"
date: 2010-09-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-09-23
I couldn't resist any longer, and had a spare hour or two, so I used the upgrade function to upgrade to Maverick Meerkat. All seemed to go well and at the end it requested a reboot, so I clicked on it.
Now all I get is the above message followed by grub rescue>
Could somebody shed some light on this for me please? Does it mean that grub2 can't find its config files? Even though they haven't moved.
Thanks and apologies for not leaving my well-working system alone

---

### Post by drs305 on 2010-09-23
If you have a LiveCD, boot to the Desktop and run the following commands. It should reinstall Grub2 and if it didn't correctly identify the drive/partition during install this should fix it. Substitute the drive/partition in the first command (such as sda5) and the *drive only* in the second (such as sda):
```
sudo mount /dev/sd**XY** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**X**
```

---

### Post by Quackers on 2010-09-23
Hello Boss. I thought it was a grub problem. That's why I posted in General. oops. 
Yes I have a live cd.
In the first command would that be the root partition?

---

### Post by drs305 on 2010-09-23
> **Quackers said:**
> Hello Boss. I thought it was a grub problem. That's why I posted in General. oops. 
Yes I have a live cd.
In the first command would that be the root partition?

Yes, the one you installed Ubuntu on. On a normal Ubuntu-only install, it would be sda1. On a normal Windows dual boot, it's often sda5. If you aren't sure, from the Desktop you can type "sudo blkid" and "sudo fdisk -l" to help you identify the correct partition.

From the Grub rescue prompt (without the CD inserted) you may be able to type "ls" and get all the partitions found by Grub2. You also may then be able to type "ls (hdX,Y)/boot" to see if it finds the kernel and initrd image. Even if you find it, I'd still boot the CD and install via that method, as it will probably be quicker.

Re: Maverick.  We just like to keep all testing questions in the testing forum so the information doesn't get confused with procedures that may not be the same with the normal releases. Plus only those testing may be aware of procedures which may be unique to the testing release.

**[COLOR="DarkRed"]Added:[/COLOR]** It's possible that G2 is installed in the correct location but some of the files are missing. If that is the case, the above may not work. What will work if that is the problem is chrooting into the real partition and purging/installing G2. Here are the instructions for doing that (Post #5):
[http://ubuntuforums.org/showpost.php?p=9836539&postcount=5]("http://ubuntuforums.org/showpost.php?p=9836539&postcount=5")

---

### Post by Quackers on 2010-09-23
Thanks for that, I'm on it.
I suspect it may have something to do with having 2 drives in the laptop. I'll install grub2 again (as per your instructions) on both drives as that seems to be the only way it will boot.

---

### Post by Quackers on 2010-09-23
I re-installed grub and when booting I now get 2 entries flashing up for about half a second. They both say file not found. Then the screen stays black. There is no hard drive activity after that.

---

### Post by drs305 on 2010-09-23
Are you able to get any results from the grub prompt with "ls"?

If you haven't tried the second method (Added), try that. If not successful, boot the LiveCD again and run *meierfra's* boot info script and post the results.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by Quackers on 2010-09-23
Ok, thanks. Will try that.

---

### Post by Quackers on 2010-09-23
You Sir, are a Grub2 guru! Success! And no nvidia graphics problems either! Oh happy day! Where do I send the cheque? A thousand thank yous.

---

### Post by drs305 on 2010-09-23
I'm easy to please - just mark the thread "SOLVED" via the Thread Tools link near the top right of the first post.

Happy Ubuntu-ing !  :P

---

### Post by Quackers on 2010-09-23
It's a deal! Cheap too :-) Until the next time I do something stupid :-)
Thanks again.

---

### Post by ranch hand on 2010-09-23
> **Quackers said:**
> You Sir, are a Grub2 guru! Success! And no nvidia graphics problems either! Oh happy day! Where do I send the cheque? A thousand thank yous.
He has been for quite some time now.

---

### Post by Quackers on 2010-09-23
From what I've read you're not exactly a n0ob yourself!

---

### Post by jcannon844 on 2010-10-05
I, too, recently tried to upgrade to 10.10 and got the same error message. I foll[SIZE=1]owed drs305's suggestion "sudo grub-install..." The live CD ran and said "install completed. No errors." Upon rebooting, I now see a quick flash that looks like 'error[/SIZE]"  then the screen goes blank with the cursor flashing violently in the upper left hand corner of the screen. Nothing else happens. I will re-install 10.04 BUT I committed the gravest sin by not backing up my Desktop and other folders, i.e., music. Could someone tell me how to access my old 10.04 files [music, docs, etc] to save them if at all possible? Thanks in advance.

---

### Post by drs305 on 2010-10-05
> **jcannon844 said:**
> I, too, recently tried to upgrade to 10.10 and got the same error message. I foll[SIZE=1]owed drs305's suggestion "sudo grub-install..." The live CD ran and said "install completed. No errors." Upon rebooting, I now see a quick flash that looks like 'error[/SIZE]"  then the screen goes blank with the cursor flashing violently in the upper left hand corner of the screen. Nothing else happens. I will re-install 10.04 BUT I committed the gravest sin by not backing up my Desktop and other folders, i.e., music. Could someone tell me how to access my old 10.04 files [music, docs, etc] to save them if at all possible? Thanks in advance.

Don't install anything to the partition with your data/music files. You can boot into the LiveCD, open a terminal, and run the following (substitute values of **XY** for your Ubuntu partition:

```
sudo mkdir /mnt/temp
sudo mount /dev/sd**XY** /mnt/temp
gksudo nautilus /mnt/temp
```

Find you files and save them to another location.

---

