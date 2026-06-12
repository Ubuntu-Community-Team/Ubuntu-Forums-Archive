---
title: "Could not download packages from repositary in ubuntu 8.04"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by OrEvA on 2009-07-06
I use Ubuntu hardy heron. Few days back I had installed google desktop on my computer. Since then I have not been able to download anything from the repos (either using synaptic or aptitude ).I am not even able to install any updates. I have to download every thing by pasting for each and every package I need to download for installing any software & hence got a broken package and am not able to fix it coz I just cant download it. this the kind of error I get every time I try to use:
pravin@pravin-desktop:~$ sudo apt-get install -f
[sudo] password for pravin:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gtk2-engines-pixbuf
The following packages will be upgraded:
  gtk2-engines-pixbuf
1 upgraded, 0 newly installed, 0 to remove and 311 not upgraded.
Need to get 317kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main gtk2-engines-pixbuf 2.12.9-3ubuntu5
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.12.9-3ubuntu5_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.12.9-3ubuntu5_i386.deb) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
pravin@pravin-desktop:~$
Pls tell me how to resolve the problem.
P.S. : I am not using any proxies and I have no problem in browsing "http://www.in.archive.ubuntu.com" and I had uninstalled google desktop the moment I found the problem.

---

### Post by BbUiDgZ on 2009-07-06
> **OrEvA said:**
> I use Ubuntu hardy heron. Few days back I had installed google desktop on my computer. Since then I have not been able to download anything from the repos (either using synaptic or aptitude ).I am not even able to install any updates. I have to download every thing by pasting for each and every package I need to download for installing any software & hence got a broken package and am not able to fix it coz I just cant download it. this the kind of error I get every time I try to use:
pravin@pravin-desktop:~$ sudo apt-get install -f
[sudo] password for pravin:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gtk2-engines-pixbuf
The following packages will be upgraded:
  gtk2-engines-pixbuf
1 upgraded, 0 newly installed, 0 to remove and 311 not upgraded.
Need to get 317kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main gtk2-engines-pixbuf 2.12.9-3ubuntu5
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.12.9-3ubuntu5_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.12.9-3ubuntu5_i386.deb) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
pravin@pravin-desktop:~$
Pls tell me how to resolve the problem.
P.S. : I am not using any proxies and I have no problem in browsing "http://www.in.archive.ubuntu.com" and I had uninstalled google desktop the moment I found the problem.

never seen google desktop on a linux machine,
but on a windows machine it installes a thing called google gears.. this is a local proxy so u can use google apps offline.

i'd be willing to put money on it has somthing to do with this

---

### Post by OrEvA on 2009-07-06
I know that it has got something to do with local proxy but I am not using any and thats why I have the problem and I and not even able to repair the broken package

---

