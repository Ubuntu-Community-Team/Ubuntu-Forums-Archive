---
title: "Wireless USB"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by G-Hypa on 2006-02-23
Hello Everyone,

I am an UBUNTU newbie. A friend of mine installed UBUNTU on an old compaq nx9010. He managed to get a wireless MN-510 adapter to work on his lynksys wireless network, unfortunately when I took the laptop home and attempted to connect it to my wireless network, it did not work. Originally I thought WEP was the problem, but I disabled it and I am still not able to connect. The configuration file usb-wireless.sh is as follows:

#! /bin/sh
#
# Wireless USB setup

#Step 1 - enable wireless USB for wlan0
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

#Step 2 - set SSID for your network
wlanctl-ng wlan0 lnx_autojoin ssid=ECHACOM
authtype=opensystem

#Step 3 - set WEP attributes
#wlanctl-ng wlan0 lnxreq_hostwep encrypt=false decrypt=false
#wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=false

#step 4 - set WEP key
#wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=3
#wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey3=11:11:11:11:11

#Step 5 - set IP configuration
ifconfig wlan0 192.168.2.11 netmask 255.255.255.0 broadcast 192.168.2.255 route add default gw 192.168.2.1



route -n results
Destination       Gateway   GenMask         Flags    Metric    Ref     Use   Iface
192.168.2.0    0.0.0.0      255.255.255.0    U        0           0        0     wlan0
0.0.0.0.0       192.168.2.1  0.0.0.0            UG      0           0        0     wlan0

pinging the router gives me a 'Destination host Unreachable'

The computer sees the USB card and it even gives me the signal strength. In short, packets are sent but none are received.

Any help would be appreciated.

---

### Post by hajk on 2006-02-23
First off, your configuration script is not really needed, as the Gnome Networking  menu item (System/Administration/Networking) will do this as well.

Your problem ("Destination host unreachable") occurs when using a firewall with the nameserver service (port 53 UDP/TCP) closed. So, either stop the firewall or open those ports (on the host computer, not on the router).

---

### Post by G-Hypa on 2006-02-23
Thanks hajk for the quick reply, I have a MS wiresless router connected to an XP machine. I disable the firewall on the router and opened ports 53 on the XP machine's firewall (I don't perceived this to be relevant, but what the heck). still no go.

---

### Post by hajk on 2006-02-23
Well, don't disable the firewall on the router if it is connected to the Internet. Disable the firewall (or open port 53) on your Ubuntu computer (like Firestarter, Lokkit or some iptables script). This is needed when the Ubuntu computer uses the router for DNS queries. I don't know anything about MS, never used it, so can't help you there...;)

---

### Post by G-Hypa on 2006-02-23
How can I tell if a firewall is install on UBUNTU? or What ports are open?

---

### Post by hajk on 2006-02-23
Open a terminal (Accessories/Terminal) en type 

     sudo iptables -L -n

If the output merely shows:

    Chain INPUT (policy ACCEPT)
    target     prot opt source               destination

    Chain FORWARD (policy ACCEPT)
    target     prot opt source               destination

    Chain OUTPUT (policy ACCEPT)
    target     prot opt source               destination

then no firewall is running. If, on the other hand, all sorts of output lines fly by and off the screen, then you have a firewall running. You could also have a look in the /etc/init.d/ directory (or "folder") whether it lists scripts for firestarter or lokkit.

---

### Post by G-Hypa on 2006-02-23
Tried it! It shows the output that you placed above, hence there is no firewall running. Any other suggestions?

---

### Post by hajk on 2006-02-23
OK, so it's not the firewall. Next, I would suggest trying the Gnome  System/Administration/Networking method (instead of your script) upon inserting the USB dongle. I gather from your original message that the wlan0 interface is created, and it should show in Gnome as not activated. Highlight it, then choose Properties, and Enable the interface. You can now enter the Essid of your network, the WEP key, and you can choose DHCP to let your router provide an IP; then OK these choices. Next, you should make sure that your router (192.168.2.1) is the DNS server (do this in the DNS tab). Once that's done try to activate the wlan0 interface -- it may just work...

---

### Post by G-Hypa on 2006-02-23
hajk,

The wlan0 interfaced was activated. I have deactivated WEP security, so I did not use a WEP key, I entered the ESSID, the router or gateway IP 192.168.2.1 as DNS, and needless to say, it did not work. Maybe, MS routers have a different packet handling function than the Linksys routers?

---

### Post by hajk on 2006-02-24
Very strange... you might also want to check the router -- does it admit any new connections? or only "registered" ones? To find out, you need to login at the router ([http://192.168.2.1](http://192.168.2.1)) with a browser, may be from your Windows XP box. 

Then check the network settings on the router: should allow new connections to be made. Some routers (like SpeedTouch) may even have a button that allows new wireless connections to be made for a short period after being pressed -- the router manual or help pages could tell you more.

All of this assuming that the wlan0 interface comes up properly in Ubuntu, the only problem being that no connection to the router is made.

---

### Post by G-Hypa on 2006-02-25
Hajk,
Thanks for your continued support, but I think there is some other type of setup elsewhere that causes the problem. for example, I deactivated the wlan in the network utility and set the connection to "lo", I rebooted and used the script above to start wlan0, after typing [route -n] why do I get the results below? my gateway has no destination, and I don't know where the "192.168.2.0" comes from. In any case to answer your question, I am able to connect to my router via a wireless XP machine and I can log in and check the settings. 

btw. is there a way to set the ipconfig command in the script to use dhtp?

Destination     Gateway      GenMask         Flags Metric Ref Use Iface
192.168.2.0    0.0.0.0        255.255.255.0     U        0     0    0 wlan0
0.0.0.0.0       192.168.2.1    0.0.0.0             UG      0     0    0 wlan0

---

### Post by hajk on 2006-02-26
The output from "sudo route -n" is correct, which shows that the problem is not in the network setup of your Ubuntu box. Just check the settings of your router, I would say... does it accept new connections?

---

### Post by G-Hypa on 2006-03-01
SUCCESS

My USB Finally works!

It worked through wlan scripting and not through the Network tool however. Here are the files that I edited

/etc/wlan

usb-wireless.sh

#! /bin/sh
#
# Wireless USB setup
#

#Step 1 - enable wireless USB for wlan0
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

#Step 2 - set SSID for your network
wlanctl-ng wlan0 lnxreq_autojoin ssid="ECHACOM" authtype="opensystem"

#Step 3 - set WEP attributes
wlanctl-ng wlan0 lnxreq_hostwep encrypt="true" decrypt="true"
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true

#Step 4 - set WEP key
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="10:11:A8:00:44"

#Step 5 - set IP configuration
ifconfig wlan0 192.168.2.33 netmask 255.255.255.0 broadcast 192.168.2.255
route add default gw 192.168.2.1

**NOTE: **DefaultkeyID=0 is equivalent as selecting channel 1 in MN-500 base station

/etc/wlan/wlancfg-DEFAULT

#=======USER MIB SETTINGS=============================
# You can add the assignments for various MIB items
#  of your choosing to this variable, separated by 
#  whitespace.  The wlan-ng script will then set each one.
# Just uncomment the variable and set the assignments 
#  the way you want them.

#USER_MIBS="p2CnfRoamingMode=1 p2CnfShortPreamble=mixed"

#=======WEP===========================================
# [Dis/En]able WEP.  Settings only matter if PrivacyInvoked is true
lnxreq_hostWEPEncrypt=true     # true|false
lnxreq_hostWEPDecrypt=true     # true|false
dot11PrivacyInvoked=true	# true|false
dot11WEPDefaultKeyID=0		# 0|1|2|3
dot11ExcludeUnencrypted=false	# true|false, in AP this means WEP is required.

# If PRIV_GENSTR is not empty, use PRIV_GENTSTR to generate 
#  keys (just a convenience)
# add-ons/ in the tarball contains other key generators.
PRIV_GENERATOR=/sbin/nwepgen	# nwepgen, Neesus compatible
PRIV_KEY128=false		# keylength to generate
PRIV_GENSTR=""

# or set them explicitly.  Set genstr or keys, not both.
dot11WEPDefaultKey0=		# format: xx:xx:xx:xx:xx   or
dot11WEPDefaultKey1=		#         xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
dot11WEPDefaultKey2=		#  e.g.   01:20:03:40:05   or
dot11WEPDefaultKey3=		#         01:02:03:04:05:06:07:08:09:0a:0b:0c:0d
#=======SELECT STATION MODE===================
IS_ADHOC=y 			# y|n, y - adhoc, n - infrastructure

#======= INFRASTRUCTURE STATION  ===================
# What kind of authentication?
AuthType="opensystem"		# opensystem | sharedkey (requires WEP)

#======= ADHOC STATION ============================
BCNINT=100			# Beacon interval (in Kus)
CHANNEL=1			# DS channel for BSS (1-14, depends 
				#   on regulatory domain)
BASICRATES="2 4"		# Rates for mgmt&ctl frames (in 500Kb/s)
OPRATES="2 4 11 22"		# Supported rates in BSS (in 500Kb/s)

Note: In /etc/wlan/wlan.conf file I commented out the following:
#SSID_wlan0=""
#ENABLE_wlan0=y

Best practice using this method is to run the script (usb-wireless.sh) from the terminal. This way you can see if the script loaded successfully. I did this by opening the terminal changing to the wlan directory (using the cd command) and then running the script with the command:
bash usb-wireless.sh

Note make sure you have rights to the directory. i.e., you  may have to log in as root.

Thanks Hajk, 

G-Hypa

---

