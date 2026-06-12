---
title: "Unable to complete PPPoE Discovery"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by LaTable on 2012-02-19
Dear Ubuntu users,
 
 I cannot establish a wireless Internet connection with my modem . I use Ubuntu 10.04. I've read some other threads on the topic but it didn't help. Actually the link works for a few seconds (some packets could be exchanged as you will see below), then it disconnects. I used 'pppoeconf' to configure my wlan0 device and I use 'pon dsl-provider' to start a connection. My Laptop is a FujitsuSiemens.
 My wlan card is Intel Corporation PRO/Wireless 3945ABG [Golan].
 
 Note that my wired eth0 connection works fine (I'm using it right now) and my wireless LAN used to work with Windows.
 
 Here is what I could monitor:
 
 $ plog  
 Feb 19 04:38:10 nicolas-laptop pppd[1739]: Using interface ppp0  
 Feb 19 04:38:10 nicolas-laptop pppd[1739]: Connect: ppp0 <--> wlan0  
 Feb 19 04:38:10 nicolas-laptop pppd[1739]: PAP authentication succeeded  
 Feb 19 04:38:10 nicolas-laptop pppd[1739]: peer from calling number 00:90:1A:41:65: DC authorized  
 Feb 19 04:38:10 nicolas-laptop pppd[1739]: Cannot determine ethernet address for proxy ARP  
 Feb 19 04:38:10 nicolas-laptop pppd[1739]: local  IP address XX.XX.XX.XX  
 Feb 19 04:38:10 nicolas-laptop pppd[1739]: remote IP address 213.191.89.9  
 Feb 19 04:38:10 nicolas-laptop pppd[1739]: primary   DNS address 213.191.92.87  
 Feb 19 04:38:10 nicolas-laptop pppd[1739]: secondary DNS address 62.109.123.6  
 $ plog  
 Feb 19 04:40:07 nicolas-laptop pppd[1739]: Timeout waiting for PADO packets  
 Feb 19 04:40:07 nicolas-laptop pppd[1739]: Unable to complete PPPoE Discovery  
 
 Could the problem come from the first failure? Namely from:  
 &#8220;Cannot determine ethernet address for proxy ARP &#8221;
 
 Here are some details on my network interfaces:
 $ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:17:42:30:33:95   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:16  

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)  
 
 wlan0     Link encap:Ethernet  HWaddr 00:19:d2:84:10:93   
           inet6 addr: fe80::219:d2ff:fe84:1093/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:359 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:544 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:174162 (174.1 KB)  TX bytes:127245 (127.2 KB)  
 

 If someone has a solution, I would be very grateful !

---

### Post by praseodym on 2012-02-19
Hi,

if you want to use a router, add the Login/PW of your ISP into the router interface. "pppoeconf" is not needed in this case. Reset the /etc/network/interfaces file to
```
auto lo
iface lo inet loopback
```
and reboot.

---

### Post by gradinaruvasile on 2012-02-19
pppoe via wireless? Why do you want to use that? Most (if not all) routers support pppoe, so you should set up the pppoe connection directly on your router. Everything that connects to your router should use standard LAN/WLAN connections. Its the simplest and most stable way.
Unless you have some very weird hardware setup there.

---

### Post by LaTable on 2012-02-28
> pppoe via wireless? Why do you want to use that?
Because that's what my ISP (Alice-Germany) told me to do. My DSL modem is not configured as a router (as far as I know) and other computers in my apartment work properly with this modem.

I realise that wireless pppoe is not  easy with Ubuntu as it is not supported by the Network Manager
[]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/601625")[URL="https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/355826"]https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/601625
https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/355826
[/URL]But still, I don't understand why pppoeconf does not provide me with a wireless connection. 
> Reset the /etc/network/interfaces file to
auto lo
iface lo inet loopback
and reboot. 
 I did, it didn't work for me. But it seems to work for some other people:
[]("http://ubuntuforums.org/showthread.php?t=1556204")[http://ubuntuforums.org/showthread.php?t=1556204](http://ubuntuforums.org/showthread.php?t=1556204)

---

### Post by praseodym on 2012-02-28
Ok, some more info:

```
route -n
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```

---

### Post by LaTable on 2012-03-26
I apologize for replying late. My problem is still the same. Here are the requested infos:

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

``````
$ lsmod
Module                  Size  Used by
pppoe                   8943  0 
pppox                   2074  1 pppoe
rfcomm                 33453  4 
sco                     7949  2 
bridge                 45646  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30656  16 rfcomm,bnep
binfmt_misc             6587  1 
snd_hda_codec_realtek   203472  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
arc4                    1153  2 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
pcmcia                 30784  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usbhid                 36110  0 
btusb                  11053  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
iwl3945                68727  0 
iwlcore               106149  1 iwl3945
snd_timer              19130  2 snd_pcm,snd_seq
i915                  289683  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
yenta_socket           20408  1 
mac80211              205434  2 iwl3945,iwlcore
drm_kms_helper         29329  1 i915
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             25962  1 
intel_agp              24375  2 i915
drm                   163779  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
irda                  186780  0 
crc_ccitt               1339  1 irda
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               3978  0 
cfg80211              126528  3 iwl3945,iwlcore,mac80211
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
fujitsu_laptop         10889  0 
led_class               2864  3 iwl3945,iwlcore,fujitsu_laptop
hid                    67288  1 usbhid
output                  1871  1 video
agpgart                31724  2 intel_agp,drm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
sky2                   40807  0 
ahci                   32680  2 

``````
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

``````
$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
$ cat /etc/resolv.conf
nameserver 62.109.123.197
nameserver 213.191.74.19
# Generated by NetworkManager

```

---

### Post by praseodym on 2012-03-27
Obviously it is a router, otherwise there would be no wlan0 connection shown. Can you connect via cable? If yes, add the router IP into the browser, deactivate the N-mode there and dont hide the network. Change also the encryption to pure WPA2-AES if possible

---

### Post by LaTable on 2012-03-28
I upgraded to Ubuntu 12.04 (beta version) and it works. Of course, as an Ubuntu novice, I cannot explain why. Under my previous Ubuntu (10.04), I might have installed something wrong like an inappropriate driver, I don't know/remember. Now, here is what I get (addresses are replaced with X)

$ sudo pppoeconf wlan0
Plugin rp-pppoe.so loaded.
$ plog
Mar 28 09:31:30 nicolas-laptop pppd[2721]: peer from calling number XX:XX:XX:XX:XX:XX authorized
Mar 28 09:31:30 nicolas-laptop pppd[2721]: local  IP address XX.XX.XX.XX
Mar 28 09:31:30 nicolas-laptop pppd[2721]: remote IP address XX.XX.XX.XX
Mar 28 09:31:30 nicolas-laptop pppd[2721]: primary   DNS address XX.XX.XX.XX
Mar 28 09:31:30 nicolas-laptop pppd[2721]: secondary DNS address XX.XX.XX.XX

So, I don't get the message "Cannot determine ethernet address for proxy ARP" any more.
Thanks for your support!

---

