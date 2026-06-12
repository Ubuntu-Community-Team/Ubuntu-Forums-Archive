---
title: "iSCSI"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by RRahl on 2010-06-21
Does anyone have any good articles on mounting a Ubuntu volume as an iSCSI share on a windows box?  Originally I was just going to use a SAMBA share but it turns out samba has issues with my lan security.  So I thought since all I really want to do is create the share on my backup server that an iSCSI device would do.
Been using the following article with limited success...
[http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target](http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target)

---

### Post by RRahl on 2010-06-22
ahhh come on no one?  Any help at all with iSCSI would be appreciated.  I am flat out stuck and the documentation is not very clear on what I can and cannot create as a Lun...

---

### Post by Bif Powell on 2010-07-28
Came across your post in a google search.

I have had luck just now with the 'client' part of this article:

[http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target](http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target)

I'm in 10.04 64-bit and although it seems strange, following the instructions worked for me to get access to my openfiler iscsi volumes.

The reason it's strange is it seems like the commands in some cases do not have enough parameters and 'just work', which might be due to configuration differences between that and the server in the above article.

Hope that helps - it's the only thing that's worked for me so far.

(edit: now I see that's the exact same article - sorry about that, so I guess I'm just one of those who says "works for me" and I hate those guys ;) )

---

