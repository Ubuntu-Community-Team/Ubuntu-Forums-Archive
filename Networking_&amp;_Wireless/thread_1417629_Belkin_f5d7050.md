---
title: "Belkin f5d7050"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by chevloschelios on 2010-02-27
Hello I have Belkin f5d7050 WiFi and I want to install it on my Ubuntu 9.10. Can anybody help me please ?

---

### Post by chili555 on 2010-02-27
There are several versions of this device. Let's find out which one you have. I believe it is a USB device. Please open Applications -> Accessories -> Terminal and do:```
lsusb
```Post the result and we'll proceed.

---

### Post by chevloschelios on 2010-02-27
Ok, I will post it later. Then, Can I send you a Private Message ?

---

### Post by chili555 on 2010-02-27
If you want to solve your wireless issue, let's keep our discussions on the forum. That way the searchers may learn from our experiences. I love to read PMs but I refer most back to the forum.

---

### Post by mark bower on 2010-02-27
The F5D7050 should work "out of the box".  Just plug it in, click on network manager in the upper right hand corner, select your router by its SSID name, and you should be on line - its that simple.  I have posted numerous times that this USB device works very nicely with 8.10 thru 9.10.  I have used it on all the previous versions mentioned and on three different motherboards including an older laptop.  Let us know how it goes, especially if it holds up as working out of the box(I would like to add your experience to my brag list!).  While not preferred, I use "MAC address allowed" for my security with the router.  Plenty good enuf at residence.

mark

---

### Post by chevloschelios on 2010-02-28
Yeah I select SSID and its working thank you very much

---

### Post by mark bower on 2010-02-28
Great.  Help on this forum to spread the word that the USB F5D7050 wireless adapter has a very high probability of working "out of the box".  I have only seen one account of it not working.

mark

---

### Post by chevloschelios on 2010-03-01
But I can´t install it on my BackTrack 4. Can you help my again ?

---

### Post by chili555 on 2010-03-01
> **chevloschelios said:**
> But I can´t install it on my BackTrack 4. Can you help my again ?Please see post #2.

---

### Post by Smith.. on 2010-05-11
I have the same make and model wifi device listed here. It works but I'm receiving on average about a 10% - 20% packet loss with the rt73usb driver. The one of the wifi drivers Lucid comes with. Can someone please help me? In 9.10 the device worked out of box. I did not receive any packet loss in 9.10. Here is the output of the lsusb command: 

```
smith@linux:~$ lsusb
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```I will subscribe to this thread and reply as soon as possible. Thank you in advance for your time.

---

### Post by chili555 on 2010-05-11
Very often, two conflicting drivers claim the device. May we please see:```
dmesg | grep -e rt2 -e rt7
```We are hoping that only rt73usb is there and not rt2500usb.

---

### Post by Smith.. on 2010-05-11
Thank you for helping me out. First and foremost here. This is the output of that command: 

```
smith@linux:~$ dmesg | grep -e rt2 -e rt7
[   15.554125] Registered led device: rt2800usb-phy0::radio
[   15.554153] Registered led device: rt2800usb-phy0::assoc
[   15.554172] Registered led device: rt2800usb-phy0::quality
[   15.554566] usbcore: registered new interface driver rt2800usb
[   15.622193] rt2800usb 1-5:1.0: firmware: requesting rt2870.bin
[  305.202657] phy1 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[  305.202670] phy1 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[  305.202753] usbcore: registered new interface driver rt2500usb
[  305.479714] Registered led device: rt73usb-phy2::radio
[  305.479758] Registered led device: rt73usb-phy2::assoc
[  305.479800] Registered led device: rt73usb-phy2::quality
[  305.480955] usbcore: registered new interface driver rt73usb
[  305.498229] rt73usb 1-3:1.0: firmware: requesting rt73.bin
[ 2017.804518] phy2 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 2.
[ 2017.804524] Please file bug report to http://rt2x00.serialmonkey.com.

```They're both running. I found this information out by using this command: 

```
less /proc/modules
```Can you tell me what that command you posted does? It seems to provide more detailed information. The output of the command I was talking about is: 

```
act_police 4620 1 - Live 0xffffffffa08e9000
sch_ingress 2098 1 - Live 0xffffffffa08d7000
cls_u32 6698 5 - Live 0xffffffffa08c9000
sch_sfq 5863 3 - Live 0xffffffffa08ab000
sch_cbq 17140 1 - Live 0xffffffffa08f0000
cryptd 8116 0 - Live 0xffffffffa08ec000
aes_x86_64 7912 1 - Live 0xffffffffa08e5000
aes_generic 27607 1 aes_x86_64, Live 0xffffffffa08d9000
rt73usb 24256 0 - Live 0xffffffffa08cc000
crc_itu_t 1715 1 rt73usb, Live 0xffffffffa08bc000
rt2500usb 19643 0 - Live 0xffffffffa08c2000
nfnetlink_queue 8141 1 - Live 0xffffffffa08a5000
nfnetlink 4142 2 nfnetlink_queue, Live 0xffffffffa0880000
binfmt_misc 7960 1 - Live 0xffffffffa0078000
nf_conntrack_ipv4 12980 3 - Live 0xffffffffa0898000
nf_defrag_ipv4 1481 1 nf_conntrack_ipv4, Live 0xffffffffa008b000
ipt_REJECT 2384 1 - Live 0xffffffffa0075000
xt_tcpudp 2667 2 - Live 0xffffffffa08bf000
iptable_filter 2791 1 - Live 0xffffffffa08b9000
ip_tables 18390 1 iptable_filter, Live 0xffffffffa08ae000
xt_iprange 1645 0 - Live 0xffffffffa08a8000
xt_state 1490 3 - Live 0xffffffffa08a2000
nf_conntrack 73934 2 nf_conntrack_ipv4,xt_state, Live 0xffffffffa0883000
xt_mark 1055 6 - Live 0xffffffffa00ac000
xt_NFQUEUE 2344 3 - Live 0xffffffffa0088000
x_tables 22429 7 ipt_REJECT,xt_tcpudp,ip_tables,xt_iprange,xt_state,xt_mark,xt_NFQUEUE, Live 0xffffffffa0878000
arc4 1473 2 - Live 0xffffffffa0032000
rt2800usb 33496 0 - Live 0xffffffffa09d9000
rt2x00usb 11260 3 rt73usb,rt2500usb,rt2800usb, Live 0xffffffffa00a4000
rt2x00lib 32133 4 rt73usb,rt2500usb,rt2800usb,rt2x00usb, Live 0xffffffffa0940000
led_class 3732 1 rt2x00lib, Live 0xffffffffa002c000
mac80211 238128 2 rt2x00usb,rt2x00lib, Live 0xffffffffa0a77000
cfg80211 148386 2 rt2x00lib,mac80211, Live 0xffffffffa0a44000
ppdev 6375 0 - Live 0xffffffffa091f000
fbcon 39270 71 - Live 0xffffffffa095d000
tileblit 2487 1 fbcon, Live 0xffffffffa009d000
font 8053 1 fbcon, Live 0xffffffffa0099000
bitblit 5811 1 fbcon, Live 0xffffffffa004c000
softcursor 1565 1 bitblit, Live 0xffffffffa0011000
crc_ccitt 1675 1 rt2800usb, Live 0xffffffffa0a41000
snd_ca0106 38051 4 - Live 0xffffffffa0a2f000
snd_ac97_codec 125394 1 snd_ca0106, Live 0xffffffffa0a05000
ac97_bus 1450 1 snd_ac97_codec, Live 0xffffffffa09ff000
snd_pcm_oss 41394 0 - Live 0xffffffffa09ed000
snd_mixer_oss 16299 1 snd_pcm_oss, Live 0xffffffffa09e3000
snd_pcm 87850 5 snd_ca0106,snd_ac97_codec,snd_pcm_oss, Live 0xffffffffa09c1000
snd_seq_dummy 1782 0 - Live 0xffffffffa09bb000
snd_seq_oss 31219 0 - Live 0xffffffffa09ac000
snd_seq_midi 5829 0 - Live 0xffffffffa09a5000
snd_rawmidi 23388 2 snd_ca0106,snd_seq_midi, Live 0xffffffffa0998000
snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi, Live 0xffffffffa0990000
snd_seq 57417 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa0978000
snd_timer 23553 2 snd_pcm,snd_seq, Live 0xffffffffa096b000
snd_seq_device 6824 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa00b4000
snd 70978 16 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa0949000
usb_storage 49833 0 - Live 0xffffffffa0931000
parport_pc 29958 1 - Live 0xffffffffa0927000
soundcore 8052 1 snd, Live 0xffffffffa0059000
snd_page_alloc 8500 2 snd_ca0106,snd_pcm, Live 0xffffffffa003c000
edac_core 45423 0 - Live 0xffffffffa0911000
edac_mce_amd 9214 0 - Live 0xffffffffa0027000
nvidia 8096262 24 - Live 0xffffffffa00bd000 (P)
k8temp 3912 0 - Live 0xffffffffa0008000
vga16fb 12757 1 - Live 0xffffffffa00b7000
vgastate 9857 1 vga16fb, Live 0xffffffffa00af000
i2c_nforce2 6099 0 - Live 0xffffffffa00a8000
lp 9336 0 - Live 0xffffffffa009f000
parport 37160 3 ppdev,parport_pc,lp, Live 0xffffffffa008d000
usbhid 40988 0 - Live 0xffffffffa007b000
hid 83376 1 usbhid, Live 0xffffffffa005e000
8139too 22245 0 - Live 0xffffffffa0051000
r8169 39554 0 - Live 0xffffffffa0040000
8139cp 19541 0 - Live 0xffffffffa0035000
mii 5237 3 8139too,r8169,8139cp, Live 0xffffffffa002e000
floppy 63156 0 - Live 0xffffffffa0015000
pata_amd 11962 2 - Live 0xffffffffa000c000
sata_nv 23778 0 - Live 0xffffffffa0000000

```This one confirms or at least I believe it does. That the rt73usb, rt2800usb, rt2x00usb, rt2x00lib, rt2500usb, and r8169 are live or currently running here. I'm not sure if r8169 is a wifi module I don't know? Just like 8139cp. What's that all about?  Thank you for responding to my post. Helping me out. I'm addicted to linux as well, Ubuntu is an awesome distribution. Yeah M$ is just old hat now. I like learning these new tricks. I feel like I'm actually running a computer now.

---

### Post by chili555 on 2010-05-11
r8169, 8139cp and 8139too are ethernet modules; if you are not using ethernet or you are but it's working well, these entries may be ignored.

My dmesg command searches the kernel messages for any information related to our subject, in this case, any lines with rt2 or rt7 in them.

Wow! You have no less than *three* conflicting drivers! Let's ban two of them and see if your card works better. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will open. Add two lines at the bottom:```
blacklist rt2500usb
blacklist rt2800usb
```Proofread carefully, save and close gedit. Reboot.

Now does your card work properly? 

It looked like there were some errors previously, so if it is not working properly, run this again:```
dmesg | grep -e rt2 -e rt7

```We hope we are not seeing stuff like this:> 
[  305.202657] phy1 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[  305.202670] phy1 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[ 2017.804518] phy2 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 2.
[ 2017.804524] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).The reason we did nothing with rt2x00usb and rt2x00lib is that they are dependencies of rt73usb.

Also, it may turn out that rt2500usb drives your device better than rt73usb, so we may have to fine-tune our process.

---

### Post by Smith.. on 2010-05-11
That seemed to work out pretty good. I'm wondering though is it possible to run two wifi adapters without conflicts? I've been trying to move to wireless n due to the improvements in the technology. Sometimes my signal cuts out. With packet loss I imagine that was most of the reason why. I want to connect to two different access points to increase my speed. The wifi G adapter I have [ Belkin F5d7050 ] is working much better now thanks to you. After running some tests and installing a couple of drivers I've found out that if I use ndiswrapper to install the WinXP64 drivers for my wireless N device [ TEW-644UB ]. The n device doesn't even show up? When I do this command: 

```
ping -s 1472 192.168.x.x
```To send large packets to my router I sometimes get a 0% packet loss. If I wait an extended period of time I get around a 10% packet loss. Which isn't bad but it's still loss. Now here is the output of the command you taught me with both devices:

```
smith@linux:~$ dmesg | grep -e rt2 -e rt7
[   14.973533] usbcore: registered new interface driver rt2870
[  306.467611] usbcore: registered new interface driver rt73usb
[  326.459333] Registered led device: rt73usb-phy0::radio
[  326.459370] Registered led device: rt73usb-phy0::assoc
[  326.459407] Registered led device: rt73usb-phy0::quality
[  326.513912] rt73usb 1-3:1.0: firmware: requesting rt73.bin
[  527.512678] Registered led device: rt73usb-phy1::radio
[  527.512713] Registered led device: rt73usb-phy1::assoc
[  527.512746] Registered led device: rt73usb-phy1::quality
[  527.526874] rt73usb 1-3:1.0: firmware: requesting rt73.bin
[  550.453532] Registered led device: rt73usb-phy2::radio
[  550.453570] Registered led device: rt73usb-phy2::assoc
[  550.453606] Registered led device: rt73usb-phy2::quality
[  550.467663] rt73usb 1-3:1.0: firmware: requesting rt73.bin
```You may need this additional background info. I installed the latest linux drivers from the ralink site as directed by other tutorials in the forums. I also installed the driver using the ndiswrapper. Ok so now when I uninstall the driver using: 

```
sudo ndiswrapper -r rt2870
```And it's removed the output from the grep command stays the same. But either way the wireless n device doesn't work. I tried blacklisting all the modules related to the wifi that I could find and just leaving rt2870sta solo and still no luck. Here's my custom section of my blacklist file. 

```
# Custom blacklist by the Smyth~
blacklist snd_hda_intel
# blacklist rt2870sta
blacklist rt73usb
blacklist rt2800usb
blacklist rt2500usb
```Since I blacklisted the other module to reply here I had to: 

```
sudo modprobe rt73usb
```The output of:

```
less /proc/modules 
```Shows that both modules are "live" and I'm not sure if the output of the grep command shows that there's an error there. It's not like the other one where the error was obvious. If I:

```
ifconfig
```I only see one device. Again thank you for taking the time to help me out man. If I can get this to work. I shall return to the thread I started on getting the device TEW-644UB to work and lay out the process.

---

### Post by chili555 on 2010-05-11
Your TEW-644UB should work with the native rt2870sta driver; it, too is also claimed by rt2800usb! Probably the reason the native driver didn't work for you, causing you to try and fail at ndiswrapper, is that conflict.

Quite often, tutorials ask you to blacklist things in /etc/modprobe.d/blacklist. It should be /etc/modprobe.d/blacklist.conf. Accordingly, a lot of new users end up with both. Do you have both? Do we need to consolidate?

You can run two wireless devices, however, Network Manager will likely not handle it correctly. I am fairly confident that a properly arranged /etc/network/interfaces file will do the trick.

So, have we at least fixed the rt73usb? Are you ready to work on the TEW-644UB?

---

### Post by Smith.. on 2010-05-11
I believe the Belkin issue is fixed. I'll have to run more tests on the packet loss. I was getting lots of packet loss with both wifi devices plugged in. Even though I had blacklisted rt2870sta and removed the driver using this command:

```
ndiswrapper -r rt2870
```Now with the wifi n device out and me posting here using the Belkin. I gave it sufficiant time I estimate to run another: 

```
ping -s 1472 192.198.x.X
```The initial burst was 71.2ms but then it started going down some about 10. No packet loss though. I think the Belkin is good. Thank you. 

I don't have two lists I only have the one: 

/etc/modprobe.d/blacklist.conf

There are other blocklists in the modprobe.d directory but none with just blacklist as a name.

```
smith@linux:/etc/modprobe.d$ ls
alsa-base.conf           blacklist-framebuffer.conf
alsa-base.conf~          blacklist-modem.conf
blacklist-ath_pci.conf   blacklist-oss.conf
blacklist.conf           blacklist-watchdog.conf
blacklist.conf~          libpisock9.conf
blacklist-firewire.conf  nvidia-graphics-drivers.conf
```The files with the ~ character I think are the backup copies if I'm not mistaken. That's a neat feature by the way if that's the case. 

Yes I would love to have both of them working. I think the Belkin is good. Let me do one last ping attack on the router here. That's was crazy the last time I did that 2031ms was the time of the initial burst. I wonder if that lags the line? No packet loss friend. I think we're good. With the Belkin device that is. Again thank you for your time man.

---

### Post by Smith.. on 2010-05-11
update: 

nope still receiving major packet loss.

---

### Post by chili555 on 2010-05-11
Have you tweaked MTU, etc.? It may be different as between computers in your network versus across your ISP to the internet.

---

### Post by Smith.. on 2010-05-11
> **chili555 said:**
> Have you tweaked MTU, etc.? It may be different as between computers in your network versus across your ISP to the internet.

After checking the wifi entry in the network manager by "editing connections". The mtu is set to automatic. No I didn't tweak the mtu? 

I did however get the wifi n to come on it's now ra0 for some reason thank you: 

```
sudo ifconfig ra0 up
```You have brought my n device up but like you were saying no entry in the network manager for ra0. 

```
ifconfig 
```shows: 

```
smith@linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:xxxxxxxx 

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:xxxxxx 

lo        Link encap:Local Loopback  
          inet addr:127.0.x.x Mask:255.0.x.x
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxxxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:289050 (289.0 KB)  TX bytes:524960 (524.9 KB)

wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.x.x  Bcast:192.168.x.x  Mask:255.255.x.x
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxxxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:459465 (459.4 KB)  TX bytes:163457 (163.4 KB)
```After running the ping test again...

```
smith@linux:~$ ping -s 1472 192.168.x.x
PING 192.168.x.x (192.168.x.x) 1472(1500) bytes of data.
1480 bytes from 192.168.x.x: icmp_seq=1 ttl=64 time=53.4 ms
1480 bytes from 192.168.x.x: icmp_seq=2 ttl=64 time=8.12 ms
1480 bytes from 192.168.x.x: icmp_seq=4 ttl=64 time=8.02 ms
1480 bytes from 192.168.x.x: icmp_seq=5 ttl=64 time=12.5 ms
1480 bytes from 192.168.x.x: icmp_seq=6 ttl=64 time=7.98 ms
1480 bytes from 192.168.x.x: icmp_seq=7 ttl=64 time=9.84 ms
1480 bytes from 192.168.x.x: icmp_seq=8 ttl=64 time=7.09 ms
1480 bytes from 192.168.x.x: icmp_seq=9 ttl=64 time=66.6 ms
1480 bytes from 192.168.x.x: icmp_seq=11 ttl=64 time=9.94 ms
1480 bytes from 192.168.x.x: icmp_seq=12 ttl=64 time=111 ms
^C
--- 192.168.x.x ping statistics ---
13 packets transmitted, 10 received, 23% packet loss, time 12017ms
rtt min/avg/max/mdev = 7.093/29.474/111.046/33.972 ms
```I don't get it?

---

### Post by chili555 on 2010-05-11
There is only one parameter you might try in rt73usb:```
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
```I am not sure this will help. I suppose it is concievable that the chip (hardware) doesn't handle WPA/WEP as well as wpa_supplicant (software). Of course, you could also un-blacklist rt2800usb and blacklist rt73usb and see if the other driver works any better. If you do so, you will need to do:```
sudo rmmod -f rt73usb
sudo modprobe rt2800usb
```

I have an appointment; I will be away for a few hours; sorry.

---

### Post by Smith.. on 2010-05-11
No hey man it's all good. Thank you for your help so far. Without your help it might have taken me longer to find out how to get more information about these modules here. The rmmod command and then re applying the module with the nohwcrypt=1 option seems to work a little better. But yeah it does have it's expiration date on it. There's intermittent  spikes where it gets up to 73% packet loss when pinging the router. The signal is ok. 51% or higher. I have moblocker and blockcontrol as an ip blocker. I've noticed that when using Empathy and I'm first setting up my accounts. That more lag would come in as I started to unblock what seemed like hundreds of M$ servers. This is just to use the MSN messenger service mind you. Now that's crazy. I'm now trying to notify everyone on my msn messenger that I will no longer be available though it. Then I'll one again start blocking that mess again. 

With everything the way it is now here is the output of the grep command: 

```
 smith@linux:~$ dmesg | grep -e rt2 -e rt7
[   15.432907] Registered led device: rt2800usb-phy0::radio
[   15.432931] Registered led device: rt2800usb-phy0::assoc
[   15.432950] Registered led device: rt2800usb-phy0::quality
[   15.433221] usbcore: registered new interface driver rt2800usb
[   15.526679] rt2800usb 1-5:1.0: firmware: requesting rt2870.bin
[  204.914128] usbcore: deregistering interface driver rt2800usb
[  221.221897] usbcore: registered new interface driver rt2870
[  268.097339] <==== rt28xx_init, Status=0
[  363.917067] Registered led device: rt73usb-phy1::radio
[  363.917106] Registered led device: rt73usb-phy1::assoc
[  363.917155] Registered led device: rt73usb-phy1::quality
[  363.919084] usbcore: registered new interface driver rt73usb
[  363.929640] rt73usb 1-3:1.0: firmware: requesting rt73.bin
``````
less /proc/modules
``````
acryptd 8116 0 - Live 0xffffffffa0941000
aes_x86_64 7912 1 - Live 0xffffffffa093a000
aes_generic 27607 1 aes_x86_64, Live 0xffffffffa092e000
rt73usb 24256 0 - Live 0xffffffffa0921000
crc_itu_t 1715 1 rt73usb, Live 0xffffffffa0903000
rt2870sta 620964 1 - Live 0xffffffffa0aa6000
nfnetlink_queue 8141 1 - Live 0xffffffffa08f3000
nfnetlink 4142 2 nfnetlink_queue, Live 0xffffffffa00e8000
binfmt_misc 7960 1 - Live 0xffffffffa0078000
nf_conntrack_ipv4 12980 3 - Live 0xffffffffa08e6000
nf_defrag_ipv4 1481 1 nf_conntrack_ipv4, Live 0xffffffffa00ab000
ipt_REJECT 2384 1 - Live 0xffffffffa0075000
xt_tcpudp 2667 2 - Live 0xffffffffa090d000
iptable_filter 2791 1 - Live 0xffffffffa0907000
ip_tables 18390 1 iptable_filter, Live 0xffffffffa08fc000
xt_iprange 1645 0 - Live 0xffffffffa08f6000
xt_state 1490 3 - Live 0xffffffffa08f0000
nf_conntrack 73934 2 nf_conntrack_ipv4,xt_state, Live 0xffffffffa08d1000
xt_mark 1055 6 - Live 0xffffffffa00c2000
xt_NFQUEUE 2344 3 - Live 0xffffffffa002b000
x_tables 22429 7 ipt_REJECT,xt_tcpudp,ip_tables,xt_iprange,xt_state,xt_mark,xt_NFQUEUE, Live 0xffffffffa08c9000
arc4 1473 2 - Live 0xffffffffa0aa3000
snd_pcm_oss 41394 0 - Live 0xffffffffa0a37000
snd_mixer_oss 16299 1 snd_pcm_oss, Live 0xffffffffa0059000
mac80211 238128 2 rt2x00usb,rt2x00lib, Live 0xffffffffa09eb000
snd_pcm 87850 5 snd_ca0106,snd_ac97_codec,snd_pcm_oss, Live 0xffffffffa09d3000
snd_seq_dummy 1782 0 - Live 0xffffffffa0032000
snd_seq_oss 31219 0 - Live 0xffffffffa0105000
snd_seq_midi 5829 0 - Live 0xffffffffa0027000
snd_rawmidi 23388 2 snd_ca0106,snd_seq_midi, Live 0xffffffffa00dc000
snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi, Live 0xffffffffa0011000
cfg80211 148386 2 rt2x00lib,mac80211, Live 0xffffffffa09ac000
snd_seq 57417 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa0994000
snd_timer 23553 2 snd_pcm,snd_seq, Live 0xffffffffa098c000
snd_seq_device 6824 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa00ca000
fbcon 39270 71 - Live 0xffffffffa0980000
tileblit 2487 1 fbcon, Live 0xffffffffa00b3000
font 8053 1 fbcon, Live 0xffffffffa00a4000
crc_ccitt 1675 0 - Live 0xffffffffa0099000
snd 70978 16 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa0962000
bitblit 5811 1 fbcon, Live 0xffffffffa0088000
ppdev 6375 0 - Live 0xffffffffa004d000
softcursor 1565 1 bitblit, Live 0xffffffffa0008000
nvidia 8096262 24 - Live 0xffffffffa010e000 (P)
usb_storage 49833 1 - Live 0xffffffffa00f6000
vga16fb 12757 1 - Live 0xffffffffa0041000
parport_pc 29958 1 - Live 0xffffffffa00ec000
soundcore 8052 1 snd, Live 0xffffffffa00e4000
edac_core 45423 0 - Live 0xffffffffa00ce000
snd_page_alloc 8500 2 snd_ca0106,snd_pcm, Live 0xffffffffa00c5000
edac_mce_amd 9214 0 - Live 0xffffffffa00bd000
k8temp 3912 0 - Live 0xffffffffa00b7000
lp 9336 0 - Live 0xffffffffa00ae000
i2c_nforce2 6099 0 - Live 0xffffffffa00a7000
vgastate 9857 1 vga16fb, Live 0xffffffffa009f000
parport 37160 3 ppdev,parport_pc,lp, Live 0xffffffffa008d000
usbhid 40988 0 - Live 0xffffffffa007b000
hid 83376 1 usbhid, Live 0xffffffffa005e000
8139too 22245 0 - Live 0xffffffffa0051000
8139cp 19541 0 - Live 0xffffffffa0046000
r8169 39554 0 - Live 0xffffffffa0035000
mii 5237 3 8139too,8139cp,r8169, Live 0xffffffffa002e000
floppy 63156 0 - Live 0xffffffffa0015000
pata_amd 11962 2 - Live 0xffffffffa000c000
sata_nv 23778 0 - Live 0xffffffffa0000000
```and 

```
ifconfig
``````
smith@linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa400 

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxxxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:697443 (697.4 KB)  TX bytes:1248720 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.x.x  Bcast:192.168.x.x  Mask:255.255.x.x
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxxxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4680938 (4.6 MB)  TX bytes:4692962 (4.6 MB)

```

You have been most helpful. Again thank you for your time. I've been dealing with this for awhile. 

: )

---

### Post by chili555 on 2010-05-11
To make this permanent:> sudo modprobe rt73usb nohwcrypt=1please do:```
sudo gedit /etc/modprobe.d/rt73usb.conf
```The text editor gedit will open with a new blank file. Add one line:```
options rt73usb nohwcrypt=1
```Proofread, save and close gedit.

---

### Post by Smith.. on 2010-05-11
Ok that's done but I'm still losing some packets but not as many. First time out 7%. The connection has improved a LOT after I created that file.

---

### Post by django0909 on 2010-07-27
I'm having a nightmare getting 10.04 to recognise this card - I can't update anything as I have no internet access on that machine....anyone help? Getting desperate now!!

---

### Post by chili555 on 2010-07-27
Is it the same chipset? Please post:```
lsusb
lsmod | grep -e rt2 -e rt7
```Thanks.

---

### Post by Smith.. on 2010-08-01
```
smith@linux-desktop:~$ lsusb
Bus 001 Device 004: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 003: ID 050d:945a Belkin Components 
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
smith@linux-desktop:~$ lsmod | grep -e rt2 -e rt7
smith@linux-desktop:~$ 

```I ended up purchasing three wifi adapters. The one that I'm using now works yay! It's another Belkin product but this one uses the wireless n protocol. 

Belkin F7D1101v1 

Did not auto run. I did get it to work however by following this guide: 

[http://ubuntuforums.org/showthread.php?p=9539649]("http://http://ubuntuforums.org/showthread.php?p=9539649")

Thank you to the author of that post! I now get wireless n with a linux usb native driver. 

This other device [ Belkin F5D7050 ] used to work right out of the box with previous versions of Ubuntu.  Running 10.4 now and when plugged in oddly it does not anymore? Would like to get them both working. As for the third device I had [ TEW-644UB ]. That one is no longer an issue because I ended up giving that one away to a friend. He needed it and I'm a nice guy. Sorry people it took so long to respond. I've been having wifi issues. Would still love to see the F5D7050 work with the F7D1101v1. That way I could connect to two access points at the same time. Dual wifi seems like it would be cool. 


Thank you all in advance for your time. After scrolling down to see what I had posted before. Chili I just wanted to say first of all thank YOU for YOUR help. This thread and your input has taught me a LOT about some of the basics I needed to know to get this far. Also I've discovered that part of my "lag" issue was that when I connect to the router. The automatic settings were not the optimal ones. What I had to do and this may help others here as well was. Enter the administration page of the router, by going to: 

[http://192.168.1.1](http://192.168.1.1) 

In my browser, this address maybe different depending on your router. But then finding out what the dns servers were and the default gateway. I then used that information to fill out a manual connection in the network manager. I'm getting the numbers messed up though. Sometimes when I create this manual connection. I'm pinging the router with .073 ms and no packet loss but can't view a web page. I'm almost there with the optimal connections. So that's what I got for now. Again thank you for all the help you've been. 

less /proc/modules 

Helped me out a LOT!

---

### Post by venkateshkh on 2010-08-30
[http://http//ubuntuforums.org/showthread.php?p=9539649](http://http//ubuntuforums.org/showthread.php?p=9539649) <-- link doesn't work.
I have a F7D1101v1 and can't get it to work..

---

### Post by Smith.. on 2010-08-30
Try this link here:

[http://ubuntuforums.org/showthread.php?p=9539649](http://ubuntuforums.org/showthread.php?p=9539649)

---

