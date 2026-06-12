---
title: "Add repository?"
date: 2012-02-23
forum: Mythbuntu
---

### Post by raptorjr on 2012-02-23
I'm running Mythbuntu 10.10 and dont want to update everything. Too much that breaks.
But i do need a newer version of libass-dev than the one that is available in 10.10. Is it possible to add a newer Mythbuntu repository to be able to apt-get a newer libbass-dev or will it break things? What repository should i add then?

/Stefan

---

### Post by winh8r on 2012-02-23
The versions available are listed here:

[https://launchpad.net/ubuntu/+source/libass]("https://launchpad.net/ubuntu/+source/libass")

I would have a long think about it though, you will probably get into problems if you start mixing different packages from older and newer releases.

Developers usually recommend keeping everything up to date in order to get the best results and not just one or two parts of an application.

Sorry if this does not fully answer your question, but I would not like to tell you something only for you to find out that it breaks your setup!!!

---

### Post by uteck on 2012-02-25
You could add a source repo and compile a new version using "apt-get build-dep libbass-dev " but even that may pull in a bunch of dependencies and end up upgrading some of your system.  

If you are worried about breaking your system, you can use something like clonezilla and make a backup of the drive and restore it if things break.  
The first time I upgraded Ubuntu versions I did this and it was a good thing since I had not rebooted the system for a few months and combined with the upgrade, the file system got corrupted.  I was able restore it all with clonezilla and was back up and running in a few minuets.

Now I reboot the system first, then run the upgrade and have not had a problem since that first time.

---

