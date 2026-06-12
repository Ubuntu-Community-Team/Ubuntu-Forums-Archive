---
title: "Wireless not working in  2.6.35-22 header image"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by yourbuddyrohan on 2010-10-22
After upgrading to 2.6.35-22 header image, I am not able to turn on my wireless driver. However when I boot with 2.6.32.25 header image, wireless works fine.

```
$ sudo lsmod  | grep iwl
iwl3945                68727  0 
iwlcore               106050  1 iwl3945
mac80211              205402  2 iwl3945,iwlcore
cfg80211              126496  3 iwl3945,iwlcore,mac80211
led_class               2864  3 iwl3945,iwlcore,sdhci

```
Tried the steps in this post [http://drupal.txwikinger.me.uk/content/ubuntu-maverick-wireless-interface-not-connecting](http://drupal.txwikinger.me.uk/content/ubuntu-maverick-wireless-interface-not-connecting) but to no avail. 

Please help.

---

### Post by yourbuddyrohan on 2010-10-25
Tried below command but got error
> sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

please help

---

### Post by yourbuddyrohan on 2010-10-28
<Bump>

---

### Post by yourbuddyrohan on 2010-10-28
Found this post, which seems to resolve the issue [http://ubuntuforums.org/showthread.php?p=9942551#post9942551](http://ubuntuforums.org/showthread.php?p=9942551#post9942551)

---

