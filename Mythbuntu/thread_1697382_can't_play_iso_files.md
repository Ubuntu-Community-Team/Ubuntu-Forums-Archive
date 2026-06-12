---
title: "can't play iso files"
date: 2011-02-28
forum: Mythbuntu
---

### Post by jim.hitch on 2011-02-28
Hi

I've checked out some of the threads regarding this issue, but none have so far worked. If I run mythfrontend in a terminal and then try to play an iso file I get this:

```
2011-02-28 23:59:04.251 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1169
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: failed to open/read the DVD
2011-02-28 23:59:04.278 Failed to open DVD device at /dev/dvd

```

So it's a file association issue?

I'm running a clean install of mythbuntu 10.10, nvidia ion. Any help would be appreciated. 

Thanks

Jim

---

### Post by Akriss on 2011-03-01
Hiya,

I'm still a noob. However, I have run in to this. So ill impart what i did to play iso's. :D
 
I installed Mediabuntu and upgraded to mythtv .24. 

thats about all.

to install mediabuntu I followed this post: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") 

Hope it helps.

---

### Post by jim.hitch on 2011-03-03
Hi Akriss

Thanks for getting back to me.

I don't really want to install another distro, esp. one that has packages I'm not going to need. And my backend is doing nicely with 0.23.1.

Can you do me a favour? Can you run 

```
mythfrontend
```

in a terminal and work your way through to playing an iso in the myth gui and then copy what the terminal screen says when you do that and then paste it in a reply?

That will give me a good idea of the problem.

Cheers

Jim

---

### Post by tgm4883 on 2011-03-03
medibuntu isn't another distro. It's a repository.


How are you trying to play an ISO? Where in the frontend are you going? Provide screenshots if you can't explain with words.

---

### Post by jim.hitch on 2011-03-04
Hi 

Thanks for the replies.

I have found the problem. I have a separate front and backend and am running 0.23.1 which won't play iso's from remote storage directories.

So I'll need to upgrade to 0.24.

Jim

---

