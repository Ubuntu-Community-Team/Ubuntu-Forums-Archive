---
title: "Storage groups"
date: 2007-10-07
forum: Mythbuntu
---

### Post by darlomrh on 2007-10-07
HI,

Will Mythbuntu include storage groups or will I have to use LVM  for multiple drives in Mythtv?

Thanks in advance

---

### Post by tgm4883 on 2007-10-07
You can use storage groups with .21 of mythtv which has not been released yet.  You can run trunk which has weekly builds and will have storage groups available.  Instructions are at mythbuntu.org.

If .21 gets released soon it should be in mythbuntu

---

### Post by dragoster on 2007-10-08
How stable is trunk? I have a new hard drive and I don't want to mess with LVM either.

---

### Post by tgm4883 on 2007-10-08
I'm not going to quote any sort of information on the stability of trunk, because truck is by definition, unstable.  With that being said there are a few people who do run trunk.

---

### Post by dannyboy79 on 2007-10-08
so does mythbuntu weekly builds use svn trunk? I don't want to ahve to compile from source to get storage groups so I am only curious if I set my repo to mythbuntu weekly builds, is that using trunk?

---

### Post by tgm4883 on 2007-10-08
> **dannyboy79 said:**
> so does mythbuntu weekly builds use svn trunk? I don't want to ahve to compile from source to get storage groups so I am only curious if I set my repo to mythbuntu weekly builds, is that using trunk?

From mythbuntu.org
> Automated Weekly MythTV Trunk Builds
Explanation

Also, there have been requests for trunk builds of mythtv. Many users opt to use trunk for features only available in development versions. It is also a good way to help with MythTV testing. Please note that these builds are not as optimized as regular builds to make it easier to debug them, so you may run into performance problems. By using the trunk builds, you sacrifice the stability afforded by a regular release cycle. If you are currently on a regular release, backup your MySQL database prior to enabling trunk builds. There is no returning to regular releases after enabling trunk.
Enabling The Repository (trunk)

Follow these directions to add/enable the repository if you are intending to use the trunk branch:

1) Add the apt-key

    wget [http://mythbuntu.org/files/EEED06D0.gpg](http://mythbuntu.org/files/EEED06D0.gpg) && sudo apt-k.......

---

### Post by dannyboy79 on 2007-10-08
that's what I read as well and merely wanted to get superm1's word that the mythbuntu trunk is the same as the mythtv svn trunk. If this is true than it does have storage groups enabled in it correct. This is awesome!

Great work mythbuntu devs.

May I ask if anyone is actually using the mythbuntu trunk weekly builds? if so, any real issues that are show stoppers? I only really use mytharchive, mythvideo and mythdvd as my plugins.

---

### Post by superm1 on 2007-10-08
Well in case it's still not clear (although it should be from reading the site).

There are a variety of possible builds to install

[B]Feisty
[/B]On feisty you've got 4 options:
- archive.ubuntu.com, feisty
This is the 0.20.1 version of mythtv
- archive.ubuntu.com, feisty-updates
The is the 0.20.2 version of mythtv

- weeklybuilds/fixes
This is taken from the 0.20-fixes svn branch on mythtv.org.  This can be considered stable
- weeklybuilds/trunk
This is take from the 'trunk' branch on mythtv.org.  This is considered unstable

[B]Gutsy
[/B]On gutsy you've got 2 options:
- archive.ubuntu.com, gutsy
This is the 0.20.2 version of mythtv
- weeklybuilds/trunk
This is take from the 'trunk' branch on mythtv.org.  This is considered unstable


Once Gutsy is released, the feisty weekly builds will stop.  The weekly fixes builds will then be moved to Gutsy as well.

---

### Post by dragoster on 2007-10-09
I've switched to trunk last night. I had to reconfigure the backend and frontend but everything else worked fine. Storage groups are available and all I had to do is mount my new drive and add than mount location during mythtv backend setup. The only problem I have is that every time I restart the computer, gdm doesn't start and I have to reinstall the nvidia driver. After I reinstall the driver, and reconfigure xorg with the nvidia utility, I can restart gdm and it works fine. If I do a full restart it fails to start again. It's some conf file that didn't get updated correctly or something that points to a wrong conf file. t I haven't had time to butt heads with it but I'll post some logs after I play with it some more.

---

