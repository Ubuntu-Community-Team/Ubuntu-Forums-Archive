---
title: "Installed Jya's updates and now mythfrontend segfaults"
date: 2009-11-08
forum: Mythbuntu
---

### Post by frego on 2009-11-08
I'm running Mythbuntu 9.04.  I just installed the latest updates (I do have 3rd party repos enabled such as JYa) and now mythfrontend segfaults.  The updates weren't entirely successful, just partial success.  

I'm getting messages like this for multiple packages:
```
Preparing to replace mythgame 2:0.21.0+fixes-svn22228-jya-0ubuntu0 (using .../mythgame_2%3a0.22.0-fixes22775-0ubuntu1_amd64.deb) ...
Unpacking replacement mythgame ...
dpkg: error processing /var/cache/apt/archives/mythgame_2%3a0.22.0-fixes22775-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/share/mythtv/themes/default-wide/game-ui.xml', which is also in package mythtv-common
```

I get above messages for mytharchive-data, mythgallery, mythgame, mythmusic.

Other packages are being left behind.  It looks like I'm updating something out of order perhaps due to having JYA's repos on.  Any way of either rolling things back or fixing what's gone wrong?

---

### Post by xinix on 2009-11-08
> I get above messages for mytharchive-data, mythgallery, mythgame, mythmusic.

I'd try removing the plugins and updating the core mythtv packages first.  Then I'd install the plugins.

---

### Post by frego on 2009-11-08
Thanks!  That definitely got me moving in the right direction.  I removed those four packages, then tried the upgrade, it still said being held back so I then did a dist-upgrade, which seemed to pull in the new mythtv-common.  And then I added the other four packages.  All seemed to be going well, but the mythfrontend is just a black screen and unresponsive.  Upon reading JYa's webpage, it looks like I should've done my reading first!  I think I need to switch my theme, but without getting into the frontend that's rather hard.  Does anyone know if that is held in a config file somewhere or is that in the database?  Or any other ideas on what I should do?  I'm considering a fresh install to 9.10 anyhow.  So no biggee either way.  Thanks!

---

### Post by xinix on 2009-11-08
If mythweb is working you can do it there.
go to, [http://localhost/mythweb/settings/mythtv](http://localhost/mythweb/settings/mythtv) ,make sure "Edit settings for:" (in the top right) is set to the machines host.  one of the options will be for the theme.  

Or, if you remove the theme it's trying to load, mythtv should switch to the default.  That has been my experience.

---

### Post by dano1 on 2009-11-09
go through myth control center. ny osd themes wil work i believe.

hth, danny

---

### Post by xinix on 2009-11-09
OSD themes are still compatible.  It's the regular themes that you need to make sure they are 0.22+ compatible.

---

### Post by frego on 2009-11-10
Thanks for the help guys.  I ended up doing a fresh install.  I wanted to check out 9.10 anyhow.  I'm loving mythvideo with the meta info!!

---

