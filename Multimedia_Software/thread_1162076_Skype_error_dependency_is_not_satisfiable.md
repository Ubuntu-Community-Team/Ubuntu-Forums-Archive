---
title: "Skype error: dependency is not satisfiable"
date: 2009-05-17
forum: Multimedia Software
---

### Post by mack27 on 2009-05-17
Hi all,
I have just reinstalled Ubuntu on my laptop (before it ran within Windows, now it's installed separately) and I wanted to install Skype, but after I download the file (Skype 2.0 for Linux) and double-click on it I get this info: Error: dependency is not satisfiable: libqt4-core. Before, when Ubuntu was an application within Windows, I had Skype but the mike wasn't working. Now I can't get to install the programme. Can you give me any hints what to do?

Many thanks.

---

### Post by Nasaki on 2009-05-17
Have you tried:
```
sudo aptitude install libqt4-core libasound2 libqt4-gui libstdc++6
```

---

### Post by mack27 on 2009-05-17
tired it. no packages were installed or upgraded.

---

### Post by Nasaki on 2009-05-17
How did you install Skype? Did you use their repository?
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```
If not try adding this to "Software Sources"

---

### Post by mack27 on 2009-05-18
well, i downloaded the install package from the skype website. but actually, after (lots of) updates for the system were performed (i had just reinstalled ubuntu then) i was able to install skype, so i suppose it was too soon after reinstalling the system itself. cheers :D

---

### Post by Francewhoa on 2010-03-05
[SIZE=2]The latest Skype Version 2.1.0.81 (skype-ubuntu-intrepid_2.1.0.81-1_i386.deb) does NOT work on Ubuntu 8.04.4. There is an issue from Skype's end. They will fix in future versions.[/SIZE]
 
 [SIZE=2]**The previous Skype version works. It isn't available on Skype site though. But you can download it from  **[/SIZE] 
 [SIZE=2][http://code.google.com/p/ubuntuchina/downloads/detail?name=skype-debian_2.0.0.72-1_i386.deb&can=2&q= ]("http://code.google.com/p/ubuntuchina/downloads/detail?name=skype-debian_2.0.0.72-1_i386.deb&can=2&q=")
[/SIZE]
 [SIZE=2]or[/SIZE]
  
 [[SIZE=2]http://www.wuala.com/TaxiDriver/Linux-Distributionen/skype-debian_2.0.0.72-1_i386.deb?lang=en[/SIZE]]("http://www.wuala.com/TaxiDriver/Linux-Distributionen/skype-debian_2.0.0.72-1_i386.deb?lang=en")
 
 [SIZE=2]Right click on file. [/SIZE][SIZE=2]
[/SIZE]
 [SIZE=2]Select OPEN WITH GDEBI PACKAGE INSTALLER option.[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]Follow instructions on screen.[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]Enjoy Skype.
[/SIZE]

---

### Post by Volomike2 on 2010-03-09
I got it to work on Ubuntu 8.04.4 with Skype 2.1 Beta **static**, but it has an annoying bug that I have listed here:

[http://ubuntuforums.org/showthread.php?p=8940386#post8940386](http://ubuntuforums.org/showthread.php?p=8940386#post8940386)

The problem with the previous version skype-debian_2.0.0.72-1_i386.deb is that the screensharing feature won't let you have a resizable screen, and screensharing has become important for me and my clients.

---

### Post by arno77 on 2010-05-03
> **Onopoc said:**
> [SIZE=2]The latest Skype Version 2.1.0.81 (skype-ubuntu-intrepid_2.1.0.81-1_i386.deb) does NOT work on Ubuntu 8.04.4. There is an issue from Skype's end. They will fix in future versions.[/SIZE]
 
 [SIZE=2]**The previous Skype version works. It isn't available on Skype site though. But you can download it from  **[/SIZE] 
 [SIZE=2][http://code.google.com/p/ubuntuchina/downloads/detail?name=skype-debian_2.0.0.72-1_i386.deb&can=2&q= ]("http://code.google.com/p/ubuntuchina/downloads/detail?name=skype-debian_2.0.0.72-1_i386.deb&can=2&q=")
[/SIZE]
 [SIZE=2]or[/SIZE]
  
 [[SIZE=2]http://www.wuala.com/TaxiDriver/Linux-Distributionen/skype-debian_2.0.0.72-1_i386.deb?lang=en[/SIZE]]("http://www.wuala.com/TaxiDriver/Linux-Distributionen/skype-debian_2.0.0.72-1_i386.deb?lang=en")
 
 [SIZE=2]Right click on file. [/SIZE][SIZE=2]
[/SIZE]
 [SIZE=2]Select OPEN WITH GDEBI PACKAGE INSTALLER option.[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]Follow instructions on screen.[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]Enjoy Skype.
[/SIZE]

This was of really great help. Works perfectly. Thanks!

---

### Post by lisar915 on 2010-05-03
Hi,

I followed Onopoc's advice and I was able to finally install Skype.  However, when I try to sign up with a user name, I got an error message saying I couldn't be signed up due to a network problem, and to check my network configuration.  Does it have anything to do with the fact that I have wireless internet access? 

Does anyone know what network settings I need to adjust to be able to sign up with Skype?  Thanks.

Lisa

---

### Post by Linuxforall on 2010-05-03
Please use Skype beta 2.1 from skype site, the older medibuntu one doesn't work with Lucid.

---

### Post by firebrick on 2010-05-30
Thanks Onopoc there is still a problem with the latest skype software your link to the older version solves the problem and just what i need.

---

### Post by arno77 on 2010-08-23
> **Onopoc said:**
> [SIZE=2]The latest Skype Version 2.1.0.81 (skype-ubuntu-intrepid_2.1.0.81-1_i386.deb) does NOT work on Ubuntu 8.04.4. There is an issue from Skype's end. They will fix in future versions.[/SIZE]
 
 [SIZE=2]**The previous Skype version works. It isn't available on Skype site though. But you can download it from  **[/SIZE] 
 [SIZE=2][http://code.google.com/p/ubuntuchina/downloads/detail?name=skype-debian_2.0.0.72-1_i386.deb&can=2&q= ]("http://code.google.com/p/ubuntuchina/downloads/detail?name=skype-debian_2.0.0.72-1_i386.deb&can=2&q=")
[/SIZE]
 [SIZE=2]or[/SIZE]
  
 [[SIZE=2]http://www.wuala.com/TaxiDriver/Linux-Distributionen/skype-debian_2.0.0.72-1_i386.deb?lang=en[/SIZE]]("http://www.wuala.com/TaxiDriver/Linux-Distributionen/skype-debian_2.0.0.72-1_i386.deb?lang=en")
 
 [SIZE=2]Right click on file. [/SIZE][SIZE=2]
[/SIZE]
 [SIZE=2]Select OPEN WITH GDEBI PACKAGE INSTALLER option.[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]Follow instructions on screen.[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]Enjoy Skype.
[/SIZE]

Hi Onopoc.

Just wanted to let you know that was very useful for me. Thanks a lot!

---

