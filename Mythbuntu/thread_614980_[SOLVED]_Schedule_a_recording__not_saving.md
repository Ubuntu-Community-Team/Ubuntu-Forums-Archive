---
title: "[SOLVED] Schedule a recording  not saving"
date: 2007-11-16
forum: Mythbuntu
---

### Post by Haim on 2007-11-16
I figure I'm just being thick but....

I'm just trying to schedule a recording, so I select a show from program finder or program listings. Then select record just this one showing, and maybe alter the odd thing.

Then choose save settings.

So screen returns to program finder or listings and there is a 'not recording' *not sure if this refers to currently recording or schedule of the selected programme.  Then look in upcoming recordings, and there a none.

Note: it has worked once before, but i'm not sure how.
Also I am not connected to the usb tv tuner whilst scheduling.....hmmmm....maybe i should go test with it connected.......

Anyway, any suggestions?

---

### Post by Haim on 2007-11-16
Checked with laptop plugged in to tv tuner. No change,still not saving the recording schedule.

hmmm could it be a problem with the database....i think i saw some fix up code somewhere, perhaps i should run that....

---

### Post by newlinux on 2007-11-16
In system status does it show your tuner as connected? If the backend doesn't show any tuners connected it won't show any shows scheduled. After connecting the tuner up you will want to restart the backend. 

```

sudo /etc/init.d/mythtv-backend restart

```

---

### Post by Haim on 2007-11-25
Thanks NewLinux,  spot on, hadn't had tuner plugged in when started.

So booted with it connected and all ok.

---

