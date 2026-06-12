---
title: "New wireless network card not working"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by chrisc200 on 2012-02-11
I am using ubuntu 11.10

I bought a new network card (cardbus) adapter which was recommended on a "well supported network cards site list" which I also want to use as an access point with hostapd.

Card is a netgear range max wpn 511.

However, the driver for this card should be using the ath9k driver but it insists on using the ath5k driver, which does not support wireless n speeds.

How can I force it to use the ath9k driver? 

I installed compat-wireless which updated all the drivers but it still uses the ath5k driver and only supports b,g modes from iwconfig.

I tried removing module with modprobe, and loading the ath9k driver (which I have) but then the wireless completely breaks.

Appreciate any help as I have been trying to get this working for days.

Here is some info which maybe useful:

 *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 01
       serial: 00:14:6c:15:ce:e9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-15-generic firmware=N/A latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:88000000-8800ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  Mode:Master  Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

lsmod | grep -i ath

ath5k                 142867  0 
ath                    19148  1 ath5k
mac80211              384409  1 ath5k
cfg80211              166959  3 ath5k,ath,mac80211


modprobe -r ath5k

$ lsmod | grep -i ath

ath9k                 110898  0 
mac80211              384409  1 ath9k
ath9k_common           13599  1 ath9k
ath9k_hw              290518  2 ath9k,ath9k_common
ath                    19148  2 ath9k,ath9k_hw
cfg80211              166959  3 ath9k,mac80211,ath


iwconfig

andrea@andrea-Latitude-D430:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

---

### Post by bogan on 2012-02-11
Hi! **chrisc200**,

I can not claim any knowledge of athxk drivers or your wpn511 WiFi card, but if they are at all like Ralink or Realtek cards and their drivers, this sort of problem is dealt with by blacklisting the one you want to prevent loading or being  used.

Check /etc/modprobe.d/blacklist.conf.
 If the file does not exist you will need to make one.
Enter: blacklist ath5k and save. ```
gksu gedit /etc/modprobe.d/blacklist.conf
``` Add the line: 
blacklist ath5k
Save and re-boot.

If it does not work, at least your Thread will be updated.

Chao!,** bogan**.

Ed: code line added

---

### Post by praseodym on 2012-02-11
Hi,

the compat-wireless drivers update ath5k amd ath9k, respectively. Alternatively, you can try the driver from the madwifi project. Blacklisting the driver alone will not work. You should deactivate the ath5k drivers' hardware encryption,

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
```
deactivate the power management,
```
sudo iwconfig wlan0 power off
```
take the ath5k from the blacklist again, and reboot.

---

### Post by chrisc200 on 2012-02-12
Thanks for the replies, I tried the methods suggested, but after blacklisting the ath5k driver and rebooting iwconfig still shows "no wireless extensions".

Ubuntu offered me to try the madwifi driver but I had big performance issues getting this working with hosapd.

Not sure what to try next.. I cant see any error messages when I load the driver manually with modprobe -v ath9k I get no error messages, but in lsmod it shows "0" next to ath9k.

---

### Post by praseodym on 2012-02-12
ath9k will not work with this card. ath5k is needed.

---

### Post by chrisc200 on 2012-02-12
So does this mean I cannot use wireless N capabilities on this card? When for example I tried setting HT capabilities and enabling wireless N in hostapd, it failed. From reading around forums, it implies I need to be using the ath9k driver for this card and not the ath5k.

Basically my issue is I have a sony DNLA box, and I connect it to my wifi with wireless access point using hostapd. I was noticing bad performance on my old card so I got this new card. 

Any other suggestions/workarounds? 

thanks

---

### Post by praseodym on 2012-02-12
Maybe its a downgraded card which normally is used in notebooks? Most of the time the manufacturers sell those for lower prices?!

---

### Post by chrisc200 on 2012-02-12
Yes it is for a notebook, not sure what to do other than trying another card.

---

