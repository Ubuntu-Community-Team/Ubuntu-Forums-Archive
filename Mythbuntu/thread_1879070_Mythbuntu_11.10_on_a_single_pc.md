---
title: "Mythbuntu 11.10 on a single pc"
date: 2011-11-10
forum: Mythbuntu
---

### Post by jerrylamos on 2011-11-10
O.K., so the hardware works, I can get tv from tv-viewer.

In a separate partition have a new updated Mythbuntu Oneiric Ocelot 11.10.

Ran thru the setups for front end and back end as best I can tell from the wiki sites.

Signal is coming from an HVR 1950 on Channel 3.  tv-viewer works.

Mythbuntu "front end" whatever that is says it cannot connect to the "backend" and can't find the ip address - why does it need an ip address if it is on the same pc??  I'm guessing 127.0.0.1 I saw that on the backend setup, how do I tell frontend to use it?

Should be a plain vanilla setup, everything on the same pc.

Any hints or pointers to guides?

Thanks, Jerry

---

### Post by nhtrader on 2011-11-11
I get what you're saying. You shouldn't need any network connections, but you do. 

Let's assume that you have a working system with myth installed and it is completely configured and operational. Then shut it down - power off. Now as a test, disconnect the ethernet cable from the PC and restart the PC. You will now get those annoying error messages despite the fact that the system was just working. Myth will automatically jump to the setup so that you can enter an IP address, despite the fact that it already has the correct IP address.

I too found this confusing, but in the end, myth requires a network connection - period. 

BTW, since you are new to this, did you activate the mythweb feature? This is an abbrev. for myth web server which means that your single PC contains a web server for mythTV. This feature is fantastic b/c it will allow you to access your media files (TV recording, Movie, Video, music, photos,etc.) from anywhere in the world (your friend's house, airport, your hotel room while on vacation, etc). Anywhere where you have an interrnet connection. 

The reason for mentioning this feature is b/c it requires a network connection. As you can see, your web server is searching for a connection and it needs one. So, I'm guessing that's why this error appears. Remember, your single PC MythTV configuration is by default able to communicate with you or anyone else in the world (if they're a user specified by you).

---

