---
title: "Black box in fullscreen mode"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by Ian Maxwell on 2007-06-06
After reinstalling Ubuntu, I have noticed that some fullscreen apps (i.e., games) don't fill the whole screen---the resolution doesn't change to accomodate them. Instead I get a big black box around the display.

I'm running Feisty (was previously running Edgy and didn't have this problem). My video card is an ATI X300SE (I'm using fglrx) and my monitor is a digital LCD with native resolution 1280x1024 75Hz (which is what I'm running at). 640x480 and 800x600 resolution are available on the menu. The particular apps I'm looking at are Penguin Command and Abuse.

Any ideas how to change this behavior?

---

### Post by Bohlio on 2007-06-06
Same Exact Problem here. Im running on an ATI X300 (dont know if it is SE) also using fglrx.

Edit: changing to a regular "X" session allows fullscreen to function properly in ZSNES and in Frets on Fire, But i still cant get it to work in FCE Ultra... I think it is because i dont know how to specify the resolution for that program, It defaults to the NES resolution. And now i cant use compiz... :-( So i guess i get to choose between fullscreen, or a purdy desktop :-)

---

### Post by Ian Maxwell on 2007-06-06
Aha, indeed it seems that XGL is the culprit. Ah well, I can just run a separate X server when I really, really need to play a game fullscreen.

---

### Post by Bohlio on 2007-06-07
Does anyone know why XGL does this? A explanation would be great if anyone has one, It just seems a little weird to me.

---

