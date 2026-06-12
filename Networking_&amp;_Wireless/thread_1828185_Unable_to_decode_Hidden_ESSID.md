---
title: "Unable to decode Hidden ESSID"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by nibol on 2011-08-18
Running BT5, aircrack-ng v. 1.1, Alfa AWUS036NH.

My curiosity has been aroused by a local AP that is not transmitting an ESSID.  It also is neither transmitting beacon frames nor data.
The channel shows a negative one, as does the power.  Facts:

1.  I know this AP is nearby because, before they hid the ESSID, the power output was fairly high.

2.  Airodump-ng shows -1 channel, -1 power, and a hidden ESSID, although the BSSID is visible.  Neither the channel nor the encryption scheme are being transmitted.

3.  Neither beacons nor data are being sent.  I can determine the correct name of the ESSID from the probe field in airodump-ng
but that is all.

4.  All attempts in aireplay-ng to dissociate the client fail with the message that "No such BSSID" is found!?

5.  Kismet, on the other hand, does not even see the AP.

6.  Loading the .cap file in Wireshark reveals no information about those packets for which the source, or dest, is the AP.

Can anyone give me guidance on how I can learn more about this?

Thanks,

---

### Post by spiky001 on 2011-08-18
I dont think you will get any help with your problem HACKING is frowned upon Try the back track forums [http://www.backtrack-linux.org/forums/](http://www.backtrack-linux.org/forums/)

---

### Post by nibol on 2011-08-19
> **spiky001 said:**
> I dont think you will get any help with your problem HACKING is frowned upon Try the back track forums [http://www.backtrack-linux.org/forums/](http://www.backtrack-linux.org/forums/)

Thanks for your response.  By the way, are you enjoying the riots?

---

