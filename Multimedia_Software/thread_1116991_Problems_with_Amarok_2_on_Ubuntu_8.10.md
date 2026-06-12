---
title: "Problems with Amarok 2 on Ubuntu 8.10"
date: 2009-04-05
forum: Multimedia Software
---

### Post by midnightLuke on 2009-04-05
Ok, I think I've done my homework on the forums here, but I still haven't found a solution to my little problem.

I successfully installed and ran amarok 2 on my ubuntu machine for a little while, and I was liking the new amarok.  Ubuntu then did a strange update that removed amarok 2 and some of my themes (this was last week sometime), and now I cannot seem to get amarok 2 installed again.

I have [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main in my third party software sources, and amarok-kde4 comes up in synaptic when I search it, but when I mark it for installation I get an error saying that kdebase-runtime needs to be installed but isn't going to be.

I thought maybe I could work around this by typing ```
sudo apt-get install amarok-kde4
``` into terminal, but I get the same error.  The output looks like: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  amarok-kde4: Depends: kdebase-runtime (>= 4:4.1.2) but it is not going to be installed
E: Broken packages
```

So now I tried typing this into the terminal: ```
sudo apt-get install kdebase-runtime
``` thinking that maybe that would solve my problem, but the error message now reads: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdelibs5 (>= 4:4.1.96) but it is not going to be installed
                   Depends: libstreamanalyzer0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
                   Depends: libstreams0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
                   Depends: kdebase-runtime-bin-kde4 (= 4:4.2.2-0ubuntu1~intrepid1) but it is not going to be installed
E: Broken packages
```

Any ideas about how I can get back my amarok 2?  I'm using aTunes now, but it is prone to crashing.

Thanks for any help, and sorry for the long post.

---

### Post by wolfen69 on 2009-04-05
you have broken packages. go to synaptic and select edit>fix broken packages. then reload.

---

### Post by midnightLuke on 2009-04-05
Ok, I clicked "Edit -> Fix Broken Packages" then "Reload"and the following error pops up: ```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
``` and I still get the same errors when trying to mark "amarok-kde4" for installation.

Any further ideas?

---

### Post by kiprit on 2009-04-05
> **midnightLuke said:**
> Ok, I clicked "Edit -> Fix Broken Packages" then "Reload"and the following error pops up: ```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
``` and I still get the same errors when trying to mark "amarok-kde4" for installation.

Any further ideas?

The answer for this was given here: [http://ubuntuforums.org/showthread.php?t=1055420]("http://ubuntuforums.org/showthread.php?t=1055420") 

Basically in your case what you need to do is to open the terminal and type:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 9423A34CCA967634
```

and then

```
gpg --export --armor 9423A34CCA967634 | sudo apt-key add -
```

after you have the new key, try again...

---

### Post by midnightLuke on 2009-04-05
> **kiprit said:**
> The answer for this was given here: [http://ubuntuforums.org/showthread.php?t=1055420]("http://ubuntuforums.org/showthread.php?t=1055420") 

Basically in your case what you need to do is to open the terminal and type:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 9423A34CCA967634
```

and then

```
gpg --export --armor 9423A34CCA967634 | sudo apt-key add -
```

after you have the new key, try again...

Ok, this all got rid of the error I was getting when reloading in synaptic, but I am still having the same problems when trying to install amarok-kde4.

Any other suggestions? Should I just give up and re-install Ubuntu all together?

---

### Post by kiprit on 2009-04-06
OK maybe I am not the best person to fix this problem but did you try typing:

> sudo dpkg --configure -a (which configures some of the partly installed packages)
and then 
> sudo aptitude -f install which checks the  dependencies and installs them.

In case this wouldn't work, I would try to reinstall kdelibs5, libstreamanalyzer0 , and kdebase-runtime-bin-kde4 with Synaptic

---

### Post by midnightLuke on 2009-04-06
Thanks for all the help and suggestions kiprit, the ubuntu community is really blowing me away here, this is awesome.

Unfortunately I am still having problems after trying your last suggestion.  Terminal and synaptic don't seem to want to install any of the packages you listed.  I'll list the error messages terminal spits out:

sudo apt-get install kdelibs5:

```

Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  kdelibs5: Depends: libstreamanalyzer0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
            Depends: libstreams0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
E: Broken packages

```

sudo apt-get install libstreamanalyzer0 (technically not an error, but it won't get the new version needed to satisfy the dependencies of everything else):

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstreamanalyzer0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

sudo apt-get install kdebase-runtime-bin-kde4:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  kdebase-runtime-bin-kde4: Depends: kdebase-runtime (>= 4:4.2.0) but it is not going to be installed
                            Depends: kdelibs5 (>= 4:4.1.96) but it is not going to be installed
E: Broken packages

```

I have already repaired broken packages using synaptic (MANY times), but this doesn't seem to resolve anything.

Thanks again for all the help!

---

### Post by JimmyJam4PHP on 2009-04-06
I had the same exact thing happen.  I was running with Amarok 2 until this last update when it was removed.  Attempting to re-install gave me the same error.  kdepim was also removed and presents a similar error.  I have installed Thunderbird and Amarok 1 until this can be resolved.

```
sudo apt-get install amarok
```

Will give you Amarok until Amarok 2 can be re-installed. Hopefully before the release of Jaunty.

~ JimmyJam

---

### Post by midnightLuke on 2009-04-06
Argh, I hope this doesn't last too long, Amarok 1 is nice, but I was getting attached to the nice new GUI of Amarok 2 (despite what the haters are saying).  Oh well, I guess I'll have to try out some other stuff for now, I've heard Songbird is pretty good...

---

### Post by aniruddha on 2009-04-06
Hello all. I am having a somewhat similar problem. Amarok 2 installs but refuses to play any audio file/audio cd. The GUI displays something like "too many errors" message in the lower right hand corner. I tried following the instructions on this thread, and synaptic refuses to install kdelibs5. The terminal displays the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs5: Depends: libstreamanalyzer0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
            Depends: libstreams0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
E: Broken packages

Any help would be much appreciated. Thanks...

---

### Post by midnightLuke on 2009-04-07
Hey aniruddha,

I wouldn't get my hopes up about a solution, although there were lots of suggestions none seemed to work for me.

I installed songbird ([http://getsongbird.com](http://getsongbird.com)), which is awesome so far.  If you're familiar with iTunes then songbird should look pretty familiar, and so far I like it better than amarok 2.

Anyways thats just a heads up, I do hope someone finds a solution, but I'm not getting my hopes up, hopefully Jaunty will fix the error.

---

### Post by aniruddha on 2009-04-08
Hmm. I personally dislike iTunes, so the relative similarity to the iTunes UI is a bit putting off (for songbird). Thanks for the suggestion though. 

Although, according to [this]("http://ubuntuforums.org/showthread.php?t=1105257&highlight=install+amarok+2") it may be possible to get amarok 2 to install and run. Although I am giving up on that as well after going over the developers wiki. Apparently, giving audiocd support was deemed unnecessary. Sheesh. 

no worries

---

### Post by gmork123 on 2009-04-09
Hi,

I was reading about the nightly builds on 
  [http://amarok.kde.org/forum/index.php?topic=15866.0](http://amarok.kde.org/forum/index.php?topic=15866.0) 
and added 

  deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) intrepid main

to my non-kde ubuntu 8.10 desktop.

After update I could install 

  amorok-nightly

it gave some scary install errors and the amarok-nightly-kdebase failed to install but I do have a amarok-nightly version 2 install now which seems to work.

Wessel

---

### Post by claudiocq on 2009-04-16
Hi,

try this

[http://ubuntuforums.org/showthread.php?t=1002626](http://ubuntuforums.org/showthread.php?t=1002626)

---

### Post by Munschy_00 on 2009-05-26
Make sure all repositories are good to go through your synaptic as well...

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

It was so simple...even though i spent hours trying to figure this out...

---

### Post by matyasfalvi on 2009-07-17
Hi!

I'm using 8.04. Just curious does amarok 2 actually work on hardy?

'cause I've been trying to install it for a while without any success. 

I always get this message from Gdebi:

```
Error: Dependency is not satisfiable: kdebase-runtime
```

although I have all the kdebase-runtime packeges installed.

I attached two screenshots one from the package installer and one from the synaptic package manager.

I also fixed all the broken packages and everything did all the stuff that was explained in this thread. 

So I'm puzzled as to whether it is even possible or I'm just chasing ghosts?

I'd appreciate any kind of help.

Thanx

---

### Post by delubu on 2009-07-26
I am trying to install amarok2 in ubuntu 8.10 and i also get the same problem

The following packages have unmet dependencies:
  amarok-kde4: Depends: kdebase-runtime (>= 4:4.1.2) but it is not going to be installed
E: Broken packages


has anybody found any solution yet? google brings me back to this thread :\

---

### Post by matyasfalvi on 2009-07-27
Hey Delubu!

You can fix broken packages with synaptic package manager.

Just go to System > Administration > Synaptic Package Manager then enter password and go to Edit > Fix broken packages.

But what I have read so far this probably won't fix it either. However give it a try it might work.

Meanwhile if someone knows something about amarok 2 and hardy let me know :D

---

