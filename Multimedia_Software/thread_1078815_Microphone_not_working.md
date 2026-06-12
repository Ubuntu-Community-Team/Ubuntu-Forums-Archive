---
title: "Microphone not working"
date: 2009-02-23
forum: Multimedia Software
---

### Post by hosch on 2009-02-23
I have not been able to get my microphone to work on my linux box.

I have tried on two computers with the same OS, but different boards with no luck.

I went out and purchased a Creative Sound Blaster Audigy SE today and while I am getting sound, still no microphone.

I have not been able to find anything posted on this anywhere - has anyone dealt with this?

Also, I am new to Linux/Ubuntu - less than a week total and loving it so far:).

---

### Post by hosch on 2009-02-23
Well, here is an example of how a noob can screw up something that is perfectly good ;\

I found a post suggesting to do this:

Open a terminal session (Applications ->Accessories -> Terminal) andÂ  type:

    gksudo gedit .asoundrc

Once gedit opens up either add this to the blank file, or change your .asoundrc file to the following:

    pcm.!default {
    type plug
    slave.pcm “surround51&#8243;
    slave.channels 6
    route_policy duplicate
    }

So I dove right in and now I have no sound at all.

Now I have nothing - no sound - no microphone.

Loving the OS overall, but still not able to do basic functions such as set up microphone, sound, etc.

Any help appreciated. Thanks.

---

### Post by JordBrow on 2009-03-14
hi, I may have done the same as you earlier this week.  I too am new to ubuntu. I ended up without any sound.  It seemed that there was no sound card installed that the system could see.  I tried restarting with the older kernel that originally installed with the iso I downloaded and magically sound was back working (not microphone though).

If you have downloaded all the updates after your first install you should too have the newer kernel (2.6.27-11).  So try to reboot and press ESC to go to the menu to select the older kernel.  See if the sound works there.  If it does then reboot in the newer kernel again and try this:

this will reinstall the kernel (worked for me)

sudo apt-get install --reinstall linux-image-2.6.27-11-generic

the only thing I had a problem with afterwards was VirtualBox (if you use it?)  I just had to uninstall, download and install again to get it working right.  None of your files will be deleted, atleast non of mine were.

Just letting you know what worked for me on Ubuntu 8.10.


good luck, and if you find anything that works to get your microphone working please post let me know on the thread i have open:
[http://ubuntuforums.org/showthread.php?t=1094333]("http:/http://ubuntuforums.org/showthread.php?t=1094333")

---

