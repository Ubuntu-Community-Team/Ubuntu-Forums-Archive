---
title: "mt-daapd transcoding problem"
date: 2009-04-30
forum: Multimedia Software
---

### Post by tropico2 on 2009-04-30
Hi all

i'm using mt-daapd to share my music with my Soundbridge.

Since migration to jaunty, my ogg files are not transcoded to wav anymore and cannot be played on the soundbridge.

in syslog, I found these messages :

[FONT=Courier New]Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: undefined symbol: avcodec_decode_audio[/FONT]

Any idea ?

Thanks.

---

### Post by wesg on 2009-05-01
I'm starting to think that mt-daapd is not compatible with Jaunty, because I've experienced a complete inability to run it properly. I'll keep looking!

---

### Post by dontodd on 2009-05-24
I recently upgraded to Jaunty and finally got around to trying to get mt-daapd / Firefly set up again. What a pain this was. I always built Firefly from source in the past because the earliest versions in Ubuntu didn't handle ogg transcoding. This time, however, it looks like Firefly isn't being developed or even maintained much. I couldn't get it to configure due to an error about avcodec.h not being found. I told the configure script where to find it but still no joy.

Soooo I decided to try installing from aptitude as I read about the version in the repositories being able to handle the transcoding. Installed it and ran into problems right off the bat. Fix the problems with avahi with the last two posts in this thread: [http://ubuntuforums.org/showthread.php?p=7335179&highlight=firefly#post7335179](http://ubuntuforums.org/showthread.php?p=7335179&highlight=firefly#post7335179)

Then my soundbridge could see the server but it couldn't play any ogg files. Sooo, edit /etc/mt-daapd.conf and comment out the items in the plugin section so it won't try to use ffmpeg to do transcoding. That section looks like this now:
[plugins]
#plugin_dir = /usr/lib/mt-daapd/plugins
#plugins = rsp.so,ssc-ffmpeg.so

Then where it says that the transcoding script is not needed because of ffmpeg, uncomment the codectypes that need to be transcoded:

# Not needed because ffmpeg is enabled (all file types transcoded to wav.
# If this behavior is undesired, see the [plugins] section and disable it,
# or selectively disable codecs below with the never_transcode option.)
# -joshk
ssc_codectypes = ogg,flac,alac

Then uncomment the pointer to the transcoding script:

ssc_prog = /usr/bin/mt-daapd-ssc.sh

But wait, there is no transcoding script! You can either get it from firefly svn or, easier, from here: [https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/139903/comments/6](https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/139903/comments/6) . That also has the wavstreamer binary you need. So, from that zip file, put mt-daapd-ssc.sh and wavstreamer in /usr/bin.

But wait, there's more! One of those wants to use an old version of flac, so create a link for it: sudo ln -s /usr/lib/libFLAC.so.8.2.0 /usr/lib/libFLAC.so.7

After all of that, I now have the same functionality I had in Intrepid. That's progress for you isn't it? I hope this saves somebody some hair. I tried different media servers but couldn't get anything else to work. At least my soundbridge is no longer a paper weight.

---

### Post by KrisWillis on 2009-07-26
dontodd, thanks for your post it really helped me getting flac playable in iTunes again.

---

### Post by xodis on 2009-09-04
It works!

---

