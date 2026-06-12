---
title: "Live TV issue - VDPAU issue?"
date: 2011-09-21
forum: Mythbuntu
---

### Post by Al_Vampyre on 2011-09-21
I've just added a GT220 to my combined FE/BE myth box so I think this may be a VDPAU issue.

The machine is running an Opteron processor but using the 32 bit Mythbuntu(PAE)10.10 with 0.24.1 fixes. I'm running 2 Nova-T 500's but using a MCE remote. I've been holding off upgrading because everything has been working fine up until now and Natty doesn't add anything new to the mix.

Since adding the GT220 I've been getting short bursts (about 1 sec) of repeating audio which happens every so often when watching LiveTV. At first when I tailed the frontend log I thought that the occasional 'Waited 100ms for video buffer' error was coinciding with the repeating audio but I've since noticed that the audio repeats with absolutely nothing showing in the frontend log.

Is there anywhere else I can look to find out what's causing this or has anyone else experienced this?

---

### Post by krisbee2000 on 2011-09-26
Since nobody has replied, and I have very limited knowledge, my suggestions would be to change the viewing profile to vdpau:slim (in the frontend setup) and increase the ringbuffer (which you can do in mythtv-setup).
 
HTH,
Kris

---

### Post by Al_Vampyre on 2011-09-26
Thanks Kris, changing the vdpau profile hasn't made any difference and I thought that there was no longer a ringbuffer for live TV but I appreciate the answer.

---

### Post by Al_Vampyre on 2011-09-30
What I can't understand is that there is nothing showing up in any of the logs when it happens. I'm getting nothing in mythfrontend.log, xorg log, messages, syslog.

There seems to be slight slowdown of the video and then the audio repeats and then everything goes back to normal. Am I right in thinking that if it was a broadcast issue then because mythtv is playing the stream exactly as received nothing would show in the logs?

---

### Post by krisbee2000 on 2011-09-30
If it was a broadcast issue, you could save the file as you record it and see the exact same issue in the same spot over and over.

I did notice there are some advanced audio setup screens in the Frontend under General that maybe you want to double-check.

Also, normally in any system, I will go out of my way to remove pulseaudio, even if I am using alsa, just to make sure it isn't highjacking anything (which logically it shouldn't, but once I had some audio issue long ago that I can't remember and that was the solution).

Of course, have you tried switching to oss emulation and seeing what happens?

---

