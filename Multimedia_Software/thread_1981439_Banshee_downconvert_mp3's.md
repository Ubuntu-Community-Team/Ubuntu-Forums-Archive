---
title: "Banshee downconvert mp3's?"
date: 2012-05-16
forum: Multimedia Software
---

### Post by Theredbaron1834 on 2012-05-16
I was recently given a Nokia C6-00 phone. I don't really use it as a phone, but I thought it would be a nice mp3 player with bluetooth. There is one problem, I only have a 2gb card for it, and about 4gb of flac/356kbps mp3 mix. I want to convert both the flac and the mp3's to 128kbps mp3's. So I set it up in the settings of banshee, and try and transfer. It does the flac's, but just copies of the mp3's. Is there anyway to get it to work?

And if not, is there any way to get banshee to work with "WMA, AAC, AAC+, eAAC, eAAC+" so I can just set that as a transfer format? I added aac/wma stuff to the is_audio_player, but it didn't show up in banshee.

---

### Post by shantiq on 2012-05-17
well from commandline   [taking it your [**Nokia player plays aac**]("http://www.developer.nokia.com/Devices/Device_specifications/C6-00/")]


change directory  > cd  to where  all your files you want converted are placed and run script below **as one block**  [it will go in each folder and turn all files to 128k aac but since it chooses a variable option the files will vary from say 125 to 130 which i am sure will not be a problem for what you want here]  All files will be dumped in a folder on desktop  so you can do your 4Gb with no manual manipulation ::]]


> for i in */
do
cd "$i"
for f in *.mp3 *.flac ; do ffmpeg -i "$f" -ab 128k "${f%.*}.aac"; done \
&& mkdir ~/Desktop/aac_for_Nokia && mv *.aac ~/Desktop/aac_for_Nokia
cd ..
done **================================**

---

### Post by Theredbaron1834 on 2012-05-17
Thanks for that, wish I saw this earlier. Spent an hour each trying banshee, rhythmbox, and amarok with no luck. So I just gave up and installed winxp in virtual box, an old mediamonkey, and did it from there. :) I am not good at sh scripts, so that was easier for me. 

Will diffanatly save that though, as it will come in handy, quite often. Even more so cause I do know how to edit scripts, just can't make from scratch. That little thing could also help me get all my video's converted too. Thanks much.

---

