---
title: "Mythtv - Who has had a good or bad installation"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by williammanda on 2007-02-15
I have tried several installs of Mythtv using the package method on Ubuntu / Kubuntu. I have only come close to Mythtv working correctly and that did not last very long. I would like to hear from anyone about their experience concerning installing Mythtv. My hope is to build some kind of centralized information so others will not fall into the same shortcoming I have. I would love to get Mythtv working on Ubuntu / Kubuntu because I really like the OS. But for now my myth machine is running knoppmyth, which Mythtv works but I can't really use the computer for anything else. Please post your replys so we may all benefit.
Thanks

---

### Post by cerbie on 2007-02-15
[http://www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150](http://www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150)

I used that guide, and, last night, got my first ever working MythTV install (the only bug was I had to stop and start the service, as restart didn't work). It doesn't have the channels named in the program guide, but everything else worked (using a PVR-150).

---

### Post by punx45 on 2007-02-15
you can't exit out of myth frontend on KnoppMyth?   I did a MythDora install, and I can escape out of myth frontend into a standard Fedora KDE desktop.

---

### Post by williammanda on 2007-02-15
you can't exit out of myth frontend on KnoppMyth? I did a MythDora install, and I can escape out of myth frontend into a standard Fedora KDE desktop.

Yes I did that but the KDE I got then wasn't as good as what I get in Edgy or Feisty. I'm a new user to linux and trying to hit the ground running with the command line is crazy. I need a good gui and that's what I like about Ubuntu.

I biggest problem with these installs are that I can't login as mythtv user. I have to sudo mythbackend and mythtv-setup. Also I had to install the latest DVB drivers to get my pcHDTV-5500 to work for HDTV. The wierd thing about that was that my fusion HDTV5 rt gold card worked without updating the DVB driver. Another thing is that in general, the install just doesn't seem real stable. I can't give you examples now but I don't experience flaky things when running knoppmyth. Lastly, there seems to be missing info concerning the database during the install. During several of the installs I couldn't get into mythtv-setup because it couldn't open the database mythconverg. I had to do the following:
mysql > mc.sql (I believe that's right). Once I did that, it worked. That's all for now.
Thanks

---

### Post by Yoooder on 2007-02-15
I've had mixed success with MythTV.  My first install didn't go so well (but it was my first time in Ubuntu and MythTV) however I managed to figure out what I needed to do, so I formatted my machine and did it again the correct way.

This installation worked well, however my video card hadn't had a fan on it for nearly two years and when I installed the nVidia drivers it would occasionly freeze the machine entirely (but it still works with the nv driver :guitar: ).  When I rebooted from one of the lock-ups MythTV's MySQL database was beyond repair.

I've since managed to reinstall MythTV (without reinstalling Ubuntu) and it has been working quite well, except that I'm still having some minor issues resulting from my database being blown up.

---

### Post by williammanda on 2007-02-15
Yoooder
What install instructions did you use?
Thanks

---

### Post by kingborel on 2007-02-15
I used these instructions:

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

They worked great for me, and with a little digging I had a functonal MythTV box :D

---

### Post by Yoooder on 2007-02-15
> **williammanda said:**
> Yoooder
What install instructions did you use?
Thanks

I used the same as kingborel.  It's good, however it links to several other tutorials (for remotes, video cards, etc... and if you try to follow them in the stated order there will be problems.

Here's my recommendation:
 - Follow the tutorial, but DONT setup anything other than MythTV and maybe your video card drivers
 - After you have MythTV working, move into the other tutorials (I used the PVR-350 TV-out and lirc tutorials) and work through them one at a time.


Here's a couple of the more specific hurdles I faced with that tutorial:
 - LIRC - I downloaded a config file for my PVR-350's Hauppauge remote, and lirc wouldn't start with it.  After some digging I found that the config file actually had several configurations in it (just had to delete the others)

 - PVR-350 TV-out.  The tutorial for this is intended to setup your machine to run X entirely on your TV.  I wanted to have only my TV shows show on my TV and still have use of my monitor.  The trick is to follow the tutorial, but not to modify your xorg.conf file, instead just ensure that you have the ivtv-fb module loaded.

---

### Post by ill0gical0ne on 2007-02-15
Every time that I've installed mythtv or any other tv service, it works... but it's apparent that the drivers are messed up, as the hardware encoding is not enabled, and the video looks like shythe. Anyone else have this problem, and end up resolving it?

For reference, I have 2 Hauppauge PVR-150s.

---

### Post by williammanda on 2007-02-15
Doing my nightly mythtv install and I have run into this the last few times:
william@PIV-2-8:~$ sudo apt-get install mythtv-frontend mythtv-backend
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv-backend: Depends: libjack0.80.0-0 (>= 0.99.0) but it is not installable
                  Depends: libmyth-0.20 but it is not going to be installed
                  Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable
                  Depends: transcode but it is not going to be installed
  mythtv-frontend: Depends: libjack0.80.0-0 (>= 0.99.0) but it is not installable
                   Depends: libmyth-0.20 but it is not going to be installed
                   Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable
E: Broken packages

I have all the repositories set. Any ideas?
Thanks

---

### Post by barney_1 on 2007-02-16
> **williammanda said:**
> Doing my nightly mythtv install and I have run into this the last few times:
william@PIV-2-8:~$ sudo apt-get install mythtv-frontend mythtv-backend
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv-backend: Depends: libjack0.80.0-0 (>= 0.99.0) but it is not installable
                  Depends: libmyth-0.20 but it is not going to be installed
                  Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable
                  Depends: transcode but it is not going to be installed
  mythtv-frontend: Depends: libjack0.80.0-0 (>= 0.99.0) but it is not installable
                   Depends: libmyth-0.20 but it is not going to be installed
                   Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable
E: Broken packages

I have all the repositories set. Any ideas?
Thanks

This first thing I would do is try to install using the "fix broken" flag -f.  I prefer to use this guide for the install:
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

To install from the command line with the fix broken try this:
```
sudo apt-get install -f mysql-server mythtv-frontend mythtv-backend mythtv-database
```
If that doesn't do it for you aptitude might help:
```
sudo apt-get install aptitude
```
```
sudo aptitude install mysql-server mythtv-frontend mythtv-backend mythtv-database
```

---

### Post by williammanda on 2007-02-16
Thanks for the reply!
I tried your other solution but I can get only some of the files and it gives me a real low score. Any other ideas?
Thanks

---

### Post by williammanda on 2007-02-16
I see another thread trying to resolve one of the mythtv install problems - no database access due to the mythtv user creation.

[http://www.ubuntuforums.org/showthread.php?t=362732](http://www.ubuntuforums.org/showthread.php?t=362732)

---

### Post by Chewiesw on 2007-02-16
I am having a bit of a nightmare installation, I have been following the guides for a complete system.(front,backend and desktop) and I get this error

**could not connect to the masterbackend server -- is it running? Is the IP address set for it in the setup program correct?**
 
I tried everything suggested in the guide, looked on every forum I could find till my nose bled ,with no luck so far.

As you might guess I am a noob so it is either a case of RTFM or missed something out

Not giving up yet

---

### Post by williammanda on 2007-02-16
Another post conerning installation problem:
Database error
[http://www.ubuntuforums.org/showthread.php?t=359463](http://www.ubuntuforums.org/showthread.php?t=359463)

---

### Post by williammanda on 2007-02-16
Post concerning fixing stuttering video and audio. The fix was loading nvidia drivers, adjusting vxmc setting and agp setting.
[http://www.ubuntuforums.org/showthread.php?t=348352](http://www.ubuntuforums.org/showthread.php?t=348352)

---

### Post by williammanda on 2007-02-16
Chewie
I would verify that the backend server is runing by starting it in terminal and waiting for it to say woke up by user or something to that effect (this would be as the mythtv user). Then start the frontend again. Also if that doesn't work try sudo mythbackend, then start the frontend. This assumes your ip address is still set to 127.0.0.1 in the backend setup.
Thanks

---

### Post by williammanda on 2007-02-16
Conerning the driver update I would get the most up to date version 1.0-9746 when trying to fix the video / audio problem.

---

### Post by superm1 on 2007-02-16
> **barney_1 said:**
> This first thing I would do is try to install using the "fix broken" flag -f.  I prefer to use this guide for the install:
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

To install from the command line with the fix broken try this:
```
sudo apt-get install -f mysql-server mythtv-frontend mythtv-backend mythtv-database
```If that doesn't do it for you aptitude might help:
```
sudo apt-get install aptitude
``````
sudo aptitude install mysql-server mythtv-frontend mythtv-backend mythtv-database
```
Do you have a third party repository in your list that might be providing these other versions of packages perhaps?  Or you did at one point?

---

### Post by williammanda on 2007-02-16
Yes I did use another repository. The standard ones had no mythtv. I used multi-media.org. Please explain why these repositories wouldn't have mythtv? (I just did a fresh kubuntu install, didn't touch anything except for the upgrade Nvidia driver to 1.0-9746).
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

I did:
sudo apt-get update
sudo apt-get upgrade

When I try to install mythtv:
william@PIV-2-8:/etc/apt$ sudo apt-get install mythtv
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-database (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is to be installed
          Depends: mythtv-frontend (= 0.20-0.2ubuntu2) but it is not going to be installed
          Depends: mythtv-backend (= 0.20-0.2ubuntu2) but it is not going to be installed
E: Broken packages

The results when I use the broken route:
william@PIV-2-8:/etc/apt$ sudo apt-get install -f mythtv
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-database (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is to be installed
          Depends: mythtv-frontend (= 0.20-0.2ubuntu2) but it is not going to be installed
          Depends: mythtv-backend (= 0.20-0.2ubuntu2) but it is not going to be installed
E: Broken package

The results when I try this route:
william@PIV-2-8:/etc/apt$ sudo aptitude install mythtv
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  mythtv mythtv-backend mythtv-frontend
The following NEW packages will be automatically installed:
  jackd kakasi-dic libarchive-zip-perl libauthen-sasl-perl libavc1394-0
  libclass-methodmaker-perl libconvert-binhex-perl libcrypt-ssleay-perl
  libdate-manip-perl libdigest-hmac-perl libdigest-sha1-perl
  libemail-address-perl libemail-find-perl libemail-valid-perl
  libexporter-lite-perl libfcgi-perl libfont-afm-perl libhtml-format-perl
  libhtml-fromtext-perl libhtml-parser-perl libhtml-tableextract-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cache-transparent-perl
  libiec61883-0 libio-socket-ssl-perl libio-stringy-perl libjack0.100.0-0
  libkakasi2 liblame0 liblingua-preferred-perl liblircclient0
  liblog-tracemessages-perl libmailtools-perl libmime-lite-perl
  libmime-perl libmyth-0.20 libnet-dns-perl libnet-domain-tld-perl
  libnet-ip-perl libnet-jabber-perl libnet-ssleay-perl libnet-xmpp-perl
  libossp-uuid-perl libossp-uuid13 libqt3-mt-mysql libregexp-common-perl
  libsoap-lite-perl libterm-progressbar-perl libterm-readkey-perl
  libtext-kakasi-perl libtie-ixhash-perl libtimedate-perl
  libunicode-string-perl liburi-perl libwww-mechanize-perl libwww-perl
  libxml-libxml-common-perl libxml-libxml-perl libxml-namespacesupport-perl
  libxml-parser-perl libxml-sax-perl libxml-stream-perl libxml-twig-perl
  libxml-writer-perl libxml-xpath-perl libxmltv-perl mythtv-themes
  xmltv-util
The following NEW packages will be installed:
  jackd kakasi-dic libarchive-zip-perl libauthen-sasl-perl libavc1394-0
  libclass-methodmaker-perl libconvert-binhex-perl libcrypt-ssleay-perl
  libdate-manip-perl libdigest-hmac-perl libdigest-sha1-perl
  libemail-address-perl libemail-find-perl libemail-valid-perl
  libexporter-lite-perl libfcgi-perl libfont-afm-perl libhtml-format-perl
  libhtml-fromtext-perl libhtml-parser-perl libhtml-tableextract-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cache-transparent-perl
  libiec61883-0 libio-socket-ssl-perl libio-stringy-perl libjack0.100.0-0
  libkakasi2 liblame0 liblingua-preferred-perl liblircclient0
  liblog-tracemessages-perl libmailtools-perl libmime-lite-perl
  libmime-perl libmyth-0.20 libnet-dns-perl libnet-domain-tld-perl
  libnet-ip-perl libnet-jabber-perl libnet-ssleay-perl libnet-xmpp-perl
  libossp-uuid-perl libossp-uuid13 libqt3-mt-mysql libregexp-common-perl
  libsoap-lite-perl libterm-progressbar-perl libterm-readkey-perl
  libtext-kakasi-perl libtie-ixhash-perl libtimedate-perl
  libunicode-string-perl liburi-perl libwww-mechanize-perl libwww-perl
  libxml-libxml-common-perl libxml-libxml-perl libxml-namespacesupport-perl
  libxml-parser-perl libxml-sax-perl libxml-stream-perl libxml-twig-perl
  libxml-writer-perl libxml-xpath-perl libxmltv-perl mythtv-themes
  xmltv-util
0 packages upgraded, 72 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.8MB of archives. After unpacking 93.7MB will be used.
The following packages have unmet dependencies:
  mythtv-frontend: Depends: mythtv-common (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is installed.
  mythtv: Depends: mythtv-database (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is installed.
  mythtv-backend: Depends: mythtv-common (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mythtv [Not Installed]
mythtv-backend [Not Installed]
mythtv-frontend [Not Installed]
mythtv-themes [Not Installed]

Score is 26

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
william@PIV-2-8:/etc/apt$

Please advise
Thanks

---

### Post by superm1 on 2007-02-17
> **williammanda said:**
> Yes I did use another repository. The standard ones had no mythtv. I used multi-media.org. Please explain why these repositories wouldn't have mythtv? (I just did a fresh kubuntu install, didn't touch anything except for the upgrade Nvidia driver to 1.0-9746).
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

I did:
sudo apt-get update
sudo apt-get upgrade

When I try to install mythtv:
william@PIV-2-8:/etc/apt$ sudo apt-get install mythtv
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-database (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is to be installed
          Depends: mythtv-frontend (= 0.20-0.2ubuntu2) but it is not going to be installed
          Depends: mythtv-backend (= 0.20-0.2ubuntu2) but it is not going to be installed
E: Broken packages

The results when I use the broken route:
william@PIV-2-8:/etc/apt$ sudo apt-get install -f mythtv
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-database (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is to be installed
          Depends: mythtv-frontend (= 0.20-0.2ubuntu2) but it is not going to be installed
          Depends: mythtv-backend (= 0.20-0.2ubuntu2) but it is not going to be installed
E: Broken package

The results when I try this route:
william@PIV-2-8:/etc/apt$ sudo aptitude install mythtv
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  mythtv mythtv-backend mythtv-frontend
The following NEW packages will be automatically installed:
  jackd kakasi-dic libarchive-zip-perl libauthen-sasl-perl libavc1394-0
  libclass-methodmaker-perl libconvert-binhex-perl libcrypt-ssleay-perl
  libdate-manip-perl libdigest-hmac-perl libdigest-sha1-perl
  libemail-address-perl libemail-find-perl libemail-valid-perl
  libexporter-lite-perl libfcgi-perl libfont-afm-perl libhtml-format-perl
  libhtml-fromtext-perl libhtml-parser-perl libhtml-tableextract-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cache-transparent-perl
  libiec61883-0 libio-socket-ssl-perl libio-stringy-perl libjack0.100.0-0
  libkakasi2 liblame0 liblingua-preferred-perl liblircclient0
  liblog-tracemessages-perl libmailtools-perl libmime-lite-perl
  libmime-perl libmyth-0.20 libnet-dns-perl libnet-domain-tld-perl
  libnet-ip-perl libnet-jabber-perl libnet-ssleay-perl libnet-xmpp-perl
  libossp-uuid-perl libossp-uuid13 libqt3-mt-mysql libregexp-common-perl
  libsoap-lite-perl libterm-progressbar-perl libterm-readkey-perl
  libtext-kakasi-perl libtie-ixhash-perl libtimedate-perl
  libunicode-string-perl liburi-perl libwww-mechanize-perl libwww-perl
  libxml-libxml-common-perl libxml-libxml-perl libxml-namespacesupport-perl
  libxml-parser-perl libxml-sax-perl libxml-stream-perl libxml-twig-perl
  libxml-writer-perl libxml-xpath-perl libxmltv-perl mythtv-themes
  xmltv-util
The following NEW packages will be installed:
  jackd kakasi-dic libarchive-zip-perl libauthen-sasl-perl libavc1394-0
  libclass-methodmaker-perl libconvert-binhex-perl libcrypt-ssleay-perl
  libdate-manip-perl libdigest-hmac-perl libdigest-sha1-perl
  libemail-address-perl libemail-find-perl libemail-valid-perl
  libexporter-lite-perl libfcgi-perl libfont-afm-perl libhtml-format-perl
  libhtml-fromtext-perl libhtml-parser-perl libhtml-tableextract-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cache-transparent-perl
  libiec61883-0 libio-socket-ssl-perl libio-stringy-perl libjack0.100.0-0
  libkakasi2 liblame0 liblingua-preferred-perl liblircclient0
  liblog-tracemessages-perl libmailtools-perl libmime-lite-perl
  libmime-perl libmyth-0.20 libnet-dns-perl libnet-domain-tld-perl
  libnet-ip-perl libnet-jabber-perl libnet-ssleay-perl libnet-xmpp-perl
  libossp-uuid-perl libossp-uuid13 libqt3-mt-mysql libregexp-common-perl
  libsoap-lite-perl libterm-progressbar-perl libterm-readkey-perl
  libtext-kakasi-perl libtie-ixhash-perl libtimedate-perl
  libunicode-string-perl liburi-perl libwww-mechanize-perl libwww-perl
  libxml-libxml-common-perl libxml-libxml-perl libxml-namespacesupport-perl
  libxml-parser-perl libxml-sax-perl libxml-stream-perl libxml-twig-perl
  libxml-writer-perl libxml-xpath-perl libxmltv-perl mythtv-themes
  xmltv-util
0 packages upgraded, 72 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.8MB of archives. After unpacking 93.7MB will be used.
The following packages have unmet dependencies:
  mythtv-frontend: Depends: mythtv-common (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is installed.
  mythtv: Depends: mythtv-database (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is installed.
  mythtv-backend: Depends: mythtv-common (= 0.20-0.2ubuntu2) but 0.20-0.3sarge1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mythtv [Not Installed]
mythtv-backend [Not Installed]
mythtv-frontend [Not Installed]
mythtv-themes [Not Installed]

Score is 26

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
william@PIV-2-8:/etc/apt$

Please advise
Thanks
Okay what you need to do is "purge" all of these broken myth packages.

Don't mix and match debian packages with ubuntu packages.  You run into troubles like this.  Once you purge all these packages, you can check your policy to make sure that you are only getting the ubuntu ones

```
apt-cache policy mythtv-frontend
```
should see this:
supermario@portablemario:~$ apt-cache policy mythtv-frontend
```
mythtv-frontend:
  Installed: 0.20-0.2ubuntu2
  Candidate: 0.20-0.2ubuntu2
  Version table:
 ***   0.20-0.2ubuntu2 0
        500 http://archive.ubuntu.com edgy/multiverse Packages

```

If you really want the newer packages that will be going into feisty, i have built them for edgy.  See [http://home.eng.iastate.edu/~superm1/](http://home.eng.iastate.edu/~superm1/) for more information about setting up the repository.

---

### Post by williammanda on 2007-02-18
Thanks for your reply!
I did as you requested and got one computer setup as a combined frontend, backend, and desktop. I'm working on finishing another frontend. I have run into a problem. I got the 2nd frontend setup and working. Watch tv for about 10 minutes and the video and audio froze. Soon after that the masterbackend computer froze. I was able to reboot the 2nd frontend properly but I had to use the reset button on the masterbackend computer. When I restarted mythbackend and started viewing the 2nd frontend I got this error message in the termianl window (where I started the master backend):
2007-02-18 14:47:30.766 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1501' , '2007-02-18T14:47:27' , '75' , 9 , '5884400' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired
Also do you have a quide for setting up a masterbackend? I followed all I know from the mythtv wiki.
Thanks

---

### Post by jimbat on 2007-02-19
I setup Mythtv on an old P3 800mhz on friday evening and had almost no problems.  I have most of the extra plugins installed and working  and even the ir remote setup worked ok, which i expected to be quite challenging.

I am using a Hauppauge Nova-T and followed this setup guide:

[Mythtv Ubuntu]("http://parker1.co.uk/mythtv_ubuntu.php")

I doubt the above guide will help you with your current problem but i thought i would post my experience anyway.

Good Luck

Jimbat

---

### Post by jethro10 on 2007-02-19
> **jimbat said:**
> I setup Mythtv on an old P3 800mhz on friday evening and had almost no problems.  I have most of the extra plugins installed and working  and even the ir remote setup worked ok, which i expected to be quite challenging.

I am using a Hauppauge Nova-T and followed this setup guide:

[Mythtv Ubuntu]("http://parker1.co.uk/mythtv_ubuntu.php")

I doubt the above guide will help you with your current problem but i thought i would post my experience anyway.

Good Luck

Jimbat
Hi,
Can you tell me how much processing time % is being used when recording via this software card?
Ta
J

---

### Post by jimbat on 2007-02-19
> **jethro10 said:**
> Hi,
Can you tell me how much processing time % is being used when recording via this software card?
Ta
J

Hi

Just to clarify i have checked exact specs (I was at work earlier today and was guessing) my cpu is a P3 866MHz 256M RAM Onboard Sound/Graphics.

Top reports that cpu usage fluctuates between 10% and 20% whilst recording, the unit was running basic ubuntu X, top, SSH server, myth-backend and mythweb.

If I am watching the program whilst i record it cpu usage is between 60% and 70%.

I Hope this answers your query

Jimbat

---

### Post by williammanda on 2007-02-19
Another good post: How to fix your mythconverg database.

[http://www.ubuntuforums.org/showthread.php?t=365155](http://www.ubuntuforums.org/showthread.php?t=365155)

---

