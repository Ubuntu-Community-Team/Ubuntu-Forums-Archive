---
title: "Videos on youtube tinted red"
date: 2011-03-03
forum: Multimedia Software
---

### Post by ubu-man on 2011-03-03
I have seen a strange problem with firefox and youtube lately. I updated (including a kernel update from 2.6.35.25 to 2.6.35.27) recently, not sure this has to do with this...

When I play videos on youtube, the video is tinted red. 
I read that this may be a conflict with Add-Blocker so I removed it, but the problem is still there.

---

### Post by Kirboosy on 2011-03-03
Try [Flash-Aid]("http://www.webgapps.org/addons/flash-aid")

That might help.

---

### Post by ubu-man on 2011-03-03
Thanks for the quick reply, but nothing changed after I installed flash-aid and ran the script...

---

### Post by test_tube_baby on 2011-03-03
I have the same problem. I hope there is a fix soon.

I'm running Lucid Lynx

---

### Post by Sandy106 on 2011-03-03
Im on the 10.04 Netbook version using Google Chrome and its happening to me as well. Whatever happened was in the past 2 days.

---

### Post by berxx on 2011-03-03
Flash Player 10.2.152.26 is the culprit. You can either downgrade Flash to 10.1.102.64, or disable hardware acceleration through the Flash 10.2 settings (right-click any Flash file and select Settings, then click the first tab and uncheck the acceleration option). You might have to right-click a non-Youtube Flash file to get into the settings with 10.2 (e.g., the Nvidia home page splash screen). quote from Nvidia forum. it worked for me.I went to the Nvidia home page splash and got to the settings. all good here...firefox 3.6.14 Lucid kernal 2.6.32-30-generic Xfce 4 old X41 IMB t-Pad

---

### Post by jester48 on 2011-03-03
Hmm, I can't even access my Flash settings anymore.

It also seems like Flash runs much better except for youtube which has this pink overlay for whatever reason.  I can watch fullscreen videos from thatguywiththeglasses with seemingly no frames dropped now, which is a plus.

Hopefully they fix youtube soon.

EDIT:  Oops, read your comment to the guy above me.  I can get to the settings on nvidia's page too.  Thanks for that :)

---

### Post by munky99999 on 2011-03-03
I am unable to open settings. For that matter, right clicked flash can tend to freeze flash.

This is certainly a flash problem. Busted firefox and chromium.

---

### Post by [censored] on 2011-03-04
> **berxx said:**
> Flash Player 10.2.152.26 is the culprit. You can either downgrade Flash to 10.1.102.64..... 

Thanks. Anyone know how I do that? 

Is there a repository somewhere of different flash plugins?

---

### Post by Dr Heelhook on 2011-03-04
I am having the exact same problem as well. Pink tinted Youtube. My flash also crashes quite often, especially in connection to Youtube. 

I have Maverick Meerkat, Firefox and Flash version 10,2,152,27. I also cannot access settings.

---

### Post by Paddy Landau on 2011-03-04
See this thread:
[http://ubuntuforums.org/showthread.php?t=1698956](http://ubuntuforums.org/showthread.php?t=1698956)

---

### Post by ubu-man on 2011-03-05
Thanks, the fix worked!

---

### Post by misssarahdee on 2011-03-11
Same problem. Seems to be only when I'm actually on YouTube. Embedded youtube videos elsewhere seem fine. Very odd.

Gives my internet viewing something of an avant-garde edge though.

---

### Post by Paddy Landau on 2011-03-11
> **misssarahdee said:**
> Gives my internet viewing something of an avant-garde edge though.
LOL. Have you seen [post #63]("http://ubuntuforums.org/showthread.php?p=10520930#post10520930") in the main thread?

We have reported this to Canonical, which has rated it as an important bug and reported it to Adobe.

---

