---
title: "Ubuntu 10.10 Wireless chip needs help"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by robrocks07 on 2011-01-22
Hi,

I'm fairly new at linux... so excuse me if this is fixed i can't seem to solve it from reading all the forum posts on it.

I recently battled with a broadcom 4312 chipset for about a month and a half trying everything from b43fwcutter to ndiswrapper. It wouldn't budge.  I can get wired internet but wireless is a no go.

Well yesterday after a trip to a local computer store i found a used atheros chipset that when inserted into my compaq the wireless led actually was on so i said yes itll work.  But after returning home and looking for drivers and all that im still at square one.

edit : oh and i forgot to mention i've tried a couple different posts solutions ....couldn't even get madwifi installed or anything ath5k seems to have been auto installed....??? not sure couldn't get any changes out of it and ath_pci couldn't find the load for it. I still have ndiswrapper on here and im wondering if it's blocking it from working if so i need to remove it and i cant seem to do that. And if it makes a difference im running 64 bit ubuntu 10.10

so please help

> lspci -v:

07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

> lsmod:

ath5k                 143332  0 
mac80211              266625  1 ath5k
ath                    10413  1 ath5k
cfg80211              170293  3 ath5k,mac80211,ath
led_class               3393  1 ath5k
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_nvhdmi    15451  1 
snd_hda_codec_conexant    37631  1 
binfmt_misc             7984  1 
nvidia              10221046  40 
joydev                 11395  0 
arc4                    1497  2 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  6467  0 
snd                    64181  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                62080  0 
soundcore               1240  1 snd
video                  22176  0 
serio_raw               4910  0 
edac_core              46822  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
output                  2527  1 video
shpchp                 34910  0 
edac_mce_amd            9387  0 
k10temp                 3535  0 
i2c_nforce2             6155  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84710  1 usbhid
usb_storage            50372  0 
ahci                   22210  2 
forcedeth              55649  0 
pata_amd               12050  0 
libahci                26052  1 ahci

> sudo iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off


Anything else i can provide to help solve this problem please let me know.

---

### Post by telovin on 2011-01-22
Try removing ndiswrapper, Just follow these commands to remove ndiswrapper.(if u compiled it from source)

```
sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo /lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko
```

---

### Post by robrocks07 on 2011-01-22
Thanks i did all of that and restarted but it seems like its still up as the "windows wireless drivers" is still under system->administration

---

### Post by telovin on 2011-01-22
If ndiswrapper reappears atetc modules,try this 

```
sudo nano /etc/modules
```
Delete the etc/modules line, and save (Ctrl+X).
Reboot.

Then run

```
sudo apt-get install -f
```

or

```
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
```

---

### Post by telovin on 2011-01-22
If it still doesn't work, try following this ndiswrapper troubleshooting guide

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by robrocks07 on 2011-01-22
> robert@robert:~$ sudo nano /etc/modules
[sudo] password for robert: 
robert@robert:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
robert@robert:~$ sudo modprobe ath_pci
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ath_pci not found.
robert@robert:~$ sudo modprobe wlan_scan_sta
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module wlan_scan_sta not found.
robert@robert:~$ 


i tried what you posted nothing seemed to have worked ill try that thread

---

### Post by telovin on 2011-01-22
I told u what I knew.May be someone else who is more proficient in ndiswrapper will help u out.

---

### Post by telovin on 2011-01-22
You can also try this:

```
sudo killall ndiswrapper
```

copy and paste the results here.It will help the person who is gonna help you out.I am not a pro here. I just told u what I know. May be an expert will help you out soon. It will be of immense help  to them if you copy n paste the results of the commands that u executed on terminal.

---

### Post by amsterdamharu on 2011-01-22
Could you post the output of the following command?

```
sudo rfkill list
```To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by robrocks07 on 2011-01-22
```
robert@robert:~$ sudo rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
```

ok theres rfkill and the killall didn't work said no process so i think its gone but now i need wireless

---

### Post by amsterdamharu on 2011-01-22
They are all soft blocked, I don't know which one is the atheros but you can unblock it with rfkill:

```
sudo rfkill unblock 0
rfkill list
```

That should remove the software block from "hp-wifi" as that is identified by 0 in rfkill list.

If that didn't do the trick I suggest blocking it again an unblock the 2nd one:

```
sudo rfkill block 0
 sudo rfkill unblock 1
 rfkill list
```

---

### Post by robrocks07 on 2011-01-28
sweet nibblets it finally works i ended up unblocking everything and so far its working off wireless just fine

THANK YOU SO MUCH!!!

---

