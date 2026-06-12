---
title: "Can't install vlc dvd codec in natty"
date: 2011-06-14
forum: Multimedia Software
---

### Post by mpcmpc on 2011-06-14
I'm running natty. My apt-get install vlc keeps failing on...
 vlc-nox : Depends: liba52-0.7.4 but it is not installable
           Depends: libass4 (>= 0.9.7) but it is not installable ...

I believe this is due to the codec being outside the standard package bundles. However I believe I have enabled the Universe package set, so I don't know why this is happening. 

I also tried adding a Medibuntu source, but it wasn't found there either.

Any other ideas on how to troubleshoot? Here's my source list below. I've tried apt-get update and install -f. Does nothing.  

Errors are identical using the synaptic GUI as well. 

MC 



root@Clemetine:/home/techclub# cat /etc/apt/sources.list
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted multiverse universe

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted multiverse universe

###### Ubuntu Partner Repo
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Banshee - [https://edge.launchpad.net/~banshee-team]("https://edge.launchpad.net/%7Ebanshee-team")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) natty main

#### VLC Media Player  - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) maverick main


####### 3rd Party Source Repos

#### Banshee (Source) - [https://edge.launchpad.net/~banshee-team]("https://edge.launchpad.net/%7Ebanshee-team")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) natty main

#### VLC Media Player  (Source) - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb-src [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) maverick main



deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports restricted main multiverse universe

## Added by hand by MPC on 6/11 to get medibuntu for vlc dvd playing
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free 
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx

---

### Post by mikewhatever on 2011-06-14
This might be the cause:
```
#### VLC Media Player - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu **maverick** main
```

There is another one there, so try removing them.

---

### Post by mpcmpc on 2011-06-14
Thanks for the reply. I assume "maverick" was an old build nickname.

I saw that right after I posted, and changed it to natty, apt-get updated and installed. 

No difference.

Technically, it shouldn't be there at all considering I've read that it's supposed to be in "Universe".

MC

---

### Post by mc4man on 2011-06-14
If I were you I'd open synaptic, click on Settings > Repositories 
Then under the 'Other Software' find that korn ppa and remove, it's no good.

Also under the 'Updates' tab you should disable natty-proposed, your choice, but proposed should only be used for specific updates that are either of known value to you or for testing.

While there also make sure the first 4 are enabled under the main 'Ubuntu Software' tab
Then close out Software Sources and click the reload icon in synaptic.

After that search vlc in synaptic, find vlc-data and if installed mark for complete removal and do so.
You should then be able to install the natty current version 1.1.9-1ubuntu1.1

(if you wish the 1.1.10 vlc or the dev 1.2+ version then ppa's that are active can be suggested

---

### Post by mpcmpc on 2011-06-15
Thanks for the advice. I will try that later today when I have access to the machine.

In the meantime, is there an official Ubuntu website that will generate proper source lists based on given criterion? 

That source file was generated from a form that I used online, but I don't remember the URL. I only remember that it was not inside the Ubuntu domain. Obviously it is suspect. 

Thanks again,

Mike C

---

### Post by mpcmpc on 2011-06-24
I finally got around to taking those steps - still getting the same error. I looks to me like the reload is not getting all that it needs to so that the DVD codecs are not seen as available. 

I don't understand this error msg: 
Failed to fetch  gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources   Hash Sum mismatch

Why is this a failure to fetch? Isn't gzip a simple compression tool? What is meant by the Hash Sum?

I should mention that I'm behind a firewall, connecting through a proxy. I have an older Ubuntu install that works just fine. Could this have something to do with an ftp failure due to a blocked port?

Again, any help parsing out these error messages would be appreciated.

mc



#
#Error from synaptic reload 
#

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: Unknown error executing gpgvGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources)  404  Not Found
Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch
Some index files failed to download. They have been ignored, or old ones used instead.


#
#  Error from vlc install
#

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libavcodec52 (>=4:0.6-1~) but it is not installable or
     libavcodec-extra-52 but it is not going to be installed
 Depends: libqtgui4 but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.10) but it is not installable
 Depends: libtar  but it is not installable
 Depends: libva-x11-1  but it is not installable
 Depends: libva1  but it is not installable
 Depends: libxcb-keysyms1 (>=0.3.6) but it is not installable
 Depends: libxcb-randr0 (>=1.1) but it is not installable
 Depends: libxcb-xv0 (>=1.2) but it is not installable
 Recommends: vlc-plugin-notify but it is not going to be installed
 Recommends: vlc-plugin-pulse but it is not going to be installed

---

### Post by mpcmpc on 2011-06-24
I think I found the problem. I switched to [Main Server] instead of [US Server] in  in Synaptic -> Settings -> Repositories -> Download from

vlc is now marked for install and is loading....

fingers crossed

---

