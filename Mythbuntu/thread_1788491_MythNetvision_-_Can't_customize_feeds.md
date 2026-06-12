---
title: "MythNetvision - Can't customize feeds"
date: 2011-06-22
forum: Mythbuntu
---

### Post by bobdole369 on 2011-06-22
Talking about the built in ones - Revision 3 specifically.  I change any item from disabled to enabled (actually I think its "enabled = "false"" to "enabled = "true"" in the rev3.xml, and I don't see any change in the menu.  I hit update map, and the whole tree stops working, all I'm left with is "Revision 3" with no arrow and no submenus.  If i delete the rev3.xml it gets downloaded again with another update. 

Is this working or maybe I'm just doing it wrong.

---

### Post by nickrout on 2011-06-22
> **bobdole369 said:**
> Talking about the built in ones - Revision 3 specifically.  I change any item from disabled to enabled (actually I think its "enabled = "false"" to "enabled = "true"" in the rev3.xml, and I don't see any change in the menu.  I hit update map, and the whole tree stops working, all I'm left with is "Revision 3" with no arrow and no submenus.  If i delete the rev3.xml it gets downloaded again with another update. 

Is this working or maybe I'm just doing it wrong.

you might need to wait longer for the feed to download.

---

### Post by bobdole369 on 2011-06-23
Nah that isn't it.  The feed has been there for a couple days now with no change.  When I hit "UpdateRSS" in frontend.log it logs "updating RSS feed", but thats it, nothing is changed - I only have the original single show that was already there.  It's up to date, but the one that I "enabled" isn't there.  I loathe to press update site map, I experimented and if I change a single byte in that rev3.xml, then hit update site map - the entire tree is gone from Revision 3. The arrow is just not there anymore.

If I manually add an RSS feed, then it shows up, but for some reason it just opens the web page for revision 3!  Why would it not just sub the RSS feed and download the mp4??!! Why in the world would it open the shows web page where I have to clumsily move the screen around with a remote, and it plays in a flash player?!! Just download the video and put it in a folder, thats the entire point of RSS!!!

There IS a "download video" option, but that doesn't work either for the RSS feeds:
The below line is logged in mythfrontend

2011-06-22 22:36:55.736 Downloading /home/dole/.mythtv/download_29611_1106.mp4

But that file doesn't exist and no further error is logged. 

I think I have my own solution which is about 80% of what it should be from a revision3 forum post from a board member there - a script which just subs, and downloads the videos like RSS is supposed to do. It just lacks metadata and the file/directory structure is just a little bit off.  I'm hoping to modify that script to handle other feeds besides rev3. I don't mind doing a little bit of this back end type stuff, but really if the mythnetvision is supposed to work, than shouldn't it do what it says it does?

---

### Post by nickrout on 2011-06-23
You might get better info asking on the mailing list.

---

