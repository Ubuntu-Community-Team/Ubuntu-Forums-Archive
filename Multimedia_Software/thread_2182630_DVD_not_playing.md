---
title: "DVD not playing"
date: 2013-10-21
forum: Multimedia Software
---

### Post by Camilia on 2013-10-21
I have in the past been able to play DVDs. I put in a DVD, which is from NetFlix. Prompt appears to ask me what to do. I click on MPlayer and a picture with mplayer appears. Area to start video is up. I click on it and nothing happens.

Are there some other programs to download?

---

### Post by QIII on 2013-10-21
Hi!

What has changed since you were last able to play DVDs?

---

### Post by Camilia on 2013-10-21
Only do updates.

Tried sudo dpkg -l ubuntu-restricted-extras and got
No packages found matching ubuntu-restricted-extras.

---

### Post by QIII on 2013-10-21
Sounds like you need to install it.  Did you just recently upgrade to a new version?

---

### Post by speartip on 2013-10-22
If you have ubuntu-restricted-extras, libdvdread4 & libdvdcss2 installed you should be good to go. The last package is not in the repos though. You need to download & install the .deb from here:
[http://download.videolan.org/ubuntu/precise/](http://download.videolan.org/ubuntu/precise/)

---

### Post by Camilia on 2013-10-22
> **speartip said:**
> If you have ubuntu-restricted-extras, libdvdread4 & libdvdcss2 installed you should be good to go. The last package is not in the repos though. You need to download & install the .deb from here:
[http://download.videolan.org/ubuntu/precise/](http://download.videolan.org/ubuntu/precise/)
My son-in-law put the os on this computer. I just put the updates on it. I went to the link. I am confused as to which 1 to download. My OS type is 32 bit. Went to the Ubuntu software store and downloaded the restricted extras. Still nothing happens when I click on play.

I downloaded movie player. The put in the DVD. I got this message: 
Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.

In terminal pasted sudo apt-get install ubuntu-restricted-extras again. Result:
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 78 not upgraded.

Tried sudo apt-get install w32codecs non-free-codecs and result:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 
--2013-10-22 11:46:50--  [http://www.medibuntu.org/sources.list.d/precise.list](http://www.medibuntu.org/sources.list.d/precise.list)
Resolving [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org](www.medibuntu.org))... 88.191.127.22
Connecting to [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org)|88.191.127.22|:80](www.medibuntu.org)|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-10-22 11:46:51 ERROR 404: Not Found.

sudo apt-get install libdvdread4
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

 sudo /usr/share/doc/libdvdread4/install-css.sh
--2013-10-22 11:49:07--  [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'
Dynamic fetch failed; Falling back to static fetch
--2013-10-22 11:49:07--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'

---

### Post by speartip on 2013-10-22
You need libdvdcss2 installed.
Go to the link in my last post, the package you want is libdvdcss2_1.2.13.0_i386.deb.
Download the package, right click it & open with ubuntu software centre.

---

### Post by Camilia on 2013-10-22
> **speartip said:**
> You need libdvdcss2 installed.
Go to the link in my last post, the package you want is libdvdcss2_1.2.13.0_i386.deb.
Download the package, right click it & open with ubuntu software centre.
Right click gives me option to open link. Left click ask me to save it. I saved it to a flash drive. Left clicked it and it opened ubuntu software center. Installed it and now it is playing the movie.

Thank you Thank you

---

### Post by speartip on 2013-10-22
Once installed you should be good to go.
Post back if it solved your problem.

---

### Post by oscarivera9 on 2013-11-11
> **speartip said:**
> Once installed you should be good to go.
Post back if it solved your problem.

I didn't start the thread but I've got a similar problem.  I used to have no problems watching DVDs before, but now I can't watch some of them.
I actually do have restricted-extras, libdvdread4 & libdvdcss2 all installed in my system but I still can't get the same functionality that I had before.  I even made sure that I had the latest libdvdcss2 installed and I do, I've got version 1.2.13 but I'm still getting problems.  I hope someone can help us.

---

### Post by oscarivera9 on 2013-11-16
I found out that Medibuntu is no longer being maintained, hence the problems with libdvdcss2.  After removing the Medibuntu repositories from my software sources and adding the vlc videolan repository given below, everything went back to normal.

This is what I added to my software sources:
> deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /

 deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /

And this is how to get the current version:

> wget -O - [http://download.videolan.org/pub/debian/videolan-apt.asc|sudo](http://download.videolan.org/pub/debian/videolan-apt.asc|sudo) apt-key add -

   libdvdcss

---

