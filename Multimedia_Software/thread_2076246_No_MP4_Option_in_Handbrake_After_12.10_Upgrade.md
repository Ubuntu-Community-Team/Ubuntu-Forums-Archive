---
title: "No MP4 Option in Handbrake After 12.10 Upgrade"
date: 2012-10-25
forum: Multimedia Software
---

### Post by cabbage on 2012-10-25
Hi,

Since upgrading to 12.10 I no longer have the option to rip to mp4 in handbrake (it only gives me the MKV option).

I've checked all the restricted packages are still installed and re-added the quantal medibuntu ppa and upgraded.

This used to work in 12.04.

Anyone know whats broke in 12.10 that would cause this?


Thanks...

---

### Post by JohnAStebbins on 2012-10-26
> **cabbage said:**
> Hi,

Since upgrading to 12.10 I no longer have the option to rip to mp4 in handbrake (it only gives me the MKV option).

I've checked all the restricted packages are still installed and re-added the quantal medibuntu ppa and upgraded.

This used to work in 12.04.

Anyone know whats broke in 12.10 that would cause this?


Thanks...
It appears that somebody decided it would be a good idea to put a crippled version of HandBrake in the official repository for 12.10.  There are certain libraries used by HandBrake that cause packagers gastrointestinal discomfort.  So they just stripped them out (along with some very core functionality).

It also appears that their version numbering scheme causes the version that I publish in my PPA to be superseded by theirs ](*,)

You might try the snapshots PPA until I can unravel this f'n mess #-o.
These are nightly builds of svn code which have different versioning and shouldn't be superseded by the "official" repository package.
[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by cabbage on 2012-10-26
Thanks John!

The snapshot version works perfectly.

Hope you manage to get things sorted with the packages...

---

### Post by rotorcraig on 2012-11-26
Thanks John; I was struggling with the same problem but the snapshot works great for me too.

---

