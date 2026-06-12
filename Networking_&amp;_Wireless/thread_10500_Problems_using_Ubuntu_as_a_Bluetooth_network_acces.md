---
title: "Problems using Ubuntu as a Bluetooth network access point"
date: 2005-01-08
forum: Networking &amp; Wireless
---

### Post by stewartbw on 2005-01-08
Hello, Please can someone help with a Bluetooth networking problem I'm having. I've already tried to find the answers on the Net, but most of the info I keep finding is out of date (ie. before rfcommd was moved to the Kernel).

I'd like to use my ubuntu machine (Warty) to act as a gateway for my bluetooth enabled palm (Tungsten T3 palmos5) to browse the Internet. I have been able to get the palm to pair with ubuntu, but cannot get a "network" connection. The error on the palm is
"Error:Serial:timeout. Could be bad cable or faulty Modem. (0x0305)"

I'm not sure if there are any further changes needed for ppp as the only change suggested was the creation of the /etc/ppp/peers/bluetooth.options files, though I'm not sure how this gets associated with the bluetooth connections, or whether something needs to be set to spawn pppd for the connection (it is not running at the moment)

The following details the steps I have already gone through.

--

Using Synaptic install
bluez.utils
bluez.pin
bluez.hcidump


$ lsmod | grep blue
bluetooth              44036  7 rfcomm,l2cap,hci_usb


$ hciconfig
hci0:   Type: USB
        BD Address: 00:04:3E:40:6C:FD ACL MTU: 1356:5  SCO MTU: 48:1
        UP RUNNING PSCAN ISCAN
        RX bytes:101 acl:0 sco:0 events:13 errors:0
        TX bytes:300 acl:0 sco:0 commands:13 errors:0


(Palm switched on)
$ hcitool scan
Scanning ...
        00:07:E0:30:9A:76       Palm

This is my palm device

Note PIN is in /etc/bluetooth/pin 
it's default is 1234


On Palm
Prefs -> Communication (Bluetooth)
Assuming status "on"
Trusted Devices
Add Device - Show Current Discovery
It should show the linux machines hostname Select and it will prompt for PIN
(see above)
The devices are now paired

check sdpd daemon is running (using ps -ef | grep sdpd)

Check it's setup for LAN
$ sdptool get Lan
Service Name: SDP Server
Service Description: Bluetooth service discovery server
Service Provider: BlueZ
Service RecHandle: 0x0
Service Class ID List:
  "SDP Server" (0x1000)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 1
    Version: 0x0001
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100


On palm create a "connection" from the prefs
Name - something appropriate
Connect to - PC
Via - Bluetooth
Device - Select previously paired device
OK


sudo rfcomm bind 0 00:07:E0:30:9A:76 1
address taken from hcitool scan
(rfcomm <devnum> <bdaddr> [<channel>])


$ rfcomm -a
rfcomm0: 00:07:E0:30:9A:76 channel 1 clean


Create file
/etc/ppp/peers/bluetooth.options 
using example from: 
[http://www.harbaum.org/till/palm/bluetooth/](http://www.harbaum.org/till/palm/bluetooth/)

on palm "Network"
new
service: appropriate name
username & password - blank
connection - select connection created earlier

Then when I attemp a connection I get:
"Error:Serial:timeout. Could be bad cable or faulty Modem. (0x0305)"

Nothing appears in /var/log/messages
I can get a hcidump, but there is lots of information and I don't know how to read it (although it does show it's at least trying to connect)

I guess I either need some changes to the ppp configuration, or it's something more basic on the bluetooth side. If anyone has any experience with this I'd appreciate some help. 

Thanks
Stewart

---

### Post by Botsinge on 2005-01-08
I haven't a fresh Ubuntu install, so I'm not 100% certain of which packages that this solution depand upon, but the ones I do now is:
[INDENT]bluez-pin
bluez-utils
ppp[/INDENT]

To be able to share the internet connection you first have to create the file /etc/ppp/peers/dun:
```
115200
proxyarp
192.168.168.1:192.168.168.50
local
ms-dns 172.16.3.3
noauth
debug
ktune
```The third row: XXX.XXX.XXX.XXX:YYY.YYY.YYY.YYY sets the ip-address of the computer's bluetooth interface and the ip-address which will be assigned to the PDA. In my setup I give the bluetooth interface the address 192.168.168.1 and my Palm 192.168.168.50. The fifth row, ms-dns XXX.XXX.XXX.XXX, sets the name server which the handheld will use. For further explanations of the options see the pppd's manpage.

After that, edit the file /etc/default/bluez-utils.
Find the row```
DUND_ENABLED=0
```and change it to```
DUND_ENABLED=1
```

and change the row```
DUND_OPTIONS="--listen --persist"
```to```
DUND_OPTIONS="--listen --persist --msdun call dun"
```Then, restart bluez-utils:```
sudo /etc/init.d/bluez-utils restart
```
This will give your Palm a IP-address, standard gateway and a nameserver. To be able to do anything besides pinging your computer you also will have to configure iptables to forward the traffic from the handheld. A very basic configuration of this can be:
```
iptables -A INPUT --in-interface ppp0 -d 0.0.0.0/0 -j ACCEPT
iptables -A FORWARD --in-interface ppp0 -j ACCEPT
iptables -A FORWARD --in-interface eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING --out-interface eth0 -j SNAT --to 192.168.1.168
```
The last ip-address (row four) is your computer's address (in my case 192.168.1.168 ).

---

### Post by stewartbw on 2005-01-09
Thanks for your help.

It was the entries needed in /etc/default/bluez-utils that I was missing. 
When I pointed these at the /etc/ppp/peers/bluetooth.options file then it started working.

Stewart

---

### Post by ac_dispatcher on 2005-03-10
First post here - Gentoo convert  ;-) 

I was pulling my hair to get my bluethooth PDA to work until this thread.

Just wanted to say thanks. -

---

### Post by tfarrow on 2005-03-14
I am not quite there yet; Palm Web Pro on my T3 is indicating that it is connecting to my laptop successfully, but for some reason routing must not be happening.  I'm getting a "DNS lookup timed out." error message on the palm.

The main difference for me from above is that my internet connection on the laptop is wlan0, and of course my ip address is different.   ](*,)

Also, another probably silly question, how to automate the string of iptable commands?

---

### Post by ac_dispatcher on 2005-03-20
My Laptop is behind my Firewall.  I didnt use the above iptables I did:

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i ! eth0 -j ACCEPT

And it worked.  I didnt want to set a hard address cause when I reboot I may end up with another given by my router/firewall.

Also on my T5:

# Pair the Palm to the Bluetooth dongle: in Bluetooth Preferences, tap "Trusted Devices", "Add Device", and select your dongle's name from the list that appears. 

# In Connection Preferences, create a new connection with the following attributes: Connect To: PC (I did local network)), Via: Bluetooth, Device: {the name of your dongle, selected in step 1}. Under Details, set the speed to 115,200 bps and Flow Ctl to Automatic.

# In Network Preferences, create a new service. You can leave the User Name and Password fields blank. Select the connection you created in the previous step, then tap Details. Here, set the Primary and Secondary DNS servers to the same as your Server, and check the box for Automatic IP Address discovery.

# Test the connection by tapping "Connect". After a few messages, the connection should be made. Tap Menu->Options->View Log..., and scroll to the bottom. Here, you can test the connection by sending the following ping command: ping xxx.xxx.xxx.xxx (your computers) -- this will test the connection between your Palm and the Server. You can then try pinging an IP on the Internet, or a DNS name.

---

### Post by tfarrow on 2005-03-27
That worked perfectly, thanks!

---

### Post by Admiral-Cyclops on 2007-06-10
You don't need the option to use msdun, you need to set msdns and such, but msdun simply makes it act like a microsoft dun server.

I found that when I used msdun I had to create a login script saying:
Wait for CLIENTSERVER
Send CLIENT
Send CLIENT

(or something along those lines) which emulates a microsoft client trying to sign in.

When I removed that option, it worked perfectly without a script at all.

Just a though.

---

### Post by xolot1 on 2007-06-12
im having a tough time getting bluetooth working between fiesty and my tungsten t5.

i can get initial connections from my palm to the computer, allowing the relationship to become trusted.
i can use 
pand --connect 00:07:E0:51:C7:A1

from my computer to explicitly connect with the palm, but apparently for not a long time.
ive followed the above instuctions, but im guessing theres something wrong with my config (typo?), or somethings changed.

there have been quite a few changes to the services referenced as bluetooth has been progressing rapidly (i dont think sdpd is used anymore, for example).

any suggestions?

---

### Post by Admiral-Cyclops on 2007-06-13
> **xolot1 said:**
> im having a tough time getting bluetooth working between fiesty and my tungsten t5.

i can get initial connections from my palm to the computer, allowing the relationship to become trusted.
i can use 
pand --connect 00:07:E0:51:C7:A1

from my computer to explicitly connect with the palm, but apparently for not a long time.
ive followed the above instuctions, but im guessing theres something wrong with my config (typo?), or somethings changed.

there have been quite a few changes to the services referenced as bluetooth has been progressing rapidly (i dont think sdpd is used anymore, for example).

any suggestions?

Well, are you sure that the T5 supports PAN?  Try using DUND as PAN isn't supported by my PDA either.  I have a T3, not that far off.

I setup DUN and worked wonderfully.

---

### Post by Xavier Oddmon on 2007-09-19
> **Botsinge said:**
> 
After that, edit the file /etc/default/bluez-utils

Alright, I would like to do the same thing, but can't find this file. I go to install it, and it tells me that I already have the latest copy of bluez-utils. Yet, this file doesn't exist, and a whereis bluez-utils returns no results. What should I do?

---

### Post by alex_mayorga on 2007-10-12
> **Xavier Oddmon said:**
> Alright, I would like to do the same thing, but can't find this file. I go to install it, and it tells me that I already have the latest copy of bluez-utils. Yet, this file doesn't exist, and a whereis bluez-utils returns no results. What should I do?

Try /etc/default/bluetooth instead. The file has changed in latest releases of bluez (bluetooth).

---

### Post by kansei on 2008-01-31
> **alex_mayorga said:**
> Try /etc/default/bluetooth instead. The file has changed in latest releases of bluez (bluetooth).

yeah it's all in /etc/default/bluetooth

I can't get my mac to see the PAN still. I know it supports PAN, because it can see the PAN on my cell phone (windows mobile 6 bleh).

sadly my mac has no functional network card (lets just say it isn't a *real* mac, but it's running leopard 10.5.1) so bluetooth pan was like my only option.

---

