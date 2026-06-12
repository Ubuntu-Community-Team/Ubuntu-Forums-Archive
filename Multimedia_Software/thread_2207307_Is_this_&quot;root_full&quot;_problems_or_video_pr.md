---
title: "Is this &quot;root full&quot; problems or video problem ??"
date: 2014-02-23
forum: Multimedia Software
---

### Post by oygle on 2014-02-23
Booted up Ubuntu today and it just hung on "Checking battery status". I followed a few threads where similar problems and was able to get past the hang, but then everytime I rebooted after that , the msg "Low Graphics Mode". So, continued to read other posts and ran **startx**, which finally got me into Ubuntu but can only see desktop or use Nautilus. Obviously there are commands to get to the shell,etc.

As I was using Nautilus a message appears ..

> The volume "filesystem root" has only 0 bytes disk space remaining

Where do I start please ? is it video problems compunded by the low disk space ? I can only see "root" space if I use GParted or similar, but how do you drop down to shell,etc

---

### Post by papibe on 2014-02-23
Hi oygle.

A few ideas:
[LIST]
[*]If you have ssh server installed, try to ssh to the machine from another.
[*]Press Ctrl+Alt+F1 to try to get text mode login.
[*]Boot into recovery mode.
[*]
[/LIST]
The commands you need to run to confirm this are:
```
df -h
df -i
```
If any of those shows a % close to 100, your disk is almost full. If so, run this commands to gain enough space to recover your desktop:
```
sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by oygle on 2014-02-23
Thanks, that made 2Gb availabe, it was 100% full. Will reboot now and see what happens.

Well, it booted up just fine, thanks.  :)

I can see now how it became full. This thread - [http://ubuntuforums.org/showthread.php?t=2206856](http://ubuntuforums.org/showthread.php?t=2206856) about mounting an external disk. Somehow, part of the backup I did went to /media/externaldisk. I thought when you do a mount, it was like a symbolic link. That is, the files are only logically there, not physically there. But these files (over 6Gb) are in the /media path, when the external drive was where they were meant to go ??

Possibly I copied them there by mistake. Will delete them.

Thanks.   :D

---

