---
title: "Logitech Headset Not Working"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by MontyV on 2006-07-26
Logitech USB Headset 350

It is not working.  I can control the volume with my button controls on my headset but the sound is still coming from the computer as opposed to the headsets, where it should be.  Under System > Preferences > Sound I can choose the headset but nothing happens.  Under Device Manager I can also see the Headset listed.  Can someone help me out please.  Thank You.

- Monty

---

### Post by wieman01 on 2006-07-26
In most of the applications (e.g. XMMS, Amarok, etc.) you should be able to choose an output device. It seems that your device is readily installed so all you need to do is select it in each application. This works in a way not dissimilar to Windows (as far as I remember).

Play around with it, you are almost there.

---

### Post by MontyV on 2006-07-28
> **wieman01 said:**
> In most of the applications (e.g. XMMS, Amarok, etc.) you should be able to choose an output device. It seems that your device is readily installed so all you need to do is select it in each application. This works in a way not dissimilar to Windows (as far as I remember).

Play around with it, you are almost there.

Thanks for the vote of confidence but almost there is where I'm stuck.  I figure my headset is plugged in so when I am hearing system sounds such as when I start up or shut down Ubuntu I should hear it through the headset.  This does not happen.  Can anybody else throw me a bone here?

---

### Post by wieman01 on 2006-07-28
Ok, I don't know about the other applications but I can explain to you how I got it working with XMMS. I also attached a screenshot:

1. Options -> Preferences
2. Audio I/O Plugins Tab
3. Output Plugin (Alsa) -> Configure
4. Audio device -> Select your sound device (headset)
5. Press 'ok'
6. Press 'apply'
7. Restart XMMS

That works for me. I am still struggling with Amarok though.

---

