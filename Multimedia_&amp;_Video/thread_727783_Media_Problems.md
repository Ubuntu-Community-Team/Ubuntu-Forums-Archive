---
title: "Media Problems"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by mr wilson on 2008-03-18
I have recently installed Ubuntu on my computer and am having a lot of trouble getting any kind of media to play. I have added the medibuntu repository and installed the libdvdcss2 and w32codecs packages. The totem player still refused to play anything properly, (it played one files' sound, without any picture). I then tried vlc (it tried to open the file but then promptly closed) and kaffeine (it 'played' the file really fast without sound or picture - I could see it 'playing' in the bar down the bottom). Could somebody please help me out. Thankyou.
P.S. I am only brand new to Ubuntu

---

### Post by Jimmyfj on 2008-03-18
You need to install some codecs on your system:

```
sudo apt-get install ubuntu-restricted-extras
```

And beside that you can scim Programs>Add & Remove programs>Sound & Media, from where you can install more codecs.

---

### Post by mr wilson on 2008-03-18
I installed those codecs but still got the same problems occuring . . . .

---

