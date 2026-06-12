---
title: "iriver e10 not working with dapper?"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by whatrucrazy on 2006-08-02
so...
having recently purchased an iriver e10 i was annoyed to find that whilst dapper recognises it as a usb external drive (or some such thing), and allows me to read and write from/to it as a data source, there is a major problem:
i cant listen to the music i have just put onto it, or see the pics or videos. 
i believe it has something to do with the e10's playlists? 
the machine itself doesn't even seem to recognize that the data is there, even though when i connect it to my pc, it shows up there when seen as a data drive. duh?

the only way i can listen to/watch my stuff is when i put it on the device via the 'iriver plus2' proprietary sofware that comes with the device.

so what's going on and how do i fix it? amarok has a tool for syncing with iriver devices but i can't get it to work and am not sure if it even will with this model. 

i am now puzzled, annoyed and lost.
can anyone help me with this
thanks.

---

### Post by WakkiTabakki on 2007-04-10
Just bought an E10 and having the same problem. 
Any news?

/N

---

### Post by whatrucrazy on 2007-05-29
SOLUTION!!!!

its not that easy, but:

install virtualbox and run windows XP as a virtual machine (you know where to get a copy if you don't have one), install the new iriver plus software from the iriver site for making playlists etc, screw around for ages getting it to recognise your USB connection to your iriver - there are guides, i can't remember exactly what i did but it works eventually - and there you go.

ta da!!

good luck


> **WakkiTabakki said:**
> Just bought an E10 and having the same problem. 
Any news?

/N

---

### Post by andre_orwell on 2008-01-13
SOLUTION????!

FWIW  I have recently got an e10 working on OSX using easypmp (developed for linux) so I susspect we can do better than pretending to be windows and running the iriver SW (which is pretty lame anyway)

Some details that might help:

1. files can be copied to and deleted from the e10 easily by treating it as a USB mass sstorage device
2. copied files will not be reflected in the e10's menu system because this is based on an index file which uses a custom database format.  To get the device to show you the files you have added you need to regenerate the index file and easypmp can do that.
3. it would be great to have this integrated into a player somehow.  Any hints? (willing to do some work on this... can code)

I don't have a linux system at the moment (soon to change)

---

