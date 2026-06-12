---
title: "mythvideo video manager"
date: 2009-07-17
forum: Mythbuntu
---

### Post by dannyboy79 on 2009-07-17
i have Enter IMDB # plastered in the middle of my video manger screen?
[http://img176.imageshack.us/my.php?image=screenshot3u.png](http://img176.imageshack.us/my.php?image=screenshot3u.png)
when I try to perform a search on movies I can't even see what;s behind that stupid pop up for entering the IMDB thingy. It's always there? I am running mythtv 0.21.0+fixes19961-0ubuntu8
 in Jaunty. I don't remember that being there before I upgraded from Hardy to Intrepid and then to Jaunty. ANy help please.

---

### Post by klc5555 on 2009-07-17
> **dannyboy79 said:**
> i have Enter IMDB # plastered in the middle of my video manger screen?
[http://img176.imageshack.us/my.php?image=screenshot3u.png](http://img176.imageshack.us/my.php?image=screenshot3u.png)
when I try to perform a search on movies I can't even see what;s behind that stupid pop up for entering the IMDB thingy. It's always there? I am running mythtv 0.21.0+fixes19961-0ubuntu8
 in Jaunty. I don't remember that being there before I upgraded from Hardy to Intrepid and then to Jaunty. ANy help please.

Known bug. The fix involves editing a single character from "enterimbd" to "entertmdb" in the config file for the particular theme you're using on your frontend. 

I'll quote rha7dotcom's post (fixing one typo):

-----------------

I followed the 'make it disappear fix' at [https://bugs.launchpad.net/mythbuntu/+bug/339880](https://bugs.launchpad.net/mythbuntu/+bug/339880), which comments out the enterimdb section at video-ui.xml at /usr/share/mythtv/themes/<you-theme>/video-ui.xml....

Et voila!

It started complaining that it couldn't get the "entertmdb" object!

Guessing I renamed the section to "entertmdb" and it works.

[B]So, in your /usr/share/mythtv/themes/<you-theme>/video-ui.xml
Change the line
<container name="enterimdb">
to
<container name="entertmdb">
or
<container name="entermdb">

whichever works ....[/B]

And in case it doesn't, just comment it completely (surround it with < !-- and -- >) and run mythfrontend -v all from the console, go to the menu (M key) and choose "Manually enter video #" and go back to the console and see what mythtv complains about, then change the above line to whatever it was.

Hope this works for you guys.

Later
Rha7

---

### Post by dannyboy79 on 2009-07-17
> **klc5555 said:**
> Known bug. The fix involves editing a single character from "enterimbd" to "entertmdb" in the config file for the particular theme you're using on your frontend. 

I'll quote rha7dotcom's post (fixing one typo):

-----------------

I followed the 'make it disappear fix' at [https://bugs.launchpad.net/mythbuntu/+bug/339880](https://bugs.launchpad.net/mythbuntu/+bug/339880), which comments out the enterimdb section at video-ui.xml at /usr/share/mythtv/themes/<you-theme>/video-ui.xml....

Et voila!

It started complaining that it couldn't get the "entertmdb" object!

Guessing I renamed the section to "entertmdb" and it works.

[B]So, in your /usr/share/mythtv/themes/<you-theme>/video-ui.xml
Change the line
<container name="enterimdb">
to
<container name="entertmdb">
or
<container name="entermdb">

whichever works ....[/B]

And in case it doesn't, just comment it completely (surround it with < !-- and -- >) and run mythfrontend -v all from the console, go to the menu (M key) and choose "Manually enter video #" and go back to the console and see what mythtv complains about, then change the above line to whatever it was.

Hope this works for you guys.

Later
Rha7
i changed it to <container name="entertmdb"> and it now is ok. THANKS. Now we just need a scraper (bulk updater) that works with themoviedb.org because they have much better dvd covers

---

