---
title: "&quot;No init found.&quot;"
date: 2010-07-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Sockerdrickan on 2010-07-17
I have been trying daily builds for x86_64 since the first one was built for 10.10. I always get an ash shell and "No init found."

I am using unetbootin 471 to create my live USB memory...

What does "No init found" mean and what can I do to fix it?

---

### Post by andrek on 2010-07-17
Same here, using alpha2 x86_64 image booting from an usb drive.

---

### Post by cybersnoop on 2010-07-17
Have you tried using the USB Creator on the ISO instead of UNetbootin?

UNetbootin has a sort of universal way of writing the bootloader to the USB-disk that does not boot the Ubuntu desktop CD kernel correctly in my experience.

---

### Post by jppr on 2010-07-17
> **cybersnoop said:**
> Have you tried using the USB Creator on the ISO instead of UNetbootin?

UNetbootin has a sort of universal way of writing the bootloader to the USB-disk that does not boot the Ubuntu desktop CD kernel correctly in my experience.

Same here, why using unetbootin when doing usb installation... ?
This morning I did clean live-cd installation and I using usb creator. I haven´t any problem and system run fine.

Edit. I always do a clean installation of usb sticks and I always do usb-stick usb Creator...

---

### Post by Sockerdrickan on 2010-07-18
Same problem today. Didn't work with Ubuntu 10.04 USB start disc creator either.

Are you guys running Nvidia video cards? Might be Nouveau (holy crap I spelt it right the first time :guitar:)

---

### Post by VMC on 2010-07-18
> **Sockerdrickan said:**
> I have been trying daily builds for x86_64 since the first one was built for 10.10. I always get an ash shell and "No init found."

I am using unetbootin 471 to create my live USB memory...

What does "No init found" mean and what can I do to fix it?

When do you get the error message? Do you get the menu for selecting "Try Ubuntu without installing"? If so, is that when you get the error?

---

### Post by Sockerdrickan on 2010-07-19
I don't get the menu. It's pre-everything. Then again unetbootin might strip that settings menu at all, I'm not sure.

---

### Post by buzucan on 2010-09-05
same problem here :(

---

### Post by jhellg on 2010-09-06
Also have this issue. Have tried several alpha dailies and now the beta.

---

### Post by federa on 2010-09-07
hi guyz..
same problem here. i can see the menu but every entry give me a "no init found"...or messages similar to that one!
although the "usb-creator-gtk" (or whaddahell its name is) does not work...i can't choose the iso image i want.

---

### Post by VMC on 2010-09-07
I have problems using Lucid usb creator, but Mavericks works fine. Since I have two Mavericks installed its easy. You guys may need to use DVD/CD to install Maverick.

---

### Post by ronacc on 2010-09-07
There seems to be a problem with maverick and usbstick installs in general . I made multiple tries to install the beta from 2 different usb sticks with the image created both by startup disk creator and unetbootin  , the attemps failed randomly anywhere from couldn't even boot the stick to almost completed the install then hung .An install from dvd burned from the same image suceeded first try . The usb sticks were prepared on a fully updated maverick install on another box and the sticks were formated to fat32 with gparted and also tried letting startup disk creator format the stick . There are also several threads about this .

---

### Post by cariboo on 2010-09-07
I must be doing something wrong then. I've created several usb drives, using the startup disk creator, and except for trying to install a 64-bit version on a 32-bit system, all have worked as expected, that was using a 1Gb and 2 4Gb thumb drives.

---

### Post by ronacc on 2010-09-07
this thing seems to affect some people/setups and not others , the 2 usb sticks I tried (several times each ) had both been used before to sucessfully install earlier releases .And different work arounds have worked for some people and not for others .

---

### Post by sagaci on 2010-09-07
I know it might be a stretch for some users but if you've got a windows box, try using the newer unetbootin-485 on launchpad. It's worked for me.

---

### Post by ranch hand on 2010-09-08
We have a window box here, has flowers in it.  Will that work?

---

### Post by diamondgar on 2010-09-08
I tried installing using latest version of netbootin in windows however no luck on my new Acer Aspire, havent had a chance to test on any other machines yet.

---

### Post by archithcr on 2010-09-08
Hi

I have as Asus EEE 1005HA, dual booting 10.04 and Win 7. i downloaded the ISOs for the desktop and Netbook edition from the Ubuntu website. I downloaded the latest build of Unetbootin for both windows and linux from sourceforge.

i wrote the ISOs onto seperate flash drives after formatting, but i am unable to boot into either of them. i am stuck at the Init = Bootarg message.

i read somewhere that there was reference to UI in syslinux.cfg in the older alpha builds, but when i opened the said file, there was no reference with UI in it. i repeated my efforts on both lucid and win7, to no avail.

for netbook users who don't have the luxury of a DVD drive, installing from USB Drives is of great importance and i hope Canonical will look into it.

from my experience, i never had problems with Hardy, Jaunty or Lucid live sticks, so hopefully this will be fixed.

---

### Post by Xilard on 2010-09-08
I have installed the 64 bit version of Ubuntu Server 10.04 today, from CD and experienced the same problem. I tried again, and again, but same problem. If someone knows the solution please help. 

[COLOR=Navy]I have the following partition layout:
**2x 500Gb** SCSI HDD-s in RAID 1 configuration
Partitions:
200MB - **/boot**
9 GB - **swap**
remaining - **root (/)**[/COLOR]

---

### Post by oregonbob on 2010-09-08
I downloaded the latest unetbootin and the 32bit Ubuntu 10.10 beta. Used unetbootin to install on a USB stick with no errors, but I cannot boot the USB stick. It gives same error:

No init found. Try passing init= bootarg.

It's Google time.

---

### Post by JoaoVr on 2010-09-11
Same error here too... Any solution?

---

### Post by KrazyPenguin on 2010-09-11
Yes!!!!

[http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html)

After you run the fsck /dev/sda1  (sda1 might be a different partition on your system)
you will be asked a lot of questions: fix (y)?

I responded YES to all of them.

And my system now boots.
Good luck!!!

---

### Post by epohs on 2010-09-11
Same problem here. Image created using unetbootin, installing NBR on a Dell Mini 9.

---

### Post by Sockerdrickan on 2010-09-17
With a unetbootin formated USB memory I can now choose the "try ubuntu" option and it works. "default" option still gives the "No init found."-error though.

---

### Post by hkphooey on 2010-09-20
> **Xilard said:**
> I have installed the 64 bit version of Ubuntu Server 10.04 today, from CD and experienced the same problem. I tried again, and again, but same problem. If someone knows the solution please help. 


This is a different issue particular to the 10.04 server install disk. I personally lost two days to this one. Basically the installer partitions the disks wrongly and doesn't allow the RAID 1 superblock to be created. To combat this, leave about .1 Gb at the end of each disk free. Or more if you want. Check here
[https://bugs.launchpad.net/ubuntu/lucid/+source/mdadm/+bug/569900](https://bugs.launchpad.net/ubuntu/lucid/+source/mdadm/+bug/569900)

Once again this is *specific to the server version 10.04*.

---

### Post by olivierz on 2010-09-21
I have posted this answer already on another page.

I had the same problem with UNETbootin and also with Pendrive Linux. They did not work!!!! Had either busybox issues, or nothing coming up at all!

You could try the Ubuntu liveusb creator, but if you do not have a nix machine at hand, there is still a solution:

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Lili USB: it installed my maverick netbook iso flawlessly, and the image booted perfectly.

I am now enjoying Unity on my eeePC 701 and my Aspire One

Try and see, you will also discover the brilliant features that are at  hand, with a portable virtual box included in the installation.

I just love it now!!! Share the love!

---

### Post by Fer Servadu on 2010-09-25
I can confirm that Oliverz's suggestion (using the linuxliveusb.com tool) worked for me. Today's daily build loaded up with no problem.

---

### Post by mageus on 2010-09-26
> **olivierz said:**
> ...there is still a solution:

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

So, you're saying in order to run linux, we have to run Windows to run a program to create an installer to install linux to run linux?

The irony kills me.

---

### Post by ncwalker2010 on 2010-09-27
Double fist pump to Krazy Penguin.

Running 10.04 and mine wouldn't start off my hard drive.

Followed the instructions in his link, answered "yes" to all the questions and I am back in Linux heaven.

I'll never go back to Windows, no matter how painful.  It's principle now.

(BTW, my system locked when I was trying to print an email from Evolution.  Just froze.  I hard booted and that's when I got the error.)

---

### Post by olivierz on 2010-10-06
> **mageus said:**
> So, you're saying in order to run linux, we have to run Windows to run a program to create an installer to install linux to run linux?

The irony kills me.

Haha, true but this solution is IF you do not have a nix machine at hand :P

Otherwise, use the live usb builder on ubuntu

"I'll never go back to Windows, no matter how painful.  It's principle now.

(BTW, my system locked when I was trying to print an email from  Evolution.  Just froze.  I hard booted and that's when I got the error.)"

I have Windows at work, so Liliusb is very useful to me. I can just work AND have Ubuntu running in the foreground, as it is with a portable version of virtualbox. Why? Because my job involves websearching, and my browsing on ubuntu is quicker and surer, I am more efficient that way.

---

