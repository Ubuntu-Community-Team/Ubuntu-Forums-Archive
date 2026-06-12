---
title: "Sound Lag"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by VRWarper on 2006-07-28
Sound works fine for me except there is a second delay which is very annoying for gaming, watching videos, etc. Does anyone know how to solve this problem?

---

### Post by spiffytech on 2006-08-07
I have the same problem, in Kubuntu 6.06, on a Dell Inspiron 6000. Does anyone know what might be causing the lag?

---

### Post by Number6 on 2006-10-11
Yup same for me with my NVidia CK804 It's driving me CRAZY!
HEEEEELLLPPP

---

### Post by Number6 on 2006-10-11
Hmm well I solved the problem by adding this to my ~/.asoundrc file :

```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
rate 48000
}
bindings {
0 0
1 1
}
}
```

then running:
 
```
sudo /etc/init.d/alsa-utils stop
sudo /etc/init.d/alsa-utils start
```

and hooray no more lag! WOOHOO! PARTY TIME! :mrgreen: :mrgreen: 8)

---

