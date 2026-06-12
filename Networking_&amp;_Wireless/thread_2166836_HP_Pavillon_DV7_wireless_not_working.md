---
title: "HP Pavillon DV7 wireless not working"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by ramon71 on 2013-08-11
Hi,
i installed ubuntu 13.04 on a HP Pavillon DV7, but the wireless (Broadcomm BCN4313) seems to be not working, any suggestion?

---

### Post by varunendra on 2013-08-11
Welcome to the forums ramon71 !

Have you installed the proprietary "wl" driver during or after installing Ubuntu? Check with -
```
lspci -nnk | grep -iA2 net
```

If the "Kernel driver in use" is "wl", purge it and load the native brcmsmac instead -
```
sudo modprobe -rfv wl
sudo apt-get purge bcmwl-kernel-source
sudo modprobe -v brcmsmac
```

If the first command gives any errors, just execute the first command above (apt-get purge...) and reboot. You should get connected on next boot.

---

### Post by ramon71 on 2013-08-11
doneand it seems to get near, i mean, now the output of iwconfig is:

```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on


```

still can't see the wifi connection icon, and the option to enable wifi under the networking icon is not selectable (grayed)

---

### Post by varunendra on 2013-08-11
> **ramon71 said:**
> still can't see the wifi connection icon, and the option to enable wifi under the networking icon is not selectable (grayed)

Please post the outputs of -
```
lsmod
rfkill list all
nm-tool
sudo iwlist scan
dmesg | egrep -i 'wlan|brcm|network|firmware'
```

---

### Post by ramon71 on 2013-08-11
hereit is:
lsmod
```

Module                  Size  Used by
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
parport_pc             28152  0 
ppdev                  17073  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
arc4                   12615  2 
brcmsmac              550698  0 
cordic                 12574  1 brcmsmac
brcmutil               14755  1 brcmsmac
mac80211              606457  1 brcmsmac
cfg80211              510937  2 brcmsmac,mac80211
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
joydev                 17377  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
snd_hda_intel          39619  3 
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
hp_wmi                 18048  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
sparse_keymap          13890  1 hp_wmi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
hp_accel               26012  0 
lis3lv02d              20111  1 hp_accel
snd_rawmidi            30180  1 snd_seq_midi
input_polldev          13896  1 lis3lv02d
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
bcma                   41051  1 brcmsmac
nouveau               939088  1 
i915                  600396  3 
mxm_wmi                13021  1 nouveau
ttm                    83187  1 nouveau
rtsx_pci_ms            13011  0 
wmi                    19070  3 hp_wmi,mxm_wmi,nouveau
video                  19390  2 i915,nouveau
drm_kms_helper         49394  2 i915,nouveau
drm                   286028  7 ttm,i915,drm_kms_helper,nouveau
microcode              22881  0 
memstick               16554  1 rtsx_pci_ms
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
psmouse                95870  0 
soundcore              12680  1 snd
serio_raw              13215  0 
lpc_ich                17061  0 
mei                    41158  0 
lp                     17759  0 
i2c_algo_bit           13413  2 i915,nouveau
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  1 
rtsx_pci_sdmmc         17475  0 
ahci                   25731  1 
libahci                31364  1 ahci
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67446  0 

```

rfkill list all:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

seems there's an hardware block on the wireless LAN

sudo iwlist scan
```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


```

trying bringin up wlan0 obviously not working due to a rfkill

dmesg | egrep -i 'wlan|brcm|network|firmware'
```

[   19.852764] type=1400 audit(1376277702.490:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=636 comm="apparmor_parser"
[   19.852976] type=1400 audit(1376277702.490:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=637 comm="apparmor_parser"
[   20.490246] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 19
[   21.035403] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   23.198392] brcmsmac bcma0:0: brcms_ops_start: brcms_up() returned -132
[   23.198605] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


```

---

### Post by ramon71 on 2013-08-11
meanwhile thanks for the assistance Varunendra

EDIT: seems the switch isn't working

EDIT: block removed with: rfkill unblock all

EDIT: the issue seems actually solved, thanks again for the assistance, i'll post updates about my other issue with the Acer laptop and XUbuntu later, gimme some time to fully test, and i'll close this topic, any comment/suggestion still welcomed

---

### Post by ramon71 on 2013-08-12
still experiencing problems: the network is detected only in the immediate proximity of the router, in the adjacent room it does not detect or connect to the network, consider now i'm writing from another pc connected from the same room where the HP Pavillon fails to connect, since it seems the issue it was an hardware block of the device, should i retry activating the proprietary drivers for the device, or what else?

EDIT: sorry i forgot the output of nm-tools, i'll post asap, now i have not access to my machines (i'm away from home), i'll try with your script also

---

### Post by varunendra on 2013-08-12
> **ramon71 said:**
> i'll try with your script also

Not my script, it's main author is Wild Man and besides him it is being developed and helped by some other knowledgeable people. I am just using that great work of others ;)

So.. now that your wireless interface is at least able to scan and connect, please try -
```
sudo iwconfig wlan0 power off
```
See if it improves connectivity. If not, run the wireless script and post back its result.

**PS:**
In my experience so far *(which is actually the experience of users with this particular card)*, the native brcmsmac driver always performs better than the **default version** of the proprietary "wl" driver.
However, in *some* cases in the *past*, some users reported that an older version of the wl driver performed better. So if we can't make the brcmsmac work satisfactorily, we may try that later (reference : [http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619))

---

### Post by ramon71 on 2013-08-12
```

sudo iwconfig wlan0 power off

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.


```

that's it, about nm-tool:

```

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        08:2E:5F:71:E3:0B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [darkstar] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:6C:8F:89

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *darkstar:       Infra, C0:3F:0E:33:73:CC, Freq 2452 MHz, Rate 54 Mb/s, Strength 67 WPA2

  IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1



```

please consider the machine is actually placed at 15 inches from the router, if i move in another room it fails connecting to the network

and here's the output from the script, thanks in advance for the time spent

---

### Post by varunendra on 2013-08-12
> **ramon71 said:**
> please consider the machine is actually placed at 15 inches from the router, if i move in another room it fails connecting to the network

I couldn't find anything suspicious in the wireless-info file. You may try changing the channel in the router to 1 or 11, but I doubt if it would make much difference. Try it anyway, and if it doesn't make it any better, please try what is suggested in this post : [http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619)

---

### Post by ramon71 on 2013-08-12
thanks varunendra, il try changing channel and the workarounds from the topic you linked asap, and will let you know about the results

---

### Post by ramon71 on 2013-08-12
> **varunendra said:**
> I couldn't find anything suspicious in the wireless-info file. You may try changing the channel in the router to 1 or 11, but I doubt if it would make much difference. Try it anyway, and if it doesn't make it any better, please try what is suggested in this post : [http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619)

i tried with the 'patched' driver, as you suggested, the process went well and the module was loaded correctly, but nothing changed: i'm able to connect from a close range, but not from another room. Il try switching channels as you suggested, but i see little margins to resolve this, at this point, thanks anyway for the help, at least it works (from a close range but it works), i'll post updates...

---

### Post by varunendra on 2013-08-12
.... and I am certainly out of ideas at this point.

Is the behaviour same with a Live CD/DVD ? On a different version/OS ? If yes, my guess would be that it is either a hardware or external problem.

Probably on a wild-goose chase you may try using [Wicd]("https://help.ubuntu.com/community/WICD") instead of the default NM, but since the same set of drivers, program and settings have been reported to be working fine for others, I seriously doubt if it will make any difference.

Please run the wireless_script when it fails to connect, and post its result. Besides that, reboot the system > (immediately) try to connect and let it fail > check syslog and post its contents :
```
cat /var/log/syslog | tail -50
```
Maybe we can find some hints in them.

**NOTE :** Try connecting and running syslog command as soon as possible after reboot, so that the syslog only contains messages that we are interested in.

---

### Post by ramon71 on 2013-08-13
i'll do all of that asap, again i',m away from home and can't access my machines for a while

---

### Post by ramon71 on 2013-08-13
Here i am: 

```

el@magdalena:~$ cat /var/log/syslog |tail -50
Aug 13 23:25:22 magdalena demond: [P:2301 T:973760320] src/demon.cpp   : 240  main                 -- usb scanners found is 0
Aug 13 23:25:22 magdalena demond: [P:2301 T:973760320] src/demon.cpp   : 309  main                 -- End of checking for USB scanners.
Aug 13 23:25:23 magdalena NetworkManager[1060]: <warn> Activation (wlan0/wireless): association took too long.
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Aug 13 23:25:23 magdalena NetworkManager[1060]: <warn> Activation (wlan0/wireless): asking for new secrets
Aug 13 23:25:23 magdalena kernel: [  122.899007] wlan0: deauthenticating from c0:3f:0e:33:73:cc by local choice (reason=3)
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Activation (wlan0/wireless): connection 'darkstar' has security, and secrets exist.  No new secrets needed.
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Config: added 'ssid' value 'darkstar'
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Config: added 'scan_ssid' value '1'
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Config: added 'psk' value '<omitted>'
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 13 23:25:23 magdalena wpa_supplicant[1121]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Aug 13 23:25:23 magdalena kernel: [  122.913362] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
Aug 13 23:25:23 magdalena kernel: [  122.913370] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
Aug 13 23:25:23 magdalena kernel: [  122.913373] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
Aug 13 23:25:23 magdalena kernel: [  122.913948] cfg80211: Calling CRDA to update world regulatory domain
Aug 13 23:25:23 magdalena kernel: [  122.917301] cfg80211: World regulatory domain updated:
Aug 13 23:25:23 magdalena kernel: [  122.917304] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> (wlan0): supplicant interface state: associated -> disconnected
Aug 13 23:25:23 magdalena NetworkManager[1060]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 13 23:25:23 magdalena kernel: [  122.917306] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 23:25:23 magdalena kernel: [  122.917307] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 13 23:25:23 magdalena kernel: [  122.917309] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 13 23:25:23 magdalena kernel: [  122.917310] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 23:25:23 magdalena kernel: [  122.917311] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 13 23:25:23 magdalena NetworkManager[1060]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> Config: set interface ap_scan to 1
Aug 13 23:25:23 magdalena NetworkManager[1060]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 13 23:25:24 magdalena wpa_supplicant[1121]: wlan0: SME: Trying to authenticate with c0:3f:0e:33:73:cc (SSID='darkstar' freq=2447 MHz)
Aug 13 23:25:24 magdalena kernel: [  123.876544] wlan0: authenticate with c0:3f:0e:33:73:cc
Aug 13 23:25:24 magdalena kernel: [  123.878424] wlan0: send auth to c0:3f:0e:33:73:cc (try 1/3)
Aug 13 23:25:24 magdalena wpa_supplicant[1121]: wlan0: Trying to associate with c0:3f:0e:33:73:cc (SSID='darkstar' freq=2447 MHz)
Aug 13 23:25:24 magdalena NetworkManager[1060]: <info> (wlan0): supplicant interface state: scanning -> associating
Aug 13 23:25:24 magdalena kernel: [  123.881219] wlan0: authenticated
Aug 13 23:25:24 magdalena kernel: [  123.884117] wlan0: associate with c0:3f:0e:33:73:cc (try 1/3)
Aug 13 23:25:24 magdalena wpa_supplicant[1121]: wlan0: Associated with c0:3f:0e:33:73:cc
Aug 13 23:25:24 magdalena kernel: [  123.889352] wlan0: RX AssocResp from c0:3f:0e:33:73:cc (capab=0x431 status=0 aid=3)
Aug 13 23:25:24 magdalena kernel: [  123.890015] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
Aug 13 23:25:24 magdalena kernel: [  123.890019] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
Aug 13 23:25:24 magdalena kernel: [  123.890020] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
Aug 13 23:25:24 magdalena kernel: [  123.890028] wlan0: associated
Aug 13 23:25:24 magdalena NetworkManager[1060]: <info> (wlan0): supplicant interface state: associating -> associated



```

and the wireless_info.txt after a boot with faulty connection

---

### Post by ramon71 on 2013-08-13
additionaly the wireless_info.txt after a faulty try of manually connecting

---

### Post by ramon71 on 2013-08-13
additionally the wireless_info.txt after a succesful connection at a close distance from my router

now i'll try wicd from your link

---

### Post by varunendra on 2013-08-13
You currently have both the wl and brcmsmac drivers loaded, which in itself is a problem. Given this fact, I doubt if it ever used the wl driver at all. Please try -
```
sudo modprobe -rfv brcmsmac
sudo modprobe -rfv wl
sudo modprobe -v wl
```
..and see if the connectivity improves. If it does, we'll need to manually blacklist the brcmsmac driver. Oh, and after running the above three commands, please post the outputs of -
```
lsmod | egrep 'wl|bcma|brcm'
iwconfig
```

**PS:**
I was suggested by my friend Hadaka that it may be also a problem of a loose antenna or a loose card connection. That makes sense given the ridiculously weak signals you are getting. So if the above does not help, I'd suggest to check the physical connections (preferably remove --> re-seat the card/antenna connections) if you can access the card. Usually, it is located in a user-accessible area at the bottom of laptops.

---

### Post by ramon71 on 2013-08-14
i'l try a clean install, and then retry the various options, gimme some time, and thanks for the attention

---

### Post by ramon71 on 2013-08-14
UPDATE: trying re-installing ubuntu from a room different from the one where my router is, the network was detected, trying to connect, it kept asking for the password without connectiong. At this point i launched the live OS from the DVD and start the installation from there, again it detected my network and, this time, it connected to the network!!!!!

Sory but i'm unable to decode this strange behaviour, maybe someone can be of help, and maybe this will help find a solution to my issue also?

---

### Post by ramon71 on 2013-08-14
UPDATE: while booting the ubuntu 13.04 media and installing the OS directly from there caused the wireless not to work properly, booting the live CD and installing from there not only allowed the connection during the installation, but the installed OS worked properly, connecting to my network everywhere in my house. Now, i really can't explain why and i'm too tired. Tomorrow i'll post the wireless script output if some of you is interested in going deeper in this issue, and will close this topic, thanks everybody for the attention and the help given!!!

---

### Post by varunendra on 2013-08-14
> **ramon71 said:**
> Now, i really can't explain why and i'm too tired.

Neither can I. :|
But glad it got fixed anyhow. The script output should be interesting to see. :)

---

### Post by ramon71 on 2013-08-15
here it is, im glad also ;-) this is the only issue i encountered with ubuntu ever (really i have even an usb TV stick wich refuse to work but that's a secondary issue, and maybe will post later about that ;-)

thanks again for the help guys, it's a pleasure to have a community of users like this to count on...

---

