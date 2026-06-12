---
title: "FTP via ubuntu VS FTP via XP"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by Aune on 2007-02-18
I go to terminal, type "FTP", then connecting to the server, then use the "PUT" command to tranfer the file to my XBOX. But then the xbox can't play the movie... But if I copy the exact same movie via windows XP, and using cuteftp.. then the xbox plays the movie just find..

Can someone please explain to me why, or what i'm doing wrong ?

---

### Post by thingy on 2007-02-18
put the ftp program in binary transfer mode before executing your PUT command.

e.g.

~/> ftp my.xbox.com
>bin
>put my-file.avi

etc.

---

