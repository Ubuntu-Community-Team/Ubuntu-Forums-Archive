---
title: "headphone jack not working"
date: 2011-09-27
forum: Multimedia Software
---

### Post by waeras on 2011-09-27
Hello,

I have Ubuntu 11.04 64 bit installed on an Acer Aspire One 522 netbook. My speakers work perfectly, but when I connect headphones the sound still comes from the speakers, and the headphones are dead silent. 

I tried to fix this myself by looking at older threads, but didn't succeed.

I did a 
```

wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

and the results are up at 
[http://www.alsa-project.org/db/?f=28d4fa4febf96ac7f0012a4c4e286ceb9bdd913a](http://www.alsa-project.org/db/?f=28d4fa4febf96ac7f0012a4c4e286ceb9bdd913a)

Any and all help would be greatly appreciated. :)

/Waeras

---

### Post by lidex on 2011-09-27
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

In your sound preferences select the HDA ATI SB soundcard
(internal audio) for output.

---

### Post by waeras on 2011-09-27
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

In your sound preferences select the HDA ATI SB soundcard
(internal audio) for output.

Thank you for your fast reply :)
I did as you instructed, however it didn't change anything. 
Nothing new at my sound prefereces either. 

(I can choose between 'Internal audio analogue stereo' and 'Internal audio digital stereo (hdmi)' nothing more.)

You wouldn't happen to have any other suggestions? :)

---

### Post by lidex on 2011-09-27
You'll want the analog output. Choose it and check the connector option on output tab. Post your amixer output please:
```
amixer
```

---

