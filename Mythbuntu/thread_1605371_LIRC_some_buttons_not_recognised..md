---
title: "LIRC some buttons not recognised."
date: 2010-10-25
forum: Mythbuntu
---

### Post by tonycollinet on 2010-10-25
I've upgraded from 9.04 (I think) to 10.10

TV Card is NovaT 500 and I'm using its remote. Previously I setup LIRC according to the how to here:
[http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote](http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote)
And everything worked fine.

However, with 10.10 the remote was recognised "out of the box" but with some buttons ignored (EG OK/Enter)

I've tried setting the files up as described in the howto above, but with absolutely no change in behaviour. (Except that the 10-local.rules file stopped everything working, so I deleted it again)

The Ok/enter key generates no response in IRW


Is there a difference in how the setup files are used for LIRC in 10.10? Any suggestions how to get the missing buttons working.

Thanks.


EDIT: As far as I can tell, the only buttons working (Also in irw) are the direction buttons, and the number buttons. Nothing else gives any response.

EDIT2: - fixed - I did need the rules file. Not sure what I did wrong the first time. Just went through the whole thing more methodically.

---

