---
title: "Wireless Connection Stopped Working"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by julianof on 2010-10-20
Hello!

About a week ago I upgraded to Maverick from Lucid. 

All networking worked fine on Lucid.

I am using an Acer Laptop with the Atheros AR928X Wireless Network Adapter.

I can connect to my home network (visible, with WPA2-Personal) fine. However, I cannot connect to my university's wireless network. The only difference I noticed is that its network is using WPA2 Entreprise with Tunneled TLS Authentication and MSCHAPv2.

I tried dmesg and I got:

wlan0: authenticate with 00:1a:1e:ef:f4:e1 (try 1)
wlan0: authenticated
wlan0: associate with 00:1a:1e:ef:f4:e1 (try 1)
wlan0: RX AssocResp frin 00:1a:1e:ef:f4:e1 (capab=0x431 status=0 aid=2)
wlan0: associated
wlan0: deauthenticated from 00:1a:1e:ef:f4:e1 by local choice (reason=1)
cfg80211: All devices are disconnected, going to restore regulatory settings
cfg80211: Calling CRDA to update world regulatory domain
cfg80211: World regulatory domain updated:
(a bunch of frequencies show up. I am copying this manually, so if needed will copy the rest)

Any ideas? Unless the driver has changed, I suspect this is not a driver issue, since it worked fine on Lucid. Is this a NetworkManager issue?

Please help! I need Linux to complete my Master's Thesis! And I can't stand Window$!

Thanks!

---

### Post by marc.verwerft on 2010-10-20
According to [https://bugs.launchpad.net/ubuntu/+source/linux?field.searchtext=ar928x&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=]("https://bugs.launchpad.net/ubuntu/+source/linux?field.searchtext=ar928x&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") there are more reports with the same chipset. Maybe you can doublecheck there with your findings?

Regards,

Marc

---

