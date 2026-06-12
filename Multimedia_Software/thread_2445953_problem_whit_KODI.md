---
title: "problem whit KODI"
date: 2020-06-22
forum: Multimedia Software
---

### Post by pfc70 on 2020-06-22
[COLOR=#242729][FONT=Arial][FONT=inherit]I have only recently been using UBUNTU and I am very satisfied. However I have a problem with the KODI player. I installed the player via ubuntu software and when I run it it shows me the home page and nothing more. How do I solve a problem?[/FONT]


[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-06-22
Welcome.

What home page?

---

### Post by TheFu on 2020-06-22
You need to point kodi at your media. The media organization it well documented on the kodi website.  Too many details needed to post them here.

Kodi is not a "player" like vlc or mpv or any of the normal players.  it plays media that is indexed inside the Kodi DB.

---

### Post by pfc70 on 2020-06-22
I'm sorry, but I'm using ubuntu for the first time and I'm not doing very well, what did you mean by what is the home page?

---

### Post by pfc70 on 2020-06-22
[COLOR=#000000]I'm sorry, but I'm using ubuntu for the first time and I'm not doing very well,[/COLOR][FONT=inherit]can you help me how to do that?[/FONT]

---

### Post by TheFu on 2020-06-22
> **pfc70 said:**
> I'm sorry, but I'm using ubuntu for the first time and I'm not doing very well, what did you mean by what is the home page?

It would work exactly the same on Windows.  Work through the menus. see what each has.  As some point under each media type, you'll see something that wants locations for the media to be added.  Because the locations can be local storage, network storage (CIFS/NFS), DLNA storage, and probably a few other types, you'll have to figure out how to specify a URL for your needs.

Start here: [https://kodi.tv/](https://kodi.tv/) and if you want more specific help, [https://kodi.wiki/view/Main_Page](https://kodi.wiki/view/Main_Page) There's a "Where Do I Start?" section.

The different media types need to be organized so the filename parsing works best to recognize the movie or TV series, then it will grab that data from free online sources and make pretty screens for your selection of what to play.  Again, there are plenty of guides for how to do this on Kodi and media-center websites. You'll want to get used to seeking out answers that way if you plan to keep running Linux.

I only run Kodi on raspberry pi systems and haven't setup the locations for mine in years - perhaps 4 yrs ago - so I don't recall the exact terms. My Kodi systems don't have any local media for many reasons, so it is all network storage. Most is accessed using DLNA, but some uses NFS.  Being new, I suspect these are terms you haven't heard before.

Don't fight the required directory layout. 

Good luck.

If you just want to drag-n-drop a video file to play, use vlc.

---

### Post by CelticWarrior on 2020-06-22
TheFu answered it perfectly for me. My question about the "home page" was a tricky one intended for you to come up with a description of what you're seeing and then segway to the point TheFu raised.

Your question is about Kodi, not about Ubuntu. Your proficiency in Ubuntu is irrelevant. Kodi is multi-platform. Kodi in Windows (as an example among many others) works the same way it works in Ubuntu.

Kodi is a media center. A media center is different from a media player. Although in many situations the differences are blurred there are still some things users must understand. The main one, again, is that a media center works with a library, a database if you want. It typically isn't used to open individual files like you would do - typically - in a media player. Instead users are supposed to add sources for the different media (example: Go to Music > Add music and select one or more music folders whose contents will then be added to the "library", the same for Movies, TV shows, etc).

Start here: [https://kodi.wiki/view/First_time_user](https://kodi.wiki/view/First_time_user)

Please note - this can't be stressed enough - that using common software/apps has little or nothing to do with the OS. Once installed - the installation method is often different though - the same software works the same way in any OS. Firefox is Firefox, Google Chrome is Google Chrome, VLC is VLC, etc. in Windows or Ubuntu. The issue here is not "[COLOR=#000000]ubuntu for the first time", is using Kodi for the first time, regardless of the OS. So, it makes as much sense to post your question here or in a Windows centric forum, i.e., it makes no sense at all. Your starting place is KODI.TV, the official website.[/COLOR]

---

