---
title: "mplayer wants to use proxy"
date: 2010-11-27
forum: Multimedia Software
---

### Post by bryncoles on 2010-11-27
Greetings friends!

I'm trying to use mplayer to stream some content from the net to my desktop. 

This worked fine the first time I did it (though failed dismally on all subsequent occasions. Now, the first umpteen times, I was behind a proxy. Now I am not behind a proxy, but mplayer still looks for the proxy settings. Why? I have changed the proxty settings in the network proxy (applied globally), in Firefox and every where else I can think of. 

I use the following command:

```
mplayer -dumpstream -dumpfile ~/Desktop/<desired_filename>.avi http://<source>.avi
```

and I'm told in response

```
Resolving www<proxy> for AF_INET6... 
```

What gives? Why is mplayer trying to use a proxy, and how can I tell it not to?

Cheers guys!

---

### Post by bryncoles on 2010-11-28
bumpy?

---

