---
title: "Flash videos stutter"
date: 2009-06-04
forum: Multimedia Software
---

### Post by sushiosoyum on 2009-06-04
I am using Ubuntu 9.04 Remix on my Acer Aspire One. It formally came with Windows XP and every single flash site worked without a problem.

Since installing Ubuntu every single flash site stutters the video (Youtube, Youporn, Comedy Central, Hulu). 

It's to the point now where I think I'm going to ditch Ubuntu and put XP back on :(

I did ANOTHER fresh install tonight.

Video still stutters. 

I installed the restricted drivers.

Video still stutters.

I have a FIOS connection so it's not the fact my connection is slow. Pausing the video and waiting for the entire clip to buffer produces the same stuttering results.

How do I fix this?

This is driving me nuts!

---

### Post by bcschmerker on 2009-06-04
What chipset does your Acer have?  I've run [Adobe Flash](http://www.adobe.com) on three different hardware sets (an all-[VIA Technologies](http://www.via.com.tw/) set with 1.5 GHz C7-D, an [nVIDIA nForce/GeForce](http://www.nvidia.com/) set with 2.8 GHz AMD Athlon X2, and an all-[Advance Micro Devices](http://www.amd.com/) set with 2.9 GHz Athlon X2), and only on the VIA set did I encounter a stutter problem (as it is underpowered for most Web applications as of Spring 2009).  Also, which LinUX kernel and Adobe Flash version are on your Acer?

---

### Post by sushiosoyum on 2009-06-04
I have no idea how to check that.

:popcorn:

---

### Post by davidryderuk on 2009-06-04
Hi,
I'm not sure how well this will work because I don't have your netbook, although i do have an intel GPU. However i thought it was worth mentioning the set up advice specific to your computer below. Solutions to your problem are listed under "To Fix Choppy Video Playback With Intel Video"  

```
https://help.ubuntu.com/community/AspireOne#Notes%20about%20Ubuntu%209.04%20(Jaunty%20Jackalope)%20desktop%20and%20UNR%20(Netbook%20Remix)
```

If you are quite new to linux I would probably just stick with the first step.

1. Edit the grub booting options by typing into terminal

```
gksudo gedit /boot/grub/menu.lst
```  

2. Scroll down to defoptions line in the text editor and add "enable_mtrr_cleanup mtrr_spare_reg_nr=1" to the end of the line so that it looks something like the following.

```
# defoptions=quiet splash enable_mtrr_cleanup mtrr_spare_reg_nr=1
```

3. Save the edited file and exit.

4. Go back to the terminal and type

```
sudo update-grub
``` 

5. Reboot and check your video performance again.

6. If you want to restore orginal performance repeat the above steps but this time remove "enable_mtrr_cleanup mtrr_spare_reg_nr=1" from the same line as before.  

There are additional improvements that can be made to your video performance, as listed in the link above, but they involve harder to follow and probably risker changes.

---

### Post by arkadas on 2009-06-24
i found the solution i send a message to him
unistall through synaptic sdwf and gnash flash players and its ok
some confilct may occured

---

### Post by wzy on 2009-08-29
Can you post the solution here? I have a simular problem but can't get it to work..

---

### Post by nunovi on 2009-11-21
Hi,
 
It's a well known problem that flash on Linux performs horribly slow, especially on Atom-based system as the GPU is not used. I don't want to discourage you but there is really no solution other than Adobe to fix Flash on Linux.
 
If we make this issue big enough, we can gain a higher priority for Adobe to solve this issue. Please go to [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692), register and vote for this issue. If we all take 5 minutes to do this, I'm sure we can reach a very high number of votes and let Adobe know Linux is an important community to take into consideration.
 
Nuno

---

### Post by ibuclaw on 2009-11-21
Old Thread - Closing.

If you are having this issue, raise a new support question.

Regards
Iain

---

