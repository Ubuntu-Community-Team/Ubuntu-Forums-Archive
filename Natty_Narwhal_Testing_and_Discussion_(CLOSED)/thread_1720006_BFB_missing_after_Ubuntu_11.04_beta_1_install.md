---
title: "BFB missing after Ubuntu 11.04 beta 1 install"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by _Doc_ on 2011-04-02
Hello all,
   I just did a fresh install of 11.04 beta 1 and all went well... up until it loaded unity.  The desktop seems to be fine... but I am missing the BFB in the upper left hand corner.  Does anyone happen to know how I can get it back?  I tried unity --reset but that didn't help.

Video card I am running is ATI 4850 and I didn't install the binaries, so should be running off the open source drivers.

thanks,

---

### Post by _Doc_ on 2011-04-02
Well looks like I managed to get it back magically.  I installed CompizConfig-settings-manager and changed hide animation to 'Fade on bfb and Slide' and Dash blur to 'Static Blur'  Then i change the monitor setting to dual screen as I have 2 monitors and it showed up.  Not sure what fixed it... I suppose I could go back and look into it... as the livecd of 11.04 beta1 also had the issue... I just figured it would of gone away magically after install somehow...

---

### Post by karthikvlk on 2011-04-04
well i installed this CompizConfig-settings-manager and did some changes and now when i login i am not able to find the panel bar in the top or the icons list in the right. how to get back that. 

I am new to ubuntu. please suggest . i am not able to find the menu also

---

### Post by cariboo on 2011-04-04
@karthikvlk You can start compizconfig-settings manager in a terminal by typing:

```
ccsm
```

you should then be able to undo the changes you made.

---

### Post by madjr on 2011-04-04
what is this "BFB" ?

is it some kind of new unity technology???!!

---

### Post by el_koraco on 2011-04-04
> **madjr said:**
> what is this "BFB" ?


big "freaking" button

---

### Post by hutchbo on 2011-04-04
> **_Doc_ said:**
> Well looks like I managed to get it back magically.  I installed CompizConfig-settings-manager and changed hide animation to 'Fade on bfb and Slide' and Dash blur to 'Static Blur'  Then i change the monitor setting to dual screen as I have 2 monitors and it showed up.  Not sure what fixed it... I suppose I could go back and look into it... as the livecd of 11.04 beta1 also had the issue... I just figured it would of gone away magically after install somehow...

I had the same issue and it looks like the dual monitor setting was the one that fixed it for me.

---

### Post by karthikvlk on 2011-04-05
> **cariboo907 said:**
> @karthikvlk You can start compizconfig-settings manager in a terminal by typing:

```
ccsm
```you should then be able to undo the changes you made.

thanks for the suggestion. i am not able to get the terminal also. i am trying ctrl+shift+f1 combo and its ask for username and password when i enter the details it gives wrong password even though i though i am supplying the correct one. 

also the panel bar on the top is also not coming please suggest

(excuse me if i sound like layman which i am)

---

### Post by ikt on 2011-04-23
> **hutchbo said:**
> I had the same issue and it looks like the dual monitor setting was the one that fixed it for me.

Yep, this is a problem because the laptop I'm using at the moment has a broken screen, thus I'm using an external monitor.

Has anyone submitted a bug?

---

