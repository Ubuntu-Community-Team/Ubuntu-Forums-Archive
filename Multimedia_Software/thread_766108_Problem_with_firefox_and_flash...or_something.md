---
title: "Problem with firefox and flash...or something"
date: 2008-04-25
forum: Multimedia Software
---

### Post by jtrink on 2008-04-25
Currently working in Hardy Heron. Uh I can playing streaming videos online after i actually click the video. In windows a "preview" of the video would be displayed then i would just hit play. Now i have to select the video in the middle to play because it is "grayed out with a big play button in the middle". I have the same problem with my flash. Btw, I have adobe flash player 9 installed and mplayer as well. Any ideas to get rid of these dang gray play buttons?

---

### Post by mrm3x1can on 2008-04-25
yeah ubuntu newb here. just installed hardy to and i have that same problem. when any type of flash related thing comes up in a website, i get this big gray play button i have to press. how do i get rid of it?

---

### Post by martrn on 2008-04-25
Have you enabled the restriced reposotories via :-
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")   ??

Then you type at a terminal
> sudo apt-get install flashplugin-nonfree

---

### Post by jtrink on 2008-04-25
yeh, that didn't work... all my repositories are enabled. I have no clue what is wrong.

---

### Post by Islington on 2008-04-25
Guys make sure that you remove swfdec-mozilla in synaptic or by doing 

```
sudo apt-get purge swfdec-mozilla 
```

---

### Post by gusmoney on 2008-04-25
> **Islington said:**
> Guys make sure that you remove swfdec-mozilla in synaptic or by doing 

```
sudo apt-get purge swfdec-mozilla 
```

The purge coupled with the aforementioned alternative flash version install worked for me..ie. removed the big play button.  Danke.

---

### Post by sigmabetatooth on 2008-05-30
> **gusmoney said:**
> The purge coupled with the aforementioned alternative flash version install worked for me..ie. removed the big play button.  Danke.

Dito on that... many thanks

---

