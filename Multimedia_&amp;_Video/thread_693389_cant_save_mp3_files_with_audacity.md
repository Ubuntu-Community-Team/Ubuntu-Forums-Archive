---
title: "cant save mp3 files with audacity"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by Hmarroqu on 2008-02-11
I can play mp3s but apparently I cant save as with audacity...I notice it says i have to install some lamemp3 thing but how do i do that?:confused:

---

### Post by soro2005 on 2008-02-11
Try installing the package lame, either by locating it in synaptic, or:
```
sudo apt-get install lame
```

---

### Post by pearjam on 2008-02-11
Hmarroqu, If you open Audacity > File > Import > Audio...  Find your song to change then... File > Export - you have an option to save as .mp3, .ogg or an uncompressed format. (Works for self-recorded music also.)

---

### Post by aysiu on 2008-02-11
Try this:
[http://www.psychocats.net/ubuntu/audacity](http://www.psychocats.net/ubuntu/audacity)

---

### Post by Hmarroqu on 2008-02-11
hmm. i still cant...

I did all of the above but i do not get the mp3 option when i "export" 

Its a lengthy list of formats but mp3 is missing.

---

### Post by anindya_m on 2008-02-11
The package you want is **liblame0**. It will work after you install it using Synaptic.

---

### Post by Hmarroqu on 2008-02-11
liblame0 was already installed when i looked in synaptic...wierd

---

### Post by Sandman1278 on 2008-02-12
I am having this same problem, I tried all those suggestions, I set up the Lame Mp3 Library in audacity and there is still nothing going on when i go to export.

---

### Post by anindya_m on 2008-02-13
Ok while setting up the lame library when it browses for files use the filter "All Files *". Choose /usr/lib/libmp3lame.so.0.0.0 as the library and accept it if audacity displays a warning. This should work on Feisty (I just verified it again). On Gutsy just installing audacity and liblame0 worked for me.

---

### Post by Hmarroqu on 2008-02-13
yea still a no go, i just upgraded to gutsy to see if the latter method workd..no dice...maybe uninstalling and installing audacity again would work

---

### Post by anindya_m on 2008-02-13
I might have figured out the problem. Say you are in Gutsy and have started the gtk2 version of audacity. Double-check if you have liblame0 installed. Next open any audio file, say a .wav from /usr/share/sounds for testing. Choose File->Export. In the dialog that pops up, expand the "browse for other folders" item. In the lower right corner just above the "Options..." button there is a filter/filetype button. Click it to expand. Does it show an "MP3" option. If so select it. Now if you click "Options" it should allow you to set mp3 params and save as mp3. Does that work?

---

### Post by ACGarland on 2008-04-06
I also had this problem and was following this thread (using Ubuntu 7.1).  Your suggestion about how to find the MP3 export capability (buried down under the 'browse' button followed by selecting MP3) worked for me. Thanks so much for making this suggestion.

WOW - that's the most obscure way to hide a common capability that I've ever seen in a GUI. I'm surprised Audacity has the audacity to expect anyone to find MP3 export down that path! :(

Anyway, it's working for me now so I appreciate your tip!

---

