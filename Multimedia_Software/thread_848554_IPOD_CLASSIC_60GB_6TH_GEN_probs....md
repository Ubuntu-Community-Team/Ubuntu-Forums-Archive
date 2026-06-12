---
title: "IPOD CLASSIC 60GB 6TH GEN probs..."
date: 2008-07-03
forum: Multimedia Software
---

### Post by real_deal_caulfield on 2008-07-03
Hi.

I've been using my new ipod classic with rhythmbox and libgpod0.6.0 with no problems for a few months now, and loving it. Recently however, it has stopped working. I'm suspecting I broke my setup with an update. Now my ipod shows no music. Rhythymbox now quits whenever I try to sync music.

Any suggestions?

Thanks in advance.

---

### Post by |{urse on 2008-07-03
that's because our friends at app(ho)le have added an extra layer of encryption to your new ipod which makes it impossible (currently) to use under linux. the 5g 5.5g 6g and nano 3g are affected. Unfortunately your only option is to restore it to factory settings with itunes and use win (ugh) or OSX (double ugh) Or you can Ebay it and get a pre 5g ipod that will work perfectly on linux and you can even install ipodlinux on it. I'm mad too man, I had to trade my 8gb nano 3g for a nano 1g.

---

### Post by real_deal_caulfield on 2008-07-05
So how did it go from working to not working? Did my Ipod "phone home"?

---

### Post by tijmz on 2008-07-05
It should work with the libgpod0.6.0 as you stated. Maybe Rhythmbox did break with the update (it spontaneously exiting is a bad omen, of course). Did you try using a different app with your iPod?

---

### Post by real_deal_caulfield on 2008-07-06
Yes, I also tried gtkpod, to no avail.

---

### Post by tijmz on 2008-07-06
I had some problems recently with my iPod (nano, 3G), which came down to data clogging up the iPod, without showing in Amarok (the program I use to sync). The only way I managed to fix this was restore it with iTunes under a Windows installation. If you have access to a Windows/OSX installation, it might be worth a try.

However, what I'm wondering about is whether your iPod shows no music if you try to use it as player, or whether Rhythmbox/gtkpod doesn't show any music being present on the pod. The latter problem could be similar to what happened to me recently, the former sounds more like the problem with older libraries.

---

### Post by real_deal_caulfield on 2008-07-09
I got it working again, though I'm not sure how. It's not recognizing my old music. My guess is a corrupted database/XML file. Thanks for your input. Long live Linux!

---

