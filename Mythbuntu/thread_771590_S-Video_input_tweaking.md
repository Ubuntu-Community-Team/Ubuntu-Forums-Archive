---
title: "S-Video input tweaking?"
date: 2008-04-27
forum: Mythbuntu
---

### Post by MrChips on 2008-04-27
Hey I'm really new to the TV tuner rig in Linux.  I had a little difficulty getting my S-Video input to show up in Myth TV.  I am using the same video source as the tuner input and that seemed to work.  Now it has a slight flicker which I can't seem to get rid of.  Is there any utility to tweak the input signal?

---

### Post by MrChips on 2008-05-01
Or best refresh rate?  Best video settings?  There is also a noticeable lag between the sources.

---

### Post by volkswagner on 2008-05-02
Have you tried replacing the cable?  Do you have a good picture when directly connected to the tv?

---

### Post by MrChips on 2008-05-02
There is just an annoying flicker in MythTV from the S-Video input channel.  As well as just poor picture quality.  However when I open the S-Video channel in the VLC player it is near perfect.  If it is really difficult to tweak I would just need a program that records the S-Video input.  If VLC would do that my problem would be solved, but as far as I know VLC only records streaming video.

MythTV seems to do fine for watching and recording the TV signal just not S-Video.

Thanks for the response.8-)

---

### Post by volkswagner on 2008-05-03
Please provide details on your setup. What tuner, how is it connected, cable, satellite, etc.

---

### Post by MrChips on 2008-05-03
A WinTV-PVR 150 MCE with two inputs. Tuner input connected to cable service.  S-Video input connected to another computer's TV-output running through a Yamaha surround reciever which also has a VCR hooked up to it. Video card on the Mythbuntu box is a Nvidia GeForce 5200.  Video card on the incoming signal comp is an ATI Radeon X1600.

I have tried adjusting the flicker level on the ATI card with minimal results in MythTV.  The picture on the VLC player is flawless.

---

### Post by volkswagner on 2008-05-03
What version of Mythbuntu and Mythtv are you running?  Check your logs during the capture on s-vid.  Logs are in /var/log/mythtv/frontend.log and /var/log/mythtv/mythbackend.log.

---

### Post by MrChips on 2008-05-03
Mythbuntu 8.04
MythTV 0.21

I'm thinking about just ditching Myth and finding a program to record video capture alone.

---

