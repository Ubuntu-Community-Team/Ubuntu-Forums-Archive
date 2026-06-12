---
title: "Alsamixer setting does not stick after reboot"
date: 2010-05-05
forum: Mythbuntu
---

### Post by larsolav on 2010-05-05
Sorry for this post, I know I read the answer in a post here a while ago, but can't find it!
Just installed 10.04, and used alsamixer to unmute SPDIF/HDMI audio. HDMI audio works fine after unmuting, but after reboot the I have to go back to alsamixer to unmute.
All I do now is start alsamixer by typing "alsamixer" in a terminal, but I vaguely remember something about typing something more to make the unmuting "stick" after reboot...
Anybody know?

PS: It took me less than 2 hrs yesterday to get set up 10.04 from scratch (including installing a compact flash reader and mounting two 2TB drives filled with recordings. Did it all in order to be able to record American Idol for the wife after I hosed the system the day before while upgrading. I really like the result; you guys just make installing and setting up Mythbuntu easier and easier!

Thanks!

---

### Post by Jose Catre-Vandis on 2010-05-05
After changing your settings, try
```

sudo alsactl store 0

```

---

### Post by nunrgguy on 2010-05-05
It's a known bug - I've fixed it on 2 boxes by doing the following from

[http://https://answers.launchpad.net/ubuntu/+question/68564]("http://https://answers.launchpad.net/ubuntu/+question/68564")


Edit /etc/init.d/alsa-utils line 372, should fix it.

---

### Post by larsolav on 2010-05-06
Thanks Jose and nunrgguy,
I did not have a /etc/init.d/alsa-utils,
but "sudo alsactl store" worked!

Thanks guys!

---

### Post by Jose Catre-Vandis on 2010-05-06
:)

---

