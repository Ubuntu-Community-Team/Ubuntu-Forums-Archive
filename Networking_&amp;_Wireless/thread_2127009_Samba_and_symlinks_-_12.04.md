---
title: "Samba and symlinks - 12.04"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by AndyGGG on 2013-03-18
Hi,

I've just been reading old forum posts on how to get symlinks  working with samba. Found that I needed to edit the /etc/smb.conf file  and add the following entries into the Global section:

follow symlinks = yes
wide links = yes
unix extensions = no

And yes, this did allow my windows box to access the symlink directories.

I  also read that there are security issues with enabling symlinks.  Another post recommended moving the the first two entries to the  specific directory share entries, which I did and the symlinks still  worked.

The problem I have found is that if I later use the  system-config-samba gui application to make any changes then it comments  out the line 'follow symlinks = yes' with a semi colon. The application  does this even if it does not need to edit the smb.conf file for any  other actions, such as when setting a samba user's password. Thus my  symlinks become instantly unavailable again, requiring me to sudo  uncomment those entries and restart the smbd.

Is there any way I can prevent this from happening?

---

### Post by AndyGGG on 2013-03-19
It seems I got this slightly wrong:

for me it was the 'wide links = yes' option that was requires as my symlinks were linking outside of the samba share directory.

In contradiction to the documentation at the head of the smb.conf file, when commented out by a semicolon the option entry means that this is the default value. The manual verified that the default is 'follow symlinks = yes'. However 'wide links' is 'no', so I needed that.

Andy

---

