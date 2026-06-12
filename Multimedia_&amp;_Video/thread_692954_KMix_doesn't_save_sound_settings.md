---
title: "KMix doesn't save sound settings"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by KDE-fan on 2008-02-10
I am trying to use skype in Kubuntu, but have a serious problem.

My sound settings in KMix are not saved, and I have to start all over again every time I log on to my computer.

Can someone please tell me how to get the computer to save these settings:
[IMG]http://img142.imageshack.us/img142/2936/kmixskypesettingsud3.jpg[/IMG]

---

### Post by MrClearPore on 2008-02-11
I found this command from another thread:

```
sudo alsactl store 0
```

0 is the audio card number.  If you wanted your second audio card, then you'd change 0 to 1, etc.

---

### Post by KDE-fan on 2008-02-11
^^ Thank you for your reply. I am sorry, but it still resets "capture"-volume to 0. The XFCE Mixer doesn't have this problem, so it must be specific to KMix.

---

### Post by MrClearPore on 2008-02-11
> I am sorry, but it still resets "capture"-volume to 0. The XFCE Mixer doesn't have this problem, so it must be specific to KMix. 

One of the KMix settings allows you to save the settings:

Settings -> Configure KMix...
Uncheck "Restore volumes on login"

Hope this helps.  If it doesn't work, then I'm out of ideas :confused:

Good luck.

---

### Post by KDE-fan on 2008-02-11
Unfortunately, that doesn't fix the problem. The capture volume is still being reset to zero, both for my new microphone and for the sound card.

---

