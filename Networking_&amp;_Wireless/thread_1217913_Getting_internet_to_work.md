---
title: "Getting internet to work"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by riaanlouw on 2009-07-20
I am a new user to ubuntu and just uploaded Ubuntu on my HP Pavillion Dv5000 Laptop. I now however have the following problem:
 
# I've got the Vodacom/Vodafone K3565-Z wireless internet connection which works through my flash drive...Ubuntu doesn't seem to pick up the device so that i may download the VCMlite.exe file that installs the software to work the device!!
 
Is there anyway i can fix this problem or do i have to start using windows again just to be able to browse the internet!! Please help!!:(

---

### Post by RikoW on 2009-07-20
Hi:)

I have the same device and had a hard time to get it to work. What worked for was was to install the latest version of the vodafon-mobile-connect software from here:

[https://forge.betavine.net/frs/?group_id=12]("https://forge.betavine.net/frs/?group_id=12")

(works with any other modile network provider, too, not just vodafon).

This seems to install all the right drivers, too. After that the stick would be recognized and switched to modem mode properly and network manager picks it up and starts the wizard which lets you configure your network. You don't actually need to use the vodafone-mobile-connect software.

Cheers,
     Riko

---

### Post by riaanlouw on 2009-07-23
> **RikoW said:**
> Hi:)

I have the same device and had a hard time to get it to work. What worked for was was to install the latest version of the vodafon-mobile-connect software from here:

[https://forge.betavine.net/frs/?group_id=12]("https://forge.betavine.net/frs/?group_id=12")

(works with any other modile network provider, too, not just vodafon).

This seems to install all the right drivers, too. After that the stick would be recognized and switched to modem mode properly and network manager picks it up and starts the wizard which lets you configure your network. You don't actually need to use the vodafone-mobile-connect software.

Cheers,
     Riko
Hey Riko, 
 
I am really beginning the whole linus thing so i'm really a NOVICE and don't always understand the "tech-talk", but i'm learning fast. I tried you're downloading tips, but found the next error messages after i entered the following: " sudo dpkg -i usb-modeswitch_0.9.4-1_i386.deb sudo dpkg -i vodafone-mobile-connect_1.99.17-8_all.dep"
 
[FONT=Times New Roman][SIZE=3]dpkg: error processing usb-modeswitch_0.9.4-1_i386.deb (--install):[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] cannot access archive: No such file or directory[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dpkg: error processing sudo (--install):[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] cannot access archive: No such file or directory[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dpkg: error processing dpkg (--install):[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] cannot access archive: No such file or directory[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dpkg: error processing -i (--install):[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] cannot access archive: No such file or directory[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dpkg: error processing vodafone-mobile-connect_1.99.17-8_all.deb (--install):[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] cannot access archive: No such file or directory[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Errors were encountered while processing:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] usb-modeswitch_0.9.4-1_i386.deb[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] sudo[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] dpkg[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] -i[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Nimbus Roman No9 L] vodafone-mobile-connect_1.99.17-8_all.deb[/FONT][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please help!!![/SIZE][/FONT]

---

### Post by riaanlouw on 2009-07-23
> **RikoW said:**
> Hi:)

I have the same device and had a hard time to get it to work. What worked for was was to install the latest version of the vodafon-mobile-connect software from here:

[https://forge.betavine.net/frs/?group_id=12]("https://forge.betavine.net/frs/?group_id=12")

(works with any other modile network provider, too, not just vodafon).

This seems to install all the right drivers, too. After that the stick would be recognized and switched to modem mode properly and network manager picks it up and starts the wizard which lets you configure your network. You don't actually need to use the vodafone-mobile-connect software.

Cheers,
     Riko
Hey, 
 
When i'm trying to install the "vodafone-mobile-connect_1.99.17-8_all.deb" file it gives me the following error message on ubuntu:
 
[COLOR=red]**Error: Dependency is not satisfilable: python-crypto**[/COLOR]
 
What does this mean and how do i fix this?

---

### Post by Kyluke on 2009-07-23
Download python-crypto and install it.
A simple google search should do the trick.
remember to add details of your Distro version (Jaunty Jackalope etc)

---

### Post by RikoW on 2009-07-23
> **riaanlouw said:**
> Hey, 
 
When i'm trying to install the "vodafone-mobile-connect_1.99.17-8_all.deb" file it gives me the following error message on ubuntu:
 
[COLOR=red]**Error: Dependency is not satisfilable: python-crypto**[/COLOR]
 
What does this mean and how do i fix this?

Hi again,

the missing dependency I would just install via Synaptic Package Manager or in a terminal doing

```
> sudo apt-get install python-crypto
```

In addition, I suggest to install the very latest version of vodafon-mobile-connect:

[https://forge.betavine.net/frs/download.php/552/vodafone-mobile-connect_2.10.01-1_all.deb]("https://forge.betavine.net/frs/download.php/552/vodafone-mobile-connect_2.10.01-1_all.deb")

This is the one I used and it works.

Cheers,

               Riko

---

### Post by st0nes on 2010-02-25
I've tried installing this, but I get:-

Error: Dependency is not satisfiable: ozerocdoff

I have installed the latest version of ozerocdoff from the site, but the error message won't go away.

---

