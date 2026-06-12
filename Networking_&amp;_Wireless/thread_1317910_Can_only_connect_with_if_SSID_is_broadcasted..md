---
title: "Can only connect with if SSID is broadcasted."
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by wavery on 2009-11-07
I'm new to Ubuntu so I apologize upfront if I'm missing something obvious.  I installed Ubuntu yesterday, configured the wireless connection, and it connected right away.  I turned it back on today and it would not connect.  After playing around with it, it seems the only way I can connect is if I set the router to broadcast the SSID, or if I create a NEW connection rather than trying to connect with the established network information (which is set to 'connect automatically').  I don't think it's a hardware problem, but I'm using:

Computer: Dell Insipron 8200
Card: Dell TrubMobile 1150

Thanks for any input.  Cheers!

---

### Post by coffeecat on 2009-11-07
Hi - which version of Ubuntu are you using? I mean which release: 8.04, 8.10, 9.04 or 9.10. There was a problem with hidden SSIDs and network manager in earlier releases, but in my limited experience this is not so in 9.04 or 9.10. I've seen that in 9.04 there is a noticeable delay before it will autoconnect to a hidden SSID. Give it a couple of minutes or so before fiddling.

Also - are you using the default network manager panel applet to configure wireless? If so, try right-clicking on the NM icon > Edit connection > Wireless. How many entries have you there? If there's more than one for your hidden network there may be some conflict between the configuration entries. If there is more than one, delete them all, let NM disconnect and close that window. Now click on the NM applet again > Connect to Hidden Network and re-configure your hidden connection. Try rebooting and this time give it a couple of minutes.

If that doesn't work, then sorry, I don't know.

---

### Post by wavery on 2009-11-07
Thanks for the thoughts.  Using 9.10.  I tried deleting, creating, renaming, rebooting, making sure just one network is available..etc.  No go.

---

### Post by coffeecat on 2009-11-07
Sorry - I misremembered about 9.10. My limited experience is helping a friend who uses a hidden SSID. I've just come across [this Launchpad thread]("https://bugs.launchpad.net/ubuntu/+bug/468741"). It's quite new, but marked as confirmed, so hopefully someone is working on it. Might be worth keeping an eye on that thread.

---

### Post by smastersonu on 2009-11-07
My first install was 9.02 - wireless would only connect after I enabled broadcast and once it connected I disabled broadcast. Occasionally it would fail and I could just enter the ssid and it would work.

Upgraded to 9.10 last night - wireless is failing again. Oh Joy - how to spend another Weekend t-shooting

---

### Post by epp on 2009-11-08
I am using Xubuntu 9.10 and have found that with the SSID broadcast turned on, after logging in, the connection is active.  I am using WPA2 encryption and in the router settings, the NIC address of my laptop is the only one allowed to connect wirelessly to the router.

With the SSID broadcast turned off, I did not see the network indicator until around 20-30 seconds after login.  

Although it does work with the SSID turned off, it authenticates immediately with SSID turned on.

---

