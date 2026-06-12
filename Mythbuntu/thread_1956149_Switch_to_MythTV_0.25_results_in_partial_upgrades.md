---
title: "Switch to MythTV 0.25 results in partial upgrades"
date: 2012-04-10
forum: Mythbuntu
---

### Post by koma77 on 2012-04-10
I switched my 11.10 mythbuntu to 0.25-repos in hope to switch to the new release of MythTV.

However, update manager warned of a "partial install" being possible - something that means that there are inconsitencies in the repo...

Is my repository messed up, or what's going on?

---

### Post by tgm4883 on 2012-04-10
> **koma77 said:**
> I switched my 11.10 mythbuntu to 0.25-repos in hope to switch to the new release of MythTV.

However, update manager warned of a "partial install" being possible - something that means that there are inconsitencies in the repo...


No it does not. It may indicate an issue with the repository, but may just indicate new dependencies.

> 
Is my repository messed up, or what's going on?

Run it from the terminal (apt-get update && apt-get dist-upgrade) and see what it is trying to do. Most likely, it's just new dependencies that need to be installed (via the apt-get dist-upgrade)

---

### Post by ZedThou on 2012-04-10
This is what I get after selecting 0.25, does everything look okay to proceed?

```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libmyth-0.24-0 mythtv-theme-childish mythtv-theme-metallurgy mythtv-themes mythvideo
The following NEW packages will be installed:
  avahi-daemon libavahi-compat-libdnssd1 libavahi-core7 libio-socket-inet6-perl libmyth-0.25-0 libnss-mdns
  libsocket6-perl libva-glx1 php-mythtv python-urlgrabber
The following packages will be upgraded:
  libmyth-python libmythtv-perl mytharchive mythbrowser mythgallery mythgame mythmusic mythnetvision mythnews
  mythplugins mythtv mythtv-backend mythtv-backend-master mythtv-common mythtv-database mythtv-dbg mythtv-frontend
  mythtv-theme-mythbuntu mythtv-transcode-utils mythweather mythweb
21 upgraded, 10 newly installed, 5 to remove and 0 not upgraded.
Need to get 182 MB of archives.
After this operation, 80.0 MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

---

### Post by tgm4883 on 2012-04-10
> **ZedThou said:**
> This is what I get after selecting 0.25, does everything look okay to proceed?

```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libmyth-0.24-0 mythtv-theme-childish mythtv-theme-metallurgy mythtv-themes mythvideo
The following NEW packages will be installed:
  avahi-daemon libavahi-compat-libdnssd1 libavahi-core7 libio-socket-inet6-perl libmyth-0.25-0 libnss-mdns
  libsocket6-perl libva-glx1 php-mythtv python-urlgrabber
The following packages will be upgraded:
  libmyth-python libmythtv-perl mytharchive mythbrowser mythgallery mythgame mythmusic mythnetvision mythnews
  mythplugins mythtv mythtv-backend mythtv-backend-master mythtv-common mythtv-database mythtv-dbg mythtv-frontend
  mythtv-theme-mythbuntu mythtv-transcode-utils mythweather mythweb
21 upgraded, 10 newly installed, 5 to remove and 0 not upgraded.
Need to get 182 MB of archives.
After this operation, 80.0 MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

yep

---

### Post by andreask73 on 2012-04-30
Would it be possible to remove the packages libmyth-0.24-0 mythtv-theme-childish mythtv-theme-metallurgy mythtv-themes mythvideo and then upgrade via apt-get upgrade or apt-get install?

I can't do dist-upgrade, because it will try to upgrade my linux kernel and I can't do that because the kernel I have has special support for my TV-cards, and I don't want to recompile the kernel just now. I would like to do a quick upgrade as opposed to upgrading my entire environment.

// Andréas

---

### Post by tgm4883 on 2012-04-30
> **andreask73 said:**
> Would it be possible to remove the packages libmyth-0.24-0 mythtv-theme-childish mythtv-theme-metallurgy mythtv-themes mythvideo and then upgrade via apt-get upgrade or apt-get install?

I can't do dist-upgrade, because it will try to upgrade my linux kernel and I can't do that because the kernel I have has special support for my TV-cards, and I don't want to recompile the kernel just now. I would like to do a quick upgrade as opposed to upgrading my entire environment.

// Andréas

That should be fine, although you will need to also install libmyth-0.25-0. If it's still has held back myth related packages after that, just apt-get install the package and it should pull in the dependencies it needs.

---

### Post by andreask73 on 2012-05-01
> **tgm4883 said:**
> That should be fine, although you will need to also install libmyth-0.25-0. If it's still has held back myth related packages after that, just apt-get install the package and it should pull in the dependencies it needs.

Thanks!

Tried it and my system is now running mythtv 0.25!

// Andréas

---

