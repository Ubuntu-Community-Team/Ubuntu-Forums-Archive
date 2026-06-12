---
title: "nFORCE drivers &amp; midi support"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by milan_nr1 on 2006-08-11
Hello my friends i need some help...with my sound card.I'm owner an nForce 4 board concrete MSI K8NGM2-FID and I'm using the onboard audio - Realtek ALC880. I can't install the nFORCE drivers corectly. I tried it but the kmix shows that i'm still using the ALSA + OSS drivers. in the nvmix there wasn't any information about the driver that i installed from the NFORCE-Linux-x86-1[1].0-0311-pkg1.run.And i need a help with playing midi files...
PS i tried fast every thig and the relsion notes from nvidia too...thanks friends

---

### Post by tseliot on 2006-08-11
If the soundcard works fine you don't need to install the driver from the Nvidia website.

If you want to play midi you have to install timidity:
```
sudo apt-get install timidity
```

To launch the GUI of timidity:
```
timidity -ia
```

---

