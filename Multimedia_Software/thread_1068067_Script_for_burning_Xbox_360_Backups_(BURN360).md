---
title: "Script for burning Xbox 360 Backups (BURN360)"
date: 2009-02-12
forum: Multimedia Software
---

### Post by ouija on 2009-02-12
Hello,

I am relatively new to Ubuntu (using for only 6 months or so) and I recently tried the process of burning some XBOX 360 backups (.iso) using Ubuntu.

I found an article online that informed me of the command line:
> growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd=IMAGE.000

Then all I did was replace the "/dev/dvd" with my burner's location (found in the "/etc/fstab" file) and provide the actual .iso name where the "IMAGE.000" text is.

This worked beautifully, but it was quite a pain trying to remember the entire command each time I wanted to burn a backup, and where you burn as much as I do, simplifying this process is a definite no-brainer!

So I went ahead and wrote a small script file which makes things a whole lot easier and works beautifully, and I thought I'd share it with you all.

All you need to do is save the attached file and ensure that you change the permissions to allow the script to execute as a program, then copy the file to the "/bin" folder and voila! EASE OF USE when it comes to burning your backups!

From there, all you need to do now is open the terminal and type:
> burn360.sh backup.iso

The only problem you may have is the default location for your system's dvd burner.  You can easily edit the script and change this location (which is currently set to "/dev/scd0") or if that is something you are not comfortable with, you can simply supply it in the command line when running the script. (works great if you also have more than one burning installed on your system)

for example, say your burner is located at /dev/dvdrom, you can run the script like such:
> burn360.sh backup.iso /dev/dvdrom

How great is that?? It's wicked awesome and you know it... hahaha. 
Pretty good for a guy who just started using Ubuntu (and Linux all together!)

Let me know your thoughts and if you find this script useful.

I'm even debating trying to configure some sort of "gui frontend" that will work with it... but that is going to take some time and I need to get learned in using Glade :p

Enjoy!

---

### Post by Opaw on 2009-02-28
Looks cool man, I will try it out next week when I get some more blanks in and I'll report back. :)

---

### Post by rahduke on 2009-11-26
works great thanks man! I was looking for a Nautilus script that did this, but this is just as good

---

### Post by Seitan420 on 2009-12-13
You could use this as a nautilus script
```
#!/bin/bash
gnome-terminal -x growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760  -dvd-compat -speed=4 -Z /dev/sr0="$1"
```

---

