---
title: "Wireless network available and &quot;connected&quot; but no internet"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by ronlie on 2011-04-23
I installed ubuntu 10.10 on a samsung N140.
I have a “working” wireless connection, but the browser and other applications do not connect to internet.
All the wireless settings are the same as on my other laptop with also ubuntu 10.10
I tried in the terminal: ping -c 4 [www.google.com](www.google.com)
The result is ping:unknown host [www.google.com](www.google.com)
When I use a wired connection everything works perfect!
Can anbody help me?

---

### Post by leclerc65 on 2011-04-23
Do
sudo apt-add-repository ppa:voria/ppa 
sudo apt-get-update

Go to Synaptics, put "samsung" into the search field and install all packages with "samsung" in the name, or at least "samsung-wireless".

---

### Post by ronlie on 2011-04-23
> **leclerc65 said:**
> Do
sudo apt-add-repository ppa:voria/ppa 
sudo apt-get-update

Go to Synaptics, put "samsung" into the search field and install all packages with "samsung" in the name, or at least "samsung-wireless".

With  the second command sudo apt-get-update I get the message:command not found

I then tried Synaptics and installed everything with samsung.
But still no working wifi connection.

---

### Post by jramshu on 2011-04-23
Don't put the hyphen after "get"
```
sudo apt-get update
```

---

### Post by KegHead on 2011-04-23
Hi!

Have you tried clicking on the internet icon on the top right and select?

Try this:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

KegHead

---

### Post by leclerc65 on 2011-04-23
Hi KegHead.
I am sorry for the typo, as pointed out by the other posters.
I should also mention that you have to run these commands with your wired internet cable connected.

---

### Post by dineshs on 2011-04-24
> I tried in the terminal: ping -c 4 [www.google.com](www.google.com)Did you try```
ping -c4 4.2.2.1
```.If you get reply,set DNS manually via network manager.(Rightcklick network manager icon edit connections-wireless-select the device and edit-ipv4-Automatic(DHCP) addresses only-enter DNS as 4.2.2.1 and apply.

---

### Post by ronlie on 2011-04-25
> **leclerc65 said:**
> Do
sudo apt-add-repository ppa:voria/ppa 
sudo apt-get-update

Go to Synaptics, put "samsung" into the search field and install all packages with "samsung" in the name, or at least "samsung-wireless".

So far I have tried:
(with a wired connection)
sudo apt-add-repository ppa:voria/ppa 
sudo apt-get update
sudo apt-get upgrade -f
sudo apt-get dist-upgrade -f
sudo apt-get install linux-image -f
Installed all the samsung packages with Synaptics
Rebooted the computer.
Removed the wired connection: the wifi connection then shows as connected.
I tried ping -c4 4.2.2.1
results:
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

What else can I do? I don't want to go back to windows....

---

### Post by ronlie on 2011-04-25
> **KegHead said:**
> Hi!

Have you tried clicking on the internet icon on the top right and select?

Try this:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

KegHead

So far I have tried:
(with a wired connection)
sudo apt-add-repository ppa:voria/ppa 
sudo apt-get update
sudo apt-get upgrade -f
sudo apt-get dist-upgrade -f
sudo apt-get install linux-image -f
Installed all the samsung packages with Synaptics
Rebooted the computer.
Removed the wired connection: the wifi connection then shows as connected.
I tried ping -c4 4.2.2.1
results:
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

What else can I do? I don't want to go back to windows....

---

### Post by dineshs on 2011-04-25
How do you connect to internet? Do you use DSL tab in Network manager?
Please post the results of ```
sudo lshw -C network
``````
route -n
```and ```
iwconfig
```(wired disconnected wireless connected)

---

### Post by ronlie on 2011-04-25
> **dineshs said:**
> How do you connect to internet? Do you use DSL tab in Network manager?
Please post the results of ```
sudo lshw -C network
``````
route -n
```and ```
iwconfig
```(wired disconnected wireless connected)

These are the results:


**_sudo lshw -C network_ **
  *-network               
       description: Wireless interface 
       product: AR9285 Wireless Network Adapter (PCI-Express) 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 01 
       serial: 00:26:b6:25:1d:0d 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A ip=192.168.0.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:16 memory:f0100000-f010ffff 
  *-network 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:24:54:0f:67:36 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical 
       configuration: broadcast=yes driver=r8169 latency=0 multicast=yes 
       resources: irq:42 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff 


**_route -n_**
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0 
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0 


**_iwconfig_** 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:"Sitecom67E618"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:F6:67:E6:18   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by bobo747 on 2011-04-25
hello I am the ubuntu beginner user. I installed ubuntu 9.10. I connected the wireless. I got DHCP address and connect. And I open the Mozilla, Mozilla Don't work. And try again to run mozilla. Mozilla is working. but no Internet. So, I type ping 192.168.0.251(that's gateway) in the terminal. I got 1 reply in Gateway and next other ping are 192.1680.101. I don't know why. My Network Detail is
Ipaddress 192.168.0.67
Subnetmask 255.255.255.0
Gateway 192.168.0.251
Primary DNS 203.81.162.22
Secondary DNS 203.81.162.23

Please help me how to fix this step by step. I am new user of ubuntu.
My English is so poor. Sorry for that.

---

### Post by KegHead on 2011-04-25
Hi!

Check this out this thread;

[http://ubuntuforums.org/showthread.php?t=1348253](http://ubuntuforums.org/showthread.php?t=1348253)

KegHead

---

### Post by leclerc65 on 2011-04-25
> **ronlie said:**
> 

What else can I do? I don't want to go back to windows....
Go to System Administration/Hardware Drivers
Do you see anything ?

---

### Post by ronlie on 2011-04-25
> **dineshs said:**
> How do you connect to internet? Do you use DSL tab in Network manager?
Please post the results of ```
sudo lshw -C network
``````
route -n
```and ```
iwconfig
```(wired disconnected wireless connected)

> **leclerc65 said:**
> Go to System Administration/Hardware Drivers
Do you see anything ?

It shows: Samsung backlight driver

---

### Post by ronlie on 2011-04-25
> **leclerc65 said:**
> Go to System Administration/Hardware Drivers
Do you see anything ?

It shows: Samsung backlight driver

---

### Post by dineshs on 2011-04-25
Can you ```
ping 192.168.0.1 -c3
```

bobo747,
Please start a new thread with the output of the following commands
```
cat /etc/network/interfaces
route -n
```

---

### Post by ronlie on 2011-04-29
[QUOTE=dineshs;10720437]Can you ```
ping 192.168.0.1 -c3
```

Dinesh,
The result is:

ping 192.168.0.1 -c3 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 

--- 192.168.0.1 ping statistics --- 
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

---

### Post by ronlie on 2011-04-30
> **KegHead said:**
> Hi!

Check this out this thread;

[http://ubuntuforums.org/showthread.php?t=1348253](http://ubuntuforums.org/showthread.php?t=1348253)

KegHead

Hi Keghead,

My wifi works now! Thanx!

---

### Post by ronlie on 2011-04-30
> **ronlie said:**
> Hi Keghead,

My wifi works now! Thanx!

Damned, I was optimistic.
It's not working now!

The only thing I did was install updates when the update manager popped up. 

I tried the whole procedure again, but this time no connection. 
The wifi is "connected" but no internet connection.
Got any more suggestions?

---

### Post by Mangus 1282 on 2011-08-08
I am having the same problem only mine is wired trying to get mine to work also. I am a new user

---

