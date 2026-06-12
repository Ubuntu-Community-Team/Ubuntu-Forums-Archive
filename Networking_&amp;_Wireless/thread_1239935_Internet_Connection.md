---
title: "Internet Connection"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by Johndo1 on 2009-08-14
I have Ubuntu on my laptop and I used to have it on an old desktop. I decided to mess around with the old one and turn it into a server so far I have installed it and have reached the server command-line. My question is how can I connect to the internet? I feel like a complete n00b asking this but w/e. Anyways I feel way over my head with the prompt so i'll probably install a GUI at first . Once I connect to the internet. 
I have a belkin wireless usb card...
Thanx 4 any help.

---

### Post by Bachstelze on 2009-08-14
> **Johndo1 said:**
> 
I have a belkin wireless usb card...


First, we need to see whether your wireless adapter is detected or not. Type [font=monospace]sudo iwconfig[/font] and post the results.

Also moved to Networking & Wireless.

---

### Post by Johndo1 on 2009-08-14
First thank you for replying.
Second the output was as followed:

lo no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thr: off Fragment thr=2352 B
Power Management: off
Link Quality:0 Signal level: 0 Noise level:0
Rxinvalid nwid:0 Rxinvalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I take it that it was discovered but not configure??
Anyways thanks for any replie

---

### Post by Johndo1 on 2009-08-14
> **Johndo1 said:**
> First thank you for replying.
Second the output was as followed:

lo no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thr: off Fragment thr=2352 B
Power Management: off
Link Quality:0 Signal level: 0 Noise level:0
Rxinvalid nwid:0 Rxinvalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I take it that it was discovered but not configure??
Anyways thanks for any replie

So anybody know if this means my wireless device is detected or not?

---

### Post by Johndo1 on 2009-08-14
It seems the wireless device is recognized. I've preformed these commands succesffully:

sudo ifconfig wlan0 address 192.168.2.1
sudo ifconfig wlan0 netmask 255.255.255.0
sudo ifconfig wlan0 gateway 72.23.150.1
sudo iwconfig wlan0 essid belkin54g
sudo iwconfig wlan0 ap any
 
I assume I am missing something because i canot upload a gui nor can I ping google. 
Any help will be greatly appreciated.

---

### Post by superprash2003 on 2009-08-14
also post output of **sudo iwlist scanning**

---

### Post by Johndo1 on 2009-08-14
> **superprash2003 said:**
> also post output of **sudo iwlist scanning**

Output of iwlist:

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] keys
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
              [interface] auth
              [interface] wpakeys
              [interface] genie
              [interface] modulation

Ty for the help!

---

### Post by Johndo1 on 2009-08-14
I think i'm close to getting it on the net...
I've preformed the following commands:

iwpriv wlan0 network_type g
iwconfig wlan0 essid "any"
ifconfig wlan0 up
iwlist wlan0 scan

I found them on a seperate forum Everything seems to be in place I have no idea why i'm not on the internet yet... I have pinged google and it states it is an unkown host.... 

I am comparing the things from iwconfig , ifconfig and iwconfig wlan0 scan with my laptop and the server and they seem to be nearly the same... I'm not sure why I dont have access to the internet. 
Any help will be appriciated.

 
It seems the inet addr is missing. It has inet6 but no inet. How can I configure
that?

---

### Post by Iowan on 2009-08-15
> **Johndo1 said:**
> sudo ifconfig wlan0 address 192.168.2.1
sudo ifconfig wlan0 netmask 255.255.255.0
sudo ifconfig wlan0 gateway 72.23.150.1
sudo iwconfig wlan0 essid belkin54g
sudo iwconfig wlan0 ap anyYou seem to be making progress... Does your wireless network use static addresses? Although it makes sense for a server to have a static address, it means you must set up DNS separately.  If the rest of the network uses DHCP (and if the DHCP server is capable), you might set up the DHCP server to issue a static lease to the server... meaning the DHCP server assigns the proper DNS entries.

Sounds like the manual address configuration didn't "stick" - if no inet address shows (unless your system uses IPv6 exclusively), and is probably why the rest fails (no address, no Internet access).

Network Manager isn't showing wireless networks?

---

### Post by superprash2003 on 2009-08-15
the command is** sudo iwlist scanning** and not just iwlist

---

### Post by Johndo1 on 2009-08-15
First of all. Thank you for replying.

1st. No my network is not using a static ip...

2nd. Unfortunately the server doesnt seem to have network manager. Maby I missed it on installation? 

3rd. Re installation is possible because I havent really done anything besides work on the Internet connection. 

4th: Sorry about that superprash... here's iwlist scanning

Wlan0 Scan completed:
      cell 01 - Address: 00:17:3F:01:77:3E
                ESSID:"belkin54g"
                Mode: Master
                Channel:11
                Frequency:2.462 GHz (Channel 11)
                Quality=100/100  Signal level:49/100
                Encryption key: off
                IE: Unknown: 000962656C6B696E353467
                IE: Unknown: 010882848B962430486C
                IE: Unknown: 03010B
                IE: Unknown: 2A0104
                IE: Unknown: 2F0104
                IE: Unknown: 32040C121860
                IE: Unknown: DD090010180204F1000000
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                          24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                          12 Mb/s; 48 Mb/s000000199741e23f
                Extra:tsf=000000199741e23f
                Extra: Last beacon: 10ms ago

---

### Post by Iowan on 2009-08-15
Eventually, you may wish to have the DHCP server issue a static lease to the server... but first things first.
I read it, then must have forgotten that you said the machine was a server.  A server would have no Desktop (or Network Manager) unless you specifically added them later.
Hold off on the re-install for awhile, Save it for a last-ditch attempt.  It might/not help with wireless problem.

---

### Post by Johndo1 on 2009-08-16
Yes, I agree. Also a DHCP static IP would require me to purchase this from my ISP?

Also any new updates on how to help me get the server online would be helpful!

Thanks

---

### Post by Iowan on 2009-08-16
A static *lease* would be assigned by your DHCP server (router?) - based on MAC Address.  I'm not familiar with all the brands/models, so I'm not sure which ones can/cannot issue a static lease (fixed address).

---

### Post by Johndo1 on 2009-08-16
I see... That would probably be good down the road.

Anyways If I do resort to re installation I skipped the parts were it asked me to put in wireless information or Address information because I didnt know what I do now thanks to the forums :) ... Anyways Any new help on getting my server onto the Internet will be helpful.

---

### Post by Johndo1 on 2009-08-18
I got tired of it not working so I installed ubuntu server 8.10 and it seems to be working fine over the internet... The command wget doesnt seem to be installed but I suppose i'll post a new thread for that :) thank you for all of the help!

---

