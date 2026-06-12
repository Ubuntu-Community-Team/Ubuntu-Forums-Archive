---
title: "How to give sound access to an user application?"
date: 2008-05-28
forum: Multimedia Software
---

### Post by stakh on 2008-05-28
Hello,

I've installed Kubuntu 8.04, and wanted to setup Enemy-Territory (which I copied in /home/me/Games/enemy-territory). The game works perfectly, but has no sound. The error message is the following:

```
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
```

I've seen [this page]("https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfensteinEnemyTerritory"), which recommends the following:
```

sudo nano /etc/rc.local
add "echo 'et.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss"
```

I have not yet tried to do it however, because it seems to me that my kubuntu install uses does not use oss but another sound service "HDA Intel" (at least that's what I see in KMix). So I wanted to ask which command should I issue to take that into account?

Second problem is that I launch ET as an user application (did not want to install it in a non user space), and I don't know if the application needs special rights to access the sound system... If so, how to proceed?

Also, according to [this page]("http://ubuntuforums.org/showthread.php?t=780625&highlight=enemy+territory"), the solution above is not stable, but the command be reissued every time... Is there a more permanent solution?

Thanks for the help!

---

