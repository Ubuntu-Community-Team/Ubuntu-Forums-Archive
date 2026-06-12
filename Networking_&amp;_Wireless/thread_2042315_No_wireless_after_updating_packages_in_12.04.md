---
title: "No wireless after updating packages in 12.04"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by Rosz777 on 2012-08-14
I use Ubuntu 12.04. Yesterday system asked me about  installing updates. I clicked install update. After that, I don't have  option to connect any connection cause i don't have an option ***wireless network***, only ***network*** or ***mobile network***. This is the output of lspci:




```

martyna@Martyna:~$ lspci 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge 00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) 00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) 00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) 00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5) 00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] 00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller 00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller 00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller 00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller 00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41) 00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40) 00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40) 00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control 00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control 01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] 01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series] 02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```


Please do help, thanks in advance :)

---

### Post by chili555 on 2012-08-14
Please try this:```
sudo modprobe rt2800pci
```Does your wireless spring to life? If so, it's a simple fix. If not, let's see if there are any clues here:```
rfkill list all
dmesg | grep rt2
```

---

### Post by Rosz777 on 2012-08-14
wow, it works! :)

```
martyna@Martyna:~$ sudo modprobe rt2800pci
[sudo] password for martyna: 
martyna@Martyna:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
martyna@Martyna:~$ dmesg | grep rt2
[ 2626.388547] rt2800pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2626.388583] rt2800pci 0000:02:00.0: setting latency timer to 64
[ 2626.619988] Registered led device: rt2800pci-phy0::radio
[ 2626.620094] Registered led device: rt2800pci-phy0::assoc
[ 2626.620152] Registered led device: rt2800pci-phy0::quality
[ 2626.815671] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
martyna@Martyna:~$ 

```

   Is there anything else I should do? 
thank u a lot! :)

---

### Post by chili555 on 2012-08-14
Let's get rt2800pci to load automagically every time:```
sudo su
echo rt2800pci >> /etc/modules
exit
```> rt2800pci_mcu_status: Error - MCU request failed, no response from hardwareI'm not sure I like that but let's see how it goes. Post back if your wireless isn't working properly.

Please use thread tools at the top to mark Solved.

---

### Post by Rosz777 on 2012-09-30
hey, I have the same situation. after updating i have no internet access. command below didn't work. can i please for the help? thank you so much.

```
sudo modprobe rt2800pci
```

---

### Post by chili555 on 2012-09-30
> **Rosz777 said:**
> hey, I have the same situation. after updating i have no internet access. command below didn't work. can i please for the help? thank you so much.

```
sudo modprobe rt2800pci
```Please let us see the usual suspects:```
lspci -nn | grep 0280
rfkill list all
lsb_release -d
```Thanks.

---

### Post by Rosz777 on 2012-10-01
hi, thank for your reply. 

```
martyna@Martyna:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
martyna@Martyna:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
martyna@Martyna:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS
martyna@Martyna:~$ 
```

---

### Post by Rosz777 on 2012-10-01
i must add, that this situations i'snt the same with the previous problem, cause now i have option to switch on and off my wireless card but i can't connect with any network because ubuntu constantly ask me about password. 2 months ago i had the same situation and i added 
```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
```

to [I]etc/modprobe.d/blacklist-rt2x00.conf 
but i checked this and i have this folder now but wireless still doesn't work

thanks for ur help
[/I]

---

### Post by Frederic77 on 2012-10-01
Hi all, I've got the same problem. I updated my lenovo T420S to 12.04 LTS and I'm not given any wireless connection option.

I've tried the command lines above but I don't make progress. Anyone can help?

Thanks in advance!

Frederic

---

### Post by Frederic77 on 2012-10-01
Just to add to the above, this is how far I get in the Terminal:

 frederic@erasmus:~$ sudo modprobe rt2800pci
[sudo] password for martyna: 
frederic@erasmus:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
frederic@erasmus:~$ dmesg | grep rt2

---

### Post by chili555 on 2012-10-01
> **Rosz777 said:**
> i must add, that this situations i'snt the same with the previous problem, cause now i have option to switch on and off my wireless card but i can't connect with any network because ubuntu constantly ask me about password. 2 months ago i had the same situation and i added 
```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
```

to [I]etc/modprobe.d/blacklist-rt2x00.conf 
but i checked this and i have this folder now but wireless still doesn't work

thanks for ur help
[/I]In Ubuntu 12.04, rt2800pci is correct for your device. If you blacklist it, of course you will have no wireless because you will have no driver!! I suggest you remove the file:```
sudo rm /etc/modprobe.d/blacklist-rt2x00.conf
```Now reboot and tell us your symptoms.

---

### Post by chili555 on 2012-10-01
> **Frederic77 said:**
> Hi all, I've got the same problem. I updated my lenovo T420S to 12.04 LTS and I'm not given any wireless connection option.

I've tried the command lines above but I don't make progress. Anyone can help?

Thanks in advance!

FredericDo you have the exact same device?> Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [[COLOR="Red"]1814:3090[/COLOR]]If not, please start a new thread and tell us what you do have:```
lspci -nn | grep 0280
```

---

### Post by Rosz777 on 2012-10-01
nothing changed. my network card constantly ask me about password.

---

### Post by chili555 on 2012-10-01
> **Rosz777 said:**
> nothing changed. my network card constantly ask me about password.Let's try a driver parameter temporarily:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```If it helps, we can write a file and make it persistent.

---

### Post by Rosz777 on 2012-10-01
It did not help. After first command wireless card switched off, after second command it is still asking for pass...

---

### Post by scwogit on 2012-10-03
A while ago I updated my ubuntu and since then I've been experiencing problems with rt2800 as I can see some of you have as well. However my problem is that it clocks out after having a few webpages open or sometimes gives up on the one webpage, however it remains connected to the wireless but inactive. 

Would be grateful if anyone could point me in the right direction.

I have read few things on thread, I've added this to the bottom if it helps.

code:
[PHP]gnat@gnat-nForce-750i-SLI:~$ lspci -nn | grep 0280
06:0a.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
gnat@gnat-nForce-750i-SLI:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
gnat@gnat-nForce-750i-SLI:~$ lsb_release -d
Description:	Ubuntu 12.04.1 LTS
gnat@gnat-nForce-750i-SLI:~$ modprobe -l | grep rt2800
kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
gnat@gnat-nForce-750i-SLI:~$ lsmod
Module                  Size  Used by
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48805  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
snd_seq_dummy          12686  0 
nls_utf8               12493  1 
udf                    84466  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
vesafb                 13516  1 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
binfmt_misc            17292  1 
snd_hda_intel          32765  7 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
hid_roccat_kone        17598  0 
snd_seq_midi           13132  0 
hid_roccat             13253  1 hid_roccat_kone
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
snd                    62064  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nv_tco                 13399  0 
soundcore              14635  1 snd
i2c_nforce2            12906  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
fglrx                2909855  234 
mac_hid                13077  0 
serio_raw              13027  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
usbhid                 41906  0 
hid                    77367  2 hid_roccat_kone,usbhid
crc_itu_t              12627  2 udf,firewire_core
forcedeth              58096  0 
pata_amd               13750  0 
sata_nv                23360  3 
floppy                 60310  0
[/PHP]

---

### Post by chili555 on 2012-10-04
> **scwogit said:**
> A while ago I updated my ubuntu and since then I've been experiencing problems with rt2800 as I can see some of you have as well. However my problem is that it clocks out after having a few webpages open or sometimes gives up on the one webpage, however it remains connected to the wireless but inactive. 

Would be grateful if anyone could point me in the right direction.

Is this a virtual machine by any chance?

---

### Post by scwogit on 2012-10-04
No this is my home PC I have XP on one hard drive and ubuntu on another hard drive.

If it helps I have a 'ciso linksys dual-band wireless-n pci adapter'. how ever I've tried downloading drivers for windows and using them on ubuntu but I seemed to get no where.

a few months ago it worked fine and then suddenly it decided just to start to clock out after so much data was being transferred over the internet e.g. when I'm downloading anything it just stops. I have to disconnect and reconnect. 

I will just mention I have no problem with the rooter on my laptop nor does any of my family on there own computers.

So I'm a little stuck.

---

### Post by chili555 on 2012-10-04
> vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt This all had me wondering. Wireless on a virtual machine is not generally possible.

Let's troubleshoot a bit. Please run and post:```
nm-tool
dmesg | grep -e rt2 -e wlan
```Also, let's try a driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```Any improvement?

---

### Post by scwogit on 2012-10-04
Ran them this is what I get. When I came to the driver parameter thing it turned my wireless off on the first line and then on on the second line.


After looking at what came up I forgot to mention another weird thing network is called caroline but I have a list of caroline 1 - caroline 2 and caroline 3, I'm not 100% sure on how these came about but just adding that incase it helps. however it doesn't allow me to join a just 'caroline' like I do my laptop.

[PHP]gnat@gnat-nForce-750i-SLI:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:1F:BC:07:A5:F6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [caroline 3] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        68:7F:74:BC:71:EE

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *caroline:       Infra, 4C:17:EB:B8:A1:0C, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


gnat@gnat-nForce-750i-SLI:~$ dmesg | grep -e rt2 -e wlan
[   16.571443] rt2800pci 0000:06:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   16.571453] rt2800pci 0000:06:0a.0: setting latency timer to 64
[   16.631055] Registered led device: rt2800pci-phy0::radio
[   16.631077] Registered led device: rt2800pci-phy0::assoc
[   16.631102] Registered led device: rt2800pci-phy0::quality
[   17.380238] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[   17.404813] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.406687] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.908112] wlan0: authenticate with 4c:17:eb:b8:a1:0c (try 1)
[   23.909641] wlan0: authenticated
[   23.909837] wlan0: associate with 4c:17:eb:b8:a1:0c (try 1)
[   23.912917] wlan0: RX AssocResp from 4c:17:eb:b8:a1:0c (capab=0x411 status=0 aid=5)
[   23.912921] wlan0: associated
[   23.920272] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.080008] wlan0: no IPv6 routers present
gnat@gnat-nForce-750i-SLI:~$ sudo modprobe -r rt2800pci
[sudo] password for gnat: 
gnat@gnat-nForce-750i-SLI:~$ sudo modprobe rt2800pci nohwcrypt=Y
gnat@gnat-nForce-750i-SLI:~$ 
[/PHP]

however no improvement, btw thanks for your continuous help.

---

### Post by chili555 on 2012-10-07
> rt2800pci_mcu_status: Error - MCU request failed, no response from hardwareOuch!! 

Please see: [https://bbs.archlinux.org/viewtopic.php?id=136607](https://bbs.archlinux.org/viewtopic.php?id=136607)

The same error is mentioned and a patch is available. I suspect the patch has made it to the backports modules. Please do:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic
```Reboot and let us see again:```
dmesg | grep rt2
```

---

### Post by scwogit on 2012-10-08
[PHP]gnat@gnat-nForce-750i-SLI:~$ dmesg | grep rt2
[   18.334834] rt2800pci 0000:06:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   18.334841] rt2800pci 0000:06:0a.0: setting latency timer to 64
[   18.345372] Registered led device: rt2800pci-phy0::radio
[   18.345396] Registered led device: rt2800pci-phy0::assoc
[   18.345417] Registered led device: rt2800pci-phy0::quality
[   19.100167] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
gnat@gnat-nForce-750i-SLI:~$ [/PHP]


That problem seems to have displayed again, and after testing the internet it still seems to be clocking out.

Also read the thread you linked to and it's one that i have found in the past but found no luck. However I'm sure it was longer last time I viewed it.

---

### Post by chili555 on 2012-10-09
Please try two things:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```Any change in behavior? If not, reload the default:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
```Now try:```
sudo iwconfig wlan0 power off
```In this case, 'power' refers to power management. Any change?

---

### Post by scwogit on 2012-10-09
Sadly no change although both methods still allow the internet to connect it still chocked out. I also ran the previous thing and it still displays the same message. and for the 'sudo iwconfig wlan0 power off ' I can't see a difference but it's not made it worse, should I just leave that off.

---

### Post by chili555 on 2012-10-11
> **scwogit said:**
> Sadly no change although both methods still allow the internet to connect it still chocked out. I also ran the previous thing and it still displays the same message. and for the 'sudo iwconfig wlan0 power off ' I can't see a difference but it's not made it worse, should I just leave that off.I'm afraid to report that I have no further ideas. Sorry.

Would you care to swap your wireless card and let's see if we can make it work?> If it helps I have a 'ciso linksys dual-band wireless-n pci adapter'If so, after it's in place, run and post:```
lspci -nn | grep 0280
```

---

### Post by scwogit on 2012-10-12
Thanks for your help anyway, I'm thinking of reinstalling ubuntu an seein if that sorts it out. Will let you know how well that goes. sadly my wireless card is the best I've ever had an always has a great signal so I'm not really looking to chuck it out.

---

### Post by scwogit on 2012-10-15
I have reinstalled ubuntu onto my computer however this hasn't fixed the problem. Is there anyway of turning the current driver off and using the one that cisco create for windows?

---

### Post by chili555 on 2012-10-15
> **scwogit said:**
> I have reinstalled ubuntu onto my computer however this hasn't fixed the problem. Is there anyway of turning the current driver off and using the one that cisco create for windows?If this is a PCI device, aren't you going to physically remove the Realtek and replace it with the Cisco? If so, the Realtek driver simply won't load. Then please post:```
lspci -nn | grep 0280
```There may be another way to get the Cisco going aside from the Windows driver.

---

### Post by scwogit on 2012-10-15
hey okay so I did some messing around anyway and followed this video to an extent... [http://www.youtube.com/watch?v=wchimaoe9KE&feature=endscreen](http://www.youtube.com/watch?v=wchimaoe9KE&feature=endscreen) ...  however every time I log into my computer I know have to use ... ```
sudo modprobe rt2800pci 
``` in terminal to start the internet. Once on the internet I find it to be very laggy and slow but I haven't found any problems with it chocking out which is an improvement I guess. 

Okay so first off I ran the query in your most recent post 'lspci -nn | grep 0280', after that I ran various other things which might happen in the new circumstance.  ( I will just mention it still shows that error ```
rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
``` and yesterday I ran the patch mentioned earlier in the 3rd page so that hasn't made any difference to it.

```
gnat@gnat-nForce-750i-SLI:~$ lspci -nn | grep 0280
06:0a.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
gnat@gnat-nForce-750i-SLI:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
gnat@gnat-nForce-750i-SLI:~$ dmesg | grep rt2
[ 1064.699631] rt2800pci 0000:06:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[ 1064.699639] rt2800pci 0000:06:0a.0: setting latency timer to 64
[ 1064.763736] Registered led device: rt2800pci-phy0::radio
[ 1064.763758] Registered led device: rt2800pci-phy0::assoc
[ 1064.763795] Registered led device: rt2800pci-phy0::quality
[ 1064.820199] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
gnat@gnat-nForce-750i-SLI:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [caroline] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        68:7F:74:BC:71:EE

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *caroline:       Infra, 4C:17:EB:B8:A1:0C, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:1F:BC:07:A5:F6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


gnat@gnat-nForce-750i-SLI:~$ dmesg | grep -e rt2 -e wlan
[ 1064.699631] rt2800pci 0000:06:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[ 1064.699639] rt2800pci 0000:06:0a.0: setting latency timer to 64
[ 1064.763736] Registered led device: rt2800pci-phy0::radio
[ 1064.763758] Registered led device: rt2800pci-phy0::assoc
[ 1064.763795] Registered led device: rt2800pci-phy0::quality
[ 1064.820199] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[ 1064.844336] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1064.844735] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1071.352118] wlan0: authenticate with 4c:17:eb:b8:a1:0c (try 1)
[ 1071.353541] wlan0: authenticated
[ 1071.353675] wlan0: associate with 4c:17:eb:b8:a1:0c (try 1)
[ 1071.356749] wlan0: RX AssocResp from 4c:17:eb:b8:a1:0c (capab=0x411 status=0 aid=6)
[ 1071.356753] wlan0: associated
[ 1071.356757] wlan0: moving STA 4c:17:eb:b8:a1:0c to state 1
[ 1071.356760] wlan0: moving STA 4c:17:eb:b8:a1:0c to state 2
[ 1071.364265] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1071.381506] wlan0: moving STA 4c:17:eb:b8:a1:0c to state 3
[ 1081.968009] wlan0: no IPv6 routers present
gnat@gnat-nForce-750i-SLI:~$ 

```

---

