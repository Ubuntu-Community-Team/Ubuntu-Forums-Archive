---
title: "Keep losing ability to monitor and record PC  audio"
date: 2010-12-05
forum: Multimedia Software
---

### Post by Buffalo_Guy on 2010-12-05
I am a recent convert to Ubuntu, 10.10  Over the past few months  Ihave continually added applications.  I have studied pulseaudio and have been generally pleased with the audio quality.  Here is my problem.  At various times I lose the ability to record audio playing through the computer.  At times it has worked flawlessly.  Now, when I go to PA volume control and try to monitor the internal sound as I have done in the past, there is no stream.  I have checked all mixer settings.  All is set to capture and at full volume. When I am playing sound from any source and go the the volume control, select monitor of analog stereo duplex and use the PA recording meter - no activity.  Now here is the best part.  When I create a VMware clean installation of Ubuntu the sound records perfectly.  I have studied the two installations to no avail to find a difference.  Can anybody offer some troubleshooting thoughts to get this corrected.  It must be something in software.  Many thanks,  Steve

---

### Post by Buffalo_Guy on 2010-12-05
UPDATE SOLVED SORT OF:
                      p { margin-bottom: 0.08in; }                      p { margin-bottom: 0.08in; }                      p { margin-bottom: 0.08in; }  After spending hours comparing installations I believe I have come across the source of the problem however the only way I could rectify it was to go to a previous backup where sound was working correctly. See below the PA default sink and source.(See attachment)  
 

 Default sink: Ladspa_output.mbeq_1197.mbeq
 

 Default source:alsa_input.pci-0000_00_14.2.analog-stereo
 

 What I have found is that somehow, presumably after installing another software application - but who knows, the default source gets changed to something other than the input source .   One of the output sources gets installed as the default source ,making it impossible to record any pc audio although all sound output is unaffected.  Somehow the input source becomes inoperable.  Any attempt to change the source back to this device results in PA not being able to connect and hence no PA.  Any PA experts out there who have an idea on this one? For now I am good but I am watching every app I install and looking for changes

---

### Post by Buffalo_Guy on 2010-12-12
UPDATE - LOST ABILITY AGAIN TO RECORD PC BASED AUDIO - FOUND SOLUTION

After spending hours studying the intricacies of Pulseadudio and trying to make adjustments via PA's command line interpreter, I came across a thread that offered a solution to another problem but solved mine.  Deleting or renaming the user's hidden pulse directory (/home/username/.pulse) followed by restarting pulseaudio or the computer restored my ability to record audio from my computer.

---

