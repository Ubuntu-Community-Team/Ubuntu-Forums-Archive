---
title: "Ubuntu 11.10 cant use rt2860sta"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by sigend on 2012-01-10
Hello!!I have a Ralink corp pci wireless card!It uses the rt2760 chip.Since kernel 3.0.0-12 i can't connect to wireless networks and when I rarely do it is highly unstable and causes my router to crash!

I ve tried installing the rt2860sta driver from Ralink's site using various instractions around the net but nothing seems to be working..:(  

also tried to blacklist the rt2800pci driver but when i do

if i have also installed the rt2860sta driver it crashes my router

if i haven't installed anything else i just doesn't find anything (meaning wlan0 or ra0).


plz someone  help me!!!:):)



> spyros@spyros-132-CK-NF78:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:"Sigend's wireless router"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:22:6B:F0:7B:DC   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-48 dBm  Noise level:-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0





> spyros@spyros-132-CK-NF78:~$ sudo lspci -k

......
05:09.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus
	Subsystem: Ralink corp. Device 2760
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta, rt2800pci



> spyros@spyros-132-CK-NF78:~$ modinfo rt2860sta
filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2860sta.ko
license:        GPL
version:        2.4.0.0
srcversion:     65223B8B7D9C2800C048813
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       3.0.0-14-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)



> spyros@spyros-132-CK-NF78:~$ lsmod | grep rt28
rt2860sta             864748  1 

---

