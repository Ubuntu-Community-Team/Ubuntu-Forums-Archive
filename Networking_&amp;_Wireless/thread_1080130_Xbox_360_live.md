---
title: "Xbox 360 live"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by monpolo on 2009-02-25
So I'm trying to run xbox live thru my laptop running Ubuntu 8.10. Basically, my laptop connects to the internet wirelessly and then I run a crossover cable to my 360 to get onto live. This worked fine in Vista, but now Vista has become corrupted (surprise huh?) Anywho, how can I bridge my wireless and ethernet connections or enable network sharing between the two?

Sorry if this is a really obvious question but I'm still a linux noob.

---

### Post by ouija on 2009-02-25
see: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Doing a quick scan, I read the fastest method could possibly be the following:

> The Firestarter firewall can do all of this for you, by the way...

Code:

sudo apt-get install firestarter

Its just a frontend to iptables.

In its preferences, set "internet connected device" to the internet, and "local network device" to the local device. Then enable NAT and DHCP if you want...
varunus is offline Report Post   	Reply With Quote

---

### Post by monpolo on 2009-02-25
Thanks for that, but now I'm getting an error message "The device eth0 is not ready" and that it can't start the firewall. eth1 is my wireless and running great and eth0 being my ethernet port where the cable runs to the xbox (through a hub which is basically doing nothing but connecting two cords so that they are long enough to reach) I've looked around and don't really understand what is wrong. My xbox is already set up to use a static ip address but perhaps I'm missing yet another obvious thing.

---

### Post by ouija on 2009-02-25
are you sure about that? On my system, wlan0 is my wireless and my wired is eth0.
I just find it strange what your wireless would appear as "eth#" as that usually specifies a wired network card.

---

### Post by monpolo on 2009-02-25
Well I could be wrong. But I don't find any wlan connections when I type iwconfig or ipconfig. All I find are eth0,eth1,lo,pan0. Eth1 says IEEE 802.11 Nickname: ""  So maybe that's my problem, perhaps the xbox is on eth1 and I just can't see wlan. Any ideas? Hope this isn't too frustrating, I know I probably sound like a 90 year old woman trying to figure out word.

Thanks for the help so far though :)

---

### Post by ouija on 2009-02-25
Okay, when you are **connected **to a _wireless_ network, look to the top right corner (where the network connection icon is) and right click on it and select "connection information"

Then look at the first item in the pop up window that appears (Interface) and it should say something like "802.11 WiFi (wlan0)"

The information in the brackets is your wirless card's "location" or device ID within Ubuntu.

This is what you would select when running Firestarter.
On the first screen when you run Firestarter it will ask you to select your internet-connected network device from the drop down.  Choose the device that matches the device ID for your wireless card.  Then click IP address is assigned via DHCP (which I believe should be applicable) and then click forward.

On the next screen, Click enable internet connection sharing and then select the device ID of your WIRED connection from the dropdown list.  Then click forward and then click save.

I believe that should do it.  (however, I have never shared my internet connection myself yet so cannot verify how well this actually works -- I've only read that Firestarter is the easiest way to allow for Internet Connection sharing)

Good Luck!

---

### Post by monpolo on 2009-02-25
Eth1 is definitely my wireless connection according to that method... I've set up firestarter using those instructions but it's still saying eth0 is not ready. I'll have to search for what I need to do to fix firestarter. Thank you for your help, even though it isn't solved yet you have helped quite a bit :D

---

### Post by ouija on 2009-02-25
I've tried using Firestarter myself now and had the same issue.

But I did get past that error by manually specifying an IP address for both my eth0 connection in Ubuntu and the system I was trying to share the internet connection with.  However, I still could not connect to the internet on the shared connection.  You can try it for yourself and see if it'll work.  Please let me know how you fair.

Here are instructions for using Firestarter that I found here: [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

> Install “Firestarter” using Applications -> Add/remove.
Then run Applications -> Internet -> Firestarter and follow the configuration guide (about 3-4 questions about how you connect to the internet and LAN)

If you do not enable the DHCP-option* (automatic network configuration) you will have to manually set the ips of the other machines so that they begin with the same three groups of numbers (eg 192.168.0.x) as the internet-connected machine has on the LAN. Then, set the gateway ip of the other machines to the ip of the internet-connected machine.

* Do not do this if your network already has a DHCP server (ie via an existing router) - two DHCP servers on the same network that gives out different settings is a bad idea…


Also see: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) for manual configuration.

---

### Post by Bixler Zavala on 2009-04-03
hi, I'm having this same exact problem. Did u manage to sort it out? If so could u help me

---

### Post by ouija on 2009-04-03
> **Bixler Zavala said:**
> hi, I'm having this same exact problem. Did u manage to sort it out? If so could u help me

Not yet.  I tried for a day and a half and gave up :(

---

