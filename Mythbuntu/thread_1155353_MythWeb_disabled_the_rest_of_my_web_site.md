---
title: "MythWeb disabled the rest of my web site"
date: 2009-05-10
forum: Mythbuntu
---

### Post by bshephard on 2009-05-10
Hello 
I just installed MythWeb on my machine which also hosts a static index page along with word press and round cube web mail and a few other bits and bobs. The problem is when I install MythWeb it changes something in my Apache config that disables the rest of my stuff.

for example I go to [http://mydomain.com](http://mydomain.com) and I'm immediately bounced to mydomain.com/mythweb and asked for the login details. If I go to mydomain.com/index.html then my index page will display properly. I also found if I click the links from there to word press (mydomain.com/wordpress) rather than seeing my blog I just get a directory listing and the same goes for roundcube webmail. When I uninstall MythWeb it goes back to normal again.

I'm using webmin to configure apache but I can't make out what's changing in my config file to put this right.

Perhaps this should be filed as a bug. I just wondered if anyone else was experiencing the same issue or knew of a way to put it right first. I had a quick Google but couldn't find anything.

Cheers
Ben

---

### Post by bshephard on 2009-05-10
[SIZE="4"]Found the solution[/SIZE]

I'd installed Mythweb from the Mythbuntu control centre.
After posting i decided to see what happened if i installed it using Apt-Get and it asked me a few questions one of which was "Will I be using this web server exclusively with MythWeb" I don't think the mythbuntu package management gui has the ability to ask questions like this during install and is just defaulting to an exclusive mythweb setup.

So uninstall from the Mythbuntu control centre and open up a terminal then:

$ sudo apt-get install mythweb

All will become clear as the install runs.
I have the feeling this is just a jaunty issue.


Hope this helps someone as it had me scratching my head for a bit.

Cheers
Ben

---

### Post by superm1 on 2009-05-10
Yeah, this is currently just a jaunty issue.  Can you file a bug on:

[http://launchpad.net/ubuntu/+source/mythbuntu-control-centre](http://launchpad.net/ubuntu/+source/mythbuntu-control-centre)

so that we can keep this tracked and shoot to have it fixed in karmic?  (Asking the question whether the machine is exclusively used for mythweb that is)

---

### Post by spicemuseum on 2009-05-29
> **bshephard said:**
> [SIZE="4"]Found the solution[/SIZE]
...uninstall from the Mythbuntu control centre and open up a terminal then:

$ sudo apt-get install mythweb

All will become clear as the install runs.I'll try this later.

Tying up with another thread on the same issue:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1117502](http://www.uluga.ubuntuforums.org/showthread.php?t=1117502)

...and the bug is reported fixed in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/356798](https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/356798)

---

### Post by brian mcgee on 2009-06-13
> **bshephard said:**
> 
So uninstall from the Mythbuntu control centre and open up a terminal then:

$ sudo apt-get install mythweb

Worked for me. Much thanks!

---

