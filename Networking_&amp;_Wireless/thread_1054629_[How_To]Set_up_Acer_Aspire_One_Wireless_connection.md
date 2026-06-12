---
title: "[How To]Set up Acer Aspire One Wireless connection"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by 5BallJuggler on 2009-01-29
This is a basic step by step to getting the AspireOne wirelessly connected.
It uses the **AR242x 802.11 Wireless PCI Express Adapter**

**Prerequisites**
Ubuntu installed and running
a wired internet/ethernet connection that is also running

firstly enable the linux-backport package.

Open a terminal and type
[B]
gksu gedit /etc/apt/sources.list
[/B]
Remove # sign in front of the lines that state:
[B]#deb http//gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
#deb-src http//gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse[/B]


Close the file, you will be asked if you want to save it, click on "Save"

Then run the following in the terminal:

[B]sudo aptitude update

sudo aptitude install linux-backports-modules-$(uname -r)[/B]

This should then install the ath5k driver for you (which is the actual name of the driver you are going to use).

**sudo modprobe ath5k**

Check if the driver is loaded with

**sudo lshw -C network**

Reboot your system, you should have wireless connection established

if this did not work open a terminal and type

**gksu gedit /etc/modprobe.d/blacklist**

Add the lines

[B]#To enable use of Atheros Wireless Controller
blacklist ath_pci
blacklist hal_pci[/B]

Close and save, reboot and you should be away

[B][COLOR="Red"]Be aware that when the Linux kernel is updated the connection may stop working, this happened to me, the easiest way round it is to default boot the old kernel that you know works.
If anyone as any ideas on how to prevent this from happening, i'll gladly update the tutorial[/COLOR][/B]

It seems that the latest kernel is a bit duff in the Atheros stakes, i've removed **linux-restricted-modules-2.6.27-11-generic(2.6.27-11.16)** from the package manager.
i've also added enabled ath5k to boot on start up

Open a terminal and type 

**gksu gedit /etc/modules**
add **ath5k** to the bottom of the list and then close

reboot and see what happens, mine is working now, I know others aren't so lucky


*Thanks to kevdog for starting the tutorial ([http://ubuntuforums.org/showthread.php?t=1052636](http://ubuntuforums.org/showthread.php?t=1052636) post5)*

---

### Post by RealGeorgeW on 2009-02-01
Appears to be working. Thank you.

---

### Post by deeejz on 2009-02-16
how do i enable the linux backport package? I forgot to enable it and did everything else you said and apparently it didn't work, do i have to erase what i did?

---

### Post by 5BallJuggler on 2009-02-17
Open a terminal and type

**gksu gedit /etc/apt/sources.list**

Remove # sign in front of the lines that state:
#deb http//gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
#deb-src http//gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse


Close the file, you will be asked if you want to save it, click on "Save"

---

### Post by wwotl on 2009-03-08
Yay, it worked! Thank you!  :)

---

### Post by scott1541 on 2009-04-07
Hi, i have a very similar problem with my sony Vaio (if not the same), and i need some information and help with this stuff (i'm new to ububtu)
Firstly  -  WTF is a terminal and how do i open one?

---

### Post by spursncowboys on 2009-04-08
The terminal is like dos. if you go to applications and then accessories. then, for mine, it is the seventh down called terminal. click on that. I am pretty new and that is all I know so far. from there you type all the commands he is talking about. 

I have a problem. my source list doesn't have
#deb http//gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

I took out the # from the second one. 
 When i redid gksu gedit /etc/apt/sources.list it gave me:
i/o error: no such file or directory (x2)
then
err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
    Could not resolve 'us.archive.ubuntu.com' (x21)

---

### Post by jokei on 2010-06-15
On the line "Remove # sign in front of the lines that state:" - I take  it you're adding these to the repositories?  I've tried doing this, but  got a nasty error, one which wouldn't let me go back into them to edit  (I might have made a typo) and was wondering how up to date those  repositories were?

---

### Post by shokalabutcha on 2011-06-14
Hi,

I had a similar problem. Whenever I did "rfkill unblock all", my wireless would go from 
Soft blocked: Yes
Hard blocked: No

to 

Soft blocked: No
Hard blocked: Yes

Tantalizing, isn't it? In the end, I created the following script as a (barely acceptable) solution:

sudo rmmod -f ath5k
sudo rfkill unblock all
sudo odprobe ath5k

I hope this script helps someone. If anybody knows how to make this permenant, that will be much appreciated.

I am using a Natty Narwhal, (Ubuntu 11.04) running on Fujitsu Siemens Amilo PA3515 with an Atheros AR5001 wireless module.

Hope this helps,
Shoka

---

