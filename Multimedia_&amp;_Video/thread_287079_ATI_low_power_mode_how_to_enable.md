---
title: "ATI low power mode? how to enable?"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by nbound on 2006-10-28
Anyone know how to enable lowpower mode for mobile ATI cards... the howto in the community wiki is quite old... any ideas? it would siginificantly lengthen battery life (only running at 100MHz instead of like 300ish)

---

### Post by nbound on 2006-10-28
Managed to get it into low-power mode while running... easy enough... now how to make it do that only when running on battery? :confused:

---

### Post by PinkyMouse on 2006-10-30
Could you explain, how you did that?

Thanks!

---

### Post by abahgat on 2006-10-30
Yes, that would be really useful!

---

### Post by nbound on 2006-10-30
Ok first run
```
aticonfig -lsp
```

and see what powermodes there are, the top is number one and any others increase in number downwards... on mine the top is low power mode. so to enable it i type:

```
aticonfig --set-powermode=1
```

which would set it to low power mode, and to check running "aticonfig -lsp" again will tell you what mode its in. To change back its as simple as:

```
aticonfig --set-powermode=2
```


I dont think this will work on any cards other than laptop cards but its worth a go :) 


I just want it to switch powermodes when i disconnect/reconnect my AC power ](*,)

---

### Post by nbound on 2007-02-27
Its been a few months... anyone got any idea how to enable this now that the Edgy upgrade rush has been over for a while? :(

---

