---
title: "Unity crashes shortly after log-in"
date: 2010-12-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jmmL on 2010-12-01
Firstly, I apologise if this has already been mentioned in the forums. I did a few searches but nothing seemingly relevant turned up.

I've just upgraded to natty. When I log in with "ubuntu desktop" unity is loaded and then crashes about 3-5 seconds afterwards, with no interaction. I'm left with no panels or window borders etc. I've worked around by selecting "ubuntu classic desktop" in gdm, which is at least functional.

I'm running x86_64 with the latest nvidia-current. I've installed ccsm. What can I do to get unity working? It looks pretty!

---

### Post by nperry on 2010-12-01
[http://ubuntuforums.org/showpost.php?p=10186308&postcount=208](http://ubuntuforums.org/showpost.php?p=10186308&postcount=208)

worked  for me

failing that, could be this [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/683686](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/683686)

---

### Post by soapytheclown on 2010-12-01
I came from virtually a fresh install, however I have noticed that if you attempt to modify nearly any settings in CCSM it crashes compiz. I expect that some of your compiz settings are screwing it up. Try backing up (move) your 

```
~/.config/compiz*
``` 

folder and log out and back in so it makes a new set of compiz settings. also as a side note if you really want to try and use unity, make a bash script with the following in:

```

#!/bin/bash
compiz --replace

```

make it executable and leave it on your desktop. Any time compiz crashes just run that to get it back on.

EDIT:
Or that post nperry linked

---

### Post by cariboo on 2010-12-01
Thanks to whiprush, have a look at [this]("http://penguindroppings.wordpress.com/2010/12/01/compiz-vs-ubuntu-classic-desktop/") blog post

---

### Post by efflandt on 2010-12-02
For the Dec 1 live iso running from USB, with Intel or older ATI video (which does do open GL), the panels and Unity come up for a few seconds, then disappear.  I would not expect that to work with nouveau with nvidia chips yet (because that failed earlier without any GL). I cannot get to a gnome-terminal with the usual shortcut keys and sudo just repeats the process (Unity appears, then panels and Unity wink out).  I will see how alpha1 goes later.

For earlier regular install using nvidia 260.19.21 w/GT 430 on USB updated to Dec 1, GNOME (Failsafe) or Classic GNOME Session work.  But for regular GNOME session with Unity it would not work until I used gconf-editor to put **gnome-panel** in desktop/gnome/session/required_components/panel and did **compiz --replace**.

However, for the quick script which I put in ~/bin with launcher on desktop, so I could have it work and be able to close the terminal, I had to use nohup [/bin/bash or /bin/sh (dash) do not make any difference in this case] and redirected output to avoid growing nohup.output:

```
#!/bin/sh
nohup compiz --replace > /dev/null
```After running that it left a terminal up with blinking cursor, but no prompt, and if I closed the terminal, Unity would temporarily wink out and then come back.  If I logged out (or shudown/reboot)  a dialog popped up saying "Unknown not responding". And I had to launch the script again after login before Unity would come up.  Once everything came up, it seemed to work fine, it just that something with compiz or Unity (as of last night) not start properly automatically.

After suspend everything comes back up and works, except all Unity icons did not refresh and were just snow (like a TV on no channel).  So you could only tell what Unity icons were from hover notifications and they still worked to launch apps.

---

