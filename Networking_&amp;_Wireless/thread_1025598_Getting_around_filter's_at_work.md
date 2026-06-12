---
title: "Getting around filter's at work"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by mikeman141 on 2008-12-30
At work the IT guys have blocked some very important things like youtube, facebook, and most ridiculously ".zip" files.  I have an "always on" desktop running 8.04 at home.

I believe a friend of mine once told me I could set up that machine as a proxy server and redirect my traffic through it and get past the filters.  Is this true?  Does anyone know of a good HOWTO guide on setting something like this up?  Or some other solution to the nonsense I have to jump through at work.  (The laptop I bring to work runs Ibex)


Thanks,
Mike

---

### Post by thefunnyman on 2008-12-30
[http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025)

---

### Post by Iowan on 2008-12-30
Unfortunately, the IT guys are responsible for the network.  My employer blocks some websites (the local radio station weather report is considered "entertainment") and our email blocks some critical attachments. If I attach an unregistered computer to the network, my phone will ring before it gets booted. But it's their network, their responsibility to keep corporate equipment virus-free and operating within corporate guidelines.

---

### Post by ieee488 on 2008-12-30
@Mikemman141,

I'd be very interested if you are able to get this to work.

My company's IT filters is a royal pain the butt, and I'd love to get around them too.

Just note that if they have software monitoring this, and I am guessing they do, this may be considered grounds for dismissal as it has the potential to put company assets at risk. In this climate, you don't want to be giving them a reason to fire you.

---

### Post by travelinman81 on 2008-12-30
you probably could set up a proxy that you could access from work through a web browser by IP address or dyndns from work to home..That being said I would say it is probably a bad idea. One you will have an open proxy that god knows who will be using for what without elaborate ACL's in place. Two like the other poster said circumventing the companies security policy is almost always grounds for dismissal. Three it is always a bad idea to piss off the IT guys or NetAdmin at your place of employment. Now I have found that squid is a very versatile proxy I use it at home and it is very configurable and can do a lot of stuff I have it accompanied with Dans Guardian so that I can filter content like virus's and stuff from the windows users on my network. You can set up an external proxy with it to use to surf your home internet from work. I would look into that if you are looking to get around your companies security stuff.

---

### Post by thefunnyman on 2008-12-30
I will agree with other posters that circumventing your companies IT filter is probably not the best idea.....just be smart...no farm animal pron at work if you know what I mean...I will say that if you have internet access at work, then https port is probably also open, so you could forward encrypted ssh traffic over an encrypted port...then, as long as IT shop isn't filtering things at the service level, you should be in the clear b/c all the net monitoring tools would see is encrypted traffic going over an encrypted channel....again, just be smart and be aware of the consequences.

EDIT:  This is also very good practice for when you are on a laptop connected to an unsecure wireless network....all internet traffic will be encrypted, just use strong passwords, or better yet, RSA encryption..

---

### Post by mikewhatever on 2008-12-30
Mikeman, please don't ask such questions here. You company's IT policy must be respected, we can't help you circumvent it.

---

### Post by thefunnyman on 2008-12-30
Would it be wise of me to delete my posts?  I do not want to break the forum rules..I very much enjoy the community here and would not like to be banned.....Will delete at the request of community members..

thanks

---

### Post by Joeb454 on 2008-12-30
As frustrating as it may be, company's put filters in place for a reason. This forum isn't the place to be asking how to circumvent those filters

---

