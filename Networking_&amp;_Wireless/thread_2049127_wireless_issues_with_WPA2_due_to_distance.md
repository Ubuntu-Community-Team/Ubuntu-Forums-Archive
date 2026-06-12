---
title: "wireless issues with WPA2 due to distance"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by Oxyris on 2012-08-28
Went back to school and found that my "new" (to me anyway) laptop can't connect to wifi. It works if it's close to the router but past 30 or so feet it doesn't pick it up. Apparently I have the same issue in my house, I just didn't notice because it's much smaller (though because I've been messing with it so much it has stopped working unless I'm in the same room as the router) than a big university.

Some info if needed:

```
sudo lshw -C network
[sudo] password: 
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1d:72:8e:26:f7
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:f8200000-f821ffff memory:f8225000-f8225fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:a3:95:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.2.0-29-generic-pae firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:f7f00000-f7f01fff
ubuntux61tablet:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

ubuntux61tablet:~$ 

```

---

### Post by chili555 on 2012-08-28
Please open a terminal and do:```
sudo modprobe -r iwl4965
sudo modprobe iwl4965 11n_disable=1
```Any improvement?

---

### Post by Oxyris on 2012-08-28
> **chili555 said:**
> Please open a terminal and do:```
sudo modprobe -r iwl4965
sudo modprobe iwl4965 11n_disable=1
```Any improvement?

Yes, it started working almost immediately. I'll check to make sure it's working in different buildings and then I'll modify the prefix. Thank you.

---

### Post by chili555 on 2012-08-28
> then I'll modify the prefix. How so? There is a right, effective way to do it. What are you planning?

---

### Post by Oxyris on 2012-08-28
> **chili555 said:**
> How so? There is a right, effective way to do it. What are you planning?
I meant change the title of the post to solved. Sorry for the confusion.


P.S. I'm not usually a technical user but if you don't mind, could you explain what I just did to my computer?

---

### Post by chili555 on 2012-08-28
You asked that the wireless driver iwlwifi be removed and then be reloaded with a parameter '11n_disable.' As you might see, it disables N speed capability. It is the subject of a long-standing bug.

What I was driving at is that the parameter disappears on reboot unless you take steps to make it persistent, which I assume you want. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. If you don't have the text editor gedit, use leafpad, kate or any other text editor.

You should be all set.

---

### Post by Oxyris on 2012-08-28
To make sure: I rebooted my computer earlier am I supposed to ```
sudo modprobe -r iwl4965
sudo modprobe iwl4965 11n_disable=1
```
Then do this
```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```
Or can I get away with just starting at the second part?

---

### Post by chili555 on 2012-08-28
Once you have written the file /etc/modprobe.d/iwlwifi.conf, then the driver parameter will be loaded automatically with no further action on your part. Once it's written, reboot and you are permanently all done.

---

### Post by Oxyris on 2012-08-28
> **chili555 said:**
> Once you have written the file /etc/modprobe.d/iwlwifi.conf, then the driver parameter will be loaded automatically with no further action on your part. Once it's written, reboot and you are permanently all done.

Well, it was working and now it's not. I'll see what else I can do to fix it but thanks a bunch for your help.

---

### Post by chili555 on 2012-08-29
Let's be sure there are no typos in the file:```
cat /etc/modprobe.d/iwlwifi.conf
```Let's also see if the parameter got accepted:```
cat /sys/module/iwlwifi/parameters/11n_disable
```

---

### Post by Oxyris on 2012-08-29
> **chili555 said:**
> Let's be sure there are no typos in the file:```
cat /etc/modprobe.d/iwlwifi.conf
```Let's also see if the parameter got accepted:```
cat /sys/module/iwlwifi/parameters/11n_disable
```

Results:
```

@ubuntux61tablet:~$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1
@ubuntux61tablet:~$ cat /sys/module/iwlwifi/parameters/11n_disable
cat: /sys/module/iwlwifi/parameters/11n_disable: No such file or directory
```

---

### Post by chili555 on 2012-08-29
Ole Dr. Chili makes an occasional error. I'm sorry. Please do:```
sudo rm /etc/modprobe.d/iwlwifi.conf
sudo gedit /etc/modprobe.d/iwl4965.conf
``` Add a single line:```
options iwl4965 11n_disable=1
```Proofread, save, close and reboot and let me hear your forgiveness and a good report.

---

### Post by Oxyris on 2012-08-30
It seems to be working okay for now. I have to start it up with the hard switch off then turn on the wifi but that's just a minor inconvenience.

---

