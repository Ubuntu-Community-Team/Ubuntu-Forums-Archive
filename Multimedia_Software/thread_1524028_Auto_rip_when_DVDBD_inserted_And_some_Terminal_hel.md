---
title: "Auto rip when DVD/BD inserted? And some Terminal help"
date: 2010-07-04
forum: Multimedia Software
---

### Post by _Fordy on 2010-07-04
Rather than a very long explanation that I often do, I'll just launch into my questions. I think they'll make it clear what I am trying to achieve.

(BTW: I'm a new one..)

1) In Windows, I can easily create a .bat file that will run commands in Command Prompt, just in a text editor, and save it as .bat. How can I do this in Ubuntu, so that whatever commands will execute when the file is run?

2) How do you set a file to run when x event happens? In my current case, when a disc is inserted, I want to run a file.

3) Can anyone provide me with commands (and any applications necessary) to break encryption of a DVD (pref. BD too) and rip .iso to x folder, using the original DVD name as the name (ie. Italian_Job.iso)


I expect it's clear what I'm trying to do here... 

Even better for number 3 would be a window popping up prompting for user to insert a name for the created .iso


Thanks!!!

---

### Post by mc4man on 2010-07-04
For number 2 - one of a couple of ways
You can set the default action for various media in File management -> Media

Many ways to access - one is - 
```
nautilus-file-management-properties
```

Then on media of choice - in the dropdown -> 'Open with other application' -> use a custom command

For that you can either use a command that is suitable or point to location and or name of a script if that's the way to go for what you wish


Note - this is not an answer to question 3, just an example

Ex. for dvd's from any drive, no structure protection (or sp without huge # of unreadable sectors) using vobcopy to rip  to folder (VTDEO_TS

with a bin directory in home folder that's in path 
( mkdir bin and then restart

script in ~/bin named dvdrip1 that's executable
```
#!/bin/bash
gnome-terminal -e "vobcopy -v -m -F 16" /media/*
```

Then in file management add dvdrip1 to defaults for dvd video - screen 
Then inserting dvd video media in any dvd drive will run script automatically

---

### Post by ajgreeny on 2010-07-04
Ubuntu and linux do not use .bat files.  You probably need to look into and understand .sh (shell script) files instead.  Start here, though I don't think it's the way to do what you are asking about here.
[http://www.go2linux.org/starting-with-shell-script](http://www.go2linux.org/starting-with-shell-script)

---

### Post by _Fordy on 2010-07-04
> **ajgreeny said:**
> Ubuntu and linux do not use .bat files.  You probably need to look into and understand .sh (shell script) files instead.  Start here, though I don't think it's the way to do what you are asking about here.
[http://www.go2linux.org/starting-with-shell-script](http://www.go2linux.org/starting-with-shell-script)

That's exactly what I was after, thanks. I was aware that Linux doesn't use .bat files, just thought it's a no-brainer to have some method of running a set of pre-written commands in Terminal, so the answer is pretty much just .sh instead of .bat, and to "tell" Linux it's executable with chmod +x?

Thanks, Ollie.


Edit:
I came accross this, would it work?
```
dd if=/dev/sr0 of=/home/user/diskimage.iso
```

Does the "if=" account for if that drive is mounted/in use or does it mean something else, and this command would still have to be run every time a disc was inserted?

Edit2: Actually I just noticed the "of=" too, so I'm guessing "i" is input, and "o" is output. In from /sr0 and out to whatever.iso

It's a start, at least.

---

### Post by ajgreeny on 2010-07-05
You are more or less right about the **dd** command.

In linux everything is a "file", even whole disks are a file to linux, though they may contain other files, of course.

if = input file
of = output file

However, be careful with **dd**; if you get the "of" wrong, everything on that drive or partition will be gone and not easily recoverable.  **dd** will not simply add files to existing files on a partition.

---

### Post by _Fordy on 2010-07-06
> **ajgreeny said:**
> You are more or less right about the **dd** command.

In linux everything is a "file", even whole disks are a file to linux, though they may contain other files, of course.

if = input file
of = output file

However, be careful with **dd**; if you get the "of" wrong, everything on that drive or partition will be gone and not easily recoverable.  **dd** will not simply add files to existing files on a partition.


Ok, so how would I do this:

sudo dd if=/dvdpath/filename_of_dvd.iso of=/iso_lib/[filename_of_dvd].iso

where the filename on the output has changed automatically according to the filename of the original disc (sorry, file ;))?

---

### Post by ajgreeny on 2010-07-06
Sorry, but that's a bit beyond my knowledge.

---

### Post by mc4man on 2010-07-06
I would think dd is less than suitable for this though certainly can be used.
You should keep in mind the .iso is encrypted and dd is intolerant of read errors, intentional or due to physical reasons.
(you can add conv=noerror, but that may create playability issues and make for a slow rip if read errors occur.
> where the filename on the output has changed automatically according to the filename of the original disc

If you wanted to pursue you'll need to write a script to do this. you'd need something to retrieve the disk label, maybe lsdvd could do that part.
Ex
> 
doug@doug-desktop1:~$ lsdvd | grep "Disc Title:" | sed -e 's/\..*$//' | cut -b 13-
libdvdread: Using libdvdcss version 1.2.10 for DVD access
CHILDREN_OF_MEN

Personally I wouldn't bother - vobcopy works well for most disks, a VIDEO_TS is basically the same as an .iso (or turn it into.

Otherwise brasero and k9copy can rip to a decrypted .iso, if either can be automated I'm not sure  (don't have them installed

Edit: here's something very simple (maybe too so

```
#!/bin/bash
dd if=/dev/sr0 of=/home/[COLOR="Blue"]doug[/COLOR]/`lsdvd | grep "Disc Title:" | sed -e 's/\..*$//' | cut -b 13-`.iso
```

2nd edit:
Small note on above script - it is setting  /dev/sr0 for dd and assuming /dev/dvd for lsdvd.

That is not always the case, more often for multi-drive systems. Check with 
sudo lshw -C disk

If not correct then adgust in script/command, dd is obvious, for lsdvd you can add, Ex.
 `lsdvd [COLOR="Blue"]/dev/dvd1[/COLOR] | grep "Disc Title:" | sed -e 's/\..*$//' | cut -b 13-`

Or adjust/switch the /dev/dvd, /dev/cdrom link(s) in 
/etc/udev/rules.d/70-persistent-cd.rules

Most logical is dvd, cdrom with sr0; dvd1, cdrom1 with sr1

---

