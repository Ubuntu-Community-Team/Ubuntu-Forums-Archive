---
title: "Can't log in to diskless frontend"
date: 2008-11-22
forum: Mythbuntu
---

### Post by dualboot on 2008-11-22
Hi All,
I have Mythbuntu 8.04.  Through the Mythbuntu setup screen I enabled diskless frontend, and built an image, and created a USB memory stick.  The fronted booted fine from it, and gets an IP address OK.  I can see lots of traffic between client and server.  After a few minutes it comes up to a nice looking login screen asking me for a username (though there is an option to click on a icon 'user' which takes me on to ask for a password.

I haven't changed from the default of user/password but it won't let me in any further.  I can't see a way to set or change the password either on the client or server.

---

### Post by dualboot on 2008-11-22
Update:  I can now get into the menu - I went into the control centre on the server's diskless page and set the 'log client in automatically', and re-built.  No it boots to the menu, but I need to make some setup changes - trying to run control centre on the client - it asks for a password, and 'password' doesn't work.

Any help greatly appreciated.

---

### Post by dualboot on 2008-11-22
All sorted.  Went into the console option in the 'diskless' page on the server - that gives you root access - from there did a passwd user and set a password.  After committing changes and re-booting the diskless frontend it accepted the new password.

Out of interest - any tips on how to write posts that illicit responses would be gratefully received.  Once every few months I post a query on the ubuntu forums.  I never ask until I've spent many hours trying myself. 

So far I have never had any replies - other questions come on the forums after mine whilst I hopefully wait for someone who has already solved my problem themselves to post, any they get answers, commiserations, troubleshooting tips - my posts get nothing.  (sorry I know I am whining now):(

Anyway I always go back and post if I sort it myself.  Just sanity checking I'm committing some terrible forum faux pas :confused:

---

### Post by dualboot on 2009-04-17
Ha ha - it was worth posting this in the end - after upgrading to 8.10 (amongst many other things it broke) the occasional fronted stopped - re-built the usb image, hit the same problem and somewhere in the back of my mind I though 'I'm sure I've done this before....'

---

### Post by AboveTheLogic on 2009-04-17
Here, I'm posting so that you at least don't feel completely alone :-\"

---

### Post by nickrout on 2009-04-17
> **dualboot said:**
> All sorted.  Went into the console option in the 'diskless' page on the server - that gives you root access - from there did a passwd user and set a password.  After committing changes and re-booting the diskless frontend it accepted the new password.

Out of interest - any tips on how to write posts that illicit responses would be gratefully received.  Once every few months I post a query on the ubuntu forums.  I never ask until I've spent many hours trying myself. 

So far I have never had any replies - other questions come on the forums after mine whilst I hopefully wait for someone who has already solved my problem themselves to post, any they get answers, commiserations, troubleshooting tips - my posts get nothing.  (sorry I know I am whining now):(

Anyway I always go back and post if I sort it myself.  Just sanity checking I'm committing some terrible forum faux pas :confused:

there are far more knowledgable users on the mythtv-user mailing list, if you don't get a reply here, try there.

Although the problem in this thread is pretty much a mythbuntu as opposed to general myth question so I don't know if the mailing list could have helped. Always worth a try though.

---

