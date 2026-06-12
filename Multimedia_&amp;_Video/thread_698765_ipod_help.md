---
title: "ipod help"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by pointless56 on 2008-02-16
[SIZE="3"] 
I Recently installed ubuntu and gtkpod on my laptop and I plugged in my 80gig i pod video into my computer and i can view and play my music through rythembox and gtkpod but when i eject my ipod it displays no music. I realized now that when i unplugged it the first time I didn't click eject i just pulled it out of the laptop. Ive tried copying my music to my laptop and back but theres an error msg. i've tried replugging it and ejecting it properly but no luck. I was wondering whats my next step to get my ipod/music working again. If anyone has any info on this it would e greatly appreciated
Thanks,
Pointless56

[/SIZE]

---

### Post by TheThingfish42 on 2008-02-16
I am also experiencing this same issue with a new 80g ipod video. When I plug it into my Laptop (running Gutsy) Rhythmbox appears, and can see all the music video etc loaded into my ipod. I do always properly disconnect the ipod, waiting for its screen to return to standard use and for the message stating that it is safe for me to disconnect, but regardless my ipod displays no music no video etc, in the settings it shows that there is space consumed, but no playable media. I have plugged it back into my computer, and Rhythmbox can still see and play all the data on the ipod. I have been poking around the internet for more information, but this is the first report I have seen of someone experiencing the same issue I am having. Anyone with a solution, I would greatly appreciate some help! Thank you all for your time :)

---

### Post by benerivo on 2008-02-16
I have no experience myself, but i have once had to share files with an apple mac across a network. My problem was the file permissions. I was unable to access them on the mac because they were classed as user id  1000 (my ubuntu id) and i could not access them using my apple mac login (some other user id number). Maybe the same happens with an iPod?

---

### Post by mrsteveman1 on 2008-02-16
If you guys mean that the ipod itself can no longer play media you know is still there, thats likely a library issue, the iPod library on the device might be corrupted.

You can probably fix it by connecting it to itunes or restoring the ipod software.

---

### Post by TheThingfish42 on 2008-02-16
I have had to restore my ipod several times due to this issue, but regardless its something that only crops up when I plug into Ubuntu, if I boot to Vista (yuk) it never occurs :/

---

### Post by mrsteveman1 on 2008-02-16
This is very likely because of the checksum on the itunes library (in the ipod), but i thought the gtkpod people had implemented it already.

I haven't ever used anything but iTunes with my 3G nano but im tempted to screw with it now :D

---

