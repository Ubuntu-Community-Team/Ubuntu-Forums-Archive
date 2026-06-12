---
title: "Installed now win7 partition is messed up"
date: 2011-01-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-01-28
Okay so i installed natty to a separate partition to my stable ubuntu and win7 installs.

I can boot into Ubuntu natty and maverick but it seems the ntfs partition has just dissapeared?

Grub doesn't detect it, it won't show up as a mountable partition either.

It is definitely there as the Disk Utility can see it as an NTFS partition.

Any ideas?

---

### Post by cariboo on 2011-01-28
Have you run update-grub to see if the windows partition shows up?

---

### Post by david stevenson on 2011-01-29
I have same story with win XP.
Did not really want the XP, but I guess I will now have to spend time fixing it, just in case I need it one day.
Not happy.

---

### Post by jerrylamos on 2011-01-29
> **david stevenson said:**
> I have same story with win XP.
Did not really want the XP, but I guess I will now have to spend time fixing it, just in case I need it one day.
Not happy.
David, fear of Alpha screwing up my hard drive with Windows 7 starter is why Narwhal is installed on a USB hard drive.  I had a left over laptop 38 GB drive so I got an inexpensive case to plug it into a USB port. Nice and responsive.

The USB hard drive has Maverick, Natty, and space left over to try Alpha 2.  The boot sequence is to try the USB hard drive first and if it is plugged in, gets Grub2.  If not plugged in, Windows 7 starter fires up.

Maybe at RC time if Natty is really stable I'll try dual boot on the 250 GB hard drive.  Shame to waste all that space just for Windows 7.

---

### Post by siegi on 2011-01-30
I've had this too. (2 times)
Just use the windows 7 cd to repair your installation. (5 minutes work, you don't need to reinstall)

I think there's something wrong with natty's version of grub.
I have a triple boot (maverick, natty, windows). And I'm using maverick's grub, and removed grub in natty.

---

### Post by rajeev1204 on 2011-01-30
> **ELD said:**
> Okay so i installed natty to a separate partition to my stable ubuntu and win7 installs.

I can boot into Ubuntu natty and maverick but it seems the ntfs partition has just dissapeared?

Grub doesn't detect it, it won't show up as a mountable partition either.

It is definitely there as the Disk Utility can see it as an NTFS partition.

Any ideas?


os-prober can come in handy in such situations.Command line.

---

### Post by ELD on 2011-01-30
As siegi pointed out i could use the win7 cd to repair it, worked a treat and then grub update finds it again.

Looks like the natty installer is a bit buggy.

---

### Post by cariboo on 2011-01-30
> **ELD said:**
> As siegi pointed out i could use the win7 cd to repair it, worked a treat and then grub update finds it again.

Looks like the natty installer is a bit buggy.

It's grub2 that is the problem, not the installer, It seems that if grub detects a dirty shutdown, it won't add a partition to the boot menu.

---

### Post by rburkartjo on 2011-01-31
i thought something like this would happen that is why i put win7 on a second internal hard drive. any dirty shutdown has not affected my grub setup.

---

### Post by rburkartjo on 2011-01-31
i stand corrected last series of updates which included x updates messed me up. had to do two hard restarts and then update grub from the recovery mode. then again update grub when in 11.04. all okay now

---

### Post by ELD on 2011-02-06
> **cariboo907 said:**
> It's grub2 that is the problem, not the installer, It seems that if grub detects a dirty shutdown, it won't add a partition to the boot menu.

I'm pretty sure it's a bug as it's happened again.

I shut down Win7 as normal, booted into ubuntu 10.10, burnt a natty cd, booted into the installed and installed and grub failed to install so i selected continue without bootloader, now windows 7 again doesn't even show up as a mountable drive or in my grub list.

At least this time i know how to fix.

---

### Post by rburkartjo on 2011-02-06
eld isnt testing fun. at least you know how to fix now

---

### Post by jerrylamos on 2011-02-06
> **ELD said:**
> I'm pretty sure it's a bug as it's happened again.

I shut down Win7 as normal, booted into ubuntu 10.10, burnt a natty cd, booted into the installed and installed and grub failed to install so i selected continue without bootloader, now windows 7 again doesn't even show up as a mountable drive or in my grub list.

At least this time i know how to fix.

Well I've got multiple partitions including Win 7, Natty. Maverick.

I head Natty Grub 2 was flaky so I fired up Maverick to do the 
sudo update=greb
sudo grub-install /dev/sda

Worked fine.

Jerry

---

### Post by nm_geo on 2011-02-06
I always install the Grub2 to the partition where the testing installation is done.  Then use my stable Lucid 10.04 to be the Grub2 pointer. Requires more (update-grub) commands in Lucid,  but I have had zero problems with the other distros or testing installations. Quackers knows what I am talking about :lolflag:

---

### Post by billbear on 2011-03-10
In short, to solve [this problem]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html"), recent update of grub introduces [this new bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/730225") (please add your comments) which can corrupt the first ntfs partition.

---

### Post by maheshasolkar on 2011-03-10
> **cariboo907 said:**
> Have you run update-grub to see if the windows partition shows up?

I would definitely try this. More than a few occasions I have seen that Windows does not appear in Grub2 choices. But running update-grub fixes it most of the time.

---

