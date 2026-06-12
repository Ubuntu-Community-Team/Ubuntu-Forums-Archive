---
title: "surfing over ssh with the wrong IP address"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by fluxqubit on 2010-09-18
I only have three day experience with ubuntu, so there. 

I log with an ssh connection to my university network so that I could use our online scientific database subscription. I log in as :

ssh -X username@host
then password
and to open firefox, I simply type "firefox"

And it works, and I have a new firefox window. The thing is, the database still seems to think that I am using my home computer and not the university computer. Therefore, it does not allow me to use it (error in IP recognition). So my question is, how do I use the opened firefox window to surf the internet from the university computer's IP address?

Thanks,
flux

---

### Post by The Cog on 2010-09-18
If you also have firefox running locally, the remote firefox engine will make your local firefox open a new window instead. To be really sure, shut down your local firefox before starting the remote one. Or try starting the remote firefox with "firefox --no-remote".

---

