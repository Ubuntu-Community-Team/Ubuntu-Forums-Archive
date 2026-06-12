---
title: "Problems following the sticky howto jaunty intel guide"
date: 2009-06-12
forum: Multimedia Software
---

### Post by joem1 on 2009-06-12
Hello,
I am a newbe, so I apologize that these are probably easy questions.  I just installed 9.04, and have been having trouble getting my flash video to work in full screen mode.  So, i have been trying to use the advice in the following two threads, but it has not worked:

[HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")

I am able to follow most of the recommendations in both threads, but am having particular problems with the second.  the first problem is that when i try to edit my xorg.conf file to conform to the one suggested in the howto, i get the following error:

"Could not save the file /etc/X11/xorg.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

How do i fix this?  I have all the administrator passwords and such, so i don't know what this is talking about.  it's probably an easy fix.

The second problem i am having, which may be related, is that further down in the Howto, when i try to add the the [X Updates PPA]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") to your sources.list, I am unable to get the authorization key to import.  I do everything suggested in the tutorial, but it simply doesn't import.  and then, when i try to manually import it, i get the following error:

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5"

I have read many threads on these subjects, but have not seen any that address these concerns directly.  Please help.

thanks,
joe

---

### Post by nmjcman101 on 2009-06-12
To fix your first issue, you need to edit it in root mode.  Go to a terminal and put in:
```

sudo gedit /etc/X11/xorg.conf
```

You can substitute gedit with your favorite text editor.

---

