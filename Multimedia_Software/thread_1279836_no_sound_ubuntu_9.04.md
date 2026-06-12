---
title: "no sound ubuntu 9.04"
date: 2009-10-01
forum: Multimedia Software
---

### Post by Wcupp on 2009-10-01
When i login to ubuntu 9.04 i have sound but after login there is no sound ubuntu recognizes my sound blaster card volume is maxed on ```
[SIZE=2]alsamixer[/SIZE]
``` what could be the problem?

---

### Post by wojox on 2009-10-01
To save your settings try:

```
sudo alsactl store
```

---

### Post by Wcupp on 2009-10-01
i have done that

---

### Post by Wcupp on 2009-10-01
ok i got it working here is what i did

check the sound card
     
     ```
aplay -l 
```Restart pulseaudio

     
     ```
pkill pulseaudio; sleep 2; pulseaudio -vv
``` 

Check mixer

     ```
alsamixer -Dhw
```

---

