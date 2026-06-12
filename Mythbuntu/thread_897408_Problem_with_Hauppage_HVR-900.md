---
title: "Problem with Hauppage HVR-900"
date: 2008-08-22
forum: Mythbuntu
---

### Post by thefixxxer on 2008-08-22
Hi all!
I'm new to this fantastic forum and I want to thanks all for the good work :)
I've a problem related to Hauppage HVR-900 DVB-T usb key. Seems that em28xx drivers are up & running but I'm not sure that everything works fine...
How can I check via terminal command (I use an SSH console)?
How can I test it and make a sort of "channel scan"?
Thanks for your help and best regards

---

### Post by thefixxxer on 2008-08-22
> **thefixxxer said:**
> Hi all!
I'm new to this fantastic forum and I want to thanks all for the good work :)
I've a problem related to Hauppage HVR-900 DVB-T usb key. Seems that em28xx drivers are up & running but I'm not sure that everything works fine...
How can I check via terminal command (I use an SSH console)?
How can I test it and make a sort of "channel scan"?
Thanks for your help and best regards

Now I've checked and with dmesg I receive this output

[   36.468626] Table at 0x24, strings = 0x1e82, 0x186a, 0x0000
[   36.469500] attach_inform: tvp5150 detected.
[   36.536238] tvp5150 1-005c: tvp5150am1 detected.
[   38.519905] successfully attached tuner
[   38.524019] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[   38.540018] em28xx #0: V4L2 device registered as /dev/video0
[   38.540033] em28xx #0: Found Hauppauge WinTV HVR 900
[   38.540084] usbcore: registered new interface driver em28xx
[   38.804418] em2880-dvb.c: DVB Init
[   39.248349] DVB: registering new adapter (em2880 DVB-T)
[   39.248364] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[   39.248862] Em28xx: Initialized (Em2880 DVB Extension) extension

and when I try with scan -c I receive this one

root@andromeda:~# scan -c
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)
Done.

someone can help me????
Thanks!!

---

### Post by thefixxxer on 2008-08-25
> **thefixxxer said:**
> Now I've checked and with dmesg I receive this output

[   36.468626] Table at 0x24, strings = 0x1e82, 0x186a, 0x0000
[   36.469500] attach_inform: tvp5150 detected.
[   36.536238] tvp5150 1-005c: tvp5150am1 detected.
[   38.519905] successfully attached tuner
[   38.524019] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[   38.540018] em28xx #0: V4L2 device registered as /dev/video0
[   38.540033] em28xx #0: Found Hauppauge WinTV HVR 900
[   38.540084] usbcore: registered new interface driver em28xx
[   38.804418] em2880-dvb.c: DVB Init
[   39.248349] DVB: registering new adapter (em2880 DVB-T)
[   39.248364] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[   39.248862] Em28xx: Initialized (Em2880 DVB Extension) extension

and when I try with scan -c I receive this one

root@andromeda:~# scan -c
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)
Done.

someone can help me????
Thanks!!

Please...can u help me in solve this issue?
Thanks so much for your help ;)

---

