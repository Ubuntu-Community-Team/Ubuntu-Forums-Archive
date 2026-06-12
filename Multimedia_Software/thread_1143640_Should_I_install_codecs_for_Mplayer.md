---
title: "Should I install codecs for Mplayer??"
date: 2009-04-30
forum: Multimedia Software
---

### Post by emix101 on 2009-04-30
Hi guys!!

I'm newb....on jaunty right now...
I installed Mplayer from Synaptic Package Manager
Do I need to install codecs from the Mplayer website....???
I already download the codecs...and extracted..

If I should, where should I put this codecs into??

I could not find any directory the Mplayer README file mentioned...

Or the Synaptic already installed these codecs for me??:popcorn:

---

### Post by andrew.46 on 2009-04-30
Hi emix,

> **emix101 said:**
> I'm newb....on jaunty right now...
I installed Mplayer from Synaptic Package Manager
Do I need to install codecs from the Mplayer website....???

With MPlayer and Jaunty you have 2 winners already :-). You do not need to *manually* install the MPlayer codecs, a better way is to install them from Medibuntu. For Jaunty first copy this into a terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

and then:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

You will be asked if you wish to accept an unauthenticated package. Saying yes means you trust Medibuntu, as I do. With that done simply install either the *w32codecs* or *w64codecs* depending on whether you have a 32bit or 64bit installation.

All the very best,

Andrew

---

### Post by emix101 on 2009-04-30
Hi Andrew!

I did try ur step u shown me....

but it came out like this:
Fetched 26.2kB in 45s (572B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E02E87DF81C6B219
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://viewizard.com/linux/debian/Packages.bz2](http://viewizard.com/linux/debian/Packages.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.


help me...???

thanx!:popcorn:

---

### Post by x33a on 2009-04-30
try the second step that andrew posted. that will authenticate medibuntu repository, and fix the error you got.

---

### Post by emix101 on 2009-05-01
I already did the second step...but the I shown earlier....that's the result came out for the second step.

---

### Post by andrew.46 on 2009-05-02
Hi emix101,

> **emix101 said:**
> 

```
Fetched 26.2kB in 45s (572B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E02E87DF81C6B219
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://viewizard.com/linux/debian/Packages.bz2](http://viewizard.com/linux/debian/Packages.bz2)  Sub-process bzip2 returned an error code (2)
```

E: Some index files failed to download, they have been ignored, or old ones used instead.


Looks like you have several errors, *one* relating to Medibuntu. There are 2 things you could try. Firstly try running a variation of the previous command:

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

If this still fails you can install the w32codecs manually:

```

wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb

```

and then:

```

sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb

```

I assume that you are not running a 64bit system?

All the best,

Andrew

---

