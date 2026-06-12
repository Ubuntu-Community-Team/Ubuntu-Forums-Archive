---
title: "Internet Connection Problems with 10.10 and 10.04"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by hawkeyeguy on 2010-11-21
I'm new to Linux and recently installed Ubuntu 10.10.  Everything seems to be working fine on the installation except I have never been able to connect to the internet (I'm on mac connected to the same linksys router at the moment).  I've been working on this for several days and have exhausted all the possible causes.  Here is my setup.  Any help would be much appreciated.  Let me know if you need any additional information.

My setup:
-I have tried running both 10.10 and 10.04 (I have 10.04 installed at the moment)
-I have windows xp on a separate hard drive on the same computer and the internet works fine when I boot in windows
-I have tried both automatic DHCP (which my windows uses) and manually connecting to my network under the IPv4 settings
-my "Connection Information" info under my networks manager has all the correct information listed as far as my driver, IP address, Bcast, mask, DNS serves are concerned (except I don't know what 'default route' is for so I can't verify that that is correct.)
-my ethernet connection is wired connection that is connected to a linksys router
-my ethernet driver is sis190
-I can ping my router successfully, but I cannot ping anything (i.e. websites) on the other side of my router

Any ideas on anything else I can try or am overlooking?  Feel free to insult my intelligence.  I am pretty computer literate but am new to Ubuntu so I wouldn't doubt that I am overlooking something obvious.

---

### Post by uncaspi on 2010-11-21
Please post the output of
sudo /sbin/route -n

---

### Post by hawkeyeguy on 2010-11-22
output from /sbin/route -n

Kernal IP routing table
Destination	Gateway	Genmask		Flag	Metric	Ref	Use	Iface
192.168.1.0	0.0.0.0		255.255.255.0		U	1	0	0	eth0
169.254.0.0	0.0.0.0		255.255.0.0		U	1000	0	0	eth0
0.0.0.0		192.168.1.1	0.0.0.0			UG	0	0	0	eth0

---------------------------------------------------
Here is some additional information on my network.
Active Network Connections:
Interface: Ethernet (eth0)
Hardware Address: 00:16:EC:4C:9A:5D
Driver: sis190

IP Address: 192.168.1.1
Broadcast Address: 192.168.1.255
Subnet Mask: 255.255.255.0
Primary DNS: 97.64.183.164
Secondary DNS: 97.64.179.250

---

### Post by hawkeyeguy on 2010-11-22
It was a little hard to read my output from /sbin/route -n above so hopefully this post is a little more clear.  Couldn't figure out a way to make it readable horizontally.


Kernal IP routing table
Destination	    
192.168.1.0
169.254.0.0
0.0.0.0

Gateway
0.0.0.0
0.0.0.0
192.168.1.1

Genmask
255.255.255.0
255.255.0.0
0.0.0.0

Flag
U
U
UG

Metric
1
1000
0

Ref
0
0
0

Use
0
0
0

Iface
eth0
eth0
eth0

---

### Post by uncaspi on 2010-11-22
Your default gw are 192.168.1.1
You can ping the router, but can you ping anything on the outside world?
ping 8.8.8.8 c-4

---

### Post by hawkeyeguy on 2010-11-22
I tried pinging 8.8.8.8 in the terminal, but it comes back as "Network is unreachable."

---

### Post by uncaspi on 2010-11-22
Ok. The problem is from the router to your ISP. Are you sure all connectors are plugged properly in? If you have a cable from your ISP it should be plugged into the WAN slot. Do you have a correct cable into the router and not a crossed cable for connecting two ps's together?
If all these is ok you could do two things.
First try to hard restart the router. Push the Reset button in the back of the router. If you still not can ping 8.8.8.8 log into the router.
Start firefox and type 192.168.1.1 in the address field and log into the router. For username and passwd consult the manual. Usually it's admin and none passwd first time you log in.
I guess you use DHCP from your ISP?? Select the WAN menu and change the router MAC address by increasing the rightmost digit by one and not above F.
Save and see if it restarts. If not pull out the power plug and in again and wait a few seconds and try to ping again.
See if this helps and post back if not.

---

### Post by hawkeyeguy on 2010-11-28
The internet on the same computer works when I run Windows XP so doesn't that mean that there isn't a problem between the router and ISP?  

My ISP is a cable modem that is using DHCP.  

I tried logging into my router through firefox, but it just says that it is "Unable to connect" when I type the 192.168.1.1 router IP into the address field.

Any other suggestions?  I appreciate your help by the way.

---

### Post by hawkeyeguy on 2010-11-28
Update:  

I don't think I changed any settings, but for some reason, I can now ping [www.google.com](www.google.com) and 8.8.8.8.  I still cannot connect to any websites when using Firefox.

I still cannot log into my router from Firefox.  I type in 192.168.1.1.  It asks me for my user name and password.  After I enter that successfully, it just keeps loading...until it times out.

---

### Post by uncaspi on 2010-11-28
Ok it's a firefox problem. Type about:config in the address field and scroll down to network.disable.ipv6 and change it to true. Restart firefox and see if it helps.

---

### Post by hawkeyeguy on 2010-11-28
I changed network.dns.disableIPv6 to true, but I'm still having the same problems.  I can still ping websites, but I cannot load them in Firefox.  I suspect it is more than just a Firefox issue because I cannot connect to my Empathy IM accounts, and I get an error when I try to download software in the 'Ubuntu Software Center.'

Any other ideas that I can try?

---

### Post by uncaspi on 2010-11-28
Though ,still seems to be a firefox problem. Have you tried other browsers?

---

### Post by hawkeyeguy on 2010-11-28
Is there another browser that comes preinstalled on Ubuntu?  I was going to download Opera and try that but I'm not able to download it since I cannot connect to the internet.

---

### Post by uncaspi on 2010-11-28
To ensure you've not been hacked, create a new user and log in. Also hard reset your router (press button on the back of your router while power is on)

---

### Post by hawkeyeguy on 2010-11-28
I was able to create a new account with no problems.  Hard resetting the router did not help.

---

### Post by uncaspi on 2010-11-28
Can you use apt-get?

Try to install wine. sudo apt-get install wine

If this works the only thing on my mind now is to reinstall firefox.

sudo apt-get remove firefox
sudo apt-get install firefox

---

### Post by hawkeyeguy on 2010-11-28
I uninstalled Firefox, but was unable to reinstall it.  It kept saying that it couldn't fetch some relevant information needed in order to install Firefox.  Since I couldn't reinstall Firefox, I decided to do a full reinstall of Unbuntu in order to get Firefox back on the computer.  I was going to switch back to Ubuntu 10.10 anyway.  So know I am back to version 10.10 and I am still having the same problems (i.e. I can ping websites but can't browse to them using Firefox).

I've done some more tinkering and found that the only website that I can access in Firefox is [www.google.com](www.google.com).  I can search using google in the general search, images, videos, etc.  The page loads showing me the results from Google, but the sites won't load when I actually click on a link.  Gmail also works as I was able to log into my account.  

I feel like I'm getting closer....

---

### Post by uncaspi on 2010-11-28
I think 10.10 has another browser you could try. Look in <Applications><Internet> menu.

---

