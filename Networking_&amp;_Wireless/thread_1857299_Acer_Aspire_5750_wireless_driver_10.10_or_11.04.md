---
title: "Acer Aspire 5750 wireless driver 10.10 or 11.04"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by nettg on 2011-10-10
Hello, in my acer aspire 5750 can't get wireless to work. Tried ubuntu 10.10, 11.04. No wireless networks detected. I tried many kernels from 2.6.38 to 3.0. Currently im running 3.0.0-0300-generic as uname -a reporting.
Hardw details: chipset Intel HM65, ethernet Broadcom NetLink Gigabit Ethernet, wireless Atheros AR5B97
Someone run succesfully AR5B97 on 10.10 or 11.04? If yes using, ath9k or madwifi? Please help.

[SOLVED]
Hi again, I found solution: acer aspire 5750 uses broadcom STA wireless driver, follow this instruction as i did, wireless works ok now:
1. download driver : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) ex: tar xzf <path>/hybrid-portsrc_x86-32_v5.100.82.38.tar.gz
2. # make (When the build completes, it will produce a wl.ko file in the top level directory)
3. remove any other drivers for the Broadcom wireless device: # lsmod  | grep "b43\|ssb\|wl"  If any of these are installed, remove them: # rmmod b43 # rmmod ssb # rmmod wl
4. Insmod the driver: modprobe # lib80211    or  # modprobe ieee80211_crypt_tkip
5. # insmod wl.ko

wl.ko is now operational.  It may take several seconds for the Network  Manager to notice a new network driver has been installed and show the surrounding wireless networks.
here is full instruction: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

good luck

---

### Post by sswittch on 2011-10-18
In the instructions to have the driver start on boot, this didn't work for me.

```
# echo modeprobe wl >> /etc/rc.local  (Fedora/SUSE)
```

I believe it is a typo and should really be

```
# echo modprobe wl >> /etc/rc.local 
```

---

