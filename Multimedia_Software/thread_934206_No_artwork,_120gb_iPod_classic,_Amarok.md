---
title: "No artwork, 120gb iPod classic, Amarok"
date: 2008-09-30
forum: Multimedia Software
---

### Post by lomonx on 2008-09-30
First off, music transfers from Amarok and plays fine, no problems there, just there is no artwork with it.

What I've tried:

Installed the latest libgpod, got rid of the nogtk one which doesn't support artwork. I *think* Amarok is recognising the latest one because it shows all the previous iPod models except the new ones.

Updated my iPod SysInfo file which was empty, but now looks like this:

```
ModelNumStr: xB565
FirewireGuid: 000A270013730D51
```

The firewireguid did start with 0x but then I used gtkpod which decided to get rid of it. It didn't work either way so I'm not sure if that matters.

The music definitely has artwork in Amarok, but I guess libgpod isn't working right in transferring it.

Any help appreciated.

---

### Post by lomonx on 2008-09-30
Bump to add a bit more detail.

Tried connecting to a windows machine with iTunes, synched some albums and artwork and it then displays as expected on the iPod. However, connecting again to Amarok and adding a couple of more albums, the artwork itunes added now no longer displays, so it seems like something is definitely not right in that Amarok is messing with artwork somehow.

---

### Post by djdjules on 2008-10-12
Similar problem here.
I had managed my ipod with itunes since the begining.
Had 25GB of music with album art working perfectly on the ipod until I decided to use amarok listen to some tracks.
I wasnt even transfering tracks to the ipod and amarok killed all of the artwork.
I had to go back to itunes and rebuild the artwork database.

What I did to rebuild the artwork database: 
In itunes under the sync options uncheck the option that says something about displaying artwork on the ipod. after it deletes de database check the option again and it will rebuild the database.

---

### Post by gingermark on 2008-11-22
> **djdjules said:**
> I wasnt even transfering tracks to the ipod and amarok killed all of the artwork.

Lets get this right - Amarok did not kill the artwork, it was Apple, and their petty and pathetic attempts to make sure you can only use iTunes with an iPod - and in the process screwing Linux users.


I had the same problem. If you are prepared to start from scratch, [this guide](http://ubuntuforums.org/showthread.php?t=804761) worked for me (although it's for hardy - if you are using intrepid just make sure you have the medibuntu repository set up and you shouldn't havce to worry about the rest of the sources.list part of the guide.

---

### Post by talkingwires on 2008-12-05
> **djdjules said:**
> What I did to rebuild the artwork database: 
In itunes under the sync options uncheck the option that says something about displaying artwork on the ipod. after it deletes de database check the option again and it will rebuild the database.Hey, thanks for that tip. I didn't have much luck getting Amarok to upload music to my 6G iPod, so I resorted to using iTunes. But playing music off it with Amarok killed my album art, and I've been looking for a way to restore it for a while now.

---

