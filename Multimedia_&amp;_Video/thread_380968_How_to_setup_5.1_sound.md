---
title: "How to setup 5.1 sound"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by nevaziah on 2007-03-10
how do i set it up? i went and double clicked on the volume button, went into edit and no luck
I use 6.06 Ubuntu and my soundcard is ALC883 HD audio from realtek. It's an onboard sound card with the ASUS P5NE-SLI motherboard.

Also, how do i pull up info on hardware with the console?(to check if 3d rendering is enabled, or surround sound is on etc...)

---

### Post by chewearn on 2007-03-10
I struggled with 5.1ch setup a while back, and it involved tinkering with a file called .asoundrc and alsa setup.  Can't recalled what I did though, as I utimately wipe the ubuntu installation on that PC.  But you might be able to find something by searching those two things.

But, to check if 3D rendering is enable:
```
glxinfo | grep rendering
```

---

### Post by nevaziah on 2007-03-10
all my rendering comes as couldnt find rbg glx visual.
extension 'glx' missing on display :"0.0".

i have 7600gs nvidia (XFX).
there's a program set made by someone to install them but i cannot recall the name..

---

### Post by chewearn on 2007-03-10
There are a couple of ways to install nVidia drivers:

1. Use the stable driver from universe repository:
```
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable

```(This is the method I used, because I am wary of installing anything that is not in the official repository).

2. EasyUbuntu
3. Envy script
4. Automatix2
5. Direct download from nvidia

---

### Post by nevaziah on 2007-03-11
I still dont know how to enable 5.1 sound. Can anyone help me?

-bump

---

### Post by nevaziah on 2007-03-20
Bump

---

### Post by chewearn on 2007-03-20
hi, looks like no one else came in with a good answer, so I'm going to give it a shot.  I assumed you have done the basic stuffs; like unmute and set volume to 100% on the surround channels, etc (doh! :lol:).

So, I went on some extended googling and forum search turns up the following links, which might help you along:
[http://www.arsgeek.com/?p=971](http://www.arsgeek.com/?p=971)
[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)
[http://ubuntuforums.org/showthread.php?p=2273247](http://ubuntuforums.org/showthread.php?p=2273247)
[http://www.ubuntuforums.org/showthread.php?t=217953](http://www.ubuntuforums.org/showthread.php?t=217953)
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

Sorry that I couldn't give you the definitive step-by-step.

---

