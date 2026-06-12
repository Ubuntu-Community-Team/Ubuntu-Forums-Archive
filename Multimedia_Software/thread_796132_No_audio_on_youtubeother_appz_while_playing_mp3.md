---
title: "No audio on youtube/other appz while playing mp3"
date: 2008-05-16
forum: Multimedia Software
---

### Post by saffolino on 2008-05-16
In a few words: I'm listening to music with rhythmbox then I open a youtube video/flash with audio/mplayer/whatever and I don't have the audio, but still can listen the mp3.So I "keep" busy my device for only an application at once?Is there a way to "open sessions" so I can listen from 2 or more application in the same time?

Ubuntu 8.04 Laptop Acer 5920G audio device Realtek ALC888(in ALSA I set HDA Intel Device)

:KS

---

### Post by hermes0710 on 2008-05-16
If you use firefox, untick the "Tell me if..." in the security tab and make sure you don't have libflashsupport installed. That is what it worked for me

To uninstall libflashsupport:
```
sudo apt-get purge libflashsupport
```

---

### Post by kpkeerthi on 2008-05-16
> **saffolino said:**
> In a few words: I'm listening to music with rhythmbox then I open a youtube video/flash with audio/mplayer/whatever and I don't have the audio, but still can listen the mp3.So I "keep" busy my device for only an application at once?Is there a way to "open sessions" so I can listen from 2 or more application in the same time?

Ubuntu 8.04 Laptop Acer 5920G audio device Realtek ALC888(in ALSA I set HDA Intel Device)

:KS

Try this tip [http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse](http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse)

---

### Post by Thanoulis on 2008-05-16
Maybe it's the pulseaudio. Go to System->Preferences->Sounds and at the Sound tab, unclick the Enable software sounds (ESD) box.
It worked for me. :)

---

### Post by saffolino on 2008-05-16
Nono, flash works fine if I close rhythmbox before loading a flash.I can hear any sound,instead, while I'm already listening to music from flash/mplayer/other application that use sound.If I close the first application that use sound, it keeps the device "busy" so loading another application with audio I can't hear any sound.IS it clear now? Sorry, for my english.

---

### Post by hermes0710 on 2008-05-16
Have you tried my suggestion?

---

### Post by saffolino on 2008-05-16
Ok. Done your suggestion and Thanoulis. It works. I love you guys :D

---

### Post by aiva114 on 2008-09-03
> **hermes0710 said:**
> If you use firefox, untick the "Tell me if..." in the security tab and make sure you don't have libflashsupport installed. That is what it worked for me

To uninstall libflashsupport:
```
sudo apt-get purge libflashsupport
```



srry for saying this but i'm noob with ubuntu but how do you do that??

---

### Post by nbayiha on 2008-09-03
> srry for saying this but i'm noob with ubuntu but how do you do that??
you dont have to be sorry dude, we were all noob one day :lolflag: , and the forum is here to help you.

Open a terminal and paste the code inside. To get the terminal is 
> Applications -> Accessories -> Terminal . 
then input the command those guys gave you above.

If that doesn't solve your problem 
follow this thread 

[http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem](http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem)

And by the way , Welcome!!

---

### Post by aiva114 on 2008-09-03
> **nbayiha said:**
> you dont have to be sorry dude, we were all noob one day :lolflag: , and the forum is here to help you.

Open a terminal and paste the code inside. To get the terminal is 
 
then input the command those guys gave you above.

If that doesn't solve your problem 
follow this thread 

[http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem](http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem)

And by the way , Welcome!!


THnX man 

i tried the both of those methods but still I don't have any sound wen i go to youtube


any idea's??





founded surround channel was muted

---

