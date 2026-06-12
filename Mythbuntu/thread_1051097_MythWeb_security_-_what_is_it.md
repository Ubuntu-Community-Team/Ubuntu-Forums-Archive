---
title: "MythWeb security - what is it?"
date: 2009-01-26
forum: Mythbuntu
---

### Post by fatmonk on 2009-01-26
When I select to password protect MythWeb from within MCC, what type of security is used?

Windows Mobile IE doesn't seem to recognise / support the authentication, which is a real same as I'd really like to be able to schedule recordings while I'm out and about, but I obviously don't want to open up access to the box without password protecting MythWeb.

Also, after I installed phpMyAdmin I was unable to set .htaccess security on that directory, so I'm wondering of there is some other type of security being used that over-rides .htaccess. (ie set up .htaccess the way I always have, but wasn't challenged at all when browsing to the phpMyAdmin directory!)

-FM

---

### Post by ian dobson on 2009-01-26
Hi,

Are you sure you're editing the correct .htaccess file? For me my mythweb directory is a symbolic link to /usr/share/mythtv/mythweb.

Maybe try restarting apache after editing the .htaccess file.

Regards
Ian Dobson

---

### Post by fatmonk on 2009-02-13
OKey dokey,

Have got .htaccess working in the mythweb directory, but have falled foul of something I read about a few weeks ago.

I'm not entirely sure how as I thought I'd done it the right way around, but no such luck.

Basically I am now stuck with the PDA/small screen version of MythWeb because I browsed to Mythweb from my PDA and logged in via the htaccess prompt.

I only configured one user for mythweb, and it seems that that user is now stuck with the PDA version.

I'd prefer not to have two users, but if I do have to then I want the current user to be the full mythweb and I want to create a new second user for the PDA version.

So... is there a way to get the user agent caching or whatever it is that means I'm only getting the PDA version, to stop caching or whatever its doing?

If not, is there a way to reset whatever has stored the setting to display the PDA version for the user that I have created already? Then I can create a PDA specific user.

Cheers,

FM

---

### Post by Boppy3125 on 2009-02-13
I think this is the same thing that happens when messing with themes.  See this discussion:

[http://www.gossamer-threads.com/lists/mythtv/commits/329712](http://www.gossamer-threads.com/lists/mythtv/commits/329712)

Short version is to add ?RESET_THEME=yes to your url and it should switch you back.  Good luck.

---

### Post by fatmonk on 2009-02-13
No joy with ?RESET_THEME=yes I'm afraid. Still the same problem.

-FM

---

### Post by fatmonk on 2009-02-15
Doh!

Read the referred thread next time (dumb Monk!)...

?RESET_TMPL=true works a treat.

So, I may well be able to access my box from my phone and laptop soon.

:)

-FM

---

