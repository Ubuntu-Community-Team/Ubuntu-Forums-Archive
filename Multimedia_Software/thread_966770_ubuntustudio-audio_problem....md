---
title: "ubuntustudio-audio problem..."
date: 2008-11-01
forum: Multimedia Software
---

### Post by jackgu1988 on 2008-11-01
I installed today ubuntu studio over ubuntu 8.10 and when I try to install packages that require ubuntustudio-audio... well I just can't... So I try to remove ubuntustudio-audio... and I can't!!! :(

> jack@jack-laptop:~$ sudo apt-get remove ubuntustudio-audio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  ubuntustudio-audio
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 53.2kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 257398 files and directories currently installed.)
Removing ubuntustudio-audio ...
Traceback (most recent call last):
  File "/usr/share/ubuntustudio-audio/rtprio.py", line 3, in <module>
    import changesettings
ImportError: No module named changesettings
dpkg: error processing ubuntustudio-audio (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/share/ubuntustudio-audio/rtprio.py", line 3, in <module>
    import changesettings
ImportError: No module named changesettings
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

I also tried synaptic but still nothing... I am confused... what should I do?

---

### Post by jackgu1988 on 2008-11-01
help! please somebody help! I tried > sudo dpkg -r ubuntustudio-audio that I found in another thread but did not help... aaaaaaaaaaaaaa

---

### Post by jackgu1988 on 2008-11-02
anybody?:(

---

### Post by TakensM on 2010-05-31
Hi i had the same problem , the error you receive is a python error .. it cannot find the module changesettings , in my case this module was found in:

/usr/lib/python2.6/dist-packages/changesettings.py

i copied it to :

/usr/share/ubuntustudio-audio , it runs the script rtprio.py from this directory and since it could not find module changesettings ... we have just placed it in here ;-) it will now execute the script rtprio.py  normally 

and executed the command:

sudo apt-get purge ubuntustudio-audio

takens@MTLIN01:/usr/lib/python2.6/dist-packages$ sudo apt-get purge ubuntustudio-audio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libtalloc1 libice-dev x11proto-xext-dev xulrunner-1.9.1 libaudio-dev libglib2.0-dev libicu40 libkadm5clnt-mit7
  xulrunner-1.9.1-gnome-support libsad2 libgail-common libcvaux1 x11proto-xinerama-dev comerr-dev x11proto-render-dev
  libindicate-gtk1 linux-rt-headers-2.6.31-9 libdns53 libxi-dev libxmu-headers libxrender-dev libcompress-bzip2-perl lmms-vst
  libaudutil1 libass3 libservlet2.4-java libkrb5-dev librasqal1 libboost-thread1.38.0 libkadm5clnt6 libglu1-xorg-dev
  libpng12-dev libisccc50 libsqlite0-dev libcdio7 libgssrpc4 libfontconfig1-dev libx264-67 redland-utils libgssdp-1.0-1
  libxcursor-dev liblwres50 libkpathsea4 x11proto-randr-dev krb5-multidev dkms libxt-dev libxmu-dev libxext-dev libpolkit-dbus2
  libjline-java kvm libbind9-50 firefox-3.5-gnome-support linux-headers-2.6.31-9-rt libxtrap6 python-rsvg libffado1
  libfreetype6-dev x11proto-fixes-dev libcv1 xlibmesa-gl-dev libgdata5 libprojectm2 xfs libhighgui1 liblcms1-dev libpq-dev
  libkadm5srv-mit7 libisccfg50 libxrandr-dev libgupnp-1.0-2 libexpat1-dev rhino libqt4-phonon libxklavier15 libprojectm-data
  libpq5 libindicate3 libxft-dev libkdb5-4 libxfixes-dev libisc50 libmng-dev mplayer-nogui libxinerama-dev python-virtinst
  libpolkit2 libntfs-3g54 libfaac0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ubuntustudio-audio*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 61.4kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 213035 files and directories currently installed.)
Removing ubuntustudio-audio ...
@audio          -       rtprio          99


et voila it was gone from my system and i copuld reinstall it without a problem :D

i also attached th changesettings.py in case you dont find it on your system.. i hope this works for you !

regards

Maarten

---

### Post by NoneMoreBlack on 2010-08-27
Hi

I was having the same problem uninstalling Ubuntustudio-audio. I used the solution above and got an error saying that rtprio.py wasn't found in /usr/share/ubuntustudio-audio. I moved the file there and now get the following error:


Traceback (most recent call last):
  File "/usr/share/ubuntustudio-audio/rtprio.py", line 18, in <module>
    rtprio.rm_setting()
  File "/usr/share/ubuntustudio-audio/changesettings.py", line 80, in rm_setting
    self.rm_list.remove(self.remove_string)
ValueError: list.remove(x): x not in list
dpkg: error processing ubuntustudio-audio (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)


I don't know what this means, so any help would be greatly appreciated.

Thanks in advance

---

### Post by rcrath on 2010-09-10
I had this problem and takensm's solution did not work.  I think it is because I manually added the rtprio line to /etc/security/limits/conf at one point and then the python script could no longer find it.  Anyway, since I just want to reinstall the ubuntu studio audio programs over again, and the python script seemed to choke on the last section, I just commented that out and the packages uninstalled fine.

Specifically, I went to /usr/share/ubuntustudio-audio, backed up rtprio.py opened it in gedit with root privileges (```
gksudo gedit /usr/share/ubuntustudio-audio/rtprio.py
```)

and commented out (by placing "#" at the beginning of each line) everything from the line "#Instance the setting we want to change" to the end so that the script no longer looked for those settings:

```
#Instance the setting we want to change
#rtprio = changesettings.ChangeSettings('/etc/security/limits.conf', '@audio\s*-\s*rtprio\s*\d*', '@audio          -       rtprio          99\n')

#if options.install:
#  rtprio.ch_setting()
#elif options.remove:
#  rtprio.rm_setting()
```

then I reinstalled the packages with no problems.
You might need to add the appropriate lines to #Instance the setting we want to change as described [here]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu"), but I still had the settings in my limits.conf file.

---

