---
title: "Upgrade to FF5 killed sound in all browsers..."
date: 2011-06-21
forum: Multimedia Software
---

### Post by Enigmapond on 2011-06-21
So, as the title exclaims, I updated the firefox-next PPA and updated to the new release however, upon doing that, I lost the sound in ALL my browsers. (?) I am using Google Chrome and Chromium as well. Any suggestions would be greatly appreciated. I have since downgraded and the problem still occurs...

Thanks!

Edit: I have sound in Umplayer and SMplayer but that's it. Banshee and Guayadeque are silent...

---

### Post by lovinglinux on 2011-06-21
Try the 5th item on this list: [http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)

---

### Post by Enigmapond on 2011-06-21
Well, I tried that and that put me into deeper doo-doo as now I have no sound system-wide and can't even access the sound preferences. I then uninstalled Pulse and tried to re-install it but it now says there are unmet dependencies...but I checked and the dependencies are already installed.... :( Would this be a good time to upgrade to Natty?...LOL

---

### Post by lovinglinux on 2011-06-21
> **Enigmapond said:**
> Well, I tried that and that put me into deeper doo-doo as now I have no sound system-wide and can't even access the sound preferences. I then uninstalled Pulse and tried to re-install it but it now says there are unmet dependencies...but I checked and the dependencies are already installed.... :( Would this be a good time to upgrade to Natty?...LOL

I don't know why removing pulse would cause such dependency problems.

Try:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get install pulseaudio
```

---

### Post by Enigmapond on 2011-06-21
Well for some reason, synaptic was not cooperating. I did as you said and then used Aptitude to install pulseaudio and it fixed the dependency issue and everything now works again. Some dependencies needed to be downgraded. Not exactly sure what happened but...THANK YOU AGAIN for you help! I'm back to normal!..:)

---

### Post by lovinglinux on 2011-06-21
> **Enigmapond said:**
> Well for some reason, synaptic was not cooperating. I did as you said and then used Aptitude to install pulseaudio and it fixed the dependency issue and everything now works again. Some dependencies needed to be downgraded. Not exactly sure what happened but...THANK YOU AGAIN for you help! I'm back to normal!..:)

You are welcome. Does the sound work on the browsers too?

---

### Post by Enigmapond on 2011-06-21
> **lovinglinux said:**
> You are welcome. Does the sound work on the browsers too?

Yes all sound in the browsers work now. I even upgraded again to FF5 and it's all good. Must of been an "Audio-Hiccup"....bloody Pulse...I hope that code improves.

Cheers!

---

### Post by lovinglinux on 2011-06-21
> **Enigmapond said:**
> Yes all sound in the browsers work now. I even upgraded again to FF5 and it's all good. Must of been an "Audio-Hiccup"....bloody Pulse...I hope that code improves.

Cheers!

Great.

Cheers.

---

