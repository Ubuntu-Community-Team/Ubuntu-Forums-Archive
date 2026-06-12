---
title: "Problem getting w32codecs"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by walkerx on 2006-06-26
I'm trying to get hold of the w32codecs, so I can use Kaffeine with success, as currently it won't decode the audio for my dvb-t stick, but will decode the video.

when i run sudo apt-get update i get the following
[size="1"] sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Errhttp://packages.freecontrib.org dapper/free Packages
  404 Not Found
Errhttp://packages.freecontrib.org dapper/non-free Packages
  404 Not Found
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Fetched 6B in 0s (8B/s)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/bin](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/bin) ary-amd64/Packages.gz  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free) /binary-amd64/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.[/size]

and unsure why it can't find the freecontrib stuff, as further up it says 'hit'.

when that was finished i tried to get the codecs, but got the following

[size="1"]sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate[/size]

am i doing something wrong or have i missed something out

any help appreciated as noob to Ubuntu

thanks
walkerx

---

### Post by vayu on 2006-06-26
I think you can get it in libdvdread3

[http://ubuntuguide.org/wiki/Dapper#How_to_install_DVD_playback_capability]("http://ubuntuguide.org/wiki/Dapper#How_to_install_DVD_playback_capability")

---

### Post by scxtt on 2006-06-26
try adding:
[indent]# $ gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# $ gpg --export --armor 33BAC1B3 | sudo apt-key add -
# w32codecs, etc
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main[/indent]to your /etc/apt/sources.list

---

### Post by walkerx on 2006-06-26
after adding that into the sources file and running apt-get update it returns the following

[size="1"]Errhttp://packages.freecontrib.org dapper/free Packages
  404 Not Found
Errhttp://packages.freecontrib.org dapper/non-free Packages
  404 Not Found
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Get: 7 [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release.gpg [189B]
Hit [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release
Errftp://cipherfunk.org dapper Release

Get: 8 [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release [1387B]
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release
Get: 9 [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper/main Packages
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper/main Packages
Get: 10 [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper/main Packages
Errftp://cipherfunk.org dapper/main Packages
  Unable to fetch file, server said ‘No such file.  ’
Fetched 1582B in 7s (198B/s)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-amd64/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-amd64/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-amd64/Packages.gz](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-amd64/Packages.gz)  Unable to fetch file, server said ‘No such file.  ’
Reading package lists... Done
W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/size]

this is what my sources file looks like at mo

[size="1"]# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531.2)]/ dapper main restricted
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531.2)]/ dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

# $ gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# $ gpg --export --armor 33BAC1B3 | sudo apt-key add -
# w32codecs, etc
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main[/size]

not sure if this is correct or not - not sure if mentioned or if anyone noticed with other post I'm using the amd64bit version

also libdvdread3 is installed as can play dvd's fine, can play xvid files but again with no sound

regards
walkerx

---

### Post by scxtt on 2006-06-26
try running:
[indent]# $ gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# $ gpg --export --armor 33BAC1B3 | sudo apt-key add -[/indent]in a terminal window - that'll import the GPG keys for cipherfunk - which can't hurt ... any reason you don't use synaptic? (i definately like using the command line, but i like using synaptic to manage packages) ...

---

### Post by walkerx on 2006-06-26
when run the first command i get

[size="1"]gpg: requesting key 33BAC1B3 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
[/size]

was just as easy to try via console, as was already open for testing dvb stuff etc

---

