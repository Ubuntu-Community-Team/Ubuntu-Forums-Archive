---
title: "Using VLC to watch live tv"
date: 2012-06-08
forum: Mythbuntu
---

### Post by mlrabbitt on 2012-06-08
Can this be done?  I tried changing the default player in frontend to VLC following these instructions: [http://www.mythtv.org/wiki/VLC](http://www.mythtv.org/wiki/VLC) .  I also tried setting default player to just 'vlc'.  

'Watch TV' still plays using the internal player though.  If I change the default player for certain file extensions, I can play videos in the media library with VLC, however recordings still play through the internal player.

Someone mentioned in another forum that VLC cannot play files in storage groups, but I am little unclear on how to get around this.  I went into backend and deleted all the paths for 'LiveTV' and 'Recordings' but I don't understand how I can specify paths for these that aren't storage groups.

I'm using Mythbuntu 12.04 .25/fixes FE/BE on same PC.

---

### Post by tgm4883 on 2012-06-08
> **mlrabbitt said:**
> Can this be done?  I tried changing the default player in frontend to VLC following these instructions: [http://www.mythtv.org/wiki/VLC](http://www.mythtv.org/wiki/VLC) .  I also tried setting default player to just 'vlc'.  

'Watch TV' still plays using the internal player though.  If I change the default player for certain file extensions, I can play videos in the media library with VLC, however recordings still play through the internal player.

Someone mentioned in another forum that VLC cannot play files in storage groups, but I am little unclear on how to get around this.  I went into backend and deleted all the paths for 'LiveTV' and 'Recordings' but I don't understand how I can specify paths for these that aren't storage groups.

I'm using Mythbuntu 12.04 .25/fixes FE/BE on same PC.

You cannot use an external player with storage groups, and you have to use storage groups for recordings. In the future, you will have to use storage groups for everything, so you won't be able to use VLC for videos either.

---

