---
title: "After WICD update, it no longer likes encryption"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by xkalibur84 on 2008-12-12
Today I got an update notification on my task bar and saw it was only for WICD.  I went and updated it and after the update, I lost wireless connection.  Ever since Intrepid came out, I've been using WICD to connect to my WPA2 encrypted network with no problems whatsoever.  After the update, however, I can no longer connect.  It sees wireless networks and my network and it can connect to an open network, but if it's encrypted, it refuses to connect now.

I checked out the log and I see a line that says "WARNING: PSK generation failed!  Falling back to wireless key."

I don't know what that means, but I guess it's the root of my problem.  I'm using Ubuntu 8.10 32-bit and an Atheros 5007eg card.  Like I said, everything worked until today's update.  Any ideas?

---

### Post by LineFeed on 2008-12-13
Hi,

I just had the same problem. It could solve it by deleting
all files in the directory:

/var/lib/wicd/configurations/

Hope that helps!

---

### Post by xkalibur84 on 2008-12-13
Thanks for your help LineFeed, but unfortunately it didn't work.  My settings were still saved so I figured it was some other file I had to delete.  I ended up deleting the wireless.conf file but after that it had problems generating that file.  I ended up uninstalling WICD and reinstalling Network Manager.  I'm now connected to my wireless network through that.

I remember NM being crap in the earlier versions.  Hopefully this version is as solid as WICD was because I always liked WICD...anyway, thanks for your help!

Oh btw, welcome to the forums! =D

---

### Post by LineFeed on 2008-12-14
> **xkalibur84 said:**
> Thanks for your help LineFeed, but unfortunately it didn't work.

There are some more solution proposals here:
[http://bbs.archlinux.org/viewtopic.php?id=59563]("http://bbs.archlinux.org/viewtopic.php?id=59563")

> **xkalibur84 said:**
> I remember NM being crap in the earlier versions.  Hopefully this version is as solid as WICD was because I always liked WICD...
Same here. NM didn't work at all for my current laptop. And, what I
dislike is that NM does not tell you what's going on. These things
are really great with wicd.

Another tool which I haven't tried, yet, but looks interesting is WiFi Radar:
[http://wifi-radar.systemimager.org/]("http://wifi-radar.systemimager.org/")

> **xkalibur84 said:**
> Oh btw, welcome to the forums! =D
Thanks!

---

### Post by Scribblah on 2008-12-14
Thank you. I had the same issue and following your link I found that just changing advanced configuration from passphrase to pre-shared key did the trick.

---

### Post by Starbuck13 on 2008-12-14
> **Scribblah said:**
> Thank you. I had the same issue and following your link I found that just changing advanced configuration from passphrase to pre-shared key did the trick.
Yeah! Changing from "WPA 1/2 Passphrase" to "WPA 1/2 Pre-Shared Key" worked for me too! Many thanks!

---

### Post by Nikolo on 2008-12-14
> **Starbuck13 said:**
> Yeah! Changing from "WPA 1/2 Passphrase" to "WPA 1/2 Pre-Shared Key" worked for me too! Many thanks!

Exact the same for me !! :) :) :)

---

