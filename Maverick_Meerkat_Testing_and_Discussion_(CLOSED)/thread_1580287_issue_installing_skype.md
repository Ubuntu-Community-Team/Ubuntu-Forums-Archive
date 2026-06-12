---
title: "issue installing skype"
date: 2010-09-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by gexi on 2010-09-23
following [this tutorial]("http://www.liberiangeek.net/2010/09/install-skype-ubuntu-10-10-maverick-meerkat/"), i tried to install skype yesterday by adding the maverick partner repos to the software-sources (because there's no specific skype-ppa for maverick yet).

apparently this lead to unsolveable dependency issues: software-center (and synaptic and apt-get) cannot install ia32-libs. or to be more precise:  */var/cache/apt/archives/ia32-libs_20090808ubuntu4_amd64.deb* &#8230;

> E: /var/cache/apt/archives/ia32-libs_20090808ubuntu4_amd64.deb: Versuche, »/usr/lib32/libstdc++.so.5.0.7« zu überschreiben, welches auch in Paket lib32stdc++5 3.3.6~ppa~lucid2 ist
this is the error synaptic gives me when i try to install ia32-libs manually. translation is:
> E: /var/cache/apt/archives/ia32-libs_20090808ubuntu4_amd64.deb: Try to overwrite »/usr/lib32/libstdc++.so.5.0.7«, which is also in package lib32stdc++5 3.3.6~ppa~lucid2

running apt-get install -f, as suggested by software-center didn't help.

btw. as you can see: i got the 64bit version of maverick.

any suggestions?

---

### Post by forcecore on 2010-09-23
Can you run static version? and it wont require installation.

[http://www.skype.com/go/getskype-linux-beta-static](http://www.skype.com/go/getskype-linux-beta-static)

---

### Post by gexi on 2010-09-23
> **forcecore said:**
> Can you run static version? and it wont require installation.

[http://www.skype.com/go/getskype-linux-beta-static](http://www.skype.com/go/getskype-linux-beta-static)


nope, same problem. error is the same when i try running skype without ia32-libs installed:

> error while loading shared libraries: libXv.so.1: cannot open shared object file: No such file or directory


---

### Post by gexi on 2010-09-23
just a guess, but, because i couldn't find any other users with the same problem, could it be, that the upgrade (instead of a clean install) is responsible for this?

---

### Post by meborc on 2010-09-23
just tried on my MM 64-bit, skype installs from repos without the problem...

I usually just uncomment the appropriate lines from /etc/apt/sources.list and then **sudo apt-get update && sudo apt-get install skype**

might be there is a glitch in the software center, lot of work going into that one still...

---

### Post by gexi on 2010-09-23
no, it doesn't work.

neither software-center, nor apt-get, nor synaptic is able to install *ia32-libs_20090808ubuntu4_amd64.deb*.

did you do a clean install, or a dist-upgrade as i did?

---

### Post by meborc on 2010-09-24
> **gexi said:**
> no, it doesn't work.

neither software-center, nor apt-get, nor synaptic is able to install *ia32-libs_20090808ubuntu4_amd64.deb*.

did you do a clean install, or a dist-upgrade as i did?

clean install as of beta1 and then upgraded to latest

upgrade to non-stable usually brings annoying glitches which I like to avoid ;)

---

### Post by KristinaK on 2010-09-24
is there open source alternative to skype?

---

### Post by meborc on 2010-09-24
> **KristinaK said:**
> is there open source alternative to skype?

there is [http://ekiga.org/](http://ekiga.org/) which you might like... but since everyone else is using skype, skype is quite important

---

### Post by FuturePilot on 2010-09-24
> **gexi said:**
> E: /var/cache/apt/archives/ia32-libs_20090808ubuntu4_amd64.deb: Try to overwrite »/usr/lib32/libstdc++.so.5.0.7«, which is also in package lib32stdc++5 3.3.6~ppa~lucid2 

You've got a package installed from a PPA for Lucid. Reinstall the version of that package that is in the Maverick repos. Or perhaps remove it all together. Sounds like it's already in ia32libs.

---

### Post by perspectoff on 2010-09-24
> **meborc said:**
> there is [http://ekiga.org/](http://ekiga.org/) which you might like... but since everyone else is using skype, skype is quite important

I have both, and I agree that Skype is important and is so widely used that it is necessary to have. Also, Skype has great quality control.

Having said that, Skype is proprietary and there is no assurance that it will not go fee-for-service one day, once it has reached a threshold penetrance (following the Microsoft business model).

Ekiga has had a slow development path, but has made leaps and bounds the past few versions.

While Skype uses encrypted point-to-point communication and is therefore secure for business use, it is still required to use Skype's SIP servers. Theoretically, there is always some risk of man-in-the-middle SIP spoofing somewhere.

You can use Ekiga within an organization using your own SIP servers (using OpenSIP, for example). For business use, this allows to keep everything in house, which ideologically I like. Any combination of programs and servers that can stay completely within my corporate LAN is desirable to me.

But even then, almost all my computers currently have Skype on them, as well.

---

### Post by SeijiSensei on 2010-09-29
I installed Kubuntu 10.10 amd64 this morning using the daily build for 9/28.  I then went to the Skype page, downloaded the 64-bit deb package they have (for 8.10; nothing more recent) and ended up in dependency hell.

The Skype binary wants five missing packages:

```

dpkg: dependency problems prevent configuration of skype:
 skype depends on lib32stdc++6 (>= 4.1.1-21); however:
  Package lib32stdc++6 is not installed.
 skype depends on lib32asound2 (>> 1.0.14); however:
  Package lib32asound2 is not installed.
 skype depends on ia32-libs (>= 1.6); however:
  Package ia32-libs is not installed.
 skype depends on libc6-i386 (>= 2.7-1); however:
  Package libc6-i386 is not installed.
 skype depends on lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19); however:
  Package lib32gcc1 is not installed.

```

So I used apt-get to install those five and got this result:

```

The following packages have unmet dependencies:
 ia32-libs : Depends: lib32z1 but it is not going to be installed
             Depends: lib32bz2-1.0 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed
             Depends: lib32v4l-0 but it is not going to be installed

```

While I could get Skype to install by adding these dependencies as well, I don't see how ordinary users could possibly negotiate their way through this minefield.  I also don't understand why ia32-libs made me include its dependencies manually; why didn't apt do that for me?

Given the growing ubiquity of Skype, not being able to install the "official" binary at skype.com is going to discourage people from using Ubuntu/Linux, I'm afraid.

"apt-get install skype" doesn't work either:

```

Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

"apt-get install skype*" results in

```
E: Unable to locate package skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb
E: Couldn't find any package by regex 'skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb'
E: Unable to locate package skype-ubuntu-intrepid_2.1.0.81-1_i386.deb
E: Couldn't find any package by regex 'skype-ubuntu-intrepid_2.1.0.81-1_i386.deb'

```

Perhaps I need to activate another repository, but the average person won't know how to do that either.

---

### Post by MarkieB on 2010-09-29
no longer participating in ubuntuforums.org

---

### Post by SeijiSensei on 2010-09-29
> **MarkieB said:**
> try the partner repo?

Best

I got it to install via the method I described above.

The partner repo wasn't mentioned during the installation I ran this morning.  How would I have known to add it if all I wanted to do was install Skype?  How would I have known how to add a repository at all?

I'm trying to look at this problem from the perspective of someone who just decided to try out Ubuntu and then tried to install Skype from its home page just like he or she would have done in Windows.  Now, admittedly, since the file is a .deb, that may well be a show-stopper right there.  Firefox didn't offer me the usual "Open with/Save as" dialog when I clicked on the link to the .deb either.  So now it's sitting in my Downloads folder.  If I open the file from there, I see the warning "You are strongly advised to install the version from the software channel..."  What's a "software channel"?  How do I get the version from there?  I think at this point I'd be giving up and returning to Windows, at least to use Skype.

---

### Post by astrobob.tk on 2010-09-29
I am not exactly sure how to help regarding the above details, but I suggest (as I did) to install the 32bit version & use it instead of the 64bit one. It worked for me on my Ubuntu 10.04 LTS

---

### Post by SeijiSensei on 2010-09-29
> **astrobob.tk said:**
> I am not exactly sure how to help regarding the above details, but I suggest (as I did) to install the 32bit version & use it instead of the 64bit one. It worked for me on my Ubuntu 10.04 LTS

Once again, I have the 64-bit version running by manually installing the needed dependencies as I described above.  I don't need help with that.  My concerns have to do with the *process* of installing Skype and how daunting the task would be for an ordinary user.

> While I could get Skype to install by adding these dependencies as well, I don't see how ordinary users could possibly negotiate their way through this minefield. I also don't understand why ia32-libs made me include its dependencies manually; why didn't apt do that for me?

---

