---
title: "nVidia Issues After Upgrading to 11.04"
date: 2011-04-30
forum: Multimedia Software
---

### Post by altearius on 2011-04-30
Hello,

I recently upgraded from 10.10 to 11.04.  Prior to upgrading, my system was stable and worked well.  Now I am having graphic issues that prevent me from using the machine in a normal manner.

There are two symptoms.  First, my text console is unreadable.  Here is a picture of what my monitor looks like after booting.  You can't tell from the image, but that's a login prompt:

[IMG]http://chris.photobooks.com/Other/forumPosts/LinuxConsole.jpg[/IMG]

Secondly, X will not start at all.

I can SSH in to the box from a working machine, including X forwarding if that matters.  Since text-mode is borked, SSH is the only way I have to use the box.

I have been using the nVidia drivers, and they were working fine before the upgrade.

I have tried reinstalling nvidia-current.  This has not helped.  I have attached a copy of Xorg.0.log that shows the nvidia drivers failing: [ATTACH]190576[/ATTACH]

I have tried editing /etc/X11/xorg.conf to change "nvidia" to "nouveau"--this worked once.  The first boot of X after this change succeeded.  However, subsequent boots fail.  I have attached a copy of an Xorg.0.log that shows this failure: [ATTACH]190577[/ATTACH]

I have tried editing /etc/X11/xorg.conf to use the "nv" driver. This works, but is a suboptimal solution.  Sadly, booting X with the "nv" driver seems to have disabled Unity, and I'm not sure how to turn Unity back on.

The nvidia failure message instructs me to check my system's kernel log for more information:

```
~$ dmesg | grep nvidia
[   23.654236] nvidia: module license 'NVIDIA' taints kernel.
[   26.047433] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
```

Is this a known issue somewhere?  I've searched the forums and found a few other people having nVidia issues, but nothing exactly like mine.  What can I do to fix this?

---

### Post by cmargolin on 2011-04-30
I see the same thing with text mode starting after the initial BIOS screen, but my X session does start normally.

My machine is a few years old and has an nVidia GeForce 7300 LE with driver version 173.14.30.

---

### Post by 23dornot23d on 2011-04-30
Mine is [_[COLOR=Red]similar too[/COLOR]_]("http://i.min.us/in1SUW.JPG") ..... a Nvidia 9300 GS

Latest nvidia driver .... current .... 270.41.06

Going to the terminal Alt + F1 ........ and my monitor kicks out completely ......

```

keith@keith-Aspire-7730ZG:~$ dmesg | grep nvidia
[   16.780373] nvidia: module license 'NVIDIA' taints kernel.
[   17.889363] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.889376] nvidia 0000:01:00.0: setting latency timer to 64
keith@keith-Aspire-7730ZG:~$ 


```
But runs ok once in 3D mode ..... compiz etc works fine ..... and UNITY too ....

---

### Post by glapidus on 2011-05-01
I faced this problem yesterday night. The following helped me. I'm apologizing for being not fully exact - that's what I remember and now I'm far from my Ubuntu box. I remember that installed nvidia-current (recommended) from additional drivers  :
1. Reboot + "recovery" from grub - this somehow helped me to avoid the "ieroglif" screen (stupid , but it works). Do it again if it did not help   
2. Reboot normally , then Ctr+Alt+F1 to get text console.
3. sudo apt-cache search nvidia  - will return all nvidia drivers
4. sudo apt-get remove  nvidia-current  (or one suitable to you from the list ) 
5. Reboot 

Then I installed nvidia-173 and unity began to work, although the ieroglif screen still remains

---

### Post by altearius on 2011-05-01
Thanks, glapidus! Using nvidia-173 does indeed let me start X consistently.  I still have issues with a text-mode console, but it looks like that is a secondary problem.

---

### Post by matthewbpt on 2011-05-09
Hey guys, I have this problem too with my nVidia GeForce 9300 chip and have submitted a bug report. This card should work using nvidia-current, driver 270.41.06, without having to roll back to the OLD nvidia-173 driver. Go to [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/770559](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/770559) and put that the bug affects you too, this way it'll get noticed and we can use our cards to their full potential again ... Up to now the bug has been completely ignored.

---

