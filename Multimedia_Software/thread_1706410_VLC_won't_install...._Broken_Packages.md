---
title: "VLC won't install.... Broken Packages?"
date: 2011-03-13
forum: Multimedia Software
---

### Post by Tirish Anau on 2011-03-13
I have attempted to install VLC several times. I didn't began having installation problems with anything until I installed then Uninstalled virtualbox. Any Suggestions? Could this be a simple as bad source?


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mozilla-plugin-vlc : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
 vlc : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 1.1.4-1ubuntu1.4) but it is not going to be installed
 vlc-plugin-pulse : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
E: Broken packages
```

---

### Post by MrEgg on 2011-03-25
Hi,

I'm having the same problem exactly. What I've done is to select a new ppa from which I pulled vlc, and then I deleted the ppa so that the rest of what it contains would not interfere with my stuff.

Available ppas containing vlc :
Ubuntu 10.04, 10.10 - ppa:ed10vi86/video
Ubuntu 10.10 - ppa:n-muench/vlc

Step 1. Subscribe to the ppa (eg : the first one listed above) :
```
sudo apt-add-repository ppa:ed10vi86/video
```

Step 2. Update your list
```
sudo apt-get update
```

Step 3. Install vlc
```
sudo apt-get install vlc
```

Step 4. Remove the ppa
```
cd /etc/apt/sources.list.d/
sudo rm ed10vi86-video-maverick.list
```

Note : in Step 4, just type 'sudo rm ed10' then hit TAB to autocomplete. 'maverick' or 'lucid' will appear as part of the name, depending on the version of Ubuntu you're running.

Step 5. Update your list : repeat step 2.

HTH,
Egg

---

