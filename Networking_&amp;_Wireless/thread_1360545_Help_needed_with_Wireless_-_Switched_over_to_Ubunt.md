---
title: "Help needed with Wireless - Switched over to Ubuntu completely"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by rawfool on 2009-12-21
Hi all, Due to many problems arising in Vista, I've completely switched over to Ubuntu. As I had a Ubuntu 8.10 DVD ready with me, I installed it. Now I've only one problem - connecting to Internet via Wireless. Now I am connected through Wired, but which is not possible all the time because of some constraints. I need your help to get connected via wireless.
I used the help file for wired connection.
First of all, I'm using BSNL broadband, with ASDL modem. I'm given a username & a password for logging in.
I typed **[SIZE="2"]sudo pppoeconf[/SIZE]** in Terminal and then followed the steps which were very easy for Wired Connection.
But as I said I cannot used wired connection as I cannot carry the modem to other room, and I cannot sit near modem due to disturbances, I need some help to get connected via Wireless.

**_System Configuration:_**
DELL Inspiron 1420
Memory: 1 GB
HDD: 120 GB
Service Provider: BSNL
Modem Type: ADSL
Distro: Ubuntu 8.10
                         Please help me.

---

### Post by Bucky Ball on 2009-12-21
What type of wireless card? If you open a terminal and paste this in:

```
lspci
```

... you should be able to spot it somewhere in there.

Check System->Administration->Hardware Drivers

Is there a driver in there disabled? Also, when plugged in via cable, you don't get offered a driver or firmware when you update? If you have not updated do so now (or as soon as you get near your wired connection).

---

### Post by rawfool on 2009-12-21
> lspci
> rahul@DreamMachine:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


**Check System->Administration->Hardware Drivers**
It's displaying that "**No proprietary drivers are in use on this system.**" Can you tell me the name of the update which is to be ticked for Wireless connection. B'coz there are lot in there. Thanks for your reply.

---

### Post by Bucky Ball on 2009-12-21
```
09:00.0 Ethernet controller: **Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)**
```This is the part that concerns us. A newer Broadcom. Broadcom cards are now well supported but the newer ones can be problematic I have noticed.

System->Administration->Synaptic Package Manager. Search for and install 'ubuntu-restricted-extras'.

System->Administration->Update Manager. Check for updates. 

Is there now anything in Hardware Drivers? If not, you might like to take a look here:

[http://www.google.com/cse?q=Broadcom+Corporation+NetLink+BCM5906M+Fast+Ethernet+PCI+Express&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8]("http://www.google.com/cse?q=Broadcom+Corporation+NetLink+BCM5906M+Fast+Ethernet+PCI+Express&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8")

A quick look shows this card DOES work pretty well but can take some tweaking to do it. Is the light on on the card? Could you open a terminal (Applications->Accessories->Terminal) and paste this in:

```
iwconfig
```Hit enter then would you copy and paste the output and post it back here, please?

---

### Post by PRC09 on 2009-12-21
I believe his wireless card is an Intel,the broadcom is the wired card.If you need the driver for the Intel card please see the following link. I have no idea how to install it tho so maybe someone else can help.....

[http://www.intellinuxwireless.org/?n=downloads](http://www.intellinuxwireless.org/?n=downloads)

---

### Post by rawfool on 2009-12-21
Thank you all for your replies once again.

@ **Bucky Ball** - Below is the output of ***iwconfig***
> rahul@DreamMachine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

---

### Post by Bucky Ball on 2009-12-21
When you hit the network icon in the toolbar what do you get? Right click it ...

Not sure if 8.10 is the same but ...

System->Administration->Network. Hit your wireless card then properties. You need to match the ESSID and security key (WEP or WPA or whatever) with those in your router or access point. Actually looks like your card is up and named 'wlan0', just missing a secure network.

---

### Post by rawfool on 2009-12-21
When I hit the Network icon, it's showing/detecting the signal from Modem. And also if I switch over to Wireless mode, in browser if I type **192.168.1.1**, it asks for username & password which is admin for both for BSNL Broadband in India. I can see that modem is actually communicating with my laptop. Here not able to open any site. I don't know how to proceed from there. 

As of now I'm downloading all the updates from Update Manager and will take an hour or so with my slow connection.

---

### Post by coffeecat on 2009-12-21
> **rawfool said:**
> When I hit the Network icon, it's showing/detecting the signal from Modem. 

I presume you mean from the wireless modem-router? A modem doesn't put a wireless signal out - the wireless part of the router does that. Can you confirm that you have a wireless modem-router? Which make and model?

Intel wireless chipsets should work out of the box. The firmware for the 3945 and the driver is included in a default install of 9.10.

Left-click on the network manager icon. Do you see your network listed? If so, simply click on it. If you have protected it with WEP or WPA (I really hope you have chosen WPA), it will prompt you for your encryption passkey, and then you will connect. If you haven't secured it, it will simply connect. There should be no more to do.

**Edit:**

> **rawfool said:**
> in browser if I type **192.168.1.1**, it asks for username & password which is admin for both for BSNL Broadband in India.

I detect a bit of confusion here. If you type 192.168.1.1 in a browser, you are asked for your username and password for the router web-interface - which is usually admin and admin, as you say. You would be well advised to change these. This username and password is nothing to do with you ISP - even if your ISP provided you with the modem-router. Your ISP will have provided you with a separate username and password for the modem, so that it can autoconnect to the broadband connection. This is something else.

And completely different again - which is what you might need here - is the WEP/WPA passkey which either you will have programmed into the router, or perhaps the router came with a passkey already set up. Some ISPs here in the UK provide wireless-routers for their customers already set up with WPA for convenience.

---

### Post by rawfool on 2009-12-21
Yes it's a wireless ASDL modem. A Nokia-Siemens one made specially for BSNL Broadband. If I select the wireless option, I can connect to modem by opening the browser and typing **192.168.1.1** which asks for username & password, but this username & password is ***not*** the one which I use for connecting to internet. But merely doing this is not enough to get connected I think. Thank you all for your patience and replies.

---

### Post by coffeecat on 2009-12-21
If you type 192.168.1.1 in a browser window and it asks you for your username and password, then you **must** be connected wirelessly to the router. Otherwise you wouldn't get the password prompt. If you put admin+admin in, do you get into the web configuration interface?

Is it that you can connect to the router, but you can't surf the internet? I'm confused as to what your problem is now.

Or is it that you are doing the 192.168.1.1 thing with a wired connection? Because going in to the web interface is not the way to establish a wireless connection.

---

### Post by atomizer on 2009-12-21
> Intel wireless chipsets should work out of the box. The firmware for the 3945 and the driver is included in a default install of 9.10.


I would suggest to download a 9.10 iso and try to install that instead of 8.10

---

### Post by coffeecat on 2009-12-21
> **atomizer said:**
> I would suggest to download a 9.10 iso and try to install that instead of 8.10

Thanks for picking that up, atomizer. I misread the OP's 8.10 for 9.10. My mistake. However, it would help if the OP told us what they see when they left-click on NM. The Intel 3945 chipset is not that new, and it might very well be supported in 8.10, and NM might be picking up wireless networks.

---

### Post by Bucky Ball on 2009-12-21
Confusion!! Just open a web browser and in the address bar type the IP for your router/modem which I think was:

192.168.1.1

Find the name of the router (ESSID) and wep/wpa key in the Wireless Section setup. Make sure it is serving IP addresses (DHCP server).

Close that then:

* System->Administration->Network. 
* Hit your wireless card then properties. You need to match the ESSID and security key (WEP or WPA or whatever) with those in your router/modem or access point.
* Configuration should be 'Auto Configuration (DHCP)'
* Enable roaming, for now, should be disabled.
* Once it all matches, Apply and close. 

Once you are connected with the router it should provide DNS IPs for your ISP which should then get you on the net. 

Simple.

---

### Post by rawfool on 2009-12-21
I'm very sorry for ambiguity.

Yesterday I tried connecting to Internet via Wireless but in vain. My friend asked me to enable Wi-Fi and type **192.168.1.1** in browser. Then type username & password, which is admin & admin. This opened up into a page which gave information about the type of Modem, my MAC id, etc. Also in this page we can add MAC id's of users who uses this connection.

Now the other side of the story. The ISP gives an username & password for every user. This is different from the above one. When I was using Vista, I had to login using the ISP given username & password to surf internet. This username & password is typed in **Network Settings**, **Broadband Connection** in Vista. I used same username & password when I connected to Wired in Ubuntu using **sudo pppoeconf**.

And I've installed all the updates and even now the message about the Hardware drivers is '**No proprietary drivers are in use on this system**'. Also the funny thing is now even if I try to enable the Wireless, it's not going into that mode though it's showing/catching the signal from modem.

Hope I made it clearer now. Thank you all.

@ **Bucky Ball** - 

I don't know what all to do with **ESSID and security key (WEP or WPA or whatever)**. Could you explain it better. Thank you very much for your help.

---

### Post by dineshs on 2009-12-24
I think you are using bridge mode for connecting Broadband.Did you connect internet using the following command?
```
pon dsl-provider
```
What do you get when you ping 4.2.2.1 after connecting?

---

### Post by rawfool on 2009-12-26
Yes dude, I used **pon dsl-provider** connecting to internet in wired mode.
> rahul@DreamMachine:~$ **ping 4.2.2.1**
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=246 time=449 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=246 time=447 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=246 time=455 ms
64 bytes from 4.2.2.1: icmp_seq=4 ttl=246 time=449 ms
64 bytes from 4.2.2.1: icmp_seq=5 ttl=246 time=451 ms
64 bytes from 4.2.2.1: icmp_seq=6 ttl=246 time=453 ms
64 bytes from 4.2.2.1: icmp_seq=7 ttl=246 time=452 ms
64 bytes from 4.2.2.1: icmp_seq=8 ttl=246 time=462 ms
64 bytes from 4.2.2.1: icmp_seq=9 ttl=246 time=450 ms
64 bytes from 4.2.2.1: icmp_seq=10 ttl=246 time=452 ms
64 bytes from 4.2.2.1: icmp_seq=11 ttl=246 time=451 ms
64 bytes from 4.2.2.1: icmp_seq=12 ttl=246 time=450 ms
64 bytes from 4.2.2.1: icmp_seq=13 ttl=246 time=449 ms
64 bytes from 4.2.2.1: icmp_seq=14 ttl=246 time=449 ms
64 bytes from 4.2.2.1: icmp_seq=15 ttl=246 time=448 ms
64 bytes from 4.2.2.1: icmp_seq=16 ttl=246 time=452 ms
64 bytes from 4.2.2.1: icmp_seq=17 ttl=246 time=445 ms

---

### Post by dineshs on 2009-12-28
I think you have a DNS issue.Try editing /etc/resolv.conf
```
sudo gedit /etc/resolv.conf
```
Add the following line at the end

nameserver 4.2.2.1

save and close the file .Now try a site

---

