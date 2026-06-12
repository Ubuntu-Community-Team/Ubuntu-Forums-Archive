---
title: "Help: Sharing wired internet connection to wireless"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by szczecinmeister on 2010-08-29
Hi there,

For the last 3 or so hours I have been trying in vain to simply give my mobile phone wifi internet access from my netbook. I have tried to google and follow some howto's and guides, but they're either too old or don't explain it very well.

I'm fairly new to use of Linux and of wireless networks, but can handle setting them up in Windows. So basically, having said that, I believe I mostly understand how this whole thing is supposed to work theoretically but I just feel as though I lack the experience to jump the wireless hurdle AND the Linux hurdle at the same time.

--

I'm really not sure what information would be useful, so just let me know what you need and I'll provide it. As a hazardous guess, I have provided some information below.

--

- Setup is based on Lucid netbook remix install with a Maverick kernel update due to lack of driver support for wireless NIC - I can confirm wireless does work properly for connection purposes
- I followed [http://ubuntuforums.org/archive/index.php/t-335465.html](http://ubuntuforums.org/archive/index.php/t-335465.html)
and kind of followed [http://ubuntu-tutorials.com/2009/06/13/how-to-share-your-internet-connection/](http://ubuntu-tutorials.com/2009/06/13/how-to-share-your-internet-connection/) however I couldn't even tell how to run Network Manager, even though Synaptic tells me it is installed
- When I ran into problems trying to install ipmasq I found [http://www.uluga.ubuntuforums.org/showthread.php?t=1309218](http://www.uluga.ubuntuforums.org/showthread.php?t=1309218) and followed what the response told me to which allowed me to restart the dnsmasq and the dhcp3-server at least
- I have restarted the entire netbook several times throughout the process

---

### Post by sikander3786 on 2010-08-29
I can just recommend you [Firestarter]("https://help.ubuntu.com/community/Firestarter"). That is the easiest way of ICS I've found for Ubuntu. Hope you can get it right.

Give it a try it is worth it. And post back if you have any problems.

Regards.

---

### Post by mikewhatever on 2010-08-29
> **szczecinmeister said:**
> Hi there,

For the last 3 or so hours I have been trying in vain to simply give my mobile phone wifi internet access from my netbook. I have tried to google and follow some howto's and guides, but they're either too old or don't explain it very well.

I'm fairly new to use of Linux and of wireless networks, but can handle setting them up in Windows. So basically, having said that, I believe I mostly understand how this whole thing is supposed to work theoretically but I just feel as though I lack the experience to jump the wireless hurdle AND the Linux hurdle at the same time.


So you have a wifi network, and you want to get connected from the mobile phone, right? What does Ubuntu or wired network has to do with it? Does your phone have wifi capabilities, and if so, what's the problem?

> - Setup is based on Lucid netbook remix install with a Maverick kernel update due to lack of driver support for wireless NIC - I can confirm wireless does work properly for connection purposes
- I followed [http://ubuntuforums.org/archive/index.php/t-335465.html](http://ubuntuforums.org/archive/index.php/t-335465.html)
and kind of followed [http://ubuntu-tutorials.com/2009/06/13/how-to-share-your-internet-connection/](http://ubuntu-tutorials.com/2009/06/13/how-to-share-your-internet-connection/) however I couldn't even tell how to run Network Manager, even though Synaptic tells me it is installed

The first how to explains how to set up internet access for one computer through another computer. Is that what you want?
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

The second one simply explains how to use the NM config applet, which, by the way, is located on the top panel, next to the speaker.

---

### Post by szczecinmeister on 2010-08-29
Thanks for your response Sikander, I tried Firestarter, went through the wizard, however when it tries to launch it says:
"Failed to start the firewall"
"The device wlan0 is not ready."
"Please check your network device settings and make sure your internet connection is active."

mikewhatever:
You quoted me, but I don't think you actually read what I typed. See > ... to simply give my mobile phone wifi internet access from my netbook.

To clarify, my netbook gets internet access through an ethernet connection.

Thank you.

---

### Post by Iowan on 2010-08-29
At the risk of throwing you yet another help page, the [link]("https://help.ubuntu.com/community/In...nectionSharing") **mikewhatever** provided has another link (near the bottom) for [wireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless"). It **does** seem to be getting a little old, though...

---

### Post by mikewhatever on 2010-08-29
szczecinmeister, if you need to know, I've read what you had typed several times, but still felt compelled to ask for clarifications. In case you feel like explaining, please do.

---

### Post by Runic56 on 2010-09-17
Hi Guys,

I've come across exactly the same issue. I'm trying to share a dial up 3G connection plugged into my Netbook (EeePC 1000) by setting up an ad-hoc wireless connection to my phone and to my wife's iPad.

I've installed Firestarter and followed instructions mostly from the Ubuntu 10.4 guide on sharing an internet connection.

Both parts of the equation seem to work, I can connect to the internet, Firestarter tells me that the connection is shared and I can connect to the ad-hoc network. BUT the devices connected to the ad-hoc network can't see the internet. Very frustrating as I have managed to get it to work in windoze xp (dual boot) which has annoyed me even more for some reason.

I was wondering if there are some packages missing from the Netbook install that are needed to make this work?

---

### Post by Runic56 on 2010-09-18
Hmmm after a bit more fiddling the problem seems to be that the dhcp server is not running properly.

Firestarter is writing to /etc/dhcp3/dhcp.conf but the ip address for subnet in that file does not match the range I am telling it to allocate addresses in, it seems to be allocating itself ipV6 addresses and not ipV4.

I suspect Firestarter is designed to work with dhcp and Ubuntu netbook is running dhcp3 can anyone confirm that? and maybe offer a solution?

---

### Post by Runic56 on 2010-09-19
> **szczecinmeister said:**
> Thanks for your response Sikander, I tried Firestarter, went through the wizard, however when it tries to launch it says:
"Failed to start the firewall"
"The device wlan0 is not ready."
"Please check your network device settings and make sure your internet connection is active."

Hi szczecinmeister,

I had exactly this happening to me as well, I had followed a few how to's and was getting very frustrated. In the end what did it was to re-install Firestarter then dhcp3-server using Synaptic, I think the versions I got using "apt-get install" were slightly incompatible somehow with the netbook remix of 10.4

Once they are installed configure your ad-hoc network:

WIRELESS
Name: whatever
Mode: Ad-hoc
MTU: automatic

WIRELESS SECURITY
None (works not tired any others yet)

IPv4
Method: Manual
Addresses: add one with Address: 192.168.1.1, Netmask: 255.255.255.0, Gateway: 0.0.0.0

IPv6
Ignore

All other fields are blank

Also tick the "Connect automatically" and "Available to all users" boxes

Then make sure that your internet connection is up AND the local wifi link is running as well by running ifconfig in a terminal, you should see info for both connections (in my case ppp0 for the internet and wlan0 for the ad-hoc wifi.

Next set up Firestarter:

In Preferences, set "Internet connected device" to whatever connects to the internet (ppp0 in my case) and L"Local network device" to your wifi (wlan0 in my case)
Tick both boxes, "Enable internet connection sharing" and "Enable DHCP for local network"
Then click on the cross next to DHCP server details and tick Create new DHCP configuration using:

Lowest IP: 192.168.1.10
Highest IP: 192.168.1.100
Name Server: THIS NEEDS TO FILLED IN, with the primary DNS of your internet connection, I found mine by right clicking on the Network-Manager applet in the top menu bar and the selecting "Connection Information" both the Internet connection and the local wifi connection are there.

Now when you restart just make sure the right connections are running, you wifi might need to be run from the "Connect to hidden wireless network" menu in Network Manager
Then once both connections are running (check with ifconfig) run Firestarter

Hope this works for you as well.

My only frusration now is that my android phone can't see ad-hoc connections, ah well can't win them all. :P

---

