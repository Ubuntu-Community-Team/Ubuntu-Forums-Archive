---
title: "Audio problems"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by randyl8753 on 2007-06-09
New to Linux, using ubuto, installed feisty (7.04)

Sound I am getting sounds like blown speakers. I have a m-audio audiophile 192 card.

I really have been looking for a fix, cant find one so perhaps someone can help me.

From what I have found, looks like a driver issue.  What my card needs is ice 1712 envy 24

What got installed is ice 1724 envy24ht

Besides this issue, I really do like linux so far....  so, anyone, how can I resolve my issue?

thanks

---

### Post by moeFinley on 2007-06-09
You can use 'lspci' (type lspci into the terminal) to view all your hardware.  Check that you are installing the correct drivers for the card listed.  You can see which are up and running by using 'aplay -l'

Though from your description it doesn't sound like a driver issue?  Could it be something simpler.  Have a look though your cards options (double click the volume icon or type alsamixer in the terminal) and see if you can switch off suround settings or change the output type to improve things?

---

### Post by randyl8753 on 2007-06-11
thanks moe, didnt work though...you may be right anout it not being the driver.

for some reason i thaught it was drivers, but i guess its the soundcard that is detected is wrong.

i have a m-audio audiophile 192.  of the information i find it should be identified as ice 1712 envy 24

when i check what card is installed, it says ive 1724 envy 24ht

i tryed everything you suggessted, nothing at all changed.

any other ideas?

thanks again

---

### Post by Lord_Alda on 2007-06-11
Icpci:
Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by CityofAsh on 2007-06-11
Try turning down the PCM.

---

