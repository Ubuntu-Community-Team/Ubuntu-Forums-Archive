---
title: "Saa7134 TV Card - No Sound... Help a noob, please? :)"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by JetaKing on 2006-06-12
I'm sort of a newb to Linux - I tried it a while ago and I hated it, but I am trying it again and I'm liking it a lot more now. However, I'm trying to get this TV card of mine to work, and the video works fine, but the sound just does not come through. It's got a Philips SAA7134 chip in it I think. Please, help this newb in need. [-o<

---

### Post by hackataca on 2006-06-16
I've the same problem.
My tv card is KWorld 220dvb-t, chip=saa7134
It works with:
modprobe saa7134 tuner=81

but it's not sound

Any sugestion? :?:

---

### Post by JetaKing on 2006-06-16
Hmm... If it helps, I have a pixelview playtv mobile... Maybe someone else out there has this card? Or has an idea on what to do?

---

### Post by Stinger on 2006-06-16
I have a Medion TV card with a Philips SAA7134 chip too , the card comes with a small stereo jack to jack cable.
The way I got sound working was connecting sound out from the TV card to the line input of my soundcard , unmute the line-in in the record tab of the mixer and turn up the volume.
Or did you already try this ?

---

### Post by JetaKing on 2006-06-16
My card doesn't have a sound out jack. It sends the sound directly into the computer. :-/

It works right under windows, but thats obviously because I have the really real driver for it. I mostly use Ubuntu, now, though, so I really want to get this to work... >.<

---

### Post by jtltgl on 2008-07-18
Just wanted to say I had no sound on tvcard . First I had to set capture to line in alsa mixer it was set to mic. Then I found this list [http://www.zonap2p.com/showpost.php?p=52674&postcount=4that](http://www.zonap2p.com/showpost.php?p=52674&postcount=4that) help me pick the right card and tuner. Then edit /etc/modprobe.d/bttv and set card and tuner to your tvcard. If you have wrong card and tuner you might not get sound like I had. One more thing if you have radio on tvcard add radio=1.

---

### Post by darknight2183 on 2008-07-18
1.) sudo apt-get install linux-source
2.) follow the following guide: [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)
    NOTE: For this part: 
# cd /[kernel source directory]/Documentation/dvb/

         Your source code is located in the following directory: /usr/src/2.6.24/ (if you are using the latest distro, Hardy)
3.) check to make sure the modules are listed: sudo nano /etc/modules
    you should see:  saa7134
                     saa7134-dvb
                     saa7134-alsa
    if you don't, just type it in, press Ctrl+X and press 'Y' to save
4.) restart alsa: should be /etc/init.d/alsa restart (I think)
     you can check to see what it's called by typing "ls /etc/init.d" and looking for "alsa" or "alsa-something"

---

