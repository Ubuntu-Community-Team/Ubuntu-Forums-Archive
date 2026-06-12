---
title: "No sound or music"
date: 2009-03-16
forum: Multimedia Software
---

### Post by leeds on 2009-03-16
I recently installed Banshee and managed to import all my music from Windows to Ubuntu. However I am unable to play any music (or sound) in either the player or any other application (i.e. Firefox). Prior to this installation I was able to here sound (for example within Youtube videos in Firefox).

---

### Post by sanderd17 on 2009-03-16
try if it works to install ALSA again
```

sudo apt-get install libasound2-dev

```
maybe banhsee will break because of this, let me know

---

### Post by leeds on 2009-03-16
Thank you for your response. I followed your instruction but still no sound. Banhsee seems unaffected.

---

### Post by leeds on 2009-03-17
Hi. Following my reply above I followed instructions in [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) of "Refreshing/Reinstalling the drivers" - following an automatic update, I now have sound again.

Thanks again for the initial response.

---

### Post by sanderd17 on 2009-03-18
OK, great you did it. with Linux I have sometimes problems and most of the times it works with reinstalling an audio driver, although I never know witch one as I'm a newbie to.

---

### Post by D3ath on 2009-03-18
> **leeds said:**
> I recently installed Banshee and managed to import all my music from Windows to Ubuntu. However I am unable to play any music (or sound) in either the player or any other application (i.e. Firefox). Prior to this installation I was able to here sound (for example within Youtube videos in Firefox).

Did you check all the preferences in the sounds mixer. Sometime randomly with new devices the sound preferences may change or mute something that you didn't want to happen. Also make sure pulseaudio is up to date.

```
sudo apt-get install pulseaudio
```

That is probably not the issue. But i would check your preferences.

Update:
Forget everything i have already done or said!

---

