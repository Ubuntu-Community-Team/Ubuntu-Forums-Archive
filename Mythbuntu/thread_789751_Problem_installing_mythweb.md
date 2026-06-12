---
title: "Problem installing mythweb"
date: 2008-05-10
forum: Mythbuntu
---

### Post by kreegor on 2008-05-10
Hey guys. I tried to install mythweb last night but got this error.

> Setting up mythweb (0.21.0+fixes16838-0ubuntu2) ...
Your apache2 configuration is broken, so we're not restarting it for you.

I removed apache2, apache2-common and apache2-utils and also mythweb and then tried to install mythweb via terminal using

```
sudo apt-get install mythweb
```

which gave me the above message. Can anyone help me out with this?

Thanks

---

### Post by nasha on 2008-05-11
How did you 'remove' apache? It says your apache is broken, which is because you attempted to remove it...
Install apache2 using apt... Why you would remove it in the first place puzzles me...

---

### Post by kreegor on 2008-05-11
I removed apache by typing sudo apt-get remove apache2.

The reason I removed it was because it said it was broken so I thought I would try removing it and installing it again to see if it worked. Installing mythweb installs apache2 as well

---

### Post by kreegor on 2008-05-11
Hmmm it seems to work now. I can get to [http://mythbox/mythweb](http://mythbox/mythweb) via the browser on my other machine but there is a mythweb.php file in the directory that when I open up in firefox I get this

[[IMG]http://img81.imageshack.us/img81/127/mythwebuv4.th.jpg[/IMG]](http://img81.imageshack.us/my.php?image=mythwebuv4.jpg)

What can I do to make it open up like a normal web page?

---

### Post by kreegor on 2008-05-11
I thought I would add some security using the instructions from [https://help.ubuntu.com/community/MythWeb]("https://help.ubuntu.com/community/MythWeb") and it just works now.

:)

---

