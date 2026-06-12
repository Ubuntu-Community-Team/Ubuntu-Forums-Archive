---
title: "looking for the best music server solution"
date: 2008-12-12
forum: Multimedia Software
---

### Post by jimmy the saint on 2008-12-12
I have a server in my living room that houses my music collection.  I currently use firefly to stream the music using the DAAP protocol.  Is there anything better?  Basically, I want to be able to listen to the music on my main box (in my home office).  The issue that I have with DAAP is that I have to manually enter the ip:port of the share every time I open the music player.

I am open to any solution that would enable me to easily listen to the music stored on my server!

Thanks 

JTS

---

### Post by jimmy the saint on 2008-12-19
Nobody?  I just need  a good suggestion to be able to play music stored on my server!

---

### Post by jay li on 2008-12-19
How about MPD or Quot Libet.
But was is firefly and how do I get it?

---

### Post by scubasteve657 on 2009-04-03
sounds like your problem is more with identifying your server than with daap.

actually i've never seen a situation where daap requires an ip address...but if you wanna avoid using ip addresses add something like:
192.68.0.2 server
to your /etc/hosts file on the client

this file exists in windows as well but is a little harder to find; a quick google search should set you in the right direction though.

---

### Post by matthewboh on 2010-02-08
Apparently it requires the avahi-daemon to be running on your server - that way desktop should just boot up and find it.

It's in the repositories, so you should be able to just say

```
sudo apt-get install avahi-daemon
```

and it should just start appearing.

However, I'm having other various problems with mt-daapd and am looking for a better solution.

---

