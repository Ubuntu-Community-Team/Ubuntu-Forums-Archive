---
title: "Wireless Drivers for Brand-New Thinkpad"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by airspoon on 2011-08-17
I just recently purchased a Lenovo Thinkpad e520 and I'm wanting to put Ubuntu 11.04 on it. I downloaded the 64bit iso and burned it to a thumb-drive, just before booting the thumb-drive. 

I have not yet installed Ubuntu, but rather I'm still running it from a thumb-drive. I want to make sure everything will work fine, before installing it permanently.

However, it doesn't appear as if any drivers for my wireless card were loaded, as I can't view the available wireless networks.

I successfully installed Ubuntu 11.04 on my desktop several months ago and I haven't booted into Windows since, -not one time. Therefore, I'm hoping to have my new laptop run Ubuntu as well.

However, I'm not sure what steps, if any, I need to take in order to get my wireless working. Can someone please help me? 

Thanks!

---

### Post by nm_geo on 2011-08-17
Do this command in terminal

```
lspci -nn | grep 0280
```That should give us some information to help identify the wireless card.

Add this too

```
sudo lshw -C network
```

---

### Post by airspoon on 2011-08-17
Thanks for the response.

Here are the results from both of those commands:

lspci -nn | grep 0280:

```

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

```


sudo lshw -C network:
```

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:64:f5:dc
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:5000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network DISABLED
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:c3:2a:02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:3000(size=256) memory:d1d00000-d1d03fff

```

---

### Post by nm_geo on 2011-08-17
Congrats the answer is yes.. Almost out of the box as they say..
Your wireless driver is already showing up...  and it is correct..

```
sudo modinfo rtl8192ce
```

Run that in the terminal 

look for the following line. 

<snip>
alias:          pci:v0000[COLOR=Red]10EC[/COLOR]d0000[COLOR=Red]8176[/COLOR]sv*sd*bc*sc*i*
<snip>

Those were the number we saw in the lspci command earlier.

Once you install,  if you decide to ... be sure to update & upgrade right away..

---

### Post by airspoon on 2011-08-18
Thanks, so even though my wireless isn't working on the "live cd" (thumb drive), it should work after the install?

Also, what just started to happen, is that I'm having a few errors, while booted on the thumbdrive. The first is saying that Zetgeist daemon crashed.

At the same time, it also keeps saying that the "ubiquity dm"  has closed unexpectedly.

Are these two error something I should be worrying about?

Again, thanks.

---

### Post by nm_geo on 2011-08-18
> **airspoon said:**
> Thanks, so even though my wireless isn't working on the "live cd" (thumb drive), it should work after the install?

Also, what just started to happen, is that I'm having a few errors, while booted on the thumbdrive. The first is saying that Zetgeist daemon crashed.

At the same time, it also keeps saying that the "ubiquity dm"  has closed unexpectedly.

Are these two error something I should be worrying about?

Again, thanks.

I have never experienced either of those problems on a live USB.  However, I usually install from the alternate iso anyway as ubiquity and the migration assistant gives me fits... probably because I have too many versions on this one old laptop and too many grubs.. I would not worry to much on those unless you were trying to install?

---

### Post by walt.smith1960 on 2011-08-18
One thing I would do if it were mine is create an image of the existing partition.  Clonezilla (clonezilla.org) seems to work okay or there are commercial choices.  By creating an image you can get back to a fresh-from-the-box state if need be.  You could also go to the networking and wireless forum and search for "RTL8188CE".  Check issues and solutions there.

---

