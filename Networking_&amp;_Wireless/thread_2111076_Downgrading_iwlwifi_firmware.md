---
title: "Downgrading iwlwifi firmware"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by Drianos on 2013-01-31
Hi everyone, I have been trying to hunt a problem of my wireless card(Intel Centrino Advanced-N 6230)that is making me have small range signal. I have try many things and now i wanna try downgrading the firmware. I want to try this because i found out that many people with the same computer are having the same problem and for some of they updating the firmware help them(In Windows where the same problem appear), but checking my current firmware:

```
sudo lshw -c network
```

I found out i'am using the latest firmware:

```

...
driver=iwlwifi driverversion=3.5.0-22-generic firmware=18.168.6.1
....

```

But in iwlwifi page [ (Link)]("http://wireless.kernel.org/en/users/Drivers/iwlwifi") my card is not listed with the latest driver, instead it indicates that i should use 17.168.5.1

Since i don't know how to do this i will really appreciate if someone teach me how to downgrade my firmware.

Thanks in Advance, Drianos

Ubuntu 12.10
Dell XPS 14z
Intel Centrino Advanced-N 6230

---

### Post by ahallubuntu on 2013-01-31
> **Drianos said:**
> Hi everyone, I have been trying to hunt a problem of my wireless card(Intel Centrino Advanced-N 6230)that is making me have small range signal. I have try many things and now i wanna try downgrading the firmware. I want to try this because i found out that many people with the same computer are having the same problem and for some of they updating the firmware help them(In Windows where the same problem appear)

The page you linked to has a download link to the firmware from:

[http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-6000g2b-ucode-17.168.5.1.tgz](http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-6000g2b-ucode-17.168.5.1.tgz)

and says that to install this firmware, do (I added the sudo):

```
sudo cp iwlwifi-*.ucode /lib/firmware
```

once you've extracted it.

---

### Post by Drianos on 2013-01-31
> **ahallubuntu said:**
> The page you linked to has a download link to the firmware from:

[http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-6000g2b-ucode-17.168.5.1.tgz](http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-6000g2b-ucode-17.168.5.1.tgz)

and says that to install this firmware, do (I added the sudo):

```
sudo cp iwlwifi-*.ucode /lib/firmware
```

once you've extracted it.

I try that but i get the same output from 
$sudo lshw -c network

---

### Post by ahallubuntu on 2013-01-31
Did you reboot? 

If that doesn't work...you can try removing all firmware for *iwlwifi* from the existing firmware directory first.  I'd probably save it instead of removing it:

mkdir ~/keep_iwlwifi
sudo mv /lib/firmware/*iwlwifi* ~/keep_iwlwifi

then extract the new (old) firmware, copy it to /lib/firmware and reboot.

---

### Post by Drianos on 2013-02-01
Yes.

I did that and work,i think that i didn't make any significant difference but is too soon to say. Thanks for your help.

---

