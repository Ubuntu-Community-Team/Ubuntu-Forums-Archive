---
title: "Need help installing edimax usb wifi driver!"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by noalternative on 2012-04-15
I am trying to install this on a lucid linx laptop.

It has linux instructions and says it is compatable with linux on the box but the instructions are fuzzy in some places.  I have cut and pasted them in the quote box.  1)I am not sure where the driver directory is.  My present wifi card is already at wlan0.  Can I make a seperate entry, say wlan1 or do I have to completely remove my present wifi card.  Should my wifi card at least be removed when I am configuring the driver.  Do I have to use the command line all the time or can I use gnome network manager applet, like with my present wifi pcmcia card.  I want to get rid of this card because I needed it for a usb expansion card bus pcmcia card I installed, so I bought wifi and bluetooth dongles.  

> RTL8192C USB Linux Driver
  Quick Installation Guide
    Software Package & Platform
           requirements

Software Package:
• 8192C linux driver (source code)
     - support 32bits linux kernel version 2.6
• 8192C documents
• wpa_supplicant software
    Software Package & Platform
           requirements
Platform requirements:

(1) PC-Based Linux platform (i386)

(2) 8192C USB Linux driver supports Linux kernel
    version
    : from 2.6.18 ~ 2.6.33
      HOW- TO: Setting up Linux
           environment
 - Demonstration based on Linux Fedora
  2.6.24

• Part 1: make 8192C USB Linux driver

(1) step1: uncompress the
  “rtl8192cu_linux_v2.0.xxxx.2010xxxx.tar.g
  z” file. (in “driver” directory)
  > tar zxvf rtl8192CU_linux_v2.0. 939.20100726.tar.gz
(2) step2: make 8192C USB driver module
  > make
(3) step3: clean the operation environment
   > ./clean
(4) step4: insert 8192C USB modules
  > insmod 8192cu.ko
• (5) step5: enable wlan0 interface
   > ifconfig wlan0 up
• (6) step6: setup IP address
   > ifconfig wlan0 192.168.1.100
•   Part 2: Site Survey & connect to AP
    without security

•    step1: Site Survey
    > iwlist wlan0 scan

•    (2) step2: Connect to AP
    > iwconfig wlan0 essid “xxx”
• Notes: connect to AP using "Network
  Manager" GUI utility
  – (a) Network Manager is a utility attempts to
   make use of wireless networking easy.
  – (b) please disable the “Network Manager”
   when using command-line method to connect
   to AP, because the “Network Manager” will
   conflict with the method of command line.

---

### Post by chili555 on 2012-04-15
> I am trying to install this on a lucid linx laptop.If you wanted to install the latest Ubuntu version 11.10, rtl8192cu is included by default. If this is not a realistic possibility, let's compile what you have. As a first step, install the prerequisites. Open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
```> can I use gnome network manager appletYes, certainly.> Should my wifi card at least be removed when I am configuring the driver. Not necessarily. We will get to a point where we're ready to stop using the PCMCIA and start using the USB; I'll prompt you to remove the PCMCIA when the time comes.> My present wifi card is already at wlan0. Can I make a seperate entry, say wlan1The driver install will take care of that for you. > (2) 8192C USB Linux driver supports Linux kernel
version
: from 2.6.18 ~ 2.6.33What kernel version are you running? Please run and post:```
uname -r
```

Let us know if an upgrade is easier or if we should proceed with what you have.

---

### Post by noalternative on 2012-04-15
> **chili555 said:**
>  what kernel version are you running? Please run and post:```
uname -r
```



I am running 2.6.32-33-386

Should I refrain from upgrading my kernel when I update to the latest lts?

---

### Post by chili555 on 2012-04-15
> Should I refrain from upgrading my kernel when I update to the latest lts?No; the latest LTS, 12.04 I believe, includes rtl8192cu by default so you should be all set. So, do you want to compile this or wait a few days for 12.04? It is scheduled for April 26.

This interesting thread may be helpful. Note they are talking about the *built-in* rtl8192cu, not the compiled as you may be doing here.

[http://ubuntuforums.org/showthread.php?t=1949810&highlight=8192cu](http://ubuntuforums.org/showthread.php?t=1949810&highlight=8192cu)

---

### Post by chili555 on 2012-04-15
Mrs. Chili and I are going out. In case you decide to compile, here are my instructions. Drag and drop the rtl8192CU_linux_v2.0. 939.20100726.tar.gz file from the CD to your desktop. Right-click it and select Extract Here. Open a terminal and do:

```
cd Desktop/rtl
```

Press Tab and the remainder of the long name will fill in automatically. Press Enter. Now do:

```
sudo su
make clean
make
make install
modprobe rtl8192cu
exit

```

Now does it work? Blink? Light up?? Remove the PCMCIA device and see if Network Manager sees your network and you can connect.

I'll check in this evening.

---

### Post by noalternative on 2012-04-15
Can I backport this driver.  I do not want to upgrade now!

---

### Post by noalternative on 2012-04-15
sorry

---

### Post by noalternative on 2012-04-15
triple posting.  something must be wrong with the forum.

---

### Post by chili555 on 2012-04-15
So did you compile it and install it? Does it work as expected?

---

### Post by noalternative on 2012-04-15
> **chili555 said:**
> So did you compile it and install it? Does it work as expected?

No, I am scared of the upgrade to 12.04 either way.  Is it possible to backport the driver from 12.04?

Is it possible to upgrade to 12.04 without upgrading my kernel?  I worry about the 3x kernel anyway, as my computer is a 2002 model, pentium 3 m, that I have given ram and harddrive upgrades.

---

### Post by chili555 on 2012-04-15
> Is it possible to backport the driver from 12.04?Not that I'm aware of. If you are concerned about the upgrade, why not run the live CD and try it? If it doesn't perform as you wish,then simply don't upgrade!

Since you have the driver from the device manufacturer, why not compile it and install it on your current Lucid install? If it works, you're all set. If not, we'll troubleshoot it together and do our very best to get it to work.

---

### Post by kurt18947 on 2012-04-16
I'm not sure which edimax adapter you're using.  I have the edimax 7811Un, the little bitty fella that uses the RealTek 8188Cus chipset. My (relatively) simple solution is to use RealTek's driver.  The built-in driver did not work for me.  The device is recognized but will not connect,  I kept getting the 'please enter your network password' endlessly. RealTek's driver includes an install script that has been perfect with Mint12 (based on ubuntu 11.10) and Ubuntu 12.04.  Here's RealTek's download page:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Scroll down to 'Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.2'.  This driver works with kernels up to the latest 12.04 - 3.2.0-23-generic. This is a terminal operation, I don't know that there's a GUI method. To use it I created a folder on my SUDO account's desktop.  Download the .zipped file and extract it to that newly created folder.  CD to that folder and you should find a few files, one of which is 'install.sh'. I just run the command
```
sudo bash install.sh
```.  There'll be two choices, something like

[LIST=1]
[*]8188CU
[*]8188DU
[/LIST]
type the number '1'.  It should run a minute or two, the blue light will flicker and life is good.  This procedure needs to be repeated as newer kernel versions are downloaded so keep the folder where you can find it.  I don't know if the same procedure works on other Edimax adapters but there should be no harm in downloading and extracting the appropriate file then see if there's an install script.

One thing I did have to do in Mint 12 was to blacklist the built-in driver. It was sort of confusing to me because it felt like I was blacklisting the driver the Realtek script created but nope, it worked fine.  The module shown in 'lsmod' is 8192cu.  The module I blacklisted was 'rtl8192cu' I think. I'm not using Mint12 right now so can't check.

---

### Post by noalternative on 2012-04-20
Thanks for all the help Chili and Kurt!  You both helped me, and were very nice!  It is up and working and the little bugger works several times better than my d-link dwl-630 pcmcia card.:guitar:

---

### Post by chili555 on 2012-04-20
Awesome! Glad it's working. Have fun!

---

