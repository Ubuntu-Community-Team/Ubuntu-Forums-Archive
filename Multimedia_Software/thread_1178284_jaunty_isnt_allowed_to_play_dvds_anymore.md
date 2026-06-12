---
title: "jaunty isnt allowed to play dvds anymore???"
date: 2009-06-04
forum: Multimedia Software
---

### Post by binskipy2u on 2009-06-04
I have medibuntu repos, libdvd, libdvd nav, blah blah blah

i have all restricted stuff installed.. blah blah blah

i have smplayer, xine, vlc, movie player, mmovie player
etc

and NOTHING works.. plays just the opening and closes..

they've ALWAYS worked before in 8.10
someone help.. dont wanna go back to windows just to enjoy dvds on a 24" lcd

---

### Post by pastalavista on 2009-06-04
Check in synaptic package manager to see if you have libdvdread4 and libdvdnav4 installed. If not, install them.

---

### Post by binskipy2u on 2009-06-04
have'em both.. all i see is the the choices "to play dvd, watch selected scenes, extras" and i hit play movie, and it dissapears
on ALL programs.. or it freezes and i have to force quit..
this is a new install..
it all worked before

---

### Post by Harrkev on 2009-06-04
Here is the one step that you need to do after installing packages:

sudo /usr/share/doc/libdvdread4/install-css.sh

I do not know why you have to do this manually.  Pain in the rear, but it has always been like this.

---

### Post by binskipy2u on 2009-06-04
same shiet... vlc, it plays the opening, lets you pick "play movie" then it dissapears..
xine, plays the opening lets you pick "play movie" then it says its encrypted

what the hell????????????????????


i mean if i cant play dvds.. whats the use?

---

### Post by pastalavista on 2009-06-04
Calm down. Updates do that sometimes. Try in terminal ```
sudo apt-get update && sudo apt-get dist-upgrade
```and if that doesn't help ```
sudo aptitude safe-upgrade
```

---

### Post by pastalavista on 2009-06-04
> **Harrkev said:**
> Here is the one step that you need to do after installing packages:

sudo /usr/share/doc/libdvdread4/install-css.sh

I do not know why you have to do this manually.  Pain in the rear, but it has always been like this.
I've never had to do that...

---

