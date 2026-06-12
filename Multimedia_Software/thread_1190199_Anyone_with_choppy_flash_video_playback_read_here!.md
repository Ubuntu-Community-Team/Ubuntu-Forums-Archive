---
title: "Anyone with choppy flash video playback read here!"
date: 2009-06-17
forum: Multimedia Software
---

### Post by sandydoull on 2009-06-17
This seems to be linux-wide issue that has existed in as far back as version 9 of adobe flash player. Symptoms are choppy video playback especially when viewing fullscreen videos from sites such as youtube, BBCiplayer, hulu.com etc.

It might help if everyone who is having this issue goes to adobe's support site and votes for the bug to be worked on: [http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

Has anyone found a workaround for this issue, if so you might want to let them know over at adobe :lol:

---

### Post by caeroe on 2009-06-17
My older notebook plays flash just fine, even fullscreen.  It's a 3400+ AMD 64bit with 1gb ram, and a ATI 64mb dedicated card.  It plays flash as well as it is expected too, very smooth even on Hulu.

However my desktop's fullscreen flash performance is terrible.  It has a 5000+ dual core 64bit with 4gb of ram, and a 8800GT 512mb card.

Every so often I check in to see if this Flash issue has been fixed, but I'm under the impression that it'll never will be.  As a result, my netbook also came with Windows XP.  I'm not losing out on Flash video if it's meant for Internet productivity.

Edit:  Both the notebook and desktop run 9.04 64bit.

---

### Post by sandydoull on 2009-06-18
May be a bug with only certain types of graphic cards, you may want to post this info on the bug site.

---

### Post by moe19790 on 2009-06-18
yep needed this info :) thankx

---

### Post by Charbax on 2009-06-23
I have terrible Flash performance and especially in full screen mode, I have a Intel Celeron 2.40Ghz, 1520Mb RAM DDR1, in the Asus T2-P barebone box.

If this is a voluntary bug by Adobe, just to put Microsoft Windows in an advantage over Linux Ubuntu, I think that would absolutely really suck.

Though I am hopful to find some solution on this forum. If anyone can point me in the right direction I would appreciate.

---

### Post by caeroe on 2009-06-27
I doubt Adobe sabotaged Flash for Linux.  As I've said above, my older and less powerful notebook plays Flash just fine, even in fullscreen.

Both machines run Ubuntu 9.04 x64.  If I cared enough I'd roll back to something earlier and see what happens.  Fortunately I dual boot, so if I want to do anything multimedia related I hop in Win7.  It's disappointing I can't use a modern OS to watch Hulu in fullscreen.

For my desktop it's merely a backup if Win7 explodes on me.  I love this OS on my notebook though... unless kernel header updates break my wi-fi.

---

### Post by kickwin on 2009-06-29
I have the same problem with my Dell Laptop Inspiron 1300 on both Xubuntu and Ubuntu 9.04. Here is the laptop configuration.

lspci | grep VGA 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Intel® Celeron® M Processor 380
1.60GHz/1MB Cache/400MHz FSB
512 MB RAM

Though, it works fine in my office computer which is a much better configuration (dual-core etc..) and it has NVIDIA graphics card. Somebody please find out what this is about.

---

### Post by philcamlin on 2009-06-29
i had that issue on my other ubuntu machine. i uninstalled flash and it was better for me :popcorn:

---

### Post by kickwin on 2009-06-29
> **philcamlin said:**
> i had that issue on my other ubuntu machine. i uninstalled flash and it was better for me 

But then how would you view youtube videos and stuff that run on Flash?

---

### Post by Shazaam on 2009-06-29
Sorry folks for the small hijack-
> **caeroe said:**
> <snip>... unless kernel header updates break my wi-fi.

Have you tried dkms? Get it with Synaptic.
[http://linux.dell.com/dkms/manpage.html](http://linux.dell.com/dkms/manpage.html)

---

### Post by kickwin on 2009-07-03
As the OP mentioned, I thought it was a linux-wide issue but mine was not. I have a Dell Inspiron 1300 with Intel Graphics Card. The solution [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928") fixed my problem and now flash videos play seamlessly. It is just two lines of code and a very simple fix. 

Let me know if you guys need me to explain what I did. I am sorry I can not post a general solution as I am not an expert and did not understand how the fix works. But as I said, I would be more than happy to explain exactly what I did.

---

### Post by DrCraigis on 2009-07-08
Yes, please explain what you did to correct it. I have the same hardware specs and have choppy fullscreen playback. I went to the link but it was too confusing... what are the two lines of code?? I am totally new to Ubuntu and not technical but I at least know how to copy and paste! thanks

---

### Post by kickwin on 2009-07-08
> **DrCraigis said:**
> Yes, please explain what you did to correct it. I have the same hardware specs and have choppy fullscreen playback. I went to the link but it was too confusing... what are the two lines of code?? I am totally new to Ubuntu and not technical but I at least know how to copy and paste! thanks

Here is what I did (I am sorry it is not exactly two lines but is very simple. I was overblown by the relief when I got my videos working and used superlatives :p):

Type in terminal:
```
lspci -vvnn
```Scroll up to find the text "VGA compatible controller". Under this heading, you will find something like this 
> Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]You have to find the memory against 'prefetchable'. Note down the number (as you see in my case it was "c0000000"). 
```
cat /proc/mtrr
```You should see something like this.
> reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x040000000 ( 1024MB), size=  512MB, count=1: write-back
reg02: base=0x05f800000 ( 1528MB), size=    8MB, count=1: uncachable
reg03: base=0x0feda0000 ( 4077MB), size=  128KB, count=1: write-throughIf you have the same type of problem I had,then you should not see the line containing "reg........ base=0xc0000000........" (for your case instead of "c0000000" what you noted down as prefetchable memory from 'lspci -vvnn'). Now what you have to do is add this line to this list. To do this go back to terminal and type
```
sudo -s
```Remember to replace your prefetchable memory instead of "c0000000".
```
echo "base=0xc0000000 size=0x10000000 type=write-combining" > /proc/mtrr
```Now type 
```
cat /proc/mtrr
```and you should see the following line added.
> reg04: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combiningThe change will not be preserved when you reboot your PC, so do the following. But before that, make sure your videos play well after you did the above.
Now you have to add the same line you just added to /proc/mtrr to /etc/rc.local.
Go to terminal,type
```
nano /etc/rc.local
```Scroll down to the bottom and enter
```
echo "base=0xc0000000 size=0x10000000 type=write-combining" > /proc/mtrr
exit 0
```Press 'Ctrl+X' to exit and make sure you save your changes before you exit the editor.
That's all I did and my videos started running smoothly.

---

### Post by wo1fe on 2009-07-08
Kinda the same thing here i am new to ubuntu. i was having serious issues with windows vista 64bit (explorer.exe  would randomly crash and make me loose all data.). so i decided after looking at ubuntu for a few weeks (each day i liked it better and better during the demo). i decided to install it. not the issues that i am currently experiencing are that even though it recognises everything RAM,GFX Card, and such it is very laggy for response time and when going into day of defeat or watching full screen videos it gets very choppy as if the system cannot handle it. i have been searching for ways to fix this but most fixes are for people who have been running this system for quite awhle and know their way around. i do wish to learn the system but for now i need to know how to fix the current issues before i can even think of begining to learn it. the operating system just seems like it cannot handle anything as it is running right now.

System Specs

Mobo: ASUS M2A-VM
Processor: Dual Core 3.1 ghtz AMD Socket AM2
RAM: 8GB
HDD: 500GB SATA
OS: Ubuntu version 9.04.2 or soemthing like that.

please if anyone can help it would be greatly appreciated.

---

### Post by DrCraigis on 2009-07-08
It worked! Tested in Hulu and YouTube and there's no more choppy playback in fullscreen. Thank you so much, kickwin, for your help and instructions.

Wo1fe, try the solution above (#13) if you get good playback in the browser window but it goes choppy in fullscreen. I'm a "noob" but it is really simple.

thanks again!

---

### Post by supermikey on 2009-07-09
(#13):guitar: Dude sweet. It works flawlessly. Thank you.

---

### Post by wo1fe on 2009-07-09
tried it and it started taking forever to load videos when moving into full screen. here is what was in the terminal when looking for the number needed.

Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    Region 5: I/O ports at df00 [size=128]
    [virtual] Expansion ROM at fbf80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

i honestly have no idea what any of this means.

this is what i get after typing cat /proc/mtrr

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-back
reg03: base=0x0cff00000 ( 3327MB), size=    1MB, count=1: uncachable
reg04: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg05: base=0x200000000 ( 8192MB), size=  512MB, count=1: write-back
reg06: base=0x220000000 ( 8704MB), size=  256MB, count=1: write-back

started working after following the steps until i tried watching HQ videos. then even in the little screen it just became a blur. also when i went to save the files this is what it told me.

[error writing .etc/rc.local : no such file or directory]

---

### Post by cyrylski on 2009-08-05
kickwin - thanks you man, that saved me :)

still, it's damn annoying we still have to resort to some workarounds when using ubuntu, especially if it's for something as basic as flash (for me at least).

---

### Post by sandydoull on 2009-08-05
The fix stated above does not fix choppy playback on Acer Aspire One hardware, but I have finally found the fix, here's a link to the thread: [http://ubuntuforums.org/showthread.php?t=1111090&highlight=up_threshold](http://ubuntuforums.org/showthread.php?t=1111090&highlight=up_threshold). It involves adjusting something called up_threshold, if the entry doesnt exist in your ondemand script you can just add it here's the part you need to add: > for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
    do
        [ -f $CPU_THRESHOLD ] || continue
        echo -n 20 > $CPU_THRESHOLD
    done
I am using a value of 60, which gives me watchable fullscreen flash

---

