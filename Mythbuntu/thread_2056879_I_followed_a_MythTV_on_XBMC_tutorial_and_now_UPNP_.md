---
title: "I followed a MythTV on XBMC tutorial and now UPNP wont work"
date: 2012-09-12
forum: Mythbuntu
---

### Post by JamerTheProgrammer on 2012-09-12
Hey! 
I followed a MythTV on XBMC tutorial and now UPNP wont work.
This is the tutorial:
[http://wiki.xbmc.org/?title=MythTV](http://wiki.xbmc.org/?title=MythTV)

I changed all the backends addresses to the local IP (192.168.2.11) of its self instead of localhost.

Then I entered:
   $ mysql -u root -p
   mysql> grant all on mythconverg.* to mythtv@"192.168.1.%" identified by "mythtv";
   mysql> flush privileges;

Now I cant find my MythTV box via UPNP anymore.
What have I done?
I feel stupid :lol:

---

### Post by nickrout on 2012-09-12
> **JamerTheProgrammer said:**
> Hey! 
I followed a MythTV on XBMC tutorial and now UPNP wont work.
This is the tutorial:
[http://wiki.xbmc.org/?title=MythTV](http://wiki.xbmc.org/?title=MythTV)

I changed all the backends addresses to the local IP (192.168.2.11) of its self instead of localhost.

Then I entered:
   $ mysql -u root -p
   mysql> grant all on mythconverg.* to mythtv@"192.168.1.%" identified by "mythtv";
   mysql> flush privileges;

Now I cant find my MythTV box via UPNP anymore.
What have I done?
I feel stupid :lol:

UPNP doesn't work when mythtv is set to work on localhost only. 

What exactly ARE your symptoms?

---

### Post by JamerTheProgrammer on 2012-09-13
> **nickrout said:**
> UPNP doesn't work when mythtv is set to work on localhost only. 

What exactly ARE your symptoms?

Oh right I see..
So just set both the Local Backend IP and the Master Backend IP to the machines LAN IP?
Nothing else appears to be broken. I can stream my recordings via MythWeb with an ASX file just fine. Its just the UPNP.
Thanks for replying.
EDIT:
Thanks!
Changed both and they are working perfect! :D

---

