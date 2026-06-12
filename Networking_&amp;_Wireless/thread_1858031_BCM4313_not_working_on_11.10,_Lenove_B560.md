---
title: "BCM4313 not working on 11.10, Lenove B560"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by Lazaruss on 2011-10-11
I upgraded to 11.10 last night, into the new kernel. I now can't use my wireless card in my laptop, a Broadcom BCM4313. I have the switch in the network manager applet, which turns off as soon as I turn it on, and is i open network settings it's always in aeroplane mode, but turning it off doesn't help.

lspci output:
```
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Broadcom Corporation Device 0510
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: brcmsmac
	Kernel modules: wl, bcma, brcmsmac

```

There appears to be a block on it in rfkill, but it's under the interface phy0, whereas iwconfig lists wlan0, and before the upgrade it was eth1 (eth0 being my ethernet)

```
samuel@samuel-Lenovo-B560:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
samuel@samuel-Lenovo-B560:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

There's also something in dmesg relating to phy0

```
[  379.925324] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
[  379.925335] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
[  379.925361] ieee80211 phy0: wl0: wlc_wme_setparams : no-clock
[  379.925369] ieee80211 phy0: wl0: wlc_wme_setparams : no-clock
[  379.925374] ieee80211 phy0: wl0: wlc_wme_setparams : no-clock
[  379.925380] ieee80211 phy0: wl0: wlc_wme_setparams : no-clock
[  379.925387] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)

```

I'd be really grateful for any help, i'm checking before filing a bug.

---

### Post by shanepardue on 2011-10-11
I was able to see available wireless connections, but couldn't connect to any of them. I tried to set my IP manually and that worked. I'm not sure if it's the same issue you're having, but it's definitely a bug. My other computers are connecting and getting their IP addresses from the DHCP server.

---

### Post by Lazaruss on 2011-10-12
I can't even see available connections, so I doubt it's the same problem... Are you using the same chipset? If so, which driver?

---

### Post by shanepardue on 2011-10-12
> **Lazaruss said:**
> I can't even see available connections, so I doubt it's the same problem... Are you using the same chipset? If so, which driver?
Strange. Well, I did do a clean install as opposed to an upgrade. I'm running bcm4313 on a Lenovo s10-3

---

### Post by Lazaruss on 2011-10-12
which driver comes up as in use on lspci?

---

### Post by shanepardue on 2011-10-12
brcmsmac

---

### Post by Lazaruss on 2011-10-12
Do you have wl/The broadcom STA drivers installed? I assume not if it's a fresh install...

---

### Post by shanepardue on 2011-10-12
I do now, but I was able to see the wireless networks available before I installed the driver.

---

### Post by Lazaruss on 2011-10-12
I must now confess to my stupidity :(

Managed to disable the wireless card in winblows, rfkill couldn't remove the block. Re-enabled in winblows, works on ubuntu :D

---

### Post by luisremis on 2011-10-22
I have the same problem on ubuntu 11.10 Lenovo v360, BROADCOM 4313.
  I've been searching a lot for a solution but I can't still find one.
  What should I do to make it work?

---

### Post by Lazaruss on 2011-10-22
If you're dual booting with windows, boot into windows and make sure it's fully enabled there...

If it's not working still, can you post your rfkill output, and the relevant section of lspci -v

---

### Post by samadritakarmakar on 2012-01-10
The problem with BCM 4313 is that the kernel loads brcmsmac instead of wl driver which works better with this hardware. Somehow blacklisting brcmsmac in /etc/modprobe.d/blacklist.conf does not work. Adding these lines in /etc/rc.local worked fine for me.

```
rmmod wl
rmmod brcmsmac
depmod
modprobe wl
exit 0
```

---

