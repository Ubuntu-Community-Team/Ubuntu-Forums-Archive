---
title: "Intel Corporation PRO/Wireless 4965 AGN not connecting after Karmic 9.10 upgrade"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by cfth on 2010-06-13
I upgraded from "Intrepid" 8.10 to "Karmic" 9.10 and my card that was working fine suddenly stopped working on my Asus G1S-B1 laptop.

I used to be able to connect to certain connections fine and they will not connect and it also doesn't seem to be able to connect to any open wireless, except this one adhoc network when I setup static IPs on both my upgraded laptop and the other laptop.

Wicd wasn't able to connect to anything so I just installed NetworkManager again. I also have linux-backports-modules-karmic installed in my normal system but I still have issues.

Here's some info and some syslogs, the first sys from a karmic livecd trying to connect to an open network, the second to the adhoc network without any static IPs, and the last from my normal system after a fresh boot trying to connect to my main wireless that used to work:

uname -a
```
Linux ubuntu 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux
```lspci -v
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
        Subsystem: Intel Corporation Device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 32
        Memory at fdffe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [e0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number 51-be-ce-ff-ff-e8-13-00
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
```syslog karmic livecd open network:
[http://paste.ubuntu.com/449036/](http://paste.ubuntu.com/449036/)

syslog karmic livecd trying to connect to the adhoc network:
[http://paste.ubuntu.com/449037/](http://paste.ubuntu.com/449037/)

syslog normal boot trying to connect to my usual network:
[http://paste.ubuntu.com/449038/](http://paste.ubuntu.com/449038/)

lsmod | grep iw
```
iwlagn                110236  0 
iwlcore               113952  1 iwlagn
mac80211              211628  2 iwlagn,iwlcore
cfg80211              130632  3 iwlagn,iwlcore,mac80211
led_class               4096  3 sdhci,iwlcore,asus_laptop
```

---

### Post by yahia999 on 2010-06-13
here, i made a small research and found this driver from INTEL LINUX WIRELESS.org : [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.61.2.24.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.61.2.24.tgz)    
hope it works, and tell me if it does, or if you want to browse the drivers, go to, and preferably bookmark ,this page: [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads)

:p :p :p :p :p :p

---

### Post by cfth on 2010-06-13
Hey, thanks for looking into it but Ubuntu seems to come with the exact file provided in there, even without karmic backports installed.
```
iwlwifi-4965-ucode-228.61.2.24$ md5sum /lib/firmware/iwlwifi-4965-2.ucode
bd6c33d15822b6005079849b5f4fa4c4  /lib/firmware/iwlwifi-4965-2.ucode
iwlwifi-4965-ucode-228.61.2.24$ md5sum iwlwifi-4965-2.ucode
bd6c33d15822b6005079849b5f4fa4c4  iwlwifi-4965-2.ucode
```


I did a bunch of tests, I'm back to stock modules that came with karmic, and through lots of trial and error I found I'm only having issues with Wireless N.

A, B, and G all work fine and WEP/WPA/WPA2 doesn't seem to make a difference. "Mixed" mode between Wireless N and A doesn't seem to work either.

Here's the syslog of a connection when the AP is set to A only and it connects fine:
[http://paste.ubuntu.com/449134/](http://paste.ubuntu.com/449134/)

Here's the syslog of a connection when the AP is set to N only and it fails:
[http://paste.ubuntu.com/449137/](http://paste.ubuntu.com/449137/)

Hopefully there's already a bug for this.

---

### Post by chili555 on 2010-06-13
I have seen a few posts that complain about being unable to connect to WPA networks when the router is set to mixed WPA ***and*** WPA2 mode. Please check your router and, if it is set so, change it to WPA2 only, assuming all the devices on your network do WPA2.

You might also try:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
```If this helps, we can create one file and make it permanent.

---

### Post by Jenkins1 on 2010-06-19
> **chili555 said:**
> I have seen a few posts that complain about being unable to connect to WPA networks when the router is set to mixed WPA ***and*** WPA2 mode. Please check your router and, if it is set so, change it to WPA2 only, assuming all the devices on your network do WPA2.

You might also try:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
```If this helps, we can create one file and make it permanent.

thanks for this this worked great for me, hopefully my wifi problems are gone. (not the thread starter)

---

### Post by rykel on 2010-09-26
> **chili555 said:**
> I have seen a few posts that complain about being unable to connect to WPA networks when the router is set to mixed WPA ***and*** WPA2 mode. Please check your router and, if it is set so, change it to WPA2 only, assuming all the devices on your network do WPA2.

You might also try:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
```If this helps, we can create one file and make it permanent.

I am running Ubuntu Lucid on Dell XPS M1330 with an Intel PRO/Wireless 4965 AG too but the adaptor can only see the networks but not connect to any.

I tried the above suggestion and still no luck. I have no control over the router so I cannot set anything in it. By any chance, the driver should NOT be acting up over what the router is set up to.

---

### Post by pcminh on 2011-02-01
> **chili555 said:**
> I have seen a few posts that complain about being unable to connect to WPA networks when the router is set to mixed WPA ***and*** WPA2 mode. Please check your router and, if it is set so, change it to WPA2 only, assuming all the devices on your network do WPA2.

You might also try:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
```If this helps, we can create one file and make it permanent.
  when i tried rmmod -f iwlagn, my wireless connection disappear, and i can enable wirelss driver again.
i kept tried the next command but error occured:
```
WARNING: Error inserting mac80211 (/lib/modules/2.6.35-25-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting iwlcore (/lib/modules/2.6.35-25-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwlagn (/lib/modules/2.6.35-25-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
now i can not find anything to enable wireless connection even in additional drivers
- rfkill list show nothing
- iwconfig just have
```
lo        no wireless extensions.

eth0      no wireless extensions
```
Please help me to get out of this trouble, thank you very much

---

### Post by barbecuy on 2011-08-10
I ran the commands, no l uck, my wireless card is still connecting at 54 Mbps.
Questions would be:
Is this fixed on latest version of Ubuntu?
Do we know which pcmcia(in my case on a laptop) is supported to run  at 300 Mbps?
Thanks

---

