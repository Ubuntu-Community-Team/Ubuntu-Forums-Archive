---
title: "DNLA/UPnP server alternatives to mediatomb? Or fix for path issue?"
date: 2014-12-22
forum: Multimedia Software
---

### Post by spockswhitepants on 2014-12-22
I have mediatomb installed on a server and for the most part it works - but there is a long outstanding bug (years it looks like) that results in files being added in the wrong place to the library. For example:  [B]  

video/tv/show/season/s01e01 - Some Show.mkv[/B]

will get added in the initial scan in the correct place:  [B]

video/tv/show/season[/B] 

 but the auto-add functionality will create a new folder in the wrong place (off the root) for any new files:  [B]

video/season[/B] 

 So that is not really usable. The workaround is apparently to use a custom javascript import routine - but the ubuntu repository version of mediatomb does not have JS support (I found that out only after trying the workaround). So I guess I am stuck with the bug unless I want to find a version already compiled with javascript support (from what I have found online apparently it is difficult/impossible to get it to compile with the JS support enabled) and use it instead of the repository version.  

So I'm wondering if anyone knows of a fix/workaround or if there any good alternatives to mediatomb? I'm just looking for a simple UPnP server that monitors a single folder recursively and makes them available to UPnP clients. XBMC would probably work as I think it has UPnP server built in but it is way overkill for what I need and does not run very well through SSH (this is on a headless server so I have to manage it through SSH).

---

### Post by bfmetcalf on 2014-12-23
I run minidlna and it works very well, it finds new videos when I add them to my video folder and pushes them out to my Smart TV very well.  Never really had much of an issue with it.

---

