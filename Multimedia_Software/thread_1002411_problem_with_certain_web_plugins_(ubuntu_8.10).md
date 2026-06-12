---
title: "problem with certain web plugins (ubuntu 8.10)"
date: 2008-12-05
forum: Multimedia Software
---

### Post by Veggiet on 2008-12-05
Hi, I just recently upgraded from 8.04 to 8.10 and so far it's been working great, except that a certain flash plugin has not been able to load. I've watched youtube, played flash games, etc... but this one website ([www.jellytelly.com](www.jellytelly.com)) uses the ooyala player [http://www.ooyala.com/products/delivery]("http://www.ooyala.com/products/delivery") it does not work, It shows the play button, but the video itself is blank.

---

### Post by Veggiet on 2009-01-09
Ok Here is a quick update, I haven't as of yet submitted a bug report. I tried reinstalling and upgrading flash yesterday, I also tried reinstalling firefox, which I found out that I couldn't uninstall it from the "add/remove programs" menu. Anyway here are some screenshots of what's happening:

This is a same from ooyala's main website at [http://www.ooyala.com/products/delivery]("http://www.ooyala.com/products/delivery")
this is the first picture that you see when I load one of the ooyala players:
[[IMG]http://img339.imageshack.us/img339/3048/ooyala15ks0.th.png[/IMG]](http://img339.imageshack.us/my.php?image=ooyala15ks0.png)

Then I click on the large play button in the center of the player, and I get this:
[[IMG]http://img377.imageshack.us/img377/2976/ooyala2yc4.th.png[/IMG]](http://img377.imageshack.us/my.php?image=ooyala2yc4.png)
this is how it sits, with the same message in the status, the video is completelly black, and while the buttons in the player can be clicked, The Video just doesn't want to load.

Here is a screenshot from JellyTelly.com : [[IMG]http://img440.imageshack.us/img440/7724/ooyalashotdr8.th.png[/IMG]](http://img440.imageshack.us/my.php?image=ooyalashotdr8.png)

---

### Post by steve2718 on 2009-03-04
I reported this issue with ubuntu 8.10 and the latest flash plugin - 10.0.22.87 - to Ooyala support.  Their verbatim reply is below.

This same breakage is seen with both the script form of their player, and the direct flash embed form, and across all browsers I have tried (FF, Epiphany, Opera).

---- response from [email]support@ooyala.com[/email] ----
Hello Steve, 

It is Ooyala's goal to deliver the best possible user experience to all viewers. To this end we conduct extensive testing on our supported platforms focusing for playback quality and overall compatibility. Unfortunately, Linux is not among our supported configurations.

Supported configurations for the Player:

Operating Systems: Windows XP, Vista, and Mac OS X

Browsers
    * Windows: IE6, IE7, FF2, FF3
    * Mac OS X: Safari 3, FF2, FF3

Flash
o Windows: 9.0.28, 9.0.45, 9.0.47, 9.0.115, 9.0.124, 9.0.151, 10+ o Mac OS X: 9.0.28, 9.0.45, 9.0.47, 9.0.115, 9.0.124, 9.0.151, 10+

The Pre 9.0.115 versions of Flash, because of their small combined installed base of less than 5% are tested in rotation and therefore each version is not exercised with every release.

Regards,

The Ooyala Team
----

---

### Post by steve2718 on 2009-03-04
By the way the new (in alpha) Ooyala player *does* work on this combination, you can see samples on the Ooyala blog page here: [http://www.ooyala.com/blog](http://www.ooyala.com/blog)

---

### Post by Veggiet on 2009-03-04
Hmm, That's interesting considering it did work well in ubuntu 8.04. That good that the new player seems to works. Thanks!

---

