---
title: "I dont get it: Play files local files"
date: 2008-03-25
forum: Mythbuntu
---

### Post by .gurkburk on 2008-03-25
Im having a very basic problem it seems.
Im not interested in the tv-card function in mythbuntu, all I really want is a decent GUI for playing movies and music. Anyways, on with my problem.

I have installed mythbuntu, got the remote etc working, so faar so good, I can juggle around in the menys etc.

I have 2 directories that I wanto play videos from, /mnt/media1 and /mnt/media2. 
Ive made a symlink to /mediafiles which seems to be working.
(I can go to /mediafiles in a terminal, and there I can see 2 directories, "media1" and "media2", I can also 'cd' into these, and see all the subdirectories and videos etc.

Now, this is what I have tried to do in the myth-interface to set it up properly.

*Utilities/setup* **->** *setup* **->** *media settings* **->** *videos settings* **->** *general settings* **->** "Directory that holds videos: /mediafiles"
Now, this doesnt work.
When I go into *Media library* **->** *Watch videos*it simply states "no files found"

I first had /mediafiles set to root as when I made the directory, then read somewhere from googling and forumsearching on this topic that mythbuntu needed this directory to be set to the user used by the interface, so I did
sudo chown -R mythtv:mythtv /mediafiles

didnt help though.

Any idea's or help?
Something tells me the solution is to simple, since I cant find a solution while searching...

Oh well, thanks in advance :)

---

### Post by jeffus_il on 2008-03-25
Look in the Myth menus, you have to scan the directories to populate the database.

---

### Post by .gurkburk on 2008-03-25
> **jeffus_il said:**
> Look in the Myth menus, you have to scan the directories to populate the database.

I started looking for something similiar to a scan, and found that if I went into "manage videos", it initially makes a "database update", and this solved my problem!
Thanks alot, as soon as I got that done, I can browse my folders, see the videos and playback with sound works like a charm! :)

---

