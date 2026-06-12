---
title: "Cisco t30 wireless"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2011-06-09
hi all,

i have been looking on the internet for the answer but not found an answer.

i have a old ibm t30 laptop with ubuntu 11.04 32-bit installed and all works fine apart from the wireless.

running the lspci gives this:

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

how do i install this wireless card i believe it is a cisco aironet 350

---

### Post by chili555 on 2011-06-09
Ooh! I love old Thinkpads! I have had a few and still have a T40. The driver for your card is probably already built in. We need to see the pci.id to know why it's not driving your card already. Please run and post:```
lspci -nn | grep Network
lsmod
```Thanks.

---

### Post by elliotbeken on 2011-06-09
thanks for the fast reply

elliot@ibm:~$ lspci -nn | grep Network
> 02:02.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]> 
elliot@ibm:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
i2c_dev                13116  0 
i2c_i801               17265  0 
cpuid                  12774  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
radeon                896428  2 
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
thinkpad_acpi          73750  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
pcmcia                 39671  0 
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
ttm                    65184  1 radeon
joydev                 17322  0 
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
snd_timer              28659  2 snd_pcm,snd_seq
drm                   180037  4 radeon,ttm,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
airo                   73165  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55295  12 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
irda                  185091  0 
i2c_algo_bit           13184  1 radeon
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
parport_pc             32111  1 
soundcore              12600  1 snd
video                  18951  0 
nvram                  14035  1 thinkpad_acpi
crc_ccitt              12595  1 irda
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e100                   40108  0 

---

### Post by chili555 on 2011-06-09
As you can see in lsmod, the module *airo* is loaded. Makes some sense for an Aironet card, doesn't it? Now, let's have a look at:```
rfkill list all
iwconfig
dmesg | grep airo
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by elliotbeken on 2011-06-09
rfkill list all - no output

> elliot@ibm:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1020   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1020   Missed beacon:0> elliot@ibm:~$ dmesg | grep airo
[   10.847023] airo(): Probing for PCI adapters
[   10.890720] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.890759] airo(): Found an MPI350 card
[   13.000577] airo(eth1): Firmware version 5.41.00
[   13.000583] airo(eth1): WPA supported.
[   13.000588] airo(eth1): MAC enabled 00:0e:9b:1b:c4:76
[   13.002575] airo(): Finished probing for PCI adapters

thanks for the help

---

### Post by chili555 on 2011-06-09
Looks perfect to me! You have a driver, a wireless interface and no complaints in dmesg. When you click the Network Manager icon, do you see networks? Your own? Does it try to connect?

By the way, I am surprised by this:> airo(eth1): WPA supported.It may be suggesting that, due to the age of this card, it supports WPA and not WPA2. I really don't know for sure. Is your network set to WPA2? Can you change to good old-fashioned WPA?

---

### Post by elliotbeken on 2011-06-09
if i click on the network icon on the top right of the screen it says

"wireless networks - disconnected"

i have made sure the wireless card is not disabled via a "fn" key function and i have also checked in the bios. 

any other ideas ?

---

### Post by chili555 on 2011-06-09
Are there any interesting messages in:```
sudo iwlist eth1 scan
cat /etc/network/interfaces
dmesg | grep eth1
```

---

### Post by elliotbeken on 2011-06-09
> elliot@ibm:~$ sudo iwlist eth1 scan
[sudo] password for elliot: 
eth1      No scan results

thanks

---

### Post by chili555 on 2011-06-09
> **elliotbeken said:**
> thanksHow about the other commands?

---

### Post by elliotbeken on 2011-06-09
what i have done is swapped the wireless card for one exactly the same i now i can see wireless networks !!

i still have the problem of not being able to connect due to encryption problems.

the wireless authentication is WPA-PSK/WPA2-PSK is this wireless card able to connect to this ?

thanks for all the help so far :)

---

### Post by chili555 on 2011-06-09
> the wireless authentication is WPA-PSK/WPA2-PSK is this wireless card able to connect to this ?See my comment above. The WPA *and* WPA2 mixed mode is always tricky; I'd try WPA2 only and, if it won't connect, try WPA.

---

### Post by thushw on 2011-09-03
> **chili555 said:**
> Looks perfect to me! You have a driver, a wireless interface and no complaints in dmesg. When you click the Network Manager icon, do you see networks? Your own? Does it try to connect?

By the way, I am surprised by this:It may be suggesting that, due to the age of this card, it supports WPA and not WPA2. I really don't know for sure. Is your network set to WPA2? Can you change to good old-fashioned WPA?

chili555 - I have a problem somewhat similar. same hardware, airo driver and the dmesg output is similar except there is a "airo(eth1): link lost (local choice)"

any clues as to how i can get this to work? iwlist scan shows the access point (both eth1 and wifi0) but iwconfig does not show an ESSID for either, neither does it show access points, says "Invalid".

Trying to set essid with iwconfig does not set it. Other parameters (like Mode) can be set, but not the essid.

---

### Post by thinkpad2 on 2012-09-17
Hi
I have a similar problem. My notebook it is t42.
my card sees the network but can't connect.
Lubuntu 12.04

lspci -nn | grep Network
> 02:02.0 Network controller [0280]: Cisco Aironet Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]

lsmod
> Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
radeon                733718  2 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
pcmcia                 39791  0 
ttm                    65344  1 radeon
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
drm_kms_helper         45466  1 radeon
snd_rawmidi            25424  1 snd_seq_midi
drm                   197692  4 radeon,ttm,drm_kms_helper
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
i2c_algo_bit           13199  1 radeon
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
airo                   77500  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
shpchp                 32325  0 
snd                    62064  12 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
video                  19068  0 
serio_raw              13027  0 
irda                  185517  0 
nvram                  14029  1 thinkpad_acpi
parport_pc             32114  1 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
crc_ccitt              12595  1 irda
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e1000                 101693  0 
floppy                 60310  0

iwconfig
> wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-105 dBm
          Rx invalid nwid:2525  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10025   Missed beacon:0

lo        no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-105 dBm
          Rx invalid nwid:2525  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10025   Missed beacon:0

eth0      no wireless extensions.

dmesg | grep airo
> [    9.063475] airo(): Probing for PCI adapters
[    9.063538] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    9.063569] airo(): Found an MPI350 card
[   10.010855] airo(eth1): Firmware version 5.41.00
[   10.010859] airo(eth1): WPA supported.
[   10.010863] airo(eth1): MAC enabled 00:0e:9b:44:09:ef
[   10.011571] airo(): Finished probing for PCI adapters
In xp wpa not works.

sudo iwlist eth1 scan
> eth1      Scan completed :
          Cell 01 - Address: 74:EA:3A:D0:79:83
                    ESSID:"Domek"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=100/100  Signal level=-36 dBm  Noise level:-105 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100


cat /etc/network/interfaces
> fauto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

---

### Post by thinkpad2 on 2012-09-17
Ok, I found the solution.
[http://ubuntuforums.org/showpost.php?p=8740779&postcount=6](http://ubuntuforums.org/showpost.php?p=8740779&postcount=6)

---

### Post by Nukem125685 on 2012-10-03
lol bro thank you so much !! its working now never been so happy haha.... my mom brought a new lap and gave this one to me and i hate windows so changed to zorin os 6 lite and it rules!! you know wifi never worked on xp and it does on ubuntu... lol I love linux..

---

