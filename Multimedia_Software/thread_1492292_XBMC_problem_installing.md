---
title: "XBMC problem installing"
date: 2010-05-24
forum: Multimedia Software
---

### Post by archeryrob on 2010-05-24
Floowing instructions on this page:
[http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)

I get to the second line
```
sudo add-apt-repository ppa:team-xbmc

```

And then get a failure to get a key
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 189701DA570C56B9488EF60A6D975C4791E7EE5E
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

It pauses for a while at the first gpg: requesting key, but never gets it.

What am I doing wrong, or is there a better way to install? XMBC did not show under the software search under applications.

---

