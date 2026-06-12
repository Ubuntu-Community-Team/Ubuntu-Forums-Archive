---
title: "xbmc &lt;-&gt; xbox 360?"
date: 2011-12-18
forum: Multimedia Software
---

### Post by netopalis45 on 2011-12-18
I have been trying to use XBMC to stream media to my Xbox 360 but haven't had any luck. I can see my XBMC server but when I select it, none of my songs or videos show up. What do I need to do to make this work?

---

### Post by stumpalump on 2011-12-18
I had a similar problem like this before. What was happening was xbmc was taking forever to build the list to send to the xbox. So xbox would say "No Videos Found" over and over until xbmc finally finished building the list of movies for sharing. Why?

I found out it was because I had multiple movies that were archived into .rar, .r01, .r02 etc. and xbmc was extracting them before building the list to send. 

So, I manually extracted or deleted the ones I wanted until none were left and then list built instantly after that.

Also, I edited the file ~/.xbmc/userdata/upnpserver.xml and changed the line "MaxReturnedItems" to this so that ALL my movies showed up on xbox.

```

<MaxReturnedItems>1000</MaxReturnedItems>

```

Hope this helps. If it doesn't. I suggest taking a look at your media library and what may be in there to cause the hang up. There really should only be strictly video files in there and nothing else.

---

### Post by netopalis45 on 2011-12-19
Do I have to be booted into XBMC or will just running the application work? I did what you said and still don't see anything.

---

### Post by stumpalump on 2011-12-19
I don't boot into xbmc ever only use application. When you try to browse from the xbox, do you notice that the computer starts working? Or are you having no activity from cpu

---

### Post by netopalis45 on 2011-12-19
As far as I can tell there is no additional CPU activity.

---

### Post by stumpalump on 2011-12-19
Try opening port 59755 on your firewall. I find it a little weird that your xbox can see the xbmc server but doesn't list anything. Are you just getting the standard "No Videos Found"?

Also, do you have an actual library built inside xbmc? The upnp server doesn't share the files it only shares what's in the library.

---

### Post by netopalis45 on 2011-12-20
I finally got about 4 songs to show up (out of several thousand, I think) and then they were gone. I am getting the "No Videos Found" and "No Albums/Songs Found" errors. XBMC is set to reload the library every time it starts up.

---

### Post by stumpalump on 2011-12-20
My library is set to only update when I say. Maybe you should try to turn that off? It's possible that it's still updating and I would bet that has a lot to do with it. 

Sounds to me like your issue could probably be solved by tinkering with some settings here and there.

I will say thought that XBMC is not perfect at upnp. Even though I have gotten my movie list to pop-up pretty fast now, I don't see the submenu for Title, Genre, Actor, Year etc. I only see the movies. Also, the movie names are usually kinda messed up and garbled and I get lucky if it plays the right movie that I clicked on.

---

### Post by netopalis45 on 2011-12-20
I ended up having to reload all my stuff into the library so it works now. Thanks for the help.

---

### Post by stumpalump on 2011-12-20
Haha it would be something like that. Glad you figured it out. Just remember xbox doesn't like a lot of the new formats for HD, particularly mkv

---

### Post by sentinelace on 2012-01-28
hate to bump into your thread, but how did you setup xbmc to stream? What guide did you follow? I want to do the same thing.  Can you stream mkv and avi?

---

### Post by stumpalump on 2012-01-29
> **sentinelace said:**
> hate to bump into your thread, but how did you setup xbmc to stream? What guide did you follow? I want to do the same thing.  Can you stream mkv and avi?

Xbmc is already setup to stream through the upnp options in settings. Xbmc wiki also is your friend

---

### Post by netopalis45 on 2012-07-11
Is there a way of streaming a particular playlist that I made in XBMC to my Xbox?

---

