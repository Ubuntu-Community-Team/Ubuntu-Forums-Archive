---
title: "Proxy Settings won't properly turn off proxy"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by jazzvibes on 2011-09-03
I have done quite a bit of searching and am yet to find a decent answer. I would really like some help here. Thanks in advance. Situation is simply I have a pac proxy at uni and direct connection at home, on Ubuntu natty. I need the internet, software centre, and terminal to work in both locations.
[LIST]
[*]I have used the Network Proxy application to make a new location with the proxy script. This works fine for internet browsing but does not work for Software centre. 

[*]I used Synaptic's own  proxy settings for downloading new applications/updating.

[*]For the terminal i used this script, which I believe works just for the current terminal. ```
export http_proxy='http://USERNAME:PASSWORD@web-cache-ext.uni.edu:8080'
```

[*]In dropbox, I manually changed the settings from auto-detect to manual, which worked. But I haven't changed any settings in Air... thats on some sort of autodetect (and stuck on proxy)
[/LIST]

However, in discovering these methods, I have tried everything i could find on the internet ... to little avail.

There are a few problems.
[LIST=1]
[*]Once I clicked "apply system wide" in Network Proxy setings, it now asks me every time I change. It didn't used to before ... what has changed and how do I change it back?
[*]Some applications are stuck using the proxy. Anything that has a sort of auto-detect. this includes the terminal, but also dropbox, and adobe-air (as far as I've discovered so far)
[/LIST]

I am willing to submit a bug report if someone can help me make sure I've already covered the bases. I would like to know the ideal workflow for changing the proxy for these two locations and also the best way to ensure all my settings are returned to default - so please exhaustively check the other 'obsolete' ways of changing proxy which are easy to find with simple googling for  ubuntu proxy. 
I've checked:
[LIST]
[*]/etc/apt/apt.conf
[*]/etc/bash.bashrc
[*]/home/username/.bashrc
[/LIST]

---

