---
title: "MP4 Codec for Ubuntu"
date: 2009-06-30
forum: Multimedia Software
---

### Post by John Private on 2009-06-30
Where can I download a MP4 Codec for Ubuntu?

---

### Post by starcraft.man on 2009-06-30
> **John Private said:**
> Where can I download a MP4 Codec for Ubuntu?

I think your confused. MP4 is a container, not a codec. It usually contains an h.264 video stream as well as audio. Wikipedia for the long explanation if you like.

As for playing back video of the type, I just install VLC, comes with everything needed. It's in the repos, if not, install all the restricted extras and you will get the codecs needed for totem to play. To use the following commands, please open a terminal (Applications > Accessories > Terminal) type em and push enter.

To install all the codecs and extras :

```
sudo aptitude install ubuntu-restricted-extras
```

To install VLC

```
sudo aptitude install vlc vlc-plugins-pulse
```

You can of course do both, that works equally well, then you have multiple options. If you need more info to understand installing, see my sig, an old tut I wrote but still valid.

---

### Post by John Private on 2009-06-30
> **starcraft.man said:**
> I think your confused. MP4 is a container, not a codec. It usually contains an h.264 video stream as well as audio. Wikipedia for the long explanation if you like.

As for playing back video of the type, I just install VLC, comes with everything needed. It's in the repos, if not, install all the restricted extras and you will get the codecs needed for totem to play. To use the following commands, please open a terminal (Applications > Accessories > Terminal) type em and push enter.

To install all the codecs and extras :

```
sudo aptitude install ubuntu-restricted-extras
```To install VLC

```
sudo aptitude install vlc vlc-plugins-pulse
```You can of course do both, that works equally well, then you have multiple options. If you need more info to understand installing, see my sig, an old tut I wrote but still valid.Thanks seems like it is going to work perfectly I will tell you after I am done installing the files as I am doing them right now.

---

### Post by John Private on 2009-07-01
> **John Private said:**
> Thanks seems like it is going to work perfectly I will tell you after I am done installing the files as I am doing them right now.Thanks it worked perfectly fine :D

---

