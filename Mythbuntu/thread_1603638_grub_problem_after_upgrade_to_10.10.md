---
title: "grub problem after upgrade to 10.10"
date: 2010-10-23
forum: Mythbuntu
---

### Post by ZedThou on 2010-10-23
A similar thing happened earlier this year when I upgraded from 9.10 to 10.04. I was able to fix that, but now the upgrade from 10.04 to 10.10 has left me with a problem I cannot seem to solve.

I did a network upgrade from 10.04 to 10.10. Upon rebooting after the upgrade I get an error - a message that says something like "the symbol 'grub_xputs' not found" and then the grub prompt. I don't really understand how grub works, so after some searching around, at the grub prompt I try both 'root (hd0,4); setup (hd0)' and 'root (hd0,4); setup (hd0,4)' (the linux root partition is /dev/sda5), but neither of these get me back to booting into mythbuntu. Instead they have the system continuing to boot directly into a grub prompt (albeit without the previous "symbol not found" error).  I've also tried rescue discs, mounting the root partition along with proc, sys and, dev filesystems under it, then doing a chroot into it and running 'update-grub'. That's what fixed the problem earlier this year, but now it causes the system to just boot into windows, which is on /dev/sda1.

I've also tried booting from a mythbuntu 10.10 install disc, but doing this I couldn't figure out how to bypass the installation procedure and go straight to the boot loader install step. So now I'm kind of stuck.

My mythbuntu system is still there on the hard drive, I just cannot figure out how to boot into it! Hopefully this post wasn't too scatter-brained and someone might know what I should do to sort this out.

Thanks!

---

### Post by garvinrick4 on 2010-10-23
Pop in Your install disk and choose Try Ubuntu and when it boots open a terminal and:
If you just need to put grub2 back into mbr and your linux is sda5 then this is the solution:
Given your linux install is sda5:
```
sudo mkdir /media/root
``````
sudo mount /dev/sda5 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
```Boot into your linux install:
```
sudo update-grub
```Now your grub2 will be in sda (mbr) looking for grub2 in sda5:

---

### Post by garvinrick4 on 2010-10-23
If for any reason there are other complications with booting you have to run this script to
your DESKTOP and then put in supplied code below and the copy and paste the text file it produces to this thread.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by ZedThou on 2010-10-23
I've just had another look at the root partition and it seems that my attempt to fix the boot problem using an install disc has wiped just about everything out from the root partition. I'm positive that when I went through the partition stage (I did it manually) I told it not to format any of them. But still it seems that /usr, /etc and /var have been wiped out. Without /var, all database information is gone, correct?

So I suppose, nevermind the grub problem :P I have to salvage something from this installation but I'm not really sure how I possibly can. I still have a year's worth of recordings but no database.

---

### Post by garvinrick4 on 2010-10-23
Put in live cd and see if you can mount partition and open her up:
```
sudo mkdir /media/root
```
```
sudo mount /dev/sda5 /media/root
```

See if you can salvage your home directory?

---

