---
title: "random failed recordings hvr-1950"
date: 2012-10-05
forum: Mythbuntu
---

### Post by Mad_Professor on 2012-10-05
My setup:
Mythbuntu 10.04
Mythtv 0.23.1
Tuners: Three hvr-1950 usb tuner using analog, no digital.
Using drivers [http://kernellabs.com/hg/~stoth/hvr1950-cc/](http://kernellabs.com/hg/~stoth/hvr1950-cc/) for closed captioning.

I've been having issue with these tuners. I was having a problem with them getting scrambled video after 24 hours randomly. Then I saw a new driver/firmware update on hauppauge website and did the firmware extract. It seemed to have fixed my problem and it also fixed blackscreen recording where if the tuners had not been used on the first boot up the first recording would record blackscreen and no sound.

But now I get randomly file size "b" on some recordings which sucks because that means I missed that episode. It does one at least every other day.

Well tonight I set a new show I've never seen before and within 10 minutes I decided to check to make sure it was recording through mythweb and it said it was but I got the dreaded file size "b." The status page said it was recording. I go out to the backend and look at the first usb tuner and the red light was on, so it was recording.
 
In the mythbackend log I get this..
```

2012-10-04 22:01:04.418 Started recording: Elementary "While You Were Sleeping": channel 1005 on cardid 1, sourceid 1
2012-10-04 22:01:06.845 DevRdB(/dev/video0) Error: Poll giving up
2012-10-04 22:01:06.870 MPEGRec(/dev/video0) Error: Device error detected
2012-10-04 22:01:06.883 DevRdB(/dev/video0): Stop(): Not running.
2012-10-04 22:01:09.396 DevRdB(/dev/video0) Error: Poll giving up
2012-10-04 22:01:09.408 MPEGRec(/dev/video0) Error: Device error detected
2012-10-04 22:01:09.419 DevRdB(/dev/video0): Stop(): Not running.
2012-10-04 22:01:11.945 DevRdB(/dev/video0) Error: Poll giving up
2012-10-04 22:01:11.971 MPEGRec(/dev/video0) Error: Device error detected
2012-10-04 22:01:11.982 DevRdB(/dev/video0): Stop(): Not running.
2012-10-04 22:01:14.504 DevRdB(/dev/video0) Error: Poll giving up
2012-10-04 22:01:14.517 MPEGRec(/dev/video0) Error: Device error detected
2012-10-04 22:01:14.560 DevRdB(/dev/video0): Stop(): Not running.
2012-10-04 22:01:17.155 DevRdB(/dev/video0) Error: Poll giving up
2012-10-04 22:01:17.181 MPEGRec(/dev/video0) Error: Device error detected
2012-10-04 22:01:17.193 DevRdB(/dev/video0): Stop(): Not running.

```
It's spammed for a good 10 minutes.

I cancelled the recording through mythweb and the mythbackend crashed but not the O/S.

After that, I went to watch live tv and it worked fine.

Checked dmesg but nothing to indicate a problem.

Anybody have any idea what this is and how it can be remedy?

---

