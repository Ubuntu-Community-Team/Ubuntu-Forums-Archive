---
title: "ALC892 + Ubuntu Server 10.04 + Intel ICH8M"
date: 2012-07-10
forum: Multimedia Software
---

### Post by dlopezsk on 2012-07-10
Hi all,

I've a problem with to capture audio in microphone, I can listen to  audio on speakers. I think to install correctly drivers for ALC892  because I get until version alsa-driver-1.0.25.tar.bz2

The problem is that the micro on JACK  doesn't capture audio and I hear noise alone, I do different things but I can't solve it.

What happen it?How can I solve?

Thanks

P.S.

After then I've to run under java a software to change volume on speakers but don't change it, try an exception NullPointerException when I get volume:

The code :

volspeaker=(FloatControl) port.getControl(FloatControl.Type.VOLUME) when is line supported. Is corrrect?

On windows has any problem.The computer is MIO-2260

---

### Post by dlopezsk on 2012-07-11
> **dlopezsk said:**
> Hi all,

I've a problem with to capture audio in microphone, I can listen to  audio on speakers. I think to install correctly drivers for ALC892  because I get until version alsa-driver-1.0.25.tar.bz2

The problem is that the micro on JACK  doesn't capture audio and I hear noise alone, I do different things but I can't solve it.

What happen it?How can I solve?

Thanks

P.S.

After then I've to run under java a software to change volume on speakers but don't change it, try an exception NullPointerException when I get volume:

The code :

volspeaker=(FloatControl) port.getControl(FloatControl.Type.VOLUME) when is line supported. Is corrrect?

On windows has any problem.The computer is MIO-2260

I solve the volume speaker, after then I change implementation and add a class in java. But I need to get selected the microphone on target device. I'll find it

Another problem JACK on micro I don't know to solve now

---

### Post by dlopezsk on 2012-07-31
> **dlopezsk said:**
> I solve the volume speaker, after then I change implementation and add a class in java. But I need to get selected the microphone on target device. I'll find it

Another problem JACK on micro I don't know to solve now

To solve JACK on micro, in my case it solve with to connect with jack speaker on Portatil.

---

