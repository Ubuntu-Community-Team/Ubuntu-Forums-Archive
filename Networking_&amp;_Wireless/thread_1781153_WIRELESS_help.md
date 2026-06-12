---
title: "WIRELESS help"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by midnightman1 on 2011-06-13
Hello! 
I need some assistance! - I'm not computer savvy at all - a friend just  installed Ubuntu onto my laptop and I can't get the WIRELESS to work.  can anyone give me a hand?
I'm not sure what info you need so let me know...

---

### Post by goldshirt9 on 2011-06-13
post us some info
what version of ubuntu.
laptop type and what ever spec's you can tell us.
the more the better
wireless router model as well

---

### Post by midnightman1 on 2011-06-13
Thank you, i got some info here:

Version Ubuntu : 10.04

Laptop type: Compaq - Presario CQ50 
                                - AMD, Athlon X264, NVIDIA Graphics, - it came with Windows Vista.

That's all the info I could see...

---

### Post by chili555 on 2011-06-13
Please go to Applications > Accessories > Terminal and run and post:```
lspci -nn
```That's a lower-case L there, not a one.

Feel free to strip away everything that you think is not your wireless card. Do you have an ethernet connection if we need to download something?

---

### Post by midnightman1 on 2011-06-16
hey there, I input the lspci and got this:

 00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2) 
  00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2) 
  00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1) 
  00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2) 
  00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1) 
  00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) 
  00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) 
  00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) 
  00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) 
  00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) 
  00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1) 
  00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) 
  00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) 
  00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2) 
  00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1) 
  00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) 
  00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40) 
  00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map 
  00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller 
  00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control 
  00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control 
  02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2) 
  07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by chili555 on 2011-06-16
> Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)Your device uses the well-supported ath5k module. Let's load it:```
sudo modprobe ath5k
```Does your wireless work? If not, please post:```
dmesg | grep ath5k
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by midnightman1 on 2011-06-16
Hey there, I input the 1st one the sudo modprode ath5k and then entered my password when it requested it, but nothing happened, so i entered the second one the - "dmesg" one and then this came out:

                     p { margin-bottom: 0.21cm; }  [   12.148924] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23  
 [   12.148939] ath5k 0000:07:00.0: setting latency timer to 64  
 [   12.148983] ath5k 0000:07:00.0: registered as 'phy0'  
 [   12.785736] Registered led device: ath5k-phy0::rx  
 [   12.785755] Registered led device: ath5k-phy0::tx  
 [   12.785759] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)


and nope the wireless hasn't started working yet...

---

### Post by chili555 on 2011-06-16
> I input the 1st one the sudo modprode ath5k and then entered my password when it requested it, but nothing happenedThat simplty means, "Command executed with no errors or warnings to report, sir!" There was no response expected, so that's good.> [ 12.148939] ath5k 0000:07:00.0: setting latency timer to 64
[ 12.148983] ath5k 0000:07:00.0: registered as 'phy0'
[ 12.785736] Registered led device: ath5k-phy0::rx
[ 12.785755] Registered led device: ath5k-phy0::tx
[ 12.785759] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

The time-stamps, in the 12s, indicate the module was loaded during boot as expected. More good news. Now we wonder why the wireless doesn't work. Please run and post:```
dmesg | grep wlan
rfkill list all
```Thanks.

---

### Post by midnightman1 on 2011-06-19
Hi chilli,
I input the: 

dmesg | grep wlan
rfkill list all

then this stuff came out: 

midnightman@midnightman-laptop:~$ dmesg | grep wlan
[   14.409249] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  238.393385] ADDRCONF(NETDEV_UP): wlan0: link is not ready
midnightman@midnightman-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by chili555 on 2011-06-19
> $ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]That strongly suggests that the wireless switch or key combination has the wireless switched off. Can you please find and press the switch?

---

### Post by midnightman1 on 2011-06-19
yeah the switch is just a button on my computer.
when i was using windows vista on here - orange meant off and blue meant on. it's been on blue since i put ubuntu on this computer. i press it, but i can't tell if it changes anything or not.

---

### Post by chili555 on 2011-06-19
Press it and run:```
rfkill list all
```Press it again and check again. When you get to 'hard blocked no,' your wireless should be working. If that doesn't do it, post back and we'll dig deeper.

---

### Post by midnightman1 on 2011-06-19
yeah i input that and this came out:


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2011-06-19
And so do networks show up in Network Manager? Can you click and connect?

---

### Post by midnightman1 on 2011-06-19
If I left click on the Network Manager when the cord is unplugged and hit "refresh" it says there's "no wireless networks found" and when I left click over the wireless tracker it says "Wireless Networks Wireless is disabled"

---

### Post by TheDoctorX on 2011-06-19
try to update yor network manager ... for me that magica thing worked

---

### Post by TheDoctorX on 2011-06-19
> **TheDoctorX said:**
> try to update yor network manager ... for me that magica thing worked

some times happendz that the network manager works bad and when u update it begins to work great!! on my computer worked .. eeepc asus

---

### Post by chili555 on 2011-06-19
> **midnightman1 said:**
> If I left click on the Network Manager when the cord is unplugged and hit "refresh" it says there's "no wireless networks found" and when I left click over the wireless tracker it says "Wireless Networks Wireless is disabled"If it is happening when the cord is unplugged, it is likely a power management issue. You might try the solution in post #2 here:  [http://ubuntuforums.org/showthread.php?t=1686641](http://ubuntuforums.org/showthread.php?t=1686641)

---

### Post by midnightman1 on 2011-06-20
alright so how do i upgrade my network manager?

---

### Post by midnightman1 on 2011-06-20
and hey chilli,. I did what you suggested and used post #2 of the page you suggested - yeah didn't seem to make a difference..

---

### Post by chili555 on 2011-06-20
I'm sorry, I have no further suggestions.

---

