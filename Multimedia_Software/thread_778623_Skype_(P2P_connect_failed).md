---
title: "Skype (P2P connect failed)"
date: 2008-05-02
forum: Multimedia Software
---

### Post by jaknap on 2008-05-02
Hi,

I have already posted on this forum about Skype, but still there is solution. When I login to Skype it gives me a error Sign in failed. P2P connect failed.I am frustrated with this error even though I have searched lot, I had open ports from proxy server and lot more R & D  like re-installation of Skype. My Skype is behind the proxy server. But nothing.
So please suggest me.


Thanks :)

Pranky****

---

### Post by Vermind on 2008-05-02
Hello,
You might try Skype options - advanced - proxy settings there.
It's set by default to proxy auto detection. I have never seen Skype fail in connecting before, but this might be worth a try.

---

### Post by jaknap on 2008-05-02
Hi,

I still tried all these options but sorry same message is displayed.
Can u have a favor about port details in ubuntu, whether there is some thing auto blocking of ports for skype.
Can there should be any other suggestion for this so I can login my account.


Pranky :)

---

### Post by carlh on 2009-03-26
I had the same problem. After searching many pages with google, I found the solution. Turns out the config files are incompatible with a prior version
of Skype I had. The problem was fixed with "rm -rf ~/.Skype" then restart
Skype. (I only have a normal WiFi/LAN router-- no proxy. Skype loaded fine, was installed via the repository from Skype via adept with no problem.)

---

### Post by shri_dhar on 2010-12-22
> **carlh said:**
> I had the same problem. After searching many pages with google, I found the solution. Turns out the config files are incompatible with a prior version
of Skype I had. The problem was fixed with "rm -rf ~/.Skype" then restart
Skype. (I only have a normal WiFi/LAN router-- no proxy. Skype loaded fine, was installed via the repository from Skype via adept with no problem.)

I tried this but it still did not work for me.
restart .. do you mean reinstall skype?

---

### Post by DoneRightI.T. on 2010-12-22
Same problem here, running 10.04 I have:

- Removed the .Skype folder
- Verified all ports open and no proxy enabled

Frustrating.

---

### Post by snakedog on 2010-12-22
It's got to be a Skype issue as I'm experiencing issues logging in via Windows XP too.  My Windows machine managed to get logged in after numerous attempts, but I got thrown off almost immediately (less than 5 minutes).  I did manage to initiate a Skype chat briefly before being thrown out.  

I've doublechecked the port forwarding on the gateway (router) but that shouldn't matter as Skype will default to ports 80 & 443 if the default port is blocked.  And I too cannot connect to [http://forum.skype.com](http://forum.skype.com) either.  I suspect their server(s) is overloaded at this point.  FYI!

p.s. -- I'm a Skype Pro user.  I did manage to login via the website and set call fwd'ing to my cell.

---

### Post by snakedog on 2010-12-22
Skype _is_ down (as of 12/22/2010 afternoon):

[http://gigaom.com/2010/12/22/skype-goes-down-millions-impacted/](http://gigaom.com/2010/12/22/skype-goes-down-millions-impacted/)

[http://news.cnet.com/8301-13506_3-20026408-17.html](http://news.cnet.com/8301-13506_3-20026408-17.html)

[http://content.usatoday.com/communities/technologylive/post/2010/12/skype-is-down/1](http://content.usatoday.com/communities/technologylive/post/2010/12/skype-is-down/1)

---

### Post by mcarrera on 2010-12-22
:-k

[https://support.skype.com/en/faq/FA10874/I-m-having-problems-signing-in-to-Skype-today?frompage=category](https://support.skype.com/en/faq/FA10874/I-m-having-problems-signing-in-to-Skype-today?frompage=category)

---

### Post by Godspell on 2010-12-28
> **snakedog said:**
> Skype _is_ down (as of 12/22/2010 afternoon):

[http://gigaom.com/2010/12/22/skype-goes-down-millions-impacted/](http://gigaom.com/2010/12/22/skype-goes-down-millions-impacted/)

[http://news.cnet.com/8301-13506_3-20026408-17.html](http://news.cnet.com/8301-13506_3-20026408-17.html)

[http://content.usatoday.com/communities/technologylive/post/2010/12/skype-is-down/1](http://content.usatoday.com/communities/technologylive/post/2010/12/skype-is-down/1)

I'm still having 'P2P Connection failed' error. Does it mean Skype is still down???

Please, if there's any solution, let us know.

EDIT: Actually, never mind because it's working now :D No fix was applied. I kept trying and got in at the end.

---

### Post by VonSpyder on 2010-12-28
my skype is up and running. me thinks it was just down.

---

### Post by stonypoint on 2012-11-10
rm -rf ~/.Skype worked fine for me. Connected at last!

---

### Post by wildmanne39 on 2012-11-10
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

