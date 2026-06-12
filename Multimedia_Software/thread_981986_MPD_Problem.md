---
title: "MPD Problem"
date: 2008-11-14
forum: Multimedia Software
---

### Post by cos4 on 2008-11-14
Hi

I installed mpd and added support for pulseaudio by editing the /etc/mpd.conf file
```
audio_output {
        type    "pulse"
        name    "My MPD PulseAudio Output"
        server  "localhost"   # optional
        sink    "alsa_output" # optional
}
```
I've also enabled network access to pulseaudio.

I did create a db which somehow failed?!
```
$ sudo /etc/init.d/mpd start-create-db 
[sudo] password for isildur: 
 * Starting Music Player Daemon mpd                                                  * creating /var/lib/mpd/tag_cache... 
                                                                             [fail]
isildur@desktop:~$ sudo cat /var/log/mpd/errors.log
isildur@desktop:~$ 

```
(there are possibly some wma files in one of the dictionaries if they are ignored I don't care).

When I open ncmpc, however I find a db and all my music is in. But when I want to play a title it is added to the playlist but not played(after hitting play the replay does not start).

What could be the reason for that? Can anyone help me?


Regards,
cos4

---

