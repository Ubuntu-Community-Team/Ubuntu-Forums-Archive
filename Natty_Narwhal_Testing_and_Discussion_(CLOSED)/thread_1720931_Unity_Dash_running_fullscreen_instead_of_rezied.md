---
title: "Unity Dash running fullscreen instead of rezied?"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mykrob on 2011-04-03
Running Natty Beta with today's updates applied. Screenshots and videos I have seen show the dash launching just big enough to contain the apps that should be showing, and resizing itself as necessary. mine launches fullscreen. My resolution is 1366768, the rest of the desktop looks normal.

How can I get the Dash to resize? This fullscreen dash is a bit silly.

Thanks,
-myk

---

### Post by Linducker on 2011-04-03
I was having the same problem. Just enter this into a terminal:

gsettings set com.canonical.Unity form-factor Desktop

Cheers oldsport!

---

### Post by mykrob on 2011-04-03
Thank yo, that worked. Why was this not already set? Can you explain what the command did?

---

### Post by mykrob on 2011-04-03
One more thing, can I make the icons smaller in the dash smaller?

---

### Post by Linducker on 2011-04-03
Unfortunately I do not think you can change the icon size yet. sorry mate! You enjoying unity so far?

---

### Post by Linducker on 2011-04-03
I have the same resolution. The default minimum to have a re sizable dash is 800 px height. The command you ran tells Unity to force "Desktop" mode. To revert simply run the same command but replace "Desktop" for "Netbook".

---

### Post by mykrob on 2011-04-03
thanks, that's excellent information. Perhaps they should consider reducing the requirement, as many laptops run at 1366*768 by default.

So far, so good. I had to do a little fixing for my wireless adapter (ath9k), there was the dash issue (which you fixed) and that's about it. I haven't really formed much of an opinion yet, can't seem to come up with much to do to put it through its paces.

For the most part, I just browse the web with this laptop, and it works fine for that.

---

### Post by taojian on 2011-04-03
Install compizconfig-settings-manager and you can change the icon size, and a lot of other stuff to boot.

---

### Post by Linducker on 2011-04-03
A bug has been submitted in launchpad so I hope the devs will fix this before release. Anyways I'm glad I could help as it was really irritating running it full screen. There still is a bug though;the second row of shortcuts is cut off so hopefully they fix this before release as well.

---

### Post by Scooter85 on 2011-04-03
Check out this link:        [http://www.omgubuntu.co.uk/2011/03/a-gnome-menu-style-unity-dash/](http://www.omgubuntu.co.uk/2011/03/a-gnome-menu-style-unity-dash/)

:confused:

---

