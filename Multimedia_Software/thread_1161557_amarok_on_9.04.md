---
title: "amarok on 9.04"
date: 2009-05-16
forum: Multimedia Software
---

### Post by Azyx on 2009-05-16
sorry i'm lazy, but thy don't i get any sond with amarok? It's seems i'm playing but i don't hear anything. ubuntu should bee a os for human being, and not coputer nerds.

some little windows says...To manyerrorrs

---

### Post by Azyx on 2009-05-16
> **Azyx said:**
> sorry i'm lazy, but thy don't i get any sond with amarok? It's seems i'm playing but i don't hear anything. ubuntu should bee a os for human being, and not coputer nerds.

some little windows says...To manyerrorrs

before i have installed amarok on ubutu, it's being clear, i don't heve right codecs or something, them i get the opputunit to download, now it's just silence, very nice when u on a party shuld show how eazy and simplr ubuntu is

---

### Post by Azyx on 2009-05-16
> **Azyx said:**
> before i have installed amarok on ubutu, it's being clear, i don't heve right codecs or something, them i get the opputunit to download, now it's just silence, very nice when u on a party shuld show how eazy and simplr ubuntu is

how do i install amarok with everything?

---

### Post by Electron on 2009-05-16
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

after installing the codecs, then reinstall amarok

---

### Post by Wiebelhaus on 2009-05-16
open term

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

Then

```
sudo apt-get install libdvdcss2
```

Then

```
sudo apt-get install w32codecs
```

Then install all the restricted packages from add/remove.

But I don't think that this is the issue , I bet you need to properly configure your audi settings in amarok to the card your using.

Do the other audio players produce sound?

---

### Post by Azyx on 2009-05-17
Thanx.
Is not a codecs error. It something other problem with the new amarok in jaunty. amarok -d says something about it can't find object...  don't have time to solve it :(

> **sx66gns said:**
> open term

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

Then

```
sudo apt-get install libdvdcss2
```

Then

```
sudo apt-get install w32codecs
```

Then install all the restricted packages from add/remove.

But I don't think that this is the issue , I bet you need to properly configure your audi settings in amarok to the card your using.

Do the other audio players produce sound?

---

### Post by rocky5051 on 2009-05-17
> **sx66gns said:**
> 
Do the other audio players produce sound?

I experienced this same problem. I can't say the same thing happened to the person who posted this, but in my case something happened that made my sound card disappear and PulseAudio loaded up null device output/input.

Hopefully this helps answer the question.

---

### Post by Azyx on 2009-05-17
> **rocky5051 said:**
> I experienced this same problem. I can't say the same thing happened to the person who posted this, but in my case something happened that made my sound card disappear and PulseAudio loaded up null device output/input.

Hopefully this helps answer the question.

It's only amarok i have problem with. but i have learned who it works, but it has change a lot since 1.4 so it's maybe better to try rhytm-box. It has maybe being better?

---

### Post by mtopro on 2009-05-17
> **Electron said:**
> after installing the codecs, then reinstall amarok

I had many issues until I followed this piece of advice.  Thank you!

Just uninstalled it then reinstalled it and it works!

---

### Post by mtopro on 2009-05-17
I spoke too soon..  After another reboot or two Amarok does not work anymore.  The new version of Amarok does not have a setting to control the output device.  This may be where the issue lies.  I read something earlier about how to change Amarok to use OSS instead of ALSA, but can't seem to find the thread anymore.

---

