---
title: "TVTIME: volume stuck at zero?"
date: 2008-07-30
forum: Multimedia Software
---

### Post by Pasdesignal on 2008-07-30
I have been trying very hard to find a solution on the forums here and elsewhere. No luck. Please help if you think you can!

Problem:

TvTime onscreen volume display is stuck at 0. 

I have my audio line out form the BT878 based capture card plugged into a mixer, and if I amplify it alot I can hear the tv sound. So it is there somewhere. If only I could turn up the volume control in the program itself.

Something is causing the program to start with volume at 0, or the controllers aren't working when I try to change it for some reason.

This is killing me. 
Has anyone ever solved such an issue?

If not, maybe someone could recommend another TV viewer that uses v4linux / bttv  ?

Thanks

---

### Post by Pasdesignal on 2008-07-30
Sorry to bump, but: anybody?:(

---

### Post by Israel Katz on 2008-07-31
> **Pasdesignal said:**
> Sorry to bump, but: anybody?:(
I have an "Leadtek" tv card attached. And Suceded to watch tv from digital income. After attaching camera to upload the photos, I loosed the connection with the TV-OUTPUT.

---

### Post by fishbulb1022 on 2008-12-27
I'm not sure if this will work, but its easy to try so its worth a shot. Open a terminal window and type "tvtime" (without quotes). Just close tvtime when it opens, you're only interested in what it says in the terminal. it should say "reading configuration from" followed by a path ending with the tvtime.xml file. If there are two paths, I think you want the first one. It starts with /etc/ on my computer. Open the file browser and use the path from the terminal to find the tvtime.xml file. Open it with Mozilla. Look for any audio settings. I believe there is one that deals with Max Volume. If you can find this one, and the value is set to 0, you've found the problem. You'll need an xml editor to fix this. I would recomoend screem. Once you've got screem, open a terminal and type "sudo screem" (agaian, without quotes). Open the file, and find that line again. Highlight the 0 and change it to whatever you want the max to be. go to file>save and try it out. 

hope this helps

---

### Post by jmlm-1970 on 2012-11-15
This makes the voulme slide goes up and down, but sound can still be missing.

Try:

cat /proc/asound/cards

Then the result will be something like:

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at xxxxxxxxxxxx
 1 [EasyALSA1      ]: easycapdc60 - easycap_alsa
                      easycap_alsa

Then just type (if your video is the 0 change video1 to video0):

tvtime-configure --device=/dev/video1 --mixer=/proc/asound/EasyALSA1:monitor

Then type:

tvtime -v

and when the key + and - is pressed the slide will go up and down, if still no sound is because the mixer=device:channel is for OSS, the ALSA way is device/channel but I do not know yet what is the equivalent, because the path needs / and also the separator between device and channel.

---

### Post by wildmanne39 on 2012-11-15
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

