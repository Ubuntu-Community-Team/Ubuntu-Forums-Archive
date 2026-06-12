---
title: "mythtv 0.26"
date: 2012-12-23
forum: Mythbuntu
---

### Post by Old Jimma on 2012-12-23
Hi Community:

I'm using 12.04 LTS and have MythTV 0.25 installed.

MythTV 0.26 has been released.

Is there any advantage for upgrading to 0.26?
Any disadvantages?

How can I upgrade?

Thanks,
Old Jimma

---

### Post by diskmaster23 on 2012-12-26
> **Old Jimma said:**
> Hi Community:
Is there any advantage for upgrading to 0.26?
Any disadvantages?


Not sure if this will help you, but here are the release notes for 0.26. [http://www.mythtv.org/wiki/Release_Notes_-_0.26]("http://www.mythtv.org/wiki/Release_Notes_-_0.26")

---

### Post by N00b-un-2 on 2012-12-26
I ran .26 on my MythBuntu box for a while.  It was okay and nice to be on the "bleeding edge" of software, but it dropped support for one of my analog TV tuner cards (not a big deal since we only get digital content here.  Can't vouch for the rest of the world though) and it did seem as though the frontend was a bit more prone to crashing on .26 than .24.

I would stick with .24 if I were you unless there is some pressing reason you need to upgrade

---

### Post by Old Jimma on 2012-12-28
Hi Community:

Here is how I upgraded from MythTV 0.25 to 0.06:

> 
sudo apt-get update
sudo add-apt-repository ppa:mythbuntu/0.26 
sudo apt-get update


Then, synaptic wanted to know if I wanted to update everything, and I let it do its thing...

To confirm I was running 0.26 I ran

> mythfrontend --version

A description of this type of upgrade path is at: 

> [http://www.ubuntuupdates.org/ppa/mythtv_0.26]("http://www.ubuntuupdates.org/ppa/mythtv_0.26")

I hope this helps other folks!

:)

Old Jimma, the Eldest
From the Old Country

(Where have all the Holerith cards gone, long time passing?)

---

