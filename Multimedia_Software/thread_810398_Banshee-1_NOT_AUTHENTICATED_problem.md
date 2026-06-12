---
title: "Banshee-1 NOT AUTHENTICATED problem"
date: 2008-05-28
forum: Multimedia Software
---

### Post by aleska on 2008-05-28
So, I read an ars technica review of Banshee 1.0 beta, and in the comments it indicated that you could keep up with the most recent builds by adding "deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main" to sources.list.
I did so, but when I run Synaptic to install it I get the warnings that this is NOT AUTHENTICATED, and could enable a malicious individual to damage or take control of my system.  I assume this is avoided in other cases by getting and adding the key?

Any ideas on how I go about getting the key for this and properly adding it so that I avoid this message?

Thx

---

### Post by hyperair on 2008-05-28
I'm sorry, but because this is launchpad.net we're talking about, there is no key. They haven't implemented GPG authentication for their PPAs yet, as private keys need to be uploaded to launchpad.net in order for the system to work as it is now. And that is a rather insecure manner of doing things.

---

