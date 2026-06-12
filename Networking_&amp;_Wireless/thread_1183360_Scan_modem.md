---
title: "Scan modem"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by jimn1547 on 2009-06-10
NEED HELP SETTING UP UBUNTU 9.04   MODEM        DOWNLOADED GNOME NETWORK ADMIN             &   SCAN MODEM.........OPEN THE PACKAGE SAYS"READ ONLY" FILE                     INSTRUCTIONS SAYS TO COPY TO YOUR ACCOUNT WITH MCOPY a:scanModem.gz                      
                             

                               CAN SOMEONE SIMPLIFY   THIS TO HELP ME GET GOING?:(

---

### Post by jjalocha on 2009-06-12
Hmmm... your post is quite hard to understand. This should help you with the first step (find your modem information):

[https://help.ubuntu.com/8.04/internet/C/modem-identify.html](https://help.ubuntu.com/8.04/internet/C/modem-identify.html)

If you need help, please try to explain exactly what you did/tried, and what happened wrong.

And please don't use ALL UPPERCASE TEXT. It's considered rude behaviour in internet customs! 

-Good luck!

---

### Post by jimn1547 on 2009-07-25
downloaded scanModem  put on floppy   double clicked package and the install manager won't come on.....opens saying "read only file"

---

### Post by lswb on 2009-07-25
Are you referring to the scanmodem program from this site?

[http://www.linmodems.org/](http://www.linmodems.org/)

Follow the directions you find there. No need for a floppy.

---

### Post by jimn1547 on 2009-07-26
Had to download on Windows computer ,put on floppy and put in Ubumtu computer.  Put in home file,open terminal: says all commands are not?           All 3 of the commands I type in says bad command.                 I understand that this file has to be changed to work.    Directions to do this are Not Clear ....assuming we know more than we do.:P

---

### Post by jjalocha on 2009-07-26
jimn, I think, I understand why and how you used a floppy drive to transfer the scanModem.gz file to your home directory in your Ubuntu install.

From your post, it is absolutely unclear what you tried to do, and what went wrong.

Following the instructions on the link I gave you, you, I guess you finished step 2, and are trying to accomplish step 3.

Please open a terminal (Applications &#8594; Accessories &#8594; Terminal), and enter the first line from the instructions:
```

gunzip -c scanModem.gz > scanModem 

```
And press enter. If everything goes well, this shouldn't give any output at all. If this gives output, please post it here.

Now, proceed with each line of step 3 in the link. If you encounter problems, please post *exactly what you did*, and what output you got.

There are many people in this forum willing to help, but we need to know what you are doing, and what is going wrong.

Good luck,
-Jerzy

---

### Post by jimn1547 on 2009-07-26
I opened floppy on desktop,           shows" box"            now what do I do ?      I don't understand how you install it.........                             :confused:

---

### Post by jjalocha on 2009-07-26
[LIST=1]
[*]You have to copy the 'scanModem.gz' file that you downloaded and copied to your floppy disk *to your computer*.
[*]You have to open a *terminal* at the location where you copied your file.
[*]You must type the commands from the link in my first post in this terminal.
[/LIST]

Tell us your results.

If you have trouble performing basic tasks such as copying/opening files, or opening a terminal, perhaps you should read some introductory documentation, such as the following free books:

[LIST]
[*] [The Linux Starter pack]("http://www.tuxradar.com/linuxstarterpack")
[*][Ubuntu Pocket Guide and Reference](" http://www.ubuntupocketguide.com/")
[/LIST]

---

### Post by jimn1547 on 2009-07-26
Ubunta 9.04                 coppied to home folder.....opened terminal........typed:gunzip-c  scanModem.gz>scanModem...........      bash:gunzip-c:command not found:(

---

### Post by martinbaselier on 2009-07-26
You need to have a space after gunzip

---

### Post by jimn1547 on 2009-07-26
:DThat's it!!!!!   I didn't leave spaces in some of it.  Thanks to everybody!   I can't wait to leave windows and have a great new operating system .

---

### Post by jjalocha on 2009-07-26
Well, I'm really glad, this helped you.

If you need anything else, just remember to ask in the forums, and good luck!

---

### Post by jimn1547 on 2009-07-29
Now that I have the file Modem Data txt         -sent to [email]discuss@linmodems.org[/email]    for drivers.........mail keeps coming back              :(

---

