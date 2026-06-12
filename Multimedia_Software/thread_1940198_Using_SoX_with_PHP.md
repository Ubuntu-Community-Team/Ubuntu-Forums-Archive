---
title: "Using SoX with PHP"
date: 2012-03-13
forum: Multimedia Software
---

### Post by TPrime on 2012-03-13
Hello,

I'm currently trying to create a php script that execute a SoX command. I've had no success so far. So I've dumbed down the procedure to simply trying to play a music file with the 'play' command in order to track down the problem like so:

```

exec("/usr/bin/play /path/to/file.mp3");

```

I had thought that it may be a PATH problem, which is why I have the full path to 'play'. Also figured it may be a permission issue, but I gave the apache user (www-data) full ownership of the file and the path to it.

I'm using PHP5, apache2, and SoX with mp3 support. Any suggestions?

---

