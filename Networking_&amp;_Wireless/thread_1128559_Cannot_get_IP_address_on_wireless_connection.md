---
title: "Cannot get IP address on wireless connection"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by gewitty on 2009-04-17
I just updated a laptop that had been running Gutsy successfully for some time. I did a clean install of 8.10 and everything looked OK until I tried to connect to the wireless router. The PC can see the network and tries to connect, but after about 30 seconds it asks for an encryption key. The settings I have are identical to the previous Gutsy setup, so I know that the correct ssid and WEP encryption details are submitted. I've also tried switching encryption off on the router, which makes no difference. So I'm thinking that the problem may be that it's failing to get a network address.

Once again, everything is set up exactly as it was in Gutsy, so I'm baffled as to what the cause might be.

---

### Post by eeking on 2009-04-17
When I was first setting up my wireless in Intrepid, it would attempt to connect but always keep failing and asking for the WPA passphrase again. Removing the stored key from Applications->Accessories->Passwords and Encryption Keys, then re-entering it the next time I tried to connect fixed it for me. May have been coincidence, I was trying so many different things at the time, but you might give it a shot.

---

