---
title: "Can't use Totem to watch DVB-T"
date: 2010-05-24
forum: Multimedia Software
---

### Post by calande on 2010-05-24
Hello,

I installed my DVB-T board and I can watch TV using VLC and my channels.conf file. I saved a copy of channels.conf as ~/.gstreamer-0.10/dvb-channels.conf but when I start Totem (GStreamer ed.), I don't see a "Watch TV" option under the "Movie" menu. Could you help me, please?
Thanks,

---

### Post by thewolfman on 2010-05-24
Hi,

my advice is to install either Me-TV and/or Kaffeine as both are pretty good at playback via DVB-T.

My personal favorite is Kaffeine.

Regards thewolfman:)

PS: I would stick to version 8.7 and download it as a deb package then install it, when that is done; LOCK THE VERSION!!!!!!! otherwise it will upgrade to the latest version which doesn't scan.

---

### Post by calande on 2010-05-24
Thanks, thewolfman, still, I'd like to use Totem if possible :)
I managed to get the "Watch TV" menu, and when I click it, I get a scanning wizard, but:
 - My DVB-T board is not listed, while another DVB-T board is, but I don't have such board.
 - No channel is found with this scan utility, after a long scan
 - The ~/.gstreamer-0.10/dvb-channels.conf doesn't seem to be taken into account
Could you help me, please?

---

### Post by thewolfman on 2010-05-24
Sorry mate,

I am not a Totem user but you could try installing wscan but I don't really know if that will help you much because I don't know how wscan works!!!!!!.

Regards thewolfman:(

---

### Post by calande on 2010-05-24
It's working now! Woohoo! I closed Totem, ran gnome-dvb-control, imported channels.conf, closed it, ran Totem and I had my channels under "Digital TV" in the sidebar.

---

### Post by thewolfman on 2010-05-24
Alright Charles,

I will have to try Totem myself.

Happy viewing. thewolfman:)

---

### Post by calande on 2010-12-04
And with the upgrade it stopped working :)

---

