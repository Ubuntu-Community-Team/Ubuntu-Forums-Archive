---
title: "New Installation questions"
date: 2009-03-25
forum: Mythbuntu
---

### Post by Uberhoser on 2009-03-25
Hello All,

I am very new to MythBuntu and have a general question or three about the installation to my hard disk.

I have just wiped and reformatted my old pc's hard drive, and have booted from the MythBuntu 8.10 cd installer I created from the .iso file.

I get to the desktop where there are 2 icons, The Live CD Frontend and the Install Mythbuntu.

When I try to run the Install Mythbuntu, it asks for a password to preform administrative tasks, which I take is blank, since I have not set one.  I hit OK, and I see something flash on my screen (like a 1 inch high by 4 inch wide bar) for a millisecond, and then nothing.  

Now I am figuring that it is installing and I leave it alone, and wait.  How long should I wait for ?


Basically I am just trying to get it installed onto my hard drive, so when I boot the PC, it loads correctly instead of giving me the error No OS found.

---

### Post by Z0014ND3l2 on 2009-03-25
You might have tried this already and I just read your post wrong. But have you tried booting from the CD itself from the Boot Selection screen?

---

### Post by Uberhoser on 2009-03-25
Yes,  Yes I have :D.

I have the CD in the cd drive, and boot the pc.

I get the language selection to pop up and choose english.

I then see the Mythbuntu Name and logo and 5 options:

Mythbuntu Live Enviroment
Install MythBuntu
Check CD for Defects
Test Memory
Boot form first hard disk

I choose the Install MythBuntu, a window pops up with the installing Linux Kernel, and then I get the Mythbuntu Logo with a litle bar moving back and forth.

It finally finishes, and I now get a "Enter you r password to preform administrative tasks.  The application 'mythbuntu-startup --load' lets you modify essential parts of your system. 

I hit ok, the screen flashes for a sec and then I get the desktop.

 Up in the upper left corner of the desktop is the Application bar.  In the middle left are the 2 icons, The Live CD Frontend and the Install Mythbuntu.

Now as I understand by reading the manual " If you won't be needing anything
other than the installer, select the Install Mythbuntu option by selecting it via the up-down keys
and pressing enter. This option is particularly useful on memory limited systems that may not be able
to handle the entire live environment."  

Basically i have the installer loaded into memory, and I need to click on the "Install MythBuntu" Icon on the desktop to install it to the HD.  SO I go clicky it, get a pw box, and hit OK. And wait... and wait.. and wait.  I don't see any indication that anything is being installed.

---

### Post by murchball on 2009-03-25
When you boot from the CD, try 'Check CD for Defects'. You should not be getting a prompt for the administrative password.

---

### Post by Uberhoser on 2009-03-25
You sir or madam, are full of WIN !

Check finished: errors found in 1 files.

So I guess I have to burn another CD ?  (sighs)  I just used my last cd on it. pah !

---

### Post by boof1988 on 2009-03-25
> **Uberhoser said:**
> You sir or madam, are full of WIN !

Check finished: errors found in 1 files.

So I guess I have to burn another CD ?  (sighs)  I just used my last cd on it. pah !

I just wanted to post a little thing I learned recently...

If you want to check the integrity of the Mythbuntu CD (after it's burnt) without booting it, you can use the following method in terminal:

[LIST=1]
[*]cd into the cdrom's directory.
[*]Type:
```
md5sum -c md5sum.txt
```
-or-
```
md5sum -c md5sum.txt | less
```
-or-
```
md5sum -c md5sum.txt | grep "FAILED"
```
[*]Visually make sure that all files are checked "OK", or use grep or something.
[/LIST]

---

