---
title: "Regenerating 70-persistent-net.rules"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by ty4tuition on 2012-11-25
Hey,

I'm relatively new to Ubuntu. I searched the forums for an answer to this question but I'm still facing issues.

I had wireless internet running on Ubuntu as well as a LAN connection with a Windows 7 computer. While playing with /etc/network/interfaces and /etc/udev/rules.d/70-persistent-net.rules I must have messed something up, because I no longer have a connection.

I reset interfaces to what it was before (I think), the following:

```

auto lo
iface lo inet lookback

```

I think I messed up my 70-persistent-net.rules file and I don't have a backup. Removing it and rebooting it does not result in Ubuntu restoring it. Also running ```
sudo udevadm trigger
``` or ```
sudo udevadm trigger --action=add
``` does not regenerate the file.

How do I restore this file to a working version?

---

### Post by Doug S on 2012-11-25
Hi, and welcome to Ubuntu forums.
 
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2087316"), from just a day or two ago. In your case, I would suggest to rename your exisiting messed up file to something else first. Then do as I suggested in that thread.
 
And please, always always save a copy of files somewhere before messing with them. It makes life so much easier. I constantly mess thing up on my computers, but always (O.K. well, almost always) give myself a way to go backwards.

---

### Post by chili555 on 2012-11-25
This may help: [http://www.linuxfromscratch.org/lfs/view/6.3/chapter07/network.html](http://www.linuxfromscratch.org/lfs/view/6.3/chapter07/network.html)>  Pre-generate the rules to ensure the same names get assigned to the same devices at every boot, including the first:

```
/lib/udev/write_net_rules all_interfaces
```In the case of Ubuntu, I'd preface the command with sudo. Also, I'd be certain all the interfaces appear in:```
ifconfig
```If wlan0 and eth0 don't appear, let's find out why and fix it.

DISCLAIMER: I've never tried this so I make no guarantees. I do, however, have confidence that we could write one from scratch.

Your /etc/network/interfaces looks fine, assuming Network Manager is managing your network connections.

---

### Post by ty4tuition on 2012-11-25
Thanks so much for the reply!

What you advised in the other thread worked, to some extent.

70-persistent-net.rules was recreated, apart from the comment section however, it is empty. No eth0 entry for instance.

My wireless connection is also not restored. Here's the output of ```
ifconfig
```

```
eth0    link encap: Ethernet HWaddr f0:4d:a2:44:22:1b
    UP BROADCAST MULTICAST MTU:1500 Metric:1
    RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
    TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
    collisions: 0 txqueuelen: 1000
    RX bytes:0 (0.0 B) TX bytes (0.0 B)

lo    link encap: Local loopback
    inet addr: 127.0.01 Mask: 255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING MTU: 16436 Metric: 1
    RX packets: 132 errors: 0 dropped: 0 overruns: 0 frame: 0
    TX packets: 132 errors: 0 dropped: 0 overruns: 0 carrier: 0
    collisions: 0 txqueuelen: 0
    RX bytes: 10040 (10.0 kB) TX bytes: 10040 (10.0 kB)

```

forgive my formatting, I had to manually write down and rewrite the output.

What's going on?

---

### Post by ty4tuition on 2012-11-25
When I try ```
/lib/udev/write_net_rules all_interfaces
```

I get 

```
missing $INTERFACE
```

---

### Post by chili555 on 2012-11-25
If there is no wireless interface, then your wireless driver isn't present at all or isn't claiming your device. Let's go back to basics. If you have a PCI wireless device, please run and post:```
lspci -nn | grep 0280
sudo lshw -C network
rfkill list all
```If it's USB:```
lsusb
```After that's sorted, we'll try automatically recreating net.rules and, if not, with brute strength and a tiny bit of talent.

---

### Post by ty4tuition on 2012-11-25
```
sudo lshw -C network
```

Showed the wireless device as deactivated, which didn't make any sense. After googling that I found the culprit. I must have jammed in Fn+F2 which disables my wifi, using the same key combo I was able to activate it again. Incredibly stupid, but I'm too happy to care.

Guys thank you so much for your help!

---

### Post by chili555 on 2012-11-25
Glad it's working by whatever means. If you want to recreate net.rules, post back and we'll probably fix it easily.

---

### Post by Doug S on 2012-11-25
Once the device is active, instead of disabled, the the rules files should popluate by itself upon system boot.

---

### Post by chili555 on 2012-11-25
> **ty4tuition said:**
> When I try ```
/lib/udev/write_net_rules all_interfaces
```

I get 

```
missing $INTERFACE
```If the file doesn't spawn automatically on boot, you might try:```
sudo /lib/udev/write_net_rules eth0 wlan0
```

---

### Post by Doug S on 2012-11-26
@chili555 : Just for my own education, I tried your suggested method for recovering content of the file(s). I couldn't get it to work.
To restore the /etc/udev/rules.d files all I had to do was re-boot my computer, I didn't even have to re-install udev.

---

### Post by chili555 on 2012-11-26
> To restore the /etc/udev/rules.d files all I had to do was re-boot my computer,Excellent. Good to know and thanks.

---

