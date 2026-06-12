---
title: "SVN server running over &quot;https&quot; not &quot;svn+ssh&quot;, lighttpd"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by vcppp_p on 2009-10-22
Hi,
 my machine running Ubuntu 9.04 is running lighttpd on port 80 (much faster than Apache2) and recently I started SVN server (using openssh I guess? Lol I dunno, I just typed "svnadmin" and it was already here, it must have been installed together with SVN-client I guess...). Unfortunately I have to connect to the machine using "svn+ssh://" protocol, which's configuration is kinda tricky on windows machines (generating both public & private key, priv key conversion, configuring putty etc) in order to avoid being prompted to input password... Therefore I'd like to enable access over https:// protocol (which allows TortoiseSVN users to simply check the "remember password" field)... 

Unfortunately I was unable to find out how to do that, considering I'm running lighttpd, not Apache ...

Thanks in advance,
v.

---

### Post by lloyd_b on 2009-10-22
> **vcppp_p said:**
> Hi,
 my machine running Ubuntu 9.04 is running lighttpd on port 80 (much faster than Apache2) and recently I started SVN server (using openssh I guess? Lol I dunno, I just typed "svnadmin" and it was already here, it must have been installed together with SVN-client I guess...). Unfortunately I have to connect to the machine using "svn+ssh://" protocol, which's configuration is kinda tricky on windows machines (generating both public & private key, priv key conversion, configuring putty etc) in order to avoid being prompted to input password... Therefore I'd like to enable access over https:// protocol (which allows TortoiseSVN users to simply check the "remember password" field)... 

Unfortunately I was unable to find out how to do that, considering I'm running lighttpd, not Apache ...

Thanks in advance,
v.

I have no clue on the lightttpd, but as an alternative you could run "svnserve", and then access the svn repository via "svn://...".  A Google search should turn up the instructions for setting up svnserve (try looking on tigris.org if Google doesn't turn up anything).

AFAIK, TortoiseSVN plays as nicely with svnserve as it does with Apache+svn...

Lloyd B.

---

