---
title: "Wireless broke after 12.04 update."
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by indie56 on 2012-06-16
Hello:
After the latest update on 12.04, that was yesterday, my wireless has stopped working. My wireless drivers is rt3090sta - This driver is activated but not currently in use. In WICD - no network found. 
Kindly help me to get it back on.
Thanks

---

### Post by chili555 on 2012-06-16
Where did you get rt3090sta? Did you compile it? It's probably no longer needed in 12.04. Please open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by indie56 on 2012-06-17
> **chili555 said:**
> Where did you get rt3090sta? Did you compile it? It's probably no longer needed in 12.04. Please open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

I did not compile the driver. I am having a lenovo laptop. 12.04 had been working perfectly till Jun 14. 
I ran the command. The output is here.
**lspci -nn | grep 0280**
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.



As per the additional hardware drivers, rt3090sta driver is activated but not in use. I had removed NM as I thought that was the problem and installed WICD. Still no internet.

Sorry for the delay in replying. (I have zero knowledge of Ubuntu. Basically I have been searching on line and doing copy paste)
Thanks

---

### Post by wildmanne39 on 2012-06-17
Hi, I will be helping you while my friend the expert chili555 is out of town please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
rfkill list all
lsmod
nm-tool
```
Thanks

---

### Post by indie56 on 2012-06-17
Here is the output- 

inderpaldeol@ubuntu:~$ **cat /etc/lsb-release; uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
inderpaldeol@ubuntu:~$ **lspci -nnk | grep -iA2 net**
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Lenovo Device [17aa:f101]
	Kernel driver in use: rt2860
inderpaldeol@ubuntu:~$ **rfkill list all**
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
inderpaldeol@ubuntu:~$ **lsmod**
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  7 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  1 
ppdev                  17113  0 
dm_crypt               23125  0 
binfmt_misc            17540  1 
joydev                 17693  0 
iptable_nat            13229  0 
nf_nat                 25891  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           81926  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_conexant    62311  1 
snd_hda_codec_hdmi     32474  1 
snd_seq_midi           13324  0 
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
fglrx                3263886  129 
psmouse                87692  0 
rts5139               351143  0 
snd_timer              29990  2 snd_pcm,snd_seq
serio_raw              13211  0 
uvcvideo               72627  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               98259  1 uvcvideo
k10temp                13166  0 
v4l2_compat_ioctl32    17128  1 videodev
sp5100_tco             13791  0 
snd                    78855  18 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13301  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ideapad_laptop         18234  0 
sparse_keymap          13890  1 ideapad_laptop
mac_hid                13253  0 
rt3090sta             944003  1 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 
video                  19596  0 
wmi                    19256  0 
inderpaldeol@ubuntu:~$ **nm-tool**

NetworkManager Tool

State: connected (global)

- Device: ra0  [Auto DEOL] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             connected
  Default:           yes
  HW Address:        94:39:E5:47:00:18

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SBS:             Infra, 84:C9:B2:4E:9D:DB, Freq 2432 MHz, Rate 54 Mb/s, Strength 39 WPA
    *DEOL:           Infra, 3C:EA:4F:C1:F1:B9, Freq 2437 MHz, Rate 54 Mb/s, Strength 88 WPA
    WF:              Infra, 78:CD:8E:C1:88:39, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    RKS:             Infra, 00:26:F3:9C:C1:AE, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    d-jay:           Infra, 00:22:75:F1:AA:7F, Freq 2437 MHz, Rate 22 Mb/s, Strength 39 WPA WPA2
    AamchiMumbai:    Infra, 00:26:F3:2B:D8:59, Freq 2457 MHz, Rate 54 Mb/s, Strength 25 WPA
    MM:              Infra, 00:22:2D:1F:23:84, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA
    RKV:             Infra, 00:1D:7E:68:74:78, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    HomeDesktop:     Infra, 00:22:2D:E3:54:B1, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA
    SD-LINK:         Infra, 00:1B:11:61:F8:A3, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WEP
    BELL073:         Infra, 00:26:50:BE:6F:61, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WEP
    romi:            Infra, 00:26:F3:33:6D:C2, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA

  IPv4 Settings:
    Address:         192.168.2.24
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:94:4E:EA

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


inderpaldeol@ubuntu:~$ 

I have been searching the net and executed quite a few commands from various forums.  ( I don't have the faintest idea what they do). I removed and installed NM and WICD many times. I do not know what i did, the wifi started working. NM is not installed, WICD shows no wireless connections available but I am having internet connected. Which program is connecting to the router?
I don't know if you will like to continue this thread.
Thanks

---

### Post by wildmanne39 on 2012-06-17
Hi, please post the output of:
```
ps aux | egrep 'Network|wicd'
```
it is hard to know what is going on without knowing all the commands you ran.

When you can connect does it work good? because you are using the wrong driver for 12.04 it should be rt2800pci.

How did you install that driver? where did you get it from?
Thanks

---

### Post by indie56 on 2012-06-18
The connection is working fine. The output is - 

~$ **ps aux | egrep 'Network|wicd'**
root       973  0.0  0.1 233596  5508 ?        Ssl  Jun17   0:12 NetworkManager
root      1212  0.1  0.3 164880 12188 ?        S    Jun17   1:48 /usr/bin/python -O /usr/share/wicd/daemon/wicd-daemon.py
root      1250  0.0  0.2  86324 10808 ?        S    Jun17   0:59 /usr/bin/python -O /usr/share/wicd/daemon/monitor.py
1000      2179  0.0  0.6 356076 24956 ?        Sl   Jun17   0:01 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py --tray
root     25176  0.0  0.0   7256  1556 ?        S    03:15   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-ra0.pid -lf /var/lib/dhcp/dhclient-4068a897-ae59-4eb6-87ce-64ccd6a94bb4-ra0.lease -cf /var/run/nm-dhclient-ra0.conf ra0
1000     28096  0.0  0.0   9376   928 pts/0    S+   05:32   0:00 egrep --color=auto Network|wicd

Regarding that driver- I have no idea how it got there or if it is the wrong driver. Somewhere I used this link [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

Thanks

---

### Post by wildmanne39 on 2012-06-18
Hi, it looks like you have some of the files left from network manager that may be causes you to not show any wireless connections available, we can try to fix it but if you want to wait until chili555 is back since your wireless is working that is understandable.

I believe you installed the 11.04 driver and blacklisted several others to get your connection working you can leave it that way if you are happy with your speed and stability or we could get rid of it and use the driver for 12.04 which usually needs a parameter added to it to make it work better.
Thanks

---

### Post by indie56 on 2012-06-18
Lets do it.
Please give exact commands that I can copy and paste in the terminal.

Thanks

---

### Post by wildmanne39 on 2012-06-18
Hi, first let me make sure I understand the issue with wicd you do not show any wireless networks available correct? can you post a screenshot of that?

My understanding is that wicd does not put an icon in the top panel like network manager does.

You want to keep using the same drivers correct?
Thanks

---

### Post by indie56 on 2012-06-19
The WICD screenshot is attached.

I would like to use the 12.04 driver.

Thanks

---

### Post by wildmanne39 on 2012-06-19
Hi, let's see if we can get wicd to see your network, you may have it setup manually.

Please do:
```
sudo apt-get install --reinstall wicd
```
Then:
```
sudo apt-get purge network-manager network-manager-gnome
```
does that fix not being able to see wireless networks?

Please post the output of:
```
cat /etc/modprobe.d/blacklist.conf
cat /etc/network/interfaces
```
so I can see if the driver for 12.04 is blacklisted before we try to use it and if the connection is setup manually.

Also let's try the driver temporarily like this:
```
sudo modprobe -r rt3090sta
sudo modprobe rt2800pci nohwcrypt=1
```
if it does not connect just reboot.

---

### Post by indie56 on 2012-06-19
The purge command killed the wireless. Now I am on cable.
Still no wireless on WICD

Other commands executed - 

l@ubuntu:~$ **cat /etc/modprobe.d/blacklist.conf**
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# Blacklist conflicting RaLink driver modules
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

blacklist acer-wmi
inderpaldeol@ubuntu:~$** cat /etc/network/interfaces**
auto lo
iface lo inet loopback

@ubuntu:~**$ sudo modprobe -r rt3090sta**
[sudo] password for inderpaldeol: 
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
@ubuntu:~$ **sudo modprobe rt2800pci nohwcrypt=1**
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.

Now there is no wifi even on rebooting

---

### Post by wildmanne39 on 2012-06-19
Hi, you had both wicd and network manager installed there was no way to know which one was running it but usually with both installed you can not connect at all.

With wicd did you manually set up wireless it has to be setup manually for dhcp you use dhclient, if we need to we will remove wicd and go back to network manager.
Thanks

---

### Post by indie56 on 2012-06-19
Removed WICD, installed NM. On reboot the wireless is working.

Lets leave it at that until it messes up next time.

Thanks

---

### Post by wildmanne39 on 2012-06-19
Hi, ok if you decide to change to the 12.04 driver just let us know.
Thanks

---

### Post by indie56 on 2012-07-05
Hello:
Once again the wifi broke with the new update. I think its time to get a permanent solution to this problem and use the 12.04 driver. 
Can you please let me know action to be taken to overcome this suitation.
Thanks

---

### Post by chili555 on 2012-07-05
Let's take a few steps.> WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.Let's see what's in there, put it where it really belongs and remove the conflict and warning:```
cat /etc/modprobe.conf
```Next, let's remove the blacklists:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Remove the parts I've highlighted:```

<snip>
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

[COLOR="Red"]# Blacklist conflicting RaLink driver modules
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

blacklist acer-wmi[/COLOR]
```Caution, only the parts I've highlighted are to be removed; the remainder of the file is unchanged. Proofread carefully, save and close gedit.

Reboot and let us have your report.

---

### Post by indie56 on 2012-07-05
Hello:
Thanks for a quick reply.
I have done as suggested and rebooted. The wifi - Network Manager is working.
Next step?

Thanks

---

### Post by chili555 on 2012-07-05
Do you mean the wifi is working or Network Manager is working or both? Can you click the NM icon, see your network and connect?

---

### Post by indie56 on 2012-07-05
NM is working and I can see other networks too. I am connected to my wifi router.

---

