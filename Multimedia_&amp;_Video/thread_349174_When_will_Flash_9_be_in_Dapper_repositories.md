---
title: "When will Flash 9 be in Dapper repositories?"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by ChrisC on 2007-01-29
I'm patiently waiting for Flash 9 to appear in the repositories as a clean update for Dapper. Is this ever going to happen? The Edgy-package/backports-package solution sounds messy.

I'm trying to keep everything on my system within the apt/Synaptic mechanism, which is why I'm trying to avoid the manual solution described at [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) .

Any idea if work is underway to officially bring Flash 9 to Dapper?

---

### Post by phossal on 2007-01-29
Why not just download it from Adobe? In fact, today, it *automatically installed itself!* I reinstalled Edgy, and the first flash-enabled page I visited prompted me to install. And it *worked!* In the past (since v9 has been available) I've just downloaded it from adobe.

---

### Post by 23meg on 2007-01-29
Stable releases don't get new packages or feature updates; only security updates.

---

### Post by ChrisC on 2007-01-30
> **23meg said:**
> Stable releases don't get new packages or feature updates; only security updates.

True, but surely there's a apt/repository method for doing this, or someone has this in the works.  If I want this machine to be clean and stable and usable for several years, until the next LTS release, then I need to exhibit discipline on software installs and stick with packages available within Synaptic.  It's served me well for the year so far (and most of my career with Linux in general).

Is anyone aware of any work to bring Flash 9 into a repository where it can be added to a Dapper/6.06 system?

---

### Post by phossal on 2007-01-30
> **ChrisC said:**
> If I want this machine to be clean and stable and usable for several years, until the next LTS release, then I need to exhibit discipline on software installs and stick with packages available within Synaptic.
Are you *serious*?

> **ChrisC said:**
> True, but surely there's a apt/repository method for doing this...
Why don't you work on it? It wouldn't take you very long. It would a good way to give back to the community, if you felt inspired.

---

### Post by abou on 2007-01-31
Flash 9 for Firefox is incredibly easy to install.  There really are no worries about messing up the system.  Just download it from Adobe and drop the file into the Firefox plug-in folder.  If you are unfamiliar with command line, just open up Nautilus or Konqueror with sudo from the terminal and move *libflashplayer.so* to the directory */usr/lib/firefox/plugins/* .  All there is to it.

---

### Post by phossal on 2007-01-31
> **abou said:**
> Flash 9 for Firefox is incredibly easy to install.  There really are no worries about messing up the system.  Just download it from Adobe and drop the file into the Firefox plug-in folder.  If you are unfamiliar with command line, just open up Nautilus or Konqueror with sudo from the terminal and move *libflashplayer.so* to the directory */usr/lib/firefox/plugins/* .  All there is to it.

Did you see my post that it *auto* installed for me? That's *awesome!* But, for the OP, some people are Ubuntu purists, and that's *O-K!* I just think it would be neat if he (or she) would take on the project of preparing the package. It would be a neat project.

---

### Post by 23meg on 2007-01-31
> **ChrisC said:**
>  If I want this machine to be clean and stable and usable for several years, until the next LTS release, then I need to exhibit discipline on software installs and stick with packages available within Synaptic. What's "in Synaptic" depends on what's in your sources.list file (your selection of repositories); the older version of Flash is in the Multiverse repository, since it's closed source and non-Free, thus does not and cannot get support. 
> **ChrisC said:**
> 
Is anyone aware of any work to bring Flash 9 into a repository where it can be added to a Dapper/6.06 system?No, and there won't be any, and as others have said, there are two very simple methods to install it.

---

### Post by abou on 2007-01-31
> **phossal said:**
> Did you see my post that it *auto* installed for me? That's *awesome!* But, for the OP, some people are Ubuntu purists, and that's *O-K!* I just think it would be neat if he (or she) would take on the project of preparing the package. It would be a neat project.Whoops, I must have skipped over it.  Good to see that function is working properly now.

For me, when I built my new machine and installed Kubuntu I just went ahead and grabbed Flash once I had internet - force of habit.  But again, good to see that is up and running.

---

