---
title: "Unity issue after updating natty"
date: 2011-01-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by LloydM999 on 2011-01-19
I updated my AMD x64 system from maverick to natty a month ago and have had no problems. Yesterday I noticed the apt repos were still pointing to maverick, so I changed them all to natty. I then got a "960 updates available" icon in the menu bar.
 
I started the update process, but it froze during the "Applying Changes" stage. After waiting overnight, I shutdown Ubuntu and retarted. Now after login I get a message saying something like
 
"Your hardware cannot run Unity, select the standard user session to get the traditional desktop."
 
After selecting "Switch User Session," the desktop comes up with no menu bars, just my Places. Configure Launcher does nothing.
 
How do I fix this problem, or do I have to reinstall natty?
 
 -Thanks! LloydM

---

### Post by Harry33 on 2011-01-19
> **LloydM999 said:**
> I updated my AMD x64 system from maverick to natty a month ago and have had no problems. Yesterday I noticed the apt repos were still pointing to maverick, so I changed them all to natty. I then got a "960 updates available" icon in the menu bar.
 
I started the update process, but it froze during the "Applying Changes" stage. After waiting overnight, I shutdown Ubuntu and retarted. Now after login I get a message saying something like
 
"Your hardware cannot run Unity, select the standard user session to get the traditional desktop."
 
After selecting "Switch User Session," the desktop comes up with no menu bars, just my Places. Configure Launcher does nothing.
 
How do I fix this problem, or do I have to reinstall natty?
 
 -Thanks! LloydM

About the upgrading process, how did you upgrade from Maverick to Natty, if the file etc/apt/sources.list still linked to Maverick repos?
You know this means you still had Maverick, not Natty.

Now after the overnigt upgrading, what does synaptic say when you open it?
Do you have any broken packages?
Are there still packages to be updated?
And yet, are all repos in /etc/apt/sources.list now linked to Natty?

---

### Post by LloydM999 on 2011-01-19
I updated to natty using [FONT=Lucida Console][SIZE=2]update-manager-d[/SIZE][/FONT] and followed the instructions for installing 11.04. I didn't see any errors, and afterwards [FONT=Lucida Console][SIZE=2]System > About Ubuntu[/SIZE][/FONT] said the version was 11.04.
 
I can't do anything on the desktop except browse my predefined Places (since I have no menu bars). I'l run [FONT=Lucida Console][SIZE=2]sudo apt-get check[/SIZE][/FONT] in text mode, and I'll also see if the repos are still set to natty.

---

### Post by LloydM999 on 2011-01-19
.

---

### Post by jerrylamos on 2011-01-19
>  
After selecting "Switch User Session," the desktop comes up with no menu bars, just my Places. Configure Launcher does nothing.
 
How do I fix this problem, or do I have to reinstall natty?
 
 -Thanks! LloydM

A lot of us see that.  Look at the thread "No Gnome panel" for suggestions.

If you get something on the screen besides the cursor, try right click anywhere to see if you can get a launcher.  If so, then try gnome-terminal for the command.  The object is to get enough of a top panel to enable logging out and logging back in, selecting classic desktop instead of ubuntu desktop which is in the throes of development...

Jerry



Jerry

---

### Post by LloydM999 on 2011-01-20
I solved the problem by running update-manager -d again. It said I needed to do a partial upgrade this time. Afterwards I could login to either Unity or classic desktop with no problems.

Now though, grub2 lists my Windows 7 loader twice...but that's another thread.

 -Thanks, LloydM999

---

### Post by garvinrick4 on 2011-01-21
# LloydM999 do not worry about the Windows 7 showing loader twice, one is boot, one is recovery and I have one in sda4 as full recovery image. Notice below sda1, sda2 and sda4
```
rick@rick-HP-G71:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 2.6.37-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.37-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
rick@rick-HP-G71:~$ 

```

---

### Post by LloydM999 on 2011-01-23
garvinrick4 -

 That command shows the first Windows 7 entry differently on my system, and neither is a recovery version:

menuentry "Windows 7 (loader) (on /dev/sda1)" {
...Linux entries...
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {

The first one (my default on timeout) still boots Windows OK, so it's just an annoyance.

 -Thanks, LloydM999

---

