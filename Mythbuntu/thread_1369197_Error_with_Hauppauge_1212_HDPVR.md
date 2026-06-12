---
title: "Error with Hauppauge 1212 HDPVR"
date: 2009-12-31
forum: Mythbuntu
---

### Post by jshaw16 on 2009-12-31
I am using Mythbuntu 9.10  x 64.  kernal 2.6.31.16- generic. I am trying to install the Hauppauge 1212 HDPVR  using instructs on  [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR) and I am getting the following error when I try to run Watch TV on the front end. This is the error in the backend log:

2009-12-31 11:54:49.630 TVRec(1): Changing from None to Watching WatchingLiveTV
2009-12-31 11:54:49.699 TVRec(1): HW Tuner: 1->1
2009-12-31 11:54:50.304 ret_pid(6562) child(6562) status(0x0)
2009-12-31 11:54:50.361 External Tuning program exited with no error
2009-12-31 11:54:50.627 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-12-31 11:54:50.928 MPEGRec(/dev/video0) Error: StartEncoding failed
            eno: Resource temporarily unavailable (11)
2009-12-31 11:54:50.986 MPEGRec(/dev/video0) Error: Failed to start recording
2009-12-31 11:55:37.197 TVRec(1): Changing from Watching WatchingLiveTV to None

Is there a lib file to resolve this? any ideas? 

When I run 
sudo modprobe hdpvr it just returns which I guess is correct? 

when I run
locate cx88-dvb.ko |grep `uname -r`
I get what appears to be appropriate data. 

when I run 
cat /dev/video0 > test.ts
it returns  cat: write error: Bad address

Thanks!

---

### Post by jshaw16 on 2010-01-02
I resolved the problem by learning the difference between component and composite and setting up all three component and composite and s-video in the input connections panel.

---

