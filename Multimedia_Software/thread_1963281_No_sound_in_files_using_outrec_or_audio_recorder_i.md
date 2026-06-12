---
title: "No sound in files using outrec or audio recorder in 12.04"
date: 2012-04-22
forum: Multimedia Software
---

### Post by ewan86 on 2012-04-22
I am trying to record the sound output of my computer. I have installed outrec (with all the required dependencies) and audio recorder. I also installed pulse audio volume control and set it to monitor of built in audio analogue stereo. I have also tried alsa mixer in the terminal but nothing seems to work. A file is created but no sound is present. Is there anything I have missed? Thank you.

---

### Post by mc4man on 2012-04-22
have you tried this one, works fine
[http://ubuntuforums.org/showthread.php?t=1952420](http://ubuntuforums.org/showthread.php?t=1952420)

---

### Post by ewan86 on 2012-04-22
Thanks for the reply, I added the PPA but it wouldn't update when I used sudo apt-get update. Said it had failed to fetch, along with medibuntu :S Just checked my sources and I actually already had that PPA enabled and I think I must therefore have the latest audio recorder.

---

### Post by moma on 2012-04-29
Hello,
Recording sound on my old Fujitsu Siemens AMILO li1718 laptop.
 
I had to install "pavucontrol" and set the configuration to "Analog Stereo Ouput". Now the recording works fine.

$ [COLOR="DarkGreen"]sudo apt-get install pavucontrol[/COLOR]
$ [COLOR="DarkGreen"]pavucontrol[/COLOR]

See picture:
[[img]http://bildr.no/thumb/1168830.jpeg[/img]](http://bildr.no/view/1168830)

---

### Post by ewan86 on 2012-04-29
> **moma said:**
> Hello,
Recording sound on my old Fujitsu Siemens AMILO li1718 laptop.
 
I had to install "pavucontrol" and set the configuration to "Analog Stereo Ouput". Now the recording works fine.

$ [COLOR="DarkGreen"]sudo apt-get install pavucontrol[/COLOR]
$ [COLOR="DarkGreen"]pavucontrol[/COLOR]

See picture:
[[img]http://bildr.no/thumb/1168830.jpeg[/img]](http://bildr.no/view/1168830)

Thank you so much, that worked perfectly. One question though, does that mean my microphone wont work until I set it back to 'analog stereo duplex' as input devices are missing when 'analog stereo output' is chosen in Pavucontrol?

---

### Post by moma on 2012-04-29
Oh my, you are right. The input devices are no longer available if we change the config to "Analog Stereo Ouput". 

I have to send a question to GStreamer's mailing list about this. Maybe there is an issue with the audio pipeline that causes this "empty file" problem. Seems like the outrec tool has a simlar issue.

I'll come back to you after the GStreamer/Pulseaudio people have given their reply. This may take several days. So long, stay optimist.

[COLOR="Red"]EDIT:[/COLOR] Recording works fine after I tampered with the settings in pavucontrol.
Now the recording works with "Analog Output Duplex", and it produces a valid audio file. I do not know why? Maybe this is due to yesterday's updates or there were some unwritten values in the settings. Investigation continues.

Yoy can test the recording with this loong command line. 
$ [COLOR="Green"]gst-launch pulsesrc name=source0  device="alsa_output.pci-0000_00_14.2.analog-stereo.monitor" ! level name=level ! queue ! audioconvert ! audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux ! filesink name=output-sink location=test1.ogg
[/COLOR]
Notice: You must replace the device id "alsa_output.pci-0000_00_14.2.analog-stereo.monitor" with your own device. Take a listing of your devices with:
$ [COLOR="Green"]pactl list | grep "Source" -A 5[/COLOR]

Notice: the word "Source" may have been translated to your language.

and take a device that ends with ".monitor". The .monitor can tap audio from a real audio hardware (from your audio card).
The above gst-launch command should produce a "test1.ogg" file. 
This is exactly what A.r does!

---

### Post by moma on 2012-04-30
Re-hello.
I added a comment to my prev. posting.

---

