---
title: "[SOLVED] after a month remote died..cant fix it... help!"
date: 2007-11-06
forum: Mythbuntu
---

### Post by zeltak on 2007-11-06
Hi guys

I have been using mythbuntu for a month and loving it. Today after a restart the remote stoped working. i tried changing batteries and a remote and IR receiver (i have 2 pvr 150 cards so i have an extra remote..) but nothing works. Lirc seems to be running when i use the dmesg | grep lirc command. The lircrc file is ok too. one thing is that when i use the irw command i get no response... can anyone point me towards some kind of solution...im totally stuck

thx

Zeltak

---

### Post by OffAxis on 2007-11-06
have you checked the cable?
Is there a lirc device listed in /dev/ ?

is the lircd.conf file loading properly?
you could try issuing a 
```
irsend LIST "" ""
```


command, and it should list your remote as a device. If you used the mythbuntu Remote Control setup it should read 'irsend: hauppauge'.

---

### Post by zeltak on 2007-11-06
thx alot for the reply..im getting desprate here:)

the cable is ok i checked with 2 diffrent cables.
there is a lirc device listed in /dev/ 

When i do the irsend LIST "" "" i see the remote (actually 4 types of hauppauge remotes but thats normal i guess) and it says 'irsend: hauppauge'.

as far as i can tell the lircd.conf is working properly.

anything else i should try?

thx again in advance

Zeltak

---

### Post by axelsvag on 2007-11-06
Have looked at this 
[http://ubuntuforums.org/showthread.php?t=590909](http://ubuntuforums.org/showthread.php?t=590909) 
the solution fixed my my problem when remote worked sometimes and not sometimes after reboot.

---

### Post by zeltak on 2007-11-06
wow axelsvag!!!! it worked!!


thx so much you made my day! ive been working on it for 4 hours!!! i was at the point of going mad!

i changed the hardware.conf to /dev/lirc1 and it started to work, i cant believe how it just stoped working like this but now its working!

thx alot man

Zeltak

---

### Post by axelsvag on 2007-11-07
Thank you, but you should actually thank psyduck!

---

