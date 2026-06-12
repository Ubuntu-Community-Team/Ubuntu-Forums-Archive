---
title: "Unable to connect to wireless"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by mfrna86-x on 2013-08-29
Hi,

I have a lenovo T410 and  have just install 13.04 on it.

My problem is as follows, when my pc comes back from suspend it doesn't connect to my home wireless.
it connects fine to my office wireless after suspend and connects fine t my home wireless upon first boot or after reboot.

Attached is my wireless info as extracted by 
wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script

---

### Post by praseodym on 2013-09-01
Please show the outputs of this command:
```

lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```

---

### Post by mfrna86-x on 2013-09-01
Hi [COLOR=#000000]praseodym,
[/COLOR]
```

mfarag@mfarag-php-T410:~$ lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv'
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
mac80211              606457  2 rtlwifi,rtl8192se
cfg80211              510937  2 mac80211,rtlwifi
mac_hid                13205  0 
sdhci_pci              18590  0 
firewire_ohci          40103  0 
sdhci                  32522  1 sdhci_pci
firewire_core          64508  1 firewire_ohci



```

---

### Post by praseodym on 2013-09-01
Try:
```

sudo touch /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module
gksudo gedit /etc/pm/config.d/00sleep_module
```
Insert:
```
SUSPEND_MODULES="$SUSPEND_MODULES rtl8192se usbhid mac_hid sdhci" 
```
Save, close the editor and try suspend.

---

### Post by mfrna86-x on 2013-09-01
Thanks [COLOR=#000000]praseodym,

surprisingly my Lenovo decided to connect to wireless normally today even before I applied your fix.
I applied it anyway and will try it for a few days (moving from office to home and vice versa).

Will resolve the thread if all goes well.[/COLOR]

---

