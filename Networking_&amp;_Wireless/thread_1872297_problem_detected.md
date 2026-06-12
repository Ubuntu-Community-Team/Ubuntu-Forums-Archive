---
title: "problem detected?"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by Matrix01 on 2011-10-30
[ATTACH]205887[/ATTACH]

this message showed up every time when i typed firefox in terminal, and launched firefox.

well,
i found out,
this message showed up every time right after 11.04 get booted.

---

### Post by Paddy Landau on 2011-10-30
What version of Ubuntu? What version of Firefox (if you're not sure, go to the Ubuntu Software Centre)? What happens when you press *Cancel* and what happens when you press *Report problem*? Did Firefox work before? When did the problem start happening? Does it happen only from the terminal, or from the launcher as well?

---

### Post by Matrix01 on 2011-10-30
[ATTACH]206107[/ATTACH]

1. Natty, 11.04
2. 4.0 it's default firefox installed on 11.04.
3. click cancel--nothing.
4. click report problem---firefox lauches.
5. yesterday...
6. firefox does not launch from launcher, and 
    i found out this message pops up whenever 11.04 get booted.




> **Paddy Landau said:**
> What version of Ubuntu? What version of Firefox (if you're not sure, go to the Ubuntu Software Centre)? What happens when you press *Cancel* and what happens when you press *Report problem*? Did Firefox work before? When did the problem start happening? Does it happen only from the terminal, or from the launcher as well?

---

### Post by Paddy Landau on 2011-10-31
> **Matrix01 said:**
> 2. 4.0 it's default firefox installed on 11.04.
That puzzles me. I'm running Natty, but I have Firefox 7.0.1.

Please run your updates (Update Manager), restart if required, and see which version of Firefox you then have.

---

### Post by Matrix01 on 2011-11-02
i'm not sure.
is this FF 4.0?

[ATTACH]206108[/ATTACH]

> **Paddy Landau said:**
> That puzzles me. I'm running Natty, but I have Firefox 7.0.1.

Please run your updates (Update Manager), restart if required, and see which version of Firefox you then have.

---

### Post by Paddy Landau on 2011-11-02
> **Matrix01 said:**
> i'm not sure.
is this FF 4.0?
Open Firefox. Go to Help > About Firefox. That will tell you your version.

---

### Post by Matrix01 on 2011-11-04
[ATTACH]206273[/ATTACH]

is this firefox 4.0?

> **Paddy Landau said:**
> Open Firefox. Go to Help > About Firefox. That will tell you your version.

---

### Post by Paddy Landau on 2011-11-04
> **Matrix01 said:**
> is this firefox 4.0?
Yes, it is.

Open Update Manager, press *Check* to check for available updates, then press *Install Updates*. It should update your Firefox to the current version.

If it does not, post back here. (Did you install a fresh version of Natty, or did you upgrade from a prior version?)

---

### Post by Matrix01 on 2011-11-05
I downloaded unetbootin 563 and iso file, and installed persistent 11.04 in USB flash drive in a few weeks ago.
[ubuntu-11.04-desktop-i386.iso]("http://mirror.yellowfiber.net/ubuntu/11.04/ubuntu-11.04-desktop-i386.iso") 

having other problems as well; unable to make short cut of terminal on desktop.

> **Paddy Landau said:**
> Yes, it is.

Open Update Manager, press *Check* to check for available updates, then press *Install Updates*. It should update your Firefox to the current version.

If it does not, post back here. (Did you install a fresh version of Natty, or did you upgrade from a prior version?)

---

### Post by Matrix01 on 2011-11-06
[ATTACH]206494[/ATTACH]

[ATTACH]206495[/ATTACH]

11.04 had gone through updating, but
message said Failed,

FF is updated to 7.0 but
FF does not show up on monitor when i clicked launcher

---

### Post by Paddy Landau on 2011-11-06
> **Matrix01 said:**
> 11.04 had gone through updating, but
message said Failed,

FF is updated to 7.0 but
FF does not show up on monitor when i clicked launcher
Firefox succeeded, but your linux kernel failed to update.

Please reboot, then type the following command into your terminal. If you get any errors, post the results back here. If you get no errors, reboot then try again.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Matrix01 on 2011-11-06
I shut netbook down, and started it.
"automatic log in" or "other" showed up on tab.
i clicked automatic log in, anything changed,
clicked "other", tab requires username showed up.

i do not even created account and username yet.
so
reinstalled unetbootin in usb, and ran update,
update failed again, and ubuntu was booting forever.

---

### Post by Paddy Landau on 2011-11-07
> **Matrix01 said:**
> update failed again, and ubuntu was booting forever.
I just realised that you are updating on a USB and not on your computer.

I am not sure to what extent you can run full updates on a USB, particularly with the kernel.

But at least the Firefox is running version 7.

As your original problem occurred on your computer's hard drive rather than on a USB, I was recommending that you run the updates for it there. Do it in two steps.


[LIST]
[*]In the terminal:```
sudo apt-get update
```If that gives errors, do not proceed but instead post the errors here.
[/LIST]


[LIST]
[*]In the terminal:```
sudo apt-get upgrade
```If that gives errors, post the errors here.
[/LIST]

If there are no errors, try rebooting and then Firefox.

---

### Post by Matrix01 on 2011-11-08
this 11.04 ubuntu was booting from USB flash drive with bootloader.

i am not sure that netbook's internal hard drive is involved with problems.
will u explain?

---

### Post by Paddy Landau on 2011-11-08
> **Matrix01 said:**
> this 11.04 ubuntu was booting from USB flash drive with bootloader.

i am not sure that netbook's internal hard drive is involved with problems.
will u explain?
Yes. After updating, your Firefox was correctly updated to the latest version.

Completely separately, your Linux kernel (that's the "inside" of Linux) failed to update correctly.

I am not sure that Linux kernel updates will be correctly updated on USB. They may be, but I'm not sure.

It is obvious that I had misunderstood you.

Try entering these two commands into the terminal (after booting from the USB):

[LIST=1]
[*]Enter the following command. If there is an error, do not proceed but instead paste the output here.```
sudo apt-get update
```
[*]Enter the following command. If there is an error, paste the output here.```
sudo apt-get upgrade
```
[/LIST]

---

### Post by Matrix01 on 2011-11-13
11.04 does not boot anymore.
i tried to reinstall it.
that did not work.

> **Paddy Landau said:**
> Yes. After updating, your Firefox was correctly updated to the latest version.

Completely separately, your Linux kernel (that's the "inside" of Linux) failed to update correctly.

I am not sure that Linux kernel updates will be correctly updated on USB. They may be, but I'm not sure.

It is obvious that I had misunderstood you.

Try entering these two commands into the terminal (after booting from the USB):

[LIST=1]
[*]Enter the following command. If there is an error, do not proceed but instead paste the output here.```
sudo apt-get update
```
[*]Enter the following command. If there is an error, paste the output here.```
sudo apt-get upgrade
```
[/LIST]

---

### Post by Paddy Landau on 2011-11-14
> **Matrix01 said:**
> 11.04 does not boot anymore.
i tried to reinstall it.
that did not work.
Do you mean that it no longer boots from your USB stick?

Without knowing what error you get, I'd have to guess. It is possible that the USB stick has hit its lifetime limit (the problem with sticks is a limited number of writes).

Are you installing onto your USB from Windows, Mac, Ubuntu or something else?

---

### Post by Matrix01 on 2011-11-15
yep,
11.04 is not booting from USB stick anymore.
this 8G usb stick is brand new, just bought it several weeks ago, and used it for only 11.04 installation.

I am on Window 7 Starter, and
reformatted USB stick, and reinstalled unetbootin 563 and ISO file; ubuntu-11.04-desktop-i386.iso

this message showed up:

(initramfs)mount:mounting/dev/loop0on//filesystem.squashfs failed:invalid argument can not mount/dev/loop0(/cdrom/casper/filesystem.squashfs)on//filesystem.squashfs

---

### Post by Paddy Landau on 2011-11-15
Did you install following the instructions for Windows 7 on the [Ubuntu download page]("http://www.ubuntu.com/download/ubuntu/download")?

---

### Post by Matrix01 on 2011-11-15
I used Unetbootin 563 and ISO file.
instruction in buntu's website uses another application; usb installer.

---

### Post by Paddy Landau on 2011-11-15
> **Matrix01 said:**
> I used Unetbootin 563 and ISO file.
instruction in buntu's website uses another application; usb installer.
That may be the problem. The USB stick has to be made bootable. As I recall, Unetbootin has not worked with Ubuntu for a couple of years.

---

### Post by Matrix01 on 2011-11-17
so
how do u suggest to install buntu?

---

### Post by Paddy Landau on 2011-11-17
Follow the instructions on the [Ubuntu download page]("http://www.ubuntu.com/download/ubuntu/download"). It has instructions how to install onto a USB stick from Windows.

---

### Post by Matrix01 on 2011-11-25
i formatted this 8G usb flash drive in NTFS,
tried to install, this time, different distro, xubuntu 11.10,
downloaded universal usb insaller from your link; [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download),
and
clicked 'create' on usb installer,
error message showed up like this;
[ATTACH]207927[/ATTACH]

repeated whole process, same message showed up.

---

### Post by Paddy Landau on 2011-11-25
> **Matrix01 said:**
> i formatted this 8G usb flash drive in NTFS
That may be the problem. NTFS is not a suitable format for a USB flash stick. I would reformat as FAT32 and try again.

It's a pity that the error message does not give more specific information. If you get the same message after formatting your USB flash to FAT32, please would you move the error window out of the way so we can see the messages hidden behind it.

---

### Post by Matrix01 on 2011-11-25
worked!
reformatted USB falsh disk in FAT32.
but i did not make persistent usb drive.

so...
I fixed step 4.
[ATTACH]207980[/ATTACH]

and rebooted, 
error message showed up; "general error mounting file system"

> **Paddy Landau said:**
> That may be the problem. NTFS is not a suitable format for a USB flash stick. I would reformat as FAT32 and try again.

It's a pity that the error message does not give more specific information. If you get the same message after formatting your USB flash to FAT32, please would you move the error window out of the way so we can see the messages hidden behind it.

---

### Post by Paddy Landau on 2011-11-26
> **Matrix01 said:**
> and rebooted, error message showed up; "general error mounting file system"
I'm sorry, that is an error I have not seen before.

This thread has strayed somewhat from its original problem. I think it's time to mark this thread as solved, and start a new thread with your new problem in a different forum. I would suggest either [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") or [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333").

Please post a link to the new thread here so that I can follow it.

---

