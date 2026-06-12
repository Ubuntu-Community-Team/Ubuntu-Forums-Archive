---
title: "Kismet and Aircrack (easy question)"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by warmnscsi on 2010-01-10
Alright, I know there are many tutorials and threads about getting these programs to work so I didn't want to flood the internet with one more post but no matter what I still can't figure this stuff out and I've spent hours.

I installed kismet through synaptic, I am unsure how to configure the kismet.conf file. I'm there, I opened using sudo gedit and I can't remember how to check what my wireless device is in terminal. I've tried multiple google searches to find out how to find out what wireless device I have using terminal and I can't find anything.

I also installed aircrack through synaptic but I'm completely lost with that. These step by step tutorials never work the way they are supposed to and I'm getting frustrated. Please help, thanks. And sorry for another noob post. :oops:

---

### Post by changingstate on 2010-01-10
sudo lshw -C network

Should post up some lovely information about your networking hardware. Failing that, lspci and lsusb should help you.

---

### Post by chili555 on 2010-01-10
Here's a kwik n durty primer. First, here is the relevant part of my /etc/kismet/kismet.conf:```
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=[COLOR="Red"]ipw2200[/COLOR],[COLOR="Blue"]eth1[/COLOR],Intel
```Next, here is the relevant part of my lshw:```
 *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: [COLOR="Blue"]eth1[/COLOR]
       version: 05
       serial: 00:16:6f:9a:5f:df
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=ipw2200[/COLOR]
       --- snip ---
```I am not sure the Intel part makes much difference. I suggest using something related to your wireless card; Atheros or Ralink or whatever.

---

### Post by warmnscsi on 2010-01-10
Thanks for all the great replies, I'm saving all these terminal commands into a document. Well this is what I've found,

```
*-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 1c:4b:d6:20:2a:3d
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=156.168.0.101 laten
```

So following the example I put in kismet.conf:

```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ath9k,wmaster0,wifi
```

Only to get this error when I attempt to run kismet:

```
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
```

and

```
FATAL: Unknown capture source type 'ath9k' in source 'ath9k,wmaster0,wifi'
Done.
```

and I get that same error when I try to put in AR9285, and I get that trying to run 'kismet' or 'sudo kismet' so I looked up the first error and it turns out I need to compile it with suid-priv dropping enabled so I was attempting to re install using the read me instructions (for the 5th time) and when I run ./configure everything looks good until the end I get:

```
configure: error: Failed to find libcurses or libncurses.
```

So I looked up libncurses into synaptic and it tells me I already have libncurses5 and libncursesw5. I'm at a loss for what to do next at this point. If you read all that I want to say thank you, even if you don't post a response - lol. Thanks for the help so far.

---

### Post by warmnscsi on 2010-01-10
Nevermind on the libncurses error I found two other dev files that werent installed, sure enough it stopped giving me that error but now its giving me a libpcre and libpcap error so I'm going to attempt to get those as well.

Edit: Current errors that I cant fix by googling,

```
configure: WARNING: Using local radiotap headers
```

```
configure: WARNING: linux/if_arp.h: present but cannot be compiled
configure: WARNING: linux/if_arp.h:     check for missing prerequisite headers?
configure: WARNING: linux/if_arp.h: see the Autoconf documentation
configure: WARNING: linux/if_arp.h:     section "Present But Cannot Be Compiled"
configure: WARNING: linux/if_arp.h: proceeding with the preprocessor's result
configure: WARNING: linux/if_arp.h: in the future, the compiler will take precedence

```

```
config.status: WARNING:  'Makefile.inc.in' seems to ignore the --datarootdir setting

```

---

### Post by chili555 on 2010-01-10
Before you tear out all your hair compiling. please see here: [http://www.kismetwireless.net/Forum/General/Messages/1231702725.208456](http://www.kismetwireless.net/Forum/General/Messages/1231702725.208456)

Please change this:> # YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ath9k,wmaster0,wifiTo this:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ath5k,wlan0,Atheros
```Now run:```
sudo kismet
```Please let us know.

---

### Post by warmnscsi on 2010-01-10
:D :D :D

You sir, have gone out of you way to help me. It's people like you who really make this forum a great place for linux newbies.I wish this forum had some type of kudo's program set up. It was also a pretty good learning experience. I can't believe after all that I just didnt have the config right, I even looked all over to find the right syntax for it to work with my chip. Anyway, thanks again. Now I can finally do some testing on my wifi.

One small thing, my chip will stay in monitoring mode after I use capital Q to quit the program. Is there a fix? If not, restarting is just a minor nuisance that I can live with compared to just getting it to work.

---

### Post by chili555 on 2010-01-10
You probably can do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```Thank you for your kind comments!

---

### Post by warmnscsi on 2010-01-10
> **chili555 said:**
> You probably can do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```Thank you for your kind comments!


Perfect, works like a charm. Now all I need to do is figure out how to do all that auto-magically with a bash script. Don't tell me! I want to figure this one out on my own :D

---

