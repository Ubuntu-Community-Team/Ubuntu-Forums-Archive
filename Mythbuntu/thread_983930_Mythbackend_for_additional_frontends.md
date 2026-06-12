---
title: "Mythbackend for additional frontends"
date: 2008-11-16
forum: Mythbuntu
---

### Post by extasy on 2008-11-16
When I'm trying to connect a frontend to my backend I get the message that no sql is pressent. First I get a message that no Upnp backend is pressent.

It must be some problem with my initial installation, is it any way I can reconfigure the backend settings? I remembered it was a question if I would be using additional frontends. I'm quite sure I answered yes on that question but the way things are turning out I can't be to sure.

Henrik

---

### Post by ian dobson on 2008-11-16
Hi,

1) Check that the ip address of the sql server on the frontend in mysql.txt is set correctly.

2) Check that mysql is configured to allow conections from the network. This is configured in the my.cnf file, bind option.

Regards
Ian Dobson

---

### Post by extasy on 2008-11-16
> **ian dobson said:**
> Hi,

1) Check that the ip address of the sql server on the frontend in mysql.txt is set correctly.

2) Check that mysql is configured to allow conections from the network. This is configured in the my.cnf file, bind option.

Regards
Ian Dobson

1) is done,

2) Is not done, this is what my my.cnf file states:
bind-address            = 127.0.0.1

what should this be changed to so it accept connections?

---

### Post by extasy on 2008-11-16
Case is solved, the only problem was that backends address was 127.0.0.1 instead of the real IP. After this change all worked.

---

### Post by ian dobson on 2008-11-16
OK good, please mark thread as solved.

Regards
Ian Dobson

---

