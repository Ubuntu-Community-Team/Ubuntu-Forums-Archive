---
title: "Lenovo s205 wireless - xubuntu 12.04"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by parovelb on 2012-04-02
Ciao!
After installing the Precise Pangolin 12.04, my wireless is having troubles and it is hard blocked all the time. The software switch Fn+F2 is working. In the BIOS the wireless is enabled. I can see the "shadowed" wirelss connection stating the switch is OFF although it is ON. I have tried a lot without success. Any ideas?

```
parovelb@lenchi:~$ sudo rfkill list all
0: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
parovelb@lenchi:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Lenovo Device [17aa:f101]
	Kernel driver in use: rt2800pci
parovelb@lenchi:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12759  1 
iptable_filter         12810  1 
iptable_nat            13229  1 
nf_nat                 25891  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           81926  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  4 ipt_MASQUERADE,iptable_filter,iptable_nat,ip_tables
bridge                 91179  0 
stp                    12931  1 bridge
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_conexant    62128  1 
snd_hda_codec_hdmi     32474  1 
sp5100_tco             13791  0 
rfcomm                 47604  16 
bnep                   18281  2 
binfmt_misc            17540  1 
joydev                 17693  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
rts5139               351143  0 
arc4                   12529  2 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
btusb                  18288  2 
bluetooth             180104  23 rfcomm,bnep,btusb
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
psmouse                87603  0 
serio_raw              13211  0 
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
k10temp                13166  0 
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
snd_hda_intel          33773  6 
snd_hda_codec         127706  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
i2c_piix4              13301  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ideapad_laptop         18234  0 
sparse_keymap          13890  1 ideapad_laptop
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
radeon                804319  3 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  22 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
video                  19411  0 
drm                   242038  5 radeon,ttm,drm_kms_helper
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
i2c_algo_bit           13423  1 radeon
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62098  0 
parovelb@lenchi:~$ iwconfig
pan1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
parovelb@lenchi:~$ sudo rmmod acer_wmi
ERROR: Module acer_wmi does not exist in /proc/modules

parovelb@lenchi:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
parovelb@lenchi:~$ 


```

---

### Post by lJ9%3MR&gt;sa on 2012-04-02
Try using my RT5370 tutorial in the Networking section of Ubuntu forums. It should also cover your chipset though I never said it would in the tutorial. Just try.
 
LINK to tutorial:
 
[http://ubuntuforums.org/showthread.php?t=1949996](http://ubuntuforums.org/showthread.php?t=1949996)
 
EDIT:
Actually, I can see that your Ralink card is not USB but PCIe. :(
You may can try my tutorial, but may have to use the PCIe driver from Ralinks website. Google "ralink" and get the driver, unzip, follow my tutorial.
 
Thanks,
faxmanloveswaffles

---

### Post by parovelb on 2012-04-02
sorry, but your solution does not work for me. the code of my result is in [http://ubuntuforums.org/showthread.php?p=11813037&posted=1#post11813037](http://ubuntuforums.org/showthread.php?p=11813037&posted=1#post11813037)

---

### Post by moteprime on 2012-04-09
@parovelb
Hi. We had a longer thread about getting the rt3090 in Ideapad s205 to work with 11.10 here. [http://ubuntuforums.org/showthread.php?t=1849602](http://ubuntuforums.org/showthread.php?t=1849602)
The was two solutions that worked for me, the one i posted in post #20, and the one in post #71 
I have had both of then working in 12.04 but for some unknown reason the easy one in #20 did not work after i upgraded til 12.04 for good. I get the bughttps://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582
So now i use the solutin #20, it works fine.

---

### Post by parovelb on 2012-04-09
@moteprime
Thank you, amigo! Your solution worked fine for me. I did the same as you did. I installed the older driver: [https://launchpad.net/~markus-tisoft...0~ppa1_all.deb](https://launchpad.net/~markus-tisoft...0~ppa1_all.deb).

Blacklisted the modules in /etc/modprobe.d/blacklist.conf:
blacklist acer_wmi
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3390sta 

 And finally added "rt3090sta" in /etc/modules. Did a reboot and voila!

---

### Post by moteprime on 2012-04-10
Do you have full network speed or is it belov 100Kbit/sec.?

I made a mistake in my post, i should have written "So now i use the solutin #71, it works fine." in stead of "#20"

---

### Post by parovelb on 2012-04-10
The connection properties are saying 54 Mb/s although I do not believe it. The connection is sloooow. Speedtest gives 5.02Mbps dowload and 0.99 Mbps upload, 29ms ping.

---

### Post by moteprime on 2012-04-10
This thing is, that it works, but there's something wrong so that the network speed never gets over 70-80 Kb/sec.
Try downloading something big, from somewhere fast and check the download speed.
If it's below 100Kb/sec, clean up the suggestion in post #20 and try the one in post #71. (run it from your /home/ralink).
For now its the only one that works for me.


-and click "The bug affects me", and subscribe to the it:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582")   ;-)

---

