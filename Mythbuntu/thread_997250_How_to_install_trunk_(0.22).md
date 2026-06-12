---
title: "How to install trunk (0.22)?"
date: 2008-11-29
forum: Mythbuntu
---

### Post by lionsnob on 2008-11-29
With the weekly trunk repositories not yet running in 8.10, what is the best way to install 0.22 on Intrepid?  Can one simply install the 8.04 binaries on an 8.10 system?  If so, how can I do that?  Or is compiling from source the best way?

Thanks!

---

### Post by ian dobson on 2008-11-30
Hi,

Why do yo want to run the bleeding edge code? If you don't have a very good reason to even attempt to install/configure trunk just stick with the version that apt-get offers you.

Have a look here [http://ph.ubuntuforums.com/showthread.php?t=813101](http://ph.ubuntuforums.com/showthread.php?t=813101)
and [http://patrick.wagstrom.net/tutorials/mythTV64/mythTV64.xml](http://patrick.wagstrom.net/tutorials/mythTV64/mythTV64.xml) it's abit out of date but it's a starting point.

Regards
Ian Dobson

---

### Post by lionsnob on 2008-11-30
Thanks for the links.  No desire to use bleeding edge specifically, but I would like to use my HD-PVR, which I believe you need 0.22 to use.

---

### Post by ian dobson on 2008-11-30
Hi,

Here's a link you should read:-

[http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR)

> Configuring the HD-PVR in MythTV 
MythTV SVN Trunk now includes support for the HD-PVR. While it is **_still strongly recommended _**that the average user not switch to the Myth development branch, advanced users of Myth and Linux are invited to participate in development and bug squashing of the HD-PVR driver and its support in MythTV. With a few caveats, the HD-PVR can now be expected to work reliably for scheduled recordings.

I ran the trunk for a while and gave up as there was almost always something broken, and the dev's were not always very helpfull.

Regards
Ian Dobson

---

### Post by lionsnob on 2008-12-05
> **ian dobson said:**
> Hi,

Here's a link you should read:-

[http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/index.php/Hauppauge_HD-PVR)



I ran the trunk for a while and gave up as there was almost always something broken, and the dev's were not always very helpfull.

Regards
Ian Dobson

Hi Ian,

I ended up installing 0.22 on a 8.04.1 install using [this repo]("https://launchpad.net/~mythbuntu-trunk-0.22/+archive").  The machine is a test machine, so if it blows up I don't care.  I installed the HD-PVR drivers as instructed from your link above.  The hardest part was figuring out how to use my serial IR blaster, but I figured that out.

While that repo does not provide plugins, the "normal" MythWeb from the weekly fixes repo works fine with it apparently.  After the recordings are done, I move them to an NFS share which contains MythVideo files for the remote front ends.  Right now this is manual, but I'll automate it soon and post that script when it's complete.

All in all, it works well!  I need to tweak the bitrate on the HD-PVR, as right now it's only set to 6.5, but I'd like to try 10.5 to see if that works okay.  I'm anxiously awaiting the production release of 0.22 and maybe in the future the inclusion of the HD-PVR driver in a Mythbuntu release.

---

