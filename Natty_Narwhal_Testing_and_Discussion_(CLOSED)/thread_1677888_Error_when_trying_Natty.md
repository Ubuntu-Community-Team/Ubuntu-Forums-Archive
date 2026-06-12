---
title: "Error when trying Natty"
date: 2011-01-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by carfield on 2011-01-29
I try to run Natty , but after I update the packages and restart. GRUB doesn't boot up and say

error: symbol not found: 'grub_env_export'

Then display "grub rescue>". What can I do to rescue it?

---

### Post by philinux on 2011-01-29
Moved to Natty testing forum.

Please read the forum stickies. Cheers.

---

### Post by carfield on 2011-01-31
I try to boot with recover CD and reinstall the system. However after I start with recovery CD, I cannot remount my disk, will anyone know how can I remount the hard disk and get back the data?

---

### Post by carfield on 2011-01-31
I just found that when I boot with recovery CD, there is /dev/dm-0 and /dev/dm-1, will those actually taking control of my /dev/sda and /dev/sdb so that I cannot mount it?

And right, sorry having provide enough information, I have 2 HDD and my motherboard support software RAID ( but I haven't use it ) 

Will that cause problem??

---

### Post by ronparent on 2011-01-31
Your raid may be turned off but it was on at one time and wrote raid meta data to the drives in question. You have to erase the meta data so that the drives aren't discovered as 'raid' drives. To erase the metadata open a terminal and write:
```
sudo dmraid -E /dev/sda
```
and sdb etc.

That should eliminate the synbolic links /dev/dm-0, etc. when booted to a live cd.

---

### Post by carfield on 2011-02-01
Thanks a lot for the pointer, but like to amend some detail, 

sudo dmraid -E /dev/sda

actually cannot do the work, what can fix the problem is

sudo dmraid -a no
sudo dmraid -x

Anyway, it is great that now I can mount /dev/sda1 and /dev/sdb1 again excellent :-)

Like to ask one more thing, From 10.10 installation CD, it is saying that reinstall will delete /usr , /lib blah blah ( look like only /home will save for you ). I just wonder can I just replace grub with older and working version so that I don't need to delete all the package and setup again?

---

### Post by carfield on 2011-02-02
> **carfield said:**
> 
Like to ask one more thing, From 10.10 installation CD, it is saying that reinstall will delete /usr , /lib blah blah ( look like only /home will save for you ). I just wonder can I just replace grub with older and working version so that I don't need to delete all the package and setup again?

Any solution for this? I found that "Boot from first hard disk" is missing from ubuntu 10.10 CD. Any chance I can recover the grub at hard disk so that I can boot?

---

### Post by cariboo on 2011-02-03
I got the same error this past weekend all I did was boot from the live CD and chrooted my Natty / using the following commands:

[LIST=1]
[*]sudo mount /dev/sdXx /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

Once at the prompt I reinstall grub:

```
grub-install /dev/sda
```

and then updated grub

```
update-grub
```

then Ctrl-D twice to exit, and reboot.

---

### Post by carfield on 2011-02-03
That way cool! But too bad I already install my system to 10.10. But definitely will try this next time!

---

### Post by latitude6500 on 2011-03-10
cariboo907 THANKS !!! WORKS PERFECTLY ! :-)

---

### Post by cmkoch on 2011-03-14
cariboo907 THANKS! 
This trick should work with any current live-cd.
For me it was a GRML-mini.

---

### Post by xandey on 2011-03-23
cariboo907

I tried your solution involving chroot and reinstall of grub. I wasn't able to make it work. I have a macbook pro 4,1 which uses refit.

In order to install 10.10 I need to change the location of grub to /dev/sda4 to get it to work. 

For 11.04 alpha3 I set it to install to the same location as 10.10 and got this grub error on bootup.

I tried your reinstall of grub solution, and got no change:
tried installing grub to both /dev/sda and /dev/sda4, from both 10.10 and 11.04 live install disks.
I had to use the --force option for grub-install for both locations because of "blacklist" or something like that.

I have since gone back to 10.10 which works fine for installation. I'd be happy to help out with testing, but I need this machine working for now.

cheers,
Sandy

---

### Post by Ice.Singapore on 2011-04-18
Today I match the same error:
```

Grub "error: symbol not found: 'grub_env_export 
grub rescue>

```

I solved this problem with follow method:
Firstly you must try your best to get into grub command line(In window you can use grub4dos get in grub, you can get the newest version for grub4dos from:[http://nufans.net/grub4dos/ ]("http://nufans.net/grub4dos/") );
Then now assum that you already get into the grub command line, Use following can solved all:
  ```
  
        grub>  find --set-root /boot/grub/core.img
        grub>  kernel /boot/grub/core.img
        grub>   boot
 
```

Finally, Dont forget to re-install  grub(change /dev/sda to where you install you grub into. ):
  ```
  
  grub-install /dev/sda
  
```

---

