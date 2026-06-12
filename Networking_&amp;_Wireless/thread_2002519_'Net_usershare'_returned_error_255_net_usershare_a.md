---
title: "'Net usershare' returned error 255: net usershare add: cannot convert name &quot;everyone&quot;"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by quatoria on 2012-06-12
Hi.

Quick background. I am writing this on Mint linux because it works. (ubuntu doesn't)

The machine I am trying to create a share on was ubuntu 10.10 which worked, however grub broke three times a year for no reason and I had to reinstall once because 9.04 broke it. However I stayed away from 11.04 onwards because the UI was god awful. Now as 10.10 is obselete I am forced to try the latest, so it is running 12.04 LTS

It is a clean and fresh, complete new install via a disk of 11.10 and then an upagrde via the update route.

I have now 44 tabs open with possible solutions to fix the issue. Absolutely none of which address the actual writing in the error message.
None of which come close to fixing the problem and the error message persists.

I have used linux since 8.04 and this is the last incarnation that I will be using as it is now bloated and broken. And I can't stand the god awful new UI that gets shipped with it so unless they release a version of quick way to remove it completely I can't use ubuntu.

I have worked in IT for 14 years and am quite comfortable messing with files.

This particular problem has taken 3.5 hours of my time today and two weeks over the last month. (It started on 11.10)

The basic problems

1. WHY in the 21st century do you still need to install as an addition  network sharing on a linux distro? Why is not standard? What lunacy makes people have it as an "Added download" because my computer asked to install SAMBA after a fresh clean install.

2. The error message states clearly that "everyone" is involved and nearly every link talks about guest shares and wins and all that malarky when an entry in some file somewhere in Ubuntu Must mention group permissions of "everyone" or ubuntu wouldn't reference it. Hardly any actually mention net share at all, most point to smb.conf and I have tried and edited all of them that I can find.

Network wise the machine can be 'seen' and 'see' everything, I can go to other shares fine. This a permissions thing not a network visibilty thing.

I am a full admin and I don't really care where the folder share is, I just want a shared folder as this machine is meant to be a stand alone media server and so far it can't even be that.

All I want is to share a folder so I can copy files to the machine. Nothing fancy, just a place to copy and past files. In ubuntu it seems to be so difficult.

Thankyou in advance.

EDIT
Fourth time for install and uninstall SAMBA GUI from the unbuntu software centre (remember it wasn't installed as default) and I set up a share.

Can't see it from any machine despite being correctly setup and visible.

However on linux mint if I type 'nautilus smb://192.168.0.5/temp' I can open the share, but the terminal is filled with a load of errors.

When I do this I get on the ubuntu machine a load of pop up windows saying "System program problem detected" So it suggests Ubuntu really is broken from a clean fresh install.

---

