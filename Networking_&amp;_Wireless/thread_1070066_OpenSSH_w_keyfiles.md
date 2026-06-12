---
title: "OpenSSH w/ keyfiles"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by Starship on 2009-02-14
Dear community,

I have been researching this question for quite a while now but couldn't find any authoritative answer to it...

If I set up an OpenSSH server and wish to authorise users using keyfiles, how is an 'unknown' user -- only identified by his keyfile -- mapped to the proper local user? I understood that the user loggin in is mapped to the local user in whose /.ssh directory the corresponding pub key is located. Is that definitely correct? 

Just to ultimately clarify this issue for me: Would it technically be possible to store a user's pub key somewhere else than in his .ssh directory and still identify that user when logging in? What would happen in the -- admittedly -- highly unlikely case that two users have the same pub key file?

Thanks for any answers,
cheers,
Starship

---

### Post by Dr Small on 2009-02-14
The public keys of the users are stored in their ~/.ssh/ directories. There can not be 2 public keys that are identical.

---

