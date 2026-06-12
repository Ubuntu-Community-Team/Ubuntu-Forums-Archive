---
title: "Problem with kismet &quot;FATAL: channel get ioctl failed 22:Invalid argument&quot;"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by vinte on 2010-11-08
Hi all, 
I installed kismet but i couldn't run it. Also google couldn't help me more. Here is my problem:

myuser@mypc:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Intel): Enabling monitor mode for iwl3945 source interface wlan0 channel 6...
FATAL: channel get ioctl failed 22:Invalid argument
Done.


* iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

          
* lshw -C network
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:8e:46:94
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-22-generic firmware=15.32.2.9 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:edf00000-edf00fff


* kismet.conf
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwl3945,wlan0,Intel


ubuntu 10.10
kismet 2008.05.R1


Pls help me fix it.
Thanks a mil.

---

### Post by gomer on 2010-11-10
Funny. I use the same card, and it was working for me under 9.04, and now I get the same issues with 9.10 ... 

I'm stumped, too. Kismet's documentation is ... well, it's not the clearest.

---

### Post by vinte on 2010-11-12
Thanks for your reply. We are the same.
Somebody helps us. :)

---

### Post by chili555 on 2010-11-12
Is the behavior improved if you do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo kismet
```

---

### Post by vinte on 2010-11-17
> **chili555 said:**
> Is the behavior improved if you do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo kismet
```

It's awsome. Worked like a charm.
Thanks a mil.:P

---

### Post by pestie on 2010-11-18
I am having that exact same problem after my upgrade to 10.10 (10.04 worked perfectly) and the above trick does not work for me. Despite iwconfig showing my card in monitor mode, Kismet still throws that same error. airodump-ng works just fine, however, so something's definitely not right with Kismet. I am also using the iwl3945 driver. Any ideas?

UPDATE: Kismet runs fine on the same machine, but with an rtl8187-based device, so it looks like this is a problem with the iwl3945.

---

### Post by chili555 on 2010-11-18
My iwl3945 works perfectly with kismet in 10.10. Would you care to troubleshoot a bit?

---

### Post by pestie on 2010-11-18
Sure, I'll gladly try whatever troubleshooting you can suggest.

---

### Post by chili555 on 2010-11-18
> **pestie said:**
> Sure, I'll gladly try whatever troubleshooting you can suggest.What does your kismet.conf sources line look like?

---

### Post by pestie on 2010-11-18
```
source=iwl3945,wlan0,intel
```It's the exact same line that used to work just fine in 10.04.

---

### Post by chili555 on 2010-11-18
> **pestie said:**
> ```
source=iwl3945,wlan0,intel
```It's the exact same line that used to work just fine in 10.04.How about this line? True, false or commented out?```
# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
#networkmanagersleep=true
```

---

### Post by pestie on 2010-11-18
It is true, and uncommented. Kismet should definitely be trying to put NetworkManager to sleep.

---

### Post by chili555 on 2010-11-19
I have been giving considerable thought to this issue. As you can see, the original poster uses the same card and my solution worked for him. In my case, I use the same card and don't even have to bring the interface down; I simply 'sudo kismet' and all is well.

I am posting this from another laptop using an Intel 2915ABG and it starts perfectly as well. Both are fully updated 10.10 machines.

Therefore, I don't think it's an obvious Kismet issue, nor a Kismet vs. 3945ABG issue. I wonder if it's a Kismet with 3945ABG and Network Manager issue. My 3945ABG machine is a stay-at-home that only needs to connect to my network. It, therefor has had NM removed.

You might try:```
sudo stop network-manager
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo kismet
```Another suggestion is to download and compile a newer version of Kismet. My version, from the Ubuntu repositories, is 2008.05.R1
. On their site, they show the latest version as 2010-07-R1. If you decide to do that and get stuck, I'll be glad to help.

If stopping NM and taking down the interface doesn't help, I'd post a bug here: [http://www.kismetwireless.net/](http://www.kismetwireless.net/)

I have compiled and not yet configured the latest version. The process is not trivial.

---

### Post by pestie on 2010-11-20
Well, I give up - I can't explain it. No combination of stopping network manager, downing the interface, and/or forcing monitor mode helped.

I'm going to try booting an Ubuntu 10.10 live CD and see if maybe there's something about the fact that I did an upgrade from 10.04 that's causing this. If that fails, I'll try building the new Kismet. The one in the Ubuntu repositories is the old branch; the new one has a whole new user interface (which isn't quite as nice, in my opinion) and is more stable and somewhat easier to configure as far as sources go. I've used it on another platform. I've compiled Kismet from source before, too - it's a pain, but it's doable. I've got a fair amount of experience compiling software from source, so I should be able to do it without too much trouble.

I very much appreciate all the help you've offered - thanks!

---

### Post by chili555 on 2010-11-20
A couple of hints: this build is a bit different, ./configure, make, sudo make install. There are some other options available which I ignored. Also, it may complain in ./configure about missing packages that you know you have. Mostly, it wants the -dev package.

We will be interested in your progress.

---

### Post by pestie on 2010-12-26
Well, it took me a while to get around to playing with Kismet again, but I thought I'd at least come back here and report on my success. After downloading and compiling Kismet 2010-07-R1, it works perfectly fine with my Intel card. I still haven't a clue why the stock Ubuntu version fails, but there you have it.

Compiling the new Kismet wasn't really very hard, either. I needed build-essential, libpcap-dev, libnl-dev, libpcre3-dev, libncurses5-dev, and possibly libncursesw5-dev (I installed it for good measure). I did the "make install" phase with checkinstall, so I can at least manage Kismet as a Debian package rather than just having the install script spew a bunch of files all over /usr/local.

---

