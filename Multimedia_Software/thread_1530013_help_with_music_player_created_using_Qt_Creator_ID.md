---
title: "help with music player created using Qt Creator IDE 4.5"
date: 2010-07-13
forum: Multimedia Software
---

### Post by vijay_kansal on 2010-07-13
Hi,

I have created a simple music player using Qt creator IDE.

As I add mp3 files to my playlist and then play them using this music player, it is unable to play anything and mediaObject->state() continously returns Phonon::LoadingState . This means that mediaObject is not coming out of loading state but why is this so and how can i overcome this problem. 

Secondly, as I try to add an audio file of .wav or .ogg format , i get the following error

(<unknown>:1998: GStreamer-CRITICAL **: gst_element_make_from_uri: assertion `gst_uri_is_valid (uri)' failed

I tried running the Phonon music player available at link [http://doc.qt.nokia.com/4.7-snapshot...sicplayer.html](http://doc.qt.nokia.com/4.7-snapshot...sicplayer.html) also , but suffered from same problems with this music player as well.

i downloaded KMPlayer which is a media player built using Qt and Phonon.This music player is also unable to play any audio file and i get similar results with it.
i.e. no errors with .mp3 files , yet player shows Player Phonon Buffering State as i try to play any audio file and hence does not play any sound.
And it shows similar error as abovementioned with .wav and .ogg files

I am using Ubuntu 9.10. and have installed Qt 4.5

Please help me with the above problems.

Thanks in advance.

---

### Post by vijay_kansal on 2010-07-13
Help needed desperately

---

### Post by vijay_kansal on 2010-07-13
Please help , in earnest need!!!

---

