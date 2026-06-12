---
title: "accessing a remote itunes library"
date: 2009-04-08
forum: Multimedia Software
---

### Post by PaganTraveller on 2009-04-08
I'm running Ubuntu 8.04 on a Dell Mini 9. I have a desktop mac which houses my very large music library. It would be nice to listen to that library on my mini.

Has anyone been able to successfully use Rhythm Box to connect to a remote iTunes library and browse the library?

If not with rhythm box, how else might i be able to connect to my remote library, or somehow stream the music from my mac?

All the music is organized and stored in a single folder on the Mac. Which I can access (via SFTP at least) from Ubuntu. If there was a way to just open and play those files over the network file-sharing, that would be great too.

---

### Post by mythidiot on 2009-04-12
I have a similar question. Any help on this would be rad. Anybody?

---

### Post by ad_267 on 2009-04-12
You shouldn't really have any problems. Just set up your iTunes to share your music using DAAP. Make sure the DAAP plugin is enabled in Rhythmbox and then go to Media - Connect to DAAP share.

I use mt-daap (Firefly) to share music between computers running Ubuntu which runs as a service, so I don't have to be logged in and running rhythmbox for this to work. I don't know if Mac has something like that already available but you can [install mt-daap on a Mac]("http://wiki.fireflymediaserver.org/Mac_Installation") if you want. I also use Banshee which automatically finds any DAAP shares available.

---

