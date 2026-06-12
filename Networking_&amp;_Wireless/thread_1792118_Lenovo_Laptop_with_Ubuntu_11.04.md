---
title: "Lenovo Laptop with Ubuntu 11.04"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by Josh_1970 on 2011-06-27
I have a Lenovo B570 installed with Windows 7. I installed Ubuntu 11.04 through the Windows installer and am now dual booting. My wired works fine. My wireless, I've installed and removed the additional drivers. I've had it work once (when I connected the cable and then disconnected it). Whenever I reboot, if it was left installed, it won't even detect the wireless. If I uninstall and reinstall, it will work insofar as it will detect my network. However, when I try to connect (router is WPA with TKIP) it gives me a bad password. I know I'm typing the password correctly as it works in windows on the same laptop.
Below is my info. I believe it was taken when I had the drivers uninstalled but I'm not sure.

Thanks,

Josh_1970
 

lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09) 
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09) 
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04) 
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05) 
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05) 
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5) 
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5) 
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5) 
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05) 
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05) 
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05) 
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 05) 
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) 
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06) 

lsmod 
Module                  Size  Used by 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
joydev                 17606  0 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13604  1 snd_hda_codec 
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
i915                  514985  3 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              29602  2 snd_pcm,snd_seq 
lib80211_crypt_tkip    17387  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
uvcvideo               72195  0 
videodev               82052  1 uvcvideo 
wl                   2568244  0 
drm_kms_helper         42136  1 i915 
acer_wmi               23771  0 
v4l2_compat_ioctl32    17078  1 videodev 
ideapad_laptop         13494  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
sparse_keymap          13898  2 acer_wmi,ideapad_laptop 
psmouse                73535  0 
drm                   227495  4 i915,drm_kms_helper 
i2c_algo_bit           13400  1 i915 
lib80211               14991  2 lib80211_crypt_tkip,wl 
serio_raw              13166  0 
soundcore              12680  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
video                  19438  1 i915 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp 
usbhid                 46956  0 
hid                    91020  1 usbhid 
ahci                   25951  3 
libahci                26642  1 ahci 
r8169                  48022  0 

rfkill list all 
0: ideapad_wlan: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: no 
1: brcmwl-0: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: yes 
2: acer-wireless: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: no

---

### Post by ahears on 2011-06-27
Open terminal (command line) and type the following command:
$ sudo /etc/init.d/networking restart
 **To start networking service, enter:**

 $ sudo /etc/init.d/networking start
 **To stop networking service, enter:**

 $ sudo /etc/init.d/networking stop

---

### Post by josephmills on 2011-06-27
> **Josh_1970 said:**
> I have a Lenovo B570 installed with Windows 7. I installed Ubuntu 11.04 through the Windows installer and am now dual booting. My wired works fine. My wireless, I've installed and removed the additional drivers. I've had it work once (when I connected the cable and then disconnected it). Whenever I reboot, if it was left installed, it won't even detect the wireless. If I uninstall and reinstall, it will work insofar as it will detect my network. However, when I try to connect (router is WPA with TKIP) it gives me a bad password. I know I'm typing the password correctly as it works in windows on the same laptop.
Below is my info. I believe it was taken when I had the drivers uninstalled but I'm not sure.

Thanks,

Josh_1970
 

lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09) 
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09) 
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04) 
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05) 
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05) 
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5) 
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5) 
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5) 
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05) 
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05) 
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05) 
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 05) 
[COLOR="Red"]]02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) [/COLOR]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06) 

lsmod 
Module                  Size  Used by 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
joydev                 17606  0 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13604  1 snd_hda_codec 
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
i915                  514985  3 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              29602  2 snd_pcm,snd_seq 
lib80211_crypt_tkip    17387  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
uvcvideo               72195  0 
videodev               82052  1 uvcvideo 
[COLOR="red"]wl                   2568244  0 [/COLOR]
drm_kms_helper         42136  1 i915 
[COLOR="DarkOrchid"]acer_wmi               23771  0[/COLOR] 
v4l2_compat_ioctl32    17078  1 videodev 
ideapad_laptop         13494  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
sparse_keymap          13898  2 acer_wmi,ideapad_laptop 
psmouse                73535  0 
drm                   227495  4 i915,drm_kms_helper 
i2c_algo_bit           13400  1 i915 
[COLOR="red"]lib80211               14991  2 lib80211_crypt_tkip,wl [/COLOR]
serio_raw              13166  0 
soundcore              12680  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
video                  19438  1 i915 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp 
usbhid                 46956  0 
hid                    91020  1 usbhid 
ahci                   25951  3 
libahci                26642  1 ahci 
r8169                  48022  0 

rfkill list all 
0: ideapad_wlan: Wireless LAN 
[COLOR="red"]	Soft blocked: yes [/COLOR]
	Hard blocked: no 
1: brcmwl-0: Wireless LAN 
[COLOR="red"]	Soft blocked: yes 
	Hard blocked: yes 
2: acer-wireless: Wireless LAN 
	Soft blocked: yes [/COLOR]
	Hard blocked: no

try a fliping the switch on the laptop for the wireless then do a ```
rfkill unblock all  
``` anything ?

---

### Post by ahears on 2011-06-27
'rfkill unblock all' works on my test. I have the same laptop.

---

### Post by Josh_1970 on 2011-06-27
It just worked for me also.  Will I have to do this every time I restart?  In windows, it never disables the wifi. Until now, every time I've rebooted from Ubuntu the Wifi is disabled. 

Thanks,

Josh_1970

---

### Post by josephmills on 2011-06-27
> **Josh_1970 said:**
> It just worked for me also.  Will I have to do this every time I restart?  In windows, it never disables the wifi. Until now, every time I've rebooted from Ubuntu the Wifi is disabled. 

Thanks,

Josh_1970

no we can fix that for you to open you terminal and type in ```
gksudo gedit /ect/rc.local
``` now add ```
rfkill unblock all 
```  right after # By default this script does nothing.
and right before before the line exit 0 save it then exit and reboot how is it working ?

---

### Post by ahears on 2011-06-27
> **josephmills said:**
> no we can fix that for you to open you terminal and type in ```
gksudo gedit /ect/rc.local
``` now add ```
rfkill unblock all 
```  right after # By default this script does nothing.
and right before before the line exit 0 save it then exit and reboot how is it working ?
 There may be a need to block or change this later for one interface or another. This will unblock everything every time. use the 'rfkill' command specific to what you want only. Using this procedure directly in the /etc/rc.local file to unblock everything all of the time might interfere with future changes. BEWARE, and don't forget in the future...

---

### Post by Josh_1970 on 2011-06-27
So would you recommend rfkill unblock wlan0 ?

---

### Post by nm_geo on 2011-06-27
> **Josh_1970 said:**
> So would you recommend rfkill unblock wlan0 ?

Here a better question Josh.
why is this loading on a lenovo laptop .. It ain't no acer..
[COLOR=Red]
[/COLOR][COLOR=Red]acer_wmi               23771  0 [/COLOR]

---

### Post by Josh_1970 on 2011-06-27
No idea. Whatever was there was put by the windows installer. Regardless, since it seems that I shouldn't unblock all in the startup, should I unblock wlan0 ?

---

### Post by nm_geo on 2011-06-27
> **Josh_1970 said:**
> No idea. Whatever was there was put by the windows installer. Regardless, since it seems that I shouldn't unblock all in the startup, should I unblock wlan0 ?
 
The link below by charles14618 had a number of other links with the same problem you have.

Now we can blacklist that acer_wmi and you might not even need the rfkill unblock all ...
That part I am not sure of, but you do not need the acer-wmi I am sure.

There are a couple ways to blacklist that module fastest is 

```
sudo su 
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf 
exit
```Then reboot ...  or we can do it graphically

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Then add the words "blacklist acer_wmi' without quotes to the file and save and exit..

It is simple to comment the blacklist statement out if it causes a problem.

You probably will not need the rfkill unblock all then..

---

### Post by Josh_1970 on 2011-06-27
Unfortunately, adding unblock all to rtc/local brought back the original problem.  It said invalid password. I took it out and manually typed unblock all and it works. Any ideas?

---

### Post by nm_geo on 2011-06-27
> **Josh_1970 said:**
> Unfortunately, adding unblock all to rtc/local brought back the original problem.  It said invalid password. I took it out and manually typed unblock all and it works. Any ideas?

Josh did you blacklist the acer_wmi  ?

---

### Post by Josh_1970 on 2011-06-27
Yes, I did. That I haven't changed. That made no difference either way.

---

### Post by nm_geo on 2011-06-27
> **Josh_1970 said:**
> Yes, I did. That I haven't changed. That made no difference either way.

Run the 
```
lsmod
```

```
rfkill list all
``` 
  
and paste please

---

### Post by josephmills on 2011-06-27
> **Josh_1970 said:**
> No idea. Whatever was there was put by the windows installer. Regardless, since it seems that I shouldn't unblock all in the startup, should I unblock wlan0 ?

josh why did you just not put the rfkill unblock all in rc.local ????? if you did that and rebooted it would show us if the wmi needs to be black listed or not. now if it is there let us see a ```
cat /etc/modprobe.d/blacklist.conf 
```
thanks we will get you all patched up. I should have explained the color thing in lsmod earlier sorry

---

### Post by nm_geo on 2011-06-27
> **josephmills said:**
> josh why did you just not put the rfkill in rc.local ????? if you did that and rebooted it would show us if the wmi needs to be black listed or not.

I think he must have had a problem with password or something.  I would sure like to see that rc.local file. I was reading the post by  charles14618 and saw that the "acer_wmi" needed blacklisting. my eyes aren't that good :p

---

### Post by jani888 on 2011-06-28
great info. 

i will surely need this when i get my lenovo soon. 

thanks guys

---

### Post by ahears on 2011-06-28
_***From your output above, the devices are listed by number, and therefore not listed by eth0 or wlan0 as you can see: ***_

rfkill list all 
**0:** ideapad_wlan: Wireless LAN 
[COLOR=red]    Soft blocked: yes    [/COLOR]<<< _This device is blocked by software_ >>>
    Hard blocked: no 
**1:** brcmwl-0: Wireless LAN 
[COLOR=red]    Soft blocked: yes      [/COLOR]<<< _This device is blocked by software_ >>>[COLOR=red]
    Hard blocked: yes    <<< _Same device is physically off_ >>>
**2:** acer-wireless: Wireless LAN 
    Soft blocked: yes      <<< _Again this device id blocked by software_ >>> [/COLOR]
    Hard blocked: no

> **Josh_1970 said:**
> So would you recommend rfkill unblock wlan0 ?
The above would be incorrect syntax...
[COLOR=Red]**Correct syntax is as follows **[/COLOR][COLOR=Red]**'rfkill unblock 0' or**[/COLOR] [COLOR=Red]**'rfkill unblock 1'**** or **[/COLOR][COLOR=Red]**'rfkill unblock 2'**[/COLOR], **_or as Josephmills stated_**, ***'rfkill unblock all'*** will work.

---

