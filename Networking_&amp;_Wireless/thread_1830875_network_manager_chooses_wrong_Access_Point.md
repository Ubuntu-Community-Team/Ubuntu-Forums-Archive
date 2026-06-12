---
title: "network manager chooses wrong Access Point"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by thomas303 on 2011-08-22
Hi, I connect to the WPA2-secured wifi of a university. They use 802.11b/g on the 2.4 GHz band and 802.11a/n on the 5.2 GHz band. Both have the same SSID xyz (for roaming).

Now, when I connect to the SSID xyz, ubuntu 11.04 (natty) chooses the Access Point with the highest Strength. However, this is a 802.11g Access Point which is very slow because of high usage and there is no 802.11n available. Slow pings make it unusable.

network-manager is just too stupid to connect to the much faster 5GHz 802.11n AP.

Windows 7 autmatically connects to the 5GHz 802.11n Adapter with 300Mbit/s. That's what I would expect from ubuntu as well. I think Mac OS X also performs great in such situations.

The only workaround for me is to enter the BSSID (Mac-Address) of the 5 GHz AP directly in network-manager. That works and I have 802.11n with up to 300 Mbit/s. However, this is not the perfect solution, because now I can't use roaming any more (we have lots of APs here!).

Do you have any Ideas to prefer 5 GHz band over 2,4 GHz band? I also tried the "band" gconf option as well as kernel module options of module iwlagn with no success.

Or is there something like a blacklist of APs?

Any Ideas? Should I write a bug report?

My setup: 
Ubuntu 11.04 (up to date), Kernel 2.6.38-11 with backports for wireless kernel modules
Dell latitude E5510 with Intel® Centrino® Ultimate-N 6300

---

### Post by thomas303 on 2011-08-22
At home, I figured out that I have a similar problem. My Router uses 802.11n for both the 2.4 GHz band and the 5.2 GHz Band.

The signal in 5.2 GHz Band is even stronger than in 2.4 GHz and 2.4 GHz is used by lots of other APs in the neighbourhood. However, Network-Manager prefers 2.4 GHz over 5.2 GHz.

This doesn't make sense to me. I would prefer 5.2 GHz over 2.4 GHz in most cases. How can I do that?

Entering a fixed BSSID again changes bandwidth from 16-65 Mbit in 2.4 GHz band to up to 270 Mbit in 5.2 GHz. But I don't like fixed BSSIDs.

---

### Post by Rmanola on 2011-10-07
I also want that feature, so I have posted on the network manager channel this problem and it seems that this is more of a wpa_supplicant limitation then the network manager itself. Below I show the chat log:

> [14:12] == rmanola [c8894169@gateway/web/freenode/ip.200.137.65.105] has joined #nm
[14:35] <rmanola> Is there a way, in NM to specify the connection to a 802.11n network without having to enter it manually?
[14:38] <dcbw> rmanola: how do you mean?
[14:38] <dcbw> rmanola: do you mean you've got an 802.11bg/a network and an 802.11n network using the same SSID and you want to prefer the N network?
[14:43] <rmanola> yep
[14:43] <rmanola> dcbw: like is stated here: [http://ubuntuforums.org/showthread.php?t=1830875](http://ubuntuforums.org/showthread.php?t=1830875)
[14:43] <dcbw> at this point we can't really do that becuase the lower layers (wpa_supplicant) dont' support that sort of thing
[14:44] <dcbw> we'd need to add some sort of band selection to wpa_supplicant first, then expose that from NM
[14:44] <dcbw> note that we don't support BG vs. A selection right now either, for the same reason
[14:44] <dcbw> I'd like to get that added though
[14:44] <rmanola> dcbw: Ok, thanks for the clarification.
[14:45] <dcbw> np
[14:45] <rmanola> I'll submit this feature request to the folks on wpa_supplicant

---

