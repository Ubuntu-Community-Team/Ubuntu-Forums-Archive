---
title: "FGLRX makes my Hardy crash"
date: 2008-04-25
forum: Multimedia Software
---

### Post by guruofquality on 2008-04-25
Hello,

Im down on my luck... :(

I have an upgraded install from gutsy to hardy. My machine is a 32bit with an ATI Sapphire X1550. 

I tried to install the fglrx with System->Admin->Hardware Drivers. I tried with all the guides on the internet. I tried manually, I tried apt sources, I tried removing every thing with fglrx from synaptic and starting again... 

But whenever I reboot my machine with fglrx in the xorg.conf, the thing gets through the ubuntu startup screen but seems to crash when X server tries to start. And I mean the whole PC crashes, I cant even ssh in. The only way to use my machine again is to boot it with the recovery kernel and run the xfix utility. 

I have the latest hardy installed, and the fglrx driver worked under gutsy. The kernel is 2.6.24-16-generic, 32 bit AMD athlon XP, wide screen lcd (if thats relevant)...

Whats wrong? What log files should I post? Can someone post their working fglrx xorg.conf for me to try out?

Thanks!

---

### Post by d-mart on 2008-04-26
Sorry kind of a noob, but i attatched my xorg.conf and I am using the flgrx driver.

Also I upgraded to Hardy today.  The one thing I had to do when I upgraded though was uninstall xserver-xgl because I needed it on Gutsy for compiz-fusion, but it just made my com crash in Hardy.  After I removed XGL things went much smoother.

FYI my graphics card is an ATI x300 

Hope this helps

---

### Post by SRTS on 2008-04-26
hi!

maybe my posting here is able to fix your issue:
[http://ubuntuforums.org/showthread.php?t=768066](http://ubuntuforums.org/showthread.php?t=768066)

later

---

### Post by guruofquality on 2008-04-26
I have no compiz or xserver-xgl installed. Thanks for the xorg.conf but my comp still crashes with it.

---

### Post by oasmar1 on 2008-04-26
I think i have the same error, and because i found it difficult explaining my exact problem i decided to record what happens and put on youtube.com.

[Link]("http://www.youtube.com/watch?v=lqRE4PQ0NU4")

Hardware:
AMD 64 3000+
ATi x1650 Pro, AGP
Biostar K8VGA-M Motherboard

(for more details ask)

The problem only started after installing the "propriety driver" which came up in the corner.

Usually when the screen goes my monitor gives the message "No Signal" but it doesn't in this instance. Also none of the commands Ctrl-Alt-Del/F1/Backspace work.

---

### Post by guruofquality on 2008-04-26
> **oasmar1 said:**
> I think i have the same error, and because i found it difficult explaining my exact problem i decided to record what happens and put on youtube.com.

[Link]("http://www.youtube.com/watch?v=lqRE4PQ0NU4")

Hardware:
AMD 64 3000+
ATi x1650 Pro, AGP
Biostar K8VGA-M Motherboard

(for more details ask)

The problem only started after installing the "propriety driver" which came up in the corner.

Usually when the screen goes my monitor gives the message "No Signal" but it doesn't in this instance. Also none of the commands Ctrl-Alt-Del/F1/Backspace work.
Yup, exactly my problem. I think the kernel is just crashing because I cant switch to terminal with ctrl+alt+fx or ssh in from another computer.

*If you do want to get your computer back, just boot into the recovery kernel and run xfix.

---

### Post by guruofquality on 2008-04-26
> **oasmar1 said:**
> I think i have the same error, and because i found it difficult explaining my exact problem i decided to record what happens and put on youtube.com.

[Link]("http://www.youtube.com/watch?v=lqRE4PQ0NU4")

Hardware:
AMD 64 3000+
ATi x1650 Pro, AGP
Biostar K8VGA-M Motherboard

(for more details ask)

The problem only started after installing the "propriety driver" which came up in the corner.

Usually when the screen goes my monitor gives the message "No Signal" but it doesn't in this instance. Also none of the commands Ctrl-Alt-Del/F1/Backspace work.
Yup, exactly my problem. I think the kernel is just crashing because I cant switch to terminal with ctrl+alt+fx or ssh in from another computer.

*If you do want to get your computer back, just boot into the recovery kernel and run xfix.

Good to know that Im not the only one!

---

### Post by oasmar1 on 2008-04-26
Thanks, I have recovered it, but that doesn't solve the driver problem. I hope they sort this out soon.

---

### Post by guruofquality on 2008-05-15
Ive been messing with this for a while... I reinstalled hardy from scratch. The computer just crashes when the fglrx driver is loaded. So, I dont know how to check any log files for failures...

 I have seen this problem in a few other posts. Does anybody know about this???

I have a Sapphire X1550. It crashes on hardy with the fglrx driver. It worked perfect in gutsy... Im sad

---

### Post by alecmg on 2008-05-30
nvm, I thought its the same issua as me, with x64+fglrx+4gb

---

### Post by Lundis123 on 2008-06-17
I have this problem too...on a MSI radeon X1650 pro 512mb AGP. I'm new to Linux so Ubuntu(8.04) is the first Linux version I've tried. What I'd like to ask is if it's worth degrading to gutsy just to make this work(if it works in gutsy, that is)? Or is there many useful features in HH that can't be found in gutsy?

---

