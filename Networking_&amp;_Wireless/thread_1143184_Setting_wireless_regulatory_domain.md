---
title: "Setting wireless regulatory domain"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by krige on 2009-04-29
I am trying to connect to a wireless network which uses channel 13.

I have read in older posts people solved this problem by modifying the wireless router configuration so that it uses a channel number between 1 and 10, but I don't have access to the wireless router I want to connect so I need to solve this problem on my computer.

Up till Ubuntu 8.10 a work around to this was, for European wireless channels, adding the following line to the /etc/modprobe.d/options file:

options cfg80211 ieee80211_regdom=EU

Ubuntu 9.04 release notes suggest to not use that kernel module option anymore and use the "iw reg" command instead. 

Since I am using "Ubuntu 9.04 netbook remix" I have tried to use the command "iw reg set EU" (I live in EU) but with no luck: after running the command "iwlist wlan0 channel" still only 11 channels are displayed.

Does anyone know what I can do to solve this problem?

---

### Post by KlausEggert on 2009-05-29
> **krige said:**
> I am trying to connect to a wireless network which uses channel 13.

Up till Ubuntu 8.10 a work around to this was, for European wireless channels, adding the following line to the /etc/modprobe.d/options file:

options cfg80211 ieee80211_regdom=EU

Ubuntu 9.04 release notes suggest to not use that kernel module option anymore and use the "iw reg" command instead. 

Since I am using "Ubuntu 9.04 netbook remix" I have tried to use the command "iw reg set EU" (I live in EU) but with no luck: after running the command "iwlist wlan0 channel" still only 11 channels are displayed.

Does anyone know what I can do to solve this problem?

Since you are located in italy use IT instead of EU. EU is not valid for the iw command. Background are the different regulations (2.4GHz and 5GHz band) of the countries.
I use "iw reg set DE" to comply with the german regulations.

---

### Post by KlausEggert on 2009-05-29
> **krige said:**
> I am trying to connect to a wireless network which uses channel 13.

Up till Ubuntu 8.10 a work around to this was, for European wireless channels, adding the following line to the /etc/modprobe.d/options file:

options cfg80211 ieee80211_regdom=EU

Ubuntu 9.04 release notes suggest to not use that kernel module option anymore and use the "iw reg" command instead. 

Since I am using "Ubuntu 9.04 netbook remix" I have tried to use the command "iw reg set EU" (I live in EU) but with no luck: after running the command "iwlist wlan0 channel" still only 11 channels are displayed.

Does anyone know what I can do to solve this problem?

Since you are located in Italy use IT. EU is not a valid country for the iw command. Background are the different regulations (channels in 2.4GHz and 5GHz band) of the countries.
I use "iw reg set DE" to comply with the german regulations.

---

### Post by krige on 2009-05-29
> **KlausEggert said:**
> Since you are located in Italy use IT. EU is not a valid country for the iw command. Background are the different regulations (channels in 2.4GHz and 5GHz band) of the countries.
I use "iw reg set DE" to comply with the german regulations.

Thank you KlausEggert. I used the command "iw reg set IT" but still no luck: command "iwlist wlan0 channel" displays only 11 channels.

Do I have to restart anything to make it work?

---

