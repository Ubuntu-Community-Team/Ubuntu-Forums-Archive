---
title: "jaunty drops wireless connections without notification"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by glubbdrubb on 2009-07-07
This problem began after I formatted and installed Jaunty. With out any message saying my wireless connection is lost, I would not be able to communication with the internet. Web pages wont load, pinging ip addresses wont work. I have manually reconnect the connection or disconnect and reconnect the wireless dongle. 

This would happen in the middle of downloads or updates and my only clues are that it wont download and the network traffic in system monitor goes to zero or very close.

Please help.

I would past the outputs from the commands listed in the post about how to post wireless questions but most of them don't output **anything**

---

### Post by The Toxic Mite on 2009-07-07
Hmm.

Try again with the following terminal commands:

```

lshw -c network
iwconfig

```

See if you get any output there :)

---

### Post by glubbdrubb on 2009-07-07
```
  
  *-network               
      
  *-network:2
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0e:2e:49:2c:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11bg

```

```
wlan0     IEEE 802.11bg  ESSID:"CSIR Lab 02"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:ED:A6:AF:66   
          Bit Rate=54 Mb/s   Tx-Power=7 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by superprash2003 on 2009-07-08
take a look at this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by glubbdrubb on 2009-07-08
Thanks, I will close this thread if possible. A search did not bring up that that thread earlier.

---

### Post by glubbdrubb on 2009-07-13
Alrighty then, problem solved. If this was Windowz I would have had to reformat and install by now.


I have found a configuration that works for me:

I am using 2.6.28-13 (32 bit)

I installed linux-backports-modules-jaunty

I installed WICD (which replaced Network Manager automatically)

Then I restarted the PC

I have been using this configuration for about 3 days now and I have not had one cut-off since.

---

