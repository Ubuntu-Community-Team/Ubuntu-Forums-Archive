---
title: "[SOLVED] SSH shell for user other than admin too basic (no autocomplete, etc)"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by jonathanmotes on 2008-12-03
I created a new user on my server (running 8.04 desktop edition at the moment), then SSH'ed in as that user. Much to my surprise, I did not have most of the functionality that the main user has. I don't have color coding or autocomplete. My shell looks extremely basic:

[[IMG]http://farm4.static.flickr.com/3069/3081263792_2e0c80b56f_m.jpg[/IMG]]("http://www.flickr.com/photos/9547627@N06/3081263792/")

I created the user like this:
useradd -m username
passwd username

Maybe I have to pass more parameters when creating the user.
Anyone have any ideas?

---

### Post by jonathanmotes on 2008-12-04
Anyone know if this is just an issue with the desktop edition? I'm hoping the server edition doesn't have this problem!

---

### Post by jonathanmotes on 2008-12-04
OK, a friend gave me the solution. I was using dash instead of bash. 

He used this command to change it to bash:

```
sudo ln -sfv bash /bin/sh
```

To see what shell you are using:
```
ls -l /bin/sh
```

---

