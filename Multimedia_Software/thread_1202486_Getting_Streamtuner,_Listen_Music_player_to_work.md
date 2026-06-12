---
title: "Getting Streamtuner, Listen Music player to work"
date: 2009-07-02
forum: Multimedia Software
---

### Post by geovino on 2009-07-02
I have streamtuner and listen installed and both can't play shoutcast live streams. How do I get them to work?

what files are missing?

I'm running Xubuntu 9.04 64bit.
(these programs all run on my laptop running Ubuntu 9.04)

---

### Post by HappyFeet on 2009-07-02
Start streamtuner via terminal and try to listen. Does it report anything?

---

### Post by geovino on 2009-07-02
> **HappyFeet said:**
> Start streamtuner via terminal and try to listen. Does it report anything?

It will play one of the preselected stations, but Shoutcast won't list any stations. What am I missing?

---

### Post by madman100 on 2009-08-03
this has been covered before on this forum here is the fix from the forum  Shoutcast has updated their web page, which no doubt has broken Streamtuner. However the Shoutcast website has a link to the older version of their search engine at [http://classic.shoutcast.com](http://classic.shoutcast.com).

So here's my hack to redirect Shoutcast queries to the "classic" page:-
Code:

sudo vi /etc/hosts

[Of course you can use nano or mousepad instead of vi.]
Add the line
Code:

205.188.234.120 [www.shoutcast.com](www.shoutcast.com)

and streamtuner's directory should come back online.

This redirection will affect firefox as well, so you'll no longer be able to access the "new" version of Shoutcast. Once Streamtuner is fixed in the repositories you might want to remove that line from /etc/hosts.

---

### Post by geovino on 2009-08-04
> **madman100 said:**
> this has been covered before on this forum here is the fix from the forum  Shoutcast has updated their web page, which no doubt has broken Streamtuner. However the Shoutcast website has a link to the older version of their search engine at [http://classic.shoutcast.com](http://classic.shoutcast.com).

So here's my hack to redirect Shoutcast queries to the "classic" page:-
Code:

sudo vi /etc/hosts

[Of course you can use nano or mousepad instead of vi.]
Add the line
Code:

205.188.234.120 [www.shoutcast.com](www.shoutcast.com)

and streamtuner's directory should come back online.

This redirection will affect firefox as well, so you'll no longer be able to access the "new" version of Shoutcast. Once Streamtuner is fixed in the repositories you might want to remove that line from /etc/hosts.

I tried adding that address to the file, but it still didn't play anything. I uninstalled Streamtuner for now. May use another program, like Exaile or just get the streams playing through Movie player. there may be some corruption, have had this much trouble with Streamtuner before. 

Maybe one day I'll find the fix.

---

