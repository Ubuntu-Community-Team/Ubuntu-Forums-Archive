---
title: "git and gitosis problems"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by sa125 on 2009-03-18
hi - 

I'm new to git, and I'm trying to push a new project to our office server but ran into problems with ssh and git protocols: 
_[http://gist.github.com/80988](http://gist.github.com/80988)_

I also tried setting up a gitosis server on that server _[with this tutorial](http://scie.nti.st/2007/11/14/hosting-git-repositories-the-easy-and-secure-way)_, and everything went great until I tried to push changes back to the server. 

I was able to clone the gitosis-admin.git repo, but trying to push back changes gave me this error:
```

error: unable to create temporary sha1 filename ./objects/26: Permission denied
fatal: failed to write object
error: unpack failed: unpacker exited with error code
To git@gitserver:gitosis-admin.git
! [remote rejected] master -> master (n/a (unpacker error))
error:  failed to push some refs to 'git@gitserver:gitosis-admin.git'
```

has anyone seen any of these before, or could propose a solution? I need either one to work. 

thanks!

---

### Post by digioi on 2010-03-31
I know this is a year too late but ... I just had someone ask me the same question and I found this thread and realized his problem may have to do with his permissions on his folder.

---

