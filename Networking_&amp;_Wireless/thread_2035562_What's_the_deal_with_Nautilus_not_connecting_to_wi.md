---
title: "What's the deal with Nautilus not connecting to windows shares in 12.04?"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by jhboricua on 2012-07-30
I've swear I've tried every permutation of Server, domain, user and password to get Nautilus to allow me to browse my windows shares in Ubuntu 12.04 and the stupid thing keeps asking for credentials.

Things I've tried:

1. Adding the following lines on the global section of smb.conf:

client lanman auth = yes
client ntlmv2 auth = no

2. Trying to connect typing the server name AND domain in all caps per numerous threads on this subject.

3. Tried via ALT-F2, via command line "nautilus smb://blahblahblah", via File>Connect to Server in Nautilus, etc, etc, etc.

All of these end in the same frustrating loop of Nautilus keep asking credentials/not accepting them.

This is only happening on 12.04. This is the third time since it was released that I upgrade my system hoping this stupid bug has been squashed and run into this problem, forcing me to revert. Has a solution _that actually works_ been found?

---

