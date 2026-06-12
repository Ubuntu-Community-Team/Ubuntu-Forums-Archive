---
title: "Windows share connection stopped working"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by jis4joe on 2011-01-06
**Windows share connection stopped working** 
I've been able to connect to a windows share on my network by:
1) Places > Connect to Server...
2) Choosing "Windows share" from the pull down
3) Entering in the IP address of the machine I'm connecting to into Server: field

Suddenly this didn't work today. When I investigated I found that the machine I was connecting too was assigned a different IP address... so... I entered the new IP address into the Server: field but this time was confronted with the requirement of a user name, domain, and password despite the fact that I have passwordless sharing enabled on the "server" machine and have never been asked for this by my UBUNTU machine in the past. Unfortunately, nothing I enter into these fields seem to matter... none of them get me reconnected to the "server".

Can anybody explain why this might be happening and better yet... how to fix easily fix it? It seems like I've experienced this once before and a reinstall of UBUNTU got things connecting again. It wasn't a big deal at the time because I needed to clean things up then anyways... but I'd rather understand why it is happening and the fix this time.

---

### Post by PatchesTheCaveman on 2011-01-07
You might be experiencing this bug:  [http://ubuntuforums.org/showthread.php?t=1655434](http://ubuntuforums.org/showthread.php?t=1655434)

---

### Post by jis4joe on 2011-01-07
Thanks.  That looks promising.
 
Side question while I have your attention... any idea why entering the share name in step #3 from original post ie... Hometheater (in this case)... Ubuntu won't find the server machine on the network but putting the IP address in it will?

---

### Post by PatchesTheCaveman on 2011-01-07
That's rather complicated and has to do with the differing ways Windows and Linux identify and discover computers by name.

Sometimes editing /etc/samba/smb.conf and changing this line to 'yes' helps:
```
wins support = yes
```

---

### Post by jis4joe on 2011-01-08
Are you sure I should set...

wins server = yes

or should I set

wins support = yes

What is the difference?

---

### Post by PatchesTheCaveman on 2011-01-08
Good catch!  Yes, you should turn on WINS Support:
```
wins support = yes
```

And comment out the WINS server line:
```
#wins server = 192.168.0.1
```

Sorry about that!  I'll correct my original post for future readers.

---

