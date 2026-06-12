---
title: "Old Acer Aspire 2310 laptop with atheros ar"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by BruceWasHere on 2011-11-05
Just installed Ubuntu 11.10 tonight. THe wireless hardware switch is 'on',
 but no connections or anything...presently using ethernet cable
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

wlan0  
wlan0: command not found

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

 *-network:1
             description: Ethernet controller
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ath5k latency=168 maxlatency=28 mingnt=10
             resources: irq:17 memory:e2010000-e201ffff


Those are some of the commands that I found that work on my end here.
The wireless worked before install
Please let me know what others 'commands', specifically, you need as I am absofreakinlootley new to Ubuntu!
Thank you all in advance!

---

### Post by BruceWasHere on 2011-11-05
brucifer@brucifer-TravelMate-2310:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
brucifer@brucifer-TravelMate-2310:~$ Sudo rmmod -f acer-wmi
No command 'Sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'udo' from package 'udo' (universe)
Sudo: command not found
brucifer@brucifer-TravelMate-2310:~$ sudo rmmod -f acer-wmi
[sudo] password for brucifer: 
ERROR: Removing 'acer_wmi': No such file or directory
brucifer@brucifer-TravelMate-2310:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

brucifer@brucifer-TravelMate-2310:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host [1039:0661] (rev 11)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 25)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller [1039:0016]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
00:06.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
00:0b.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
brucifer@brucifer-TravelMate-2310:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

brucifer@brucifer-TravelMate-2310:~$

---

### Post by wildmanne39 on 2011-11-05
Hi, welcome to the forum! rfkill says it is hard blocked which usually means the switch is off, can you turn it on by hitting a fn f5 or a set of buttons close to that?

Disconnect your wired connection then you can try:
```
sudo rfkill unblock all
```
Just copy and paste all commands please.

If it does not work post the results of:
```
iwconfig
```
```
rfkill list all
```
```
lsmod | grep ath
```
Thank you

---

### Post by BruceWasHere on 2011-11-06
[wildmanne39;11428995]Hi, welcome to the forum! rfkill says it is hard blocked which usually means the switch is off, can you turn it on by hitting a fn f5 or a set of buttons close to that?
```
 There is no FN F5 or anything like that. Its an actual hardware switch, that remains in the 'on'(lit) position and I cannot get it to turn off no matter how many times i press it or for how long i press it for 
```Disconnect your wired connection then you can try:
```
sudo rfkill unblock all
```brucifer@brucifer-TravelMate-2310:~$ sudo rfkill unblock all
[sudo] password for brucifer: 
brucifer@brucifer-TravelMate-2310:~$ 
'Enable Wireless' = stiill greyed out


If it does not work post the results of:
```
iwconfig
```lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
rfkill list all
```0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
lsmod | grep ath
```ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
cfg80211              172392  3 ath5k,ath,mac80211





I hope that these help you help me, and thank you very much!!!!!

---

### Post by wildmanne39 on 2011-11-06
Hi, try this please:
```
gksudo gedit /etc/rc.local
```
Add these three lines above exit:
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working.
Thank you

---

### Post by BruceWasHere on 2011-11-06
I will definitely try those suggestions after I finish up a memory test.  (29%) I already did a disk check. The reason for these new tests, is  that when i try to boot...the laptop doesn't make it all the way to the  login screen and says something about pressing s to skip and m to  mount... (dev...mapper...cryptswap is not ready or is not present...for mounting something or other)
 it gos to fast for me to see it properly....then the screen goes blank. 
I think it may have to do with a sleep/hybernate/closing the lid setting somewhere.

will update after memtest86 completes

Thank you wildmanne39

I appreciate your info and help

'Additions'....tried the suggestions...but got stuck at the blank screen crap again...have to do a hard shutdown and try again i think...fourth time....wont let me in

---

### Post by wildmanne39 on 2011-11-06
Hi, this is just the networking area but I believe the other problem if you hit s it will load and I think it is caused by a partition or disk that is no longer attached or can not be read.
Thank you

---

### Post by BruceWasHere on 2011-11-06
> **wildmanne39 said:**
> Hi, try this please:
```
gksudo gedit /etc/rc.local
```Add these three lines above exit:
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```Proofread carefully, save and close gedit. Reboot and tell us if it's working.
Thank you


Above instructions = 'Enable Wireless' = still greyed out


network service discovery disabled is also a popup that I get .local domain

---

### Post by BruceWasHere on 2011-11-06
I think that I just have to wait for it to load...takes quite a while though....in regards to ------->(the dev...mapper...cryptswap is not ready or is not present...for mounting something or other)
 
I added this info here to help with the original post about my wireless networking issue as maybe it could be of help.

---

### Post by wildmanne39 on 2011-11-06
Hi, let's make sure it is not for another reason now that you ran the code I gave you, please post the results of:
```
rfkill list all
```
again and 
disconnect your wired connection then run the following commands please.
```
lsmod
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa -e etwork | tail -n55
```
```
dmesg | grep ath
```
Thank you

---

### Post by BruceWasHere on 2011-11-06
[QUOTE=wildmanne39;11432305]Hi, let's make sure it is not for another  reason now that you ran the code I gave you, please post the results of:
```
rfkill list all
``` brucifer@brucifer-TravelMate-2310:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
brucifer@brucifer-TravelMate-2310:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
brucifer@brucifer-TravelMate-2310:~$  Tried both plugged and not plugged
again and 
disconnect your wired connection then run the following commands please.
```
lsmod
```lsmod
Module                  Size  Used by
ath5k                 145100  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
joydev                 17393  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
arc4                   12473  2 
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39822  0 
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  3 ath5k,ath,mac80211
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_sis96x             12743  0 
binfmt_misc            17292  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sis900                 22729  0 
sis_agp                13165  1 
brucifer@brucifer-TravelMate-2310:~$ 

```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa  -e etwork | tail -n55
```sudo cat /var/log/syslog | grep -e ath -e  firmware -e wlan -e wpa -e etwork | tail -n55
[sudo] password for brucifer: 
Nov  6 13:09:37 brucifer-TravelMate-2310 NetworkManager[491]: <info> Activation (eth0) successful, device activated.
Nov  6 13:09:37 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit)  complete.
Nov  6 13:09:37 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get)  complete.
Nov  6 13:09:37 brucifer-TravelMate-2310 avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Nov  6 13:16:52 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): carrier now OFF (device state 100, deferring action  for 4 seconds)
Nov  6 13:16:55 brucifer-TravelMate-2310 dhclient: receive_packet failed on eth0: Network is down
Nov  6 13:16:55 brucifer-TravelMate-2310 avahi-daemon[3181]: Network interface enumeration completed.
Nov  6 13:16:56 brucifer-TravelMate-2310 dhclient: Listening on LPF/wlan0/00:14:a4:0b:46:67
Nov  6 13:16:56 brucifer-TravelMate-2310 dhclient: Sending on   LPF/wlan0/00:14:a4:0b:46:67
Nov  6 13:16:56 brucifer-TravelMate-2310 dhclient: receive_packet failed on eth0: Network is down
Nov  6 13:16:56 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): device state change: activated -> unavailable  (reason 'carrier-changed') [100 20 40]
Nov  6 13:16:56 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Nov  6 13:16:56 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): canceled DHCP transaction, DHCP client pid 2887
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]: <info> (eth0): carrier now ON (device state 20)
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): device state change: unavailable -> disconnected  (reason 'carrier-changed') [20 30 40]
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]: <info> Auto-activating connection 'Wired connection 1'.
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) starting connection 'Wired connection 1'
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): device state change: disconnected -> prepare  (reason 'none') [30 40 0]
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 1 of 5 (Device Prepare)  scheduled...
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 2 of 5 (Device Configure)  scheduled...
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 2 of 5 (Device Configure)  starting...
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): device state change: prepare -> config (reason  'none') [40 50 0]
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 2 of 5 (Device Configure)  successful.
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 3 of 5 (IP Configure Start)  scheduled.
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 3 of 5 (IP Configure Start)  started...
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): device state change: config -> ip-config (reason  'none') [50 70 0]
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in  45 seconds)
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]: <info> dhclient started with pid 3289
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 3 of 5 (IP Configure Start)  complete.
Nov  6 13:17:32 brucifer-TravelMate-2310 NetworkManager[491]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Nov  6 13:17:38 brucifer-TravelMate-2310 NetworkManager[491]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Nov  6 13:17:38 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get)  scheduled...
Nov  6 13:17:38 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get)  started...
Nov  6 13:17:38 brucifer-TravelMate-2310 NetworkManager[491]: <info>   address 192.168.0.166
Nov  6 13:17:38 brucifer-TravelMate-2310 NetworkManager[491]: <info>   prefix 24 (255.255.255.0)
Nov  6 13:17:38 brucifer-TravelMate-2310 NetworkManager[491]: <info>   gateway 192.168.0.1
Nov  6 13:17:38 brucifer-TravelMate-2310 NetworkManager[491]: <info>   nameserver '192.168.0.1'
Nov  6 13:17:38 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit)  started...
Nov  6 13:17:39 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): device state change: ip-config -> activated  (reason 'none') [70 100 0]
Nov  6 13:17:39 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Policy set 'Wired connection 1' (eth0) as default for IPv4  routing and DNS.
Nov  6 13:17:39 brucifer-TravelMate-2310 NetworkManager[491]: <info> Activation (eth0) successful, device activated.
Nov  6 13:17:39 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit)  complete.
Nov  6 13:17:39 brucifer-TravelMate-2310 NetworkManager[491]:  <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get)  complete.
Nov  6 13:17:39 brucifer-TravelMate-2310 avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Nov  6 13:18:58 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): carrier now OFF (device state 100, deferring action  for 4 seconds)
Nov  6 13:19:01 brucifer-TravelMate-2310 dhclient: receive_packet failed on eth0: Network is down
Nov  6 13:19:01 brucifer-TravelMate-2310 avahi-daemon[3437]: Network interface enumeration completed.
Nov  6 13:19:02 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): device state change: activated -> unavailable  (reason 'carrier-changed') [100 20 40]
Nov  6 13:19:02 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Nov  6 13:19:02 brucifer-TravelMate-2310 NetworkManager[491]:  <info> (eth0): canceled DHCP transaction, DHCP client pid 3289
Nov  6 13:19:02 brucifer-TravelMate-2310 dhclient: Listening on LPF/wlan0/00:14:a4:0b:46:67
Nov  6 13:19:02 brucifer-TravelMate-2310 dhclient: Sending on   LPF/wlan0/00:14:a4:0b:46:67
brucifer@brucifer-TravelMate-2310:~$ 
```
dmesg | grep ath
```dmesg | grep ath
[   19.434722] ath5k 0000:00:0b.0: enabling device (0010 -> 0012)
[   19.434752] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.434823] ath5k 0000:00:0b.0: registered as 'phy0'
[   20.607634] ath: EEPROM regdomain: 0x63
[   20.607640] ath: EEPROM indicates we should expect a direct regpair map
[   20.607647] ath: Country alpha2 being used: 00
[   20.607650] ath: Regpair used: 0x63
[   20.762189] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   24.225470] ath5k 0000:00:0b.0: PCI INT A disabled
[   24.276529] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.276616] ath5k 0000:00:0b.0: registered as 'phy1'
[   25.054333] ath: EEPROM regdomain: 0x63
[   25.054339] ath: EEPROM indicates we should expect a direct regpair map
[   25.054346] ath: Country alpha2 being used: 00
[   25.054348] ath: Regpair used: 0x63
[   25.068990] ath5k phy1: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[ 1005.008070] Modules linked in: ath5k bnep rfcomm bluetooth parport_pc  ppdev dm_crypt joydev snd_intel8x0 snd_ac97_codec ac97_bus arc4 snd_pcm  snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia ath mac80211  snd_timer snd_seq_device cfg80211 psmouse serio_raw snd yenta_socket  pcmcia_rsrc pcmcia_core soundcore snd_page_alloc i2c_sis96x binfmt_misc  shpchp lp parport vesafb usbhid hid sis900 sis_agp [last unloaded:  ath5k]
[ 1005.008139]  [<c10478e2>] warn_slowpath_common+0x72/0xa0
[ 1005.008154]  [<c10479b3>] warn_slowpath_fmt+0x33/0x40
brucifer@brucifer-TravelMate-2310:

---

### Post by wildmanne39 on 2011-11-06
Hi, try this please:
Unplug wired connection and run
```
sudo rmmod -f acer-wmi
```
Do not restart your computer if it works we will need to make it permanent.
Thank you

---

### Post by chili555 on 2011-11-07
> **wildmanne39 said:**
> Hi, try this please:
Unplug wired connection and run
```
sudo rmmod -f acer-wmi
```
Do not restart your computer if it works we will need to make it permanent.
Thank youIt won't do us much good to remove acer-wmi; according to lsmod, it isn't loaded. It might, however, help us to load it. Please show us:```
sudo modprobe acer-wmi
dmesg | grep -i acer
```

---

### Post by BruceWasHere on 2011-11-08
It would seem that I had to reinstall Ubuntu, for the fourth time. But, the wireless is working now...I dont understand Ubuntu....yet, but I will. Does anybody still want me to post results of anything or should I mark this as solved?

Thank you very much for your help by the way!!!

---

### Post by wildmanne39 on 2011-11-08
Hi, I am glad to hear that it is working, would you please post the results of:
```
lsmod
```

The information that I found on the issue with your card and 11.10 said it happens once the card has been disabled by using the hardware switch if that is the case and you disable it with the switch or function key you may have that problem again.
Thank you

---

### Post by BruceWasHere on 2011-11-08
Here are the resulkts of that last qyuery:

brucifer@brucifer-TravelMate-2310:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
arc4                   12473  2 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
ath5k                 145100  0 
snd_rawmidi            25241  1 snd_seq_midi
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
pcmcia                 39822  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              172392  3 ath5k,ath,mac80211
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_sis96x             12743  0 
shpchp                 32356  0 
binfmt_misc            17292  1 
sis_agp                13165  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
sis900                 22729  0 
brucifer@brucifer-TravelMate-2310:~$

keep in mind also that I have yet to apply any of the 177 or so updates that are still needing to be done.
I think i will do that now...then we will see what is up with this again.

---

### Post by BruceWasHere on 2011-11-08
updates done and all is still going....*shrug*

---

### Post by wildmanne39 on 2011-11-09
Hi, I am glad that it is still working.

Thank you for posting the information.
Enjoy

---

