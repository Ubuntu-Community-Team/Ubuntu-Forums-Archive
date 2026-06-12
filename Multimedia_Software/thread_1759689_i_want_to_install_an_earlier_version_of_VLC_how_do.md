---
title: "i want to install an earlier version of VLC how do i do that?"
date: 2011-05-16
forum: Multimedia Software
---

### Post by shantiq on 2011-05-16
ok simple situation    the sound on 1.1.9 is giving me grief on Natty the sync is out between all audio and vid ( and not on other programs )and i have tried everything so i now want to try an earlier version   say 1.1.4

but whatever i do it reloads the 1.1.9

how can i make sure to install 1.1.4 or even earlier anything that is really stable on my machine


ps   i have had all version of 1.1.9 development and synaptic

any clever suggestions   probably a deb    but how do i make sure it does not go and get that blasted 1.1.9


thanx



ps2   i have flushed all 1.1.9 out of /var/cache/apt/archives


ps3    of course i am aware that it might not be 1.1.9's fault but this is a sure way to find out

---

### Post by matthewbpt on 2011-05-16
Get the download from one of these urls, click the mirror closest to you.

[http://packages.ubuntu.com/maverick-updates/i386/vlc/download](http://packages.ubuntu.com/maverick-updates/i386/vlc/download) vlc 1.1.4 for 32 bit
[http://packages.ubuntu.com/maverick-updates/amd64/vlc/download](http://packages.ubuntu.com/maverick-updates/amd64/vlc/download) vlc 1.1.4 for 64 bit

After installing one of those you want to lock the version so it doesn't update itself to the new one, follow the guide here [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by shantiq on 2011-05-16
> **matthewbpt said:**
> Get the download from one of these urls, click the mirror closest to you.

[http://packages.ubuntu.com/maverick-updates/i386/vlc/download](http://packages.ubuntu.com/maverick-updates/i386/vlc/download) vlc 1.1.4 for 32 bit
[http://packages.ubuntu.com/maverick-updates/amd64/vlc/download](http://packages.ubuntu.com/maverick-updates/amd64/vlc/download) vlc 1.1.4 for 64 bit

After installing one of those you want to lock the version so it doesn't update itself to the new one, follow the guide here [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)


Thanx Matthew will give that a whirl

---

### Post by mc4man on 2011-05-16
> will give that a whirl
good luck with that, - you'll likely need at least the corresponding vlc-nox package, probably an earlier libx264 also

To do properly you should gather all the same version packages that make up a min vlc in debian/ubuntu (6), libx264 if needed  and use dpkg on the lot of them

You could build the 1.1.4 source or just use the 1.2 dev version which works quite well here and is a superior version, either self- built or from the [Videolan Master ppa]("https://launchpad.net/~videolan/+archive/master-daily")

---

### Post by Lars Noodén on 2011-05-16
Also look at [apt pinning](https://help.ubuntu.com/community/PinningHowto).  That will let you still use the packagemanager.

---

### Post by shantiq on 2011-05-16
ok went for the [https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily) in the end and still the same

lag between audio and video    no idea what it is been there for three days now and not on other players


weird:KS    and other times it works  computers amaze me supposed to be logical they indeed seldom are:KS

---

