---
title: "Serious memory leak in Unity 2d - Warning"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by fabricator4 on 2011-04-03
Everyone running Unity 2D should check out this bug on launchpad - [Bug #723956 ]("https://bugs.launchpad.net/unity-2d/+bug/723956")

See down the bottom where I describe how to recreate it simply by searching for an application.

If you've been wondering where your memory has been going, this is probably it.  I haven't checked for a similar problem in Unity 3d yet.

Chris

---

### Post by fabricator4 on 2011-04-03
For now, the quick workaround appears to be to select Unit-2d-places in system monitor under "processes" and just end the process. This seems to release the memory back to the pool.

2d-places will be opened again as soon as you select "applications" and the process starts all over again.  My objective until this gets fixed will be to not use the applications finder if I can possible help it. I may finish up with a lot on the launcher. ](*,)

Chris.

---

### Post by kansasnoob on 2011-04-03
I haven't had much time to play the past week but I'm curious if you're using unity-2d from the repos, or the ppa version:

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

I should note here that I've tried both and find the ppa version to run much better but, if you try the ppa version and then want to revert, the process is not as straight forward as just running ppa-purge. Be sure to make a note of what's upgraded and/or installed in /var/log/apt/history.log so you know how to revert to the repo version :)

I doubt I'll have much time to play the next week or two :(

---

### Post by fabricator4 on 2011-04-03
> **kansasnoob said:**
> I haven't had much time to play the past week but I'm curious if you're using unity-2d from the repos, or the ppa version:


I installed from the repository.  My feeling at the moment is that I'll just live with it until a fix comes through, or until the release of Natty.  I also will not have much time to fiddle with this, so hopefully the fix will be sooner rather than later.

For the record this problem is limited to Unity 2D, in particular the unity-2D-places module.  Unity 3D plays nicely with memory.

Chris

---

### Post by lucazade on 2011-04-03
I'm not able to reproduce this issue here (natty - unity2d ppa)
unity-2d-places is always around 30mb, no visible leaks here. :confused:

---

### Post by fabricator4 on 2011-04-03
> **lucazade said:**
> I'm not able to reproduce this issue here (natty - unity2d ppa)
unity-2d-places is always around 30mb, no visible leaks here. :confused:

Thanks, that would be important information!  I've added it to the comments on the bug report on Launchpad; hopefully it means something to somebody.

Obviously there's something different in the build of the PPA version as compared to the version that's in the repository.

Chris

---

