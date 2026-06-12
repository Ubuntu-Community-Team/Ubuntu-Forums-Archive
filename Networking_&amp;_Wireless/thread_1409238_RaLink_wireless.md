---
title: "RaLink wireless"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by woodsonoversoul on 2010-02-17
Hi all,
    I know this question has been asked a thousand times, but I've got a fresh install of ubuntu server and can't seen to get my wireless up. I'm working on it on a different machine, so I can't copy and paste code here, but I can answer any questions about command outputs. According to 'lshw -C network' my wireless is not disabled (although I seem to have to enable it on every boot). What's the next step?

P.S. I'm also posting this in absolute beginner to see if I get anymore bites there. I'm mark this as solved once I get it figured out...

---

### Post by chili555 on 2010-02-17
If it is a server install, may we assume there is no window manager, Gnome, KDE or the like? What do you have to do to enable it? Does lshw -C network show an interface; wlan0, ra0 or eth1 or whomever? Is /etc/network/interfaces populated with your wireless details, for example:> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid mylilrouter
wireless-key 096CXXXXAFE 

#auto eth0
iface eth0 inet dhcp

---

### Post by woodsonoversoul on 2010-02-17
Correct, no window manager.
'lshw -C network' does show an interface (ra0)
/etc/network/interfaces has:
```
auto lo
iface eth0 inet dhcp
iface ra0 inet dhcp
iface lo inet loopback
```

Thanks for the reply...

---

### Post by chili555 on 2010-02-17
It won't start automatically because you have not told it to do so with 'auto ra0.' You have also not specified the essid of the wireless access point you want it to connect to. There are probably several available in your area. Is there any encryption on your network? Those details must be specified, also.

---

### Post by woodsonoversoul on 2010-02-17
What should I do to set my networking as auto enabled? Just auto ra0, auto eth0?

Should I just poke around in my router to find my home network's essid?

I believe the network is WPA encrypted...

---

### Post by woodsonoversoul on 2010-02-17
Cool. Now I can see my home network with 'iwlist scan'

---

### Post by woodsonoversoul on 2010-02-17
'iwconfig' is showing ra0 as connected to a different network from my home network (different ESSIDs)

---

### Post by woodsonoversoul on 2010-02-17
Well now it's not connected to any networks after I 'sudo iwconfig ra0 essid "my home network name"'

---

### Post by chili555 on 2010-02-17
If you simply specify the essid, it will not automatically connect, you should follow that with:```
sudo dhclient ra0
```If this is a server, don't you want a static IP address, so you can find it? My previous post suggested a working perfectly setup. When you do:```
sudo iwlist ra0 scan
```What is your network's essid? Amend your /etc/network/interfaces to look like this, substituting your wireless details:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid mylilrouter
wireless-key 096CXXXXAFE #<--add your encryption details here.

#auto eth0
iface eth0 inet dhcp 
```> I believe the network is WPA encrypted... Scanning should tell you clearly.> Should I just poke around in my router to find my home network's essid?Yes.

---

### Post by woodsonoversoul on 2010-02-17
It's just a development server on a netbook. Is the 'static' thing still important?

---

### Post by chili555 on 2010-02-17
> **woodsonoversoul said:**
> It's just a development server on a netbook. Is the 'static' thing still important?Once you have the server running headless (no windowing manager) and you want to ssh into it to tweak your apache settings or ftp some content on to it, how do you know what it's IP address is when you, from another machine, do:```
ssh -l user 192.168.i.dont.know
```Servers very seldom have a display and keyboard attached, so they are usually set up with static IPs.

---

### Post by woodsonoversoul on 2010-02-17
Changing /etc/network/interfaces to:
```
auto lo
auto ra0
iface ra0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ourhouse
iface eth0 inet dhcp
iface lo inet loopback
```

and restarting the network with 'sudo etc/init.d/networking restart'

returns:
```
*Reconfiguring network interfaces...
SIOCDELRT: No such process
```

I'm looking into it...

---

### Post by chili555 on 2010-02-17
Let's clean it up a bit:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ourhouse

iface eth0 inet dhcp
```Now, restart networking:```
sudo [COLOR="Red"]/[/COLOR]etc/init.d/networking restart
```Any complaints or errors?

Did you determine if the network is WPA encrypted? If so, that needs to be addressed in your file. Here is a good tutorial: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by woodsonoversoul on 2010-02-17
I am getting some errors, but I've got to run. I'll post them in a couple of hours. Thanks for all your help so far, and yes, it is WPA encrypted.

---

### Post by woodsonoversoul on 2010-02-17
Edited interfaces to match what was posted. Restarting the network produces the following (twice)
```
* Reconfiguring network interfaces...
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; Network is down.
```

---

### Post by chili555 on 2010-02-17
When you do:```
iwconfig ra0
```Does the mode read something other than 'Managed?' If so, please do:```
sudo iwconfig ra0 mode managed
sudo /etc/init.d/networking restart
```Do you still get the error?

---

### Post by woodsonoversoul on 2010-02-17
Mode is 
```
Mode:Auto
```

Changing it now...

---

### Post by woodsonoversoul on 2010-02-17
Still get the same error with:
```
There is already a pid file /var/run/dhclient.eth0.pid with pid 1536
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium
All rights reserved
For info blah blah blah

Listening on LPF/eth0/00:54:08:52:8c
Sending on LPF/eth0/00:54:08:52:8c
Sending on Socket/fallback
```

and then the original message again

---

### Post by woodsonoversoul on 2010-02-17
Trying to change the mode didn't do anything. mode is still 'auto'. Have tried it multiple times...

---

### Post by chili555 on 2010-02-17
> auto ra0
iface ra0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ourhouse

Can you please proofread this carefully? Please be sure, in your router that the address is not within the range of the DHCP server. That is, that if the router assigns up to 10 addresses from 192.168.1.2 to 192.168.1.11, then your static address needs to be outside this range; 192.168.1.25, for example. You will have to check in the router. Some set 50 addresses, so guessing could still cause a collision.

Also, make sure netmask is correct; ***not*** net***work***.

---

### Post by woodsonoversoul on 2010-02-17
I'm using addresses provided by network connection information from another linux machine connected to the wireless network. I'm using IP Address for the address, Subnet Mask for the netmask, and Default Route/Primary DNS (same) for gateway. Are these not correct? and if so, where should I look for the correct information?

---

### Post by woodsonoversoul on 2010-02-17
From your previous post (chili555), does that mean I make up the address?

---

### Post by woodsonoversoul on 2010-02-17
Actually, I know that I don't just make up the address, but I don't understand where to find the range I should avoid and the range I can pick from...

---

### Post by chili555 on 2010-02-17
> Are these not correct?These are *not* correct. You can't have two computers with the same IP address if you want both of them to work correctly.

The gateway and net***mask*** appear correct. The correct way to fix the IP address is in the router as I discussed above. The lazy way is to guess that there are no more than, say five, computers in the house, so we'll use 192.168.1.15. It will probably work just fine, but then you won't be a hard-core, hard-bitten server guru!

---

### Post by chili555 on 2010-02-17
> **woodsonoversoul said:**
> Actually, I know that I don't just make up the address, but I don't understand where to find the range I should avoid and the range I can pick from...If you log on to the router's administration pages, you will find where DHCP is enabled and it usually allows you to specify the starting number (192.168.1.2, it appears) and the allowable number of addresses. I have seen as many as 50!!! My router is set to six.

If your router allows 20 IP addresses starting at 192.168.1.2, then you can pick any number above 192.168.1.21 but below 192.168.1.254. You choose; you are the server dood.

It seems tricky when you first start, but it's really logical and easy once you learn it.

---

### Post by chili555 on 2010-02-17
Here is what my router administration page looks like. Since the DHCP range is from x.102 to x.107, I set static IP addresses above x.110.

---

### Post by woodsonoversoul on 2010-02-17
Thanks so much for taking the time to explain all this to me. I've found where my router is setup to be a DHCP server, but the range it gives is 192.168.1.2 to 192.168.1.254 So what does that mean? :)

> a hard-core, hard-bitten server guru!
I love that...

---

### Post by woodsonoversoul on 2010-02-17
Can't figure out how to delete post...

---

### Post by chili555 on 2010-02-17
> but the range it gives is 192.168.1.2 to 192.168.1.254Does it give you the option to change the range to, for instance, 192.168.1.2 to 192.168.1.10? Surely you are not going to have 250 guests with their laptops all wanting wireless access!!!

If so, please change and then you can safely use static addresses from, say 192.168.1.15 on up. Proofread carefully and click Apply.> I love that... You can tell one because he or she has a burnt out Pentium III hanging from the key-chain!

---

### Post by woodsonoversoul on 2010-02-17
Alright set limit on router to 25 and address in interfaces to 30 and I'm still getting the same error. I've got an address for a DMZ server, would that help? also my password information is still not in interfaces, if that's making a difference...

---

### Post by woodsonoversoul on 2010-02-17
now iwlist scan isn't bringing back any results either...

---

### Post by woodsonoversoul on 2010-02-17
when I enter 'iwconfig' I get:
```
ra0    RT2860 Wireless ESSID:"" Nickname:"RT2860STA"
       Mode: Auto Frequency=2.437 GHz  Bit Rate=1 Mb/s
       RTS thr:off  Fragment thr:off
       Link Quality=48/100 Signal level:-86 dBm Noise level:-97 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

If that helps at all...

---

### Post by chili555 on 2010-02-17
> I'm using addresses provided by network connection information from another linux machine connected to the wireless networkWould you please go to that machine and run:```
ifconfig
route -n
```Please post it here.> also my password information is still not in interfaces, if that's making a difference...We will need to get that sorted out, but we should be able to get all the errors solved without it. We just won't be able to actually connect without authentication from the router.

---

### Post by woodsonoversoul on 2010-02-17
ifconfig = 
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4890 (4.8 KB)  TX bytes:4890 (4.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:cc:47:5a  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fecc:475a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4919202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2613952 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4252506865 (4.2 GB)  TX bytes:248604791 (248.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-CC-47-5A-37-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

/CODE]

route -n =
[CODE]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by chili555 on 2010-02-17
> auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.1.30
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ourhouse

iface eth0 inet dhcpBased on the route, netmask, etc. on the other machine, I feel these settings, along with encryption settings, are correct. Now please tell me what this tells us on the little netbook server:```
route -n
```I hope the gateway is 192.168.1.1. If it is, please restart networking and let me know if the error persists.

---

### Post by woodsonoversoul on 2010-02-17
route -n gives us:
```
Kernal IP routing table
Destination    Gateway        Genmask          Flags  Metric
192.168.1.0    0.0.0.0        255.255.255.0    U      0
0.0.0.0        192.168.1.1    0.0.0.0          UG     100

Ref  Use  Iforce
0    0    ra0
0    0    ra0
```

---

### Post by woodsonoversoul on 2010-02-17
And the same errors are present on a network restart. Could it be something about drivers? I know I've had problems with linux and drivers on this machine before...

---

### Post by chili555 on 2010-02-17
In post #13, it was: SIOCDELRT: No such process

In post #15, it was: Error for wireless request "Set ESSID" 

Which is it now? If it is ESSID, please try amending /etc/network/interfaces to enclose the name of your network in quotes:```
--- snip ---
wireless-essid [COLOR="Red"]"[/COLOR]ourhouse[COLOR="Red"]"[/COLOR]
--- snip ---
```> Could it be something about drivers?What does *lshw* say the driver is?

---

### Post by chili555 on 2010-02-17
Please try another approach:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.1.30
netmask 255.255.255.0
gateway 192.168.1.1
    pre-up iwconfig ra0 essid "ourhouse"
    pre-up iwconfig ra0 mode managed

iface eth0 inet dhcp 
```Then restart networking and let me know.

---

### Post by woodsonoversoul on 2010-02-17
It's the ESSID error, quotation marks don't help

---

### Post by chili555 on 2010-02-17
> **woodsonoversoul said:**
> It's the ESSID error, quotation marks don't helpPlease see post #39.

---

### Post by woodsonoversoul on 2010-02-17
lshw shows the driver as rt2860

---

### Post by woodsonoversoul on 2010-02-17
I was getting the ESSID error twice, now I'm only getting it once followed by "Failed to bring up ra0"

---

### Post by woodsonoversoul on 2010-02-17
lshw -C network list both ra0 and eth0 as disabled

---

### Post by chili555 on 2010-02-17
It looks like the Ralink cards require slightly unique settings. I was checking here: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

I'll check back tomorrow.

---

### Post by woodsonoversoul on 2010-02-17
Thanks man

---

### Post by woodsonoversoul on 2010-02-17
When I run ifconfig the output for both eth0 and ra0 have fields marked RX and TX with mb/b/kb next to them, does that mean I'm somehow receiving and transmitting?

---

### Post by woodsonoversoul on 2010-02-18
Any ideas?

---

### Post by woodsonoversoul on 2010-02-18
bump for new crowd...

---

### Post by woodsonoversoul on 2010-02-18
It looks like everything is working now, I still can't use use 'sudo apt-get install update' though... What should I be checking?

---

### Post by chili555 on 2010-02-18
> **woodsonoversoul said:**
> It looks like everything is working now, I still can't use use 'sudo apt-get install update' though... What should I be checking?Please try:```
sudo apt-get update
```the word 'install' is used to install a package, such as:```
sudo apt-get install skype
```If it still doesn't work, please try:```
ping -c3 www.google.com
ping -c3 192.168.1.1
```Thanks.

---

