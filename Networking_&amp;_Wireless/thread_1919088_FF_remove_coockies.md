---
title: "FF remove coockies"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by ahso4271 on 2012-02-02
Hi
even after setting in FF delete cockies at shutdown they are still present. 

How to get rid of those. Any shell script etc.?
Thanks

---

### Post by Linux Dutchman on 2012-02-02
You can try a tool like Bleachbit. But be carefull with this tool. It can remove a lot, even things you don't want to get removed. But it will clean your system really good!
 
But are they the "normal" cookies or flash cookies?
You could try this too: [http://www.ihaveapc.com/2011/09/how-to-delete-flash-cookies-from-firefox-in-linux-mint-ubuntu/](http://www.ihaveapc.com/2011/09/how-to-delete-flash-cookies-from-firefox-in-linux-mint-ubuntu/)
 
and:
[http://www.ubuntugeek.com/how-to-remove-temporary-information-such-as-web-page-cookies-browser-history-or-the-list-of-recently-opened-documents-in-ubuntu-10-10-system-maverick.html](http://www.ubuntugeek.com/how-to-remove-temporary-information-such-as-web-page-cookies-browser-history-or-the-list-of-recently-opened-documents-in-ubuntu-10-10-system-maverick.html)
 
and:
[http://ubuntuforums.org/showthread.php?t=1874539](http://ubuntuforums.org/showthread.php?t=1874539), this is a closed and solved thread on this forum, might be very usefull to you.
 
Good luck!

---

### Post by ahso4271 on 2012-02-03
Yes i already use BetterPrivacy but I am looking for a way to remove simple cockies at every ff closing.(without the ff menu)
I was thinking of a shell script but cannot localize those cockies.

---

### Post by Lampi on 2012-02-03
- Check your FF privacy menu
- change it to "user defined" settings
- you'll notice below the third-party cookies one more option "keep until" - change this to "I close firefox"

you're done!

There's firefox addon Cookie-Culler to give you a quick access button to the cookie manager ... useful to manage those you are willing to keep.

---

### Post by ahso4271 on 2012-02-03
yes sure but this doesn't work. they're still present after restarting FF

---

### Post by Lampi on 2012-02-03
only if you restore the last session, ahso4271

... or if you keep them with a rule in the cookie manager

---

### Post by ahso4271 on 2012-02-04
ahh now they are gone...many thanks.

---

