---
title: "Flash-plugin error (Mozilla)"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by Sofie on 2007-10-08
I am having trouble reading flash-sites. 
Before I did anything, Firefox just stopped, and I could not use the flash on the sites. 

Then I tried installing Gnash wich made everything worse. I unistalled.

Then I tried installing swf, that did not change anything.

After reading about it at [http://www.psychocats.net/ubuntu/flash#aptget](http://www.psychocats.net/ubuntu/flash#aptget), I did this:
sudo aptitude update && sudo aptitude install flashplugin-nonfree

And now its the same error as with Gnash:
 .alpha{filter:alpha(opacity=25);opacity: 0.5;-moz-opacity:0.5;}

When I go to youtube, it says I will have to get a flashplayer.

How can I make flash-plugins / flash player ?? work with Firefox in Ubuntu 7.04?

---

### Post by RomeReactor on 2007-10-08
Hi. Did you restart Firefox after installing Flash? If so, perhaps deleting the **xpti.dat** file in Firefox's configuration in your home folder can help (Firefox will re-create the file next time you open it):

Close Firefox and:
```
rm ~/.mozilla/firefox/*.default/xpti.dat
```
Then open it again.

---

### Post by Sofie on 2007-10-08
Now I can watch videos.

But this site: [http://www.myspace.com/69newscph](http://www.myspace.com/69newscph) is still not working. I see the site, but I cant interact. I cant push the button "add friend".

This site is either working:
[www.rapunsel.dk](www.rapunsel.dk)

But this -VERY FLASHY!!! - site IS working: [www.requiemforadream.com](www.requiemforadream.com)


I am very confused?:confused:

---

### Post by RomeReactor on 2007-10-08
Same problem here with those sites. Sorry, I'm out of ideas at the moment.

---

### Post by Sofie on 2007-10-08
Then I think it must be the sites.

Thank you so much for looking them up!!

Beans to you! (If thats the credit for helping?)

---

