---
title: "dual screen in XP, how in ubuntu?"
date: 2010-02-11
forum: Multimedia Software
---

### Post by gofudgeyourselfx on 2010-02-11
i switched my netbook over to ubuntu and love it, ive been trying to switch over my desktop and managed to work out the file sharing...but cant figure out how to do dual screens with ubuntu. 

my video card is a geforce 7600 gs, i loaded wubi to give ubuntu a shot and couldnt manage to get it like i have it in XP...i use my main monitor and i can move things to the right to my TV hooked up with an RCA cable, maximize it and play it like its a 2nd screen...when i tried to hook it up using ubuntu it made it like one giant screen...how do i get 2 entirely separate screens?

---

### Post by Nunu on 2010-02-11
Does both screens switch on?
Are they mirrored? 
Do you have a shortcut on the keyboard to switch screen modes? on dell its usually Fnc key + one of the F keys. 
does both screens show up on the display settings window?

---

### Post by gofudgeyourselfx on 2010-02-15
both screens are working...i can run both in landscape mode where the tv and monitor are 1 desktop...but i want 2 separate displays, 1 for videos and 1 for surfing the net.

---

### Post by skierkyles on 2010-02-16
if you have installed the graphics driver, open up a terminal (you will find this in: Applications - Accessories - Terminal), and type in
```

sudo nvidia-settings

```
then click "X Server Display Configuration" 

then click the monitor you want to enable, and click configure,

then check the box for "TwinView" and press "Ok"

then press Apply, if it is working properly, click "Save to X Configuration File" and it will automaticly be enabled from that point on!

---

