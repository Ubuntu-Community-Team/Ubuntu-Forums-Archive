---
title: "hp-500 no wireless (noob)"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by learnr4lyf on 2012-12-19
hello every one.i just recently installed ubuntu 12.04 as the only os on my comps and it works well except i cannot connect to the internet. i can access info on wired and vpn but not on wireless. i can access the network on any other computer but the ubuntu.

i've done a rfkill list all (from searching the threads)and got this result:

0: hp-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 

please, any help would be greatly appreciated. i'm not even able to click on enable wireless :S

---

### Post by chili555 on 2012-12-19
I suspect the needed driver or firmware for your wireless is missing. Let's see what you need. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by learnr4lyf on 2012-12-19
> **chili555 said:**
> I suspect the needed driver or firmware for your wireless is missing. Let's see what you need. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

thanks so much. this is what i'm getting:

02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

---

### Post by chili555 on 2012-12-19
The driver ipw2200 is present in 12.04 and your wireless should work perfectly. Let's do some diagnostics:```
sudo modprobe ipw2200
iwconfig
dmesg | grep ipw
nm-tool
```Thanks.

---

### Post by learnr4lyf on 2012-12-19
these are the results:

iwconfig 
lo        no wireless extensions. 
 
eth1      IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Channel:0  Access Point: Not-Associated    
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0   
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
eth0      no wireless extensions. 
 
grace@grace-HP-500-Notebook-PC-RW860AA-ACH:~$ dmesg | grep ipw 
[   15.074654] libipw: 802.11 data/management/control stack, git-1.1.13 
[   15.074658] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com> 
[   15.146189] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq 
[   15.146194] ipw2200: Copyright(c) 2003-2006 Intel Corporation 
[   15.560239] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[   15.560271] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection 
[   16.310685] ipw2200: Radio Frequency Kill Switch is On: 
[   16.328298] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels) 
[   18.256047] ipw2200: Failed to send POWER_MODE: Command timed out. 
[   21.328053] ipw2200: Failed to send POWER_MODE: Command timed out. 
[ 1826.472057] ipw2200: Failed to send POWER_MODE: Command timed out. 
[ 1830.555535] ipw2200 0000:02:04.0: PCI INT A disabled 
[ 1831.216839] ipw2200 0000:02:04.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b) 
[ 1831.216861] ipw2200 0000:02:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0000000) 
[ 1831.216868] ipw2200 0000:02:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x4010) 
[ 1831.216875] ipw2200 0000:02:04.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900006) 
[ 1831.310581] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[ 1831.444019] ipw2200: Radio Frequency Kill Switch is On: 
[ 1837.008085] ipw2200: Failed to send POWER_MODE: Command timed out. 
grace@grace-HP-500-Notebook-PC-RW860AA-ACH:~$ nm-tool 
 
NetworkManager Tool 
 
State: disconnected 
 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            e100 
  State:             unavailable 
  Default:           no 
  HW Address:        00:16:D4:A2:97:CD 
 
  Capabilities: 
    Carrier Detect:  yes 
 
  Wired Properties 
    Carrier:         off 
 
 
- Device: eth1 ----------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            ipw2200 
  State:             unavailable 
  Default:           no 
  HW Address:        00:16:6F:C4:0C:77 
 
  Capabilities: 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points

---

### Post by chili555 on 2012-12-19
>  ipw2200: Radio Frequency Kill Switch is On: Now it looks like the wireless switch is set to disable wireless. When you started the thread,you said:```
0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: no[/COLOR] 
```In this instance, 'hard' means the hardware switch.

So is the switch on or off? Is there an LED that changes as you press a button? Is there a key combination; Fn+Fsomething?

---

### Post by learnr4lyf on 2012-12-19
its on. idk what's happening

---

### Post by learnr4lyf on 2012-12-19
the light is on and i get the same message of hard and soft blocked all say no.

---

### Post by chili555 on 2012-12-19
> **learnr4lyf said:**
> idk what's happeningYou and me, both! However, let's keep digging.```
md5sum /lib/firmware/ipw22*
dmesg | grep -i -e 02:04 -e error
```Thanks.

---

### Post by learnr4lyf on 2012-12-19
md5sum /lib/firmware/ipw22* 
045a46163341514ef17490c76bd0c858  /lib/firmware/ipw2200-bss.fw 
44cdedc8d5a0eb727466ed982db97a53  /lib/firmware/ipw2200-ibss.fw 
ebc70dce66f876695fa8852b8ff757ee  /lib/firmware/ipw2200-sniffer.fw 
grace@grace-HP-500-Notebook-PC-RW860AA-ACH:~$ mdesg | grep -i -e 02:04 -e error 
No command 'mdesg' found, did you mean: 
 Command 'mesg' from package 'orville-write' (universe) 
 Command 'mesg' from package 'sysvinit-utils' (main) 
 Command 'dmesg' from package 'util-linux' (main) 
mdesg: command not found 
grace@grace-HP-500-Notebook-PC-RW860AA-ACH:~$ dmesg | grep -i -e 02:04 -e error 
[    0.108602] pci 0000:02:04.0: [8086:4220] type 0 class 0x000280 
[    0.108628] pci 0000:02:04.0: reg 10: [mem 0xd0000000-0xd0000fff] 
[    0.108742] pci 0000:02:04.0: PME# supported from D0 D3hot D3cold 
[    0.108748] pci 0000:02:04.0: PME# disabled 
[   14.943172] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro 
[   15.560239] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[ 1830.555535] ipw2200 0000:02:04.0: PCI INT A disabled 
[ 1831.216839] ipw2200 0000:02:04.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b) 
[ 1831.216861] ipw2200 0000:02:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0000000) 
[ 1831.216868] ipw2200 0000:02:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x4010) 
[ 1831.216875] ipw2200 0000:02:04.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900006) 
[ 1831.310581] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[ 1834.862222] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id 


u're pretty good at this. most is giberish to me :(

---

### Post by learnr4lyf on 2012-12-19
so guess what? i'm now posting this from my ubuntu YAY!! so what i did was disable networking, and re-enabled it, and it allowed me to connect #facepalm. THANKS SOOOOOO MUCH for ur help.

i am now going to install chromium. and continue to search out the forums for more advice on customizing and helping others where i can. thanks again so much!! i really appreciate it :)

---

### Post by chili555 on 2012-12-19
One thing we see is that you have the needed firmware and, according to md5sum, it's not corrupted. We also see no complaints about needing and not finding firmware. We are still troubled by:> [ 16.310685] ipw2200: [COLOR="Red"]Radio Frequency Kill Switch is On:[/COLOR]
[ 16.328298] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[ 18.256047] ipw2200: [COLOR="Red"]Failed to send POWER_MODE: Command timed out.[/COLOR]
[ 21.328053] ipw2200: Failed to send POWER_MODE: Command timed out.
[ 1826.472057] ipw2200: Failed to send POWER_MODE: Command timed out.
[ 1830.555535] ipw2200 0000:02:04.0: PCI INT A disabled We are very low on skill/ideas/mojo. Please try:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
sudo modprobe -r ipw2200
sudo modprobe ipw2200
sudo iwlist eth1 scan
```Any warnings or errors may be informative; please post any you see.

---

### Post by learnr4lyf on 2012-12-19
imma do the codes still until all clear up. the computer is moving slowly so i'm back on the other one :(

---

### Post by learnr4lyf on 2012-12-19
ethl       Interface doesn't support scanning.

and net is gone again. in fact i see nothing no wireless at all. as if it doesn't exist. did the same thing i did again, but it doesn't work.

---

### Post by chili555 on 2012-12-19
Alrighty then. Reboot and then let's see:```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by learnr4lyf on 2012-12-19
did it again, realized i made a mistake. here r the scan results:

eth1      Scan completed : 
          Cell 01 - Address: 00:15:D0:99:6F:C2 
                    ESSID:"arris54g" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Frequency:2.462 GHz (Channel 11) 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality=93/100  Signal level=-36 dBm   
                    Extra: Last beacon: 8ms ago 

and i am also once again connected to wireless network.

---

### Post by learnr4lyf on 2012-12-19
saw ur last message late (sorry) so i didn't reboot r follow those instructions. awaiting response now :$

---

### Post by chili555 on 2012-12-20
Your wireless seems to start and stop for no reason I can see or even imagine. Every place I Google about 'Failed to send POWER_MODE: Command timed out' seems to be resolved by turning on the wireless switch. Your wireless switch isn't turned off and *rfkill list all* so far never reports your wireless as hard blocked. I am down to four thoughts:

# The wireless card might be defective;

# The wireless card may not be completely and correctly seated in its slot;

# The switch may be defective; or

# I don't have any more ideas.

Unless there are any new clues, I'm afraid I have nothing else to offer.

---

### Post by learnr4lyf on 2012-12-23
My deepest apologies about the late reply. I'm not sure what's been happening, but thank you so much for your help. I hope it won't be a problem in the future. The wireless seems to work fine now for the most part, connecting and finding networks quickly.

One of the suggestions you made as to why it was giving these results could be very well the case though, as a few months ago the computer fell off a table and the hardware was not properly checked. Maybe the wireless card got dislodged somehow, but not enough to make me totally unable to connect.

Again, thanks so much for your help.

---

### Post by chili555 on 2012-12-24
No apology needed. I understand that people have full and rich lives outside of their computers. I just wish I did, too.

I am glad it is working well enough now.

---

