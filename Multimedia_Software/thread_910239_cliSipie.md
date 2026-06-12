---
title: "cliSipie"
date: 2008-09-04
forum: Multimedia Software
---

### Post by myname on 2008-09-04
I have sipie running with the popup.  how do I get sipie to run in the command line as it did circa 2006/2007?  I see there is a cliPlayer.py, but can't get it to work.

I also have a Kubuntu machine with I think Edgy Eft on it with an older version of a command line only sipie player working on it, and when I copied the sipie file over to my newer install of linux I can't get it to work.

Any help?

--kp

ps.  btw, this forum seems to be the only linux distro that has an active sipie base.

---

### Post by myname on 2008-09-05
I just tried to get the latest version of sipie with subversion, here is what I did, and the error that I received:


```

svn co https://sipie.svn.sourceforge.net/svnroot/sipie sipie
cd sipie
sudo easy_install sipie

```

error I received:
```

~/sipie> sudo easy_install sipie
root's password:
error: can't create or remove files in install directory

The following error occurred while trying to add or remove files in the
installation directory:

    [Errno 2] No such file or directory: '/usr/local/lib/python2.5/site-packages/test-easy-install-7871.pth'

The installation directory you specified (via --install-dir, --prefix, or
the distutils default setting) was:

    /usr/local/lib/python2.5/site-packages/

This directory does not currently exist.  Please create it and try again, or
choose a different installation directory (using the -d or --install-dir
option).

```

I am using openSUSE and not ubuntu if that helps.  This is one of the only forums/distros that have active sipie threads in them.  I would also like to get the command line sipie working, though I don't see cliSipie as other mentioned.  I do see cliPlayer but that doesn't work.

any help is greatly appreciated.

--kp

---

