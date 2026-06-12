---
title: "VLC installation problem"
date: 2017-02-21
forum: Multimedia Software
---

### Post by zkab on 2017-02-21
I have Ubuntu 16.04.2 LTS (4.4.0-63).
When I try to install VLC I get this ... how can I fix it ?

$ sudo apt install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: libgles1-mesa (>= 7.8.1) but it is not going to be installed or
                libgles1
E: Unable to correct problems, you have held broken packages.

---

### Post by mc4man on 2017-02-21
You could start with these & take from there - 
```
apt-cache policy libgles1-mesa
```
```
sudo apt install libgles1-mesa
```

---

### Post by zkab on 2017-02-22
OK - but it didn't work ...

[HTML]raivo@zkab:~$ sudo apt-cache policy libgles1-mesa
libgles1-mesa:
  Installed: (none)
  Candidate: 17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~xenial
  Version table:
     17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~xenial 500
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) xenial/main amd64 Packages
     12.0.6-0ubuntu0.16.04.1 500
        500 [http://ftp.lysator.liu.se/ubuntu](http://ftp.lysator.liu.se/ubuntu) xenial-updates/main amd64 Packages
     11.2.0-1ubuntu2 500
        500 [http://ftp.lysator.liu.se/ubuntu](http://ftp.lysator.liu.se/ubuntu) xenial/main amd64 Packages
raivo@zkab:~$ sudo apt install libgles1-mesa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgles1-mesa : Depends: libglapi-mesa (= 17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~xenial) but 17.0.0~git20170212+17.0.e81e2846-0ubuntu0ricotz~xenial is to be installed
E: Unable to correct problems, you have held broken packages.
[/HTML]

---

### Post by Rick St. George on 2017-02-22
Since I see the E: at the bottom, it usually means to me that it cannot access the needed files. Make sure, when you goto Software & Updates, goto the Ubuntu Software Tab and select both Universe and Multiverse (not sure which one these files are located in). 

Then let it update. You could then Run in Terminal;
```
sudo apt-get install vlc
```

Hope this helps!
Rick

---

### Post by zkab on 2017-02-22
I have them both ... still get the error

```
raivo@zkab:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: libgles1-mesa (>= 7.8.1) but it is not going to be installed or
                libgles1
E: Unable to correct problems, you have held broken packages.

```

---

### Post by mc4man on 2017-02-22
> **zkab said:**
> OK - but it didn't work ...

raivo@zkab:~$ sudo apt-cache policy libgles1-mesa
libgles1-mesa:
  Installed: (none)
  Candidate: 17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~xenial
  Version table:
     17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~xenial 500
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) xenial/main amd64 Packages

The following packages have unmet dependencies:
 libgles1-mesa : Depends: libglapi-mesa (= 17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~xenial) but 17.0.0~git20170212+17.0.e81e2846-0ubuntu0ricotz~xenial is to be installed

Wasn't meant to "do" anything but acquire some info which shows - 
You're using the xorg-edgers ppa. 
The latest mesa build **there** no longer has libgles1 in proper package version, it's now libgles2 only (libgles2-mesa_17.0.0~git20170212+17.0.e81e2846-0ubuntu0ricotz~xenial

It appears vlc needs both...

You can either  - 
Try updating your source & running an update
Contact the ppa maintainer & inquire as to this situation. 

Or best bet -
 Use ppa-purge on the xorg-edgers ppa to go back to repo version packages. 
Then add this ppa for the stable 17.0 release which contains both libgles1-mesa & libgles2-mesa in same package versions
[https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)

---

### Post by RAMChYLD on 2017-02-24
I'd like to report that I'm having the same issues since last week. I need to use Xorg-edgers because of my very specific NVidia GPU setup that the Xorg in the normal Ubuntu repos doesn't seem to like.

Since last week I've been having issues with vlc, same error message regarding libgles1-mesa. 

Since I can't find a fix to it, I decided to take the risk and download said offending package, tweak the package to accept a newer libglapi-mesa dependency, and repackage. This is a risky move as symbols may no longer add up, but I figure that since it was just bugfixes and still the same major version, the ABI changes are minimal to none, and the worst that could happen is that VLC segfaults. 

Following instructions that I found online, I downloaded and unpacked the package, and add one character to the Depends field:

I changed
```
Depends: libglapi-mesa (= 17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~yakkety), libc6 (>= 2.2.5)
```
to
```
Depends: libglapi-mesa (>= 17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~yakkety), libc6 (>= 2.2.5)
```

I also tweaked the version number to reflect the minor fix.

I then repackaged and proceeded to use dpkg to install it. I then installed vlc and tested it, and it appears to work fine.

So yeah. If you're willing to take the risk, this appears to work. But YMMV.

---

### Post by zkab on 2017-02-25
OK - I made a ppa-purge on the xorg-edgers ppa and then 'sudo update; sudo apt install vlc' ... voila it worked.

---

### Post by jotadeaa on 2017-06-04
> **RAMChYLD said:**
> I'd like to report that I'm having the same issues since last week. I need to use Xorg-edgers because of my very specific NVidia GPU setup that the Xorg in the normal Ubuntu repos doesn't seem to like.

Since last week I've been having issues with vlc, same error message regarding libgles1-mesa. 

Since I can't find a fix to it, I decided to take the risk and download said offending package, tweak the package to accept a newer libglapi-mesa dependency, and repackage. This is a risky move as symbols may no longer add up, but I figure that since it was just bugfixes and still the same major version, the ABI changes are minimal to none, and the worst that could happen is that VLC segfaults. 

Following instructions that I found online, I downloaded and unpacked the package, and add one character to the Depends field:

I changed
```
Depends: libglapi-mesa (= 17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~yakkety), libc6 (>= 2.2.5)
```
to
```
Depends: libglapi-mesa (>= 17.0.0~git20170206+17.0.07571cd8-0ubuntu0ricotz~yakkety), libc6 (>= 2.2.5)
```

I also tweaked the version number to reflect the minor fix.

I then repackaged and proceeded to use dpkg to install it. I then installed vlc and tested it, and it appears to work fine.

So yeah. If you're willing to take the risk, this appears to work. But YMMV.

Could you please share the tweaked pakage?

---

