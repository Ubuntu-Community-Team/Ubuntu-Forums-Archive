---
title: "Keyboard shortcuts for xgl/compiz resetting?"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by pathik on 2006-05-31
Sorry if this is the wrong thread, however, I was curious if anyone could help with something.. I am running xgl/compiz, and it works great, however, everytime I boot I have to go into preferrences, keyboard, and change my keyboard layout to something other then whatever it is, and then change it back, for my xgl or ubuntu shortcut keys to work. I don't know if it's just an xgl issue, or ubuntu. However, if anyone could provide any help it would be greatly appreciated.

Thanks

---

### Post by jasay on 2006-06-01
You might add something like this to the end of your thefuture script (assuming you have one).  You'll have to modify it of course to fit your keyboard.
```

setxkbmap -model pc105 -layout us -variant basic &
```

---

### Post by jms830 on 2006-06-08
could you tell me what to add to thefuture script for _Generic 101-key PC_  or  _Dell 101-key PC_ keyboards?

---

