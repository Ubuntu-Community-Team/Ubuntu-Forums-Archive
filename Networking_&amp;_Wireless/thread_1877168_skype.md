---
title: "skype"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by goldshirt9 on 2011-11-07
running 11.10 64 bit.
when i try to install skype  I get the following error using  the software manager

  	 	 	 	 	 	  The following packages have unmet dependencies: 
  
 skype:i386: Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is to be installed 
             Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed 
             Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed 
             Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed 
             Depends: libqtcore4 (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed 
             Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed 
             Depends: libstdc++6 (>= 4.2.1) but 4.6.1-9ubuntu3 is to be installed 



mmmmmmmmmmmm what does this mean :confused:

---

### Post by ajgreeny on 2011-11-07
That must be a 64 bit problem as I have skype running fine on a ubuntu 11.10 32 bit system here.  How are you trying to install it?

I used synaptic, which, of course, I had to install first, as I find it impossible to manage without synaptic, and just can not get on with the software-center, which is too dumbed-down for my liking.

---

### Post by goldshirt9 on 2011-11-07
software centre.
will try synaptic

---

### Post by goldshirt9 on 2011-11-08
no go i get the same error if trying to install via synaptic.
even tried to install from the skype web site.

---

### Post by JayKay3OOO on 2011-11-08
I installed skype about 4h ago from the website and it works fine on 64bit.

I'm confused. Skype i386? Ain't that 32bit skype and you say you are on 64 bit? 

Call me a moron, but did you download the 64bit version from the website?

I've installed the 32 bit version onto 32 bit skype from the website too and it's worked fine in the past.

EDIT:

Download the deb file and open it with software centre. It'll do the rest for you.

---

### Post by goldshirt9 on 2011-11-09
so i cannot install from the software manager which only offers 32 bit,because of the said errors.

if i install from skype direct , i can only find 10.04 64 bit  ,
which gives me the same error's.
As my webcam also has a pretty poor picture using cheese , I am guessing it is something to do with the drivers and such.

although i run 11.10 it is a derivative of Ubuntu 
it is luninuxos.

i have posted this on their site , but as it is mainly Ubuntu i was hoping to find 
a solution here.

anyway onwards i go. to find a solution.

---

### Post by sauen on 2011-11-09
Are you sure you downloaded this?

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/downloading.ubuntu64]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/downloading.ubuntu64")

To find out if you are running 32 or 64 bit Linux, open a terminal and type 'uname -m'. If i says x86_64, you need the 64 bit deb file in the above link, if not, you need to install the 32 bit deb file.

To install the dependencies you mentioned in the first post, just type it in a terminal like this:
```
sudo apt-get install libgcc1 libqtgui4 libqt4-network libqt4-network libqtgui4 libstdc++6

```

---

### Post by saleki on 2011-11-09
Does anybody know if it is possible to join a conference call? Not to make one, but to join?

---

### Post by goldshirt9 on 2011-11-10
@ Sauen
from the terminal 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgcc1 is already the newest version.
libqt4-network is already the newest version.
libqtgui4 is already the newest version.
libstdc++6 is already the newest version.
The following packages were automatically installed and are no longer required:
  cups-pk-helper libcaribou0 gir1.2-upowerglib-1.0 gir1.2-gee-1.0
  gir1.2-telepathyglib-0.12 gir1.2-caribou-1.0 libboost-program-options1.46.1
  libboost-date-time1.46.1 libmozjs185-1.0 mutter-common caribou
  gir1.2-folks-0.6 gir1.2-polkit-1.0 gir1.2-gkbd-3.0 libmutter0
  gir1.2-telepathylogger-0.2 gnash-common gjs gir1.2-accountsservice-1.0
  libboost-thread1.46.1 gnash gir1.2-networkmanager-1.0 gir1.2-mutter-3.0
  libgjs0c
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and when i download the link , i get the same result as before.
it installs via the software manager ,( and it just gives the option to install again not the option to remove in the software manager )
shows in applications but when i click to run nothing happens at all .

---

### Post by goldshirt9 on 2011-11-10
sod it i have had enough.
have reinstalled Ubuntu and alls well

---

