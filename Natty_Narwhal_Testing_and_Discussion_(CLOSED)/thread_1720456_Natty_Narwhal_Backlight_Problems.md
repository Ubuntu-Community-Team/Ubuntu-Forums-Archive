---
title: "Natty Narwhal Backlight Problems"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by travissparks1307 on 2011-04-03
Greetings Forum!

I have recently downloaded the Ubuntu 11.04 Natty Narwhal Beta. It would probably work just fine, if not for the lack of back light.
When I load the disk, (I'm running from a Live CD) there is no boot splash, or anything. At first I thought I had a blank screen, but on closer inspection I realized that there was no back light! I know for a fact it's not my display, because it works just fine in Maverick Meerkat, (as well as Linux Mint 10 Julia). I have tried increasing screen brightness to no avail. I can't even see the screen unless I use a flashlight. Is this is a bug?

My computer is an Acer Aspire 5734Z notebook, with an Intel GMA 4500M graphics chipset. 

Don't tell me the problem is failing or buggy hardware either. I know better. Thank you all in advance.

---

### Post by Dutch70 on 2011-04-03
Looks like a bug...
[[COLOR="Red"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611")

You probably should have posted this in the Natty testing forum though.
I'm sure it will get moved there soon.

---

### Post by Elfy on 2011-04-03
moved

---

### Post by sanderd17 on 2011-04-03
I think I have the same problem:

Ahtec Laptop with an i3 processor (integrated graphical card) 4GB RAM and probably no other special things.

---

### Post by sanderd17 on 2011-04-03
It seems my problem is a bit worse, I started a new thread here: [http://ubuntuforums.org/showthread.php?p=10632946](http://ubuntuforums.org/showthread.php?p=10632946)

---

### Post by travissparks1307 on 2011-04-03
Sorry about posting in the wrong place. I just wanted to bring attention to it. For future reference, how do I submit suspected bugs?

---

### Post by cariboo on 2011-04-03
You can use **ubuntu-bug** to report bugs, you must have a launchpad account. Go [here]("https://launchpad.net") to create an account. Once you have an account, just open a terminal, or press Alt-F2 and type:

```
ubuntu-bug <package_name>
```

where <package_name> = the name of the package you are having a problem with.

---

### Post by anypundit on 2011-04-04
I have the same model laptop.  After applying the latest patch from the bug report above my screen now only shuts off for *25-30 seconds* before continuing to boot normally. Ugh.

---

### Post by saket3143 on 2011-04-05
I m using acer 4736z and was facing the same problems
after changing the kernel parameters my problem was solved
try adding the line
acpi_osi=linux
and the brightness goes back to normal 100% without any controls

---

### Post by poodoopealeoaph on 2011-04-07
I have the same issue and I have an emachines e725. I looked at the link above that said that it was a bug and when I checked the link out it was for the complete wrong issue. This issue is for <u>no backlighting</u>, not the issue with not being able to change screen brightness.... I would really like to find a fix for this soon because I really want to try out the new versions... I've already kicked regular ubuntu out of my life and if things don't shape up I will have to even get rid of kubuntu.. I'm really hoping I don't have to though.

---

### Post by waspbr on 2011-04-07
I had a similar issue on maverick with an hp laptop. I got it fixed by adding

```
nomodeset
``` 


to the boot line, it's worth  shot. 


gl

---

### Post by travissparks1307 on 2011-04-08
To saket3143,

You said try adding a line in order to fix the problem. Where do I add it? Is this an argument I pass to grub at boot? Is it a command? Please be a little more clear. :confused: 

If it's a grub line, I'll need instructions on how to do it. I'm not as familiar with grub as I am/was with LILO. Thanks in advance.

---

### Post by travissparks1307 on 2011-04-08
Okay so I've been playing with the boot options, nomodeset fixed the backlighting but uses GNOME instead of Unity. edd=on did nothing same story with acpi=off. I tried putting acpi_osi=linux at the end of the boot line but nothing.

I should point out that I did these using the daily build (04082011) and NOT Beta 1. I am downloading Beta 1 as I type this and will continue to work on it.

---

### Post by Buschbarber on 2011-04-08
I am not sure if this is a similar problem.

I just installed 11.04 X86 on an HP Pentium D 2Ghz machine. It is a 32bit machine. The install went fine. When I first opened FireFox, it defaulted to the size of half the screen. When I clicked on Maximize, the screen went completely White. When I clicked on Maximize, again, the window went to half screen and the text appeared again. I experimented with dragging the border of the window to the right and after 1/4", the window went White.

I got up this Am to find my Desktop all White. I could see the mouse, but clicking or hitting Enter on the Keyboard, did nothing. I hit Ctrl-Alt-F1 and it took me to Terminal. I did a Sudo Reboot and it rebooted to the Login screen. It sat there for a few minutes and then the display turned White, again.

I did not have this problem on my other machine with the 64bit install.

---

