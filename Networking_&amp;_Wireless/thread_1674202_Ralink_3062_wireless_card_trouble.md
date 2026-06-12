---
title: "Ralink 3062 wireless card trouble"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by mkrogius on 2011-01-23
Hi, I am absolutely new to linux/ubuntu and I am having issues getting online wirelessly. I installed ubuntu alongside windows 7 and I can connect to wireless networks in windows, but I can't in Ubuntu. Network Manager just says "disconnected" under wireless networks. 

Here is some information that I hope will help you help me.

```
max@max-desktop:~$ uname -r
2.6.35-24-generic
max@max-desktop:~$ lspci -v

03:05.0 Network controller: RaLink Device 3062
    Subsystem: RaLink Device 3062
    Flags: bus master, slow devsel, latency 32, IRQ 20
    Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

max@max-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=3 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```I have only included the part of lspci which concerns the wireless card.

Thanks for helping!

---

### Post by chili555 on 2011-01-23
Let's have a look at:```
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by mkrogius on 2011-01-23
That gives me
```

max@max-desktop:~$ lsmod | grep -e rt2 -e rt3
rt2800pci              10233  0 
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  1 rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
mac80211              266625  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              170293  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci
```

---

### Post by chili555 on 2011-01-23
Looks just fine. Are you, by chance, connected with ethernet? Network Manager is designed to disallow a wireless connection if wired ethernet is available. [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themDoes NM show networks when you detach the ethernet cable and click the icon? Does it try to connect?

---

### Post by mkrogius on 2011-01-23
When I remove the ethernet cable (and reboot for good measure), network manager still shows no available networks.

---

### Post by chili555 on 2011-01-23
Let's see, still with the ethernet cable detached:```
dmesg | grep -e wlan -e rt2
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```

---

### Post by mkrogius on 2011-01-23
Ok.

```
max@max-desktop:~$ dmesg | grep -e wlan -e rt2
[   11.364538] rt2800pci 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   11.389384] Registered led device: rt2800pci-phy0::radio
[   11.389393] Registered led device: rt2800pci-phy0::assoc
[   11.389404] Registered led device: rt2800pci-phy0::quality
[   11.793142] ADDRCONF(NETDEV_UP): wlan0: link is not ready
max@max-desktop:~$ sudo ifconfig wlan0 up
[sudo] password for max: 
max@max-desktop:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

---

### Post by chili555 on 2011-01-23
Ouch! I hate where this is leading us. Please post:```
lspci -nn | grep Network
```Also, there is evidently a newer rt2800pci available. Please hook up the ethernet cable and do:```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-generic
```Detach the ethernet, reboot and run these tests again:```
dmesg | grep -e wlan -e rt2
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Thanks.

---

### Post by mkrogius on 2011-01-23
Okay, the first test gives 

```
max@max-desktop:~$ lspci -nn | grep Network
03:05.0 Network controller [0280]: RaLink Device [1814:3062]
```

and after downloading and rebooting the other tests gave
```

max@max-desktop:~$ dmesg | grep -e wlan -e rt2
[   11.288810] rt2800pci 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   11.295628] Registered led device: rt2800pci-phy0::radio
[   11.295637] Registered led device: rt2800pci-phy0::assoc
[   11.295646] Registered led device: rt2800pci-phy0::quality
[   11.423064] ADDRCONF(NETDEV_UP): wlan0: link is not ready
max@max-desktop:~$ sudo ifconfig wlan0 up
[sudo] password for max: 
max@max-desktop:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

---

### Post by chili555 on 2011-01-23
> $ uname -r
2.6.35-***24***-generic
Just to humor an old chili and to save some hair-tearing, please reboot; immediately hold down the shift key until the GRUB menu comes up. Use the arrow keys to select kernel version 2.6.35-23 and repeat these tests:```
dmesg | grep -e wlan -e rt2
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```If there is no improvement, we will compile rt3562sta from a tar.gz.

---

### Post by mkrogius on 2011-01-23
There was no option for 2.6.35-23 in GRUB, but there was an option for 2.6.35-22 which I chose. This did not work like I expected it to, it only brought up a command line interface (no GUI). I rebooted hoping to get a GUI so i would be able to copy and paste the results of the test into a text file but on the second reboot it was still the same command line interface. On the second reboot something strange happened though. During boot an error flashed up on screen saying something about "MCU request failed". I had to copy the results of the tests out by hand and then type them, so the formatting probably isn't exactly right.

```
max@max-desktop:~$ dmesg | grep -e wlan -e rt2
[11.465765] rt2800pci 0000:03:05.0:PCI INT A -> GSI 20 (level,low) -> IRQ 20
[11.503429] Registered led device: rt2800pci-phy0::radio
[11.503440] Registered led device: rt2800pci-phy0::assoc
[11.503453] Registered led device: rt2800pci-phy0::quality
[11.570513] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[11.672946] ADDRCONF(NETDEV_UP):wlan0: link is not ready
max@max-desktop:~$ sudo ifconfig wlan0 up
[sudo] password for max: 
max@max-desktop:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

When i rebooted into 2.6.35-24 there was no mention of "MCU request failed" and when I ran the tests again they were the same as before, with no mention of "mcu failure".

---

### Post by chili555 on 2011-01-23
Arrgh! Let's compile. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now, with the ethernet cable attached, do:```
sudo apt-get install build-essential linux-headers-generic
```Now, download this package to your desktop: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)> RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592)Right click the package and select 'Extract here.' Open the folder that is extracted and open os/linux/config.mk with the text editor and set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. They are currently =n. Proofread, save and close the text editor. Back to the terminal:```
cd Desktop/DPO
```Press Tab and the remainder will fill in.```
sudo su
make
make install
echo rt3562sta >> /etc/modules
exit
```Reboot and tell us how your wireless is working.

Note any errors and post back. You will get some warnings.

---

### Post by mkrogius on 2011-01-23
Wow!!!! it works!!!! Thank you so much! you are the best!

---

### Post by chili555 on 2011-01-23
Thanks. Glad to help. Have fun!

---

### Post by behoof on 2011-01-30
Chilli555,

You Da Man !!!! errr or woman should that be the case...

No matter, I followed you along with the other fellow and whalla... we be nettin' ...

Straight forward and well stated for we newbies... 

Thank you very much for all the help you didn't know you were giving!!!

Best to ya,
behoof

---

### Post by behoof on 2011-01-31
Thanks so very much!! See message below.  \\"D/

> **chili555 said:**
> Thanks. Glad to help. Have fun!

---

### Post by Elludium_Q-36 on 2011-03-16
There is utility to use windows wireless drivers but it must be an .inf file.

I tried to run the included .exe under wine but get a DLL error.
I don't have a windows box but have downloaded a tar driver file from ralink, on "sneaker net", to try.

---

### Post by chili555 on 2011-03-16
> **Elludium_Q-36 said:**
> There is utility to use windows wireless drivers but it must be an .inf file.

I tried to run the included .exe under wine but get a DLL error.
I don't have a windows box but have downloaded a tar driver file from ralink, on "sneaker net", to try.See post #12 above. It's rather straight-forward. Post back if you get stuck.

---

### Post by Elludium_Q-36 on 2011-03-18
Thanks Chili,

I will try this.  Other posts suggest using the tar command and I had an error, 'old command' needs flag/attriute' etc. and I'm running 8.04!

I'm on "Sneaker Net" which means my box is still offline and I walk to an online box.

I did e-mail ralink asking for the .inf driver file as I have the ndisgtk package installed, which is a userspace utility for ndiswrapper.  Ndiswrapper seems to be a utility to use windows wireless drivers in Ubuntu Linux.

One thing, I have read that when you update the headers, it negates what has been done to make the drivers work...

Thanks, I'll try steps listed in #12 and post back...

---

### Post by chili555 on 2011-03-18
> I have read that when you update the headers, it negates what has been done to make the drivers work...More correctly, the linux-image, also known as kernel. In that case, repeat the process but add an extra step:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
exit
```Adding the module to /etc/modules has already be done in the first install; it need not be repeated.

---

### Post by Elludium_Q-36 on 2011-03-31
Thanks chili,

I got it going, not verbatim but "make install" made it happen.

Unfortunately the 3G to wifi modem, a Virgin Mobile MiFi 2200, gets no signal where I live and my ubuntu box is a desktop.

Time to build a long range WiFi Yagi antenna or try a Verizon USB760 3G modem.  Either that or get a laptop.

There are plenty of broadband desert areas here in the United States.  I wonder if "White space" IEEE 802.22 will ever be implemented. :o|  [http://en.wikipedia.org/wiki/IEEE_802.22](http://en.wikipedia.org/wiki/IEEE_802.22)

---

### Post by jcwojdel on 2011-07-05
Hi everyone,
Did anyone notice 3062 giving big problems on the newest kernels? I had it all working not long ago (drivers from Ralink web-page, blacklisting rt2800 and rt2860, WPA flags for Network Manager to work correctly), but since I started running Natty, the rt3560sta driver hangs the system totally. It does not happen immediately - after modprobing everything runs fine for couple of seconds, driver writes all the right stuff to syslog, and then the system console scrolls through countless pages of debugging information before freezing completely (not even kernel panic to be seen).
Googling did not show up anything but the old trustworthy procedure for installing the driver, so am I the only one with this kind of problem?

---

### Post by jcwojdel on 2011-07-07
More information on the problem on 2.6.38-8-generic kernel:
The network card goes scanning the WiFi channels couple of times without any problem. 
```

[ 5353.058493] SCANNING, suspend MSDU transmission ...
[ 5353.061609] SYNC - BBP R4 to 20MHz.l
[ 5353.063816] RT35xx: SwitchChannel#1(RF=8, Pwr0=20, Pwr1=21, 2T), N=0xF1, K=0x02, R=0x02
[ 5353.206215] RT35xx: SwitchChannel#2(RF=8, Pwr0=20, Pwr1=21, 2T), N=0xF1, K=0x07, R=0x02
[ 5353.350228] RT35xx: SwitchChannel#3(RF=8, Pwr0=20, Pwr1=21, 2T), N=0xF2, K=0x02, R=0x02
...
[ 5354.790212] RT35xx: SwitchChannel#13(RF=8, Pwr0=22, Pwr1=23, 2T), N=0xF7, K=0x02, R=0x02
[ 5354.934215] RT35xx: SwitchChannel#14(RF=8, Pwr0=22, Pwr1=23, 2T), N=0xF8, K=0x04, R=0x02
[ 5355.078213] RT35xx: SwitchChannel#1(RF=8, Pwr0=20, Pwr1=21, 2T), N=0xF1, K=0x02, R=0x02
[ 5355.080413] SYNC - End of SCAN, restore to channel 1, Total BSS[00]
[ 5355.080420] SCAN done, resume MSDU transmission ...
[ 5356.066138] Driver auto reconnect to last OID_802_11_SSID setting - Dennis2860AP, len - 12
[ 5356.066242] CntlOidSsidProc():CNTL - 0 BSS of 0 BSS match the desire (12)SSID - Dennis2860AP
[ 5356.066251] CntlOidSsidProc():CNTL - No matching BSS, start a new scan

```
I'm not actually sure if the final bit about trying to reconnect to "Dennis2860AP" is OK, or not, as it seems to trigger another scan, and then another...

Anyway, after several scans it hangs completely with "unable to handle kernel paging request at ..." message. This does not enter tha logs anymore, as the system freezes completely.

---

### Post by Luponiano on 2011-08-02
Hi jcwojdel, I am facing some problems also (posted in this thread: [http://ubuntuforums.org/showthread.php?p=11098538](http://ubuntuforums.org/showthread.php?p=11098538)). But not as hard as yours, what happens to me is that from time to time the network stops working cutting all my connections and then, after a lag of 10seconds aprox, is as if it restarts again and all connections start to work properly again. 

Still no idea what can be going on here.

---

### Post by Luponiano on 2011-08-03
Hello, I have it working. See my post at: 
```

http://ubuntuforums.org/showthread.php?p=11113880#post11113880

```

---

### Post by Davekyn on 2011-08-06
It works for me, however I had to do it all over again as I lost connection on restart?
Going to restart my computer to see if I loose connection again...
edit... seems to of held up this time round...I wonder what threw it off? Oh well, I'm saving this page and will just reinstall as instructed above next time it drops.
Thanks for the fix at any rate. ;)

---

### Post by Jason Pierce on 2011-10-19
Hi everyone!

After following the solution step by step wifi started working, but "connection info" of Network Manager shows rt2860 driver instead the proper one.

Is this normal? Wifi apparently works well but falls from time to time.

---

### Post by chili555 on 2011-10-19
> **Jason Pierce said:**
> Hi everyone!

After following the solution step by step wifi started working, but "connection info" of Network Manager shows rt2860 driver instead the proper one.

Is this normal? Wifi apparently works well but falls from time to time.
Let's have a look at:```
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by Jason Pierce on 2011-10-19
> **chili555 said:**
> Let's have a look at:```
lsmod | grep -e rt2 -e rt3
```Thanks.

This is the result:

```

seth@Altair:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             986681  1 
seth@Altair:~$

```

Seems to be ok, isn't it?

---

### Post by chili555 on 2011-10-19
Seems to be perfectly correct. Have fun!

---

### Post by Jason Pierce on 2011-10-19
Thx!

---

### Post by Jason Pierce on 2011-12-27
Hi again.

I come back to this thread because the wifi connection, despite I've installed the proper drivers, is very unstable. Every now and then falls and my sister is not having these problems under Windows.

I've tried everything: changing the channels, WPA2 to WPA, disabling internal firewall,... And nothing seems to improve performance.

I'm pretty sure this issue is driver related.


Any suggestion? :confused:

---

### Post by chili555 on 2011-12-28
Do you still have only rt3562sta driving the device? Let's see:```
lsmod
```Are there any clues here?```
sudo cat /var/log/syslog | grep -e etwork -e rt3 | tail -n20
```Thanks.

---

### Post by Jason Pierce on 2011-12-28
Done. Let see if something is going wrong:


```
seth@Altair:~$ lsmod
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  18 
ipt_LOG                17016  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13359  0 
xt_state               12578  6 
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28167  4 
snd_hda_codec_realtek   336771  1 
joydev                 17606  0 
iptable_nat            13182  0 
nf_nat                 25736  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19640  9 iptable_nat,nf_nat
nf_conntrack           81956  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
snd_hda_intel          33176  6 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
usb_storage            53538  0 
usbhid                 46956  0 
uas                    17996  0 
snd_pcm                96391  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nvidia              10709116  48 
hid                    91020  1 usbhid
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
ip_tables              27456  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29581  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
i915                  515134  1 
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         42394  1 i915
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
snd                    67382  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   227534  2 i915,drm_kms_helper
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lm75                   13257  0 
coretemp               13490  0 
rt3562sta             986681  1 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
xhci_hcd               77643  0 
libahci                26642  1 ahci
r8169                  48022  0
```


And...


```
seth@Altair:~$ sudo cat /var/log/syslog | grep -e etwork -e rt3 | tail -n20
[sudo] password for seth: 
Dec 28 14:19:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  4-way handshake -> group handshake
Dec 28 14:19:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  group handshake -> completed
Dec 28 14:21:40 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  completed -> disconnected
Dec 28 14:21:40 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Dec 28 14:21:41 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  scanning -> associating
Dec 28 14:21:41 Altair kernel: [ 6469.575325] ===>Set_NetworkType_Proc::(INFRA)
Dec 28 14:21:41 Altair kernel: [ 6469.575328] Set_NetworkType_Proc::(NetworkType=1)
Dec 28 14:21:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  associating -> associated
Dec 28 14:21:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  associated -> 4-way handshake
Dec 28 14:21:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  4-way handshake -> group handshake
Dec 28 14:21:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  group handshake -> completed
Dec 28 14:23:40 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  completed -> disconnected
Dec 28 14:23:40 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Dec 28 14:23:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  scanning -> associating
Dec 28 14:23:42 Altair kernel: [ 6589.909196] ===>Set_NetworkType_Proc::(INFRA)
Dec 28 14:23:42 Altair kernel: [ 6589.909199] Set_NetworkType_Proc::(NetworkType=1)
Dec 28 14:23:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  associating -> associated
Dec 28 14:23:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  associated -> 4-way handshake
Dec 28 14:23:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  4-way handshake -> group handshake
Dec 28 14:23:42 Altair NetworkManager[954]: <info> (ra0): supplicant connection state:  group handshake -> completed
seth@Altair:~$
```



Apparently driver rt3562 is loaded...

---

### Post by chili555 on 2011-12-28
> Apparently driver rt3562 is loaded...Correct; and no conflicting drivers. Good so far.

I don't see any disconnects and no fixable reason for them. Let's dig deeper:```
sudo cat /var/log/syslog | grep -e etwork -e rt3 > syslog.txt
sudo cat /var/log/syslog.1 | grep -e etwork -e rt3 >> syslog.txt
zip syslog.zip syslog.txt
```Without 'tail -n20' the file will be huge, so we zip it. We also look at the previous log.

You will find a file syslog.zip in your user directory. Please attach the syslog.zip file to your reply using the paperclip tool at the top of the reply box.

---

### Post by Jason Pierce on 2011-12-28
I hope not seem like a fool if you don't find anything. I swear that my connection is very unstable sometimes ;)

Thx!

---

### Post by chili555 on 2011-12-28
I found plenty:> Dec 27 17:19:26 Altair NetworkManager[937]: <info> (ra0): supplicant connection state:  associating -> associated
Dec 27 17:19:26 Altair NetworkManager[937]: <info> (ra0): supplicant connection state:  associated -> 4-way handshake
Dec 27 17:19:26 Altair NetworkManager[937]: <info> (ra0): supplicant connection state:  4-way handshake -> group handshake
Dec 27 17:19:26 Altair NetworkManager[937]: <info> (ra0): supplicant connection state:  **group handshake -> completed**
Dec 27 17:20:04 Altair NetworkManager[937]: <info> (ra0): supplicant connection state:  [COLOR="Red"]completed -> **disconnected**[/COLOR]
Dec 27 17:20:04 Altair NetworkManager[937]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Dec 27 17:20:06 Altair NetworkManager[937]: <info> (ra0): supplicant connection state:  **scanning -> associating**
Let's try to fix it. Please do:```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```Change managed=false to managed=true; proofread, save and close gedit.

Next, do:```
sudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```Change this line as shown:```
SSID=.:Arcadia:.
```Proofread, save and close gedit.

I am wondering if the dots in the name of your network are confusing wpa_supplicant. Can you please try renaming it to Arcadia? Or aArcadiaa?

---

### Post by Jason Pierce on 2011-12-28
Just changing the SSID and managed=true the coverage is much better and by the moment there's no falls.

I'll keep you posted but seems resolved. By the way, what does managed mode really do?


Thx a lot! :D


>>I've attached a new syslog, just in case...

---

### Post by Jason Pierce on 2011-12-28
Ohhhhhh, much less but it's happening again :(

---

### Post by chili555 on 2011-12-28
> By the way, what does managed mode really do?Managed=true means that Network Manager will manage, or try, all the network interfaces. I was wondering if this was a problem from your previous logs that managed=true might solve:> Dec 27 17:18:59 Altair NetworkManager[937]:    SCPluginIfupdown: management mode: unmanaged> much less but it's happening againReviewing the logs. Keep monitoring and keep us posted.

Edit: So far, the logs look the same. Did you reboot after the managed=true change? Would you please?

---

### Post by Jason Pierce on 2011-12-28
I've just rebooted. After a while I'll send another log.


Edit: Here it is. Looks pretty similar to the others.

---

### Post by Jason Pierce on 2011-12-30
More or less same situation. Any idea?

---

### Post by chili555 on 2011-12-31
I have read a couple of bug reports that suggest that Network Manager is the culprit and to install Wicd. Would you please try that and report back. Let me know if you need additional guidance.

---

### Post by Jason Pierce on 2011-12-31
I've installed Wicd and disabled Network Manager loading but authentication wasn't possible, even changing WPA Supplicant driver.

---

### Post by chili555 on 2011-12-31
> and disabled Network Manager loadingI believe you will need to remove it entirely:```
sudo apt-get remove --purge network-manage*
```

---

### Post by Jason Pierce on 2012-01-02
Done. I hope Wicd is doing the trick, connection seems more stable.

We'll see...


Thanks and happy new year!

---

### Post by chili555 on 2012-01-02
Keep us posted. Good luck!

---

### Post by Jason Pierce on 2012-02-01
Hi again.

Now I'm experiencing problems when I try to switch the router config from WPA to WPA2. On every machine start it completely freezes and I have to go back to WPA.

Guess I'll have to manually edit some kind of network config file. Do you think so?


Thanks!

---

### Post by chili555 on 2012-02-01
> Guess I'll have to manually edit some kind of network config file. Do you think so?I do. I'd look for any Wicd configuration files that contain default network profiles and delete them. I'd start looking in /etc/wicd/wireless-settings.conf.

Please be sure your driver actually does WPA2:```
sudo iwlist wlan0 auth
```> wlan0     Authentication capabilities :
		WPA
		[COLOR="Red"]WPA2[/COLOR]
		CIPHER-TKIP
		CIPHER-CCMPFinally, set the router for WPA2 ***only***; not mixed mode WPA and WPA2.

---

### Post by Jason Pierce on 2012-02-02
```
seth@Altair:~$ sudo iwlist ra0 auth
[sudo] password for seth: 
ra0       Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP

```
Ok.


> /etc/wicd/wireless-settings.conf
Successfully deleted. Then shut down computer.


> Finally, set the router for WPA2 only; not mixed mode WPA and WPA2.
Done.


Power on computer again, configure Wicd, 'automatically connect' option cheched (big mistake!), press 'Connect' and Ubuntu freezes again during 'Authentication validation'. After that I'm not able to open any TTY or use 'Safe-mode'. Solution: switch off router, delete Wicd wireless-settings.conf and then configure router to WPA again.



:confused:

---

### Post by Jason Pierce on 2012-02-02
Not sure if is wrong, but I've found in wireless-settings.conf this two options:

enctype=wpa
encryption_method=wpa2

---

### Post by chili555 on 2012-02-02
You might look at:```
sudo less /var/log/syslog
```Use the arrow keys to examine the logs at about the time of the freeze. If the syslog has been archived, check syslog.1. Also check:```
ls /var/log
```Does Wicd have a log to check?

What driver is Wicd set for? wext or ...??

---

### Post by Jason Pierce on 2012-02-02
At /var/log/syslog I haven't found anything related to Wicd, as far as I know... Neither at syslog1.


What I've found is the Wicd log. Is attached to the reply.


At the moment Wicd is working "fine" with wext driver.


Maybe this [**post**]("http://www.linuxquestions.org/questions/slackware-14/wicd-crashed-and-took-x-with-it-919696/") in another forum could be related...

---

### Post by chili555 on 2012-02-02
The thread you linked is inconclusive. Did the original poster indeed have two modules loaded; rt2800pci and rt2860sta? Do you?

Your attached log shows four beautiful, perfect connections. What I wish we were seeing is a crash so we could get some clues. Is there a /var/log/wicd.log.1 or similar other archive?> At the moment Wicd is working "fine" with wext driver.Perhaps with WPA; perhaps not with WPA2.

---

### Post by Jason Pierce on 2012-02-02
> Did the original poster indeed have two modules loaded; rt2800pci and rt2860sta? Do you?

Yes.

```
04:00.0 Network controller: Ralink corp. Device 3062
	Subsystem: Ralink corp. Device 3062
	Kernel driver in use: rt2860
	Kernel modules: rt3562sta, rt2800pci
```

> Is there a /var/log/wicd.log.1 or similar other archive?

Nope.

---

### Post by chili555 on 2012-02-02
> Yes.

```
04:00.0 Network controller: Ralink corp. Device 3062
	Subsystem: Ralink corp. Device 3062
	Kernel driver in use: rt2860
	Kernel modules: rt3562sta, rt2800pci

```
Looks are deceiving. That's not what you said before:> Quote:
Let's have a look at:
Code:

lsmod | grep -e rt2 -e rt3

Thanks.
This is the result:

Code:

seth@Altair:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             986681  1 
seth@Altair:~$

Seems to be ok, isn't it?It never hurts to check:```
lsmod | grep -e rt2 -e rt3
```

---

### Post by Jason Pierce on 2012-02-02
Two ways of checking it and two differente results (apparently):


```
seth@Altair:~$ lspci -k
04:00.0 Network controller: Ralink corp. Device 3062
	Subsystem: Ralink corp. Device 3062
	Kernel driver in use: rt2860
	Kernel modules: rt3562sta, rt2800pci
```


```
seth@Altair:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             986681  1 
seth@Altair:~$
```

---

### Post by chili555 on 2012-02-03
> seth@Altair:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             986681  1 This is the correct result and no extra modules are loaded. 

Are there no signs of a WPA2 crash in syslog or syslog.1?

---

### Post by Jason Pierce on 2012-02-03
Previously I was searching for something like "wicd" in syslog and didn't find anything.

But for "wpa" there's a good amount of lines like these, even after having solved the hang. I'm a bit confused ¿?

> Feb  2 11:47:25 Altair kernel: [   97.764782] WPAPSK Key length(0) error, required 8 ~ 64 characters!(keyStr=)

> Feb  2 16:26:23 Altair kernel: [16831.726220] WPAPSK Key length(0) error, required 8 ~ 64 characters!(keyStr=)

I didn't change the password, so mistake is not an option. Maybe changing it and proving a version without "strange" characters...

---

### Post by chili555 on 2012-02-03
> WPAPSK Key length(0) error, required 8 ~ 64 characters!(keyStr=) That appears to be referencing the file /etc/Wireless/RT2860STA/RT2860STA.dat. You might edit the file to add your details; especially as I've highlighted.```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=[COLOR="Red"]???[/COLOR]
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=[COLOR="Red"]WPA2PSK[/COLOR]
EncrypType=[COLOR="Red"]TKIP? AES?[/COLOR]
WPAPSK=[COLOR="Red"]mysecretkey[/COLOR]

```I am a little surprised that Network Manager doesn't handle all this for you. Can you confirm you made the needed changes to config.mk before you compiled?

---

### Post by Jason Pierce on 2012-02-03
My RT2860STA.dat is a bit longer, but with the changes you suggested is working fine :popcorn:

```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=[COLOR="Red"]mySSID[/COLOR]
NetworkType=Infra
WirelessMode=9
Channel=[COLOR="Red"]13[/COLOR]
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=[COLOR="red"]WPA2PSK[/COLOR]
EncrypType=[COLOR="red"]AES[/COLOR]
WPAPSK=[COLOR="red"]myKey[/COLOR]
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
FtSupport=0
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
PSP_XLINK_MODE=0
WscManufacturer=
WscModelName=
WscDeviceName=
WscModelNumber=
WscSerialNumber=
RadioOn=1
```


If you mean this I'm sure I've done it:

> Right click the package and select 'Extract here.' Open the folder that is extracted and open os/linux/config.mk with the text editor and set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. They are currently =n. Proofread, save and close the text editor.



Just for curiosity, I've attached the piece of syslog file that corresponds to the last hang.



Thanks a lot (again)!

---

