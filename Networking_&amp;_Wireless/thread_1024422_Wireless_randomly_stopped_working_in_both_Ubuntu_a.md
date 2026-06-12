---
title: "Wireless randomly stopped working in both Ubuntu and Vista"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Zetorux on 2008-12-29
Hi, I am using a Toshiba laptop (Satellite L305D-S5893), and recently my wireless card stopped working in both Ubuntu 8.10 and Vista.  I don't know exactly what happened, but one of the last things I remember doing over the wireless network was installing the recommended software/security updates for Ubuntu 8.10.  The next time I used the laptop, the wireless device wasn't working.

About a month ago, I originally got my wireless working by following the instructions on [this page](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/).  It had been working fine until just recently.

I tried going through the process once again, but that didn't fix the problem.  I don't believe the problem has anything to do with the wireless network in my house because I am not able to detect my neighbor's network anymore either.

The wireless switch on my laptop is on.

Here is the output of a few potentially relevant commands:

```
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```
```
~$ iwlist wlan0 scanning
wlan0     No scan results

```
```
~$ dmesg | grep ath
[   23.856782] ath5k_pci 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   23.856794] ath5k_pci 0000:04:00.0: setting latency timer to 64
[   23.856827] ath5k_pci 0000:04:00.0: registered as 'phy0'
[   24.195847] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   37.592145] ath5k phy0: gain calibration timeout (2412MHz)
[   37.592165] ath5k phy0: can't reset hardware (-11)
[   37.937874] ath5k phy0: gain calibration timeout (2412MHz)
[   37.937894] ath5k phy0: can't reset hardware (-11)

```
```
$ uname -a
Linux rofl 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
```
```
$ cat /etc/issue
Ubuntu 8.10 \n \l

```

And I've copied the output of [sudo lshw](http://pastebin.com/f5f9e9678) and [lsmod](http://pastebin.com/f48c04d71) to pastebin.


Vista detects the wireless card as an Atheros ar5007eg.  I tried updating the drivers in Vista as well, but this did not help.  Vista reacts to the wireless switch and will notify me if I switch it off, but it can no longer detect any of the nearby wireless networks.  The problem seems to be the same in both operating systems.


I'm still somewhat new to networking, so I'm not sure what to do or where the problem could possibly lie.  Can anybody point me in the right direction?

---

### Post by Tak11 on 2009-02-16
I have the same issue, 
lspci:
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


System Info:
os[Linux 2.6.27-11-generic i686] 
distro[Ubuntu "intrepid" 8.10] 
cpu[2xIntel(R) Core(TM)2 Duo CPU T5450 @ 1.66GHz (GenuineIntel) @ 1.66GHz] 
mem[Physical: 3.0GB, 72.3% free] 
disk[Total: 223.0GB, 15.7% free] 
video[nVidia Corporation GeForce 8800M GTS] 
sound[HDA-Intel - HDA Intel]

---

### Post by abreiner on 2009-02-28
I just got

[   67.954926] ath5k phy0: gain calibration timeout (2412MHz)
[   67.954938] ath5k phy0: can't reset hardware (-11)

On kerneltrap it suggested doing a suspend to ram.  After I did that it starting working again.  I don't know why it stopped working.  I haven't done any updating.  The only thing I can think of is NetworkManager was trying to connect and I issued a iwlist scanning at the same time.  I don't know if this confused it or what.  Just letting you know that a suspend to ram worked to fix it.

Andy B.

---

### Post by sqb on 2009-03-02
Same symptoms, but doing a suspend fixed it. :guitar: Thanks!

---

