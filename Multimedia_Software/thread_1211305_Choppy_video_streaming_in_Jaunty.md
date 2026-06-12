---
title: "Choppy video streaming in Jaunty"
date: 2009-07-12
forum: Multimedia Software
---

### Post by DnjS on 2009-07-12
Hi,

Ok, so I know this question's been asked a thousand times though none of the posts I've read so far has provided an answer. (actually one did fry my system... :P ) Anyways, one of the main things I use my computer for is watch anime on sites such as animeshippuuden.com and the fact that I have to log into windows every time I feel like watching some is kind of a deal breaker for me, I usually just end up logging in to windows from the start because of it.

I have no issues when not in fullscreen and I have a 10Mb connection.

My computer is an Inspiron 6400 laptop and the VGA compatible controller is an Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
                                       I'll appreciate any help I can get ;)

---

### Post by lovinglinux on 2009-07-12
[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

See section: Flash Optimization

> Compiz users might get considerable flash performance improvement in full screen mode by disabling the option Unredirect Fullscreen Windows that can be found under "System >> Preferences >> CompizConfig Settings Manager >> General Options >> General".

Also recommend: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by DnjS on 2009-07-12
unfortunately none of those actually worked for me, though I still appreciate the help. At the moment I'm resorting to the firefox-plugin download help manager for my anime viewing. I guess there's not an easy solution to this issue, though seemingly not everybody experience the flash-problem. Is that due to having a more powerful computer or something?

---

### Post by lovinglinux on 2009-07-12
> **DnjS said:**
> unfortunately none of those actually worked for me, though I still appreciate the help. At the moment I'm resorting to the firefox-plugin download help manager for my anime viewing. I guess there's not an easy solution to this issue, though seemingly not everybody experience the flash-problem. Is that due to having a more powerful computer or something?

Probably is due to your graphics card, which is not playing well with Ubuntu 9.04.

Anyway, when I play flash videos, Firefox uses 45% of my CPU which is not normal. The same video when played through gecko-mediaplayer or when downloaded and played locally with gnome-mplayer, uses only 9%. [Something is wrong](http://bugs.adobe.com/jira/browse/FP-1692).

---

### Post by DnjS on 2009-07-13
Hmmm, what's the reason for it being so bad? Is it Adobe's fault for not writing better drivers? And why aren't the free ones any good?

I just went to the adobe site you linked and it would seem that they're working on it :) Can't wait untill the fix is ready. :D

---

### Post by lovinglinux on 2009-07-13
> **DnjS said:**
> Hmmm, what's the reason for it being so bad? Is it Adobe's fault for not writing better drivers? 

I guess so.

> **DnjS said:**
> And why aren't the free ones any good?

Because flash is proprietary. I have no idea how the make the free ones, but incompatibilities with some sites is kind of expected.

---

### Post by DnjS on 2009-07-13
K k, thanks for your help!

---

### Post by Shpongle on 2009-07-15
this works for me its not really a fix but if you watch the video normall and zoom in with compiz its watchable

---

### Post by DnjS on 2009-07-17
Yeah I've heard about that. thanks for the tip, I'll try it out soon! :)

---

### Post by cottfcfan on 2009-07-19
This problems bugged me for ages. Ive got a dell inspiron 531, 3GB Ram
my CPU shows between 60-70% usage even in small screen when streaming. Full screen is just too choppy to watch. The strange thing is that, 1st boot after installing FGLRX from hardware drivers its fine. But after that deteriorates again. Ive searched for weeks but found no answer.

---

### Post by cottfcfan on 2009-07-19
OK From searching countless threads i`ve discovered this:
 When I run "cat /proc/mtrr" from a terminal I get this:

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back 
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back 
reg02: base=0x0e0000000 ( 3584MB), size=  256MB, count=1: write-combining 

At the moment streaming video and everything runs fine with CPU running at 20-25%.

However after a reboot streaming video runs crappy again CPU is using 70-80%
but now "cat /proc/mtrr" reads this:

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back 
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back 

I`m no expert but this has to be something to do with the problem.
And I`ve no idea what to do about it.
Expert help needed please!!

---

### Post by cottfcfan on 2009-07-19
Ignore the above post. After experimenting ive managed to keep my cat/proc/mtrr file the same as in figure one and i`m still experiencing high CPU usage and choppiness when streaming using flash.
 Ive just added the following to my xorg.conf file:

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Now ive got perfect streaming again, only using 25% CPU.
The problem is I know as soon as I reboot, i`ll lose all the improvements.
Back to the drawing board.

---

