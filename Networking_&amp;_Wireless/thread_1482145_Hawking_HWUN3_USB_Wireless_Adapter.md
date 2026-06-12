---
title: "Hawking HWUN3 USB Wireless Adapter"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by bonbeeno on 2010-05-13
Hi,
 
Recently I have bought a Hawking HWUN3 USB Wireless Adapter which has been working very very well with my Windows 7 system. The adapter supports both Windows and Mac OSX so I asume that it couldn't be to hard to get it to work with Ubuntu. 
 
My problem is that I cannot find any driver support on the internet which is weird OR any drivers (.sys files and .inf files). The only drivers that I can get anywhere is from the Hawking website and all they give are .EXE driver installers.
 
I have tried to extract all files from the exe's on the cd but all I get is stuff that I have no idea what it is like data.cab files and more folders but no .SYS files.
[LIST]
[*]I have the original CD that came with the adapter
[*]I am planning to use Ubuntu 10.04 64-bit
[*]I have heard of ndiswrapper but have not heard of EXE support from it.
[/LIST]Please help, :mad:

---

### Post by chili555 on 2010-05-13
Let's see if we can find a native Linux driver first. Please open a terminal and do:```
lsusb
```Post the outcome. 

I am going to take a chance here; let's also do:```
sudo modprobe rt2870sta
iwconfig
```If we are lucky, you will now have a wireless interface.

---

### Post by bonbeeno on 2010-05-13
I typed in all the commands you asked me to...in order and this is the exact results that I have got. I bolded all the stuff that is relevant to the forum. THIS IS UBUNTU 10.04

Code:
[SIZE=1]brendan@brendan-desktop:~$ **lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 0e66:0013 Hawking rt2870 [Hawking Hi-Gain Wireless-N] **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
brendan@brendan-desktop:~$ **sudo modprobe rt2870sta**
brendan@brendan-desktop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.[/SIZE]


It helps to know that it recognizes the adapter.

Please reply asap.

---

### Post by chili555 on 2010-05-13
It says its an rt2870 device, yet the driver doesn't claim it. The usb.id is not included in rt2870sta. Let's see if we can trick it. We are going to create two files. Please open a terminal and do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```The text editor gedit will open. Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0e66", ATTR{idProduct}=="0013", RUN+="/sbin/modprobe -qba rt2870sta"
```Proofread carefully twice. Save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0e66 0013" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread carefully twice. Save and close gedit.

Now do:```
sudo rmmod -f rt2870sta && sudo modprobe rt2870sta
iwconfig
```Any new wireless interface? It may take a reboot.

---

### Post by bonbeeno on 2010-05-13
[SIZE=1]Hey,

I got some **SUPER** good news.
But I have some tiny bad news.

[/SIZE][SIZE=1]You are one smart son of a gun. [/SIZE][SIZE=1]Good news is that I did what you said, rebooted, and now I am connected to my neighbors Internet.

Bad news is. It will connect to my neighbors, but not mine, which we probably both won't like. I am using an **Apple Airport Router **and Ubuntu detects it. But when I connect to it, it goes for like 2 minutes then ask for the network password, which I put in, and then it does the same thing again.
[/SIZE]
[LIST]
[*][SIZE=1] I am posting this from the Ubuntu computer[/SIZE]
[/LIST]
[SIZE=1]Any more thoughts on this?[/SIZE]

---

### Post by chili555 on 2010-05-13
Is your router set for G or N speeds or mixed? I am not sure, if it is set to N, that your device will connect. It may need to negotiate N *after* it's connected. Have you double-checked the password? What mode is it? WEP? WPA? How many characters? Do not post the actual key here.> You are one smart son of a gun.My ex-wife's lawyer will disagree!

---

### Post by bonbeeno on 2010-05-13
My USB adapter is supportive of both N and G routers but I wouldn't guess that is the reason why it won't connect to my Internet. My router has WPA & WPA2 Personal security. The password is 11 characters long, 3 being numbers and the rest letters.

P.S. That was a funny joke.

---

### Post by chili555 on 2010-05-13
> My router has WPA & WPA2 Personal security.Is it set to WPA or WPA2? I worked on another case where the router had some kind of mixed mode. I wonder if it works better set to one or the other. 

Does this tell us which it is broadcasting?```
sudo iwlist wlan0 scan
```Substitute your wireless interface if it is not wlan0. Learn with:```
iwconfig
```

---

### Post by bonbeeno on 2010-05-15
I scanned my network and it says it is:

       Cell 02 - Address: 00:1E:52:78:5D:80
             Protocol:802.11b/g/n
                                 ESSID:"John Doe's Network"
                                 Mode:Managed
                                 Channel:9
             Quality:42/100  Signal level:-73 dBm  Noise level:-83 dBm
                                 Encryption key: on
                                 Bit Rates:18 Mb/s
                                 IE: **WPA** Version 1
                                          Group Cipher : TKIP
                  Pairwise Ciphers (1) : TKIP
                                         Authentication Suites (1) : PSK
                                 IE: IEEE 802.11i/**WPA2** Version 1
                                          Group Cipher : TKIP
                  Pairwise Ciphers (2) : CCMP TKIP
                  Authentication Suites (1) : PSK

I cannot get it to connect to my network still. It is an Apple Airport router like I said before.

---

### Post by chili555 on 2010-05-16
> Quality:[COLOR="Red"]42/100[/COLOR] Signal level:-73 dBm Noise level:-83 dBm
Encryption key: on
Bit Rates:18 Mb/sWow! It looks like it's half a block away. Is it actually nearby in the house? Does it have any option to change its broadcast strength? My wireless router comes set to 50% by default. I had to move it to 75% to get solid connectivity throughout the house.

Does Network Manager prompt you for the correct mode; that is WPA & WPA2 Personal?

Have you tried to right-click the NM icon and put in your details and select Connect Automatically? Does it try?

---

### Post by bonbeeno on 2010-05-31
I want to apologize for my late response but yes I tried what you said and it still will not connect. Remember that it sees the connection and ask for password which I do...I press connect and then it goes for about a minute or 2 and then it brings up that window with my network name and password field will all the black dots and I press connect again and it is one big loop. And yes I am putting in the right password.

---

### Post by nachfolger on 2010-06-19
Great Post!  This worked for me as well.  One quick note: disconnect any other wireless adapters before running the commands... maybe this goes without saying, but it did not for me.  Once my other wireless card was disconnected it worked great.  Thanks!

---

### Post by bonbeeno on 2010-07-07
Sorry for the long respond because I was using my neighbors internet (shhhhhh). Now that they moved I am back to square one. 

The Hawking Wireless Adapter does detect my internet but will not connect to it. I think it is trying to connect with connection i believe 802.11n (which my wireless adapter has capabilities for). What it does is that it asks for the network password which I type in but then it "connects" for about 1 minute then re-asks
for the password which I am typing correctly.

---

### Post by drew408 on 2010-08-12
I did everything as you said. Seems to be working perfectly fine but when i do: 

```
rhino@dev:~$ sudo rmmod -f rt2870sta && sudo modprobe rt2870sta
```

I get:

```
ERROR: Removing 'rt2870sta': Resource temporarily unavailable
```

Is this something I should worry about? How can I fix it?

---

### Post by bonbeeno on 2010-08-12
So I am still at the point where it does detect the network, but then when I put in the password it "loads" for a few minutes then re-asks for the password and never fully connects.

---

### Post by n3cr0 on 2011-03-08
bonbeeno I'm not sure that my post will offer any kind of help but i have had problems with wpa2 keys especially with isp's that will remain nameless (actually i think i blamed the isp and just configured the router diff) but it was doing exactly what your saying never connecting fully, i changed the encryption from wpa/wpa2 to wpa and had no problems since then i realize its an old post and my reply i fear isnt much help but hey best i can tell ya buddy :P

---

