---
title: "Draytek Vigor N61 USB dongle"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by Spudz0r on 2009-01-15
I was wondering if there was a way to get this (Look Title) dongle to work in ubuntu.

i dont particularly mind if i need to use ifconfig or the gui configuration tool, either is fine.

i also dont particularly care if it uses an ndiswrapper. I do not know what chipset it uses (though i read somewhere it might be ralink 2870 based).

I would however like to be able to see connection status in the gui.

needs to support at WPA2 if possible.

pretty much, this is the last thing i need to organise before i can switch over to ubuntu full time. (at the moment i have no network under ubuntu)

thanks.

---

### Post by Spudz0r on 2009-01-15
I followed the instructions to install the ra2870 driver, but alas i have run into problems.

when i get to the bit that asks you to run (as root) make install.
using: sudo make install

it tells me that ra2870.ko does not exist and bombs out.

can anybody help me with this?

---

### Post by Spudz0r on 2009-01-16
lol.. thanks for the help everyone (or not)

i figured out how to fix it.

the HOWTO was missing a step.

it had

"extract tar"
"run as root - "make install""

but really it should have been.
"extract tar"
"run as root - "make" THEN "make install""

that worked =P

---

### Post by i_hate_command_line on 2009-01-27
**@Spudz0r**: Thank you for sharing this! I have not tested this yet, but would like to do so asap. Would you be so kind as to help us Linux newbies by providing a step-by-step guide on what you did? I found some Ralink drivers [here]("http://www.ralinktech.com/ralink/Home/Support/Linux.html"), but can't find the r**a**2870 driver nor the HOWTO you are referring to.

Btw, this topic has also been discussed [here]("http://ubuntuforums.org/showthread.php?t=728365") (locked topic) and next [here]("http://ubuntuforums.org/showthread.php?p=6629379#post6629379").

---

### Post by Spudz0r on 2009-01-30
would be happy to.

give me a little while to dig it up and i will post up a step by step.

---

### Post by Spudz0r on 2009-02-01
sorry for the delay mate, havent had a chance to get onto my ubuntu box.

i want to make sure the howto i saved (I have half a dozen of them and only 1 worked) is the correct one before i post it up.

---

### Post by Spudz0r on 2009-02-02
ok found it.. will need to do in a few posts.

First. Download the latest RT2870 driver from:
[http://www.ralinktech.com.tw]("http://www.ralinktech.com.tw")

direct link (possible older version):
[http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2]("http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2")

copy this file to a fresh directory (i used ~/drivers/ralink/2870)

extract it into that directory.

=> continued next post

---

### Post by Spudz0r on 2009-02-02
Enter the directory and edit the config.mk file so that the driver will support NetworkManager

```
nano os/linux/config.mk
```
 
Change the following part
 
```
# Support Wpa_Supplicant

HAS_WPA_SUPPLICANT=n 

# Support Native WpaSupplicant for Network Magang

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
```

to this
 
```
# Support Wpa_Supplicant

HAS_WPA_SUPPLICANT=y 

# Support Native WpaSupplicant for Network Maganger

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

---

### Post by Spudz0r on 2009-02-02
Next we need to compile and install it.

from the top directory of the extracted files, do the following in a terminal.

```
sudo make
sudo make install
```

Next we edit the config file (I had to change AuthMode to WPA)
```
sudo nano /etc/Wireless/RT2870STA/RT2870STA.dat
```
its most likely this is all that needs to be changed as the other information can be changed with NetworkManager.

Not sure if the rest is needed in intrepid as mine came up right away, but i had been fiddling for a while.

Finally we make sure it runs @ startup.

```
sudo nano /etc/modules
```
add this below the last entry.
```
alias ra0 rt2870sta
```

Ugly fix to make ra0 come up @ boot.

```
sudo nano /etc/init.d/rc.local
```
add to end of file.
```
ifconfig ra0 inet up
/etc/init.d/NetworkManager restart
```

Reboot and all should be peachy.

---

### Post by i_hate_command_line on 2009-02-10
> **Spudz0r said:**
> ... will need to do in a few posts.
**@Spudz0r**: Thanks to your excellent tutorial, my N61 now works fine for me. Thank you some much for sharing, which is really appreciated a lot!

System -> Administration -> Hardware drivers:
[IMG]http://img17.imageshack.us/img17/2885/hardwaredriverdb8.png[/IMG]

It works with [IEEE 802.11g (54Mb/s)]("http://en.wikipedia.org/wiki/IEEE_802.11g-2003"):
[IMG]http://img17.imageshack.us/img17/5690/g054pr9.png[/IMG]

It works with [IEEE 802.11n (270Mb/s)]("http://en.wikipedia.org/wiki/IEEE_802.11n"):
[IMG]http://img11.imageshack.us/img11/555/n270xm1.png[/IMG]

In the file "RT2870STA.dat", I changed "AuthMode=OPEN" to "AuthMode=WPA2" (instead of to "AuthMode=WPA"), as I have a [WPA2]("http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access#WPA2")-capable router.

By running [JoikuSpot Premium]("http://www.joiku.com/?action=products&mode=productDetails&product_id=451") on my [Nokia N95]("http://en.wikipedia.org/wiki/N95"), my laptop can access the internet anywhere:
[IMG]http://img19.imageshack.us/img19/5230/nokian95et3.png[/IMG]

I have only one problem left: My Vigor N61 does not connect to hidden SSID's. I have tried both via "Connect to Hidden Wireless Network -> etc." and via "Edit Connections -> Wireless -> Add -> etc.". Any clues?

---

### Post by Spudz0r on 2009-02-10
(yeah, i had mine on wpa2 as well good ol draytek.. i see you are connected at G speeds, what ap are you using.. (mine connects at between 270mbps and 300))



hmm..

havent actually tried to connect to a hidden SSID in ubuntu..

you may need to find out what settings the router uses for authentication when using a hidden ssid, as some use different settings for non hidden, and hidden (like authmode etc).

other then that, i can only suggest going through the trawl of google and looking for some form of howto.

my windows 7 install borked my grub setup so i cant go in and test at the moment.

---

### Post by tomski on 2009-03-09
hi there

i was wondering if any of you chaps had any experience in using this device as an AP (access point)?

---

### Post by i_hate_command_line on 2009-03-11
> **Spudz0r said:**
> ... what ap are you using? ...
A [Draytek Vigor 2800 series]("http://www.draytek.com/product/index/adsl2plus_firewall.php")

> **Spudz0r said:**
> ... you may need to find out what settings the router uses for authentication when using a hidden ssid ... i can only suggest going through the trawl of google and looking for some form of howto ...
Thx 4 your thoughts on this. One day I will test the N61 with another OS, to rule out if the problem has to do with the OS. However, the N61 seems to work fine with hidden SSID's of AP's of other brands. So, the problem has likely  to do with the setting of my AP, some how. Strange though, as I tried the N61 with a SSID which was first hidden and then unhidden (i.e. other then that with identical AP-settings).

I have enjoyed using the N61 many times already, thanks to your contribution. Again, thank you so much! :D

> **tomski said:**
> ... any experience in using this device as an AP?
No.

---

### Post by sameubu on 2010-08-19
Hi all,

I got ubuntu 10.04 literally this afternoon, and i have a problem similar to the ones above. I have a draytek vigor n61 dongle (which works fine with windows 7) and it can't join my wifi network.

it recognizes the dongle, and even detects many wifi networks with it, but it can't seem to join it. I've tried all of those websites above, but can't find any of the drivers they talk about.

Thank you very much for any advice you give.

sameubu

---

### Post by sameubu on 2010-08-19
Hi all,

I got ubuntu 10.04 literally this afternoon, and i have a problem similar to the ones above. I have a draytek vigor n61 dongle (which works fine with windows 7) and it can't join my wifi network.

It recognizes the dongle, and even detects many wifi networks with it, but it can't seem to join it. I've tried all of those websites above, but can't find any of the drivers they talk about.

Thank you very much for any advice you give.

sameubu

---

### Post by sameubu on 2010-08-19
> **sameubu said:**
> Hi all,

I got ubuntu 10.04 literally this afternoon, and i have a problem similar to the ones above. I have a draytek vigor n61 dongle (which works fine with windows 7) and it can't join my wifi network.

It recognizes the dongle, and even detects many wifi networks with it, but it can't seem to join it. I've tried all of those websites above, but can't find any of the drivers they talk about.

Thank you very much for any advice you give.

sameubu
sorry about that double post ;)

---

### Post by sameubu on 2010-08-19
pleeeease help, it's just i want to give ubuntu a try...

---

### Post by i_hate_command_line on 2010-08-19
> **sameubu said:**
> pleeeease help, it's just i want to give ubuntu a try...

Well 'sameubu', you may like what I just found [here]("http://rapidshare.com/files/413981073/2008_0925_RT2870_Linux_STA_WebUI_v1.4.0.0.rar"). ;)
I hope this helps. Please, share your findings with installing, configuring and using the N61 with Ubuntu 10.04 in this topic.
Also, regarding whether you can connect to a hidden (!) SSID.

---

### Post by sameubu on 2010-08-20
I have just downloaded the RT2870 file from the website. It's now on my ubuntu desktop. but it can't open the file properly, it doesn't see it as a driver:confused:

---

### Post by sameubu on 2010-08-20
I will be away for the next two weeks, so thanks for replying to me so soon, but i won't be on this forum for a while):P:lolflag:

---

