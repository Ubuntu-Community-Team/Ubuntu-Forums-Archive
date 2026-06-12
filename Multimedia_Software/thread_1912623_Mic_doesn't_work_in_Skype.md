---
title: "Mic doesn't work in Skype"
date: 2012-01-21
forum: Multimedia Software
---

### Post by mace200200 on 2012-01-21
So I'm running xubuntu 11.04 and have tried every guide I could find online to get my Mic to work in Skype. First I used pulse audio, tried all three Mic options (Mic 1, Mic 2, and line in), then I installed pavucontrol and tried the same thing, but like before the bar would move telling it was working there but no matter what it still never works in Skype. anything else I can try?

---

### Post by Rodney9 on 2012-01-21
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


Fix internal mic for use with Skype

[http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol](http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol)

Thanks To ZekeGraal

---

### Post by mace200200 on 2012-01-21
> **Rodney9 said:**
> These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


Fix internal mic for use with Skype

[http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol](http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol)

Thanks To ZekeGraal


Thank you for the links i will give them a try a little later today and post back if they worked or not. :D

---

### Post by mace200200 on 2012-01-21
nope nothing worked, its not an internal mic either, i have it plugged into the back of my desktop, works every where else just never once in skype.

---

### Post by mace200200 on 2012-01-21
(bump) anyone got anything else for me to try? Still have no idea what else to try that i havn't already :frown:

---

### Post by jelli32 on 2012-07-14
I am using precise pangolin and I got my internal microphone to work. Tested it out with a friend and he said he could hear me well. Maybe this can help you. Here's what I did:

First, open up Mixer (click on the audio button at the top of your screen). Mixer is where you can adjust the volume for different sources. If you can see the volume controls for Microphone and Mic Boost, make sure they're not muted. If you can't see them, click the "Select Controls" button at the bottom and check the Microphone and Mic Boost options. Then, increase the volume for both.

Secondly, go to Multimedia and click on PulseAudio Volume Control. Make sure the volumes for Playback, Recording, and Output Devices are not muted, and try to increase the volume for each. Go to the Internal Devices tab and next to where it says "Port," select the source for your microphone. In my case, I selected "Internal Microphone" because I have a built-in microphone for my laptop. If you are using an external microphone, select a different option from the drop-down list. Make sure the "mute" icon at the top is not selected. Next, go to where it says "Front Left" and "Front Right" and increase the volumes for your microphone.

Test it out with a friend or family member during Skype, Google+, or some other videochatting service and see whether they can hear you. I set the volumes high initially just to make sure people can hear me.

---

### Post by winecurmudgeon on 2013-01-08
I couldn't get Skype to work with the mic on my Microsoft web cam or my Samson Go Mic, so you can imagine the frustration. I found one solution, and it involved upgrading the alsa drivers. The first thing I did was go [here]("https://wiki.ubuntu.com/Audio/HDAGeneric") to find out if my sound card was supported. Turns out it wasn't, that I had a Realtek ALC 888. This card has shown up in various Skype/mic problem posts that I have found.

Then I upgraded the drivers, using this [post]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules"). That did the trick. Best yet, not only does Skype now work, but it doesn't look like upgrading the drivers screwed up the sound on anything else -- music player, VLC, etc.

---

