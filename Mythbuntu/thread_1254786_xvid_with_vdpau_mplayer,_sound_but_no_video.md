---
title: "xvid with vdpau mplayer, sound but no video"
date: 2009-08-31
forum: Mythbuntu
---

### Post by laffinet on 2009-08-31
Hi!

I'm running mythbuntu 9.04 with the avenard testing repos, current nvidia driver 190.25

I've set mythtv up to play videos via mplayer, the command I'm using is:

```
mplayer -ao alsa -zoom -quiet -fs -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau
```

When I select an h264 encoded .mkv file everything works fine, player opens in full screen, video plays etc.

Trying to play a xvid encoded .avi file doesn't work though.

Mythtv reamins at the "loading video" screen, sound starts and plays normally but there's no video. mplayer is running (I can see it in "top") but there's no mplayer window anywhere (doesn't open in the background, too).

Starting the same video from the command line with

```
mplayer -ao alsa -zoom -quiet -fs -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, file.avi
```

works just fine. 

Using

```
mplayer -ao alsa -zoom -quiet -fs -vo xv %s
```

works fine from within mythtv as well.

---

### Post by laffinet on 2009-09-01
Found the solution myself.

Line has to read

```
mplayer -ao alsa -zoom -quiet -fs -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,
```
The "," at the end is important. It tells mplayer to try other default codecs if none of the previously listed work.

---

