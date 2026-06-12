---
title: "Cannot play BBC news: video"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by nimonika on 2008-04-14
I have mplayer installed which plays almost everything except the BBC news. I have firefox 3.0 beta. Please can someone point out what settings do I have to make in firefox for mplayer to pick up BBC news

Thanks

---

### Post by SamSlater on 2008-04-14
"sudo apt-get install mozilla-mplayer"

i had to uninstall the totem plugins to get it to work, and I'm using Gutsy with Firefox 2. I dunno if the plugin works for Firefox 3.

---

### Post by nimonika on 2008-04-15
I have removed all the totem plugins and still it does not work

---

### Post by dje on 2008-04-15
Try adding the medibuntu repositories, howto [here]("https://help.ubuntu.com/community/Medibuntu")
Then do:
```
sudo apt-get update
```
and
```
sudo apt-get install w32codecs
```

hope that helps,
dje

---

