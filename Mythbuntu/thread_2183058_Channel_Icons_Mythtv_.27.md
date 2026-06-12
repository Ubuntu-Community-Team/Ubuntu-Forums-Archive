---
title: "Channel Icons Mythtv .27"
date: 2013-10-23
forum: Mythbuntu
---

### Post by diesel48 on 2013-10-23
Just wondering how I can get my channel icons to appear on all of my frontends around the house? They appear on my masterbackend/frontend combo but my frontend machines do not have the icons. It worked with mythtv .26.  Also how often are the repos updated? I just updated my mythv .27 fixes and it looks like it had a date of yesterday.

---

### Post by dekarl on 2013-10-25
[LIST]
[*]try [http://www.mythtv.org/wiki/Channel_icons#Universal_Location](http://www.mythtv.org/wiki/Channel_icons#Universal_Location)
[*]see [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) "It is automatically built each day when there are upstream fixes available."
[/LIST]

---

### Post by diesel48 on 2013-10-25
I did share ./mythtv/channels from the backend that has the icons to one of my frontends ./mythtv/channels directory. I can verify they are there but they still do not show up. I did a direct NFS share not symbolically linking them. Not sure that should matter.

---

### Post by Antti_Savinen on 2014-03-22
I have the same problem after upgrading from 0.25 to 0.27. Mythweb shows all icons, but not the frontend. I actually copied all icon to ~/.mythtv/channels with no luck.

---

### Post by blm-ubunet on 2014-03-22
Have you seen this:
[http://www.mythtv.org/wiki/Release_Notes_-_0.27](http://www.mythtv.org/wiki/Release_Notes_-_0.27)
and this:
[http://www.mythtv.org/wiki/Channel_icons#Universal_Location](http://www.mythtv.org/wiki/Channel_icons#Universal_Location)

From 0.27 the channel icon filenames are stored in DB without directory/folder path.
Can use mythtv-setup or mythweb to cleanup the existing icon filenames.

Note the the backend runs as user "mythtv" regardless of whether you have created a new user for FE.
So icons would be in /home/mythtv/.mythtv/channels/

---

