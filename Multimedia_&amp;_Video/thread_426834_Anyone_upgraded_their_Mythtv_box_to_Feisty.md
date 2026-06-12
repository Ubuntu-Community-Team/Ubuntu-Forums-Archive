---
title: "Anyone upgraded their Mythtv box to Feisty?"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by ebike on 2007-04-28
Title says it all. 

Before I upgrade my Mythtv box I would like to know if anyone
has done so allready ... and what, if any, problems there were. 

In particluar I notice that the Mythtv downloads are called different names (looking at the Feisty Mythtv guide)
does this mean you have to un-install Mythtv and re-install the new packages?

Thanks.

---

### Post by supertdog on 2007-04-29
I can't speak to an "upgrade" but I did follow the feisty mythtv guide and the problem I have is that even though the backend is running, when I try and watch tv I get the error message :
```
Could not connect to the master backend server -- is it running?
```

However if I run the master backend and frontend as root then everything seems to work.  I would love to know how to solve this.

if I just run the master backend as root and the frontend as "mythtv" then it tires to watch tv, meaning I get no error about the backend being down but the frontend crashes each time and logs out the "mythtv" user.

---

### Post by ebike on 2007-05-01
Try running the backend from a console window so you can see what errors are reported, you could do that for the frontend in a seperate console as well. Report the errors here.

Now, anyone done the upgrade yet?

---

### Post by superm1 on 2007-05-02
> **ebike said:**
> Try running the backend from a console window so you can see what errors are reported, you could do that for the frontend in a seperate console as well. Report the errors here.

Now, anyone done the upgrade yet?
I have on all of my myth boxen.  I personally didn't have any breakage on anything related to myth.  I had some third party packages installed that messed up a few other things - but nothing major.

Also, a bit of an adjustment for all DVD playback - /dev/hda -> /dev/sda

---

### Post by williammanda on 2007-05-02
I added a 4th computer with feisty that just has mythfrontend. It works fine and the installation was easier than before, Superm1 and the team have done a very good job of making ubuntu a very user friendly distro for mythtv. The other three units all use dapper. I'm going to load mythbackend on the 4th unit this weekend and if all goes well I will be changing the other three units. I will do a clean install not an upgrade, I find this must easier for me.

---

### Post by ebike on 2007-05-13
Anyone done the "upgrade" yet, rather than a clean install?

---

