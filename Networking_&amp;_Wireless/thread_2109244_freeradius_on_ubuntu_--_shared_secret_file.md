---
title: "freeradius on ubuntu -- shared secret file"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by IslandBill on 2013-01-27
Hi,

I'm running a ubuntu 10.04 LTS server with freeradius installed.  I have a very specific question which admittedly does not necessarily specify to ubuntu.  But help on this little question is nowhere that I've found.  Hopefull someone here knows the answer.

I want to script and run radclient to check user accounts.  In fact, I've already done this.  But the scripted command in a cgi file has the shared secret in it.  I'd like to use the -S option and specify the location of the shared secret file but it doesn't seem to want to play nice.  I've used:

radclient *blah blah..... -S /etc/freeradius/shared.secret.file 

No workee.  The file is just a text file with the shared secret being one word at the top and nothing else.  As clean as it can get.    Also be aware the radclient script is running on localhost, so I would think the pathname would hold up.  I've also tried running it with the file in the cgi-bin directory.  No luck there either.

Is this the right approach?

Many thanks in advance, and my apologies if anyone doesn't care for there being a freeradius question in here.

---

### Post by IslandBill on 2013-01-27
Wouldn't you know?  No sooner did I post this than I discovered my mistake.  It turns out my method does work, I had simply forgotten to include an option in the rest of the command when testing.  So here is the way it works, for the benefit of those who land here looking for the answer:

> echo "User-name=*someusername*, User-password=*somepassword*" | radclient -c 1 -n 3 -r 3 -t 3 -x 127.0.0.1:1812 auth -S sharedThis is part of a CGI script, so the "shared" file is within that cgi-bin directory.  I suppose (though I have not tested it) that any readable path would do.  The shared secret file  simply consists of the one word shared secret at the top.  Nothing else.

---

