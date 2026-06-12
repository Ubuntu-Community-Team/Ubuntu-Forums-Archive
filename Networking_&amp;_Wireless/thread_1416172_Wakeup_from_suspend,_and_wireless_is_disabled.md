---
title: "Wakeup from suspend, and wireless is disabled"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by donsy on 2010-02-25
Using wireless is fine until I suspend, then upon waking up I can't reconnect with wireless and on right-clicking the network connection icon  the wireless networking check box is greyed out. I can however reconnect with my wired ethernet. Is there a setting somewhere to choose a preference of autoconnect mode upon boot up and waking up from suspend, either ethernet or wireless? Driver installed via b43-fwcutter.

---

### Post by theozzlives on 2010-02-25
what version of Ubuntu?

---

### Post by evPaseo on 2010-02-25
I've got the same problem. Running Karmic 9.10 on a Vaio PCG-K13. Never had this problem until yesterday.

---

### Post by donsy on 2010-02-25
> **theozzlives said:**
> what version of Ubuntu?

9.10 Karmic

---

### Post by donsy on 2010-02-25
This may be a solution:

[http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/](http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/)

Haven't tried it yet. Will tomorrow.

---

### Post by donsy on 2010-02-26
> **donsy said:**
> This may be a solution:

[http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/](http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/)

Haven't tried it yet. Will tomorrow.


Well I tried it and it made no difference. Is there a setting somewhere to enable wireless?

---

### Post by psb6m on 2010-02-28
Same problem here (Ubuntu 9.10, Dell Latitude D600, Broadcom BCM4306 wireless), and the method of setting STOP_SERVICES has not worked, so I'm hoping someone knows another fix.

---

### Post by chili555 on 2010-02-28
Please try this:```
sudo gedit /etc/pm/config.d/config
```It will probably be a new file. Add a single line:```
SUSPEND_MODULES="iwl3945"
```Substitute your wirless driver if it's not iwl3945. Learn with:```
lshw -C network
```Here is mine, for example:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 99:19:d2:c2:88:77
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:31 memory:edf00000-edf00fffIt sounds like yours, donsy, is b43.

As always, proofread carefully, save and close gedit. Use kate, nano, vim or, if you are an Uber-geek, emacs, if you don't have gedit.

---

### Post by Nottawa on 2010-02-28
I too sometimes have this problem.  Wake up from suspend and I am unable to make my wireless connect.  The connect button is greyed out.  Fortunately, it always does connect, but it can take up to 5 min before it autoconnects.  I tried chilli555's suggestion, but no change.  Anybody have any other ideas?

I am running 9.10 64 bit on a Lenovo T400 with an Intel WiFi 5300.

---

### Post by mu3en on 2010-03-10
correct wireless resume for HP pavilion zv5000 (zv5475ea) (Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03))

file "/etc/pm/config.d/config" now contains:

SUSPEND_MODULES="b43"

NB: "lshw -C network" gives "driver=b43-pci-bridge", that broke resume completely.

thank you people.

---

### Post by donsy on 2010-03-11
Thanks chili555 and mu3en, this works for me also.

---

### Post by Goombie on 2010-03-18
I've been looking for a solution to this problem for some time now. I'll post back here later if it worked for me. :)

Update: Yes, it does work! Thank you very much.

---

### Post by ianrobertperez on 2010-03-24
This worked for me as well.. I wonder though if the Ubuntu devs are aware of this issue or if they have already fixed it in the upcoming release...

---

### Post by chili555 on 2010-03-24
> **ianrobertperez said:**
> This worked for me as well.. I wonder though if the Ubuntu devs are aware of this issue or if they have already fixed it in the upcoming release...You could probably report it on Launchpad. I am not a programmer, but I imagine it would be a bit hard to parse the last used network interface's driver and reload it...but maybe not.

---

### Post by dm6257 on 2010-03-30
I don't know how you figured this out, but as with Donsy, your suggestion worked great.
Thanks.

---

### Post by ProsperB on 2011-11-12
Thanks, Chili555, this saved my day on Oneiric !

---

### Post by chili555 on 2011-11-12
Glad it's working. Have fun!

---

### Post by chchandler on 2011-12-27
> **mu3en said:**
> correct wireless resume for HP pavilion zv5000 (zv5475ea) (Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03))

file "/etc/pm/config.d/config" now contains:

SUSPEND_MODULES="b43"

NB: "lshw -C network" gives "driver=b43-pci-bridge", that broke resume completely.

thank you people.

This worked for me as well on an Acer Aspire 3000, Broadcom BCM4318 wifi.  There was no /etc/pm/config.d/config file so I created one with the single line:

SUSPEND_MODULES="b43"

and it worked without a re-boot.  My "lshw -C network" also returned the entry "driver=b43-pci-bridge" so that makes me think this may work for any b43 driver with a similar issue under power management.

---

