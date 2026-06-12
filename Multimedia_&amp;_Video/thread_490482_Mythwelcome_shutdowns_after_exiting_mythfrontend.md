---
title: "Mythwelcome shutdowns after exiting mythfrontend"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by Saubazi on 2007-07-02
It seems to be a known issue with gnome however, the solution does not seem clear to me.

Here is an example:

[http://www.gossamer-threads.com/lists/mythtv/commits/264985](http://www.gossamer-threads.com/lists/mythtv/commits/264985)

So the problem is that mythwelcome is in sessions and starts automatically after boot and autologin.
It consequently starts mythfrontend - the problem is that after exiting mythfrontend it also exits
mythwelcome. I tried adding a shell script to sessions that starts mythwelcome. I thought it worked the
first time I tried it but afterwards it did not work anymore :(

I am wondering that bit about saving session or something in the above discussion. 
I think this is a common issue with gnome and mythwelcome but after searching
longer time with google I haven't been able to found solution :(

---

### Post by reclusivemonkey on 2007-07-04
Sorry I don't have an answer to your question, but you may want to ask on the MythTV forums; they might be able to help. There is also a #ubuntu-mythtv IRC channel with some helpful and knowledgeable people in.

---

### Post by Saubazi on 2007-07-11
I am still struggling with the issue...I have tried to ask about via irc to no avail.
From what I read, it is a typical problem with gnome and sessions - I am just not
able to make anything out of the suggestions made in that link...

---

### Post by reclusivemonkey on 2007-07-11
Have you tried using a different desktop? Gnome is overkill really if its going to be a myth frontend. What about using Openbox or XFCE?

---

### Post by Saubazi on 2007-07-12
At the moment I am interested in getting it to run with gnome. Of course I can solve it by installing fluxbox or whatever, although it means that I need to uninstall ubuntu-desktop - for fluxbox I'd need another autologin and so on, so at the moment I am looking for solution to get it running under gnome and that's that. It might be overkill from the "heaviness", like it is overkill having openoffice and other default packages from desktop on the system as well, but as long as there is no real drawback it has been a minimum installation effort.

---

