---
title: "Shopping for a Linux compatible 802.11g PCMCIA card"
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-02-08
Hi,

After 4 weeks of trying to get my Cisco Aironet 350 PCMCIA card to work with WPA (or WEP for that matter) under Ubuntu, I'm starting to look for a [FONT=Verdana]replacement [/FONT]card. I'm asking the Ubuntu lappy users: 

Are you using a wifi-G PCMCIA card that works with WPA_supplicant using native linux drivers... No not NDISwrapper stuff... only native please!! ;)

if so what is the make/model/version??

---

### Post by hollinch on 2006-02-08
Hi ssalman, I wonder if your problem is the same as mine? See my [thread]("http://ubuntuforums.org/showthread.php?t=126858"). If so, it even more points to a bug in Ubuntu with respect to either this network adapter, an incorrect module for the adapter, or the PCMCIA modules.

Cheers, Jaap

---

### Post by ssalman on 2006-02-09
Thanks hollinch, But I think this is a linux driver/card firmware problem rather than a ubuntu specific problem. I'm duel-booting between Ubuntu and SuSE and have the same problem with both (so far). anyways I see on the net that there are people who were able to setup the Aironet350 card with WEP, so in the mean time I'm going to keep on trying untill I get there, but my ultimate goal is to set it up with WPA, maybe using the windows drivers through NDISwrapper... If I ever get that working, I'll post it here... for now keep on trying, and post any improvments! :) 

Still, if I find a good deal on a new PCMCIA G card with native support for linux WPA, I'll just get one and move on!

---

### Post by Lambert on 2006-02-09
Sorry to hear about your troubles but wireless can be tricky.

I personally like and recommend atheros chipset. Just bought a wna-2330 from best buy last night for $50. Supposedly this is d-links latest line release which is exclusive to best buy for a period of time. You won't find much info about this seris (wna-) anywhere. NOt even currently on d-links site.

There are posts with those that have had problems with this chipset, I have never had a problem and it works flawlessly (used a dwl-g650 which the wna-2330 replaces)

Now, my knowledge on WPA is limited, I don't use it but know it is supported natively by wpasupplicant with the madwifi driver. You can read more about the driver here.

[http://madwifi.org/](http://madwifi.org/)
[http://madwifi.org/wiki/UserDocs/802.11i](http://madwifi.org/wiki/UserDocs/802.11i)

ONe thing I will note is breezy comes with madwifi-old and there is a madwifi-ng driver out. I use the -ng and you'll find mixed comments about which driver to use. With WPA I suggest trying the -ng driver which there is a howto in the tips and tricks section. There has been a lot of updates to the driver which might improve wpa support. You will also need to compile a newer version of wpasupplicant though then what's in breezy repos.

On a side note
There is a list of wpasupplicant supported chipsets on this page. [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

I would suggest comparing that with devices on this page
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
Choose a WPA supported chipset to see the various cards.

Do your research and I hope some others chime in with comments.

Good luck :)

---

### Post by ssalman on 2006-03-28
Update:

I ended up buying a Netgear WG511T PCMCIA wireless card, and it worked right out of the box, for WPA I needed to get compile the latest madwifi driver and latest wpa_supplicant and it is working great.

Thanks Lambert for giving some really useful information.

---

### Post by az on 2006-03-28
If more people would buy any card, try it in Ubuntu and then return it if there was no native linux support, there would eventually be no problem.

I have done this in the past and I encourage anyone else to do so.

---

