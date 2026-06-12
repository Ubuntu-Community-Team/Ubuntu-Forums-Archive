---
title: "Trouble installing Virtualbox 6.1.10 on Linux Mint 19.3"
date: 2020-06-07
forum: MINT
---

### Post by glostiik on 2020-06-07
So this is more of an error in upgrading, I have a Virtualbox 5.x.x installed and I uninstalled the program and did a restart on the machine. When i tried to install Virtualbox 6.1.10 I kept getting this error and I idk why. I already looked for those two dependencies and made sure they were installed. Any help would be appreciated.

mint@mint-desktop:~$ sudo apt-get install virtualbox-6.0 -y

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
******The following packages have unmet dependencies:
 virtualbox-6.0 : Depends: libqt5opengl5 (>= 5.0.2) but it is not installable
                  Depends: libsdl1.2debian (>= 1.2.11) but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by wildmanne39 on 2020-06-07
*Thread moved to **MINT for a more appropriate fit**.*

---

### Post by ajgreeny on 2020-06-08
You need to use the Oracle Virtualbox  repos to get the most recent version, 6.1.10.
You will then need to install package virtualbox-6.1, not 6.0

---

