---
title: "Serious iPod woes (brand new iPod)"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by jsedwards on 2008-04-21
Three years ago I used gtkpod to load my iPod with 4,500 mp3s.  It worked perfectly and I've used the iPod for years.  I haven't ever plugged it in again because I haven't had time to rip any more CDs.

Now I have a new iPod and the Linux iPod world seems to have changed.  I tried to put some songs on this new iPod with gtkpod and gtkpod was not happy and would not let me put any songs on it at all (I don't remember the exact errors because that was 3 weeks ago).

I then tried Amarok and that loaded songs onto the iPod ok, but the iPod did not recognize that any songs were on it.  I did a Google search and found this web page: [http://gtkpod.wikispaces.com/Sysinfo+File](http://gtkpod.wikispaces.com/Sysinfo+File) that says you have to put a Firewire GUID on it for it to recognize it.  I did that but it still didn't work.

Finally, I thought that if I hooked it to a Mac and it put the initial db on it then Amarok could take it from there.  I borrowed a MacBook and plugged it in.  It said it had a DOS FAT file system and it would have to initialize it.  (Which is weird because in the old days iPods always came with HFS filesytem and you had to initialize it if you were going to use it with Windoze.  However, the Mac would not restore it without becoming superuser, so that was out of the question. (Which is a really dumb thing on Apple's part).

Then I borrowed another 80 GB ipod and used 'dd' to just copy the entire disk from the working iPod to the new iPod.  My thinking being that if I could get it to play at all, then I could change the music later.  After cloning the disk, I mounted both of them and did a diff and the two iPods were identical (no differences found).

Still... it did not think there was any music on it at all.  I tried adding the Firewire GUID and discovered that now it thinks the file system is "read only".  It won't let me write anything to the disk.

So I am not sure what to do now.  Does anybody have any suggestions?

Thanks
  -Scott

---

