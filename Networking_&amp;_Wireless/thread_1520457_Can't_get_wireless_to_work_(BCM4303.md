---
title: "Can't get wireless to work (BCM4303"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by JayStayPaid9888 on 2010-06-29
Hey guys, I recently posted this in the Absolute Beginner forum and haven't got much feedback, so I figured I would try it here as well.

I recently installed Ubuntu (Lucid Lynx) on a desktop that was gathering dust in my house. I absolutely love everything about it so far and I'm learning something new everyday. However, I have spent the past few days following every tutorial I can find in an effort to get my wireless to work, but to no avail. I have a BCM 4303 wireless card (apparently the most aggravating card on the market) and the chipset is 14e4:4301. I am connected to the internet through my laptop currently. I have tried ndiswrapper (no luck) as well as b43-fwcutter (no luck), but perhaps now that I have a whole wonderful community behind me, I might make a little more progress! Let me know whatever info I need to post and I will do it asap.

I have since reinstalled and am now working with a clean slate. I did apt-get update and also enabled the b43legacy driver found under System>Hardware Drivers. However, when I click the Network Manager and try to enable wireless, I find that it says wireless is disabled and Enable Wireless is blacked out when I right click. This is where I've been stuck for quite a while. 

I went ahead and moved to trying ndiswrapper.

I cabextracted the WinXP drivers I found here: [http://h10025.www1.hp.com/ewfrf/wc/s...os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/s...os=228&lang=en)

I then moved the files bcmwl5.inf and bcmwl5.sys to my desktop. I started ndisgtk and selected the bcmwl5.inf which it installed with no problems. Then I restarted my computer, just for good measure, but the "Enable Wireless" option is still faded when I right click Network Manager and it says "Wireless is Disabled." I'm very new to Ubuntu so any direction from here is greatly appreciated!

Also, I'm using a Dell desktop.

Let me know if you guys need more info and I will post it asap! Thanks so much in advance, guys! I am otherwise loving the Ubuntu experience.

---

### Post by purelinuxuser on 2010-06-29
Welcome to Ubuntu! :) In order to help you, we'll need some more information.  Post the output of the following commands:
```
lshw -c network
lspci
iwconfig
```

Good luck! ;)

---

### Post by bkratz on 2010-06-29
Would also like to see the output of 

lsmod

(that is LSMOD in lowercase) to see if we have more than one driver competing for supremacy since multiple approaches have already been tried.

---

### Post by kerry_s on 2010-06-29
where you connected to the internet when you enabled the drivers?
because you need to be connected for them to download.

---

### Post by chicoharv on 2010-06-29
make sure you have bcm4328 installed in package manager. Also see [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by JayStayPaid9888 on 2010-06-30
I installed something foolish which somehow led to Network-Manager applet disappearing. One thing led to another, I am once again working with a clean slate, lol. I have done nothing but install the b43-fwcutter found under Hardware Drivers. Here are the results of the commands, as requested.

lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 04
       serial: 00:13:20:93:79:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.0.77 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:dfcfd000-dfcfdfff ioport:d8c0(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:22:ee:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b


lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:01.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
03:02.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated       Tx-Power=0 dBm   
          Retry  long limit:7      RTS thr: off      Fragment thr: off
          Power Management: off



lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      51914  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
fbcon                  35102  71 
b43legacy             115152  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
tileblit                2031  1 fbcon
mac80211              204922  1 b43legacy
font                    7557  1 fbcon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
bitblit                 4707  1 fbcon
cfg80211              126485  2 b43legacy,mac80211
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
led_class               2864  1 b43legacy
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i915                  282354  3 
drm_kms_helper         29297  1 i915
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
intel_agp              24177  2 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
psmouse                63245  0 
serio_raw               3978  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
dell_wmi                1793  0 
lp                      7028  0 
dcdbas                  5422  0 
parport                32635  2 ppdev,lp
b44                    25542  0 
e100                   28211  0 
mii                     4381  2 b44,e100
ssb                    37336  2 b43legacy,b44



> where you connected to the internet when you enabled the drivers?
because you need to be connected for them to download.Yessir, I was.


I have tried blacklisting certain drivers in earlier efforts and realize I have not done so as of right now. I decided when I came to this forum I wouldn't make any moves without being told to do so, regardless of what I THINK I know. :p



Currently, network-manager shows wireless as "device is not ready"

---

### Post by JayStayPaid9888 on 2010-06-30
> **chicoharv said:**
> make sure you have bcm4328 installed in package manager. Also see [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)


I failed to locate bcm4328 in Synaptic Package Manager. Is it found in a repository other than Main Universe Restricted or Multiverse?

---

### Post by JayStayPaid9888 on 2010-06-30
Got this piece of advice in the other thread, which I linked to this one. Sorry for the multi posts! DON'T HATE ME! :lolflag:

> **anewguy said:**
> It's possible you need to add b43 and ssb to the  blacklist.conf file to stop default drivers from stepping on what you  are trying to install.  The same applies to the restricted driver.  If  you still have it enabled you must disable it before you can have any  success with another driver and method.  Same  goes  for the firmware  cutter.

It's also possible you need to do a ifup on wlan0 or some such thing -  you'd need to lshw -C network to see which you wireless adapter  is.

Added to blacklist.conf in /etc/modprobe.d/ :
blacklist b43
blacklist ssb

Which is the restricted driver? b43-legacy? I'm a bit confused. Pardon my ignorance!



::EDIT::
Ok, executed cmd sudo ifconfig wlan0 up. network manager instantly showed wireless went from "Device is not ready" to "Wireless is disabled." Enable Wireless is also blacked out again.

---

### Post by purelinuxuser on 2010-06-30
> **JayStayPaid9888 said:**
> Which is the restricted driver? b43-legacy? I'm a bit confused. Pardon my ignorance!

::EDIT::
Ok, executed cmd sudo ifconfig wlan0 up. network manager instantly showed wireless went from "Device is not ready" to "Wireless is disabled." Enable Wireless is also blacked out again.

b43 = built-in driver for newer Broadcom cards
b43legacy = built-in driver for older Broadcom cards
wl = restricted driver (nice name, Broadcom)

Repost lshw -c network.

---

### Post by JayStayPaid9888 on 2010-06-30
Ok, so far I've added b43, ssb, and wl to blacklist.conf. Any others?

Here are the results of lshw -c network
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 04
       serial: 00:13:20:93:79:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.0.62 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:dfcfd000-dfcfdfff ioport:d8c0(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:22:ee:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

---

### Post by bkratz on 2010-06-30
> **JayStayPaid9888 said:**
> Ok, so far I've added b43, ssb, and wl to blacklist.conf. Any others?

Here are the results of lshw -c network
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 04
       serial: 00:13:20:93:79:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.0.62 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:dfcfd000-dfcfdfff ioport:d8c0(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:22:ee:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b



Since you are not using an **ethernet** device that requires b44 ( a Broadcom version), I believe you should probably do that one too ( I think it makes ssb load anyway even though blacklisted). Someone please correct if wrong, you might wait just a little while for any comments. A reboot is probably required.

---

### Post by JayStayPaid9888 on 2010-06-30
> **bkratz said:**
> Since you are not using an **ethernet** device that requires b44 ( a Broadcom version), I believe you should probably do that one too ( I think it makes ssb load anyway even though blacklisted). Someone please correct if wrong, you might wait just a little while for any comments. A reboot is probably required.


Ok, I'll hold off until I get some more feedback. Also, I've currently got my desktop on the internet through my laptop with an ethernet cable. Will blacklisting b44 cut that off?

---

### Post by bkratz on 2010-06-30
> **JayStayPaid9888 said:**
> Ok, I'll hold off until I get some more feedback. Also, I've currently got my desktop on the internet through my laptop with an ethernet cable. Will blacklisting b44 cut that off?

No, actually it would only affect the ethernet of the laptop, the desktop has it own card and may or may not use the same driver, but it would be there in it if used.

---

### Post by purelinuxuser on 2010-06-30
Hold on, guys. **JayStayPaid9888**, let's make one thing clear: which route do you want to go?

B43 Legacy driver - open source driver
Ndiswrapper - Windows driver emulated (sort of ) under Linux
[s]Broadcom proprietary driver (wl) - Broadcom's Linux wireless driver[/s]

Once you've picked your desired driver, we can proceed with a solution. ;)

---

### Post by bkratz on 2010-06-30
> **purelinuxuser said:**
> Hold on, guys. **JayStayPaid9888**, let's make one thing clear: which route do you want to go?

B43 - open source driver
Ndiswrapper - Windows driver emulated (sort of ) under Linux
Broadcom proprietary driver (wl) - Broadcom's Linux wireless driver

Once you've picked your desired driver, we can proceed with a solution. ;)

The BCM4303 can not use either the b43 or sta drivers, it can only use the b43legacy driver.

See here
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by purelinuxuser on 2010-06-30
> **bkratz said:**
> The BCM4303 can not use either the b43 or sta drivers, it can only use the b43legacy driver.

See here
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

I knew it was b43legacy only, but I didn't know it wasn't STA compatible! :confused:

(post edited)

---

### Post by JayStayPaid9888 on 2010-07-01
Ok, so lets go the b43legacy route! ;-)

Direct me, oh Directors!

---

### Post by bkratz on 2010-07-01
Since your card shows up as disabled--it might be nice to see the outputs of the following terminal commands.

rfkill list
and
iwconfig

---

### Post by purelinuxuser on 2010-07-01
> **JayStayPaid9888 said:**
> Ok, so lets go the b43legacy route! ;-)

Direct me, oh Directors!

Easy squeezy! :)

[LIST=1]
[*]Plug into Ethernet for an Internet connection
[*]Install the package "b43-fwcutter"
[*]During installation you will get a checkbox that reads "Automatically download and install firmware?" make sure it is **checked**.
[*]Reboot.
[/LIST]
Good luck! ;)

EDIT: If this doesn't work, please post ```
dmesg | grep -i b43
```

---

### Post by JayStayPaid9888 on 2010-07-01
I reinstalled fwcutter, making sure i had the box checked. After a restart, Enable Wireless is still blacked out and here are the results of the cmd's requested:
[B]

rfkill list[/B]
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
[B]

iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power= off   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off



**dmesg | grep -i b43**
[    1.498335] b43-pci-bridge 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.290251] b43legacy-phy0: Broadcom 4301 WLAN found
[   13.312064] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   13.312089] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   13.344182] b43legacy-phy0 debug: Radio initialized
[   14.196080] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   14.222665] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   14.242635] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   14.365047] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   14.422660] b43legacy-phy0 debug: Chip initialized
[   14.422870] b43legacy-phy0 debug: 30-bit DMA initialized
[   14.423657] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2B
[   14.423665] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x78
[   14.423672] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2E
[   14.423678] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x19
[   14.423722] b43legacy-phy0 debug: Wireless interface started
[   14.423743] b43legacy-phy0: Radio hardware status changed to DISABLED
[   14.423752] b43legacy-phy0 debug: Radio initialized
[   14.424304] b43legacy-phy0 debug: Adding Interface type 2
[   14.472284] b43legacy-phy0: Radio turned on by software
[   14.472292] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   14.528273] b43legacy-phy0 debug: Removing Interface type 2
[   14.536272] b43legacy-phy0 debug: Wireless interface stopped
[   14.536390] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   14.536435] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   14.536485] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   14.544300] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   14.552285] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   14.560272] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   14.568300] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   14.658741] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   14.764043] b43legacy-phy0 debug: Radio initialized
[   14.764061] b43legacy-phy0 debug: Radio initialized

---

### Post by bkratz on 2010-07-01
> **JayStayPaid9888 said:**
> I reinstalled fwcutter, making sure i had the box checked. After a restart, Enable Wireless is still blacked out and here are the results of the cmd's requested:
[B]

rfkill list[/B]
0: phy0: Wireless LAN
    Soft blocked: no
   [COLOR="Red"] Hard blocked: yes[/COLOR]
[B]

iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated  [COLOR="Red"] Tx-Power= off[/COLOR]   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off



**dmesg | grep -i b43**
[    1.498335] b43-pci-bridge 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.290251] b43legacy-phy0: Broadcom 4301 WLAN found
[   13.312064] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   13.312089] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   13.344182] b43legacy-phy0 debug: Radio initialized
[   14.196080] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   14.222665] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   14.242635] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   14.365047] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   14.422660] b43legacy-phy0 debug: Chip initialized
[   14.422870] b43legacy-phy0 debug: 30-bit DMA initialized
[   14.423657] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2B
[   14.423665] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x78
[   14.423672] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2E
[   14.423678] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x19
[   14.423722] b43legacy-phy0 debug: Wireless interface started
[   14.423743] b43legacy-phy0: Radio hardware status changed to DISABLED
[   14.423752] b43legacy-phy0 debug: Radio initialized
[   14.424304] b43legacy-phy0 debug: Adding Interface type 2
[   14.472284] b43legacy-phy0: Radio turned on by software
[   14.472292] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. [COLOR="Red"]Press the button to turn it on.[/COLOR]
[   14.528273] b43legacy-phy0 debug: Removing Interface type 2
[   14.536272] b43legacy-phy0 debug: Wireless interface stopped
[   14.536390] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   14.536435] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   14.536485] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   14.544300] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   14.552285] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   14.560272] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   14.568300] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   14.658741] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   14.764043] b43legacy-phy0 debug: Radio initialized
[   14.764061] b43legacy-phy0 debug: Radio initialized

The red above indicates that there is some switch or key combination that is needed to turn on the wireless.

---

### Post by JayStayPaid9888 on 2010-07-01
Yea, I suspected that may be the issue. But I'm giving Ubuntu a test run on this crappy Dell Dimension E310 desktop and I'm not aware of any hotkey or button combo that unlocks the wifi. I also checked the back of my wifi card and found nothing. Any ideas, fellas? I feel like we're gettin close!

---

### Post by bkratz on 2010-07-01
You might also check the bios and make sure it is on there ( if it is even mentioned). Probably not that though, because I believe it would have shown "soft blocked", but I am really not sure about that (at all!).

---

### Post by purelinuxuser on 2010-07-02
> **JayStayPaid9888 said:**
> Yea, I suspected that may be the issue. But I'm giving Ubuntu a test run on this crappy Dell Dimension E310 desktop and I'm not aware of any hotkey or button combo that unlocks the wifi. I also checked the back of my wifi card and found nothing. Any ideas, fellas? I feel like we're gettin close!

I tried to help a guy with the same problem earlier, I can't remember how it turned out though.

It's possible that b43legacy is misidentifying the RFkill button for your card (if there is any at all).  If so, you'll have to go the ndiswrapper route.  If you already have the appropriate Windows driver installed, you can run
```
modprobe -r b43 ssb ndiswrapper
modprobe ndiswrapper
```

If there are any errors, post them. :)

---

### Post by kplo on 2010-07-08
not sure if the OP has solved the problem, but I am having the exact same problem with the same card right now.  Additional information is that, my card worked (and still works) in 8.04 by using b43-fwcutter and the b43legacy driver from wl_apsta-3.130.20.0.o.  I confirmed that again using the 8.04 live CD, and all I have to do is 1) install b43-fwcutter, 2) sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o.  Doing the same in 10.4 does not work.  Any idea?

---

### Post by chicoharv on 2010-07-08
I might suggest that as long as 8.04 is working , just upgrade to the latest edition by downloading as I did. I know that some packages aren't needed on the upgrade and maybe you won't have a problem that way where you might using the CD or live version.

---

### Post by sirhc1004 on 2010-08-12
I have the same card wireless card (BCM4303)

I found this:
[http://wireless.kernel.org/en/users/Drivers/b43#Known_PCI_devices](http://wireless.kernel.org/en/users/Drivers/b43#Known_PCI_devices)
which suggests that the b43legacy driver supports this card.

However, following the steps in this thread, I ran into nearly identical situations (we might even have the same Dell Dinosaur (BNJ8721?).  I was unable to get the b43legacy driver to work, and currently, I can't get the Ndiswrapper method to work either.

Any suggestions?
@[JayStayPaid9888]("http://ubuntuforums.org/member.php?u=1103107"), did you solve this problem?

---

### Post by sirhc1004 on 2010-09-23
My BCM4303 works with the steps in this thread:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

