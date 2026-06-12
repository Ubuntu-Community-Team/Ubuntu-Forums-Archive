---
title: "Will my logitech speakers ever work?"
date: 2009-09-16
forum: Multimedia Software
---

### Post by kids0406 on 2009-09-16
Hi all-

I am new to using a linux os due to the fact that I went away on vacation and came back to a dead pc. Since the idiots at Compac don't give windows disc out I had nothing to reinstall vista with so I said the hell with it.

Anyways, so far so good. I am learning my way slowly and through trial and error.

The problem I am having is that I have a set of logitech x240 speakers - 2 satellites and a subwoofer. I get sound out of the subwoofer but not the smaller speakers so the sound I do get is very muffled. I have tried looking for drivers but can't find any.

Any suggestions? The speakers worked great before windows crapped out.

---

### Post by kids0406 on 2009-09-17
bump......anyone???????

---

### Post by etnlIcarus on 2009-09-17
Unless these speakers have on-board sound processing and hook up via USB, I doubt it's your speakers. It's either your soundcard or your mixer settings.

I'm unfamiliar with Gnome's mixer but if it's anything like Xfce's (which is very likely), you're looking for a setting which controls how many channels to output in. Try both the 2.1 and the 2.0 configuration.

Should look at least similar to this: [http://img15.imageshack.us/img15/6489/screenshotchn.png](http://img15.imageshack.us/img15/6489/screenshotchn.png)

---

### Post by wojox on 2009-09-17
Open a terminal and type:

```
alsamixer
```

See if everything is turned up.

---

### Post by ubongo2008 on 2009-09-17
had the oposite problem mine always worked ... had to blacklisten them maybe you wanna trade?

edit: maybe you wanna blacklisten your other sound-devices (if there is only one, that will be used)

---

### Post by HappyFeet on 2009-09-17
Right click your speaker icon and select **open volume control**. Check your sound levels. Also click the preferences button in volume control.

---

### Post by kids0406 on 2009-09-17
I have everything turned up in the preferences. My sound card shows up when I check it......


ETA: when I did the alsamixer, I have all the levels up and I can still only hear sound from my subwoofer.

---

### Post by etnlIcarus on 2009-09-17
> **kids0406 said:**
> I have everything turned up in the preferences. My sound card shows up when I check it......


ETA: when I did the alsamixer, I have all the levels up and I can still only hear sound from my subwoofer.

Did you set the channel mode correctly?

Also, what sound card/chipset are you using?

---

