---
title: "Video drivers for ThinkPad T60?"
date: 2013-02-17
forum: Multimedia Software
---

### Post by Controll on 2013-02-17
Under Xubuntu 12.04, I'm trying to figure out how to install video drivers for my T60

I believe it uses the Radeon x1400 chip.

Thank you.

---

### Post by Bucky Ball on 2013-02-17
*Thread moved to **Multimedia & Video**.*

---

### Post by Controll on 2013-02-17
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video**.*

Thank you for getting me in the right place.

---

### Post by linrunner on 2013-02-17
Hi,

the ATI X1400 runs with the pre-installed radeon driver, there aren't any other drivers.

---

### Post by Controll on 2013-02-17
> **linrunner said:**
> Hi,

the ATI X1400 runs with the pre-installed radeon driver, there aren't any other drivers.

Well, when I try to play a steam game in linux, I get this error:

```
Could not find required OpenGL entry point 'glColorMaskIndexedEXT'! Either your video card is unsupported, or your OpenGL driver needs to be updated.
```

---

### Post by Bucky Ball on 2013-02-17
Try these two commands in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Mark Phelps on 2013-02-17
> **Controll said:**
> Well, when I try to play a steam game in linux, I get this error:

```
Could not find required OpenGL entry point 'glColorMaskIndexedEXT'! Either your video card is unsupported, or your OpenGL driver needs to be updated.
```

Can't speak to that specific problem, but Gaming with that video chipset is NOT going to work well. AMD dropped restricted video driver support for that chipset years ago, and the open-source drivers only have minimal acceleration.

To do Gaming, you would need to upgrade the video chipset -- which you can't do on a laptop.

---

### Post by Controll on 2013-02-17
> **Bucky Ball said:**
> Try these two commands in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

Still get the same error.

---

### Post by Controll on 2013-02-17
> **Mark Phelps said:**
> Can't speak to that specific problem, but Gaming with that video chipset is NOT going to work well. AMD dropped restricted video driver support for that chipset years ago, and the open-source drivers only have minimal acceleration.

To do Gaming, you would need to upgrade the video chipset -- which you can't do on a laptop.

When I used XP on this laptop I had no problem playing more modern games on this chip, had some lag at higher graphic settings, but drivers weren't an issue.

But that was Windows, not Linux

---

### Post by Yellow Pasque on 2013-02-17
Forum failure = double post

---

### Post by Yellow Pasque on 2013-02-17
User failure = triple post

---

### Post by Yellow Pasque on 2013-02-17
> But that was Windows, not Linux
Windows has DirectX, and Linux doesn't, and a lot of these titles were written specifically for DX. Porting to OpenGL is not trivial.

[https://github.com/ValveSoftware/Source-1-Games/issues/32](https://github.com/ValveSoftware/Source-1-Games/issues/32)
The crux of the problem is indeed a buggy driver (since the card itself supports the GL extension in question).

---

### Post by gazpachu on 2013-03-18
I also have this exact problem :-(

DELL Inspiron 9400 (from Sept 2006) 4gb ram and Radeon x1400 (the nVidia 9600GS died 2 years ago).

I've just installed an SDD drive and Ubuntu 12.10. This machine still can do a lot of things! I don't see the point of buying a new one. What a pity the graphic driver is not good enough

---

