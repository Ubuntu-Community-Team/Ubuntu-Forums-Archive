---
title: "Xine problem!"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by ar0n on 2006-06-18
Hello!

After using debian for years I`ve switched to ubuntu 6.06. I`ve used debootstrap to install it. After installing compiz and Xgl I`ve got everything working except amarok and kaffeine.

Kaffeine and amarok uses xine.
When I start a video in kaffeine i get this error:
```

Can't init Audio Driver 'alsa' - trying 'auto'...

>>> Check if another program already uses PCM <<<
snd_pcm_open() failed:-2:No such file or directory

```
Screenshot: 
[IMG]http://public.aron.ws/Screenshot-1.png[/IMG]

Amarok just plays an audio file in 1 sec and stops.

In System -> Preferences -> Sound my default soundcard is listed
If I restart alsa I get this strange error:
```

root@aron:~# /etc/init.d/alsasound restart
Shutting down sound driver: done
Starting sound driver: snd-intel8x0 done
/usr/sbin/alsactl: load_state:1236: No soundcards found...
root@aron:~# uname -a
Linux aron 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux

```

```

root@aron:~# lspci | grep audio
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
root@aron:~#

```

Oh and if I set ALSA output in XMMS the sound is working so the problem is with xine i think ...

Any help will be appreciated!

---

### Post by georgeous on 2006-06-18
Hi! I'm having a similar problem with amarok, even after installing the gstreamer libraries, etc. It still won't play mp3s, it just opens the file and completes it instantaneously, as you say.

XMMS works for me though...

I'm afraid i don't know much more than that though. All other sound on my system is fine, and i haven't recieved a single error message with any audio player, although only xmms and real have managed to play mp3s.

Can anyone point me in the right direction for trouble-shooting further?

George

---

### Post by ar0n on 2006-06-19
[QUOTE=georgeous]Hi! I'm having a similar problem with amarok, even after installing the gstreamer libraries, etc. It still won't play mp3s, it just opens the file and completes it instantaneously, as you say.

XMMS works for me though...

I'm afraid i don't know much more than that though. All other sound on my system is fine, and i haven't recieved a single error message with any audio player, although only xmms and real have managed to play mp3s.

Can anyone point me in the right direction for trouble-shooting further?

George[/QUOTE]

Hello!

I think Ive solved it!

Ive purged libxine-main1.
```

dpkg --purge libxine-main1
apt-get install libxine-main1 libxine1c2 libxine-extracodecs libarts1-xine

```

In amarok:
Settings -> Configure Amarok... -> Engine -> Select output plugin for xine 'esd'

In kaffeine:
Settings -> xine Engine Parameters -> Audio -> Select 'esd' as driver ..


Sound now works for me !!! Coool :D
I hope this will help you!

Best wishes,
Aron

---

