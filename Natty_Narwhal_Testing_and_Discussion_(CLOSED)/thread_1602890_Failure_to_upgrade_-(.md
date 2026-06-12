---
title: "Failure to upgrade :-("
date: 2010-10-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-10-22
I am getting an error while trying to upgrade. Am I missing something obvious? Thanks.

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by AoSteve on 2010-10-22
Try a terminal  ...


```
 sudo apt-get update 
```

See if that helps out.    It would seem that your sources.list file has some broken repo's in it.

---

### Post by Quackers on 2010-10-22
Thanks, but that's when I get that error message. TBH I can't see the particular repo mentioned in the sources list. That wouldn't explain a 404 error would it?

---

### Post by cariboo on 2010-10-22
I have the extras repository set to maverick, as I was getting the same error when it was set to natty.

You can change ti by opening System->Administration->Synaptic Package Manager->Settings->Repositories->Other Software. Highlight Independent, then click the edit button and change the distribution form natty to maverick.

---

### Post by Quackers on 2010-10-22
Thanks cariboo907 I might not have to try that. From nowhere I've just got 161MB of updates to run and one of the early ones is regarding the repo that was giving the 404 error.  It does seem that that part of the site is down though. We'll see :-) (If my system reboots ok :-)

---

### Post by Quackers on 2010-10-22
Oh dear. It restarted ok but things are just the same.
I tried what you suggested Mr Cariboo but as soon as I select Repo's a pop-up appears saying the repos have changed and I need to click on Reload. I click on reload and a pop-up appears giving the 404 error again.
And now the Software Sources won't start and the Update Manager just loops with the same 404 error whenever I click on settings. And it offersw me a partial upgrade - which I refuse.
Hmmmm.

---

### Post by Quackers on 2010-10-22
Thank you Mr Cariboo, after following your advice and after following Vanishing's additions I am able to run the upgrade. It's churning as we speak :-)
Let the fireworks begin :-)
I've got this install on a seperate drive - for playing purposes :-)

---

### Post by Quackers on 2010-10-22
:-):-):-)
natty64@natty64-laptop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"

Thank you

---

### Post by Quackers on 2010-10-22
I can't mark this thread as solved - no option in thread tools :-(

---

### Post by cariboo on 2010-10-22
> **Quackers said:**
> I can't mark this thread as solved - no option in thread tools :-(

I can't mark it solved either, I'll get one of the admins to have a look at it.

---

### Post by Quackers on 2010-10-22
Thanks again :-)

---

### Post by cariboo on 2010-10-22
The solved feature is fixed now.

---

