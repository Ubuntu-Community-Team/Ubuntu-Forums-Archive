---
title: "Installing Maverick with Wubi"
date: 2010-06-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mer on 2010-06-29
I have a laptop which is notoriously unfriendly to Linux (HP TouchSmart tm2t), but I wanted to track its progress through Maverick and maybe report some hardware bugs. Currently, I can't find a way to make a Wubi installation with 10.10. The 10.04 wubi installer doesn't recognize the 10.10 iso (even after I renamed it 'ubuntu-10.04-desktop-amd64.iso'). I even tried to install an unannounced test release from here [http://people.canonical.com/~evand/wubi/maverick/](http://people.canonical.com/~evand/wubi/maverick/)
but no luck. Has anyone actually done this? Perhaps this is not the right place to ask... if someone could direct me to the right person to talk to, that would be great too!

---

### Post by joshmuffin on 2010-06-29
I'm pretty sure the only way would be install 10.04 then upgrade

---

### Post by bcbc on 2010-06-29
wubi.exe has a built in check for the latest release. This is 10.04 (it wouldn't consider an alpha for obvious reasons?)
There is an override to skip this check (--skipmd5check), in which case it should use the .iso it finds in the same folder as wubi.exe.

My understanding is that if you run it from a cd it will respect the version on the CD, but I could be wrong.

---

### Post by wilee-nilee on 2010-06-29
> **bcbc said:**
> wubi.exe has a built in check for the latest release. This is 10.04 (it wouldn't consider an alpha for obvious reasons?)
There is an override to skip this check (--skipmd5check), in which case it should use the .iso it finds in the same folder as wubi.exe.

My understanding is that if you run it from a cd it will respect the version on the CD, but I could be wrong.

I installed from a thumb loaded with maverick but it downloaded Lucid when installing, I didn't know about the command.

---

### Post by bcbc on 2010-06-29
what does it do if you disable the internet?

---

### Post by philinux on 2010-06-29
[http://ubuntuforums.org/showthread.php?t=1479694](http://ubuntuforums.org/showthread.php?t=1479694)

---

### Post by wilee-nilee on 2010-06-29
> **bcbc said:**
> what does it do if you disable the internet?

I thought the same thing, I will have to remove the one installed and test that.

---

### Post by mer on 2010-06-29
First of all, thanks for all the replies! I read this [http://ubuntuforums.org/showthread.php?t=793840]("http://ubuntuforums.org/showthread.php?t=793840") thread, and it looks like there is a logfile created in /%temp%/. When I read its contents, it seems that besides the md5 check, wubi also checks the listed version, sub-version, code name, and architecture of the distro in the iso file. This happens even if you burn a cd and try to install from there. There may be a way to change these properties in the iso. It also shouldn't be too hard to find these strings in the source code of wubi. Perhaps there is a --SkipVersionCheck switch of some sort that has gone undocumented.

---

### Post by bcbc on 2010-06-29
try the --isopath option.

I think the distro is built in the wubi.exe so it may or may not accept this. We might have to wait until someone creates a new version for maverick.

---

### Post by bcbc on 2010-06-29
> **bcbc said:**
> try the --isopath option.

I think the distro is built in the wubi.exe so it may or may not accept this. We might have to wait until someone creates a new version for maverick.

FYI this doesn't work.

Wubi.exe checks the .disk/info file on the .iso image and makes sure it matches what's saved in wubi.exe (different versions for differents releases), then it tries to download one if there is no match. If there is no internet connection to download, it exits.

What I am trying... I mounted and copied the maverick alpha iso, modified the .disk/info file to say it was 10.04 and then recreated the .iso. Then I ran wubi.exe again.

It's installing now - so I got it past the first part. I'll report back on the result later.

PS even if this works, it's not a very practical workaround :) so I suppose we'll have to wait until they include a 'maverick' wubi.exe on the cd images.

---

### Post by bcbc on 2010-06-29
It works... but still, what a waste of time :)

I won't bother publishing exactly what I did unless someone is interested... but fyi I used this resource [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) for changing and recreating the iso.

---

### Post by mer on 2010-07-02
Ok thanks guys! Maybe I'll try making a Maverick version over the weekend. If you say it works without changing anything except the strings, it really shouldn't be very hard.

---

### Post by bcbc on 2010-07-02
> **mer said:**
> Ok thanks guys! Maybe I'll try making a Maverick version over the weekend. If you say it works without changing anything except the strings, it really shouldn't be very hard.

The alpha2 has a wubi.exe so you shouldn't need to do anything special to get it to run. I haven't tried it, but assume it works as it wasn't on alpha1.

---

