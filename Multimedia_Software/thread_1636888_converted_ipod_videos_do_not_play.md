---
title: "converted ipod videos do not play"
date: 2010-12-03
forum: Multimedia Software
---

### Post by patjennings on 2010-12-03
Hi everyone, I am a new to linux and so far have really liked it. I recently ran into a problem though. using mav. meerkat I have figured out how to rip dvds using acid rip, medibuntu and some youtube tutorials. Then I tried to put them on my ipod using gtkpod. when this did not work I did some research and realized the video files needed to be converted. At first I tried avidemux, it seemed to work but when i put them on my ipod  (video white 80 gb) I tried to play them and the screen just went black and several seconds later was sent back to the menu. Then I tried winnff, but there was no ipod preset only a rockbox ipod preset which I tried with the same result. I then tried openshot using these parameters -ipod libx264 libfaac 1.25 Mbit/s -> 1.5 Mbit/s 128 kbit/s
to
160 kbit/s Quarter Square NTSC 320x240
29.97Hz
AVCHD
*Quicktime 7*Still same result. I have gotten purchased mp4 videos to work using gtkpod, so I am assuming it is a conversion problem. Also the converted mp4 I made using openshot plays fine on banshee player. Any suggestions would be greatly appreciated. Thanks

---

### Post by Chronon on 2010-12-03
The Rockbox presets are MPEG video for playback with the Rockbox firmware.  In WinFF you should use the iPod-iTunes presets instead.

---

### Post by patjennings on 2010-12-03
there is no ipod preset in winnff, not in my version anyway.

---

### Post by bluebyt on 2010-12-04
You can you use Handbrake, work perfectly for me.

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

---

### Post by Chronon on 2010-12-04
Here are instructions for installing new presets for WinFF:
[http://code.google.com/p/winff/wiki/InstallPresetsxml](http://code.google.com/p/winff/wiki/InstallPresetsxml)

---

### Post by patjennings on 2010-12-05
Im not great with the terminal yet, how do you install the file once you download it?

---

### Post by Chronon on 2010-12-05
You should be able to use the file browser to find the downloaded file and open it.  File Roller should open it and then you can extract the presets.xml to /home/YourUserName/.winff/presets.xml.  However, I'm not totally certain that this config file is compatible with your version of WinFF.

I am using 10.10 and will attach my presets.xml file if needed.

---

### Post by patjennings on 2010-12-06
Hi Thanks for the help, I extracted presets.xml to /home/YourUserName/.winff/presets.xml , and then i loaded them in winff, at least i thought i did, It pretty much reloaded the presets i already had. There is still no ipod preset. I feel like i am missing something really simple at this point, that i will probably kick myself later on for.

---

### Post by patjennings on 2010-12-06
now i have gotten ipod presets in winff but when i use it, it tells me that some of the information such as bit rate etc are wrong? I thought the presets would automatically put that info in for me?

---

### Post by patjennings on 2011-01-11
I tried handbrake successfully, It was a little confusing getting it downloaded, not hard though once I realized how. Thanks everyone for your help and suggestions.

---

### Post by patjennings on 2011-01-11
Thanks, handbrake works great!

---

