---
title: "Trouble scanning for cable channels."
date: 2012-08-05
forum: Mythbuntu
---

### Post by soggypretzels on 2012-08-05
I've just installed Mythbuntu 12.04 on a desktop but I am having trouble scanning for cable channels. In mythTV backend setup I add a capture card under the MPEG-2 tab and it seems to reccognise the Hauppauge 850 I have installed. I set the video source to the EIT grabber. However, when I go to scan for channels it quickly returns that it failed to find any channels.

Most of the guides I have seen online are working with analogue TV as opposed to digital cable. I tried manually scanning for channels as outlined [here]("http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_%28For_ATSC/QAM_Tuner_Cards_--_USA/Canada%29") but that didn't work either (each channel times out). I have the COAX running direct to the tunner card (without going through the cable box). I do know my cable is working because if I run it through the cable box to the TV I get normal video.

I've already torn out most of my hair. Any suggestions?

PS. I'm a noob.

---

### Post by anonymousdog on 2012-08-05
Which of the three versions listed [here]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850") do you have?

---

### Post by nickrout on 2012-08-05
> **soggypretzels said:**
> I've just installed Mythbuntu 12.04 on a desktop but I am having trouble scanning for cable channels. In mythTV backend setup I add a capture card under the MPEG-2 tab and it seems to reccognise the Hauppauge 850 I have installed. I set the video source to the EIT grabber. However, when I go to scan for channels it quickly returns that it failed to find any channels.

Most of the guides I have seen online are working with analogue TV as opposed to digital cable. I tried manually scanning for channels as outlined [here]("http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_%28For_ATSC/QAM_Tuner_Cards_--_USA/Canada%29") but that didn't work either (each channel times out). I have the COAX running direct to the tunner card (without going through the cable box). I do know my cable is working because if I run it through the cable box to the TV I get normal video.

I've already torn out most of my hair. Any suggestions?

PS. I'm a noob.

If you want digital then it is not an mpeg2 vard. It will be a DVB card for digital.

---

### Post by soggypretzels on 2012-08-05
> **anonymousdog said:**
> Which of the three versions listed [here]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850") do you have?

I have the  WinTV-HVR-950Q

nickrout: I also changed it to DVB; still nothing.

---

### Post by dangerous_d on 2012-08-08
Did the driver and firmware load correctly?  What is the output of `dmesg'?

Have you checked the frontend and backend logs for useful information?  I recall there is a boolean setting "Use EPG".  Did you enable it?

---

### Post by soggypretzels on 2012-08-13
sorry for the slow reply. I didn't know I needed to load drivers manually if Mythbuntu seemed to probe the device getting it's name. How would I go about loading drivers?

I also tried installing windows and using Hauppauge's drivers but when it scanned it only came back with the 1 local cable channel.

Someone mentioned something to me about needing an M-card. The M-card is a PCMCIA card and I'm running Mythbuntu on a desktop. I'm quite lost.

Thanks again.

---

### Post by soggypretzels on 2012-08-19
As expected I missed something obvious. Forgive me for wasting your time's

The solution: The tuner card I had (Hauppauge 850) doesn't support encrypted cable. I now have a different card, which has turned up a whole new set of issues.

Thanks again for your help.

---

### Post by mtbdrew on 2012-09-07
The Hauppauge WinTV HVR-850 and 950 models are over the air ATSC digital only. The only cable support is for analog.

---

