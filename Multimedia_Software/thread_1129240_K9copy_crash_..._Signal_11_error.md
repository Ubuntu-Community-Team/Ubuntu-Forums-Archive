---
title: "K9copy crash ... Signal 11 error"
date: 2009-04-18
forum: Multimedia Software
---

### Post by dragoonaz on 2009-04-18
So, I'm new to the forum and this is my first post.  

I've recently switched to Ubuntu and am loving it, so far, but I am having one major problem:

After using K9copy successfully for a while, I've recently been getting the following error msg when trying to backup my DVDs:


"A Fatal Error Occurred
The application k9copy (k9copy) crashed and caused the signal 11 (SIGSEGV)."

I've searched the forum but haven't found a solution.  At first, the error msg was infrequent but now it happens with every DVD that I try to back up.  I have two optical drives and neither works.  

Some of the things I've tried:

I've re-installed K9copy.
I've redirected the temp output to my home folder, which is a separate partition, since it is a much larger partition than the one on which Ubuntu is installed.
I've set the temp output to clear when I close K9copy also to make sure it's not a space issue.
I've tried using DVD::Rip but can't seem to get it to work either.

I realize I could use Wine to run DVDshrink, as I did in XP, but I would prefer to use a Linux native program to do my backups, and K9copy seems to be the most user-friendly interface. 

Has anyone else experienced this error with K9copy?
Also, how do I verify how much available space is on the root partition? (remember I'm a Linux newb)

I don't think it's a space issue but it could be.

Thanks for any assistance.

---

### Post by xc3RnbFO8P on 2009-04-18
Install this if you haven't:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
and this:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by dragoonaz on 2009-04-19
Thanks for the informative links.

I will definitely install the packages/libraries and see if that solves my K9copy problem.  In the meantime, I decided to install Wine, after all, and am up and running with DVD Decryptor and Shrink.  Aside from editing the Fake Windows Registry (didn't think I'd be doing that anymore ;-), it was fairly easy to set up.

Thanks again.

---

### Post by ferral-cat on 2009-04-30
I was using Ubuntu 8.10 Intrepid and one day k9copy just stopped working.  I remember that this happened soon after I had installed a very large system update.

Basically I had my PC in storage for about 2 months and I had k9copy working 100% on intrepid until one day it just started doing this thing where around 80% into the dvd copy process it would suddenly crash with SIG 11 error.  Pain in the ***.  

Then it occured to me that after running a large update that included an update of the kernel from 2.6.27-7-generic to the latest kernel which is called 2.6.27-11-generic that THE NEW KERNEL MAY BE TO BLAME.

My solution to the K9Copy problem is to downgrade to kernel 2.6.27-7-generic.  Thats what I did and it solved the problem immediately.  You're not actually "downgrading" the kernel as much as adding an option so that you can boot into the 2.6.27-7-generic kernel or the new kernel 2.6.27-11-generic.  Whichever you choose.

Its not as hard as it sounds.  In fact I have mine set up in the GRUB menu that gives me the option of booting into 2.6.27-7-generic or instead I could boot into the newest kernel.  Many peoples machines are already set up that way.  

So I recommend you give this "possible fix" a try since it will not harm your system in anyway as you will simply be adding a boot entry into the file /boot/grub/menu.lst and this procedure is easily reversible.  

Now you may already have 2.6.27-7-generic as an option in grub.  If you do then simply choose that one when you first power on your computer.  Then try copying a DVD with K9copy.  

If it works then great!  And if not then dont bother following the rest of these instructions.  But if you do not have an entry in grub for 2.6.27-7-generic then you will have to perform the following steps:


Lets begin by launching TERMINAL and then type this:

```
uname -r
```

here is my output:

```
daka@daRk-deSkTop:~$ uname -r
2.6.27-7-generic

```

Okay now make a note of the output.  Thats the present kernel you are booted into right now.  Most likely YOU are using  kernel 2.6.27-11-generic which is the newest kernel and I suspect its the main culprit in screwing up k9copy.  

Now copy and paste the exact kernel number into your favorite text editor.  We will need this later.  

Now type the following:

```
sudo apt-get install linux-image-2.6.27-7-generic linux-headers-2.6.27-7-generic
``` 

Here is my output:
 

```
daka@daRk-deSkTop:~$ sudo apt-get install linux-image-2.6.27-7-generic linux-headers-2.6.27-7-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.27-7-generic is already the newest version.
linux-headers-2.6.27-7-generic is already the newest version.
linux-headers-2.6.27-7-generic set to manually installed.
```

As you can see in my case I already had the kernel installed on my hard drive.  If you dont have it then say "Yes" that you want to install it.  

Now reboot the computer.  In some cases the entry will be added to Grub automatically.  If that is not the case for you (and it was not for me) then you will have to edit menu.lst and add an entry for 2.6.27-7-generic

Lets do that:

```
sudo gedit /boot/grub/menu.lst

```

I recommend you hit SAVE and save it as Old_menu.lst because if you screw something up then you can revert to this backup copy of menu.lst

Now copy and paste the entry for kernel 2.6.27-11-generic which should look similar to this: 

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		88505efa-f3c3-4980-b0fd-816c4976fbd0
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=88505efa-f3c3-4980-b0fd-816c4976fbd0 ro all_generic_ide floppy=off  
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

Now yours may look a little different then mine but just copy and paste what you have and add a duplicate entry of kernel 2.6.27-11-generic.  

Then change the number 11 to 7.  Do you understand my instructions?  Here is an example of my personal menu.lst for you to see how mine looks:```


## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		88505efa-f3c3-4980-b0fd-816c4976fbd0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=88505efa-f3c3-4980-b0fd-816c4976fbd0 ro all_generic_ide floppy=off  
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		88505efa-f3c3-4980-b0fd-816c4976fbd0
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=88505efa-f3c3-4980-b0fd-816c4976fbd0 ro all_generic_ide floppy=off  
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		88505efa-f3c3-4980-b0fd-816c4976fbd0
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=88505efa-f3c3-4980-b0fd-816c4976fbd0 ro all_generic_ide floppy=off  single
initrd		/boot/initrd.img-2.6.27-11-generic


title		Ubuntu 8.10, memtest86+
uuid		88505efa-f3c3-4980-b0fd-816c4976fbd0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

Now save the file and close gedit.  So you have just now added an entry in GRUB for kernel 2.6.27-7-generic

Now reboot the computer and when GRUB comes up you must select 2.6.27-7-generic from the list and boot into that one.  

Then launch k9copy and let me know if it fixes your problem because this worked for me.  

I know this sounds dumb but make sure you have at least 3 different DVDs that you are using to test out k9copy to make sure the problem is not with the DVD

For example when I insert a movie that had been burned onto a DVD-RW disc that would hang k9copy and force me to x-kill it.

---

### Post by ivo_ac on 2009-08-22
Hi,

I have exactly the same problem but I fixed it by just starting "k9copy assistant" instead of k9copy.

I dont know why the backup assistant works and the main program causes a fatal error but I'm just glad it works now.

If someone knows how to solve this issue for the main k9copy program i would appreciate the help.

Regards, Ivo Ac.

---

### Post by puller on 2009-10-03
I had the same problem as dragoonaz.
The solution was pretty easy, I just needed libdvdcss2, here's how to install it in jaunty ( from here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) )

Istall libdvdread4:

```
sudo apt-get install libdvdread4
```

install libdvdcss2:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Greetings.

---

### Post by dapaintballer331 on 2010-06-30
> **puller said:**
> I had the same problem as dragoonaz.
The solution was pretty easy, I just needed libdvdcss2, here's how to install it in jaunty ( from here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) )

Istall libdvdread4:

```
sudo apt-get install libdvdread4
```

install libdvdcss2:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Greetings.

Worked for me, thanks so much!

---

### Post by fmmarzoa on 2010-11-03
Also works for me! thx. a million :-)

---

