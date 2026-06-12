---
title: "Wireless Won't connect after having shut laptop lid without restart"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by idcrewdawg on 2012-12-18
Greetings all. I've got a very minor problem with my wireless.

System info:

Linux -HP-Pavilion-dv7-Notebook-PC 3.2.0-34-generic-pae #53-Ubuntu SMP Thu Nov 15 11:11:12 UTC 2012 i686 i686 i386 GNU/Linux

My problem:

Wireless works well without disconnects except when I close the lid, and reopen it without shutting down the computer. Closing the lid turns off the screen and locks the computer. Once I reopen, and login my wireless can't reconnect to my router. The only way I've found to fix the issue is restarting the computer. I'd rather not do this if I can avoid it.

Anyone familiar with the issue who can help it would be appreciated.

---

### Post by chili555 on 2012-12-18
You might try this: [http://ubuntuforums.org/showpost.php?p=11694361&postcount=13](http://ubuntuforums.org/showpost.php?p=11694361&postcount=13)

Find out your wireless driver with:```
sudo lshw -C network
```For example:> *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: xx:yy:zz
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwlwifi [/COLOR]driverversion=3.5.0-19-generic firmware=9.221.4.1 build 25532 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:f2400000-f2401fff
If I were going to create the file, I'd substitute *iwlwifi*. Yours will be different.

*lshw* takes a few moments, please be patient. This technique sometimes, but not always works.

---

### Post by idcrewdawg on 2012-12-18
So if I understand everything correctly. Here is the results of the wireless driver inquiry.

> *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 08:2e:5f:86:b2:f5
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:49 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:92:2b:64
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR="Red"]iwlwifi[/COLOR] driverversion=3.2.0-35-generic-pae firmware=41.28.5.1 build 33926 ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:52 memory:c4500000-c4501fff


I should replace the highlighted phrase with [COLOR="red"]lshw[/COLOR].

My next question would be.... Where do I modify that setting?

---

### Post by chili555 on 2012-12-18
> I should replace the highlighted phrase with lshw.No. You should create a new file from scratch, like this:```
sudo gedit /etc/pm/config.d/config
```A new empty file will open in the text editor. Add one line:```
SUSPEND_MODULES="iwlwifi"
```Proofread, save and close the text editor. After a reboot, see if your wireless comes to life upon opening your lid and logging in.

---

### Post by idcrewdawg on 2012-12-19
I added the config file, rebooted and logged in, then closed lid and opened lid and relogged in. The added code didn't seem to fix the problem.

I sure appreciate your help on this. You just recently helped my wife with a wireless issue, and she's not had any problems since. So I have high faith in your expertise!

I'm willing to try whatever modification is needed next.

---

### Post by chili555 on 2012-12-19
I'm not too sure what to try next. Let's do some diagnostics. Close the lid and open it and log in. Run this command and post the result:```
rfkill list all
lsmod | grep -e iwl -e 802
ps aux | grep etwork
```Perhaps there is something else not loading.

Try to get your wireless back without rebooting with:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
sudo service network-manager restart
```We will be very interested in what combination of commands restarts the wireless, if any.

That funny pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by dannyboy79 on 2012-12-19
i have this same issue but it's intermitant, meaning sometimes the wifi card won't wake from sleep and sometimes it does. i don't have the same card as you though. Check your dmesg output, does it mention your wifi not being able to wake from deep sleep? when I get home later tonight, i'll post my wifi card chipset as I would also love a solution

---

### Post by chili555 on 2012-12-19
> **dannyboy79 said:**
> when I get home later tonight, i'll post my wifi card chipset as I would also love a solutionWe'll do the best we can.

---

### Post by idcrewdawg on 2012-12-19
I did all the diagnostic questions. The sudo commands did turn my wireless off, and back on. Though they restart didn't command the wireless to reconnect upon executing the restart command.

Due to the length of the text, I saved the results to a text file, and attached them.

I did find instances of "wake disable" in the dmesg results, but not smart enough on how they related to my wireless to know if that's the source of the problem.

Again, thanks so much for the help!

---

### Post by chili555 on 2012-12-20
> 40243.743945] iwlwifi 0000:07:00.0: Queue 0 stuck for 2000 ms. 
[40243.743959] iwlwifi 0000:07:00.0: Current read_ptr 0 write_ptr 3 
[40243.743965] iwlwifi 0000:07:00.0: On demand firmware reload 
[40244.023644] iwlwifi 0000:07:00.0: fail to flush all tx fifo queues 
[40244.024403] ieee80211 phy0: Hardware restart was requested I'm sure this is at least some of the problem. 

Here is a bug report about 'stuck queue' and it seems to be resolved by upgrading to 12.10. Perhaps you could try the live CD for 12.10 and see if the problem is resolved. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1009878](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1009878)

Another person reports that a router reset fixed the problem. Is your router set to N speeds? Can you try resetting it to B and G only to see if there is any improvement? You might also try:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. Reboot. Any improvement?

---

### Post by idcrewdawg on 2012-12-21
I did the upgrade first, and it didn't fix the problem. Then I tried adding the line to the config file. That disabled the wireless, but didn't allow it to re-enable after reboot.

The router reset also didn't have any effect.

I appreciate all the effort with this, and if it can't be fixed it's okay. I just don't close the lid.

---

### Post by chili555 on 2012-12-22
> Then I tried adding the line to the config file. That disabled the wireless, but didn't allow it to re-enable after reboot.I made a mistake. I apologize. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```*REMOVE* this line (and curse old Chili):```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. Now let's try it again and I will proofread my own work...twice!```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit.

Now reboot, accept my apologies and let us have your report.

---

### Post by idcrewdawg on 2012-12-22
That was it! Thanks a bunch!

---

### Post by chili555 on 2012-12-24
Glad it's working!

---

### Post by TecTef on 2013-01-12
I had the same issue and post #4 solved it for me. Thanks!

---

