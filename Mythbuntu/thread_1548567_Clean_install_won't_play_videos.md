---
title: "Clean install won't play videos"
date: 2010-08-08
forum: Mythbuntu
---

### Post by miststlkr on 2010-08-08
When I try to play a video I get the "Please Wait..." screen then either get dropped back to mythvideo or the frontend crashes out and refuses to reload until I reboot [[or, presumably do something smarter if i knerw any better..]] I posted a one-session log for both front and back ends on pastebin and it looks like the two [on the same machine] are not able to communicate.   Suggestions?  I noticed that at least some of the videos have been changed to the mysql group somehow, not sure if that is at all relevant but thought I'd mention it.

[http://mythbuntu.pastebin.com/D5VbUU1t](http://mythbuntu.pastebin.com/D5VbUU1t)


Thanks for any suggestions.

---

### Post by LowSky on 2010-08-09
have you installed the codecs?

open up Mythbuntu control panel and you can easily check them on.

---

### Post by miststlkr on 2010-08-09
I can have a look when I get home, but the files play fine in VLC so I am not sure that is the issue.

---

### Post by nickrout on 2010-08-09
your frontend is trying to play from 127.0.0.1 whereas your backend seems to be starting on 192.168.1.26 so something is screwy.

No extra codecs should be required.

---

### Post by LowSky on 2010-08-09
sorry my fault, I didn't read the whole post. 

It is funny that the frontend finds the file but then can not play it or crashes... hhmmmm

---

### Post by miststlkr on 2010-08-09
NickRout -- That was the only thing that stood out to me also, and I was going to tinker with that next.  I'm not sure that is the issue as 127.* is the localhost loop and the 196.* is that machine's local /8 address on the LAN, so I was trying other things first.  I'll have a tinker later.



LowSky -- No worries, I don't think I mentioned that the files opened in other programs, which is a somewhat relevant thing to leave out.   sorry.



To add another oddity to the problem, when I rebooted last night and tried, the first video I played worked fine, then nothing after that.  Now I'm completely lost.  I'll mess with the backend address I suppose and see what happens.

[edit=add]erm... naturally, that isn't a /8 block... but the rest still stands :-P  [/edit]


[edit2=add]   I didn't have too much time to kill on it last night.  I went into the frontend settings and changed the 127.* to the 196.* IP address but the frontend froze when leaving the settings screen.  I wasn't in the best mood to begin with so I took it as an omen and let it be for the night.  I likely won't have time to get more into it until this weekend.   Thanks for the quick suggestions, I'm sorry I'll be so slow getting back to you about the results.   Cheers. [/edit]

---

### Post by miststlkr on 2010-08-17
For what it is worth to others, I finally got/made some time to put into this tonight and got this sorted out just a few minutes ago.  I went into the backend controls, then to "general" and changed the fields for both the local backend IP and the master backend ip addresses to "localhost".  The local IP had been the 127.* address and the master had been the 196.* addresses, both are now "localhost" rather than an actual I and it works fine.  I don't know if this is a "correct" fix to the issue, but it makes the system work so I call it a win.  Perhaps  changing just the master backend IP to 127.* would have been a more appropriate answer?

Thanks to those who offered help, and I hope this post saves someone else some aggravation.

Cheers!

---

