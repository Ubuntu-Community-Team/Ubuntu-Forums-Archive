---
title: "No sound altough alsa mixer seems to indicate that sound card works properly"
date: 2010-11-06
forum: Multimedia Software
---

### Post by drolimi on 2010-11-06
I'm newbie in Ubuntu. 
I have installed xubuntu version 10. My sound card is a Yamaha dS-1S, and seems to be properly configured. Alsa mixer doesn't indicates any error. However, I can't manage to get any sound. I have checked that jacks are correctly plugged.
Thanks for any help!
Lilia

---

### Post by lidex on 2010-11-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by drolimi on 2010-11-07
Done. The info is at :
 [http://www.alsa-project.org/db/?f=e84a18b46fc5079f4790ed21709f593e268e55c7](http://www.alsa-project.org/db/?f=e84a18b46fc5079f4790ed21709f593e268e55c7)
Thanks!
Lilia

---

### Post by lidex on 2010-11-07
Nothing is really jumping out at me. I see you have 'external amplifier' enabled. Try disabling it in your mixer.

BTW, do you have xfce-mixer installed? It may help:
```
sudo apt-get install xfce4-mixer
```

---

### Post by drolimi on 2010-11-20
The problem was that I didn't connected properly the sound card. It works fine now. Thanks for your help

---

