---
title: "upgrade alsa question"
date: 2010-10-04
forum: Multimedia Software
---

### Post by cmcanulty on 2010-10-04
I am the tech person for our local library and can't get one machine running Lucid to have sound. I am following the instructions on this web page and the terminal stops at this point every time-see below code-is that normal and should I continue the reason I ask is it never seems to finish and go to the user prompt. I have waited over an hour on several tries. The sound card is Ensoniq ES1371 and worked in  windows but I want all our public computers on Ubuntu only. This is the only one with a sound problem.I am a volunteer though not a pro. Thank you.
[URL="http:// http://[URL="http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/"]monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04
```

librarian@OldDell:~$ wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2
--2010-10-04 17:34:14--  ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2
           => `alsa-lib-1.0.23.tar.bz2'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/lib ... done.
==> SIZE alsa-lib-1.0.23.tar.bz2 ... 808271
==> PASV ... done.    ==> RETR alsa-lib-1.0.23.tar.bz2 ... done.

    [                     <=>               ] 808,271      129K/s   in 6.3s    

2010-10-04 17:34:22 (125 KB/s) - `alsa-lib-1.0.23.tar.bz2' saved [808271]

librarian@OldDell:~$ wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2
```

---

