---
title: "HDHomeRun works OK, HD-PVR drivers are dead"
date: 2010-03-19
forum: Mythbuntu
---

### Post by trevmar on 2010-03-19
I have been using Mythbuntu, fully updated, including weeklies, with a dual HDHomeRun box for some time. No problems.

I decided to buy a Hauppauge HD-PVR so I could record output from my set top box. I bought a unit from Frys, sticker on bottom says "rev E1"

The HD-PVR is recognized by MythTV, but will not stream LiveTV.

From the command line I have set up modprobe to default to the correct inputs, and the configuration looks OK, I can control the box encoding parameters OK. But when I do a 
cat /dev/video0 > /dev/null

I get this log (from dmesg)

[  752.953578] hdpvr 1-5:1.0: video signal: 720x480@30hz
[  752.957567] hdpvr 1-5:1.0: encoder start control request returned 0
[  752.976581] hdpvr 1-5:1.0: config call request for value 0x700 returned 1
[  752.976598] hdpvr 1-5:1.0: streaming started
[  752.976616] hdpvr 1-5:1.0: hdpvr_read:438 buffer stat: 64 free, 0 proc
[  752.976729] hdpvr 1-5:1.0: hdpvr_submit_buffers:205 buffer stat: 0 free, 64 proc
[ 1784.668557] hdpvr 1-5:1.0: config call request for value 0x800 returned 1
[ 1784.668575] hdpvr 1-5:1.0: transmit worker exited
[ 1785.984070] hdpvr 1-5:1.0: used 0 urbs to empty device buffers

I have the debug level set to 7:
options hdpvr default_audio_input=2 default_video_input=0 hdpvr_debug=7 video_nr=0

and so I should be seeing buffer transfers in the logs. There are none. The blue light on the top of the HD-PVR is not illuminated, and apparently nothing is streaming. If I send the output to a file (instead of null) the file is zero length.

Is there a more up-to-date driver available than the one in the mythbuntu repositories? Or is mythtv-backend grabbing the box and messing with the initialization? This is sooooo frustrating.



ps: the HD-PVR works well on Windoze...

---

### Post by trevmar on 2010-03-20
OK - fixed.
The HD-PVR box doesn't put out any digital data unless its inputs are streaming analog data to it. Hmmm. I plugged in the Optical SPDIF, and put (active) plugs into every other input socket on the PV-DVR and gradually figured it out.

Mythbuntu has three setup configurations in backend setup, and then a variety of configurations in the frontend (Recording Profiles) all of which need to be set up. But, with that all done, I am at least getting video now...


I just have to figure out how to get the channels on my cable box to change:frown:

---

### Post by rhpot1991 on 2010-03-23
> **trevmar said:**
> 
I just have to figure out how to get the channels on my cable box to change:frown:

IR Blasting and Firewire channel changers are the most popular choices.  If you can do firewire then there are some scripts in the contrib directory (/usr/share/doc/mythtv-backend/contrib/) you can try out.

---

### Post by p1um1oco on 2010-05-23
> **trevmar said:**
> OK - fixed.
The HD-PVR box doesn't put out any digital data unless its inputs are streaming analog data to it. Hmmm. I plugged in the Optical SPDIF, and put (active) plugs into every other input socket on the PV-DVR and gradually figured it out.

Mythbuntu has three setup configurations in backend setup, and then a variety of configurations in the frontend (Recording Profiles) all of which need to be set up. But, with that all done, I am at least getting video now...


I just have to figure out how to get the channels on my cable box to change:frown:

I have both the HDHomeRun and just added the HD-PVR, now the frontend no longer sees the channels or can change to the HDHomeRun.  Not sure what happened.

On the other hand I have heard that the HD-PVR can use IR to transmit and change channels on the DirecTV reciever, but I am not sure how to get that working as of yet.

-Dave

---

### Post by trevmar on 2010-05-24
Dave,
I wouldn't bother to spend much time on getting the HD-PVR IR blaster functional. I got mine working, but it locks up when the box is streaming video and you send an IR-blaster command. Others have reported this, as well.

I bought an "Linksys MCE Remote Control + HP Receiver" mceusb blaster on Ebay ($20 from HongKong) and it worked straight out of the box...

I haven't had time to look into the problem discussed above. I am so busy these days...

---

