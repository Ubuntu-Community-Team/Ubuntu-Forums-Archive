---
title: "Upgrade Minitube 1.2"
date: 2010-11-05
forum: Multimedia Software
---

### Post by dutchgirl on 2010-11-05
Hello, I am trying to upgrade my minitube player to 1.2 on ubuntu 10.10 and I can't figure out for the life of me on how to upgrade/reinstall to the latest version. I downloaded the .gz binary file from the website. I originally installed the minitube via synaptic package manager. I've tried unistalling and reinstalling. Please help. Thanks in advance for your time and effort.

---

### Post by luigi_mb on 2010-11-05
> **dutchgirl said:**
> Hello, I am trying to upgrade my minitube player to 1.2 on ubuntu 10.10 and I can't figure out for the life of me on how to upgrade/reinstall to the latest version. I downloaded the .gz binary file from the website. I originally installed the minitube via synaptic package manager. I've tried unistalling and reinstalling. Please help. Thanks in advance for your time and effort.

First uninstall the version of Minitube you installed with Synaptic

```

sudo dpkg -r minitube

```

Then, in your home folder, unpack the archive you downloaded

```

tar xvf minitube-linux-1.2.tar.gz

```

Finally launch the application

```

cd ~/minitube
./minitube

```


/luigi

---

### Post by Pabbajati on 2010-11-06
I tried the solution at this ppa where they have commands to update to 1.2:

[http://www.webupd8.org/2010/07/minitube-11-released-upgrade-to-get-it.html](http://www.webupd8.org/2010/07/minitube-11-released-upgrade-to-get-it.html)

It worked for me on 10.04

---

### Post by dutchgirl on 2010-11-06
Thanks so much for your help guys, worked like a charm :popcorn:

---

