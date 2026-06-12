---
title: "Mic not working"
date: 2013-07-14
forum: Multimedia Software
---

### Post by skarme on 2013-07-14
Hello,


I've used Windows 8, Ubuntu 12.04 and Linux Mint Cinnamon 15 before I decided to settle for Linux Mint 13 KDE as my OS of choice. I liked the appearance of KDE and the fact that Linux Mint 13 which is based of Ubuntu 12.04 is a long term support(LTS) OS. 


The Problem:
All was well till I installed Skype and the party at the other end could not hear me. I first thought it was a Skype issue but then by trying other programs I realized that my microphone or audio input was not functioning. I do want to mention that I've never had the issue on other OS and that Linux Mint 15 Cinnamon was able to detect audio input with Skype and everything working 2 days ago. Basically I'm certain its an software issue and my built-in mic is perfect.


What I've done so far:
On going through the web, certain folks suggest replacing pulseaudio with alsa. I followed the instructions on this page [http://linuxg.net/how-to-properly-replace-pulseaudio-with-alsa-on-crunchbag-linux-and-debian-squeeze/](http://linuxg.net/how-to-properly-replace-pulseaudio-with-alsa-on-crunchbag-linux-and-debian-squeeze/). Although my soud output has been working with both before and after I installed alsa, the mic still is not.


Any help will be greatly appreciated. I don't want to go and install another OS because of such an issue....

---

### Post by speartip on 2013-07-14
I have just had the same problem with Skype on Kubuntu 13.04. 
This is how I solved the problem.
With the microphone plugged in, Right click the volume icon in the system tray, select Audio Setup (assuming nothing has changed between releases),
click on Audio Recording, & make sure the microphone you're using for Skype is at the top of the list & set as the prefered device in all the Audio Recording sub columns. Apply & try Skype again. 
This worked for me hope it does for you.

---

### Post by dannyboy79 on 2013-07-15
have you made sure your mic isn't muted in alsamixer?

---

### Post by skarme on 2013-07-17
None of the above worked. I checked with the Linux Mint Cinnamon live CD..the internal mic works fine there. Any ideas?

---

### Post by speartip on 2013-07-17
All I can suggest is using pavucontrol & alsamixer, make a note of all the seetings when using the live cd & replicate them on your harddrive.
If it works on the cd then it can't be a hardware problem, it must be a sound setting, IMO.

---

