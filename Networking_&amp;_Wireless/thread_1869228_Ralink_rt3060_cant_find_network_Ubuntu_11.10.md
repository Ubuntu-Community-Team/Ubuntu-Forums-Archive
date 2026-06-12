---
title: "Ralink rt3060 cant find network Ubuntu 11.10"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by Reded on 2011-10-25
Hey all, I bought a new wireless card recently, and it doesn't seem to find any networks in Network manager. When I try to 'connect to a hidden network' it just never gets anywhere.

I've put all the commands in the sticky into terminal, this is what they all returned:

lsmod
Module                  Size  Used by
vesafb                 13809  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
ppdev                  17113  0 
fglrx                2929009  101 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  4 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
crc_ccitt              12667  1 rt2800lib
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  5 rt2800pci,rt2800lib,rt73usb,rt2x00usb,rt2x00pci
mac80211              310872  4 rt2800lib,rt2x00usb,rt2x00pci,rt2x00lib
snd_timer              29991  2 snd_seq,snd_pcm
edac_core              53746  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 13057  0 
cfg80211              199587  2 rt2x00lib,mac80211
edac_mce_amd           23709  0 
eeprom_93cx6           12725  1 rt2800pci
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_timer,snd_seq_device
soundcore              12680  1 snd
parport_pc             36962  1 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
binfmt_misc            17540  1 
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
forcedeth              67563  0 
sata_nv                32305  0 
pata_amd               14121  3

Sorry I have no idea which part of this you're after...

lspci
01:07.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R

iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

ifconfig
wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c7:42:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo lshw -C network
 *-network               
       description: Wireless interface
       product: RT3060 Wireless 802.11n 1T/1R
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: wlan0
       version: 00
       serial: c8:3a:35:c7:42:a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-12-generic firmware=0.34 latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fa000000-fa00ffff

sudo iwlist scan
wlan0     No scan results

dmesg | grep rt2
[   16.327441] rt2800pci 0000:01:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   16.376389] Registered led device: rt2800pci-phy1::radio
[   16.376407] Registered led device: rt2800pci-phy1::assoc
[   16.376427] Registered led device: rt2800pci-phy1::quality
[   17.448313] phy1 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware

rfkill list
0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

ubuntu 11.10

3.0.0-12-generic x86_64

I noticed where it says driver=rt2800pci after the lshw command doesn't seem to match what the Network Manager says, not sure if that could be the issue...

I'm a serious newbie when it comes to Ubuntu, not been running it too long, so please feel free to dumb down anything answers to any extent you feel necessary!

Any help is appreciated.

---

### Post by praseodym on 2011-10-25
Please show:

```
lsmod
dmesg | grep rt2
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by Reded on 2011-10-27
Already posted iwconfig + sudo iwlist scan..
 
I'll post the others when I get back on Linux, mostly posting this to make sure the thread doesn't die - I'm on Windows for a couple days while I fix something up on there, thanks!

---

### Post by Reded on 2011-10-28
Alright, been away for a bit had to clean-install Ubuntu, don't ask..

Editting my first post to contain all the info now.

---

### Post by Reded on 2011-10-28
All editted. Hope this gets sorted at some point! Thanks.

---

### Post by praseodym on 2011-10-28
Which device ID does the card have?

```
lspci -nnk | grep -iA2 net
```

please. If it is "1814:3060" there is an installation procedure here (copy/paste it line by line):

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
tar xzvf angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make
sudo make install
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt3562sta
```

---

### Post by Reded on 2011-10-28
Device is working fine, thanks a bunch!

I got drivers with the card, but the installation instructions didn't seem to be for Ubuntu (Or at least not for 11.10) And that just confused me further, your list of commands worked perfectly, thanks again :):):):)

EDIT:

Now I'm getting that old problem where it cuts me off when I try to download anything big. I've tried the iwconfig power off command, doesn't seem to fix it!

---

### Post by praseodym on 2011-10-29
Show:

```
route -n
ifconfig -a
iwconfig
sudo iwlist scan
cat /etc/resolv.conf
lsmod
```

---

### Post by Reded on 2011-10-29
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ra0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ra0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 ra0

ifconfig -a
Link encap:Ethernet  HWaddr c8:3a:35:c7:42:a0  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3a:35ff:fec7:42a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3028784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2711279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:401239699 (401.2 MB)  TX bytes:397528679 (397.5 MB)
          Interrupt:17 

iwconfig
ra0       Ralink STA  ESSID:"ZyXEL_8376vik"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:02:CF:7F:60:00   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-48 dBm  Noise level:-75 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist scan
Scan completed :
          Cell 01 - Address: 00:02:CF:7F:60:00
                    Protocol:802.11b/g
                    ESSID:"ZyXEL_8376vik"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-49 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1

lsmod
Module                  Size  Used by
snd_hrtimer            12744  1 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  8 rfcomm,bnep
vesafb                 13809  1 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  7 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
fglrx                2929009  200 
edac_core              53746  0 
edac_mce_amd           23709  0 
snd_timer              29991  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt3562sta             990799  1 
ppdev                  17113  0 
parport_pc             36962  1 
snd                    68266  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 13057  0 
i2c_nforce2            13058  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
forcedeth              67563  0 
sata_nv                32305  0 
pata_amd               14121  2 

Like I said the Wireless Card is working now - it just disconnects whenever I download something big (Similar to the power management issue I always get when I fresh-install Ubuntu - I've tried the usual fix for that, apparently ra0 doesn't support that operation!

---

### Post by praseodym on 2011-10-30
You can change the power management in a file. Please show:

```
cat /usr/lib/pm-utils/power.d/wireless
```

---

### Post by Reded on 2011-10-30
cat /usr/lib/pm-utils/power.d/wireless

#!/bin/sh

. "${PM_FUNCTIONS}"

# See if we have the usual wireless tools.
# Do not just fail because not all cards require these.
which iwpriv >/dev/null 2>&1 && have_iwpriv="true"
which iwconfig >/dev/null 2>&1 && have_iwconfig="true"

# If only all the drivers did The Right Thing with iwconfig power.
# Too bad they do not.

get_wireless_params() {
    # $1 = interface 
    # $2 = on or off
    unset iwpriv iwconfig iwlevel
    
    # Don't do anything if we cannot find a driver for this iface.
    [ -L "/sys/class/net/$1/device/driver" ] || return 1
    # Skip if not a wireless card.
    [ -d "/sys/class/net/$1/wireless" ] || return 1
    # Also don't do anything if the device is disabled
    [ "$(cat /sys/class/net/$1/device/enable)" = "1" ] || return 1
    driver="$(readlink "/sys/class/net/$1/device/driver")"
    driver=${driver##*/}
    case $driver in
        ipw2100) iwpriv_ac="set_power 0"
            iwpriv_batt="set_power 5"
            iwconfig_ac="power on"
            iwconfig_batt="power on";;
        ipw3945)
            iwpriv_ac="set_power 6"
            iwpriv_batt="set_power 7";;
        iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 iwlevel_batt=3
              else
                 iwconfig_ac="power off"
                 iwconfig_batt="power on"
              fi;;
        *) iwconfig_ac="power off"
           iwconfig_batt="power on";;
    esac
    case $2 in
        off) [ "$iwpriv_ac" ] && iwpriv="$iwpriv_ac"
            [ "$iwconfig_ac" ] && iwconfig="$iwconfig_ac"
            [ "$iwlevel_ac" ] && iwlevel="$iwlevel_ac";;
        on) [ "$iwpriv_batt" ] && iwpriv="$iwpriv_batt"
            [ "$iwconfig_batt" ] && iwconfig="$iwconfig_batt"
            [ "$iwlevel_batt" ] && iwlevel="$iwlevel_batt";;
    esac
    return 0
}

wireless_powersave() {
    for dev in /sys/class/net/*; do
        get_wireless_params "${dev##*/}" "$1" || continue
    ret=0
    printf "Turning powersave for %s %s..." "${dev##*/}" "$1"
    if [ "$have_iwconfig" = true -a "$iwconfig" ]; then
        iwconfig "${dev##*/}" $iwconfig || ret=1
    fi
        if [ "$have_iwpriv" = true -a "$iwpriv" ]; then
        iwpriv "${dev##*/}" $iwpriv || ret=1
    fi
        if [ "$iwlevel" ]; then
        echo "$iwlevel" > "$dev/device/power_level" || ret=1
    fi
    [ "$ret" -eq 0 ] && echo Done. || echo Failed.
    done
}

case $1 in
    true) wireless_powersave on ;;
    false) wireless_powersave off ;;
    *) exit $NA ;;
esac

---

### Post by praseodym on 2011-10-30
Change this part:
```
case $driver in
ipw2100) iwpriv_ac="set_power 0"
iwpriv_batt="set_power 5"
iwconfig_ac="power on"
iwconfig_batt="power on";;
ipw3945)
iwpriv_ac="set_power 6"
iwpriv_batt="set_power 7";;
iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
iwlevel_ac=0
iwlevel_batt=3
else
iwconfig_ac="power off"
iwconfig_batt="power on"
fi;;
*) iwconfig_ac="power off"
iwconfig_batt="power on";;
esac
```
into
```
case $driver in
        ipw2100) iwpriv_ac="set_power 0"
            iwpriv_batt="set_power [COLOR="Red"]0[/COLOR]"
            iwconfig_ac="power on"
            iwconfig_batt="power on";;
        ipw3945)
            iwpriv_ac="set_power 6"
            iwpriv_batt="set_power [COLOR="Red"]6[/COLOR]";;
        iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 iwlevel_batt=[COLOR="Red"]0[/COLOR]
              else
                 iwconfig_ac="power off"
                 iwconfig_batt="power [COLOR="Red"]off[/COLOR]"
              fi;;
        *) iwconfig_ac="power off"
           iwconfig_batt="power [COLOR="Red"]off[/COLOR]";;
    esac
```
Proof read twice, save, close, and reboot.

---

### Post by Reded on 2011-10-30
Successfully downloaded an 80MB file without being thrown off, solved for the 2nd time!

Thanks a lot for sticking to the thread and solving both issues, very much appreciated. I'll be sure to pester this forum next time something happens :D Thanks again.

---

### Post by Reded on 2011-10-30
Alright it doesn't seem to be fixed. Now it seems whenever I turn my cam on or screenshare on Skype, the internet cuts off. Skype issue or Wireless issue?

---

### Post by praseodym on 2011-10-31
Please show after that event:

```
dmesg >> dmesg.txt
```

and upload the file

---

### Post by Reded on 2011-10-31
I typed that command and nothing happened. Is there anything else I should do after typing it?

---

### Post by praseodym on 2011-10-31
Now there should be a .txt-file in your /home-folder named dmesg.txt, upload it or if its too big use some pastebin service

---

### Post by Reded on 2011-10-31
[http://pastebin.com/FGe0Ybwt](http://pastebin.com/FGe0Ybwt)

File was too big to attach here, pastebin'ed as asked.

---

### Post by praseodym on 2011-10-31
Which channel do you want to connect to? Which country do you live in? Please show

```
iwlist chan
```
Deactivate (if active) roaming in the NetworkManager (or Wicd) and choose a channel from 1-6 fixed in the router. Additionally:
```
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```
It wants to connect via roaming and falls back to channel 11 which doesnt work.

---

### Post by Reded on 2011-10-31
ra0       13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.462 GHz (Channel 11)

Not sure which channel I want to connect to - Just whichever one works I guess... 

cat /etc/Wireless/RT2860STA/RT2860STA.dat
#The word of "Default" must not be removed
Default
CountryRegion=1
CountryRegionABand=1
CountryCode=DE
ChannelGeography=1
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=5
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
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
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

I live in England. You said channel 11 doesn't work but iwlist said that's my current, not sure if that holds any relevance to a fix. My internet is generally dodgy anyway, it just seemed odd how it seemed to disconnect every 10 minutes after A) Starting a large download, or B) Video Chatting on Skype.

---

### Post by praseodym on 2011-10-31
```
gksu gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```
Change at least:

```
#Default                                                                 
CountryRegion=1                                                          
CountryRegionABand=1                                                     
CountryCode=[COLOR="Red"]UK[/COLOR]                                                           
ChannelGeography=1                                                       
SSID=[COLOR="Red"]youressid[/COLOR]                                                             
NetworkType=Infra                                                        
WirelessMode=5                                                           
Channel=[COLOR="Red"]yourchannel[/COLOR]                                                             
AuthMode=WPAPSK
EncrypType=AES
WPAPSK=[COLOR="Red"]your key[/COLOR]
HT_BW=1
```
You may want to search for the other settings for England here. These changes are neccessary for Draft-N. The other settings were for Germany

---

### Post by Reded on 2011-10-31
I noticed some things in that seem to be with WPA key, my router is WEP. It's by choice, I sometimes use it to go online with an old nintendo DS. Will that effect it at all? And will using those German settings effect anything? If not what exactly is it I'm looking for online for English settings? Sorry I'm a complete novice at this, I need this dumbed down a bit :(

---

### Post by praseodym on 2011-10-31
These settings (obviously still) need WPA2-AES encryption, key, ESSID, etc. to work flawlessly with Draft-N. You can add the Nintendo via Internet Connection Sharing (ICS) to your wireless, which only works with WEP encryption in Linux/Ubuntu (still, most of the time) because of the drivers/firmware. Whatever the NetworkManager tells you, it only works with WEP!

---

### Post by praseodym on 2011-10-31
P.S.: This file wants your wireless to connect to "Channel 0" ("Channel Zero" is a nice belgian metal band btw ;-) ), but there is no channel in your router.

---

### Post by Reded on 2011-10-31
There's three computers in the house, so changing my router back to WPA will have to wait till tomorrow - Don't want the parents to be wondering why the Passkey isn't working!

I'll get back as soon as that's done. And I checked out Channel Zero, liked the guitar riffs didn't like the vocals sadly :P

---

### Post by Martin A on 2011-11-02
Same problem, same card, fix worked for me too.

Thanks praseodym for keeping us wifi :guitar:

---

### Post by VeaRN on 2011-11-03
Hi i'm new here and to ubuntu. So do i have to do everything from page 1? or theres a simple way?

---

### Post by praseodym on 2011-11-03
@VeaRN: Do it like this:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
tar xzvf angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
gedit RT2860STA.dat
```
Change your country code, SSID, etc. before compiling, save, close, and:
```
sudo make
sudo make install
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt3562sta
```
Check with "iwconfig" if the power management is "on"

---

### Post by swarsron on 2011-11-03
Hi praseodym,

thank you very much for your help. I was quite annoyed that my wlan wouldn't work with my new ubuntu installation ...

One problem left: I have many log entries like
Nov  3 13:33:12 johannes-desktop kernel: [159568.504028] QuickDRS: TxTotalCnt <= 15, train back to original rate 
Nov  3 13:33:15 johannes-desktop kernel: [159571.907120]    Tx Power, BBP R49=10, TssiRef=10, TxAgcStep=1, step = +0
Nov  3 13:33:19 johannes-desktop kernel: [159575.914099]    Tx Power, BBP R49=10, TssiRef=10, TxAgcStep=1, step = +0
Nov  3 13:33:23 johannes-desktop kernel: [159579.922109]    Tx Power, BBP R49=10, TssiRef=10, TxAgcStep=1, step = +0
Nov  3 13:33:27 johannes-desktop kernel: [159583.931105]    Tx Power, BBP R49=10, TssiRef=10, TxAgcStep=1, step = +0
<snip many more lines>

The transmission rate drops to 58.5 mbit, then speeds up to 65 mbit again. I tried to lower it but no combination of iwconfig ra0 rate foobar seems to work. I don't need the full speed so i would be happy to sacrifice a bit to avoid those messages. 

# iwconfig ra0
ra0       Ralink STA  ESSID:"asdf"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.452 GHz  Access Point: asdf   
          Bit Rate=65 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:asdf
          Link Quality=80/100  Signal level:-59 dBm  Noise level:-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

the messages only occur during large file transfers, browsing doesn't trigger it. Any ideas?

Thank you

---

### Post by praseodym on 2011-11-03
Try

```
sudo iwconfig ra0 rate auto
```

---

### Post by swarsron on 2011-11-03
Doesn't help. This is the syslog part after 
iwconfig ra0 rate auto

[http://dailybs.de/wlan.log](http://dailybs.de/wlan.log)

---

### Post by praseodym on 2011-11-04
More infos, please:

```
iwconfig
sudo iwlist scan
lsmod
cat /etc/resolv.conf
cat /etc/network/interfaces
route -n
ifconfig -a
dmesg | egrep 'rt2|rt3'
```

---

### Post by swarsron on 2011-11-04
i'm sorry, here it is:
[http://dailybs.de/out](http://dailybs.de/out)
(little bit too long for this forum)

---

### Post by praseodym on 2011-11-04
Do you use the network-manager? If yes, remove anything but

```
auto lo
iface lo inet loopback
```

from the /etc/network/interfces. Change the encryption mode to pure WPA2-AES instead of mixed. Maybe changing the channel to 1 or 2, around 8 is a lot of traffic.

---

### Post by swarsron on 2011-11-04
no i don't use network manager. I changed the encryption and the channel to no avail

ra0       Scan completed :
          Cell 01 - Address: C0:25:06:32:82:D0
                    Protocol:802.11b/g/n
                    ESSID:"JonnyDomi"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:91/100  Signal level:-54 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD6A0050F204104A0001101044000102103B0001001047001042605727F92BBA44D1DC1FEDAFF764201021000341564D10230009465249545A21426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103

But i discovered a strange behavior:
# while /bin/true; do iwlist scan 2> /dev/null | grep -i jonnydomi -A 3 | grep Quality; iwconfig ra0 | grep Quality; done

                    Quality:5/100  Signal level:-88 dBm  Noise level:-83 dBm
          Link Quality=100/100  Signal level:-59 dBm  Noise level:-83 dBm
                    Quality:0/100  Signal level:-96 dBm  Noise level:-102 dBm
          Link Quality=100/100  Signal level:-67 dBm  Noise level:-91 dBm
                    Quality:86/100  Signal level:-56 dBm  Noise level:-92 dBm
          Link Quality=100/100  Signal level:-67 dBm  Noise level:-91 dBm
                    Quality:91/100  Signal level:-54 dBm  Noise level:-92 dBm
          Link Quality=100/100  Signal level:-64 dBm  Noise level:-88 dBm
                    Quality:0/100  Signal level:-90 dBm  Noise level:-85 dBm
          Link Quality=100/100  Signal level:-69 dBm  Noise level:-93 dBm
                    Quality:10/100  Signal level:-86 dBm  Noise level:-81 dBm
          Link Quality=100/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Quality:10/100  Signal level:-86 dBm  Noise level:-81 dBm
          Link Quality=100/100  Signal level:-69 dBm  Noise level:-93 dBm
                    Quality:86/100  Signal level:-56 dBm  Noise level:-92 dBm
          Link Quality=100/100  Signal level:-69 dBm  Noise level:-93 dBm
                    Quality:5/100  Signal level:-88 dBm  Noise level:-83 dBm
          Link Quality=100/100  Signal level:-81 dBm  Noise level:-105 dBm
                    Quality:96/100  Signal level:-52 dBm  Noise level:-92 dBm
          Link Quality=100/100  Signal level:-79 dBm  Noise level:-103 dBm
                    Quality:10/100  Signal level:-86 dBm  Noise level:-81 dBm
          Link Quality=100/100  Signal level:-79 dBm  Noise level:-103 dBm
                    Quality:10/100  Signal level:-86 dBm  Noise level:-81 dBm
          Link Quality=100/100  Signal level:-77 dBm  Noise level:-101 dBm
                    Quality:10/100  Signal level:-86 dBm  Noise level:-81 dBm
          Link Quality=100/100  Signal level:-76 dBm  Noise level:-100 dBm
                    Quality:5/100  Signal level:-88 dBm  Noise level:-83 dBm
          Link Quality=100/100  Signal level:-73 dBm  Noise level:-97 dBm
                    Quality:0/100  Signal level:-90 dBm  Noise level:-85 dBm
          Link Quality=100/100  Signal level:-75 dBm  Noise level:-99 dBm
                    Quality:10/100  Signal level:-86 dBm  Noise level:-81 dBm
          Link Quality=100/100  Signal level:-81 dBm  Noise level:-105 dBm
                    Quality:10/100  Signal level:-86 dBm  Noise level:-81 dBm
          Link Quality=100/100  Signal level:-79 dBm  Noise level:-103 dBm

Looks like i have a problem with background noise ...

---

### Post by praseodym on 2011-11-04
Is it a hidden network? Wicd is in use?

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo apt-get remove --purge network-manager network-manager-gnome
sudo service wicd restart
```
Choose **ra0** as interface and **wext** as driver.

---

### Post by swarsron on 2011-11-04
no hidden network. wicd wasn't in use, is now. 
My logs are now flooded with

Nov  4 16:11:08 burner kernel: [ 3477.535135]    Tx Power, BBP R49=11, TssiRef=10, TxAgcStep=1, step = +0
Nov  4 16:11:09 burner kernel: [ 3478.986553] ==>rt_ioctl_giwfreq  2
Nov  4 16:11:09 burner kernel: [ 3478.986582] ===>rt_ioctl_giwencode 0
Nov  4 16:11:09 burner kernel: [ 3478.986589] MediaState is connected
Nov  4 16:11:09 burner kernel: [ 3478.986595] ==>rt_ioctl_giwmode(mode=2)
Nov  4 16:11:09 burner kernel: [ 3478.986602] ===>rt_ioctl_giwrange
Nov  4 16:11:09 burner kernel: [ 3478.986619] rt28xx_get_wireless_stats --->
Nov  4 16:11:09 burner kernel: [ 3478.986624] <--- rt28xx_get_wireless_stats
Nov  4 16:11:11 burner kernel: [ 3481.031770] ==>rt_ioctl_giwfreq  2
Nov  4 16:11:11 burner kernel: [ 3481.031799] ===>rt_ioctl_giwencode 0
Nov  4 16:11:11 burner kernel: [ 3481.031806] MediaState is connected
Nov  4 16:11:11 burner kernel: [ 3481.031811] ==>rt_ioctl_giwmode(mode=2)
Nov  4 16:11:11 burner kernel: [ 3481.031819] ===>rt_ioctl_giwrange
Nov  4 16:11:11 burner kernel: [ 3481.031836] rt28xx_get_wireless_stats --->
Nov  4 16:11:11 burner kernel: [ 3481.031841] <--- rt28xx_get_wireless_stats
Nov  4 16:11:12 burner kernel: [ 3481.542102]    Tx Power, BBP R49=11, TssiRef=10, TxAgcStep=1, step = +0
Nov  4 16:11:14 burner kernel: [ 3483.490450] ==>rt_ioctl_giwfreq  2
Nov  4 16:11:14 burner kernel: [ 3483.490480] ===>rt_ioctl_giwencode 0
Nov  4 16:11:14 burner kernel: [ 3483.490487] MediaState is connected
Nov  4 16:11:14 burner kernel: [ 3483.490493] ==>rt_ioctl_giwmode(mode=2)
Nov  4 16:11:14 burner kernel: [ 3483.490501] ===>rt_ioctl_giwrange
Nov  4 16:11:14 burner kernel: [ 3483.490519] rt28xx_get_wireless_stats --->
Nov  4 16:11:14 burner kernel: [ 3483.490524] <--- rt28xx_get_wireless_stats
Nov  4 16:11:16 burner kernel: [ 3485.497874] ==>rt_ioctl_giwfreq  2
Nov  4 16:11:16 burner kernel: [ 3485.497905] ===>rt_ioctl_giwencode 0
Nov  4 16:11:16 burner kernel: [ 3485.497913] MediaState is connected
Nov  4 16:11:16 burner kernel: [ 3485.497919] ==>rt_ioctl_giwmode(mode=2)
Nov  4 16:11:16 burner kernel: [ 3485.497926] ===>rt_ioctl_giwrange
Nov  4 16:11:16 burner kernel: [ 3485.497943] rt28xx_get_wireless_stats --->
Nov  4 16:11:16 burner kernel: [ 3485.497948] <--- rt28xx_get_wireless_stats

dailybs.de/out has current information of iwconfig etc.

---

### Post by VictorMature on 2011-11-10
This solution worked great for me.  I had the same card.

What I am wondering is, how persistent is this installation?  I'm not familiar enough with Linux and the modular kernel concept to understand what I just did.

The situation is, I am building this desktop for a friend who probably won't be able to reinstall this driver.  So, I'm wondering if this driver install will be persistent through future upgrades to different kernels?

---

### Post by swarsron on 2011-11-11
it's not persistent since a new kernel will require a recompilation of the module. You could write him a script which repeats the compilation and hope that it does work for a while.

---

### Post by praseodym on 2011-11-11
You always need to recompile with a new kernel

---

### Post by VictorMature on 2011-11-11
Thanks for the quick response.  It really saved me since I am delivering this tomorrow.  He would have really been stuck with no local driver package and no network to download it.

I put the driver package on a hidden directory in his home folder, then put a script based on your code in his home folder to run after an update.

It seems to work.  Anyway I run it, and I lose the interface then it comes back up.


> sudo apt-get install --reinstall linux-headers-generic build-essential dkms
cd /home/jim/.ralink/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make
sudo make install
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt3562sta

---

### Post by luissil on 2012-02-17
> **praseodym said:**
> Which device ID does the card have?

```
lspci -nnk | grep -iA2 net
```please. If it is "1814:3060" there is an installation procedure here (copy/paste it line by line):

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
tar xzvf angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make
sudo make install
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt3562sta
```


Ok, there's a problem:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
--2012-02-17 22:47:49--  http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-17 22:47:51 ERROR 404: Not Found.

```Where are the files??

---

### Post by praseodym on 2012-02-18
Try this one:

```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/22/31/2739482-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/22/31/2739482-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz)
```

---

### Post by luissil on 2012-02-23
> **praseodym said:**
> Try this one:

```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/22/31/2739482-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/22/31/2739482-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz)
```


Well I found the files here in my pc and did all the steps... now my problem is that it goes offline for no reason once and again, sometimes reconnects but other times not :-(

---

### Post by praseodym on 2012-02-24
Change the encryption mode to pure WPA2-AES if possible

---

### Post by luissil on 2012-02-26
> **praseodym said:**
> Change the encryption mode to pure WPA2-AES if possible


Mmm... the security options available are: 

WEP (Which I have)
WPA-PSK
WPA2-PSK
WPA-PSK MIXED

which one should I have?

---

### Post by praseodym on 2012-02-26
WPA2-PSK

Use "WPA & WPA2 Personal" for this in the NM-applet.

---

### Post by luissil on 2012-03-03
> **luissil said:**
> Mmm... the security options available are: 

WEP (Which I have)
WPA-PSK
WPA2-PSK
WPA-PSK MIXED

which one should I have?

> **praseodym said:**
> WPA2-PSK

Use "WPA & WPA2 Personal" for this in the NM-applet.


I think there was a problem with the signal strength, because I moved the router closer to my pc and now works fine!

Thank u very much!

---

### Post by luissil on 2012-05-01
Sorry, maybe off-topic but, after installing the latest updates, I tried to re-activate my wireless connection and got this error 127:

```
luis@luis-casa:~/Tarjeta de red/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared$ sudo apt-get install --reinstall linux-headers-generic build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwrap0:i386 libsamplerate0:i386 libjack-jackd2-0:i386 libnspr4-0d:i386 libjson0:i386 libspeexdsp1:i386 libasound2:i386
  libflac8:i386 libvorbisenc2:i386 libasyncns0:i386 libpulse0:i386 libvorbis0a:i386 libnss3-1d:i386 libsndfile1:i386
  libasound2-plugins:i386 libogg0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/80.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 247558 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu1 (using .../build-essential_11.5ubuntu1_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.2-1ubuntu4 (using .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-generic 3.0.0.19.23 (using .../linux-headers-generic_3.0.0.19.23_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Processing triggers for man-db ...
Setting up build-essential (11.5ubuntu1) ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up linux-headers-generic (3.0.0.19.23) ...

``````

luis@luis-casa:~/Tarjeta de red/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared$ sudo make
make -C tools
make[1]: Entering directory `/home/luis/Tarjeta de red/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/luis/Tarjeta de red/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared/tools'
/home/luis/Tarjeta de red/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared/tools/bin2h
make: /home/luis/Tarjeta: Command not found
make: *** [build_tools] Error 127

```

:confused:

btw, I have internet by tethering my phone...

please help!

---

### Post by praseodym on 2012-05-01
Try the native driver:

```
sudo modprobe rt2800pci
```
Check:

```
iwconfig
sudo iwlist scan
grep rt2 /etc/modprobe.d/*
lsmod
dmesg | grep rt2
```

---

### Post by luissil on 2012-05-01
> **praseodym said:**
> Try the native driver:

```
sudo modprobe rt2800pci
```Check:

```
iwconfig
sudo iwlist scan
grep rt2 /etc/modprobe.d/*
lsmod
dmesg | grep rt2
```

Doesn't solve the problem either... :-(

```
luis@luis-casa:~$ sudo modprobe rt2800pci
[sudo] password for luis: 

``````
luis@luis-casa:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
``````
luis@luis-casa:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

wlan0     No scan results
``````
luis@luis-casa:~$ grep rt2 /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:blacklist rt2800pci
/etc/modprobe.d/blacklist.conf:blacklist rt2x00lib
/etc/modprobe.d/blacklist.conf:blacklist rt2x00pci
/etc/modprobe.d/blacklist.conf:blacklist rt2800lib
/etc/modprobe.d/blacklist-rt2800pci.conf:blacklist rt2800pci
``````
luis@luis-casa:~$ lsmod
Module                  Size  Used by
arc4                   12529  2 
rt2800pci              18715  0 
rt2800lib              54538  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              54461  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              462046  3 rt2800lib,rt2x00pci,rt2x00lib
eeprom_93cx6           12725  1 rt2800pci
rndis_wlan             37554  0 
cfg80211              199630  3 rt2x00lib,mac80211,rndis_wlan
rndis_host             13848  1 rndis_wlan
cdc_ether              13536  1 rndis_host
usbnet                 26212  3 rndis_wlan,rndis_host,cdc_ether
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166150  10 rfcomm,bnep
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13844  1 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330815  1 
snd_seq_midi           13324  0 
snd_hda_intel          33390  2 
snd_hda_codec         104968  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
lp                     17799  0 
snd_seq_midi_event     14899  1 snd_seq_midi
parport                46562  3 parport_pc,ppdev,lp
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17083  1 videodev
fglrx                3101156  54 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13791  0 
soundcore              12680  1 snd
k10temp                13166  0 
serio_raw              13166  0 
joydev                 17693  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
shpchp                 37345  0 
wmi                    19256  0 
fam15h_power           13032  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
usbhid                 47198  0 
hid                    95463  1 usbhid
crc_itu_t              12707  1 firewire_core
pata_atiixp            13164  0 
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 
xhci_hcd               82820  0
``````
luis@luis-casa:~$ dmesg | grep rt2
[  149.634285] rt2800pci 0000:04:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  149.660472] Registered led device: rt2800pci-phy0::radio
[  149.660519] Registered led device: rt2800pci-phy0::assoc
[  149.660562] Registered led device: rt2800pci-phy0::quality
```

Thank you for your help!

---

### Post by praseodym on 2012-05-01
Ok, unload it:

```
sudo modprobe -rfv rt2800pci
```

and try the other driver as "root":

```
sudo make clean
sudo su
make
make install
exit
```
Are there blanks in the path to the driver? If yes, remove them and try it the regular way again

---

### Post by luissil on 2012-05-02
> **praseodym said:**
> Ok, unload it:

```
sudo modprobe -rfv rt2800pci
```and try the other driver as "root":

```
sudo make clean
sudo su
make
make install
exit
```Are there blanks in the path to the driver? If yes, remove them and try it the regular way again


Pff! the problem was the blanks!

Now everything works! Thank you very much again!

---

### Post by refandina on 2012-06-29
Hola, esta solucion sirve para ubuntu 11.04? tengo Ranlink rt3060 en Ubuntu 11.04.

Hello, this solution is for ubuntu 11.04?  I have  Ranlink rt3060 in Ubuntu 11.04.

---

### Post by praseodym on 2012-06-29
Yes, it should work, too, in 11.04. Check after that:

> iwconfig
lsmod
sudo iwlist scan
rfkill list

---

### Post by refandina on 2012-06-29
la pc se colgo cuando ejecute: ```
sudo modprobe -v rt3562sta
```the pc is hung when running ```
sudo modprobe-v rt3562sta
``````
iwconfig  
 lo        no wireless extensions.  
 

 eth3      no wireless extensions.  
 

 wlan3     IEEE 802.11bgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
 
``````
lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17335  1  
 fat                    55505  1 vfat  
 snd_hda_codec_realtek   255820  1  
 rt3562sta             869831  0  
 snd_hda_intel          24140  2  
 snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13274  1 snd_hda_codec  
 arc4                   12473  2  
 snd_pcm                80244  2 snd_hda_intel,snd_hda_codec  
 snd_seq_midi           13132  0  
 rt2800pci              18159  0  
 rt2800lib              43824  1 rt2800pci  
 snd_rawmidi            25269  1 snd_seq_midi  
 crc_ccitt              12595  1 rt2800lib  
 rt2x00pci              13986  1 rt2800pci  
 rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci  
 mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 i915                  450944  3  
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event  
 usbhid                 41704  0  
 usblp                  17827  0  
 binfmt_misc            13213  1  
 ppdev                  12849  0  
 hid                    77084  1 usbhid  
 cfg80211              156212  2 rt2x00lib,mac80211  
 snd_timer              28659  2 snd_pcm,snd_seq  
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq  
 drm_kms_helper         40745  1 i915  
 snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 drm                   180037  4 i915,drm_kms_helper  
 eeprom_93cx6           12653  1 rt2800pci  
 parport_pc             32111  1  
 soundcore              12600  1 snd  
 i2c_algo_bit           13184  1 i915  
 snd_page_alloc         14073  2 snd_hda_intel,snd_pcm  
 video                  18951  1 i915  
 asus_atk0110           17664  0  
 lp                     13349  0  
 parport                36746  3 ppdev,parport_pc,lp  
 usb_storage            43946  1  
 uas                    17676  0  
 atl1c                  36237  0  
 
``````
sudo iwlist scan  
 [sudo] password for user:  
 lo        Interface doesn't support scanning.  
 

 eth3      Interface doesn't support scanning.  
 

 wlan3     No scan results
 

 
``````
rfkill list  
 0: phy0: Wireless LAN  
     Soft blocked: no  
     Hard blocked: no  
 
```

---

### Post by praseodym on 2012-06-30
Blacklist rt2800pci:

> echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
and reboot.

---

### Post by refandina on 2012-07-02
disculpa. pero no funciono, ahora parece que no reconoce la placa inalambrica.
sorry. but did not work, now it seems it does not recognize the wireless board.
hice esto: 
I did this:
```
$ echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
and reboot
$ sudo modprobe -rfv rt2800pci
and reboot
$ sudo modprobe -v rt3562sta

```

---

### Post by praseodym on 2012-07-02
Please show:

> lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
dmesg | egrep 'rt3|rt2'

---

### Post by refandina on 2012-07-02
Resultado:
Result:

```
lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [Realtek RTL8111E] [1043:8432]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. Device [1814:3060]
    Subsystem: Ralink corp. Device [1814:3060]
    Kernel driver in use: rt2860

``````
lsmod
Module                  Size  Used by
nls_iso8859_1          12617  2 
nls_cp437              12751  2 
vfat                   17335  2 
fat                    55505  1 vfat
binfmt_misc            13213  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
i915                  450944  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
rt3562sta             869831  0 
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  4 i915,drm_kms_helper
usbhid                 41704  0 
parport_pc             32111  1 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    77084  1 usbhid
asus_atk0110           17664  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usb_storage            43946  2 
uas                    17676  0 
r8169                  42534  0 

``````
 iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


``````
$ rfkill list
$
```no dio ningun resultado
did not give any results


```
dmesg | egrep 'rt3|rt2' 
[    8.161951] rt3562sta: module license 'unspecified' taints kernel.
[    8.170322] ===> rt2860_probe
[    8.170337] rt2860 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.171566] @rt2860_probe MAC address: 00:a1:b0:66:5c:dc
[    8.171568] <=== rt2860_probe
[  221.737749] rt28xx_get_wireless_stats --->

```

---

### Post by praseodym on 2012-07-02
Remove (not edit!) your wireless profile in the network-manager and create a new one.

---

### Post by refandina on 2012-07-03
Disculpa, no paso nada. Borre y despues agregue una nueva red inalambrica y sigue sin andar
Sorry, nothing happened. Delete and then add a new wireless network and still no go


ademas no aparece para activar la red inalambrica, ahi va captura de pantalla
also does not appear to enable the wireless network, there is screenshot


[[IMG]http://ompldr.org/tZW1mNg[/IMG]]("http://ompldr.org/vZW1mNg")

---

### Post by praseodym on 2012-07-03
Ok, check:

```
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
ifconfig -a
rfkill list
```
Router firmware is up-to-date? MAC-address filter is turned off in the router?

---

### Post by refandina on 2012-07-03
el router anda bien. con otras notebook y celulares funciona perfecto. no tiene filtrado por mac.
the router is fine. with other notebook and mobile works perfect. is not filtered by mac
.

ahi va lo solicitado:
As requested here it goes:

 ```
cat /etc/network/interfaces
auto lo
iface lo inet loopback

``````
cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1

``````
route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth3
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth3

``````
ifconfig -a
eth3      Link encap:Ethernet  direcciónHW 14:da:e9:9d:a1:f5  
          Direc. inet:192.168.1.43  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::16da:e9ff:fe9d:a1f5/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:26919 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:20019 errores:0 perdidos:0 overruns:0 carrier:1
          colisiones:0 long.colaTX:1000 
          Bytes RX:34507000 (34.5 MB)  TX bytes:2697565 (2.6 MB)
          Interrupción:44 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:16 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:16 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:960 (960.0 B)  TX bytes:960 (960.0 B)

``````
$ rfkill list
:~$ 

```
rfkill list no dio ningun resultado
rfkill list did not give any results

---

### Post by praseodym on 2012-07-03
"eth3" is your wired connection, which is preferred! Unplug the cable and try it again

---

