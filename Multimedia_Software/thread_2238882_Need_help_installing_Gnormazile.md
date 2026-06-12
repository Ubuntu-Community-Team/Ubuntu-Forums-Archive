---
title: "Need help installing Gnormazile"
date: 2014-08-10
forum: Multimedia Software
---

### Post by Cindi_Marshall on 2014-08-10
I have been trying to install gnormalize on Ubuntu 14.04.1.  I have downloaded the install package, opened the terminal window and type in the first command to try to install it, and this is what I get:

cindi@cindi-Aspire-X1430G:~$ tar zxvf gnormalize-version.tar.gz
tar (child): gnormalize-version.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

I don't understand what I am doing wrong - unless I need to move the package to the root directory instead of the download directory that it is in right now.  Can someone please help me?

---

### Post by coffeecat on 2014-08-11
The message "Cannot open: No such file or directory" is the clue. You have downloaded to your Downloads folder, but in the terminal you are in your home folder. You need:

```
cd Downloads
```

Before you run the tar command. Also, the "tar zxvf gnormalize-version.tar.gz" command needs to be adapted to the actual filename. I presume you found the instructions here:

[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)

Telling people to "tar zxvf gnormalize-version.tar.gz" without any note for inexperienced users explaining that you need to adapt the command is scrappy, unprofessional even, in my opinion. I hope the software is better than the instructions. Currently, the downloaded tar.gz file is gnormalize-0.63.tar.gz, so the tar command needs to be:

```
tar zxvf gnormalize-0.63.tar.gz
```

And the cd command that follows would need to be:

```
cd gnormalize-0.63
```

By the way, it's "Downloads" not "download". The bash terminal is specific to spelling and case.

---

