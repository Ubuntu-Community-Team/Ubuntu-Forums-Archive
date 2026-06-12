---
title: "libdvdread4/install-css.sh says &quot;command not found&quot;"
date: 2011-09-08
forum: Multimedia Software
---

### Post by Rebelli0us on 2011-09-08
I'm trying to get Ubuntu to play DVD movies:

```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh

```

This has worked fine on several machines, but on this system the **2nd** command returns "command not found"! The script file is there. Any ideas?

---

### Post by dniMretsaM on 2011-09-08
Make sure the script is executable.

If that doesn't work, try this:
```
sudo apt-get install libdvdread4[FONT=monospace]
[/FONT]sudo /usr/share/doc/libdvdread4/install-css.sh
```You might have to install libdvdread4 separately from the *buntu-restricted-extras package. I know I did.

---

### Post by Rebelli0us on 2011-09-08
> **dniMretsaM said:**
> Make sure the script is executable.

If that doesn't work, try this:
```
sudo apt-get install libdvdread4[FONT=monospace]
[/FONT]sudo /usr/share/doc/libdvdread4/install-css.sh
```You might have to install libdvdread4 separately from the *buntu-restricted-extras package. I know I did.


Thank you, script is executable and libdvdread4 is already installed.

---

### Post by Rebelli0us on 2011-09-08
So, repeating the command works:


```

$ **sudo /usr/share/doc/libdvdread4/install-css.sh**
sudo: command not found

$ **sudo apt-get install libdvdread4**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ **sudo /usr/share/doc/libdvdread4/install-css.sh**
sudo: command not found

$ **sudo apt-get install libdvdread4**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ **sudo /usr/share/doc/libdvdread4/install-css.sh**
--2011-09-08 17:19:36--  http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8021 (7.8K) [text/plain]
Saving to: `/tmp/dvdcss-DABeQn/Packages'

100%[======================================>] 8,021       --.-K/s   in 0.1s    

2011-09-08 17:19:37 (52.7 KB/s) - `/tmp/dvdcss-DABeQn/Packages' saved [8021/8021]

--2011-09-08 17:19:37--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38080 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-DABeQn/libdvdcss.deb'

100%[======================================>] 38,080      84.6K/s   in 0.4s    

2011-09-08 17:19:43 (84.6 KB/s) - `/tmp/dvdcss-DABeQn/libdvdcss.deb' saved [38080/38080]

Selecting previously deselected package libdvdcss2.
(Reading database ... 164133 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-DABeQn/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
$ 

```


Thank you... free is free :)

---

### Post by dniMretsaM on 2011-09-08
That's really odd. Anyway, glad it worked for you! Please mark as solved.

---

### Post by stanley82 on 2012-01-23
Thanks the scripts ran so now I have codecs and flash player but cnn.com still tells me to ge flash player.  Thanks any way.  Ian.

---

