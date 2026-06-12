---
title: "Optical sound out put not enabled &amp; video problems"
date: 2008-08-28
forum: Multimedia Software
---

### Post by Kolobok01 on 2008-08-28
Hello every one. I'm new to Ubuntu and Linux. For past couple of days I was truing to configure Ubunto to work proper.

I'm using x64 bit edition 
:confused::confused:
I have “ASUS M2N32-SLI Deluxe Wireless Edition AM2” with “ADI AD1988B audio chipset”
And I'm using Optical out put for a Head set for gaming. But I'm not being able to enable it in Ubuntu. So if you can help me how to enable Optical audio out that will be grate.

The second problem I'm having is with Video I have Ati Radeon HD 2900XT and I have install new 8.8 drivers for it. I'm truing to run Steam under Wine.

So the problem I'm having is with screen contraption and dividing ti thousands of squares and shifting them all over  screen. 

I did follow instructions on inhalation from [URL="Optical sound out put not enabled & video problems"]http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide
[/URL]

:confused:

---

### Post by ToulCit on 2008-08-28
Hi,

here are instructions how to run steam under wine :

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

or if you want to do it the easy way, add this repository to your software sources:

first add the key, open the terminal and insert this line:

sudo wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

then add the repository:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

then upgrade wien to the newest version

sudo aptitude update && sudo aptitude upgrade

then type: wine iexplore.exe

soem software needs an internet browser.

when that's finished, install the steam.exe from the steam site.

then you should be ready to go.

for your audio problem:

go to alsa.org and see if your audio device is supported.

cheers

---

### Post by Kolobok01 on 2008-08-28
Thanks for your help.

I did fallow all you steps and i steel have problems with corruption of a screen. steam is fine but as soon as i try to lunch game it dos start game but screen is corrupted. 

About my audio card it works on my speakers i was wandering how can i enable optical out. The regular out works fine.

---

### Post by markbuntu on 2008-08-29
You can go here for some tips on setting up the ati graphics driver fglrx:


[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

