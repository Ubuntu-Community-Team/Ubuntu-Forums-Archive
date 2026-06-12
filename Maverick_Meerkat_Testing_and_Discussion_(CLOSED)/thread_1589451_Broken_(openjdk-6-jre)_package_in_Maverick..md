---
title: "Broken (openjdk-6-jre) package in Maverick."
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by moma on 2010-10-06
Hello,
I have installed 64bit Maverick from current (daily) iso image.
When running the following commands, it complains that the "openjdk-6-jre" package is broken. Is this a normal behaviour?

[COLOR="SeaGreen"]sudo apt-get install --reinstall ubuntu-restricted-extras icedtea6-plugin openjdk-6-jre[/COLOR]

Then remove the openjdk packages (or simply remove all openjdk-6-*).

[COLOR="SeaGreen"]sudo apt-get remove --purge -y icedtea6-plugin openjdk-6-jre openjdk-6-jre-lib[/COLOR]
Reading package lists... Done
Building dependency tree       

[COLOR="Red"]The following packages have unmet dependencies:
 openjdk-6-jre : Depends: openjdk-6-jre-headless (>= 6b20-1.9-0ubuntu1) but it is not going to be installed
E: Broken packages
[/COLOR]
Check:
[COLOR="SeaGreen"]dpkg -l | grep openjdk[/COLOR]
ii  openjdk-6-jre        6b20-1.9-0ubuntu1 OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless  6b20-1.9-0ubuntu1 OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib      6b20-1.9-0ubuntu1  OpenJDK Java runtime (architecture independent libraries)
---

See also: [http://ubuntuforums.org/showthread.php?t=1585795](http://ubuntuforums.org/showthread.php?t=1585795)

---

### Post by cariboo on 2010-10-06
Could it be that you are using a mirror that is a little behind?

---

### Post by moma on 2010-10-06
Re-hello,
That is absolutely possible. My current repo-server is   [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/). 
I will update the package list and try the commands tomorrow. So long.

---

### Post by moma on 2010-10-07
Hi,
The problem still persist. I think this is a real issue.

EDIT: It works if I first remove openjdk-6-jre
[COLOR="SeaGreen"]sudo apt-get remove --purge -y openjdk-6-jre[/COLOR]
Then remove the rest
[COLOR="SeaGreen"]sudo apt-get remove --purge -y openjdk*[/COLOR]

---

### Post by DevHead on 2010-10-07
This works for me:
sudo apt-get install openjdk-6-jdk

I'll need to try jre next.

---

