---
title: "[SOLVED] best way to get recordings off comcast dvr"
date: 2008-04-08
forum: Mythbuntu
---

### Post by kameleon25 on 2008-04-08
I have a DVR from comcast that I have recorded a few things on until I can get a spare cable box to get past channel 100 on my mythbuntu box. I would like to get the recordings to my mythbuntu box so I can run a transcoding job on them and shrink down to my usual file size and store. I have a PVR-500 in my mythbuntu box and the DVR of course has composite, component, and HDMI out. What would be the best way to get the recordings off of the DVR and onto the mythbuntu box so I can flag commercials and transcode them? I am thinking just hooking up the DVR to the composite in on one of the tuners, hit record on teh mythbuntu box, and hit play on the DVR. But then how do I get it to record from there since there is no "channel" there.

On a side note, what would be the best way to add a spare cable box so I can record above channel 100? The pvr-500 cannot tune above that channel. I don't care about the HD channels I get. Just mainly the good stuff is above 100. Like the Science Channel, Military Channel, etc. Any good pointers?

Thanks in advance.

---

### Post by w0lfpaws on 2008-04-08
the firewire works , if you want to copy the whole files

---

### Post by newlinux on 2008-04-09
Firewire won't work if your recording is a 5c protected program. If you don't care about HD you could just capture it your recording analog from through your PVR-500 outside of myth. You can do it commandline:

Start the program on your DVR. Then type:
```

cat /dev/video1 > filename.mpg

```

Change video1 to whatever your pvr-500 capture device name is. Then hit ctrl c when you are done recording. Make sure myth isn't using the tuner at the time. If you wanted to schedule this to start and stop you could use the "at" command to give it a time to kill the process (end the recording).

As far as regularly recording from a cable box, the most reliable way is to output the analog output of your cable box (s-video or composite) to your PVR-500. Setup a video source that has the cable channels you want. Then you'll need to setup a way to change the channels on your cable box through myth. You can use firewire or an IR blaster to change channels, or even a serial connection. Plenty of info on doing all of them on this forum and in the documentation if you do a little searching.

---

### Post by kameleon25 on 2008-04-09
Thank you for the info. I will try that cat command. Then I should be able to import it into Myth to flag the commercials then I can manually run my transcode job to cut the commercials and convert to xvid. 

On the setting up of the cable boxes, I had read up some on that. I was mainly just shooting for what others had experience with using comcrap and which cable boxes. I know that is not what I said but I choose words badly sometimes. lol

Thanks again!

---

### Post by newlinux on 2008-04-09
I use firewire to capture channels on my dCT-6200 and to change channels for capture via my pvr-150's s-video input for channels that are 5c protected. I have also don this with a DCH -xxx models and DCT 6412 and DCT -3412. This is all with comcast... But what stations are 5c encrypted vary from region to region... But you can always get them all with standard definition analog capture.

---

### Post by Dilligaf on 2008-04-09
@newlinux

Just curious , how did you overcome the firewires tendency to change port and node whenever you reboot?

Mike

---

### Post by newlinux on 2008-04-09
I don't reboot very often (my current uptime on that machine is 151 days). But when I did it changed sometimes, and I'd always check after a reboot and adjust mythtv-setup accordingly.

---

### Post by kameleon25 on 2008-04-10
Thanks for the tip on the firewire. Unfortunatly I have the only HD DVR box they have in this area. It is an SA 8300HDC. I have not heard good things about it and firewire. But I will see if I can get one of those listed for my mythbox. Thanks!

---

### Post by kameleon25 on 2008-04-10
newlinux: I just did a quick and dirty test this morning before leaving for work to try to get that cat command to work. Worked great except it recorded whatever channel the tuner was set to on the myth box. I will search on how to change it from the internal tuner to the composite in and try again.

---

### Post by newlinux on 2008-04-10
> **kameleon25 said:**
> newlinux: I just did a quick and dirty test this morning before leaving for work to try to get that cat command to work. Worked great except it recorded whatever channel the tuner was set to on the myth box. I will search on how to change it from the internal tuner to the composite in and try again.

I should have mentioned this:
```

ivtvctl -n
```

will list your inputs

```
ivtvctl -p NUM
```

where NUM is the number of the input you see outputted from the previous command that your cable box is connected to. Oddly, it seems even the single tuner models list to s-video/composite inputs so you may need to try both. That should get it on the right input for recording...

---

### Post by kameleon25 on 2008-04-11
Thank you for the help. I searched and found the command that does basically the same thing:

v4l2-ctl -d /dev/video0 -n

and then

v4l2-ctl -d /dev/video0 --set-input=NUM

By using that I was able to switch from the internal tuner to the composite and back with no problems. Though I like yours better as it is less typing. lol. Thanks again!

---

