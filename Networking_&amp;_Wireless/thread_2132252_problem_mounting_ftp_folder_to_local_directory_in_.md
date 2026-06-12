---
title: "problem mounting ftp folder to local directory in Ubuntu"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by Xeovke on 2013-04-04
[Running on Ubuntu quantal on a Dell Optiflex 9010.] I'm slightly bluffed by a strange problem in mounting a ftp folder to a local directory. When I type

```
[FONT=arial]ftp://username@blabla.server.com:portnumber/folder/subfolder[/FONT]
```

in firefox, I do get access to the desired folder. Using the same link, in Kubuntu on another computer, I get to have access to the subfolder and copy/move files to/from there.

However, the current Ubuntu/Optiflex, I can't even use "connect to server..." then "ftp (with login)". Using curlftpfs returns errors such as "Error connecting to ftp: QUOT command failed with 501" or "Error connecting to ftp: Access denied: 530". However, using simply firefox, it's possible to access the subfolder... It's probably good to note that my username only allows me to access the subfolder and not the folder.

Any clues?

---

### Post by Xeovke on 2013-04-04
oh sorry that was easy... simply added 

```
ftp://username@blabla.server.com:portnumber/folder/subfolder
```

[FONT=arial]in the .gtk-bookmarks file of my home folder and now it appears automatically on the left under "bookmarks" of Nautilus. Not quite what I wanted but good enough.
[/FONT]

---

