---
title: "lucid nm-applet. No longer connects to wifi."
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by myjess on 2010-05-02
Lucid network manager:
Installed Lucid yesterday. Rebooted and lucid seen my wifi connection but after a few mins drops the connection and will not re-connect. Now, I cannot get it to connect at al even though the WPA password is correct, and rebooting to Win7 shows no problems there.
Looks like it's back to go old wicd, yet again!

---

### Post by myjess on 2010-05-02
In fact, wicd doesnt help so looks like it is wpa-supplicant.

---

### Post by schiotz on 2010-05-03
Me too :-(

After upgrading to Lucid Lynx my laptop can no longer connect to my WPA encrypted network at home.  Any suggestions / workarounds would be most welcome.

wpa_supplicant fills the log with messages like:

```
May  3 20:58:42 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  3 20:58:45 demokrit wpa_supplicant[981]: WPS-AP-AVAILABLE 
May  3 20:58:45 demokrit wpa_supplicant[981]: Trying to associate with 00:1e:58:29:63:3b (SSID='AsgardWPA' freq=2437 MHz)
May  3 20:58:45 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  3 20:58:55 demokrit wpa_supplicant[981]: Authentication with 00:1e:58:29:63:3b timed out.
May  3 20:58:55 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  3 20:58:55 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  3 20:58:58 demokrit wpa_supplicant[981]: WPS-AP-AVAILABLE 
May  3 20:58:58 demokrit wpa_supplicant[981]: Trying to associate with 00:1e:58:29:63:3b (SSID='AsgardWPA' freq=2437 MHz)
May  3 20:58:58 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  3 20:59:08 demokrit wpa_supplicant[981]: Authentication with 00:1e:58:29:63:3b timed out.
May  3 20:59:08 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  3 20:59:08 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  3 20:59:11 demokrit wpa_supplicant[981]: WPS-AP-AVAILABLE 
May  3 20:59:11 demokrit wpa_supplicant[981]: Trying to associate with 00:1e:58:29:63:3b (SSID='AsgardWPA' freq=2437 MHz)
May  3 20:59:11 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  3 20:59:21 demokrit wpa_supplicant[981]: Authentication with 00:1e:58:29:63:3b timed out.
May  3 20:59:21 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  3 20:59:21 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  3 20:59:24 demokrit wpa_supplicant[981]: WPS-AP-AVAILABLE 
May  3 20:59:24 demokrit wpa_supplicant[981]: Trying to associate with 00:1e:58:29:63:3b (SSID='AsgardWPA' freq=2437 MHz)
May  3 20:59:24 demokrit NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  3 20:59:26 demokrit NetworkManager: <info>  wlan0: link timed out.
May  3 20:59:34 demokrit wpa_supplicant[981]: Authentication with 00:1e:58:29:63:3b timed out.

```/Jakob

---

### Post by goneskiing on 2010-05-04
I've got the same problem with my macbook (santa rosa) - and I cannot right-click to activate and cannot update .... so it's a real problem - I need a command line fix - any help ?   running nm-applet did not help

---

### Post by wtalbott on 2010-05-04
Not sure if more confirmation will help, but I'm having the same problem.  I'd be happy to give more information if someone lets me know what, and how to get it.

---

### Post by nukedathlonman on 2010-05-04
I'm not fully sure if it's wpa_supplicant to blame here or if it's the back end to network manager.  I started a bug a few days ago, no response to it so far.

[https://bugs.launchpad.net/ubuntu/+bug/572777](https://bugs.launchpad.net/ubuntu/+bug/572777)

I haven't been able to use Kubuntu for days with wireless...Starting to think that I may have to do something drastic if I can't get it going....

---

### Post by nukedathlonman on 2010-05-04
I'm attaching full debugging output (it's a text file in the ZIP file).

---

### Post by schiotz on 2010-05-05
Actually, it seems to be an intermittent problem.  After many unsuccessful retries, it finally connected.  Now it connects something like every third time.  With Karmic Koala, it was rock solid.  I use an Intel 3945ABG [Golan] controller. 

I am not sure the bug really relates to nm-applet, it could be wpa_supplicant or the driver.

/Jakob

---

### Post by nukedathlonman on 2010-05-05
Agreed that it's most likely not networkmanger - wicd doesn't work when network manager is completely eliminated.  But with all the reading I'm doing, I believe it's squarely a wpa_supplicant bug.  While there seems to be numerous people with RaLink problems, it's be awfully strange to see quite a few people experiencing this issue with Intel based wireless, Broadcom, and Athros based cards.  While the RaLink based cards seem to have a bug on there hands, it's still awfully strange that three wireless drivers all of a sudden no longer work when they did in prior releases - why would so many wireless drivers just suddenly stop working all at once?

---

### Post by nukedathlonman on 2010-05-05
Hmmmm...  I'm not in Kubuntu so I can't confirm versions.  The package details page indicates Ubuntu is using wpa_supplicant 0.6.9.  I did stumble on something - it's looking like you could be very right about the issue being a combination.  wpa_supplicant had a change in 0.7.1 - directly from the changelog: "cleaned up driver wrapper API (struct wpa_driver_ops); the new API is not fully backwards compatible, so out-of-tree driver wrappers will need modifications"  The last 0.6.x listed change was 0.6.7, not 0.6.9.  but I can't help but wonder if this change might be the caused so many drivers to suddenly not work perhaps?  If so, I'm most likely cooked until Broadcom release an update of the driver.

---

### Post by wtalbott on 2010-05-06
I'm not sure that it's only the version 0.7 wpa_supplicant...  I'm noticing the same behavior with 0.6.9 in Ubuntu, not Kubuntu.

---

### Post by cubsfan53 on 2010-05-06
I filed a comment with Bug #572777 just a few moments ago. I have no problem using an unsecured router at the coffeeshop. But it takes a number of tries (longest was 1 1/2 hours) to connect with my home network.

Laptop - Broadcom 4312
Home Router ZyXEL using WPA-PSK
Ubuntu 10.04 with today's kernel release 2.6.32-22

Rick

---

### Post by schiotz on 2010-05-07
I reported previously that it does not work with my Intel card, however like cubsfan53 it works intermittently, it typically takes 2-3 tries before it works.

```
 ~ $ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```/Jakob

---

### Post by myjess on 2010-05-08
This may be a duplicate of Bug 496093. Looks like a common problem.

---

