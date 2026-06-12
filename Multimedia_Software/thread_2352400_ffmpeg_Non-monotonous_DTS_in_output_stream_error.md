---
title: "ffmpeg Non-monotonous DTS in output stream error"
date: 2017-02-12
forum: Multimedia Software
---

### Post by YaPaY on 2017-02-12
Dear all,

I am trying the transcode satellite signals and send the receievers . I am using nginx+rtmp for it. Here is my command

```
ffmpeg -i http://192.168.1.59:81/zdfinfo/index.m3u8 -c:v libx264 -profile:v baseline -b:v 2000K -s 1280x720 -f flv -c:a aac -ac 1 -strict -2 -b:a 56k rtmp://127.0.0.1:1936/myapp/zdfinfohd
```

sometimes maximum 24 hour everything goes well but after that I am getting errors:

many of them:

```
[flv @ 0x32c9180] Non-monotonous DTS in output stream 0:1; previous: 95383795, current: 76360330; changing to 95383795. This may result in incorrect timestamps in the output file.
[flv @ 0x32c9180] Non-monotonous DTS in output stream 0:1; previous: 95383795, current: 76360352; changing to 95383795. This may result in incorrect timestamps in the output file.
[flv @ 0x32c9180] Non-monotonous DTS in output stream 0:1; previous: 95383795, current: 76360373; changing to 95383795. This may result in incorrect timestamps in the output file.
[flv @ 0x32c9180] Non-monotonous DTS in output stream 0:1; previous: 95383795, current: 76360394; changing to 95383795. This may result in incorrect timestamps in the output file.

```

Could you please help me?

---

### Post by mc4man on 2017-02-12
you could read thru here, (I didn't
[https://lists.ffmpeg.org/pipermail/ffmpeg-user/2013-May/015184.html](https://lists.ffmpeg.org/pipermail/ffmpeg-user/2013-May/015184.html)

---

### Post by YaPaY on 2017-02-12
thanks but there is no any suggest in this thread

---

### Post by keith-k on 2018-01-19
Try adding     -vsync 1 -async 1    before the -c:v libx264  if that doesn't work then try adding -vf fps=x (where x is the fps the video is, so if it's 23.976; x would = 24)

---

