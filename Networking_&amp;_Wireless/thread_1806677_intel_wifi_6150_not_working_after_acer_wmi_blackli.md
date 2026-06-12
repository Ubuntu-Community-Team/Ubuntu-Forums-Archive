---
title: "intel wifi 6150 not working after acer_wmi blacklist"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by friv_livs on 2011-07-18
```
~$ lsmod | grep acer
~$ rfkill list all
0: ideapad_wlan: Wireless LAN
             Soft blocked: yes
             Hard blocked: no
1: phy0: Wireless LAN
             Soft blocked: yes
            Hard blocked: yes
~$ lsmod | grep wl
iwlagn             284569 0
iwlcore            148965 1 iwlagn
mac80211       257001 2 iwlagn,iwlcore
cfg80211         156212 3 iwlagn,iwlcore,mac80211
```Lenovo Ideapad v570. Have no ethernet connection available, just transferring files.

EDIT: blacklisting ideapad_laptop yieled:
```
~$ rfkill list all
1: phy0: Wireless LAN
             Softblocked: no
             Hardblocked: yes
```Just had to apt-get update from a chroot'ed live distro.

EDIT: unblacklisting ideapad_laptop had no effect on wireless after above step:
```
~$: rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

