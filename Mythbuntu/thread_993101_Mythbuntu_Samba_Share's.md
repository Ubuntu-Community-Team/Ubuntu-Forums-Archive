---
title: "Mythbuntu Samba Share's"
date: 2008-11-25
forum: Mythbuntu
---

### Post by DemonBob on 2008-11-25
How would i allow full guest access to the music share so that i can delete files from my vista box? I can add, and modify but not deleted.

---

### Post by ian dobson on 2008-11-25
Hi,

Maybe something like this:-

```

-----------------------------------------------------------
# A publicly accessible directory, read/write to all users. Note that
# all files created in the directory by users will be owned by the 
# default user, so any user with access can delete any other user's 
# files. Obviously this directory must be writable by the default user. 
# Another user could of course be specified, in which case all files 
# would be owned by that user instead.

[public]
   path = /usr/somewhere/else/public
   public = yes
   only guest = yes
   writable = yes
   printable = no

```

I've not tested it myself, but it looks about right to me.

Regards
Ian DObson

---

