---
title: "Nicotine-Plus Crashing"
date: 2010-03-29
forum: Multimedia Software
---

### Post by cybrsaylr on 2010-03-29
Nicotine-Plus overall works great. 
The only problem seems to be when you do a search for a popular artist like say the Beatles, I get so many search result selections that Nicotine-Plus seems to overload and crashes and shuts down. It there a way to keep this from happening?

---

### Post by cybrsaylr on 2010-03-30
Anyone having the same problems?

---

### Post by cybrsaylr on 2010-03-31
Bump.

Nobody uses Nicotine anymore?

---

### Post by medienstudent on 2010-04-09
i've got the same problem but no solution ....

---

### Post by cybrsaylr on 2010-04-10
To get around this bug I tailor my searches. 
If you just do a search for say, Elvis, Beatles, Elton John etc you get so many search results Nicotine crashes. However if you looks for a specific song or album by these popular artists, you get less results and Nicotine doesn't crash and works pretty well. 

Just wish they would fix this bug.

---

### Post by dogbin on 2010-04-22
I have a problem where I go to launch nicotine plus. I open N+ in the applications -> Internet menu. The mouse icon changes to show the computers thinking and then nothing happened. I read somewhere that you can delete all the .db files in the download directory and I did that and I had the same problem,. I also tried uninstalling and reinstalling it still nothing.

Help would be appreciated

---

### Post by cheeseburgerpizza on 2010-05-03
I was having the same problem and ended up getting the tarball version from [http://www.nicotine-plus.org/](http://www.nicotine-plus.org/), 1.2.15 (3 revisions above the Ubuntu version).  Everything works fine now, and I looks like there are some good new features too.  I wonder why the new version isn't in the Lucid repository? 

Anyway, here are some instructions on the install if anyone wants them.  

Download the archive and extract:
```
wget http://129.125.101.92/nicotine+/nicotine+-1.2.15.tar.bz2
tar jxvf nicotine+-1.2.15.tar.bz2
cd nicotine+-1.2.15/
```

Uninstall the Ubuntu nicotine package to prevent conflicts.  There might be a way to have both versions at once, but I got errors when the install tried to overwrite files from the old version.
```
 sudo aptitude remove nicotine 
```
Now you have the option of using checkinstall to make a .deb package that can be removed later, which I recommend to keep your system sane.  

to get it, ```
sudo aptitude install checkinstall
```

Assuming you're still in the nicotine source directory, 
```
sudo checkinstall python setup.py install
```

It will ask you to enter a description for the package etc, at this point one might want to look at the ubuntu nicotine package and try to set this package up to look like a new version of that, but I just installed it the way that checkinstall created it by default.

without checkinstall, ```
 sudo python setup.py install 
``` should install it somewhere, or you can also just run nicotine.py from the directory you extracted it into.

---

### Post by cheeseburgerpizza on 2010-05-03
It also looks like someone has the latest version up in a PPA for Ubuntu. I haven't tried it but that might be a good way to get the new version while staying Ubuntu about installed software. [https://launchpad.net/~lopeztobal/+archive/maths](https://launchpad.net/~lopeztobal/+archive/maths)

---

### Post by Podex on 2011-03-16
> **cheeseburgerpizza said:**
> I was having the same problem and ended up getting the tarball version from [http://www.nicotine-plus.org/](http://www.nicotine-plus.org/), 1.2.15 (3 revisions above the Ubuntu version).  Everything works fine now, and I looks like there are some good new features too.  I wonder why the new version isn't in the Lucid repository? 

Version 1.2.16 has been released in October 2010 but it is still not included in the repository of Natty. This is bad since this version might fix some peoples problems. I made a bug report but nobody has reacted on it: [https://bugs.launchpad.net/ubuntu/+source/nicotine/+bug/696819](https://bugs.launchpad.net/ubuntu/+source/nicotine/+bug/696819)

---

### Post by cybrsaylr on 2012-10-18
Having problems with version 1.2.16 with Precise. It loads slow, balky and just doesn't run smooth like verson 1.2.14 did with Natty. Got 1.2.16 from Synaptic.

Nicotine 1.2.14 ran great with Natty before upgrading to Precise.
Would going back to version 1.2.14 help?
And if so, how do you go back to 1.2.14?

Synaptic only shows version 1.2.16 now.

---

### Post by cybrsaylr on 2012-10-20
Bump!
Can anyone help here?

---

### Post by cybrsaylr on 2012-10-21
Bump.
Anyone have any ideas?

---

### Post by wildmanne39 on 2012-10-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

