---
title: "AutoBuild does not work on ubuntu 10.04"
date: 2010-07-21
forum: Mythbuntu
---

### Post by dibuntux on 2010-07-21
AutoBuild works ok on my master backend/frontend which is a mythbuntu 10.04 AMD64 PC, with 0.23 PPA. On the latest upgrade, my other frontend with ubuntu 10.04 AMD64 stopped connecting, saying the network protocol was different (0.56).
I tried to activate the Autobuild with 0.23 & PPA on this machine, but sw sources are wrong and I get this:

Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/binary-amd64/Packages.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/source/Sources.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/source/Sources.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I tried to modify the http address, but could not find the right syntax.

Any help? TIA

---

### Post by dibuntux on 2010-07-21
Ok, I solved this by copying manually info on sw sources from the master backend; still did not understand why the autobuild install proc from the mythbuntu site worked for mythbuntu and not for ubuntu...

hope it can help others

Dave

---

### Post by tgm4883 on 2010-07-21
That is odd, it should work on either. How did the sources differ?

---

### Post by dibuntux on 2010-07-22
mmmh, I copied the right ones over... if I recall well, in URL it was just [http://ppa.launchpad.net/mythbuntu/0.23](http://ppa.launchpad.net/mythbuntu/0.23) instead of
[http://ppa.launchpad.net/mythbuntu/0.23/ubuntu](http://ppa.launchpad.net/mythbuntu/0.23/ubuntu)

and in Distribution it was ubuntu instead of lucid and in Components lucid main instead of main...

a mix of this: it just came out of the standard install proc, I did not mess it up, in the beginning, then I tried giving it the right url, but did not just work, and finally I copied the ones on the master.

Hope it helps.
Dave

---

### Post by dibuntux on 2010-10-07
Just updated my Ubuntu 10.04 AMD64 machine, noticed there was an update on Myth Updater and AGAIN it scrambled the sources in update manager:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/binary-amd64/Packages.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/source/Sources.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/source/Sources.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

This was of july; in october still this is scrambled? I cannot be the only one with this...

---

### Post by tgm4883 on 2010-10-07
> **dibuntux said:**
> Just updated my Ubuntu 10.04 AMD64 machine, noticed there was an update on Myth Updater and AGAIN it scrambled the sources in update manager:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/binary-amd64/Packages.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/source/Sources.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/lucid/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/source/Sources.gz](http://ppa.launchpad.net/mythbuntu/0.23/dists/0.23,/ubuntu/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

This was of july; in october still this is scrambled? I cannot be the only one with this...

You actually seem to be. Can you attach your /etc/apt/sources.list.d/mythbuntu-repos.list and also /etc/default/mythbuntu-repos

Also, what language is your system set to?

---

### Post by dibuntux on 2010-10-07
Language is set to english

/etc/apt/sources.list.d/mythbuntu-repos.list is :
deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/0.23](http://ppa.launchpad.net/mythbuntu/0.23) 0.23,/ubuntu lucid main
deb-src [http://ppa.launchpad.net/mythbuntu/0.23](http://ppa.launchpad.net/mythbuntu/0.23) 0.23,/ubuntu lucid main

/etc/default/mythbuntu-repos :


[cfg]
activateweekly = True
weeklylocation = PPA
weeklyrepo = 0.23 0.23,
testingppa = False

as I stated in previous posts, /etc/apt/sources.list.d/mythbuntu-repos.list is wrong and I can manually set it ok, then at the next Ubuntu 10.04 upgrade it will be screwed again...

Any Ideas on how to solve it? TIA

---

### Post by tgm4883 on 2010-10-07
> **dibuntux said:**
> Language is set to english

/etc/apt/sources.list.d/mythbuntu-repos.list is :
deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/0.23](http://ppa.launchpad.net/mythbuntu/0.23) 0.23,/ubuntu lucid main
deb-src [http://ppa.launchpad.net/mythbuntu/0.23](http://ppa.launchpad.net/mythbuntu/0.23) 0.23,/ubuntu lucid main

/etc/default/mythbuntu-repos :


[cfg]
activateweekly = True
weeklylocation = PPA
weeklyrepo = 0.23 0.23,
testingppa = False

as I stated in previous posts, /etc/apt/sources.list.d/mythbuntu-repos.list is wrong and I can manually set it ok, then at the next Ubuntu 10.04 upgrade it will be screwed again...

Any Ideas on how to solve it? TIA

Well your /etc/default/mythbuntu-repos file is incorrect. Specifically this line

```
weeklyrepo = 0.23 0.23,
```

That should read whatever version you selected. 

Could you edit that file so the line looks like this

```
weeklyrepo = 0.23
```

then run

```
dpkg-reconfigure mythbuntu-repos
```

and select whatever version you had selected before. After that look at /etc/apt/sources.list.d/mythbuntu-repos.list and tell me if it is correct.


:EDIT:

I want to add that the mythbuntu-repos.list is completely rewritten each time you reconfigure mythbuntu-repos, and it pulls the info from /etc/default/mythbuntu-repos which is why I am troubleshooting that part

---

### Post by dibuntux on 2010-10-08
There it is Sir, thank you so much!

Now /etc/apt/sources.list.d/mythbuntu-repos.list is :
deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/0.23/ubuntu](http://ppa.launchpad.net/mythbuntu/0.23/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/mythbuntu/0.23/ubuntu](http://ppa.launchpad.net/mythbuntu/0.23/ubuntu) lucid main

as it should be and Update Manager works OK

This after correcting /etc/default/mythbuntu-repos as per your suggestions.

But it was set wrong from the standard Mythbuntu autobuild configuration... if this can be of any help  to devs.

My best to all

---

### Post by tgm4883 on 2010-10-08
> **dibuntux said:**
> There it is Sir, thank you so much!

Now /etc/apt/sources.list.d/mythbuntu-repos.list is :
deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/0.23/ubuntu](http://ppa.launchpad.net/mythbuntu/0.23/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/mythbuntu/0.23/ubuntu](http://ppa.launchpad.net/mythbuntu/0.23/ubuntu) lucid main

as it should be and Update Manager works OK

This after correcting /etc/default/mythbuntu-repos as per your suggestions.

But it was set wrong from the standard Mythbuntu autobuild configuration... if this can be of any help  to devs.

My best to all


It may have happened when we tried to have mythbuntu-repos figure out which versions to provide on it's own. Possibly something else. Either case it's fixed now and shouldn't cause issues for you in the future.

---

