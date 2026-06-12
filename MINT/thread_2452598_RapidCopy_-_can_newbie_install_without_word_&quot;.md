---
title: "RapidCopy - can newbie install without word &quot;compile&quot;?"
date: 2020-10-25
forum: MINT
---

### Post by donjuane2 on 2020-10-25
Brand new to Linux, Ubuntu, Mint desktop.   

One goal for this new GUI Linux user is thinking with the full range of drive format types supported by Linux, I was hoping to do some mass-file copying from some backup hard drives to others I've collected over the years of taking photos.   On Windows I use FastCopy and via a search I found the Linux equivalent called RapidCopy:
[URL="https://github.com/KengoSawa2/RapidCopy"]https://github.com/KengoSawa2/RapidCopy

[/URL]What would be the shortest and easiest path for me to be able to use this tool my new "first ever Linux install" desktop?    Please understand that this is my first installation of Linux and it's takem me over a year of multiple tries just to finally discover how to install it, learning I needed to convert my disk from GPT to MBR, make all kinds of changes to my BIOS just to get both Mint and Windows working on the same machine, so if the only answer is beyond an elementary level like that, then I am sunk.   I was somehow able to figure out how to add one "app" off the terminal based install facility but I notice that RAPIDCOPY is not in the list of available apps.

Any help is appreciated and if anyone has RAPIDCOPY in a form where I just have to copy some files to install it, I should be set.   Doing things like compiling this code or re-compiling Linux is about 10 years off my base knowledge level but thanks to anyone who can add any insight.

---

### Post by howefield on 2020-10-25
Thread moved to the "*MINT*" forum.

---

### Post by SeijiSensei on 2020-10-26
The best Linux tool for mass file copying is called rsync. I run it from the command prompt, but there are graphical front ends for rsync as well like grsync.

---

### Post by oldfred on 2020-10-26
Best not to convert a MBR drive to gpt?
Windows only boots in UEFI mode from gpt.
Windows only boots in BIOS mode from MBR(msdos).

Ubuntu can be installed in UEFI mode to gpt, but also in BIOS mode to gpt. But you need to match mode of Windows.
Ubuntu will let you  install in UEFI mode to MBR, but that typically breaks a Windows install if on same drive.

I prefer to use rsync. Back in Windows days, I has a simple .bat file to copy my data.

I have never used this as I create my own scripts. But those who want a gui front end seem to like it.
[https://help.ubuntu.com/community/rsync#Grsync](https://help.ubuntu.com/community/rsync#Grsync)

Simple example  of a script.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first

---

### Post by TheFu on 2020-10-26
As SeijiSensei said, **rsync** is THE tool for mirroring files between 2 locations. 

Unix systems have been around a very long time. There are solutions, well-tested and optimized, for Linux that do pretty much everything.

rsync is one of those commands where seeing a few examples can clarify exactly how to use it. The general way to mirror entire directories is this:
```
$ rsynz -avz SOURCE TARGET
```

If you need more exact examples, google "rsync examples".

rsync is one of the top 5 greatest Unix inventions of all time, IMHO.
[LIST=1]
[*]Unix
[*]ssh (including scp, sftp, sshfs, and 20 other tools)
[*]rsync
[*]dd
[/LIST]

Almost every backup tool on all Unix systems are based off rsync and ssh, for example.  rsync is amazing.

---

