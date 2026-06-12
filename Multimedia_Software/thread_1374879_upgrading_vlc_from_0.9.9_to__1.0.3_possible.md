---
title: "upgrading vlc from 0.9.9 to  1.0.3 possible?"
date: 2010-01-07
forum: Multimedia Software
---

### Post by gobbledigook on 2010-01-07
Hi!

I'm having trouble upgrading to the latest release of VLC! I'm running 9.10 on a machine which is mainly used as a file server, with XBMC running as a media centre on the telly :)

I have an .m2ts file which i would like to play... i understand that VLC 1.0.3 suppports this type quite well, with video stutter reduced by manipulating the frame-rate.

When i try ```
sudo apt-get install vlc
``` the error is that vlc is already the latest version? if i use ```
vlc --version
``` it is 0.9.9! I have purged, updated, then tried installing again and get the same version! i even tried using synaptic to see if the higher version was available through this!

I also tried downloading the src and installing, after ./configure the error i get for make and sudo make install is 'permission denied' ?

is the 1.0.3 vlc compatible with 9.10 server? am i missing something fundemental ;)

thanx!

dan

---

### Post by snowpine on 2010-01-07
See slakkie's excellent post below :)

---

### Post by slakkie on 2010-01-07
Seems like you have jaunty in your sources.list, since I'm unable to find 0.9.9 in karmic:

```

vlc:
  Installed: 1.0.3-1ubuntu2
  Candidate: 1.0.3-1ubuntu2
  Version table:
 *** 1.0.3-1ubuntu2 0
        990 http://archive.ubuntu.com lucid/universe Packages
        100 /var/lib/dpkg/status
     1.0.2-1ubuntu2.1 0
        990 http://archive.ubuntu.com karmic-proposed/universe Packages
     1.0.2-1ubuntu2 0
        990 http://archive.ubuntu.com karmic/universe Packages
     0.9.9a-2ubuntu1 0
        500 http://archive.ubuntu.com jaunty/multiverse Packages

```

Could you run lsb_release -a?

---

### Post by SlugSlug on 2010-01-07
Your best of adding the PPA 

instructions here:
[http://tuxarena.blogspot.com/2009/07/how-to-install-vlc-10-from-ubuntu-ppa.html](http://tuxarena.blogspot.com/2009/07/how-to-install-vlc-10-from-ubuntu-ppa.html)

---

### Post by fancypiper on 2010-01-07
> **SlugSlug said:**
> Your best of adding the PPA 

instructions here:
[http://tuxarena.blogspot.com/2009/07/how-to-install-vlc-10-from-ubuntu-ppa.html](http://tuxarena.blogspot.com/2009/07/how-to-install-vlc-10-from-ubuntu-ppa.html)This is for 9.04, for Ubuntu 9.10 see:

[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

---

### Post by Duck86 on 2010-01-08
> **fancypiper said:**
> This is for 9.04, for Ubuntu 9.10 see:

[https://launchpad.net/~c-korn/+archive/vlc]("https://launchpad.net/%7Ec-korn/+archive/vlc")


I tried that PPA and I got vlc 1.0.2 goldeneye, not 1.0.3

?

---

### Post by m0o on 2010-01-08
Use the [GetDeb]("http://www.getdeb.net/updates/ubuntu/9.10/#how_to_install") repositories, I currently have VLC 1.0.4 Goldeneye.

---

### Post by fancypiper on 2010-01-08
> **Duck86 said:**
> I tried that PPA and I got vlc 1.0.2 goldeneye, not 1.0.3

?Strange, I got vlc-1.0.3 on my box using that. The GetDeb repository installed vlc-1.0.4 which works OK so far with a quick test.

---

### Post by gobbledigook on 2010-01-10
Hi! and thanx for your helpful replies :)

Apologies for my late response!! 

@ slakkie: My noob error! i have just been upgrading the packages and NOT the distro! i found that when i do:

```
server@server:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty
```

so i did a dist-upgrade but it didn't seem to work??

after the upgrade and a reboot i still get the same response as above for ```
lsb_release -a
```

attached is my output from the upgrade... am i an idiot?!? d'oh!

Dan

---

### Post by gobbledigook on 2010-01-10
Ok... now i worked it out! 

upgraded package to 9.10 as per the [_**help page**_]("https://help.ubuntu.com/community/KarmicUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29") and upgraded vlc via apt-get :)

Still have the problem of it not playing .m2ts files though!! all i get is audio :(

---

### Post by sdowney717 on 2010-01-10
I downloaded a sony test file mt2s from rapidshare

It plays in VLC, gnome mplayer, smplayer, totem.
totem has video no sound

[http://rs447.rapidshare.com/files/317997026/hd_distributor_sony_pictures.m2ts](http://rs447.rapidshare.com/files/317997026/hd_distributor_sony_pictures.m2ts)

---

### Post by SlugSlug on 2010-01-11
> **gobbledigook said:**
> Hi! and thanx for your helpful replies :)

Apologies for my late response!! 

@ slakkie: My noob error! i have just been upgrading the packages and NOT the distro! i found that when i do:

```
server@server:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty
```so i did a dist-upgrade but it didn't seem to work??

after the upgrade and a reboot i still get the same response as above for ```
lsb_release -a
```attached is my output from the upgrade... am i an idiot?!? d'oh!

Dan


to upgrade to 9.10 you need to 

sudo do-release-upgrade

---

### Post by slakkie on 2010-01-11
> **gobbledigook said:**
> 
@ slakkie: My noob error! i have just been upgrading the packages and NOT the distro! i found that when i do:

so i did a dist-upgrade but it didn't seem to work??


You're not an idiot. dist-upgrade does not automaticly upgrade your release. You need to change your sources.list accordingly. Please have a look at the upgrade Ubuntu link in my sig. It will tell you all the possibilities on how to upgrade.

Assuming most of your packages are already from Karmic it will be a quick ride.

---

