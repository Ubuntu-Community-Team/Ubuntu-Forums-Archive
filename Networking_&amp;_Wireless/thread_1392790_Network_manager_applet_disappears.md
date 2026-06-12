---
title: "Network manager applet disappears"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by redbook4574 on 2010-01-28
Hi all,

Strange one here, on about 90% of bootups I find that network manager has disappeared from the notification area to be replaced by a random duplicate of one of the other icons (at random). If I remove the notification area and add it again all is fine. Anybody got any ideas. ?????

---

### Post by Enigmapond on 2010-01-28
No but if you find out, I will be interested...you are not alone. Every boot I have to replace it...:confused:

---

### Post by redbook4574 on 2010-01-28
> **Enigmapond said:**
> No but if you find out, I will be interested...you are not alone. Every boot I have to replace it...:confused:

Just out of interest, do you have cairo-dock installed??

---

### Post by jamere on 2010-01-28
I think the panel applets are buggy. I have to remove and replace notification area, network-manager applet and weather applet fairly regularly.

---

### Post by redbook4574 on 2010-01-29
I think I may have an answer but I could do with a few others to try. The notification area seems to become unstable with more than 4 icons.

So here goes:

I disabled bluetooth (I don't use it) and Ubuntu One (can open from places) in startup, this leaves me with 3 icons in notification area and seems to be stable, but I would be interested in other peoples results.

---

### Post by jamere on 2010-01-29
Redbook,
I've never had more than 3 applets in the notification area:
laptop battery
network manager
audio volume

The weather applet isn't in the notification area but is really flaky, in that at times it shows only a small portion of the weather graphic and the temperature is blocked out. I have to remove it from the panel and add it back in order to restore it. Hope this makes sense.

Definitely buggy behaviour that will eventually be fixed, hopefully.

---

### Post by SecretCode on 2010-01-29
Sadly, the number of icons in the notification area is not definitely the issue. I had this problem quite often a while ago, but now it's stable ... currently have 9 icons there. The Banshee icon displays with the wrong background, but is functional; everything else is fine.

Sadly, I didn't do anything specific to fix it.

---

### Post by redbook4574 on 2010-01-29
That being the case I can only think it was the Ubuntu One applet that was causing my problems, I have re-enabled bluetooth but left Ubuntu one off and after 35 boots have had no further problems. So I can only suggest disabling each applet in turn to find out which one causes the problem.

We can all hope this will be fixed soon or at least in Lucid.

---

### Post by Enigmapond on 2010-01-30
I fixed my problem altogether by replacing the network manager with wicd which is another network manager that seems to be more stable and also the icon is better.

```
sudo apt-get install wicd
```

This will also uninstall the standard manager, so I would at least get the old one in the cache just in case there are any problems, but I didn't encounter any at all...it's worked now constant for 2 days.

Hope this helps.

---

### Post by redbook4574 on 2010-02-02
> **Enigmapond said:**
> I fixed my problem altogether by replacing the network manager with wicd which is another network manager that seems to be more stable and also the icon is better.

```
sudo apt-get install wicd
```

This will also uninstall the standard manager, so I would at least get the old one in the cache just in case there are any problems, but I didn't encounter any at all...it's worked now constant for 2 days.

Hope this helps.
  Wicd would be great but I need mobile broadband and I think I'm right in saying wicd does not as yet support it, ofcourse I could just use gppp but I'm feeling lazy.

---

