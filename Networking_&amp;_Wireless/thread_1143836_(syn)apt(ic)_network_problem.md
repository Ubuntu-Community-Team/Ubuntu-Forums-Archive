---
title: "(syn)apt(ic) network problem"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by j.marinus.dejong on 2009-04-30
On several occasions concerning apt/synaptic (upgrading to jaunty, reloading list in synaptic, 'sudo apt-get upgrade' in terminal) an error report similar to the following occurs:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty Release: The following signatures were invalid: NODATA 2
W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://nl.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://nl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Error reading from server - read (104 Connection reset by peer)
W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://nl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://nl.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  
W: Some index files failed to download, they have been ignored, or old ones used instead.

I think the problem lies somewhere outside the computer because the problems occurs both in jaunty as in intrepid, and on different computers in my home network. Even after a clean install of jaunty, the problem persists. So it must be the modem or my internet provider but I have no idea where to look. Internet access through firefox and evolution is working normally, as are some repositories in synaptic.

Could someone help me any further?

---

### Post by t0mppa on 2009-04-30
Did you check [this thread]("http://ubuntuforums.org/showthread.php?t=1137452")?

---

### Post by j.marinus.dejong on 2009-04-30
I just did.

I did what is proposed there, without any result. After making my sources.list empty, I opened synaptic, checked the boxes of the additional repositories, then I clicked 'Reload' and got the following error message:

GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release: The following signatures were invalid: NODATA 2Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.92.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

It's smaller then the previous ones, but is still there.

---

### Post by t0mppa on 2009-04-30
Then I'm out of ideas. Think I remember seeing someone with this problem, because he had an expired pgp key for the Ubuntu archives that was giving the trouble, but that kind of an issue shouldn't persist over a format + clean install.

---

