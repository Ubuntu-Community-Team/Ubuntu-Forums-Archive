---
title: "Lirc dead after resume from sleep"
date: 2009-09-05
forum: Mythbuntu
---

### Post by 13ojo on 2009-09-05
Howdy.

I've search for this, and found all strange differeing solutions. So i thought i'd ask people who are using mythbuntu how they do it.

(my install is based of ubuntu 9.04 install, then choosing mythbuntu from synaptic, on both the frontend only, and frontend+backend machine).

Basically, i managed to wrangle lirc into sending the machine to sleep when i hit the power button on the remote (very nice!).

It even comes out of suspend when i hit the power again (:D). However the remote decides that's enough and gives up after that. Even if i run irw from a ssh login, it isn't reporting any keypresses.

I think it came back by unloading the mce_usb2 module and reloading it and then lirc. Then manually restarting mythfrontend.

I gather that lirc seems to need to be restarted from this (where should i do this and how?), but is there a way i can make mythfrontend not be?. The machine kinda comes out of sleep in about 4 seconds, and mythfrontend takes more like 10 to appear (or even show any signs of life). I 14 seconds is abit long, if 10 seconds are on a desktop. Isn't there a way to fix this?

---

### Post by SiHa on 2009-09-05
Not sure how Jaunty does it, but if you're using pm-suspend, then you might be able to use the solution I figured out after a week or so of hair pulling.

Have a look here: [http://ubuntuforums.org/showthread.php?t=909195](http://ubuntuforums.org/showthread.php?t=909195)

If you try this for the mce_usb2 module, you might have some success. 

From my experience, if you make any change to LIRC, mythfrontend needs to be restarted, so I think you may be stuck with the wait. I'll be happy to be proved wrong though.

---

### Post by 13ojo on 2009-09-06
Howdy.

That seems to be workign alright. Though now irexec no longer seems to run.

I was using the power button to run the pm-suspend command, so now without irexec i get to do it once lol.

While i was thinking about putting the sleep thing more into myth (so it unallocates tuners etc), it still might be a problem if i ever have any other irexec stuff up. (EDIT: basically how does mythbuntu start irexec? i think i need to call that command, as i have to stop lirc when suspending, and resume it afterwards, and then irexec is no longer running!)

I needed to put a 3 second sleep in as well, as mythtv kept on trying to start up before the network came up.

---

