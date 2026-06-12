---
title: "Rhythmbox permissions issue"
date: 2008-11-26
forum: Multimedia Software
---

### Post by snares on 2008-11-26
I was having trouble with Intrepid so I resized my partition install Hardy on a 20GB section and the old installation as the /home so I could still have all my data. Plus it is probably a better setup anywho. Well computer runs great now but I am having permissions problems with Rhythmbox. Sometimes and only sometimes it returns importing errors and none of my music is playable within Rhythmbox or Exaile. I tried switching permissions:

chown <username> Music
chown <username> Music/*
chown <username> Music/*/* ..so on so forth until ownership changed to me   on all subfolders.

chmod 644 Music
chmod 644 Music/* you know the drill

better but still sometimes Rhythmbox returns import errors still. Many times a simple restart of Rhthymbox works and I can access my music. Other times I can fiddle with it for an hour or two before it plays nice.  I believe it is a simple permissions problem but really I am puzzle by the sporaticness or it all. Any ideas?

cheers
snares

---

### Post by doug1212 on 2008-11-26
I am not sure if this is your issue, but if your Music folder contains nested directories these will need to have the executable bit set.

Try this:

```
find /path/to/Music -type d -exec chmod a+rx {} \;
```

---

