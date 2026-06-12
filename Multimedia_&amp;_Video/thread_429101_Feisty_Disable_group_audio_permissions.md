---
title: "Feisty: Disable group audio permissions?"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Jaguar0616 on 2007-04-30
Hello all,

I'm using a Fedora server and NIS to share logins with clients running Ubuntu (Feisty).

Now, Feisty only allows members of group "audio" to access the sound card . . . BUT . . . Fedora doesn't have a group audio so none of the shared accounts are able to play sound.

I'd like to change the permissions on my Feisty servers so that any user can access the sound card regardless of group membership. How can I do that?

Thank you!!

---

### Post by Jaguar0616 on 2007-05-01
Found my own answer. The /etc/udev/rules.d/40-permissions.rules
file has two lines:

SUBSYSTEM=="sound",                   GROUP="audio"
KERNEL=="rtc",                               GROUP="audio"

Replacing "audio" with "users" allows members of "users" to access the sound card. Happily, Fedora and Ubuntu use the same group number for "users".

---

