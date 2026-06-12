---
title: "BQ M10 tablet: first impressions"
date: 2016-04-20
forum: Mobile Technology Discussions (CLOSED)
---

### Post by John_Harris on 2016-04-20
[LIST]
[*]I've powered up the Ubuntu tablet.
[*]I've upgraded to Ubuntu version 3 (that's what I saw, anyway), 510MB, something now says "software up to date".
[*]I've not yet tried a Bluetooth keyboard but I think I need to, there's one on my desk doing nothing at the moment, the on-screen keyboard involves shifting for numerics, special characters and control characters.
[*]I've opened LibreOffice and saved a document, which is encouraging.
[*]I installed a terminal and failed to successfully run sudo apt-get update.
[*]So far I've found no documentation but I'm sure it has to exist somewhere.
[*]Immediately, I'd like to compile a couple of programs to help me wander around. Midnight Commander (mc) and ncdu, they'd be a good start. If anyone else does it they might enter the thread please.
[*]I have a lot of new vocabulary to learn. What's a Scope?
[*]How do I encrypt the storage so the device can't leak data if it's stolen? Ubuntu uses LVM2 and LUKS, if I remember right. I can't put any work files on this without encryption on the home directory at the very least. I don't think the passphrase lock is sufficient if it doesn't control an encryption layer.
[*]I may misunderstand the SD card, either I don't know where it automounts or it's not automounting.
[/LIST]

---

### Post by Michael_Crees on 2016-04-21
Fun isn't it?
On your last point, the best way to access the data on your SD card is to install the File Manager app and use that. You'll find it replicates the home folder structure on it (whether you want it to or nor not) indeed, it'll do the same if you use an OTG USB drive.

---

### Post by Johan_Helsingius on 2016-04-21
In the same boat - finally managed to get sshd to work, but a bit put off by the "feature" of non-active applications being suspended (a "feature" caused by the underlying android OS?) - sshd only works if the terminal application is the active one on the tablet.

---

### Post by John_Harris on 2016-04-21
I need a compiled compiler from somewhere, since I have no compiler to compile a compiler with. Has anyone yet found a developer resource with tools like that?

---

### Post by John_Harris on 2016-04-21
> **Michael_Crees said:**
> the best way to access the data on your SD card is to install the File Manager app and use that. You'll find it replicates the home folder structure on it (whether you want it to or nor not) indeed, it'll do the same if you use an OTG USB drive.

Right - I can see the SD drive and I can create a folder on it. The File Manager app seems reluctant to drag-and-drop, or copy/paste. Shifting files back and forth is an option which eludes me.

And it's formatted (by the M10) as some flavour of vfat, which isn't going to hold permissions. When I can get to mount it onto the file tree and address it as a dev I'll try the SD card as ext4. Though my nominal 9GB of free space out of the box will last me for quite a while, the SD card isn't vital.

---

### Post by John_Harris on 2016-04-22
I've used the M10 terminal to 

sudo umount /dev/mmcblk1

which was the fat partition - note there's no partition table. I could make a partition table with cfdisk and I'm sure I could, had I got the umount right at the time, have formatted the partition. As it is I formatted the SDcard itself

sudo mkfs.ext4 /dev/mmcblk1

and it will mount. Restarting the tablet, the SDcard isn't recognized by the android half - not surprising - but the ext4 is still there from the terminal app. I reckon there's ways from here to encrypt that space on the fly, either with cryptsetup and LUKS or with something else, and to mount it as the replacement ~/home. Without an encrypted home I'm stuck.

I still can't yet install a compiler though. And I don't have an Ubuntu desktop to use the phablet-tools and drive the M10 content from the desktop, and I don't want to. I want a tablet that can stand on its own abilities.

---

### Post by bernard-godard on 2016-04-24
> **Johan_Helsingius said:**
> In the same boat - finally managed to get sshd to work, but a bit put off by the "feature" of non-active applications being suspended (a "feature" caused by the underlying android OS?) - sshd only works if the terminal application is the active one on the tablet.

As a workaround, when you enable Desktop mode the terminal does not get suspended when focus is given to another application.

---

### Post by Jon_Thomas on 2016-04-24
> **bernard-godard said:**
> As a workaround, when you enable Desktop mode the terminal does not get suspended when focus is given to another application.

If you switch to Desktop mode, does the on-screen keyboard still work, or is it expecting a physical keyboard at that point?

---

### Post by bernard-godard on 2016-04-24
> **Jon_Thomas said:**
> If you switch to Desktop mode, does the on-screen keyboard still work, or is it expecting a physical keyboard at that point?

The on-screen keyboard is still working. However it will hide part of the desktop and you should resize manually the terminal window to use only the upper half of the screen to be able to see what you type (it is not done automatically).
According to the user manual in desktop mode even legacy X11 apps such as Firefox make use of the on-screen keyboard when no external keyboard is attached, but this doesn't work for me.

---

### Post by Harald Franzen on 2016-04-25
Hi guys,

I too, have bought the tablet - for the first time in my life I am an early adaptor :-)
In principal, I love the idea and I commend Canonical (and BQ) for the effort: the potential for a tablet running Ubuntu -for me- is fantastic; it could be a wonderful tool that I really WANT to use in my (small) business environment. Well done so far!

My findings so far:
- I can lock an app to the dash, but I cannot - in tablet mode; I am yet to hook up a keyboard - unlock the app from the dash and remove it
- location sucks; it puts me around 300 km from where I am, even with GPS on
- the idea of "Scopes" is not necessarily my cup of tea, but they would be a powerful tool for most users IF they were adaptable. I don't want to read news served up by the BBC, for example, so it would be great to have many more configurable option.
- for the tablet to be a real convergence tool, it would need the basic infrastructure we have on i386 and AMD64; my NAS, for example, serves up directories under NFS (I have used NFS shares ever since Edgy, IIRC, so around a decade). nfs-common does not seem to be available (yet) under ARM. Methinks all of this type of infrastructure should become available ASAP (like mysql-client) for the tablet to be able to properly connect with its surroundings. I do not use SMB at all, and exactly that is available though. NFS is linux native. SMB is windows :-(
- LibreOffice on a tablet: it's a fantastic thing, but neither LibreOffice nor Firefox open the on screen keyboard, so they are useless without a USB keyboard
- When you have on app on side stage - another great feature that I love - the app running on the main screen (so to the left) is not scaled correctly; you cannot read all the text on a website for example if you run the browser on the main screen with another app on the side stage. It took me forever, though, to find some video on the web telling me it takes a 3-finger gesture to get an app to run side stage :-)
- I managed to crash the tablet when I ran "sudo apt-get update", using the terminal app.
- Dekko (the email client) does not like to co-operate much with my Dovecot server (I found a posting somewhere indicating how to rectify it and will try to do that once I hook up a keyboard).
- the file manager from the Ubuntu store can copy files, but I cannot find where I can paste the file, files or directory I have just copied (I changed the NAS settings so it will serve up my music files over SMB - which needs "anonymous access" :-( but cannot do an "en masse" copy of multiply files so the tablets' music player has something to play.

So.... that's a brief overview of my first exploits. It's a cool and rather snappy device, but Canonical and the community need to step up to the plate to turn this machine into something stunning and useful!

---

### Post by Johan_Helsingius on 2016-04-25
> **Harald Franzen said:**
> - Dekko (the email client) does not like to co-operate much with my Dovecot server (I found a posting somewhere indicating how to rectify it and will try to do that once I hook up a keyboard).

When you do, please post the instructions here too. I am using dekko with a dovecot server, but it is almost but not entirely useless...

---

### Post by bernard-godard on 2016-04-25
> **Harald Franzen said:**
> 
- I can lock an app to the dash, but I cannot - in tablet mode; I am yet to hook up a keyboard - unlock the app from the dash and remove it


If you leave your finger pressed a few seconds on the app icon in the dash, you will have a popup menu with the option to unlock.

---

### Post by Harald Franzen on 2016-04-25
> **bernard-godard said:**
> If you leave your finger pressed a few seconds on the app icon in the dash, you will have a popup menu with the option to unlock.

unfortunately, that does not work. Now I have a keyboard attached, I can remove the apps from the dash.

---

### Post by Harald Franzen on 2016-04-25
> **Johan_Helsingius said:**
> When you do, please post the instructions here too. I am using dekko with a dovecot server, but it is almost but not entirely useless...

This here worked for me: [https://bugs.launchpad.net/dekko/+bug/1435066](https://bugs.launchpad.net/dekko/+bug/1435066)

Once I changed the .conf file, it worked!

Good luck!

---

### Post by Johan_Helsingius on 2016-04-26
Thanks!

---

### Post by alj-3 on 2016-04-26
After purchasing my M10, I am really reminded of my first forays into Ubuntu, back with 8.04. Everything kind of half-worked, and you had to implement a bunch of workarounds to get things going right. And you looked forward to every little update, because that meant maybe that #$%^! wifi would start working. Hoping for the same rapid progress here.

---

### Post by Harald Franzen on 2016-04-27
> **alj-3 said:**
> After purchasing my M10, I am really reminded of my first forays into Ubuntu, back with 8.04. Everything kind of half-worked, and you had to implement a bunch of workarounds to get things going right. And you looked forward to every little update, because that meant maybe that #$%^! wifi would start working. Hoping for the same rapid progress here.

I agree completely!
However, it makes sense for us to let Canonical and the community know we are here so there's more incentive for them to improve.
I found a list somewhere of all the applications they had already ported to ARM and I assume eventually all will be ported :-)
*thinking positive*

---

### Post by Michael_Crees on 2016-04-27
Unfortunately I was rather more reminded of my experience with a FirefoxOS phone. Only a sequence of updates that dramatically improve functionality will serve to dispel that impression.

---

### Post by John_Harris on 2016-04-27
I'll not return the tablet but I'll put it in a drawer for a couple of months, I've work to be getting on with. Maybe it will get useable with time. I'm pleased the effort's being made, at least.

---

