---
title: "Blacklisting 8139too has no effect"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by searchfgold6789 on 2013-01-16
Hi,

I am trying to get my RTL8188CUS USB wifi dongle to work. The kernel module(s) for it currently are not working but are included in the kernel anyway. So I have to get a driver from the Realtek website which creates the 8192cu kernel module, which I place in /etc/modules. I place rtlwifi, rtl8192c_common, and rtl8192cu (the non-working modules) in /etc/modprobe.d/blacklist.conf. On my laptop running Lubuntu 12.04, this works perfectly and I can connect to wifi.

However, on my desktop machine running Kubuntu 12.10, after doing these same steps, the wireless will not connect. The correct modules are blacklisted, and 8192cu is loaded, but there is one module, 8139too, that shows up *even when it is placed in my blacklist.conf.* I think this is what is causing the problem. When I look at the wirless device details in KDE's network manager, the driver name reported is "rtl8192cu", which is not what should be there.

Can anyone tell me what is going on here or how to get rid of that pesky 8139too? I read that the 'mii' module causes my unwanted module to be loaded anyway, but I do not know how to set that right if that is indeed the issue.

Sincere thanks,
 - searchfgold6789

---

### Post by ahallubuntu on 2013-01-16
Maybe you've got a syntax error in your blacklist.conf file?  Show its contents here?

---

### Post by chili555 on 2013-01-16
> but there is one module, 8139too, that shows up even when it is placed in my blacklist.conf. 8139too is an ethernet driver, not wireless. It needn't be blacklisted.

---

### Post by searchfgold6789 on 2013-01-16
> **chili555 said:**
> 8139too is an ethernet driver, not wireless. It needn't be blacklisted.
Hmm... ok. So it's being loaded because of the old D-Link PCI. Makes sense; thanks for the info!

> **ahallubuntu said:**
> Maybe you've got a syntax error in your blacklist.conf file?  Show its contents here?
Attached: /etc/modules; /etc/modprobe.d/blacklist.conf; the output of "lsmod" with the dongle plugged in. KDE network manager still reports that the driver being used for the dongle is rtl8192cu.

---

### Post by ahallubuntu on 2013-01-16
Your lsmod output shows "8192cu" loaded but not "rtl8192cu" so it appears the correct module is really loaded after all.

What kind of problem are you having then?  I too wonder why you think it is related to 8139too ?  (Try putting a blank line under that module name in the blacklist file just to be safe...)

You can always try this from a terminal:

```
sudo modprobe -r 8139too
```

To remove it one time and see if that fixes anything.

---

### Post by ahallubuntu on 2013-01-16
Your lsmod output shows "8192cu" loaded but not "rtl8192cu" so it appears the correct module is really loaded after all.

What kind of problem are you having then?  I too wonder why you think it is related to 8139too ?  (Try putting a blank line under that module name in the blacklist file just to be safe...)

You can always try this from a terminal:

```
sudo modprobe -r 8139too
```

To remove it one time and see if that fixes anything.

---

### Post by searchfgold6789 on 2013-01-16
> **ahallubuntu said:**
> Your lsmod output shows "8192cu" loaded but not "rtl8192cu" so it appears the correct module is really loaded after all.

What kind of problem are you having then?  I too wonder why you think it is related to 8139too ?  (Try putting a blank line under that module name in the blacklist file just to be safe...)

You can always try this from a terminal:

```
sudo modprobe -r 8139too
```To remove it one time and see if that fixes anything.
Thanks for your response. I realized that 8139too was loaded because of a D-Link ethernet adapter I have plugged in. It's supposed to be there. Yes, my blacklist.conf has a final newline.

My problem is that the correct module is loading, but I believe that something weird is going on - I don't know what - because when I try to connect to wireless, entering the KDE wallet password, Network Manager keeps asking for the wifi passcode and never connecting as it should, which is what happens when I use the modules that come with the kernel. The KDE Network Manager lists "rtl8192cu" as the driver being used for the wireless dongle, which is the built in kernel module. `lsmod` says that rtl8192cu is not loaded.

So we have a contradiction between `lsmod` and the Network Manager. `lsmod` says 8192cu is loaded, rtl8192cu is not, and things should be working; but Network Manager says that rtl8192cu is being used, and it behaves as if it is. It's a mystery to me :S

---

