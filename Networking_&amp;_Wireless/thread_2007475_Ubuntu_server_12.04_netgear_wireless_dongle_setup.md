---
title: "Ubuntu server 12.04: netgear wireless dongle setup"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by Toxic Tom on 2012-06-20
I am trying to setup a lamp server to work with a netgear wireless dongle I have. Ubuntu has recognized the dongle and it's logical name is wlan0. I'm not sure how to connect it to a network. The ubuntu server has come up in the dhcp server area of my router software (although I'm not sure if that is from using it with a wired connection earlier). I am trying to access my server through openSSH (already installed) from another device. This has been my only way of telling if the server is connected to the internet. Is there another way to tell? Also there is no server software installed yet, only openSSH.

---

### Post by chili555 on 2012-06-20
Your wireless is not going to connect to anything until you tell it what secure network you want to connect to and the encryption key. The usual way in a server not running a windowing manager and not running Network Manager, is to configure /etc/network/interfaces something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
    wpa-ssid mynetwork
    wpa-psk mysecretkey
dns-nameservers 8.8.8.8 8.9.192.whatever
```Then reload:```
sudo ifdown wlan0 && sudo ifup wlan0
```Check:```
ping -c3 www.google.com
```

---

### Post by Toxic Tom on 2012-06-21
Thanks for your help, although my network has a wep key, do you have to write something different if you have a wep key?

---

### Post by chili555 on 2012-06-21
> **Toxic Tom said:**
> Thanks for your help, although my network has a wep key, do you have to write something different if you have a wep key?Yes; you log on to your router and change it to WPA2. WEP is about as secure as putting your credit card in a shoebox on the front porch. If, however, you love to live on the wild side, try this:```
auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid mynetwork
wireless-key mysecretkey 
dns-nameservers 8.8.8.8 8.9.192.whatever
```

---

### Post by Toxic Tom on 2012-06-21
Also what do I put in the DNS name servers bit?

---

### Post by chili555 on 2012-06-21
What are the DNS nameservers on other computers on the network? You can safely use Google's service 8.8.8.8 and/or the router's IP address; something like 192.168.1.1.

Make sure the static IP address is outside the address range used in the router. In the attached example, the DHCP server assigns up to 50 addresses starting at 192.168.1.100. Therefor, the first static IP address I suggest you use is 192.168.1.151.

---

### Post by Toxic Tom on 2012-06-21
Thanks so much for your help! Now I'll test it! :)

---

### Post by Toxic Tom on 2012-06-22
It's still not working. The light on the dongle has lit up, the result of sudo lshw -C network says link=yes but the ping just isn't working! unknown host [www.google.com](www.google.com) although it works fine with the wired connection. 

So what do I do now?

---

### Post by Toxic Tom on 2012-06-22
Also, every so often I get the error "ieee80211 phy0 invalid plcp cck rate (0)" with a different number code before it each time...?

---

### Post by Toxic Tom on 2012-06-22
Now I can see my Ubuntu server in the list of wireless clients in my router software (now I changed the static ip to dhcp, not ideal though!)

---

### Post by chili555 on 2012-06-22
> **Toxic Tom said:**
> Now I can see my Ubuntu server in the list of wireless clients in my router software (now I changed the static ip to dhcp, not ideal though!)And will it connect? If so, please post:```
ifconfig
route -n
```Did you change to DHCP like this?```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by Toxic Tom on 2012-06-22
> **chili555 said:**
> Did you change to DHCP like this?```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
```

Yeah I did. I still can't seem to ping though, even using dhcp.

---

### Post by chili555 on 2012-06-22
Rats! I made a mistake. It should be:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid mynetwork
wireless-key mysecretkey 
dns-nameservers 8.8.8.8 8.9.192.whatever
```Is that what you did? If not, please amend and then do:```
sudo ifdown wlan0 && sudo ifup wlan0
```You ought to see dhclient ask for an IP address and get one or not. If not, we ought to see informative messages.

---

### Post by Toxic Tom on 2012-06-22
Yep that's what I did. I don't really wanna use dhcp though, I wanna have a static ip!
The assigned ips on my router go up to 192.168.1.200 so I set it to 192.168.1.201 so why won't it work?

---

### Post by chili555 on 2012-06-22
When it's temporarily set to DHCP, what are the messages, errors, warnings, etc. when you:```
sudo ifdown wlan0 && sudo ifup wlan0
```

---

### Post by Toxic Tom on 2012-06-23
If wlan0 is already up then it just says ssh stop/waiting ssh start/running. But if wlan0 is down before I do it it says "RNETLINK answers: No such process ssh stop/waiting ssh start/running" and the wireless dongle flashes few different colours before settling on blue.

EDIT: that's what happens when I try to use static. When using dhcp, I get the second result every time, without the RNETLINK error.

EDIT2: aha dhcp works now!! Just need to get static working.

---

### Post by chili555 on 2012-06-23
> EDIT2: aha dhcp works now!! Just need to get static working.Excellent! Check your IP address, gateway, etc. with:```
ifconfig
route -n
```Then adapt the settings to static and restart the interface:```
sudo ifdown wlan0 && sudo ifup wlan0
```Working now?

---

### Post by Toxic Tom on 2012-06-23
Result of ifconfig:
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3160 (3.1 KB)  TX bytes:3160 (3.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:3f:0e:eb:84
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:fe0e:eb84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:923461 (923.4 KB)  TX bytes:70380 (70.3 KB)
```

Result of route -n:
```
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
```

What do I do now?

---

### Post by chili555 on 2012-06-23
You've confirmed the IP range and gateway. I suggest you amend the interfaces file:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.201
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid mynetwork
wireless-key mysecretkey 
dns-nameservers 8.8.8.8 192.168.1.1
```Now restart the interface:```
sudo ifdown wlan0 && sudo ifup wlan0
```You will probably get no confirmations if there is no error or warning. Then check:```
ping -c3 www.google.com
```If you get ping returns, you're all set.

---

### Post by Toxic Tom on 2012-06-23
It's all setup and working now! Thanks for your help!

---

### Post by chili555 on 2012-06-23
Great work! Please use thread tools at the top and mark Solved. The searchers setting up their servers will appreciate your help.

---

### Post by Toxic Tom on 2012-06-23
Now my wireless dongle keeps switching itself off after a period of inactivity. Is there anything I can do about this?

---

### Post by chili555 on 2012-06-23
Please run:```
iwconfig
```What does it say about power management? If we can turn it off and it helps, we can make it permanent.```
sudo iwconfig wlan0 power off
```

---

### Post by Toxic Tom on 2012-06-24
Result of iwconfig:
```
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"OrangeED9600"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:01:E3:ED:96:02
          Bit Rate=36 Mb/s   Tx-Power=27 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

eth0      no wireless extensions.
```
Power management appears to be off

---

### Post by chili555 on 2012-06-24
Is your computer suspending after a period of inactivity? Can you check your power settings? Please see attached.

---

### Post by Toxic Tom on 2012-06-24
How can I check that from terminal?

---

### Post by chili555 on 2012-06-24
> **Toxic Tom said:**
> How can I check that from terminal?Hmmm, I forgot...a server on a laptop. Let's look at this from another viewpoint. Let's ask the system to reload the wireless driver on resume:```
sudo vim /etc/pm/config.d/config
```Since you are running a server, you do know vim, right?? Right?

Add one line:```
SUSPEND_MODULES="[COLOR="Red"]###[/COLOR]"
```Substitute your actual wireless driver. Find out with:```
sudo lshw -C network
```Here's an example from my computer:> *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       <snip>
       logical name: wlan0
       version: 35
       <snip>
       configuration: broadcast=yes [COLOR="Red"]driver=iwlwifi[/COLOR] driverversion=3.2.0-25-generic-pae firmware=9.221.4.1 build 25532 ip=192.168.1.108 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
So if I were writing the file, I'd substitute iwlwifi above.

Proofread, save and close vim. After a reboot, you will probably be all set.

---

### Post by Toxic Tom on 2012-06-24
It's not a laptop, it's a desktop pc and no I don't know vim :P

I'll give that stuff a go though, thanks!

---

### Post by Toxic Tom on 2012-06-30
I don't have a file called /etc/pm/config.d/config

What can I do about that?

---

### Post by chili555 on 2012-06-30
The intent here is that you are writing the file from scratch as I outlined.

---

### Post by Toxic Tom on 2012-06-30
Ok now, I have created that file with the content you told me to put in it, it should be up and running now!

---

### Post by Toxic Tom on 2012-06-30
It's all working now! Thanks for the help!

---

