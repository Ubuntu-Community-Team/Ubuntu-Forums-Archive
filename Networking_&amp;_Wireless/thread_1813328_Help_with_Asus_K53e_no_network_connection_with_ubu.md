---
title: "Help with Asus K53e no network connection with ubuntu 10.04"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by TiffanyElenbaas on 2011-07-27
I recently bought an Asus laptop and had a friend install ubuntu 10.04. After the install was complete I tried to connect to a network and there was no networks availiable. After some research time my friend said the i need network drivers to install in ubuntu. Now i am stuck and need help!

---

### Post by chili555 on 2011-07-27
What kind of network connection would you like to have, wired ethernet or wireless? Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by TiffanyElenbaas on 2011-07-27
I followed my friends directions and installed ndisgtk along with the drivers from windows that I found in my program files, but after selecting the inf files for the wireless and wired network connections ndisgtk displayed an error message saying 'invalid driver' - is this a glitch or are they actually invalid driver .inf files? I have tried finding drivers for Asus to no avail on the internet =(

---

### Post by chili555 on 2011-07-27
ndisgtk probably won't work for wired ethernet. .inf files can be invalid if they are for the wrong device or are not Windows *XP* drivers which are a requirement.

---

### Post by ramunaidu on 2011-07-27
hi this is ramu i am using asrock H61M-s mother board for ubuntu 10.04.3
network driver not installed i unable to install the network drivers pleease help me

---

### Post by TiffanyElenbaas on 2011-07-28
I have downloaded xp drivers and ndisgtk still says they are invalid - any way to manually install them?

---

### Post by chili555 on 2011-07-28
Please post:```
lspci -nn | grep 0280
ndiswrapper -l
```That's a lower-case L for 'list.' Thanks.

---

### Post by svenskmand on 2011-08-16
I was thinking about getting the Asus K53E, but I would like to know about its ubuntu compatability first, so could you make a short review maybe?

---

### Post by chili555 on 2011-08-16
> **TiffanyElenbaas said:**
> I have downloaded xp drivers and ndisgtk still says they are invalid - any way to manually install them?The answer has already been given:> ndisgtk probably won't work for wired ethernet. Also, in order to troubleshoot your ethernet, please open a terminal and:> Please post:
```
lspci -nn | grep 0280
ndiswrapper -l
```

That's a lower-case L for 'list.' Thanks. 

---

### Post by seandude on 2011-12-27
I'm actually in the same boat at the moment.  Just got an Asus K53e and am using a clean install of Ubuntu 10.04.  

[FONT="Courier New"]lspci -nn | grep 0280[/FONT]

outputs:

[FONT="Courier New"]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec;8176] (rev 01)[/FONT]

As for ndiswrapper, apparently it isn't installed by default.  

From what I've seen, there are a few fixes (the easiest of which is just to upgrade -- but I'm trying to stick with 10.04.  Any suggestions?

---

### Post by chili555 on 2011-12-28
> **seandude said:**
> I'm actually in the same boat at the moment.  Just got an Asus K53e and am using a clean install of Ubuntu 10.04.  

[FONT="Courier New"]lspci -nn | grep 0280[/FONT]

outputs:

[FONT="Courier New"]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec;8176] (rev 01)[/FONT]

As for ndiswrapper, apparently it isn't installed by default.  

From what I've seen, there are a few fixes (the easiest of which is just to upgrade -- but I'm trying to stick with 10.04.  Any suggestions?Here is a pretty good guide: [http://ubuntuforums.org/showthread.php?t=1700635](http://ubuntuforums.org/showthread.php?t=1700635)

---

### Post by seandude on 2011-12-28
The only problem is that I can't download *linux-headers-generic* or* build-essentials *.  The laptop that's giving me the trouble doesn't have *any* networking drivers installed.  

I've downloaded the driver onto my working laptop and if needed, can compile it, but I'm a little worried that it'll be compiled to run on this, the working laptop.

Both laptops are running the 2.6.32-33 kernel, but this one is i686, while the other (target laptop) is x86_64.  

Because my target laptop has no networking abilities, the only thing that I can think of is to transfer the * apt-get cache * from the working laptop into the target laptop; then use one of the apt-get options (*--no-install * maybe?) to get the list of dependencies I need for installing * linux-headers-generic * and *build-essentials *.  Then, on the working computer, download .debs the suggested packages, transfer them onto the target computer, and  install them.

How does that sound?

---

### Post by chili555 on 2011-12-28
> The laptop that's giving me the trouble doesn't have *any *networking drivers installed.No ethernet? That's odd.

I'm not at all confident that the build-essential and linux-headers will be consistent from i686 to x86_64. You could download the .debs _and all their dependencies_ from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Post back if you need assistance picking out what's needed.

---

### Post by seandude on 2011-12-28
> **chili555 said:**
> Post back if you need assistance picking out what's needed.


This is the first time I've done something on this level, so would you mind walking me through a bit?  Or at least how do I find the names of each package that I want?

Thank you for the help, by the way.  I really appreciate it.

---

### Post by chili555 on 2011-12-29
Start here: [http://packages.ubuntu.com/lucid/build-essential](http://packages.ubuntu.com/lucid/build-essential)

As you can see, build-essential requires dpkg-dev, g++, libc6-dev and make. You can click all those links and download the .deb to a folder on the other computer. Then go here: [http://packages.ubuntu.com/lucid/linux-headers-2.6.32-33-386](http://packages.ubuntu.com/lucid/linux-headers-2.6.32-33-386). Likewise, get the dependencies coreutils, libc6 and linux-headers-2.6.32-33. In all cases, be sure to get the i386 version.

Transfer the folder and packages to your computer with a USB key or similar and drag and drop it to your desktop. Then, in a terminal, do:```
cd Desktop/folder
sudo dpkg -i *.deb
```It could be that some of the .debs you downloaded themselves have unmet dependencies. Just go back and get them and follow the same process.

Good luck. I'm here for you!

---

### Post by seandude on 2011-12-29
> **chili555 said:**
> In all cases, be sure to get the i386 version.


The other computer is running x86_64.  Why would I use the i386 versions?

---

### Post by chili555 on 2011-12-29
> **seandude said:**
> The other computer is running x86_64.  Why would I use the i386 versions?My bad; I read too fast and made a mistake. For this:> while the other (***target laptop***) is **x86_64**. ...you need 64-bit. Sorry about my mis-step.

---

### Post by seandude on 2011-12-29
Alright, just wanted to make sure before I did anything.

[Edit]  Worked perfectly well.  Had a bit of trouble hunting down dependencies, but once that was taken care of, the driver installed without any trouble.  

For anyone else who's using a 2.6.32-33 kernel, like I am, be sure to run the wireless compatibility script.

Thank's for the help Chill.

---

