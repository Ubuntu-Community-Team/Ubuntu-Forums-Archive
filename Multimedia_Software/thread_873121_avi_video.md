---
title: "avi video"
date: 2008-07-28
forum: Multimedia Software
---

### Post by AmadeusOK on 2008-07-28
I'm trying to watch an avi video but there is no image just sound. Then I get a message saying that the codec is not installed (Intel Indeo 5). When I click on Search, I get this: "There is no matching application available". Where can I install it? Thank you very much.

---

### Post by bryncoles on 2008-07-29
have you enabled the medibuntu repo, and installed the restricted extras? if not, go to

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and follow the guide to enabling the repo. should be a cut and past job. then search synaptic for 'ubuntu restricted extras' and see if that helps you. if not, post back and hopefully someone who knows more than me will join in...

---

### Post by AmadeusOK on 2008-07-29
Thanks a lot bryncoles. Unfortunately, I installed the Ubuntu restricted extras but I keep receiving the same message as before.

---

### Post by wolfen69 on 2008-07-29
try vlc player.

---

### Post by ITAndrew on 2008-07-29
Is the AVI using the VP7 codec? I have had a few problems with no plugins for totem, xine, and VLC, but works flawlessly with mplayer.

In other words, if VLC does not work for you, give mplayer a go. If you find also that it is VP7, I know if you dig around you can find ways of re-encoding the files into another codec.

---

### Post by AmadeusOK on 2008-07-30
I tried to use VLC but it didn't work. When I open the file with mplayer I get the message saying that the required software isn't installed. It also gives me the option to search for a codec that supports the file. When I click on search I get the answer:

"There is no matching application available."

The audio works well but there is no image. At the very end I get one last message saying:

"An error ocurred

The playback of this movie requires a Intel Indeo 5 decoder plugin which is not installed." 

I have already enable the medibuntu repositories.

---

### Post by aeiah on 2008-07-30
from a quick search it seems that what you need is:

gstreamer0.10-pitfdll

i guess a version higher than 0.10 will work too, but the key bit is pitdfll i think.

there has been a bug posted for this problem but it came in too late for it to be resolved for hardy, from what i read.

---

### Post by AmadeusOK on 2008-07-30
Thank you guys for all your help. I did everything you told me to do but it doesn't work.

---

