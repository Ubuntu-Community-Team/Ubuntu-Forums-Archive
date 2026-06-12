---
title: "Continually losing connection"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by smakand on 2009-08-18
Hey all, I have a DWA-552 (well I think, it's the PCI one with the AR5008 chip), and I was using the driver that Ubuntu 9.04 (2.6.28-14-generic x86_64) chose for me, and every couple of minutes I would just lose connection, and then get it back.

This problem has never happenned in any Windows, so it'd definitely something with Linux or related.

DMESG reported nothing. I have a signal monitor on conky that kept showing a valid signal. I just wasn't getting traffic either way. My signal was around 40%, 2 bars in the traditional network manager status icon.

I updated to the madwifi trunk drivers, and my signal now ranges at around 60%, but there is still intermittant connection loss. Also, pidgin is stupid and doesn't even realize when I disable wireless completely, let alone when the connection is lost. It adds to this problem because I can't even tell when the disconnects are happening unless I'm downloading something and conky's traffic monitor just flatlines.

Here are some goodies that might help, I'm not really sure what's happening. I like to think of myself as slightly above novice in the linux world, but probably not.

```
04:02.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

``````
wlan0     Link encap:Ethernet  HWaddr 00:1e:58:2c:8d:23  
          inet addr:192.168.0.194  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:58ff:fe2c:8d23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:231786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:342969212 (342.9 MB)  TX bytes:12731615 (12.7 MB)
``````
wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:91:F7:31:F9   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=65/100  Signal level:-48 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
$ lsmod | grep 'ath'
ath_pci               223936  0 
wlan                  260768  1 ath_pci
ath_hal               399584  1 ath_pci
ath9k                 288568  0 
mac80211              251528  1 ath9k
led_class              13064  1 ath9k
```-- This one is weird. Why is it ignoring my wireless?

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
```Thanks for any help you can give. My internet cut out 3 times for around 30 seconds each while writing this post.

---

### Post by smakand on 2009-08-18
Arg! If I cannot fix this, this may happen:

[IMG]http://www.businessweek.com/the_thread/techbeat/archives/hammer.jpg[/IMG]
[IMG]http://tbn2.google.com/images?q=tbn:tckGMMeFyX-8AM:http://www.tweakpc.de/gallery/data/500/DWA-552.jpg[/IMG]

---

### Post by smakand on 2009-08-19
Bump.

---

### Post by superprash2003 on 2009-08-19
could be similar to this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by smakand on 2009-08-19
> **superprash2003 said:**
> could be similar to this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

Well I don't have to restart it manually, as far as network manager is concerned I never lose connection. As far as anything is concerned, I never lose connection. Data just stops being sent either way, and it only happens on this computer when Ubuntu is running (this does not happen when Windows is running on the same hardware).

I installed the 2.6.28-11 kernel and backport modules as suggested in that thread though, besides an nvidia failure on the first boot attempt (second one worked but with an error message), I'm going to test it more thoroughly to see if the problem is rectified.

EDIT: Unfortunately it does not seem to be. In downloading an ubuntu iso from my school's mirror (RIT) to get something to read out on the traffic monitor, all traffic stopped periodically. I don't really know of a good traffic monitor, but below are screenshots showing traffic in CONKY and the download file.

---

### Post by smakand on 2009-08-19
Conky shows traffic just above the bottom right corner, you can see the network do-hicky in the top right.

During the freeze:

[http://bayimg.com/HADGmAAcF](http://bayimg.com/HADGmAAcF)

After the freeze:

[http://bayimg.com/hadgfaaCf](http://bayimg.com/hadgfaaCf)

Installing WicD seems to have done it. I was planning on doing that anyways because it's what I prefer on Fedora, but I didn't want to make changes until I got my internet fully fixed. Go figure.

---

