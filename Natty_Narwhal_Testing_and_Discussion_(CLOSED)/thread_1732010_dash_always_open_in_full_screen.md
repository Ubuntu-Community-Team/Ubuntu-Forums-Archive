---
title: "dash always open in full screen"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-04-17
I tried Natty on my 14" laptop and a 12" netbook. The dash always opens in full screen on the 14" laptop (my main machine) but on the 12" netbook it only takes up about 1/2 of it. I can live with the dash taking up 1/2 the screen but full screen is very annoying and I thought the dash only takes up full screen on netbooks, now it seems to be the opposite.

Is there a way to fix this so that the dash doesn't use up the whole screen on my 14" laptop?

Thanks.

---

### Post by garvinrick4 on 2011-04-17
Sorry was in wrong thread. GEZZZ

---

### Post by Sashin on 2011-04-17
Its the same on my 14 inch, you can change it in dconf-editor.

---

### Post by beew on 2011-04-17
> **Sashin said:**
> Its the same on my 14 inch, you can change it in dconf-editor.

How do you do that?  Thanks.

---

### Post by mc4man on 2011-04-17
See screen for dconf-editor - change to Desktop
or 
```
gsettings set  com.canonical.Unity form-factor Desktop
```

---

### Post by beew on 2011-04-17
Hi,

My configuration editor doesn't look like yours.

P.S. Thanks to your help I was able to install emerald.

---

### Post by mc4man on 2011-04-17
> My configuration editor doesn't look like yours.
That's dconf-editor, not gconf-editor (if that's the issue
The gsetting command will do the same if you run in a terminal
> I was able to install emerald. 
glad you got it going..

---

### Post by beew on 2011-04-17
> **mc4man said:**
> That's dconf-editor, not gconf-editor (if that's the issue
The gsetting command will do the same if you run in a terminal
.

Opps, I missed that. I installed dconf-tools from Synaptic and change the setting to "desktop" instead of "automatic" and it worked. The dash still takes up 2/3 of the screen but probably it is the best I can ask for right now.

Thanks.

---

