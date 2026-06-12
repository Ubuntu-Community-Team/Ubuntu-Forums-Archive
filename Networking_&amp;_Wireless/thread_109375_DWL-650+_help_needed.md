---
title: "DWL-650+ help needed"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by hanakj on 2005-12-28
I have a Compaq Presario 700Z using a known working DWL-650+ WLAN card.  I installed Ubuntu 5.10.  Install works fine, but I don't know how to configure my wireless to work.  I have found other posts that describe this, but I have not been able to understand too well.  I use a linksys wireless router(wrt54g) and the 650+ is only capable of WEP.  I don't want to buy a new card.  how do I get this going?  I would really appreciate a little hand-holding.  Please?

---

### Post by Lambert on 2005-12-29
There are a couple different chipsets used in these cards. So need to find out which one is in your card.

Post the output of these commands with card in.

```
sudo lshw -C network
```
```
sudo lspci -v | grep -A 8 Ethernet
```

(If the second command doesn't have any output just use sudo lspci -v and post output of that)

---

### Post by hanakj on 2005-12-29
Sorry for the sparseness.  the problems are on my laptop, and i'm typing this on my desktop.  How to get stuff from my lap to my desk, I don't know.  I can't even get the lap to allow me to write to a floppy disk!  So I have to type everything by hand.

IWconfig sees the card, but with all zeros for the Access point.

*-network DISABLED
product: ACX 100 22Mbps Wireless interface
vendor: Texas Instruments
Phys id: 0
bus info: pci@02:00.0
logical name:wlan0
version :00
serial : 00:80:c8:ae:8c:42
configuration: broadcast=yes driver=acx_pci multicast=yes woreless=IEEE 802.11b+

If you need any other info please let me know

The lspci command gave a bunch of info on the inboard NIC, a Realtek device.

---

### Post by Lambert on 2005-12-29
I got what I needed. Try this page. You dont have to compile a driver. Just go 1/3 way down the page where it says intall driver/firmware then something about bringing device up.

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

---

### Post by hanakj on 2005-12-29
OK, this is going to sound very dumb, but now that I got the driver from the house if craig website, how do i get it to the laptop?  How can I get the file to a floppy to transfer it to the laptop?  I am pretty dumb here, this is my first foray into Linux filesystems.

---

### Post by Lambert on 2005-12-29
It's not dumb, just a learning curve.

To make sure I'm clear. You do not need to get a driver from that site. The correct driver comes with breezy. It just needs some tweaking possibly. So let me back up.

configuration: broadcast=yes driver=acx_pci

this line in your lshw command says that the acx_pci driver loaded and allocated to the device. So let's try something.

(I assume you're using gnome, ubuntu not kubuntu)

Go to system>administration>networking You should see your wireless device in the list. Click on properties, enter your network information (only open signal or wep can be configure from here, if you're using wpa I suggest turning it off first, get your card working, then work wpa into the equation) click ok then try to activate.

then open a browser to see if you can surf. If not open a terminal and type these commands

iwconfig
ifconfig

with iwconfig I'm looking for the line with Access Point in it. If it's not all zeros then that's good, if it's all zeros that's bad.

With ifconfig the second line has inet addr (not third line with inet6 address) is this line there? if not then that's bad.(if Access Point is all zeros then this line definitely won't be here)

Ok if you didn't connect here then go back to the houseofcraig site. You don't need the driver, just the firmware. Just copy the file to either floppy or cd. When you load ubuntu the file should auto mount and show up on your desktop. Just copy the file to your home folder then run the tar command given on that site so it unzips and goes to correct directory. Then just continue with the bringing up your device section.

Post back with any snags or misunderstandings you have and no question is dumb.

---

### Post by hanakj on 2005-12-29
DD,

    Thanks for the comprehensive help.  Thanks for taking the time.

    I try to go into networking under System Administration, but it asks me for a password, which i give, and then nothing happens.

---

### Post by Lambert on 2005-12-29
If you want we can try this from the command line. A couple simple commands. 

```
sudo ifconfig wlan0 up
```

```
sudo iwconfig wlan0 essid ____ commit
```

```
sudo dhclient wlan0
```

You might/should be connected with these commands (if network uses dhcp)

This is all based on open signal (no encryption) which is best to make sure everything works first, then work encryption in if you want it.

There are some other options I can throw in here but need more info. 

run this command and you'll see something like this.

```
sudo iwlist wlan0 scan
```


Address: 00:12:17:A6:AA:3F
                    ESSID:"linksys-g"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)

then you can add to the iwconfig command and run it like this.

```
sudo iwconfig essid linksys-g ap 00:12:17:A6:AA:3F channel 6 commit
```

---

### Post by mrhaffer on 2005-12-30
I followed this thread with interest since I have a D-link 520 rev E Prism 2.5 Chip set exhibiting similar problems.  Shows up with driver in lsshw.  Shows up as wlan0 in iwconfig network disabled.  Seems to activate in Networking under System administrator but no internet.  Tried console commands and was not able to commit ESSID [invalid argument]  all zeros in listing for access point.  I did the default install.  I also have an ISA ethernet card which was not recognized under default install but I was able to configure under expert install.  Have old beater PII 300MHZ running dual system with windows 98.  By the way what is an Essid? is it the same as Bssid?  I tried the SSID and mac address both.  Learned a lot but but not getting anywhere.  Did not try the firmware upgrad for my chip.:confused:

---

### Post by Lambert on 2005-12-30
mrhaffer

essid is the identifying name of the wireless network. It's basically what ever you set it up as in your network. 

bssid is the mac address of the station in the ap? This is auto set locally I usually no interaction is needed on your part in setting up your network.

After you try to activate the card start a new thread and post the output of these commands

iwconfig
ifconfig
route

also try to ping your router

ping -c 4 192.168.0.1

replace 192.168.0.1 with the ip of your router if it's different.

---

### Post by hanakj on 2005-12-30
Got authorization problems.

Everytime I try to do a sudo command in terminal, it tells me that i am not in the sudoers file.  When I tried to do the tar command in the house of craig acx website, i can't get permission.  how can I become authorized?

---

