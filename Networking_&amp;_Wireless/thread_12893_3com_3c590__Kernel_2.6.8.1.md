---
title: "3com 3c590 / Kernel 2.6.8.1"
date: 2005-01-27
forum: Networking &amp; Wireless
---

### Post by traveler on 2005-01-27
Hi Community,

now after searching the web I could not find a successfull solution to my problem:
I've istalled Ubuntu Warty successfully on my Laptop (Thinkpad x20). After installation, where several updates were installed from the web (?) I booted into the GUI. Unfortunally I have no working Network now. 
I suspect Kernel 2.6.8 to not support the 3com card in the Notebook. Why? Well, when I issue 
lsmod I can see, that the 3c59x is loaded but not used. Another "hint" for the Kernel was, that after rebooting during system loadup I get a handfull of messages stating:
localhost kernel: eth0: command 0x5800 did not complete! Status=0xffff

Now I know that the Laptop is supportet by the complete Kernel 2.2.x and 2.4.x series since I use Slackware on that Laptop too.

Now my question is: is there anyone who could tell me how to get close to the problem? Or better: solve it :)

Take care
-traveler (from freezing cold Germany *shivvvver*)

[edit]
[http://lists.debian.org/debian-user/2004/09/msg03615.html](http://lists.debian.org/debian-user/2004/09/msg03615.html)
Seems to be a known (reported), but yet unsolved problem...
[/edit]

---

### Post by traveler on 2005-01-28
[QUOTE=traveler]Hi Community,

now after searching the web I could not find a successfull solution to my problem:
I've istalled Ubuntu Warty successfully on my Laptop (Thinkpad x20). After installation, where several updates were installed from the web (?) I booted into the GUI. Unfortunally I have no working Network now. 
I suspect Kernel 2.6.8 to not support the 3com card in the Notebook. Why? Well, when I issue 
lsmod I can see, that the 3c59x is loaded but not used. Another "hint" for the Kernel was, that after rebooting during system loadup I get a handfull of messages stating:
localhost kernel: eth0: command 0x5800 did not complete! Status=0xffff

Now I know that the Laptop is supportet by the complete Kernel 2.2.x and 2.4.x series since I use Slackware on that Laptop too.

Now my question is: is there anyone who could tell me how to get close to the problem? Or better: solve it :)

Take care
-traveler (from freezing cold Germany *shivvvver*)

[edit]
[http://lists.debian.org/debian-user/2004/09/msg03615.html](http://lists.debian.org/debian-user/2004/09/msg03615.html)
Seems to be a known (reported), but yet unsolved problem...
[/edit][/QUOTE]


OK. I solved it myself:
Version a: recompile the Kernel and EXCLUDE acpi support.
Version b: get the latest mm-patch, patch the Kernel, recompile it, be done.
Both variantes work fine - I used Version a because my Notebook doesn't support acpi at all :->

Cet la.

Regards
-traveler

---

### Post by class_A on 2005-02-01
[QUOTE=traveler]OK. I solved it myself:
Version a: recompile the Kernel and EXCLUDE acpi support.
Version b: get the latest mm-patch, patch the Kernel, recompile it, be done.
Both variantes work fine - I used Version a because my Notebook doesn't support acpi at all :->

Cet la.

Regards
-traveler[/QUOTE]Would you be able to provide a link to your kernel for me please?  I'm suffering the same problems, but I'm very much a n00b with kernel compiling, so a drop in replacement would be ideal :)

Cheers!
Alex

---

### Post by traveler on 2005-02-02
Cheers Alex,

now I found an easyer way to get rid of that "naughty" and buggy ACPI support:
boot with the following flags:
```
linux acpi=off
```
and implement that also into the grub-configuration:
```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.8.1-4-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda1 ro **acpi=off** quiet splash
initrd          /boot/initrd.img-2.6.8.1-4-386
savedefault
boot

```
That should do the job!

If you are realy interested in the ACPI-off Kernel I can only provide Kernel 2.6.10 - i486 plus all modules packaged nicly for Slackware (TM) Linux :)

Take care, and the best of luck
-traveler

Grub-HowTo:
[http://www.linuxorbit.com/modules.php?op=modload&name=Sections&file=index&req=viewarticle&artid=539&page=1](http://www.linuxorbit.com/modules.php?op=modload&name=Sections&file=index&req=viewarticle&artid=539&page=1)

---

### Post by class_A on 2005-02-06
traveler,

Many thanks!  acpi=off was all I needed :D

Alex

---

