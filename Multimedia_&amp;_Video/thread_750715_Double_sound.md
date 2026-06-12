---
title: "Double sound"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by vedran.omeragic on 2008-04-09
Hi,
I have recently installed ubuntu on my laptop, but I'm having problems with sound. When I plug my headphones in, I can hear sound both coming from them AND laptop. My latpop is toshiba satellite a1200 and i have built-in stereo speakers. How can I fix this?

---

### Post by Yellow Pasque on 2008-04-09
Upgrade to the latest version of ALSA and configure your alsa-base file appropriately. Details here: [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by vedran.omeragic on 2008-04-10
After doing that, I'm onlz geting following message:

"No Volume control GStreamer plugin and/or devices found"

---

### Post by Yellow Pasque on 2008-04-10
- Do you still have sound?
- Go to System -> Preferences -> Sound and make sure you select ALSA and the proper mixer.

---

### Post by vedran.omeragic on 2008-04-10
After second rebooting, it worked. Don't really understand way...
Temüjin, thank you, really appreceate it!

---

### Post by Yellow Pasque on 2008-04-10
> **vedran.omeragic said:**
> After second rebooting, it worked. Don't really understand way...
Temüjin, thank you, really appreceate it!
Great! I'm happy to hear it worked for you.

---

