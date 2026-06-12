---
title: "what is needed to play video on new install of 18.04?"
date: 2018-06-05
forum: Multimedia Software
---

### Post by wfriedwaldgmail.c on 2018-06-05
with the help of SeijiSensei & the rest of you, I believe that I have been able to successfully do a clean install of 18.04.

thanks!

next question: one of the main things I need to do is play videos.  When I tried to do that, using the built-in video player, I was informed that I am missing the proper MPEG decoding software. (I guess that isn't pre-installed!)

can anyone give me a SUDO command or something like that to install these necessary components?

thanks again!

w

---

### Post by kazakore on 2018-06-05
I go with VLC, it is compiled using the ffmpeg libraries so doesn't need the codecs installing externally and is about the only feature rich player I've found with Jack support, which for me personally is a must. But as with everything Linux there is more than 101 answers to this question!

```
sudo apt-get install vlc
```

---

### Post by monkeybrain20122 on 2018-06-05
```
sudo apt install ubuntu-restricted-extras 

```
for the codecs.

---

### Post by deadflowr on 2018-06-05
You need the ubuntu-restricted-extras package to playback most video and audio.
```
sudo apt install ubuntu-restricted-extras
```
Note: you need to agree to the Microsoft corefonts EULA.
To do so use the tab key and the arrow keys to select the *I agree *option.
If you fail to agree it can bonk the whole install.

ninja'd ^

---

### Post by wfriedwaldgmail.c on 2018-06-05
hey thank you!

i got as far as this - it seems to be waiting for me to give it permission, but I am not getting the prompt, so I can't figure out where to say "yes" or give a password.

[ATTACH=CONFIG]279977[/ATTACH]

thanks for any further help!

---

### Post by slickymaster on 2018-06-05
*Thread moved to **Multimedia Software**.*

---

### Post by deadflowr on 2018-06-05
I posted already you need to try to toggle down with the tab key and or the arrow keys.
It'll highlight the OK and then press enter.
(I mixed up I agree with Ok)

---

### Post by #&amp;thj^% on 2018-06-05
Just use your tab key until the "ok" is highlighted then hit enter.
Ninja'd again :)
Going to take a nap now. :D

---

### Post by wfriedwaldgmail.c on 2018-06-05
all right, yes!  now I can play videos on both the "native" player as well as VLC.  Will test see if one player stutters more than the other - so far VLC seems to be smoother.

thanks again,

w

---

### Post by deadflowr on 2018-06-05
Also note that the restricted packages does not include the packages for restricted dvd playback, for that follow:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by monkeybrain20122 on 2018-06-05
If you don't want mscorefonts you don't need to agree to the EULA, just press enter and it would install the rest without the msttcorefonts installer.

I would skip it because the mscorefont installer is broken in 18.04 [https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/1713615](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/1713615)

---

### Post by kazakore on 2018-06-05
> **wfriedwaldgmail.c said:**
>   Will test see if one player stutters more than the other - so far VLC seems to be smoother.


What video card do you have if any? If you are using onboard Intel graphics this should be fixed in both by adding the tearfree option for the Intel driver.

[https://askubuntu.com/questions/418398/tear-free-disabled-in-intel-graphics-tearing-in-xubuntu](https://askubuntu.com/questions/418398/tear-free-disabled-in-intel-graphics-tearing-in-xubuntu)

---

