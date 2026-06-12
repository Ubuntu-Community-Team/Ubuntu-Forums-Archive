---
title: "Mediatomb: how do I get it to see my HDD outside of filesystem?"
date: 2008-05-24
forum: Multimedia Software
---

### Post by oxymoron on 2008-05-24
Hi,

this is doing my head in. How can I get mediatomb to see my hdd outside of "filesystem"?

The hdd is totally seperate its called "big storage", also do I have to have it auto mounted each time i start ubuntu? If so how do i do that?

Hope you can help me

ty Oxy

---

### Post by amak79 on 2008-05-30
oxymoron,

Is your hdd an external USB drive? Ubuntu auto mounts external USB drives when plugged in under /media. The drive should then be accessible by MediaTomb as it only needs read permissions. You only need to setup auto mounting in fstab if the hdd is an internal drive or you don't have GNOME installed which auto mounts drives when plugged in.

---

### Post by bifi37 on 2008-09-09
i have labled my disks filesystem so it always mounts the same.

for mediatomb you can add the whole directory or mount.
if you want to see the directory structure in youre upnp device add the following lines in your import.js: (usualy found in: /usr/share/mediatomb/js)

[I]function addDirectoryView(obj)
{
var chain = new Array();
var location = obj.location.split('/');

// location is in the form of /mnt/MEDIA/TV Shows/Heroes/Season 1/episode.avi
// this should add TV Shows + Heroes + Season 1 to the path of MEDIA
for (x=3;x<location.length-1;x++)
{
chain.push(location[x]);
}

addCdsObject(obj, createContainerChain(chain));[/I]
}

---

