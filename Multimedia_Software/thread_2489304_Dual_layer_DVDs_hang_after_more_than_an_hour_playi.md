---
title: "Dual layer DVDs hang after more than an hour playing"
date: 2023-07-25
forum: Multimedia Software
---

### Post by lescribe on 2023-07-25
Hello,

I have an issue with dual layer commercial DVDs.
After playing the movie nicely for more than an hour, they start stumbling and eventually hang. I tested several players (VLC and Kaffeine). The DVDs themselves have no physical damage. Memory isn't overloaded. I tried changing a few parameters in VLC like increasing the buffer, but it didn't provide any significant improvement.
While investigating the issue, I tried extracting the ISO from one of those DVDs. At about 5 GB reading errors occurr frequently, and rapidly bring the extraction to a stall. Single DVDs play and get extracted just fine. This pointed me to the direction of an issue with the second layer.
I googled the issue and searched this and the French Ubuntu forum for hints, but didn't find anyting. So I hope this community will be able to find a solution for me :)
Any idea?

Please note that the same DVDs used to work just fine on this computer (with the same integrated DVD player). But this is the first time I try playing DVDs since I did a complete reinstall of my machine, scrapping my 20.04 LTS installation (and its Windows dual-boot) and going to 22.04 LTS only. 


Thanks!




Here are my system details:[INDENT]Kubuntu 22.04[/INDENT]
[INDENT]KDE Plasma version 5.24.7[/INDENT]
[INDENT]KDE Framework 5.92.0[/INDENT]
[INDENT]Qt version 5.15.3[/INDENT]
[INDENT]Kernel version 5.15.0-76-generic (64-bit)[/INDENT]
[INDENT]Graphics platform X11[/INDENT]
[INDENT]PC HP G71-340US[/INDENT]
[INDENT]Memory 3.7 GiB RAM[/INDENT]
[INDENT]Intel Graphics Media Accelerator (GMA) 4500MHD[/INDENT]
[INDENT]Intel® Core™2 Duo Processor T6600 2M Cache, 2.20 GHz, 800 MHz FSB[/INDENT]
[INDENT]Lecteur CD-RW/DVD+/-RW DL HP DVD RW AD-75615[/INDENT]

---

### Post by gezzer2 on 2023-07-25
have you installed the Ubuntu restricted extra packages via synaptic, there are two of them and also have a look at libdvd-pkg as it has the libdvdcss2 libs ...

---

### Post by lescribe on 2023-07-26
Hi,
Yes, I've installed the restricted extras and libdvd libraries. That's how I could watch the first part of the movies.

---

### Post by gezzer2 on 2023-07-26
have a look here on the VLC site this gives a howto on duel layer DVD issues ...

[https://code.videolan.org/videolan/vlc/-/issues/20355](https://code.videolan.org/videolan/vlc/-/issues/20355)

---

### Post by lescribe on 2023-08-01
Hi,

Disabling the DVD menu didn't help. I got the error message "Playback failure: DVDRead could not read 1/4 blocks at 0x26b3f1."
But anyway, it's the DVDs themselves who seem to be at fault. On the French forum someone looked at my logs and arrived at this conclusion. And indeed I borrowed a dual layer DVD from my neighbour, and it reads perfectly well. So I'm left with a whole "Special Extended Version" set of The Lords of the Rings which aged bad and are now unreadable. Not sure New Line Cinema will agree to refund me after several years. A real shame!

Thanks for looking into this!

---

### Post by gezzer2 on 2023-08-02
> **lescribe said:**
> Hi,

Disabling the DVD menu didn't help. I got the error message "Playback failure: DVDRead could not read 1/4 blocks at 0x26b3f1."
But anyway, it's the DVDs themselves who seem to be at fault. On the French forum someone looked at my logs and arrived at this conclusion. And indeed I borrowed a dual layer DVD from my neighbour, and it reads perfectly well. So I'm left with a whole "Special Extended Version" set of The Lords of the Rings which aged bad and are now unreadable. Not sure New Line Cinema will agree to refund me after several years. A real shame!

Thanks for looking into this!

could you not rip the DVD's to a HDD and see if they play from there, just a thought ...

---

### Post by lescribe on 2023-08-02
I had the same exact thought and tried this prior to posting here. The copy stalled shortly before reaching 5GB. That's actually what led me to thinking the second layer was the trigger. Indeed, I tried single layer disks and they worked fine. What I did not think of doing at the time was trying other dual layer DVDs, not from the LotR set. In the end it's not just any dual layer DVD exhibiting the issue. It's just those from this set.

---

### Post by gezzer2 on 2023-08-02
have a look here as it would seem you are not alone with the LoTR DVD's. but there is a work around ...

[https://forum.videohelp.com/threads/75221-Backup-of-LOtR-extended-version](https://forum.videohelp.com/threads/75221-Backup-of-LOtR-extended-version)

---

### Post by lescribe on 2023-08-03
Indeed, searching specifically for the LOTR extended edition DVDs yields a number of forum posts about reading issues. Thanks for the nudge in that direction.
None of them have been helpful, though. Mostly it was firmware compatibility issues when the DVDs first came out years ago.

---

### Post by gezzer2 on 2023-08-03
a cunning plan or an idea has spring to mind. do these LoTR DVD's play alright in Windows? ...

if they do play in windows you could use a VM (virtual box or gnome boxes) with Windows 10 installed in the VM and then rip the DVD's to HDD then try playing them in Linux.

as stated its just thought but a lot of effort ...

---

### Post by lescribe on 2023-08-04
I don't have a Windows machine I can try them on, but that's an interesting idea. I'll see if I can find one. If they do work on a Windows machine, I could simply rip them on it and shun the DVDs altogether.
Thanks for the suggestion.

---

