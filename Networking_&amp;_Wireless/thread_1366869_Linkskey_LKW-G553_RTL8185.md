---
title: "Linkskey LKW-G553 RTL8185"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by Powerman2442 on 2009-12-28
Okay, I posted a topic months about about my Linkskey (not Linksys) LKW-G553 wireless nic. I never did get it up and running with Linux and decided to switch back to Windows. Now I am back with only Linux (no dual-boot), so I have to try to get this card working again. 

The card I bought can be found [here]("http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=3350640&sku=L70-1034&srkey=Linkskey%20LKW-G553"). I bought it on sale for like $6.99 and was told it would work with Linux out of the box, which it doesn't.

When I type "lspci" in terminal the card is detected, but I can't find anything to connect to under my network manager.

Code output: "00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)"

I am currently running Ubuntu 8.04 LTS (Hardy). Has anyone else fixed this problem? I couldn't find anything of extremely helpful after searching "RTL8185" on the forums and Google. Oh, the wireless nic does come with a driver CD that has drivers for Widnows, Mac, and Linux. The Linux drivers never work though. Maybe I am doing something wrong?

Is there any other information anyone might need to know to help me?

---

### Post by Project PWNED on 2009-12-28
A solution offered appears here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I've never done a driver through ndiswrapper, but since it's Ubuntu's Help area it shouldn't be a problem

Actually, just found this: 

[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

This is another solution

---

### Post by Project PWNED on 2009-12-28
Actually, according to Linkskey, the chipset is Marvel

> The LKW-G553 and LKW-G651 are using Marvell chipset.
The LKW-G750 Rev.A is using SIS chipset and Rev.B is using ZyDAS chipset.

Sorry. Ndiswrapper looks like the only solution but I don't know why the Aircrack people are wrong.

---

### Post by Bucky Ball on 2009-12-28
> **Project PWNED said:**
> A solution offered appears here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I've never done a driver through ndiswrapper, but since it's Ubuntu's Help area it shouldn't be a problem

Actually, just found this: 

[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

This is another solution

Yeeks!! AVOID ndiswrapper at all costs unless you specifically know your card will ONLY work with that (unlikely). It is pretty much superceded. 

Make sure you have an ethernet cable plugged in and get online. Get updates. Open synaptic package manager and install 'ubuntu-restricted-extras'. Go to System->Admin->Hardware Drivers and see if you have a restricted driver disabled for the card.

Open a terminal and run this command:

```
lspci
```Near the bottom you will find your cards EXACT chipset which will remove any doubt. Look for something containing **RTL8185** or similar. If it is, that is pretty easy and shouldn't require ndiswrapper at all so not sure where that info came from. Get you updates with an ethernet cable. ****

---

### Post by Project PWNED on 2009-12-28
Linkskey isn't even mentioned on [http://linux-wless.passys.nl](http://linux-wless.passys.nl) and this site has every vendor/chipset on it. I always check this site then Aircrack's. IMHO, ndiswrapper seems like the only way unless you want to drop $10 on a TP-Link TL-WN321G from Amazon.com

---

### Post by Powerman2442 on 2009-12-29
> **Bucky Ball said:**
> Yeeks!! AVOID ndiswrapper at all costs unless you specifically know your card will ONLY work with that (unlikely). It is pretty much superceded. 

Make sure you have an ethernet cable plugged in and get online. Get updates. Open synaptic package manager and install 'ubuntu-restricted-extras'. Go to System->Admin->Hardware Drivers and see if you have a restricted driver disabled for the card.

Open a terminal and run this command:

```
lspci
```Near the bottom you will find your cards EXACT chipset which will remove any doubt. Look for something containing **RTL8185** or similar. If it is, that is pretty easy and shouldn't require ndiswrapper at all so not sure where that info came from. Get you updates with an ethernet cable. ****

I posted the output on the "lspci" command on my first post. Here is exactly what shows in terminal.

"derek@derek-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
00:0b.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
00:0d.0 Communication controller: ESS Technology ES2898 Modem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
derek@derek-desktop:~$"

Also, I've gone to "Hardware Drivers" and the only thing available is for my GeForce2 MX 400. Everything graphics wise works fine so I don't plan on enabling it. :) Like I said the drivers CD that came with this card has Windows, Mac, and Linux drivers on it. I follow the readme exactly and every time there is some type of error while trying to build the driver.

---

### Post by Powerman2442 on 2009-12-29
> **Project PWNED said:**
> Actually, according to Linkskey, the chipset is Marvel



Sorry. Ndiswrapper looks like the only solution but I don't know why the Aircrack people are wrong.

Not sure if this means anything, but I pulled the wireless nic out and looked at the chip on card and it has the Realtek logo on it with RTL8185L printed below it.

---

### Post by macho on 2009-12-29
i have a card with this exact chipset, and the rtl8180 module seems to work okay for me, although i'm having a few reliability and speed issues.

for me (in hardy/8.04) that driver is in the linux-backports-modules-2.6.24-26-generic package.  i think you need to enable the backports repository to get that.  make sure to replace 2.6.24-26-generic in the package name above with your kernel version, which you can find with "uname -r".

after installing that i think it should be a simple matter of rebooting or a "sudo modprobe rtl8180" to get it going.

---

### Post by Bucky Ball on 2009-12-29
> **Powerman2442 said:**
> Not sure if this means anything, but I pulled the wireless nic out and looked at the chip on card and it has the Realtek logo on it with RTL8185L printed below it.

Exactly:

```
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```To enable the backports as suggested previously:

[http://willdaniels.co.uk/articles/howto-guides/15-rtl8180-hardy](http://willdaniels.co.uk/articles/howto-guides/15-rtl8180-hardy)

... or even:

[http://willdaniels.co.uk/articles/howto-guides/12-r8180-hardy](http://willdaniels.co.uk/articles/howto-guides/12-r8180-hardy)

... but both suggest the driver you want is in the current kernel. 

Before attempting any of this make sure you have opened a terminal and entered these two commands:

```
sudo apt-get update

sudo apt-get upgrade
```This will NOT upgrade your OS release version but will upgrade Hardy kernel or packages that are outdated and have replacements. If you are running an older kernel that might be your problem.

---

### Post by Powerman2442 on 2009-12-29
Hello all, the used hard drive I just bought off of Ebay died. Talking with the seller to see about getting a new one as the item had a 7 day DOA warranty. I will try the suggested steps above once I get the computer back up and running again.

Thanks!

---

### Post by Powerman2442 on 2009-12-31
> **Bucky Ball said:**
> Exactly:

```
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```To enable the backports as suggested previously:

[http://willdaniels.co.uk/articles/howto-guides/15-rtl8180-hardy](http://willdaniels.co.uk/articles/howto-guides/15-rtl8180-hardy)

... or even:

[http://willdaniels.co.uk/articles/howto-guides/12-r8180-hardy](http://willdaniels.co.uk/articles/howto-guides/12-r8180-hardy)

... but both suggest the driver you want is in the current kernel. 

Before attempting any of this make sure you have opened a terminal and entered these two commands:

```
sudo apt-get update

sudo apt-get upgrade
```This will NOT upgrade your OS release version but will upgrade Hardy kernel or packages that are outdated and have replacements. If you are running an older kernel that might be your problem.

Okay ran the following:

sudo apt-get update
sudo apt-get upgrade

Everything was up to date though.

Checked out the second link first and ran all the commands. Went to the network manager and all the wireless networks were listed! Unfortunately when I clicked on my wireless network Ubuntu locked up and I had to manually shut it down and turn it back on. When I turned it back on none of the activity LEDs on the wireless nic were lighting up. Going to retry then check out the first link.

Edit: Okay checked out the first link about adding the backports and after I typed the commands and rebooted to try to boot into the new kernel it freezes every time. I selected (Recovery Mode) of the new kernel in the GRUB menu and booted up normally and watched as it loaded certain drivers. It seems to be hanging every time while trying to load something for Bluetooth. Any idea why? I had to boot up with the old kernel from GRUB. For now I edited menu.lst and made the older kernel the default.

---

### Post by Powerman2442 on 2009-12-31
Okay well I got my wireless nic to work (perfectly so far). According to the network manager the connection quality has been anywhere between 75% and 98%.

First I installed ndiswrapper.

I went [HERE]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") and downloaded the Windows 98/ME driver and saved it.

Then, I did the following...

Unpacked the .rar file (had to type "sudo apt-get install unrar" first)
Loaded up ndiswrapper from System => Administration
Selected "Install New Driver"
Navigated to the "WinME" folder
Selected "net8185.inf" file
Left clicked the network manager (all of the local wireless networks were displayed)
Selected my network and entered my 128 bit WEP hex code and it connected immediately.

Haven't lost connection yet and connection quality has been between 75% and 98%. Hope this helps anyone else with the similar chipset (RTL8185). Going to leave this thread open for a few days just to make sure no problems occur. Thanks to all of you who tried to help.

P.S. I've tried all of the above methods. A few of them locked up my computer when I attempted to click on the network manager to check for networks. One method caused a lock up when I tried to connect. Not sure what caused this. :(

Edit: Okay it has been a few days since I got my wireless card up and running with ndiswrapper and I have to say I am happy with it. I've downloaded well over 4 GBs of data using my wireless card. Signal strength has been consistently 75% - 98%. What more can I ask for from a cheap off-brand product! :D Solved!

---

### Post by mdecler2 on 2010-01-12
I have the exact same problem as above. I can detect the device (RTL8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)). I have the 2.6.26 kernel installed, and the entire system hangs when I run ```
ifconfig wlan0 up
``` My kernel should have the available drivers considering this bug report suggests backporting to kernel 2.6.25: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/176507](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/176507) Is the only way to solve this by using ndiswrapper?

---

### Post by Powerman2442 on 2010-01-12
> **mdecler2 said:**
> I have the exact same problem as above. I can detect the device (RTL8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)). I have the 2.6.26 kernel installed, and the entire system hangs when I run ```
ifconfig wlan0 up
``` My kernel should have the available drivers considering this bug report suggests backporting to kernel 2.6.25: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/176507](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/176507) Is the only way to solve this by using ndiswrapper?

All the previous steps I've tried locked up my computer as well. Even the driver that came with the card made for Linux. The only way I've got mine to work is with ndiswrapper. 

So far no problem other then I switched to a newer computer and the wireless antenna was to close to my VGA connector and my graphics were glitching out and my connection strength was 35%. I moved the antenna two inches away from the connector and resolved both issues. :D

---

