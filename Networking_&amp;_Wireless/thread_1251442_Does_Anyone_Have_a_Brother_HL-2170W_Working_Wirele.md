---
title: "Does Anyone Have a Brother HL-2170W Working Wireless?"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-08-27
Just wondering. I can get it to work fine with an ethernet cable connected to my Netgear, but not matter what I setup (even using my wife's Windows lappie) I can't get it to wirelessly connect. I'm using WPA2-PSK with AES.

---

### Post by hurricanesfan66 on 2009-08-27
Yeah, I have done it twice.  Once about a year ago, once about a month ago.  Originally I did use a Macbook to set it up.  The second time, it wasn't a full reinstall, so I was able to just use one of my Ubuntu laptops.

A large problem I had, once it was set up was a problem losing its IP, so I suggest, should you ever get it (try the Windows laptop again from scratch), set it with a static IP.

---

### Post by mykrob on 2009-08-28
working fine here. I set it up using Windows XP in Virtual Box via a USB connection to set its static IP, then Ubuntu was able to use it just fine.

In the future, I will just be sure to get a network printer that I can set the IP address directly on the printer versus having to use some special software.. :(

Otherwise, a very good printer.

---

### Post by moore.bryan on 2009-08-28
> **hurricanesfan66 said:**
> Yeah, I have done it twice.  Once about a year ago, once about a month ago.  Originally I did use a Macbook to set it up.  The second time, it wasn't a full reinstall, so I was able to just use one of my Ubuntu laptops.

A large problem I had, once it was set up was a problem losing its IP, so I suggest, should you ever get it (try the Windows laptop again from scratch), set it with a static IP.
I've already tried that one, without success.
> **mykrob said:**
> working fine here. I set it up using Windows XP in Virtual Box via a USB connection to set its static IP, then Ubuntu was able to use it just fine.

In the future, I will just be sure to get a network printer that I can set the IP address directly on the printer versus having to use some special software.. :(

Otherwise, a very good printer.
My problem seems to be the printer won't let me authenticate to the router. I have WPA2-PSK AES and the web admin page requires a WEP key to be entered.

---

### Post by moore.bryan on 2009-08-28
I'm still at a loss... everything seems as though it's setup properly, as per the network config print-out of the printer itself:
> 
[FONT=Lucida Sans Unicode][FONT=Courier New]<<NETWORK CONFIGURATION>>
<IP Settings>
IP Address             192.168.1.5 (set manually)
Subnet Mask            255.255.255.0
IP Gateway             192.168.1.1
IP Config              STATIC
<Comm. Mode>           Infrastructure
<Name (SSID)>          35moore
<Authentication Mode>  WPA/WPA2-PSK
<Encryption Mode>      AES[/FONT]
[/FONT]

---

### Post by Maximus_ARNP on 2010-07-10
I know this is a year old post. But, I did not find any other post providing a solution to the same problem. So, I am sending out this solution that worked on Ubuntu 10.04 AMD64.

1). Using Synaptic install **Brother-lpr-drivers-laser** and **brother-cups-wrapper-laser**.
2) System---->Administration----->Printing----->Add New Printer---->Network PRinter ------> Find Network Printer
3) Type IP address of your printer in to **Network Printer** ----> Find ----->wait for results.
4). I have **JetDirect (192.168.#.#)** with **Queue** "PASSTHRU".
5).Forward ---->Apply----->Print Test Page.

That's it. FYI, I had my printer connected to the network wirelessly during the entire setup. I did not have to use hardwired connection. If your printer has never been connected to the wireless network, you **may** have to set the printer on your network first using hardwire.

Enjoy.

---

### Post by squigish on 2010-07-31
I've had my HL-2170W working beautifully on wifi for several months now, but am only just now trying to get it to talk to my linux boxes (until now I've just been printing from windows).  

I did all the initial setup using an ethernet cable, and set it to use a static ip (I chose to use different static ip's for ethernet and wifi).  At first, it wouldn't always connect to the wifi network (I'm using WPA encryption), but then, without me doing anything, it just started working.  We switch it off to save power whenever we aren't using it, and it only takes around 10-15 seconds between powering on and connecting to wifi.

---

### Post by fredpauling on 2011-01-30
Thanks Maximus_ARNP, your method works well.
--Fred.

---

