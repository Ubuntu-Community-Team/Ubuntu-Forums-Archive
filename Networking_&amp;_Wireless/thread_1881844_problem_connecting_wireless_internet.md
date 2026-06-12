---
title: "problem connecting wireless internet"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by infogirl on 2011-11-16
Hello,
 
i have  reinstalled  xubuntu from cd successfully (i hope). But i have problem connecting to the wireless internet. It shows a list of wireless connections. I click on my home wireless network and enter the right password but it fails to connet.
 
I have had previous version of  xubuntu and it worked perfectly... if it helps my computer is samsung rv 508 and my second OS is windows vista (by the way wireless network works ok with it).
 
I have no idea what to do. I'm actually new at open source OS but i really like it. Can anyone help me? Please ...:(

---

### Post by praseodym on 2011-11-16
Hi,

please show the terminal outputs of
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by infogirl on 2011-11-16
Thank you for answering so quickly! :)

---

### Post by paccamura on 2011-11-16
Hi,
I've got a similar problem... after updating to ubuntu 11.11 the wireless stopped working...
this is the output for those commands


thanks for your help





serio_raw              12990  0 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
video                  18908  1 nouveau
wmi                    18744  2 dell_wmi,mxm_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
frida@frida-Inspiron-1520:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by praseodym on 2011-11-16
@infogirl:

Deactivate the Power-management via:

```
sudo iwconfig wlan0 power off
```
Check, if your router allows new clients (MAC-filter off!) and if the encryption is WPA2-AES, not mixed WPA/WPA2 or even WEP or non-encrypted. Additionally you can/should deactivate the hardware encryption of the driver:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo service network-manager restart
```
Check after that:
```
iwconfig
sudo iwlist scan
ifconfig wlan0
dmesg | grep ath
rfkill list
```

@paccamura:

Please show _all_ the outputs. You both can also copy the outputs into a text-file and upload it.

---

### Post by paccamura on 2011-11-16
Hi,
here is the result (text file attached)...
thanks you very much

PS I also tried  "sudo apt-get install --reinstall bcmwl-kernel-source" but it didn't work...

 
I also post this,in case it might help:

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:8d:7a:aa  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe8d:7aaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2246279 (2.2 MB)  TX bytes:780923 (780.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66453 (66.4 KB)  TX bytes:66453 (66.4 KB)




> **praseodym said:**
> 
@paccamura:

Please show _all_ the outputs. You both can also copy the outputs into a text-file and upload it.

---

### Post by paccamura on 2011-11-16
problem solved!
"sudo modprobe b43" did it... 


actually, I tried this before but without disconnecting the Ethernet cable and it didn't work

thanks anyway for your time

---

