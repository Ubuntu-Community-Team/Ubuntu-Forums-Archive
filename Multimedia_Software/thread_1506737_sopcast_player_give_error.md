---
title: "sopcast player give error"
date: 2010-06-10
forum: Multimedia Software
---

### Post by suli8 on 2010-06-10
hi 
i have the sopcast player that stopped working, and i need your help
it worked good before so... i dont know wts the problem here
when i run it nothing happens..
so i run it from the terminal and thats what i get


suliman@suliman-laptop:~$ sopcast-player
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 1783, in <module>
    pySop = pySopCast()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 371, in __init__
    self.vlc = VLCWidget.VLCWidget(*p)
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 28, in __init__
    self.player=instance.mediacontrol_new_from_instance()
AttributeError: 'Instance' object has no attribute 'mediacontrol_new_from_instance'
suliman@suliman-laptop:~$ 


how can i fix it? somthing related to vlc?

tried reinstalling vlc and sopcast... no luck
thanks in advance

---

### Post by howefield on 2010-06-10
Did you install using the sopcast ppa ?

---

### Post by suli8 on 2010-06-10
yes... the jason_scheunemann ppa
it worked perfectly till 2 days ago... and then suddenly stopped!
i did mess up somthing with vlc...2 days ago....but i cant remember what..


edit: tried to reset all vlc configuration....no luck either..

---

### Post by howefield on 2010-06-10
> **suli8 said:**
> i did mess up somthing with vlc...2 days ago....but i cant remember what..

It wasn't the pre release of VLC 1.1 you tried was it ?

---

### Post by suli8 on 2010-06-10
no.. it was somthing with the sound mixer....equalizer..
i don't really understand the 3 errors in the terminal...the lines in the script....
its a shame that tomorrow the world cup is starting and my sopcast is gone  :(

---

### Post by suli8 on 2010-06-10
oh..and now i remember reinstalling the "linux-sound-base" package... for oss and alsa...

---

### Post by howefield on 2010-06-10
Try following/posting in this thread...

[http://ubuntuforums.org/showthread.php?t=1032901&page=42](http://ubuntuforums.org/showthread.php?t=1032901&page=42)

---

### Post by suli8 on 2010-06-10
thanks a lot!
i posted there now
hope it will be solved soon!
best regards

---

### Post by suli8 on 2010-06-10
i saw that the problem in fact is with vlc...
in that thread they speak about it in page 39! and it seems i have the 1.1.0rc vlc!!!
i dont know how...maybe with the system update....
any way i asked them if i can downgrade vlc and solve the issue...we will see...
but its a big relief... problem found...thx

---

### Post by suli8 on 2010-06-11
ok, i disabled the 3rd party ppa for vlc
reinstalled the 1.0.6 version
reinstalled sopcast

and problem solved!!
:p:p:p

thx a lot

---

### Post by joanmunoz on 2010-08-15
Thanks for the post,dude! I had the same problem,now solved.

Joan

---

### Post by ilabor on 2010-09-15
[http://ubuntuforums.org/showpost.php?p=9847168&postcount=422](http://ubuntuforums.org/showpost.php?p=9847168&postcount=422)

---

