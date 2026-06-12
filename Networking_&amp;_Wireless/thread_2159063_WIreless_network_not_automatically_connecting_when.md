---
title: "WIreless network not automatically connecting when booting"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by Janno2 on 2013-07-01
I had to re-install 12.04, which went good. 
However, my HP Pavilion laptop with a Broadcom 4311 on board was giving problems to establish a wireless connection.
So I connected to the internet using a cable, and was able to do the necessary updates a.s.o.
I managed to get the wireless connection working again, but when I do restart the system the wireless connection will not work.
I can manually make it work, but I did activate the option to make a connection automatically at start up.
Which does not work.

nm-tool learns:
Device: eth0
Type: wired 
Driver: forcedeth
State: unavailable
Default: No
HW Address: 00:1B:24:7F:D4:5A

Capabilities:
Carrier detect: yes

Wired Properties
Carrier: Off

I did remove the wired connection. 

How to fix?

---

### Post by Hadaka on 2013-07-01
Hi, did you check mark "Connect Automatically" with the
network mgr. setting? also..please post the output of..
```
lspci -nn | grep 0280
```
thanks.

---

### Post by Janno2 on 2013-07-01
> **Hadaka said:**
> Hi, did you check mark "Connect Automatically" with the
network mgr. setting? also..please post the output of..
```
lspci -nn | grep 0280
```
thanks.

Yes, I sis check the "Connect Automatically".

spci - nn | grep 0280 gives: 03:00.0 Network Controlle [0280]: Broadcom Corporation BCM 4311 802.11a/b/g [14e4:4312]] (rev 02)

---

### Post by Hadaka on 2013-07-01
ok, lets take a quick look at..
please post the output of..
```
lsmod
```
then we can write a file to get that going on boot.
thanks.

---

### Post by Janno2 on 2013-07-01
> **Hadaka said:**
> ok, lets take a quick look at..
please post the output of..
```
lsmod
```
then we can write a file to get that going on boot.
thanks.

There it is:

jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$ lsmod 
Module                  Size  Used by 
vesafb                 13516  1 
joydev                 17393  0 
nvidia              10286823  43 
snd_hda_codec_conexant    52521  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec 
rfcomm                 38139  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
psmouse                86520  0 
serio_raw              13027  0 
r852                   17901  0 
k8temp                 12905  0 
usbhid                 41937  0 
uvcvideo               67203  0 
hid                    77428  1 usbhid 
sm_common              16772  1 r852 
videodev               86588  1 uvcvideo 
nand                   49667  2 r852,sm_common 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event 
nand_ids                8547  1 nand 
mtd                    35584  2 sm_common,nand 
nand_bch               13003  1 nand 
bch                    21784  1 nand_bch 
nand_ecc               13105  1 nand 
snd_timer              28931  2 snd_pcm,snd_seq 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
snd                    62218  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
r592                   17808  0 
memstick               15857  1 r592 
soundcore              14635  1 snd 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm 
i2c_nforce2            12906  0 
wmi                    18744  1 hp_wmi 
video                  19115  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp 
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci 
crc_itu_t              12627  1 firewire_core 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci 
pata_amd               13750  0 
forcedeth              58096  0 
jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$

---

### Post by Hadaka on 2013-07-01
Hi, looks like you have no wifi driver loaded...
please do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
post back any errors or problems.
thanks.

---

### Post by Janno2 on 2013-07-01
> **Hadaka said:**
> Hi, looks like you have no wifi driver loaded...
please do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
post back any errors or problems.
thanks.

No success. Error [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu2

WIth sudo modprobe b43 I get the option "wireless enabled"
Looking in system.network the wireless option is there, but tells me firmware is missing.

Going to bed now....

---

### Post by Hadaka on 2013-07-01
ok, please do from a wired connection..
```
sudo apt-get update
sudo apt-get upgrade
```
boot,
then do..
```
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modporbe -r b43
sudo modprobe b43
```
thanks.

---

### Post by Janno2 on 2013-07-02
> **Hadaka said:**
> ok, please do from a wired connection..
```
sudo apt-get update
sudo apt-get upgrade
```
boot,
then do..
```
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modporbe -r b43
sudo modprobe b43
```
thanks.

It's getting worse!

All went well until "sudo modprobe - r b43"

This was the result:

jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$ sudo modprobe -f b43 
WARNING: Error inserting bcma (/lib/modules/3.2.0-48-generic-pae/kernel/drivers/bcma/bcma.ko): Invalid module format 
WARNING: Error inserting cfg80211 (/lib/modules/3.2.0-48-generic-pae/kernel/net/wireless/cfg80211.ko): Invalid module format 
WARNING: Error inserting mac80211 (/lib/modules/3.2.0-48-generic-pae/kernel/net/mac80211/mac80211.ko): Invalid module format 
FATAL: Error inserting b43 (/lib/modules/3.2.0-48-generic-pae/kernel/drivers/net/wireless/b43/b43.ko): Invalid module format 
jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$

---

### Post by Janno2 on 2013-07-02
OK, I tried:

sudo apt-get update
sudo apt-get upgrade

sudo apt-get install --reinstall linux-firmware-nonfree

sudo modprob b43

Ansd the wireless connection was there!

However, wen rebooting it was gone again.

And "sudo modprobe b43" does not bring back the wireless connection.

---

### Post by Hadaka on 2013-07-02
ok, let;s look at some stuff, see what is going on..
please post the output of..
```
lspci -n | grep 0280
cat /etc/modules
cat /etc/network/interfaces
lsmod
```
thanks.

---

### Post by Janno2 on 2013-07-02
> **Hadaka said:**
> ok, let;s look at some stuff, see what is going on..
please post the output of..
```
lspci -n | grep 0280
cat /etc/modules
cat /etc/network/interfaces
lsmod
```
thanks.

lspci -n | grep 0280:
03:00.0 0280: 14e4:4312 (rev 02)

cat /etc/modules:
(without the comment)
lp

cat /etc/network/interfaces
auto lo
tface to inet loopback

---

### Post by Hadaka on 2013-07-02
Thanks,you forgot the lsmod
please post..
```
lsmod
sudo modprobe -r b43
sudo modprobe -v b43
```
and..
```
dmesg | egrep 'wl|b43'
nm-tool
```
thanks.

---

### Post by Hadaka on 2013-07-02
AH HA !! i just noticed your /etc/network/interfaces says..
```
tface to inet loopback
```
it shouod be "i"face...not "t" face
please do..
```
sudo gedit /etc/network/interfaces
```
replace tface.....with...iface
```
auto lo
iface lo inet loopback
```
save and close gedit.
boot
thanks.

---

### Post by Janno2 on 2013-07-02
> **Hadaka said:**
> AH HA !! i just noticed your /etc/network/interfaces says..
```
tface to inet loopback
```
it shouod be "i"face...not "t" face
please do..
```
sudo gedit /etc/network/interfaces
```
replace tface.....with...iface
```
auto lo
iface lo inet loopback
```
save and close gedit.
boot
thanks.

Type error, sorry!

Sudo gedit /etc/network/interfaces makes a gedit window popping up which says:
auto lo
iface lo inet loopback

saved, and closed gedit
booted

---

### Post by Janno2 on 2013-07-02
Sorry, will be away for a couple of hours.
But get back to you!

---

### Post by Janno2 on 2013-07-02
> **Janno2 said:**
> Sorry, will be away for a couple of hours.
But get back to you!

Back again. Here's what you asked for:

jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat 
usb_storage            39646  0 
vesafb                 13516  1 
joydev                 17393  0 
nvidia              10286823  43 
hp_wmi                 13652  0 
snd_hda_codec_conexant    52521  1 
sparse_keymap          13658  1 hp_wmi 
bnep                   17830  2 
parport_pc             32114  0 
rfcomm                 38139  0 
bluetooth             158479  10 bnep,rfcomm 
ppdev                  12849  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event 
psmouse                86520  0 
k8temp                 12905  0 
r852                   17901  0 
sm_common              16772  1 r852 
nand                   49667  2 r852,sm_common 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
r592                   17808  0 
memstick               15857  1 r592 
nand_ids                8547  1 nand 
mtd                    35584  2 sm_common,nand 
nand_bch               13003  1 nand 
bch                    21784  1 nand_bch 
nand_ecc               13105  1 nand 
snd                    62218  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              14635  1 snd 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo 
usbhid                 41937  0 
hid                    77428  1 usbhid 
wmi                    18744  1 hp_wmi 
i2c_nforce2            12906  0 
video                  19115  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp 
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci 
crc_itu_t              12627  1 firewire_core 
pata_amd               13750  0 
forcedeth              58096  0 
jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$ sudo modprobe -r b43 
[sudo] password for jan: 
jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$ sudo modprobe -v b43 
insmod /lib/modules/3.2.0-48-generic-pae/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.2.0-48-generic-pae/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.2.0-48-generic-pae/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-48-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-48-generic-pae/kernel/drivers/net/wireless/b43/b43.ko 
jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$ dmesg | egrep 'wl|b43' 
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv9500 Notebook PC    /30DA, BIOS F.32     03/03/2009 
[ 6669.790084] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, low) -> IRQ 16 
[ 6669.790105] b43-pci-bridge 0000:03:00.0: setting latency timer to 64 
[ 6670.197278] b43-phy0: Broadcom 4311 WLAN found (core revision 13) 
[ 6670.355195] Registered led device: b43-phy0::tx 
[ 6670.355283] Registered led device: b43-phy0::rx 
[ 6670.355381] Registered led device: b43-phy0::radio 
[ 6670.652071] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07) 
[ 6670.744965] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 6670.746246] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 6674.180522] wlan0: authenticate with e8:40:f2:7d:36:1d (try 1) 
[ 6674.184601] wlan0: authenticated 
[ 6674.185380] wlan0: associate with e8:40:f2:7d:36:1d (try 1) 
[ 6674.187832] wlan0: RX AssocResp from e8:40:f2:7d:36:1d (capab=0x411 status=0 aid=1) 
[ 6674.187841] wlan0: associated 
[ 6674.189383] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 6684.816028] wlan0: no IPv6 routers present 
jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$ nm-tool 

NetworkManager Tool 

State: connected (global) 

- Device: wlan0  [UPC909089] --------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            b43 
  State:             connected 
  Default:           yes 
  HW Address:        00:1A:73:88:C6:6E 

  Capabilities: 
    Speed:           18 Mb/s 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points (* = current AP) 
    *UPC909089:      Infra, E8:40:F2:7D:36:1D, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA2 
    UPC796211:       Infra, 38:60:77:AD:C8:12, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2 
    UPC244030540:    Infra, 5C:A3:9D:C9:E7:68, Freq 2472 MHz, Rate 54 Mb/s, Strength 52 WPA2 
    ZyxelPuda:       Infra, CC:5D:4E:1C:F8:6C, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2 
    karl en lenny:   Infra, 5C:A3:9D:DB:9D:F8, Freq 2467 MHz, Rate 54 Mb/s, Strength 42 WPA2 
    Jay:             Infra, 00:1B:FC:39:48:D7, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WEP 

  IPv4 Settings: 
    Address:         192.168.1.42 
    Prefix:          24 (255.255.255.0) 
    Gateway:         192.168.1.1 

    DNS:             62.179.104.196 
    DNS:             213.46.228.196 


- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            forcedeth 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1B:24:7F:D4:5A 

  Capabilities: 
    Carrier Detect:  yes 

  Wired Properties 
    Carrier:         off 


jan@jan-HP-Pavilion-dv9500-Notebook-PC:~$ 

By the way: "modprobe b43" does make the wireless network work.
But after reboot it does not come back.:(

---

### Post by Janno2 on 2013-07-02
Looks like I've found a solution in this thread:

[http://ubuntuforums.org/showthread.php?t=1973756](http://ubuntuforums.org/showthread.php?t=1973756)

I used sudo gedit /etc/modules
added b43 
saved
reboot

Thank you for your help, it learned me that the b43 module was not starting at boot, so I looked in ubuntuforums for modprobe b43, and
stumbled upon this thread.

Happy now.:D

Bye

Jan:D

---

### Post by Hadaka on 2013-07-02
Fantastic !! funny thing is...thats exactly what i was going to
have you do once the thing actually went live. I'm surprised
the modprobe command didnt fire it up. Anyway....GREAT !!
please mark this thread solved.
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
be sure to edit the FIRST post of your thread to mark solved.
thanks.

---

