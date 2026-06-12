---
title: "HDMI sound is crummy"
date: 2011-03-05
forum: Multimedia Software
---

### Post by rockem_sockem on 2011-03-05
I just got a Shuttle [COLOR=Blue]**[XS35GT]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856101099")**[/COLOR] for an HTPC and installed ubuntu 10.10 (32-bit). This is my first attempt at Linux at all, and I think I'm learning quickly but still feel very lost. After a bit of a struggle I got my audio to work through HDMI, but the quality is crap. I've searched the forums but haven't found a solution. I also don't know what sort of information would be useful to anyone, but I'll post anything you need. It almost sounds like a feedback loop, but I tried everything in [COLOR=Blue]**[this thread]("http://www.linux-archive.org/ubuntu-user/425194-shriekingly-tinny-sound-10-10-higher-volumes.html")**[/COLOR] to no avail.

I have an NVidia Ion graphics/sound card and I'm hooked up to a Sony Bravia tv that otherwise has pretty decent sound.

As I mentioned, I'm pretty new so please be detailed and specific in your responses/requests for info. Thank you!

---

### Post by rockem_sockem on 2011-03-05
Credit to my girlfriend who has far superior google-fu than do I.
Solution found here: [http://www.linux-archive.org/ubuntu-user/425194-shriekingly-tinny-sound-10-10-higher-volumes.html](http://www.linux-archive.org/ubuntu-user/425194-shriekingly-tinny-sound-10-10-higher-volumes.html)

modify /usr/share/alsa/alsa.conf and fix these lines:
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0
 to read as such:
 defaults.ctl.card NVidia
defaults.pcm.card NVidia
defaults.pcm.device 7
 and then reboot

---

### Post by rockem_sockem on 2011-03-07
Now my sound is quite muddy. Voices don't sound right. Is there an equalizer available for HDMI output? I have had no luck finding one. I've only really tested using Hulu, since that will be the main purpose of this machine.

---

