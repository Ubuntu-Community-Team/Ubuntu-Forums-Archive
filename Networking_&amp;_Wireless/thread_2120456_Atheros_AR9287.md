---
title: "Atheros AR9287"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by davidlubomirov on 2013-02-26
I have 2 OS. When i use Windows 7 my network adapter work better, but when i start Ubuntu 12.04 LTS and try going round the INTERNET 
on the same range from the router the network adapter is't working the same way like when i'm using Windows 7. My question is how can I fix it if I can?

---

### Post by squigish on 2013-02-26
I'm afraid we're going to need more information in order to help you fix this problem.  What do you mean when you say  
> **davidlubomirov said:**
> when i start Ubuntu 12.04 LTS and try going round the INTERNET 
on the same range from the router the network adapter is't working the same way like when i'm using Windows 7. 

Are you using a wired network adapter, or wireless? 

Are you able to browse websites like [www.google.com?](www.google.com?) 

Please open a terminal window by pressing CTRL+ALT+T and post the results of the following commands.

```
ping -c 10 8.8.8.8
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

The ping command will probably take a few seconds to run, but the others should all run instantly.

I probably won't be able to help you personally, but by posting this information, the next (more knowledgeable than I) person to come along can get right to work on troubleshooting, without having to request this information.

---

### Post by davidlubomirov on 2013-02-26
OK let say it that way. When i browse around internet from range about 15 meters by using Windows 7 i have no problem. But if i switch to Ubuntu 12.04 LTS i can't even connect to the router.

---

### Post by squigish on 2013-02-26
It sounds like you're using a wireless network card (is that right?) and that there's some problem with its configuration.  

If you can't even connect to the router, replace 8.8.8.8 with the ip address of the router in the ping command.  

At what point in the process do you fail to connect to the router? Can you see the wireless network in the list of available networks? Can you connect to other wireless networks using Ubuntu?

Posting the output of the commands I listed above will also be helpful.

---

### Post by davidlubomirov on 2013-02-26
```
ping -c 10 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=52 time=46.6 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=52 time=59.0 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=52 time=88.9 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=52 time=47.8 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=52 time=61.5 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=52 time=42.8 ms
64 bytes from 8.8.8.8: icmp_req=7 ttl=52 time=41.7 ms
64 bytes from 8.8.8.8: icmp_req=8 ttl=52 time=57.1 ms
64 bytes from 8.8.8.8: icmp_req=9 ttl=52 time=43.9 ms
64 bytes from 8.8.8.8: icmp_req=10 ttl=52 time=46.6 ms

--- 8.8.8.8 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 41.757/53.640/88.998/13.559 ms
```

```
lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:036d]
	Kernel driver in use: tg3
--
08:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e034]
	Kernel driver in use: ath9k
```

```
lsmod
Module                  Size  Used by
vesafb                 13846  1 
bnep                   18240  2 
rfcomm                 47562  4 
bluetooth             211812  10 bnep,rfcomm
parport_pc             32867  0 
ppdev                  17114  0 
kvm_amd                56136  0 
kvm                   422160  1 kvm_amd
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79855  1 
joydev                 17694  0 
acer_wmi               32845  0 
sparse_keymap          13891  1 acer_wmi
snd_hda_intel          34117  5 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
video                  19653  1 acer_wmi
wmi                    19257  1 acer_wmi
snd_rawmidi            30750  1 snd_seq_midi
arc4                   12530  2 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
microcode              23030  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13254  0 
fglrx                4715455  163 
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
ath9k                 133133  0 
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
mac80211              555272  1 ath9k
ath9k_common           14054  1 ath9k
ath9k_hw              399708  2 ath9k,ath9k_common
sp5100_tco             13792  0 
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
k10temp                13174  0 
edac_core              53053  0 
soundcore              15092  1 snd
edac_mce_amd           23548  0 
i2c_piix4              13302  0 
amd_iommu_v2           19228  1 fglrx
cfg80211              208382  3 ath9k,mac80211,ath
psmouse               102075  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
serio_raw              13216  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
tg3                   156594  0
```

---

### Post by squigish on 2013-02-26
> **davidlubomirov said:**
> ping -c 10 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=52 time=46.6 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=52 time=59.0 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=52 time=88.9 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=52 time=47.8 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=52 time=61.5 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=52 time=42.8 ms
64 bytes from 8.8.8.8: icmp_req=7 ttl=52 time=41.7 ms
64 bytes from 8.8.8.8: icmp_req=8 ttl=52 time=57.1 ms
64 bytes from 8.8.8.8: icmp_req=9 ttl=52 time=43.9 ms
64 bytes from 8.8.8.8: icmp_req=10 ttl=52 time=46.6 ms

--- 8.8.8.8 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 41.757/53.640/88.998/13.559 ms


This tells me that at some level, you ARE connected to the internet, since you can talk to other computers on the internet.  If you can't connect to websites using a web browser, it could be a problem with your web browser, or it could be a DNS issue.

Try 
```
ping -c 4 www.google.com
```

Please also post the output of the other commands I listed.

---

### Post by davidlubomirov on 2013-02-26
ping -c 4 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (173.194.39.212) 56(84) bytes of data.
64 bytes from sof01s01-in-f20.1e100.net (173.194.39.212): icmp_req=1 ttl=60 time=5.38 ms
64 bytes from sof01s01-in-f20.1e100.net (173.194.39.212): icmp_req=2 ttl=60 time=4.43 ms
64 bytes from sof01s01-in-f20.1e100.net (173.194.39.212): icmp_req=3 ttl=60 time=5.38 ms

--- [www.google.com](www.google.com) ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3004ms
rtt min/avg/max/mdev = 4.432/5.067/5.389/0.449 ms


You don't understand anything i tell you. The problem is't in the browser I thing is in the Drivers !!!

---

### Post by squigish on 2013-02-26
The reason I think the problem is in the browser is that some other services that use the internet seem to be working.

Try running ```
sudo apt-get update
``` and posting the output.

Can you please tell me what is NOT working? You're right that I'm having trouble understanding you. What are you trying to do that doesn't work?  What do you mean when you say that the network adapter doesn't work the same way as it does on Windows?

---

### Post by davidlubomirov on 2013-02-26
Here is the situation again. 
When Im browsing the WEB from 15 meteres distance from my router by using Windows 7 I have no problem. But when I reboot and start ubuntu 12.04 LTS and try to connect again from the same distance and place I can connect to my router (because is't in rage). Like I sad I thing the problem is in the driver but I'm not sure. Or maybe in the router. The router is Linksys

---

### Post by squigish on 2013-02-26
This is what the tests you've run have told me:

The fact that you can successfully ping 8.8.8.8 means that you do in fact have a connection to your router, and then to the internet.  

The fact that when you ping [www.google.com](www.google.com), it resolves to a correct ip address means that you also have a working DNS connection, which is the most common cause of a web browser not working.  

The fact that one of the four pings to [www.google.com](www.google.com) never came back is a cause for concern, but it might just be caused by a signal problem between your computer and the router.  

In an imaginary straight line between your computer and your router, does the line go through many walls?  Is there a large metal object in the way, like a refrigerator or bathtub? These things can cause signal problems.

If you want help diagnosing your problem, you're going to have to give us more information, including information about what browser you're using.  

Simply saying "I think the problem is ____" doesn't really help.  You should say "I think the problem is ___ because of these reasons: ..."

I also think that there seems to be a language issue.  What is your native language? It's possible you'll be able to find someone who can help you in that language, which might be easier for you.

I'm pretty quickly getting out of my depth here, so I'm going to turn this over to someone else to help you out.  

Good luck!

---

### Post by davidlubomirov on 2013-02-27
Thank you man! NO I have no problem with the language. And still think that you just can'n understand anything. I know how the router work and the rage he can cover. The walls are no problem or the refrigerator. 
I'll explain again. 

In my apartment I install lynksys WRT160Nv3, and when I try connect from 15 meters range by using Windows7 the connection to my router is good and everything work just fine. But when I try connect using Ubuntu 12.04 LTS from the same place, same spot I can't even connect to the router. 
My question again is how is that possible why the connection is better when i use windows and is realy bad when i use ubuntu 12.04???

---

### Post by chili555 on 2013-02-27
Let's try a driver parameter. Please open a terminal and do:```
sudo modprobe -r ath9k
sudo modprobe ath9k btcoex_enable=1
```If it helps, we can write one file and make it permanent. If not, we will try a couple of other things. May we see:```
nm-tool
```Many Linux drivers still struggle a bit with 802.11N speeds. Is your router set to use B, G and N speeds? Can you please try B and G only and see if there is any improvement?

---

### Post by davidlubomirov on 2013-03-08
Is is possible that my router is't supporting Linux

---

### Post by chili555 on 2013-03-08
> **davidlubomirov said:**
> Is is possible that my router is't supporting LinuxI have never seen one yet that doesn't support Linux, so I doubt it. On the other hand, I have seen a great many routers including my Linksys, that are *running* Linux!

---

### Post by davidlubomirov on 2013-03-12
OK so can you tell me how can I find some updates for the wireless driver .

---

### Post by chili555 on 2013-03-12
> **davidlubomirov said:**
> OK so can you tell me how can I find some updates for the wireless driver .Was there any improvement from my post #12 suggestions? You could try the linux-backports-modules-cw package. If you are running 12.04 LTS:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```Reboot and let us hear your report.

---

### Post by davidlubomirov on 2013-03-15
Nothing changed. It's still the same.

---

