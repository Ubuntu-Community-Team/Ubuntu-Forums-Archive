---
title: "pandora won't finish loading"
date: 2009-05-05
forum: Multimedia Software
---

### Post by Iwilllearn2 on 2009-05-05
I'm using firefox and I when to [www.pandora.com](www.pandora.com) and it will say please wait pandora is loading but will only load about half way and never finish loading. There is not any error message it just won't finish loading.

---

### Post by Iwilllearn2 on 2009-05-05
Update Hulu doesn't work either, both worked in Ubuntu 8.10, but now don't work.

---

### Post by Iwilllearn2 on 2009-05-05
I just got Ubuntu-restricted-extras but it still hangs while loading and won't finish loading.
I'm going to look for more restricted packages. I just discovered the Show button in Add/Remove Applications. Now its on All available applications instead of just Canonical-maintained applications, so I might find a package to make it work.

---

### Post by Iwilllearn2 on 2009-05-05
Is anyone there? I'll check this thread again before I go to bed, thanks for quick help on my duel boot woos anyway.

---

### Post by rswhiting on 2009-05-12
[The solution]("http://impnerd.com/ubuntu-is-firefox-crashing-with-flash")

I've been looking for the solution to this very problem, and I just found it after I came here. Here's the basic summary of the above link:
1. remove swfdec-mozilla
2. sudo apt-get install adobe-flashplugin
3. Restart firefox
4. Enjoy Pandora (and Hulu)

---

### Post by qwelm on 2009-06-10
Thanks for posting this solution.  It worked great on my wife's new install

---

### Post by discodan on 2009-06-29
This worked great for me as well on Xubuntu 9.04.  Thanks so much!  :guitar:

---

### Post by James_nac on 2009-08-01
Have the same problem.  Installed ununtu 9.0.4 yesterday (Linux newbie!).  I encountered the problem with [www.pandora.com](www.pandora.com) not loading all the way.  I thought maybe I should have chosen a different plug-in for Flash so I went to Tools-> Manage Content Plug-ins, did the search, and changed it to the Adobe one.  I still had the same problem so I did a search and found this post.  I tried following the suggested fix, but this is what I get when I do:

jamesr@cartman:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

So I went back into Firefox and now, the Tools -> Manage Content plug-ins menu item is disabled!  I have no idea what to do now...

Thanks,
James

---

### Post by xc3RnbFO8P on 2009-08-01
Download the Adobe Flash Player from here (works in 8.04, 8.10, 9.04):
[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

---

### Post by James_nac on 2009-08-02
I think I did that right.  I chose .deb for ubuntu (or something like that) and it threw up a bunch of confusing windows and finally said it was finished installing.  Restarted firefox and at least now the menu item "Manage Content Plug-ins" is not disabled anymore.  However, pandora.com still won't finish loading.  Gets to about 20% and just hangs.  The Manage Content Plug-ins window still says "Swfdec SWF player" next to "Adobe Flash movie...".

---

### Post by hibliss on 2009-08-02
Add the Medibuntu repository and you can get Flash Nonfree through Synaptic.

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by ubugirl on 2009-08-13
Removed swfdec-mozilla and now Pandora loads.  Thank You.

---

### Post by ManiacMagee on 2009-09-12
I had the same problem until I found this thread. Thanks for posting the solution rswhiting.

---

