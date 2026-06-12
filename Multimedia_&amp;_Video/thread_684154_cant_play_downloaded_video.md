---
title: "cant play downloaded video"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by 565Customz on 2008-01-31
im having trouble playing video that was downloaded using frostwire. i get the error archive type not supported. it trys to open with the archiver.  if i try to manually open it from mplayer it tells me that the data resembles a .rar file and i should rename it. i tried that and it wont work either. i guess i need a decrypter or something..anyone had this problem?

wont open with gxine either

---

### Post by jleaker01z on 2008-01-31
Go to applications>add/remove, search for gstreamer, and add in all the plugins for it.  That will install the necessary codecs.

---

### Post by 565Customz on 2008-01-31
cool im tryin it now

---

### Post by 565Customz on 2008-01-31
does it take a while or what....it went gray when i clicked apply but it doesnt seem to be doing anything

---

### Post by jleaker01z on 2008-01-31
It should start downloading stuff from the internet.  You can try to open a terminal, and enter 'sudo apt-get install ubuntu-restricted-extras' and do it manually.

---

### Post by 565Customz on 2008-01-31
ok i got it to download i had to restart....i get this message when itry to run it


The playback of this movie requires a application/x-rar
 decoder plugin which is not installed.

---

### Post by jleaker01z on 2008-01-31
What is the file extension?  Thats the last 3 letters.

---

### Post by 565Customz on 2008-01-31
this is exactly what it says under the icon....i havent seen any with that many extensions lol

I am Legend (W. Smith) DVD.Premium.SCR.[USA].avi

so its an avi...i changed it to rar but it still didnt work...and i dont know how to use unrar in the terminal to unpack it.

---

### Post by jleaker01z on 2008-01-31
You can install the UnRAR utility by clicking system>administration>synaptic package manager.  Search for 'unrar' and install it.

Understand tho that things like that downloaded off of a p2p network often arent what they say they are.

---

### Post by 565Customz on 2008-01-31
i got it from a freinds comp directly through the direct connect and it works on his....when i try it using gxine  i get a message that says 

no demuxer installed, stream not recognized.

---

### Post by jleaker01z on 2008-01-31
I dunno then...should work as long as you have the codecs installed.  I suppose it could be some type of DRM issue, but I doubt that.

---

### Post by 565Customz on 2008-01-31
well maybe someone knows...

---

### Post by jleaker01z on 2008-01-31
You could always try VLC Media Player.  It has all the codecs built in, and doesnt depend on the gstreamer ones.

---

### Post by 565Customz on 2008-01-31
im tryin acid rip right now to see if i can rip it and decode it that way...if not vlc is my next stop

---

