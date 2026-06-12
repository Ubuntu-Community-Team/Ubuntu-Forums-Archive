---
title: "sound coming siultaneously fro headphone and speaker"
date: 2011-12-16
forum: Multimedia Software
---

### Post by kpdutta on 2011-12-16
Hi,
    I am using ubuntu 10.04. whenever I plugged headphone to the audio port sound also comes simultaneously from computer speaker. I checked the sound output option, but no option for headphone is shown.
    please help me to fix this problem.

         regards'
     Kamal Dutta

---

### Post by drpjkurian on 2011-12-16
Hi
Please try this code in terminal


```
# sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
# sudo apt-get update
# sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

---

### Post by kpdutta on 2011-12-19
No man, its not working....

---

