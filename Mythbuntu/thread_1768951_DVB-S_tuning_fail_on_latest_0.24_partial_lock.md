---
title: "DVB-S tuning fail on latest 0.24: partial lock"
date: 2011-05-27
forum: Mythbuntu
---

### Post by dibuntux on 2011-05-27
I'm getting mad with this. This is the only real problem I have with Myth: partial lock. I had it ever since with DVB-T, now I'm getting it with channels on DVB-S that I had a lock yesterday and ever since.

This the story: the channel worked fine; they just had no guide, since the source was configured to use EIT.
Since I have the same channels on DVB-T, configured to get the guide from XMLTV, I believed I could modify the source to get the guide on the DVB-S channels.
So I modified the source to get guide data from XMLTV. It did not work and could not get a lock on the channels anymore. Channels on the SAME transponder not configured for XMLTV but using EIT lock OK. 
So I went back and put the source as it was to get EIT data only. I deleted all channels and rescan: I cannot get a lock on those channels anymore, but I can on other channels from the same multiplex. And this with 2 different multiplex.

Any ideas? TIA

Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen X 2
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI
dibuntux is online now Report Post Edit/Delete Message

---

### Post by nickrout on 2011-05-28
Check your H/V polarisation and also your LNB settings. Sometimes when you change things around myth seems to set these wrong.

---

### Post by dibuntux on 2011-05-30
For sure myth setted something wrong, but not LNB or polarization. In fact I can have a lock on channels transmitted on the transponder in question, but not on others of the same multiplex. 

If I erase all the channels for the incriminated transponders and scan again, the results I get is: channel recognized ok and then I cannot get a lock in watchtv 

Any other ideas on what to do? TIA

---

### Post by dibuntux on 2011-06-01
OK, it is definitely myth: if I use VLC to tune in, I can watch all channels correctly!

The strange thing with VLC is that you do not have to specify polarization (V or H): just input freq and symbol rate and it does the rest automatically.

---

### Post by redger on 2011-06-03
Try setting the Quick Tuning" option in backend setup/input connections  as described here [http://www.gossamer-threads.com/lists/mythtv/users/476465](http://www.gossamer-threads.com/lists/mythtv/users/476465)

Worked for me - I had 6 different DVB tuners all with the same symptom. All fixed with Quick Tuning set to "Always"

---

### Post by dibuntux on 2011-06-06
redger, you're da man! Thanks a lot! I've been looking for this forever (and it was under my nose...). 

Now I set all my tuners to "quick tuning" option on ALWAYS (in backend setup/input connections) and it get a lock on all channels.
BTW, "quick tuning" is really quick: half the time to lock on & display the channel! 

I think this one should be in the troubleshooting section.

Thanks again!
Dave

---

### Post by shad0w_walker on 2011-06-06
I'll second this going into the troubleshooting section. Somewhere high up, in bold. Got my new DVB-S card on thursday, took til about 4pm saturday trying to deal with this one niggling issue. Much appreciated suggestion.

---

