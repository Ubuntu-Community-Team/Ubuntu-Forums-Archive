---
title: "HP/AtherosWireless/Ubuntu 8.10/Can't Connect After Update"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by SrEstroncio on 2009-02-27
Hello everyone at Ubuntu forums, I am having a small connection issue with Ubuntu 8.10 and I would really appreciate if someone could help me with some guidance.

Around two months ago I bought a new HP Pavilion (specs ahead) laptop on which I installed Ubuntu 8.10 x86-64. Even though the LiveCD was able to connect to the internet without any problems, after installing Ubuntu I started having wireless issues: Ubuntu did not detect any wireless networks and it seemed as if it didn't even recognize my wireless card. 

After a short while browsing these forums someone in here suggested me to install the **linux-backports-modules-intrepid-generic** package from the backports repository, after installing it Ubuntu started to recognize wireless signals and the Network Manager stopped graying out all the non-eth0 options. The led button on my laptop continued red (as if the wireless was still disabled) and had no effect when I pressed it.

After a while (about a month ago) new updates came along, I installed them (can't recall their names) and after rebooting I had no wireless connection and almost every option in the Network Manager was grayed out again.

I have been busy and ignoring the problem for the time being (using Vista right now,)but right now I really feel the urge to properly fix this issue so I can start using Ubuntu again. 

Even though any help will be **greatly** appreciated, more complete answers are encouraged with the purpose of making this thread useful to other people having similar issues and so that I might grasp what's wrong with my computer as I (hopefully) fix this, instead of just clicking and typing without learning anything in the process.

I apologize if this post might seem overly long (read: boring) and my writing unclear, English is not my mother tongue.

My laptop specs are: 

HP Pavilion dv5 Notebook PC.
AMD Turion X2 Ultra Dual-Core Mobile ZM-80 2.10 GHz 64 bits.
4 GB RAM.
ATI Radeon HD 3200 Graphics. 

Network adapters: 
Atheros AR5007 802.11 b/g WiFi Adapter
Realtek RTL8102E Family PCI-E Fast Ethernet NIC (NDIS 6.0)

Currenly running Ubuntu 8.10 x86-64 and Windows Vista 64 bits.

Thanks you for your attention in reading this long long post. Really thank you.

---

### Post by binbash on 2009-02-27
I am not using linux-backports-modules-intrepid-generic method to get my wireless working for my atheros but you have to reload your driver everytime you reboot with backports.

---

### Post by superprash2003 on 2009-02-27
try doing the same thing what you did earlier.. the backports...

---

### Post by smani on 2009-02-27
Did you ever search whether a driver is actually loaded for your wifi card? Specifically, look at the output of
```
sudo lshw
```
and look if it says UNCLAIMED in the section concerning the wifi card.
If so, you might want to try and load the module
```
sudo modprobe ath5k
#or
sudo modprobe ath9k
```
Look at [http://madwifi-project.org/](http://madwifi-project.org/) for more informations on the drivers and supported cards.
If you notice that the module is not automatically loaded at startup, you can add the module name to /etc/modules.

---

### Post by SrEstroncio on 2009-02-27
I'm sorry if this might seem like a stupid question, do I have to download and install ath5, ath9 or MadWifi before doing any of that? 
I'm going to go get myself a wired connection to try what smani suggested.

---

### Post by smani on 2009-02-27
If I am not mistaken ath9k is included in a default installation, ath5k is in the backports modules. To see if they are available on your system, type
```
modinfo module_name
```
it will either report that the module was not found or will give you information about the module. Madwifi (whose module is called ath_pci) should also be included by default.

---

### Post by SrEstroncio on 2009-02-28
I did the **sudo lshw** thing and it did say UNCLAIMED, so I did the **sudo modprobe ath5k** thing and then lshw-ed again, but it still said network UNCLAIMED: 

*-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

Info was returned when I did modinfo for ath5k, ath9k and ath_pci, by the way.

This is a screenshot of how things normally look (having no wireless and all):
[[IMG]http://img6.imageshack.us/img6/6007/drivers.th.png[/IMG]](http://img6.imageshack.us/my.php?image=drivers.png)

---

### Post by Reiger on 2009-02-28
> **binbash said:**
> I am not using linux-backports-modules-intrepid-generic method to get my wireless working for my atheros but you have to reload your driver everytime you reboot with backports.

No you haven't. You can configure the OS to automatically load it at boot time:
```

echo "ath5k" | sudo tee -a /etc/modules

```

/etc/modules is a list of instructions for drivers to load at boot time.

---

### Post by Reiger on 2009-02-28
> **SrEstroncio said:**
> I did the **sudo lshw** thing and it did say UNCLAIMED, so I did the **sudo modprobe ath5k** thing and then lshw-ed again, but it still said network UNCLAIMED: 

*-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

Info was returned when I did modinfo for ath5k, ath9k and ath_pci, by the way.

This is a screenshot of how things normally look (having no wireless and all):
[[IMG]http://img6.imageshack.us/img6/6007/drivers.th.png[/IMG]](http://img6.imageshack.us/my.php?image=drivers.png)

In order to see if your device is properly recognized, you should look at the output of:
```

ifconfig

```
That should list your wireless device.

Now if it doesn't do so at the modprobe ath5k command, try ensuring that nothing interferes:
```

sudo modprobe -r ath5k
sudo modprobe -r ath9k
sudo modprobe -r ath_pci

```
Then load it again & check output:
```

sudo modprobe ath5k
ifconfig

```

And if it still won't work it is time to collect log messages from the kernel about your driver:
```

dmesg | grep ath5k

```

---

### Post by Life On Mars on 2009-02-28
> **SrEstroncio said:**
> Hello everyone at Ubuntu forums, I am having a small connection issue with Ubuntu 8.10 and I would really appreciate if someone could help me with some guidance.

Around two months ago I bought a new HP Pavilion (specs ahead) laptop on which I installed Ubuntu 8.10 x86-64. Even though the LiveCD was able to connect to the internet without any problems, after installing Ubuntu I started having wireless issues: Ubuntu did not detect any wireless networks and it seemed as if it didn't even recognize my wireless card. 

After a short while browsing these forums someone in here suggested me to install the **linux-backports-modules-intrepid-generic** package from the backports repository, after installing it Ubuntu started to recognize wireless signals and the Network Manager stopped graying out all the non-eth0 options. The led button on my laptop continued red (as if the wireless was still disabled) and had no effect when I pressed it.

After a while (about a month ago) new updates came along, I installed them (can't recall their names) and after rebooting I had no wireless connection and almost every option in the Network Manager was grayed out again.

I have been busy and ignoring the problem for the time being (using Vista right now,)but right now I really feel the urge to properly fix this issue so I can start using Ubuntu again. 

Even though any help will be **greatly** appreciated, more complete answers are encouraged with the purpose of making this thread useful to other people having similar issues and so that I might grasp what's wrong with my computer as I (hopefully) fix this, instead of just clicking and typing without learning anything in the process.

I apologize if this post might seem overly long (read: boring) and my writing unclear, English is not my mother tongue.

My laptop specs are: 

HP Pavilion dv5 Notebook PC.
AMD Turion X2 Ultra Dual-Core Mobile ZM-80 2.10 GHz 64 bits.
4 GB RAM.
ATI Radeon HD 3200 Graphics. 

Network adapters: 
Atheros AR5007 802.11 b/g WiFi Adapter
Realtek RTL8102E Family PCI-E Fast Ethernet NIC (NDIS 6.0)

Currenly running Ubuntu 8.10 x86-64 and Windows Vista 64 bits.

Thanks you for your attention in reading this long long post. Really thank you.

Not sure if this will help you at all, but for what it's worth: in January 2009 I installed Intrepid on my wife's HP laptop, which has the AR5007 wireless card. 

I can't remember if I had to do any tweaking to get it to work, but it was working fine up until I updated the linux kernel headers to 2.6.27-12 earlier this week. 

I reverted back to 2.6.27-11 and it all works fine again.

---

### Post by SrEstroncio on 2009-02-28
Okay, this is what pops up when I type **ifconfig**:

eth0      Link encap:Ethernet  HWaddr 00:1e:68:89:9d:79  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe89:9d79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:890 errors:0 dropped:145771887 overruns:0 frame:0
          TX packets:596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:635889 (635.8 KB)  TX bytes:100349 (100.3 KB)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

I did the **sudo modprobe -r athXXX** commands. And then **sudo modprobe ath5k** again. But nothing seemed to have changed in the output of ifconfig.

This is the output of **dmesg | grep ath5k**:

srestroncio@lucifer:~$ dmesg | grep ath5k
[   17.492619] ath5k 0000:08:00.0: enabling device (0000 -> 0002)
[   17.492642] ath5k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.492669] ath5k 0000:08:00.0: setting latency timer to 64
[   17.492741] ath5k 0000:08:00.0: registered as 'phy0'
[   17.504549] ath5k phy0: failed to wakeup the MAC Chip
[   17.504549] ath5k 0000:08:00.0: PCI INT A disabled
[   17.504549] ath5k: probe of 0000:08:00.0 failed with error -5
[  338.708083] ath5k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  338.708115] ath5k 0000:08:00.0: setting latency timer to 64
[  338.708194] ath5k 0000:08:00.0: registered as 'phy0'
[  338.720045] ath5k phy0: failed to wakeup the MAC Chip
[  338.720045] ath5k 0000:08:00.0: PCI INT A disabled
[  338.720045] ath5k: probe of 0000:08:00.0 failed with error -5

Also, Life on Mars, how do I revert the the update?

---

### Post by Simyager on 2009-03-01
> **smani said:**
> Did you ever search whether a driver is actually loaded for your wifi card? Specifically, look at the output of
```
sudo lshw
```
and look if it says UNCLAIMED in the section concerning the wifi card.
If so, you might want to try and load the module
```
sudo modprobe ath5k
#or
sudo modprobe ath9k
```
Look at [http://madwifi-project.org/](http://madwifi-project.org/) for more informations on the drivers and supported cards.
If you notice that the module is not automatically loaded at startup, you can add the module name to /etc/modules.

I got with ath5k FATAL and something and as for the rest they didn´t do anything. I posted my problem [here]("http://ubuntuforums.org/showthread.php?p=6818011#post6818011") as well for more information. If you would like, I would tell it in this post too to make it more manageble but in short I can´t get it working either.

---

### Post by Simyager on 2009-03-01
> **Reiger said:**
> In order to see if your device is properly recognized, you should look at the output of:
```

ifconfig

```
That should list your wireless device.

Now if it doesn't do so at the modprobe ath5k command, try ensuring that nothing interferes:
```

sudo modprobe -r ath5k
sudo modprobe -r ath9k
sudo modprobe -r ath_pci

```
Then load it again & check output:
```

sudo modprobe ath5k
ifconfig

```

And if it still won't work it is time to collect log messages from the kernel about your driver:
```

dmesg | grep ath5k

```

I did this as well and nothing happend. It was like I didn´t input anything, I could see what I entered but it didn´t do anything.

---

### Post by Life On Mars on 2009-03-02
> **SrEstroncio said:**
> ...

Also, Life on Mars, how do I revert the the update?

When you reboot your PC you should get the option to choose which kernel you boot into - if you don't do anything it defaults to the latest one. 

Here's an example of the screen (not mine):

[IMG]http://i3.photobucket.com/albums/y71/Cocasoca/grub.jpg[/IMG]

If that works for you, you can, temporarily at least, edit the grub menu so that your default start up kernel is the one that works with your wireless card.

---

### Post by Simyager on 2009-03-08
Unfortunatly I installed oly 8.10 Ubuntu so that trick won´t work for me. But can anyone help me with my internet problem?

I can only connect to the internet via wifi so please help me

---

### Post by Life On Mars on 2009-03-14
Now I found what it is I used to get my wife's wireless working. Have you tried these instructions?

[How To Get Atheros AR242x To Work on 8.10 Intrepid Ibex]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/")

---

