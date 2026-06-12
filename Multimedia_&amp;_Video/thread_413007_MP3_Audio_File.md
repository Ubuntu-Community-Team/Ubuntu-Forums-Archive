---
title: "MP3 Audio File"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by rosswmcgee on 2007-04-18
My wiife wants me to make a CD from an MP3 audio file. I am an old Linspire hand and have used K3b successfully in the past . I got it to burn the file but there is no audio when I play the CD. Trying other methods now K3b says: Unable to handle the file do to unsuported format. The file is on my desktop with two big musical notes. If I touch the file with my mouse it starts playing. If I want to open the file it plays with Totem movie player, but there is no video. There is not supposed to be.

I tried Serpentine it says Converting files failed. 

I looked at the threads on that but the fix does not work. Is this the wrong kind of file, what can I do?:)

The file came from Audio Acrobat.com

---

### Post by RomeReactor on 2007-04-18
Hi. Open Synaptic, search and find K3B, and make sure you install all the packages **Recommended for Installation** and **Suggested for Installation**, especially **libk3b2-mp3**. You need at least that library to decode mp3 files with K3B. Also, when you right-click the mp3 file and view its properties, does it confirm it's a mp3 (MPEG layer 3 audio)?

---

### Post by rosswmcgee on 2007-04-18
Yes it is an audio /mpeg type mp3 audio. when I installed  K3b in symatic it did inclued two other files but I will check this out as well. Thanks

---

### Post by rosswmcgee on 2007-04-18
> **rosswmcgee said:**
> Yes it is an audio /mpeg type mp3 audio. when I installed  K3b in symatic it did inclued two other files but I will check this out as well. Thanks
That did it CD has been made and wife is happy and can do her Yoga peacefully. I wonder why that libk3b2-mp3. was not included in K3b? Perhaps that is why Serpentine did not work as well. These forums are great!

I am thinking about Feisty but am only a month into Edgy 6.10. I have two 6.10 computers so maybe I will do a clean install and no Automatix Feisty. Do you like the idea? and thankyou. Ross

---

### Post by RomeReactor on 2007-04-18
Check [this post]("http://ubuntuforums.org/showpost.php?p=1790759&postcount=9") to see if this is the problem that you are having with Serpentine; It might also be a good idea to search the forums for **serpentine mp3 convert** or something similar to see if someone has already had this issue and solved it. I also recommend that when installing programs, also check for **Recommended** and **Suggested** packages and install those as well; makes for less trouble down the road. Have fun!

---

### Post by rosswmcgee on 2007-04-18
Yes this is the one but no can do fix because after the first sudo I find no line 495 that the writer speaks of and the lines are not numbered.

---

### Post by FuturePilot on 2007-04-18
Do you have the restricted formats installed? You might want to look here
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by rosswmcgee on 2007-04-18
My understanding here is limited. If you are saying is everthing Kosher, probably not, because I did use Automatix.

---

