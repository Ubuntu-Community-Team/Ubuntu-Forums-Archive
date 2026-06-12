---
title: "Youtube with Chromium"
date: 2010-11-10
forum: Multimedia Software
---

### Post by googleye on 2010-11-10
Hi, just started using ubuntu and i'm having difficulties playing flash movies in chromium, works fine in Firefox. I've downloaded anything that I can find in the program central(what is it called in English?) that seems to be associated to flash.

When I googled it I only found results for older Ubuntu versions, help a lost soul?

---

### Post by googleye on 2010-11-10
NVM it suddenly fixed itself, wierd!

---

### Post by TBABill on 2010-11-10
Flash is built into Chromium. Firefox relies on you to install Flash, but Chromium (and I think Opera) does not. Glad to see you got it worked out.

---

### Post by googleye on 2010-11-10
Huh, wierd that it didn't work at first then. Are there any differences between Chromium and Chrome? Do they sync between each other? I'm running Windows on two other computers with regular Chrome and I have a lot of bookmarks

---

### Post by I'mGeorge on 2010-11-10
> **googleye said:**
> Huh, wierd that it didn't work at first then. Are there any differences between Chromium and Chrome? Do they sync between each other? I'm running Windows on two other computers with regular Chrome and I have a lot of bookmarks

Chromium it's like the prototype of Chrome. Let's say Chromium it's the testing version and Chrome it's the stable bullet proof one. But in principle they are the same thing.

---

### Post by googleye on 2010-11-10
But is Chromium still being worked on and updated? Or did you mean that they release new stuff in Chromium first to make sure theyre stable?

---

### Post by efflandt on 2010-11-10
When I have installed Chromium (64-bit) I have never seen it install its own flash.  It automatically uses the real 64-bit libflashplayer.so I put in /usr/lib/mozilla/plugins.  Although I had to point ~/.huludesktop to /usr/lib/mozilla/plugins/libflashplayer.so

But [http://googlechromereleases.blogspot.com/2010/03/dev-channel-update_30.html](http://googlechromereleases.blogspot.com/2010/03/dev-channel-update_30.html) says "*There is no bundled Adobe Flash Player plug-in for 64-bit Linux.*", so maybe that is why I have never seen it in Chromium.  Flash works fine though.

If you installed everything flash, that may have been your problem (conflicting flash plugins).  ubuntu-restricted-extras installs **flashplugin-installer**, which should be the only flash package you need, unless you want real 64-bit flash, or are doing something out of the ordinary.

---

### Post by googleye on 2010-11-10
I installed Ubuntu extra(or thats what i searched for) and one or two other Flash-related stuff, but the important thing is that it works.

---

### Post by I'mGeorge on 2010-11-10
> **googleye said:**
> But is Chromium still being worked on and updated? Or did you mean that they release new stuff in Chromium first to make sure theyre stable?

well chromium it's something like the first release of chrome. If you wanna stay fresh and have the newest things available in browsing regarding google chrome(ium), but you don't mind a bug here or there (though this rarely happens), than use chrome. If you want a browser that won't trouble you in any kinda way than use chrome, though it's a little bit oldish than chromium regarding the newest features in town.

---

### Post by googleye on 2010-11-10
I'm too lazy to download chrome, chromium was available in the program center :D

---

