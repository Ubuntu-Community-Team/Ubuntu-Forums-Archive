---
title: "VLC stops playing when browsing Samba share in Dolphin"
date: 2010-04-11
forum: Multimedia Software
---

### Post by infecticide on 2010-04-11
Hey Folks,

Got a strange problem, I have a NAS with video files on it mounted via CIFS to my desktop.

I can play the videos with no problems.

The problem begins when I start a video and attempt to browse around the CIFS share, when I do so, VLC stops playing the video with no apparent errors.

Any ideas?

---

### Post by infecticide on 2010-04-11
It always seems that once you write down your problems you get an idea.

:p

I opened the Messages dialog in VLC and cranked up the Verbosity to max and surfed the CIFS share and this is what comes out when it stops playing.

> avi warning: failed reading data
avi warning: failed reading data
avi warning: failed reading data
avi warning: all tracks have failed, exiting...
main debug: EOF reached
main debug: waiting decoder fifos to empty
main debug: waiting decoder fifos to empty
main debug: waiting decoder fifos to empty
main debug: waiting decoder fifos to empty
main debug: waiting decoder fifos to empty
main debug: finished input
main warning: can't get output picture
main warning: can't get output picture
avcodec debug: ffmpeg codec (MPEG-4 Video) stopped
main debug: removing module "avcodec"
main debug: killing decoder fourcc `XVID', 0 PES in FIFO
main debug: [0] 2 0
main debug: [1] 2 0
main debug: [2] 2 0
main debug: [3] 2 0
main debug: [4] 2 0
main debug: [5] 2 0
main debug: [6] 2 0
main debug: [7] 4 0
main debug: [8] 2 0
main debug: [9] 2 0
main debug: [10] 1 0
main debug: [11] 2 0
main debug: [12] 4 0
main debug: [13] 2 0
main debug: [14] 4 0
main debug: saving a free vout
main debug: removing module "mpeg_audio"
main debug: killing decoder fourcc `mpga', 0 PES in FIFO
main debug: removing module "mpgatofixed32"
main debug: removing module "scaletempo"
main debug: removing module "bandlimited_resampler"
main debug: thread ended
main debug: removing module "alsa"
main debug: removing module "float32_mixer"
main debug: releasing aout
avi debug: free chunk avih
avi debug: free chunk strh
avi debug: free chunk strf
avi debug: free chunk LIST
avi debug: free chunk strh
avi debug: free chunk strf
avi debug: free chunk LIST
avi debug: free chunk LIST
avi debug: free chunk ISFT
avi debug: free chunk LIST
avi debug: free chunk JUNK
avi debug: free chunk LIST
avi debug: free chunk idx1
avi debug: free chunk RIFF
avi debug: free chunk LIST
main debug: removing module "avi"
main debug: removing module "stream_filter_record"
main debug: removing module "access_file"
main debug: Program doesn't contain anymore ES
main debug: thread ended
main debug: dead input
main debug: changing item without a request (current 0/1)
main debug: nothing to play
main debug: destroying useless vout
qt4 debug: IM: Deleting the input
qt4 debug: Updating the geometry
qt4 debug: Updating the geometry
qt4 debug: Qt: Entering Fullscreen
main debug: TIMER input launching for 'Mythbusters 525 - Airplane Hour.avi' : 2569.505 ms - Total 2569.505 ms / 1 intvls (Avg 2569.505 ms)
qt4 debug: releasing video...
qt4 debug: Video is not needed anymore
qt4 debug: Updating the geometry
main debug: removing module "qt4"
main debug: removing module "xvideo"
main debug: removing module "blend"
main debug: removing module "freetype"
main debug: removing module "yuvp"
main debug: removing module "swscale"


So it would appear that VLC is not buffering enough video to compensate for a temporary interruption in service while the NAS services other requests.

There are no dmesg errors regarding the CIFS mount.

Still at a loss as to how to fix this issue though...

---

