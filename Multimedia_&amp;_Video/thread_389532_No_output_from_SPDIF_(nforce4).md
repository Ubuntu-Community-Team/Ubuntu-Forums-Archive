---
title: "No output from SPDIF (nforce4)"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by Innova on 2007-03-20
My SPDIF output is not working at all. I have searched these forums, and nothing that I have found has worked for me.

I have a EPoX 9NPA nForce4 based motherboard. I do have sound through the Line-out (lime green) jack, but the optical spdif is not working at all. I do have this computer hooked up to my home theater, so getting this to work is crucial.

Here is the output from aplay -l:

wesley@mediacenter:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0


When I try speaker-test -c6, the program runs fine, and I get output through the line-out, but nothing through the optical out. I also tried: speaker-test -c6 -Dplug:surround51

And this errors out:

wesley@mediacenter:~$ speaker-test -c6 -Dplug:surround51

speaker-test 1.0.11

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 3 to 5461
Period size range from 3 to 5461
Using max buffer size 5461
Periods = 4
was set period_size = 5461
was set buffer_size = 5461
buffer to small, could not use
Unable to determine current swparams for playback: Input/output error
Setting of swparams failed: Input/output error


I have tried various different .asoundrc files, but none of them seemed to help.

Does anyone have any suggestions on how I can get my spdif to work?

---

### Post by Cappy on 2007-03-20
I googled on "Optical SPDIF" because I didn't know what it was and I found this:
[http://www.nforcershq.com/forum/next-vt58251.html?postdays=0&postorder=asc&&start=10](http://www.nforcershq.com/forum/next-vt58251.html?postdays=0&postorder=asc&&start=10)

also (probably better):
[http://www.mythtv.org/wiki/index.php/Enabling_nForce4_optical_SPDIF_output](http://www.mythtv.org/wiki/index.php/Enabling_nForce4_optical_SPDIF_output)

---

### Post by Innova on 2007-03-20
Thank you!  With that first link I finally have sound coming out of my SPDIF.  However, it is already decoded.

Does anyone know how to get the AC3 signal passed through so my external receiver can do the decoding?  I found a few other people asking this question, but have seen no answers.

---

