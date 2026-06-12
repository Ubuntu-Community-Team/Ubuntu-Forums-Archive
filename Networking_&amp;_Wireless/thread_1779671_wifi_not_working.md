---
title: "wifi not working"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by amautotech on 2011-06-10
I have installed 11.04 on lenovo V460 , evenafter updating the broadcom driver in addtional drivers it does not show any wireless connections, have to connect it through lan cable everytime...please guide me

---

### Post by chili555 on 2011-06-10
Let's see what you have so far. Please open Applications > Terminal and run and post:```
lspci -nn | grep -i 14e4
lsmod | grep -e b43 -e wl
dmesg | grep -e b43 -e wl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by amautotech on 2011-06-10
did that , still not working , do u need the screen out puts of the above commands...??

---

### Post by chili555 on 2011-06-10
> **amautotech said:**
> did that , still not working , do u need the screen out puts of the above commands...??Those commands were not intended to get it running, they were intended to gather information. That's what I meant by 'let's see what you have.' Yes, I need to see the outputs; that's what 'post' means.

---

### Post by amautotech on 2011-06-10
[FONT=monospace]lspci -nn\ grep -i l4e4
lspci: invalid option -- ' '
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
ayman@ubuntu:~$ lsmod \grep -e b43 -e wl
Usage: lsmod
ayman@ubuntu:~$ dmseg \ grep -e wl
No command 'dmseg' found, did you mean:
 Command 'mmseg' from package 'sunpinyin-utils' (universe)
 Command 'dmesg' from package 'util-linux' (main)
dmseg: command not found
ayman@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

[/FONT]

---

### Post by chili555 on 2011-06-10
lspci -nn\ grep -i l4e4 is not the same thing as lspci -nn | grep -i 14e4. Also, it's 14e4; the first character is one, not L. Please try again. Also let me see:```
sudo rfkill unblock all
rfkill list all
```It's not dmseg \ grep -e wl, it's [COLOR="Red"]dmesg[/COLOR] | grep -e b43 -e wl

---

### Post by amautotech on 2011-06-10
lspci -nn | grep -i 14e4
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
ayman@ubuntu:~$ lsmod | grep -e b43 -e wl
wl                   2642531  0 
lib80211               14570  1 wl
ayman@ubuntu:~$ dmesg | grep -e b43 -e wl
[   23.543810] wlc_bmac_attach:: deviceid 0x4727 nbands 1 board 0x510 macaddr: ac:81:12:14:09:09
[   23.551077] wl_set_hint: Sending country code US to MAC80211
[   23.551082] wl0: Broadcom BCM43xx 802.11 MAC80211 Driver (1.82.8.0) (Compiled at 06:32:13 on Apr 11 2011)
[   23.651355] wl: module license 'MIXED/Proprietary' taints kernel.
ayman@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

---

### Post by amautotech on 2011-06-10
could not do the rf kill commands as my system got stuck every time i did it , had to manually restart it

---

### Post by chili555 on 2011-06-10
Ahhh! Much better. Thank you.

It looks like you have the correct driver installed, but software is blocking your wireless:> 2: acer-wireless: Wireless LAN
[COLOR="Red"]Soft blocked: yes[/COLOR]Let's see if we can fix it. Please do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Now is your wireless working? If so, we'll need to write changes to two files to make it permanent; otherwise you'll have to issue these commands on every boot.

---

### Post by amautotech on 2011-06-10
As i write the first command , it asks for password  & while i write the password it does not take that ...

---

### Post by amautotech on 2011-06-10
and i am using lenovo ideapad , so do we have to change the command for that..??

---

### Post by chili555 on 2011-06-10
> **amautotech said:**
> As i write the first command , it asks for password  & while i write the password it does not take that ...For security reasons, Linux does not show the password or even show *** giving a clue as to the number of characters. Put it in and press Enter. If you put in the right password, the command will execute.

That's one of the interesting things about Linux that we all take for granted that new users stumble over. Welcome to Linux!

---

### Post by amautotech on 2011-06-10
ayman@ubuntu:~$ sudo rmmod -f acer-wmi
[sudo] password for ayman: 
ERROR: Removing 'acer_wmi': No such file or directory

---

### Post by chili555 on 2011-06-10
Let's see:```
sudo rfkill unblock all
rfkill list all
lsmod | grep -e acer -e idea -e wmi
```Thanks.

---

### Post by amautotech on 2011-06-10
just as write the first line 
sudo rfkill unblock all the system does not respond any more , so can't carry on with further steps...

---

### Post by chili555 on 2011-06-10
Ouch! Reboot and I'll check in tomorrow.

---

### Post by amautotech on 2011-06-10
thanks for ur support...

---

### Post by chili555 on 2011-06-11
Frankly, I'm not at all sure you can get the module wl going in Natty because of the softblocked issue. Please see here:

[http://ubuntuforums.org/showthread.php?p=10858742](http://ubuntuforums.org/showthread.php?p=10858742)

[http://ubuntuforums.org/showthread.php?t=1753072&page=3](http://ubuntuforums.org/showthread.php?t=1753072&page=3)

I am more than happy to try to help, but I don't have much hope. If I were you, I'd revert to Ubuntu 10.10 and be happy.

---

### Post by amautotech on 2011-06-11
the command u told me was for an acer machine where as i m using lenovo idea pad , so shouldn't i change that cammand...??

i wont be happy either ways as the problem persisted  in 10.10 also...

---

### Post by chili555 on 2011-06-11
Let's see:```
lsmod
```I think an Acer module is loaded:> ayman@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
Soft blocked: yes
Hard blocked: no
1: ideapad_bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
2: [COLOR="Red"]acer-wireless[/COLOR]: Wireless LAN
Soft blocked: yes
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: no


---

### Post by amautotech on 2011-06-11
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27479  4 
joydev                 17322  0 
snd_hda_codec_realtek   255820  1 
wl                   2642531  0 
lib80211               14570  1 wl
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
nouveau               626066  0 
brcm80211             690428  0 
i915                  450979  8 
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              257001  1 brcm80211
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
uvcvideo               66851  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               23123  0 
videodev               75143  1 uvcvideo
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59039  0 
cfg80211              156212  2 brcm80211,mac80211
intel_ips              17769  0 
serio_raw              12990  0 
ttm                    65184  1 nouveau
drm_kms_helper         40745  2 nouveau,i915
ideapad_laptop         13262  0 
soundcore              12600  1 snd
drm                   184133  6 nouveau,ttm,i915,drm_kms_helper
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sparse_keymap          13666  2 acer_wmi,ideapad_laptop
i2c_algo_bit           13184  2 nouveau,i915
video                  18951  2 nouveau,i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  1 
libahci                25548  1 ahci
atl1c                  36237  0

---

### Post by chili555 on 2011-06-11
> snd_timer 28659 2 snd_pcm,snd_seq
uvcvideo 66851 0
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq
[COLOR="Red"]acer_wmi[/COLOR] 23123 0
videodev 75143 1 uvcvideo
snd 55295 14 snd_hda_codec_hdmThere it is.

Now let's see:```
rfkill list all
sudo rfkill unblock all
rfkill list all
```

---

### Post by amautotech on 2011-06-11
ayman@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

---

### Post by chili555 on 2011-06-11
Let's try this one more time, I suspect it will work in 10.10:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```

---

### Post by amautotech on 2011-06-11
after  writing
"sudo rfkill unblock all" 
system was not responding so restarted it , can't we use any alternative method...

---

### Post by chili555 on 2011-06-11
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668234](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668234)

Let's try:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell me if your wireless is working.

---

