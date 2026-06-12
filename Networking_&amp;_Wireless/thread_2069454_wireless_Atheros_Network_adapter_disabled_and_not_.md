---
title: "wireless Atheros Network adapter disabled and not scanning."
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by jcushman20112012 on 2012-10-10
Hey there..sure hope someone can help..I know it can scan and pick up my wireless network because it did about 1 month ago after following various instructions in previous postings.  However, I do not know exactly what it was that got to work and I did and do not know how to make it permanent.  It had gone back to not working at the next boot..

lspci -nnk | grep -iA2 net

00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth
--
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5

cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux jean-laptop 2.6.32-43-generic #97-Ubuntu SMP Wed Sep 5 16:43:09 UTC 2012 i686 GNU/Linux

nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:1D:72:6B:A3:D3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.2.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        00:22:69:0F:D5:17

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

rfkill list all

2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

lsmod

Module                  Size  Used by
ath5k                 122927  0 
mac80211              225491  1 ath5k
ath                     8041  1 ath5k
cfg80211              144650  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8933  2 
fat                    47767  1 vfat
isofs                  29250  0 
udf                    79365  0 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
dm_crypt               11331  0 
ppdev                   5259  0 
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_conexant    22705  1 
joydev                  8740  0 
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74297  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2             5199  0 
psmouse                63677  0 
serio_raw               3978  0 
shpchp                 28835  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usbhid                 36110  0 
hid                    67288  1 usbhid
usb_storage            40033  5 
nouveau               467048  2 
ttm                    49847  1 nouveau
drm_kms_helper         29329  1 nouveau
video                  17375  0 
drm                   163779  4 nouveau,ttm,drm_kms_helper
output                  1871  1 video
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 nouveau
ahci                   32680  0 
pata_amd                8766  0 
forcedeth              49556  0 


some info to get started..Thanks


10_16_2011 - Please help me get this Atheros card to start scanning again..Thank you!

---

### Post by jcushman20112012 on 2012-10-25
10-25-2012 - Here is a listing from - sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa -e etork | tail -n55

Oct 25 17:22:33 jean-laptop kernel: [    0.731550] device-mapper: multipath: version 1.1.0 loaded
Oct 25 17:22:33 jean-laptop kernel: [    0.731554] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct 25 17:22:33 jean-laptop kernel: [   22.256125] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
Oct 25 17:22:33 jean-laptop kernel: [   22.256139] ath5k 0000:07:00.0: setting latency timer to 64
Oct 25 17:22:33 jean-laptop kernel: [   22.256186] ath5k 0000:07:00.0: registered as 'phy0'
Oct 25 17:22:33 jean-laptop kernel: [   22.759377] ath: EEPROM regdomain: 0x64
Oct 25 17:22:33 jean-laptop kernel: [   22.759380] ath: EEPROM indicates we should expect a direct regpair map
Oct 25 17:22:33 jean-laptop kernel: [   22.759386] ath: Country alpha2 being used: 00
Oct 25 17:22:33 jean-laptop kernel: [   22.759388] ath: Regpair used: 0x64
Oct 25 17:22:33 jean-laptop kernel: [   22.775869] Registered led device: ath5k-phy0::rx
Oct 25 17:22:33 jean-laptop kernel: [   22.775890] Registered led device: ath5k-phy0::tx
Oct 25 17:22:33 jean-laptop kernel: [   22.775894] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Oct 25 17:22:34 jean-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/eth0, iface: eth0)
Oct 25 17:22:34 jean-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 25 17:22:34 jean-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/0000:07:00.0/net/wlan0, iface: wlan0)
Oct 25 17:22:34 jean-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/0000:07:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct 25 17:22:34 jean-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct 25 17:22:34 jean-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:14.0/0000:07:00.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k')
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): now managed
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): bringing up device.
Oct 25 17:22:34 jean-laptop kernel: [   23.423448] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): preparing device.
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Oct 25 17:22:34 jean-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready

Something appears to be blocking the scanning part of the Atheros card..Any help would be appreciated..Thanks

---

### Post by wildmanne39 on 2012-10-27
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by jcushman20112012 on 2012-10-27
Here is the netinfo.txt file, if I attached it correctly..Thank You so much for responding so quickly..

---

### Post by wildmanne39 on 2012-10-29
Hi, sorry it took me so long to get back to you, I had to work a 36 hour shift.

Your card is hard blocked, first make sure your switch is on or it could be a key combination that turns it on.

With 10.04 you have to have your hard wire disconnected to connect with wireless.

Also please do:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
if it still does not come on then do:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
``` 
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by grizlbr on 2012-10-29
Read use Jockey to choose between (######) &  (######) ??? where did I just see that?? MCP77  nVidia  ubuntu While I recovered my password on two forums?:confused: blue light is on just got 10.10 installed on HD. Oh yeah:!
/etc/modprobe.d/blacklist-ath_pci.conf

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

now what is Jockey??

---

### Post by chili555 on 2012-10-29
I suspect the Wild Man will have a few questions about this:> 0: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="Red"]Hard blocked: yes[/COLOR]And this:> IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.[COLOR="Red"]1[/COLOR].1

    DNS:             192.168.[COLOR="Red"]2[/COLOR].1

---

### Post by wildmanne39 on 2012-10-29
Hi, you said > blue light is on just got 10.10 installed on HD.did you install 10.10 if so why? is it not supported anymore, I recommend 12.04 LTS.

Good to see you chili555!!!
Thanks

---

### Post by jcushman20112012 on 2012-10-30
Okay..according to the manual, the wireless light is blue when on, amber when off.  When cold-booted, it starts out amber till about 1 second before the sign-on screen displays..it stays blue if I just restart it.  Apparently it is on with some (leftover) software piece "various things I tried to get it work" that kills the scanning of wifi networks.  Sure appreciate your help!

---

### Post by chili555 on 2012-10-30
I don't want to step on Wild Man's toes, but would you please do:```
sudo gedit /etc/network/interfaces
```Change it to:```
auto lo
iface lo inet loopback
```Proofread, save and close gedit. Now do:```
sudo service network-manager restart
```What explains this?> IPv4 Settings:
Address: 192.168.1.100
Prefix: 24 (255.255.255.0)
Gateway: 192.168.[COLOR="Red"]1[/COLOR].1

DNS: 192.168.[COLOR="Red"]2[/COLOR].1 Do you have a router behind a router? Or...what? Did you place the DNS nameserver in Network Manager yourself?

Please run and post:```
sudo rfkill unblock all
rfkill list all
```What kind of laptop is it?

---

### Post by jcushman20112012 on 2012-10-30
IPv4 Settings:
Address: 192.168.1.100
Prefix: 24 (255.255.255.0)
Gateway: 192.168.[COLOR=Red]1[/COLOR].1 - router ip address (its default)

DNS: 192.168.[COLOR=Red]2[/COLOR].1 			 		- DSL modem ip address - had to be changed years ago..don't remember why.

      /etc/network/interfaces is now back to what it used to be:
auto lo iface lo inet loopback

sudo service network-manager restart - done

rfkill list all
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

That about covers the last reply..oh yeah the laptop is a 
Compaq CQ50-215NR Presario with an AMD Athlon X2 64 processor or so 
the sticker says..

---

### Post by chili555 on 2012-10-30
> rfkill list all
1: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]This must be overcome before we can make any progress. Does pressing the wireless button change anything?```
rfkill list all
```Press wireless button.```
rfkill list all
```Does the LED turn on or off or change color or smoke or spark??

Please see attached.

---

### Post by jcushman20112012 on 2012-10-30
rfkill list all - before button press..(button is blue)

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

pushed button..still blue

rfkill list all

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by chili555 on 2012-10-30
Please try:> sudo modprobe -r ath5k
sudo modprobe ath5k no_hw_rfkill_switch=Y
sudo rfkill unblock all
rfkill list allAlso, please run and post:```
ls /etc/modprobe.d
```

---

### Post by jcushman20112012 on 2012-10-30
sudo modprobe -r ath5k

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

      sudo modprobe ath5k no_hw_rfkill_switch=Y

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting ath5k (/lib/modules/2.6.32-43-generic/updates/compat-wireless-2.6.34/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

      sudo rfkill unblock all

jean@jean-laptop:~$ sudo rfkill unblock all

      rfkill list all

jean@jean-laptop:~$ rfkill list all 

       ls /etc/modprobe.d

alsa-base               blacklist.conf              blacklist-oss.conf
alsa-base.conf          blacklist.conf.dpkg-old     blacklist-oss.dpkg-bak
ath5k.conf              blacklist-firewire.conf     blacklist-watchdog.conf
blacklist               blacklist-framebuffer.conf  libpisock9.conf
blacklist-ath_pci.conf  blacklist-modem.conf        nvidia-kernel-nkc.conf

ps...The wireless network section in Network Manager has disappeared altogether..

---

### Post by chili555 on 2012-10-31
Yikes.

Let's fix one problem at a time.> WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.You have a file called alsa-base and one called alsa-base.conf. You only need one: alsa-base.conf. Please see what is in the wrong one:```
cat /etc/modprobe.d/alsa-base
```Write it down somewhere. Now look in the other file:```
cat /etc/modprobe.d/alsa-base**.conf**
```Does the item you wrote down appear in the correct .conf file? If no, and you are sure you need it, then let's add it:```
sudo su
echo whateveryoufound >> /etc/modprobe.d/alsa-base.conf
exit
```Do the same with blacklist and blacklist.conf. If what is in blacklist has anything to do with wireless, please stop and ask me.

Once you are quite sure you have correctly consolidated the files, you can remove the improper files:```
sudo rm /etc/modprobe.d/alsa-base
sudo rm /etc/modprobe.d/blacklist
```If in the slightest doubt, stop and ask me.

Now the hard one:> FATAL: Error inserting ath5k (/lib/modules/2.6.32-43-generic/updates/compat-wireless-2.6.34/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)It appears that you tried to compile the compat-wireless package. Have you done so since you started this thread? I don't understand because you had ath5k loaded just fine at post #1:> lsmod

Module Size Used by
ath5k 122927 0
mac80211 225491 1 ath5k
ath 8041 1 ath5k
cfg80211 144650 3 ath5k,mac80211,ath
led_class 2864 1 ath5k
<snip>What's going on?

---

### Post by jcushman20112012 on 2012-11-01
1. 
sudo rm /etc/modprobe.d/blacklist -- done

2.the alsa-base seems to have alot in it.  Seems to be mostly about 
sound. I have no idea if I need any of the differences. It'd be nice 
just to rename the file to have a "-old" at the end of it..or comment out 
each line..

3.  It appears that you tried to compile the compat-wireless package. Have  you done so since you started this thread? I don't understand because  you had ath5k loaded just fine at post #1:

No I haven't, at least not knowingly.  I'll run 
ls /etc/modprobe.d now to see what it says..
    alsa-base               blacklist.conf.dpkg-old     blacklist-oss.dpkg-bak
alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
ath5k.conf              blacklist-framebuffer.conf  libpisock9.conf
blacklist-ath_pci.conf  blacklist-modem.conf        nvidia-kernel-nkc.conf
blacklist.conf          blacklist-oss.conf

next..
sudo modprobe -r ath5k
[sudo] password for jean: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

next..

sudo modprobe ath5k no_hw_rfkill_switch=Y
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

jean@jean-laptop:~$ sudo rfkill unblock all
jean@jean-laptop:~$ rfkill list all
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

btw.. here's lsmod again..
Module                  Size  Used by
ath5k                 122927  0 
mac80211              225491  1 ath5k
ath                     8041  1 ath5k
cfg80211              144650  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8933  2 
fat                    47767  1 vfat
usbhid                 36110  0 
hid                    67288  1 usbhid
isofs                  29250  0 
udf                    79365  0 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
dm_crypt               11331  0 
ppdev                   5259  0 
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_conexant    22705  1 
joydev                  8740  0 
snd_hda_intel          22069  2 
snd_hda_codec          74297  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
arc4                    1153  2 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
shpchp                 28835  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usb_storage            40033  5 
nouveau               467048  2 
ttm                    49847  1 nouveau
drm_kms_helper         29329  1 nouveau
drm                   163779  4 nouveau,ttm,drm_kms_helper
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 nouveau
ahci                   32680  1 
forcedeth              49556  0 
pata_amd                8766  0 
video                  17375  0 
output                  1871  1 video

to get ath5k listed again I used.. 
sudo modprobe ath5k

think that's all...you asked..

---

### Post by chili555 on 2012-11-02
> 2.the alsa-base seems to have alot in it. Seems to be mostly about
sound. I have no idea if I need any of the differences. It'd be nice
just to rename the file to have a "-old" at the end of it..or comment out
each line..
You certainly don't need an alsa-base file and an alsa-base.conf file. I suggest you copy alsa-base to a text document in your home directory:```
sudo cp /etc/modprobe.d/alsa-base ~/alsa.txt
```Now open the file alsa.txt with any text editor. Minimize it while you do:```
sudo gedit /etc/modprobe.d/alsa-base.conf
```Maximize the alsa.txt file and copy all the text: Edit > Select All > Copy. Paste it in to the file alsa-base.conf. Proofread it carefully to be sure everything copied over correctly. Save and close gedit. Now we can rename the alsa-base file:```
sudo mv /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.old
```> to get ath5k listed again I used..
sudo modprobe ath5kI don't understand this. It *was* listed:> [COLOR="Red"]ath5k[/COLOR] 122927 0
mac80211 225491 1 ath5k
ath 8041 1 ath5k
cfg80211 144650 3 ath5k,mac80211,ath
led_class 2864 1 ath5kWe still haven't found any way to change the wireless to not be hard blocked.

---

