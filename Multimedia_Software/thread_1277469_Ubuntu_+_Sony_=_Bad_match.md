---
title: "Ubuntu + Sony = Bad match?"
date: 2009-09-28
forum: Multimedia Software
---

### Post by ChiVampir on 2009-09-28
I have a Sony NWZ-S615F (MTP player as far as I know) mp3-player which Ubuntu don't want to cooperate, which is really frustrating. 

In Windows, Xandros and Mac the mp3-player shows up as a harddrive. It actually shows up in Ubuntu as well but I can't se any files or folders, and I get a message that tells me that the files are placed on a digital mediaplayer with the button "Open VLC media player". I have tried to syncronice with lots of meida players (Rythmbox, Amarok, Songbird, Banshee, VLC, Mplayer osv...) and a program made to manage MTP-devices named Qilx, but still without any luck. And I have of course made the mandatory Google search, but I didn't get anything out of that either. 

So my question is: Has anyone got these two to cooperate or is it impossible?

And if the answer is no: Which mp3-players can I get Ubuntu to cooperate with?

---

### Post by ChiVampir on 2009-09-29
I finally found a solution ^^
> All Sony Walkmans with model numbers beginning "NWZ" work with all USB-capable operating systems, as they just uses standard USB Mass Storage drivers.

Due to a bug in HAL, it will not automatically mount in Ubuntu 8.04. It can be manually mounted.

Due to a bug in Gnome, it will not be correctly mounted in Ubuntu 9.04. If you run the command "killall gvfs-gphoto2-volume-monitor", unmount the device, unplug it and plug it back in, it will correctly mount. Or you can use KDE.

Older Walkmans that do not have model numbers beginning "NWZ" are not Linux-compatible.Source: [http://www.linuxcompatible.org/Sony_Walkman_NWZ_c14105.html](http://www.linuxcompatible.org/Sony_Walkman_NWZ_c14105.html)

But lets see if I have understood this right: Does this mean that Sony NWZ players work in Kubuntu?

---

### Post by doas777 on 2009-09-29
I;'ve never found an OS that sony plays nice with, with the exception of their XCP rootkit. that seemed to install without fail.

---

### Post by chrisjsmith on 2009-09-29
Sony's really cheap USB stick MP3 players are /usually/ ok.  Not sure about NWZ.  I just threw mine away the other day though as it's annoying me.

TBH though all Sony products are based around proprietary lock-in - think MiniDisc, ATRAC, horrid custom utilities on their laptops, memory stick etc etc.

Apple are no better.

Sorry rant over!

---

### Post by pythonscript on 2009-09-29
I've had the same problem with my NWZ-S616F, and even though I've found "solutions" online, the strategies tried were either out of date or simply didn't work for numerous reasons. I use mine through a virtual windows xp, which is a royal pain to have to boot a virtual win xp to send music to it, but I guess that's life. The mp3 player uses an MTP file system, so if anyone knows more about getting those to work with ubuntu, let's get it on this thread.

According to this link, such mp3 players should "just work" with Rhythmbox after installing MTP support from the repos. However, I've never been able to get it to work (or maybe just understand how even to *use* Rhythmbox with an mp3 player in general) but I've never had any luck with it. 

[http://linuxtechie.wordpress.com/2008/03/09/ubuntu-804-hardy-heron-brings-better-mtp-support/](http://linuxtechie.wordpress.com/2008/03/09/ubuntu-804-hardy-heron-brings-better-mtp-support/)

---

### Post by ChiVampir on 2009-09-29
> **doas777 said:**
> I;'ve never found an OS that sony plays nice with, with the exception of their XCP rootkit. that seemed to install without fail.

Weird.
I have got this player to work in every OS I have tried so far (including for example: Windows 98->7, Mac OS, Xandros und so weiter), except from Ubuntu actually, and the same with other Sony products that are based on drag and drop. 

But when I read the KDE note, it made me aware that every Linux OS I have used were KDE based. So if this is a Gnome problem I can understand why it's not working in Ubuntu.

But as I said I have found a solution that works :)

---

### Post by pythonscript on 2009-09-29
> **ChiVampir said:**
>  But as I said I have found a solution that works :)

 Care to elaborate?

---

### Post by ChiVampir on 2009-09-29
> **pythonscript said:**
> Care to elaborate?

See the fist reply to this tread which I have actually written myself when I found the solution. 

I was kind of surprised that this unanswered tread got so many answers today, since I actually found and posted a solution as the fist answer.

---

### Post by pythonscript on 2009-09-29
I couldn't get your solution to work at first, but I'll give it another try when I'm back to my apartment.

---

### Post by ChiVampir on 2009-09-29
> **pythonscript said:**
> I couldn't get your solution to work at first, but I'll give it another try when I'm back to my apartment.

Ok...
Try to check if you have **pmount** and **hal  **installed if you can't get it to work (restart after the instalations) and try again.
Installed these packages when I tried another guide which didn't work, so maybe they will do the trick.

---

### Post by pythonscript on 2009-09-29
I'll give that a try; thanks! More details later.

---

### Post by pythonscript on 2009-10-12
Sorry to raise an old thread, but I finally had a chance to try out the solution from post #2 on my laptop, and it worked great! After I ran the command, copied some music, etc, I thought it might have messed up a few of my other gnome apps (banshee and gedit kept crashing) but those problems went away after a few minutes, so I guess it was unrelated. This works great; just one more thing I can slowly migrate away from Windows. Any idea how to make this work with, say, banshee or rhythmbox, so I can sync playlists, though?

---

