---
title: "OS X really ticks me off sometimes"
date: 2008-11-19
forum: Mac OSX
---

### Post by decoherence on 2008-11-19
(rant warning)

I have never, ever seen a computer behave as randomly as OS X computers do.

So our OS X Server goes down... well, just the AFP (file server) part of it does. I have no idea why because nothing was logged. I restart AFP, which comes back up just fine, and some users are immediately able to work with their files again. Well, some of their files. Disk images won't mount and the error message leads to you believe it is corrupted (whoo boy, the users were happy when that came up!)

Trying to copy a file from the network to the local disk gives you a type 41 error... what is this, System 7? Write a damned error message!

Other users can limp along... things seem to work normally except they get the pinwheel/beachball of doom every five seconds. Is anything being logged to either the client or the server while this denial of service is happening? No, of course not!

How did I solve it? Just reboot everything. Oh, that's @#$@#$%^ing great! I still have no idea why it happened, so I guess I can just wait for it to happen again.

I knew I should've switched to a Linux server for this year... OS X Server has so much potential, in terms of a neat (though occasionally too cute) interface for managing services. Too bad about the rest of it.

---

### Post by handy on 2008-11-19
I have had no personal experience with Mac OS X Server, though from what I have read it is not what Apple do best.

---

### Post by 3rdalbum on 2008-11-22
I remember when I went to university, the network was running off OS X Server. It kept falling over and giving the clients the spinning pinwheel of death.

If I was really generous, I'd say it was because the network administrator hadn't bothered to check the settings of Adobe Premiere on the clients... they were all set to use the network share as scratch space! Maybe if a whole video editing class all started rendering their projects at the same time, it would bring down the server?

But to be blunt, Apple treats its server product as a bit of a toy, and I think a real Unix or Linux (or Windows Server) would have coped much better.

---

