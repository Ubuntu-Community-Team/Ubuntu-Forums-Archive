---
title: "Natty beta 64 bit - LiveCD works great, install fails to install grub"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by TBABill on 2011-04-03
The beta works great in the live session but fails on every install, whether installed without going into the live session or from the live session. 3 downloads, 3 different disks (1 was a DVD just as a trial). Exact same failure every time. I get the error notice during install, but the next prompt is to restart. So I restart and get to a grub rescue prompt.

Ideas? Not workarounds, but a way to make this work the way it is intended to work on a fresh install. I have installed countless distros including Ubuntu many times and never had this type of failure. Since it's beta, perhaps that's a partial reason.

---

### Post by TBABill on 2011-04-03
Disregard. I gave up on 64 bit, downloaded 32 bit and all is well.

---

### Post by VMC on 2011-04-03
> **TBABill said:**
> ... Exact same failure every time. I get the error notice during install, ...

Even though you have moved on, do you remember what the error message said? 

I don't think I have ever used side by side or any other install. I guess I should on a spare HD, but I always have my partitions setup and use the manual method. Also I now only use usb hard drive installs. Much faster. I've been using amd64 installs for a year now.

---

### Post by TBABill on 2011-04-03
I've been exclusively using 64 bit for a long time as well. The error said something about either broken packages or older packages. Odd since it was the beta and it hasn't been out very long. The MD5SUM was fine and I burned to both CD and DVD, plus downloaded multiple times with multiple burns. I've never had an issue in the past getting a decent CD or DVD from a download. I've had errors, but never after running beautifully in a live session and then just selecting install.

The error was right at the end where you'd normally see Grub2 being installed. It just didn't happen, as if it skipped the step entirely. And it still said that my system needed to restart because the install finished. That's the worst part. It looked as if it worked fine other than the single error popup followed by "system install complete" or something like that. I clicked ok to restart and found no grub. 

The burner is fine as well. The 32 bit burned fine for me, installed and I'm working from it now. I prefer 64, but this is a beta and I'll probably reinstall later if I decide I like Natty enough to stick with it. Right now it's relatively non-intuitive. Just simple things like disabling the lock on the screensaver will frustrate new users who may not find it as easily as an experienced user.

I'm undecided right now. It's a "neat toy" but for serious business it still feels like it will be more in the way than standard Gnome. I guess it looks ok, but its practicality hasn't shown itself yet. Still toying though.

---

### Post by cariboo on 2011-04-03
I had the same problem, last week during iso testing, I just booted from the Live CD, chrooted /dev/sda1 and manually installed and setup grub, that was on the 32-bit version.

---

### Post by Armando Penblade on 2011-04-03
I have this same issue. Next time I re-burn and retry, I'll write down the exact file it's unable to install due to the error you mentioned. I'll post back here when that's done; hopefully someone much brighter than me can help figure it out :)

---

### Post by beameup on 2011-04-04
My 64 bit laptop is my "production machine" so i won't beta test on it, but I did the LiveCD and it worked great. Hope this one gets sorted out before the 28th.

---

### Post by cariboo on 2011-04-04
> **beameup said:**
> My 64 bit laptop is my "production machine" so i won't beta test on it, but I did the LiveCD and it worked great. Hope this one gets sorted out before the 28th.

You must be new here. :) there is going to be quite a lot of bug fixing going on in the next two weeks.

---

### Post by beameup on 2011-04-04
LOL, yeaaa, only been here since 2004 :P

---

### Post by TBABill on 2011-04-04
Tonight the problem worsens. I decided I just can't learn to like Unity but wanted to install a variant. I downloaded 64 bit Xubuntu....EXACT same problem. Grub won't install and I end up with a grub prompt (grub rescue). I've verified MD5SUM and all the other items.....burn slow, verify burner, different DVD and CD....it's the OS. The beta iso in 64 bit is broken at least on two different computers and burners with totally different specs. I tried both Ubuntu 64 and Xubuntu 64 (11.04 Natty beta of both) and they just fail to install grub and error right at the end of the install. 

I finally threw in the towel on Natty after at least 10 different downloads, even more numbers of burned media, and countless install hours. Downloaded and burned LMDE....working great again. We'll see how it goes after final release perhaps.

---

### Post by Armando Penblade on 2011-04-10
Still getting this issue. Attached is a screenshot of where the error occurs; the installation of Ubuntu will not continue from this point forward.

[IMG]http://i.imgur.com/QGFWsl.jpg[/IMG]

Full image is [http://i.imgur.com/QGFWs.png](http://i.imgur.com/QGFWs.png)

---

### Post by fdrake on 2011-04-10
Try to install and use the 32bit version. For the developers takes more time and energy to resolve problems on 64bit machines. I am sure there is a solution but since you are installing a beta version it will take a wile before one of the developers takes a look at it.

---

### Post by garvinrick4 on 2011-04-10
> **TBABill said:**
> Tonight the problem worsens. I decided I just can't learn to like Unity but wanted to install a variant. I downloaded 64 bit Xubuntu....EXACT same problem. Grub won't install and I end up with a grub prompt (grub rescue). I've verified MD5SUM and all the other items.....burn slow, verify burner, different DVD and CD....it's the OS. The beta iso in 64 bit is broken at least on two different computers and burners with totally different specs. I tried both Ubuntu 64 and Xubuntu 64 (11.04 Natty beta of both) and they just fail to install grub and error right at the end of the install. 

I finally threw in the towel on Natty after at least 10 different downloads, even more numbers of burned media, and countless install hours. Downloaded and burned LMDE....working great again. We'll see how it goes after final release perhaps. After installing and get error.
Boot into live CD or another install and mount in /mnt and mount and bind /dev /dev/pts /proc and /sys
chroot and well such as below: using sda5 use your own with internet connection: 
  	 	 	 	 	```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 
```
```
dpkg --configure -a
```
```
apt-get upgrade && apt-get dist-upgrade
```
```
grub-install /dev/sda
```
```
update-grub
```
```
exit
```
   	 	 	 	 	```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 


```
```
sudo shutdown -r now
```

---

### Post by mziel on 2011-04-11
Installing Natty from Install mode (not Live mode) works for me.
Installing it via live session fails.

---

### Post by zobbo on 2011-04-11
Yes, same experience as mziel. If I installed having booted into the live desktop it failed. Choosing to install directly worked. 

I now wonder if this is because it was the live updates that the live cd was pulling down which caused the problem. When installing directly I just did an upgrade after the normal install finished.

Ian

---

### Post by zobbo on 2011-04-11
I have now redone the install, starting from the live cd but not connecting to the network when doing it. Install completed fine.

---

### Post by TBABill on 2011-04-14
Wow. Just a few days later and beta 2 has fixed all my complaints. Adding an item to the launcher is easier, opening more than one instance is a right click away on the launcher, removing an item is simple, the launcher isn't auto hiding when an app is opened, and the 64 bit now installs beautifully. That's a ton of fixes in a very short period of time.

I have it installed, running great, temps well under what they were in 10.04 and 3D is working well on my Intel Core i3's GPU. 

I can no longer complain. I still hate the search function, but the fix was to add those items to the launcher that I use regularly so I only have to use the applications menu rarely. No cluster of icons on the desktop or panel and functionality is much improved. I'll continue testing things, but so far the beta2 release has cured most of its ills that I had identified previously.

---

