---
title: "Vlc 1.0.0?"
date: 2009-07-12
forum: Multimedia Software
---

### Post by Roasted on 2009-07-12
I understand VLC 1.0.0 supports blu-ray playing. But I have 0.9.9 and that's the latest in the repos. I've tried installing the tar.gz of 1.0.0 and it didn't work... what can I do to get 1.0.0 installed?

---

### Post by anystupidname on 2009-07-12
[http://webupd8.blogspot.com/2009/07/install-vlc-100-final-in-ubuntu-arch.html](http://webupd8.blogspot.com/2009/07/install-vlc-100-final-in-ubuntu-arch.html)

> sudo sh -c "echo 'deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main' >> /etc/apt/sources.list" && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7613768D && sudo aptitude update && sudo aptitude upgrade && sudo aptitude install vlc vlc-plugin-esd mozilla-plugin-vlc

---

### Post by Ekeluo on 2009-07-12
I think and updated version is available in the medibuntu repos.

P.S. Not trying to advertise or some thing but ubuntu tweak ([http://ubuntu-tweak.com](http://ubuntu-tweak.com)) can help with these extra repository stuff.

---

### Post by Roasted on 2009-07-12
> **anystupidname said:**
> [http://webupd8.blogspot.com/2009/07/install-vlc-100-final-in-ubuntu-arch.html](http://webupd8.blogspot.com/2009/07/install-vlc-100-final-in-ubuntu-arch.html)

Wow. Really? I was kind of hoping there'd be an add on in the repos or something as opposed to a long string of commands, but alas, I'm trying it now.

---

### Post by drunk-wolf on 2009-07-12
is this safe, I just followed the instructions at that link and now when I try to update VLC in Synaptic I get a warning about malicious software and the potential for someone to take over my system, please tell me I didn't just install spyware or something like that, can a Mod please confirm that it's valid and safe, I don't understand what the "PPA" is, I've gotten the rest of my software through Synaptic and never had a problem till now.

New user and I'm really loving Ubuntu!!!

---

### Post by HappyFeet on 2009-07-12
Yes, PPA's are safe. I use them all the time. The "malicious software" warning is standard fare.

---

### Post by drunk-wolf on 2009-07-12
No it wasn't safe it screwed everything up I can't upgrade or reinstall or anything, all I get when I try is an error message of

vlc:
 Depends: vlc-nox but it is not going to be installed
  Depends: libc6 (>=2.8) but 2.8~20080505-0ubuntu9 is to be installed
  Depends: libgtk2.0-0 (>=2.16.0) but 2.14.4-0ubuntu1 is to be installed
 Depends: libvlccore2 but it is not going to be installed
 Depends: libx264-65 (>=1:0.svn20081230) but it is not installable

someone please help....

---

### Post by anystupidname on 2009-07-12
> **drunk-wolf said:**
> No it wasn't safe it screwed everything up I can't upgrade or reinstall or anything, all I get when I try is an error message of

vlc:
 Depends: vlc-nox but it is not going to be installed
  Depends: libc6 (>=2.8) but 2.8~20080505-0ubuntu9 is to be installed
  Depends: libgtk2.0-0 (>=2.16.0) but 2.14.4-0ubuntu1 is to be installed
 Depends: libvlccore2 but it is not going to be installed
 Depends: libx264-65 (>=1:0.svn20081230) but it is not installable

someone please help....

1) The warning is probably because the key didn't get imported properly. Are you perhaps behind a firewall that blocks TCP port 11371? The keys have to be manually imported in such a case...

2) Are you running jaunty? Lets see your /etc/apt/source.list

3) Depending on the answer to #2, you could try "sudo aptitude update && sudo aptitude -f"

---

### Post by drunk-wolf on 2009-07-12
no firewall that I'm aware of unless it's on by default.
running Intrepid (and used the code for intrepid from the site)
what will #3 do?? all I want at this point is it restored
and sorry about being impatient, just thought that the beginners section was the right place to ask about the restore point.

---

### Post by mc4man on 2009-07-12
> running Intrepid (and used the code for intrepid from the site)
But somehow you tried to install vlc 1.0 for jaunty, there is no 1.0 in that ppa for intrepid (0.9.9a is the intrepid version
> Depends: libvlccore2 but it is not going to be installed
libvlccore2 is only in vlc 1.0,, the other packages mentioned are also jaunty versions.
[B]
Did you try to install directly from the ppa? (vlc 1.0....
[/B]
If you did add the intrepid sources then just open synaptic package manager, search vlc and mark all for removal, apply, and then install ( mark and remove vlc, libvlc2, libvlccore0, vlc-data, and any plugins if installed.

If you inadvertently added the jaunty sources then remove them ( System -> Admin. -> Software sources -> third party. Then do above to go back to intrepid's vlc 0.9.4

---

### Post by drunk-wolf on 2009-07-12
Thank you so much! that fixed it, but I am curious, is there somewhere to get 1.0.0 for Intrepid?? I don't want to risk doing the switch to Jaunty just for a simple bug fix in VLC.

---

### Post by mc4man on 2009-07-12
> is there somewhere to get 1.0.0 for Intrepid??
Atm I haven't seen a ppa that has 1.0 for intrepid, but I'd expect something to show up, the package build of 1.0 isn't very much different for intrepid vs. jaunty.
Hardy on the other hand is a bit more difficult.

Otherwise you'd have to build your own version.


What version of 0.9.x did you end up with? (korn's 0.9.9a or the default 0.9.4

The 0.9.9a version is superior to intrepid's 0.9.4 which is one of the worst 0.9.x releases

---

### Post by drunk-wolf on 2009-07-13
I ended up with the 0.9.9a, seems to run fine, the only reason I wanted the update to 1.0.0 was for a bug fix so that it would properly display the band and song name while listening to internet radio stations.

---

### Post by guayusa on 2009-07-13
> **drunk-wolf said:**
> I ended up with the 0.9.9a, seems to run fine, the only reason I wanted the update to 1.0.0 was for a bug fix so that it would properly display the band and song name while listening to internet radio stations.


[B]
[https://launchpad.net/~moviemaniac/+archive/ppa](https://launchpad.net/~moviemaniac/+archive/ppa)[/B]

this PPA has vlc - 1.0.0~rc2-1~ppa1~intrepid2 - which works fine for me.

[RIGHT]):P[/RIGHT]

---

