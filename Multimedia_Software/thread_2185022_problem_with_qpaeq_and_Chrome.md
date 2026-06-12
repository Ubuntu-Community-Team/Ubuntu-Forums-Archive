---
title: "problem with qpaeq and Chrome"
date: 2013-10-31
forum: Multimedia Software
---

### Post by fondatommaso2 on 2013-10-31
Hi folks,
I use ubuntu 13.10 and Google chrome. Since I'm a music lover, I use qpaeq (pulseaudio's built-in equalizer) to equalize my music.
Now, I've got a big problem: it works with rhythmbox, vlc, etc by selecting "FFT based equalizer" as the default sound sink in pavucontrol, but it doesn't work in Google chrome, when watching a youtube video. If I select "FFT based equalizer" in pavucontrol sound crackles and becomes awful. I think it's something related to pepper flash (used by chrome), because it works in firefox, which uses the normal flash player 11.2 provided by the package flashplugin-installer.
Do you know how to solve this problem? I know it might be difficult....
thanks in advance

---

### Post by warp99 on 2013-10-31
It sounds like this bug:

[https://code.google.com/p/chromium/issues/detail?id=128870](https://code.google.com/p/chromium/issues/detail?id=128870)

You could disable pepperflash and use the adobeflashplugin in chrome://plugins.

---

### Post by fondatommaso2 on 2013-11-01
> **warp99 said:**
> 
You could disable pepperflash and use the adobeflashplugin in chrome://plugins.
Of course I could, but I use Chrome because I want flash player up to date, because it works better. Using adobeflashplugin in Chrome is the same of using firefox...
Thanks

---

### Post by warp99 on 2013-11-01
Since this is a bug with Chrome and not Ubuntu you could check the posts in the link I provided for a workaround otherwise that would be the only option available until Google decides to fix the problem.

---

