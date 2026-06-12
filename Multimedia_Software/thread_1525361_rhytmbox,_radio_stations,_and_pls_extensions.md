---
title: "rhytmbox, radio stations, and pls extensions"
date: 2010-07-06
forum: Multimedia Software
---

### Post by mirwanda on 2010-07-06
Hi guys

I wonder how can i play internet radio with .pls extension in rhytmbox....

Ctrl+I didn't work for pls... 

I am using lucid, and the station i am going to listen is:
[http://dialup.kawaii-radio.net:80/listen.pls]("http://dialup.kawaii-radio.net/listen.pls")

(m3u works, it's just pls that didn't work)

thanks for your kind reply

---

### Post by ron999 on 2010-07-06
Hi
That radio station's playing OK for me in Rhythmbox.

Choose
[U]Create new Internet Radio Station
[/U]
then paste in **this** URL

```
http://dialup.kawaii-radio.net/listen.pls
```

---

### Post by mirwanda on 2010-07-06
> **ron999 said:**
> Hi
That radio station's playing OK for me in Rhythmbox.

Choose
[U]Create new Internet Radio Station
[/U]
then paste in **this** URL

```
http://dialup.kawaii-radio.net/listen.pls
```
I am glad to hear that it's work...

but it still didn't work on my rhytmbox...

it give me a message:
"Couldn't start playback, connection terminated unexpectedly"

whaaat's wrooong with my rhytmbox????

---

### Post by ron999 on 2010-07-06
Hi
That radio stream is aac. Those other m3u links are probably mp3.
So make sure you've got the correct gstreamer plugins installed and also faad decoder.

Also you should be able to play that station with VLC or mPlayer using commands:-
```
vlc http://dialup.kawaii-radio.net/listen.pls
```
and
```
mplayer http://dialup.kawaii-radio.net/listen.pls
```

---

### Post by ajgreeny on 2010-07-06
It also plays OK in RB for me, though I personally seldom use rhythmbox for radio stations or pls files.  I play them direct in vlc or gnome-mplayer which I think have lower overheads than rhythmbox.

I have a full complement of gstreamer packages and also w32codecs installed which may well make a difference for many audio (and video) formats

---

### Post by mirwanda on 2010-07-06
I installed gstreamer for aac and try using vlc

this is what i got:
```
mirwanda@mirwanda-center:~$ vlc http://dialup.kawaii-radio.net/listen.pls
VLC media player 1.0.6 Goldeneye
[0x8d38668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xb6f31768] es demux error: cannot peek
[0xb6f31768] main access error: Read error: Connection reset by peer
[0xb6f31768] access_http access error: failed to read answer
[0xb6f31768] main access error: Read error: Connection reset by peer
[0xb6f31768] access_http access error: failed to read answer
[0xb6f31768] access_mms access error: invalid HTTP reply 'ICY 200 OK'
[0xb6f2a428] main input error: open of `http://dialup.kawaii-radio.net:80/' failed: (null)

```oh my god.... XD
I already turned off my firewall and my connection is ok, something wrong here...... :O

edit:
it still didn't work on rhythmbox :O

---

### Post by mirwanda on 2010-07-06
anyone have the same problem?

---

