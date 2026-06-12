---
title: "scanning channels not working"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by terry_gardener on 2008-03-26
i have 2 tv cards in my pc hauppauge wintv nova-t 500 and hvr 1110. 

i have plugged in an arial and when i scan using kaffeine signal hovers about 50-60% and the snr stays 0% 

it is finding no channels at all. 

i have checked the local transmitter and change the setting to the transmitter and still nothing. 

any ideas 

thanks

---

### Post by xc3RnbFO8P on 2008-03-26
If you haven't read this:
[http://hftom.free.fr/phpBB2/viewtopic.php?t=178]("http://hftom.free.fr/phpBB2/viewtopic.php?t=178")
Running Kaffeine in Terminal gives you useful  information.

---

### Post by terry_gardener on 2008-03-26
yes i have read and tried this and still the same.

---

### Post by xc3RnbFO8P on 2008-03-27
If you can, get the information about the stations in your neighborhood, (Google it, station freqence bandwidth etc ) something like this: 
> DR1:602000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:111:135:101
Then add it in the Channel> New. (Kaffeine)

You could also try [Me-TV]("http://me-tv.sourceforge.net/download.html") 
You have to add manually channel.conf file in /home/your folder/**.me-tv/**  (in Gedit) and add channel information as well.

---

