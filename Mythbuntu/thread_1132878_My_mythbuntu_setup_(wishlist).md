---
title: "My mythbuntu setup (wishlist)"
date: 2009-04-22
forum: Mythbuntu
---

### Post by Rafiek on 2009-04-22
I have given myself a project. 
At home I want to setup a media server. And I think mythbuntu is what I need.
These are my wishes:
[LIST=1]
[*]Server containing all my music and video's.
[*]Streaming media to ubuntu and Windows clients.
[*]Connected to the TV to play DVD's and other content.
[*]One user that can add and remove content, change settings etc. The rest of the clients users can only view and listen to the content. 
[*]A nice client-front listing the content so easy that even my 60 year old mother can use it.
[*]Torrent client for downloading new content with a remote admin interface.
[*]Syncing content with my Ipod.
[/LIST]
Optional extras.
[LIST=1]
[*]Content rating so the admin (me) knows which content is popular and which content can be removed.
[*]Live stats so I know when my clients are watching/listening to what content.
[*]Restrict content for selected clients/users (no violent movies/tv shows for the kids)
[*]Restrict video content for clients/users based on time (if it's time for homework only music is allowed)
[/LIST]

What are the recommendations for these wishes. And can everything be done with mythbuntu?
I haven't touched Mythbuntu yet so this is a mythbuntu beginners project. :) Yep I'm aiming high for a beginner.

---

### Post by Weidbrewer on 2009-04-22
[LIST=1]
[*]Server containing all my music and video's. 
      **Yep**
[*]Streaming media to ubuntu and Windows clients. 
      **Definetly can go to other Ubuntu Machines, and I think it *can* be done to a Windows client, but I haven't done it.**
[*]Connected to the TV to play DVD's and other content. 
      **Yep**
[*]One user that can add and remove content, change settings etc. The rest of the clients users can only view and listen to the content. 
      **Lock down the permissions on the clients, and this is easily doable.**
[*]A nice client-front listing the content so easy that even my 60 year old mother can use it. 
     ** That depends on the 60 year-old.  The menu is just as easy as any Tivo/Digital cable menu...but, for example, my wife doesn't use it because she's afraid she'll "screw something up."  (she won't...see #4)**
[*]Torrent client for downloading new content with a remote admin interface. 
      **Can't help you on this one.**
[*]Syncing content with my Ipod.
     ** iPods don't play nice with Linux, and i haven't heard of anyone doing it through Myth.  Doesn't mean it can't be done, I just wouldn't know how.**

Of the optional ones, the only one I know for *sure* you can do is restrict based on content.  There are parental controls built in to Myth.


I hope that this helps, and welcom aboard.

[/LIST]

---

### Post by AboveTheLogic on 2009-04-22
> **Rafiek said:**
> [*]Torrent client for downloading new content with a remote admin interface.


I did this:

sudo apt-get install kde-core

and installed FreeNX, told my FreeNX client to connect to KDE, so I have a nice remote admin background session with vuze and lots of other goodies, while the console session on the TV is XFCE and the mythfrontend just as mythbuntu installed it.

---

### Post by cat5 on 2009-04-23
Well, as long as your install Mythbuntu - make sure MythWeb is installed, then install Torrent-Flux (it's in the repo's) -
gives you a nice web interface for your torrents.
 

I've got my mythbuntu box inside my network like most people, but I have another server running ubuntu server + ispconfig to host my dns/mail/web server,etc.. with a reverse proxy connection so I can reach my mythweb interface from anywhere in the world - which is also nice.

I can grab a torrent @ work, throw it up, and it'll be waiting for me when I get home...  and, I can schedule TV shows from work too.

---

### Post by AboveTheLogic on 2009-04-23
reverse proxy, eh?

that sounds interesting (I just read about it on wikipedia, didn't know about it)

I simply use SSH with C2S forwarding to get to my mythweb interface, but that requires a SSL client (like putty, which I have on my flash drive as a portable app if I need it)

---

### Post by Rafiek on 2009-04-29
> **weidbrewer said:**
> 
[*]syncing content with my ipod.
     ** ipods don't play nice with linux, and i haven't heard of anyone doing it through myth.  Doesn't mean it can't be done, i just wouldn't know how.**


I was thinking about that. I think the best way (in my mind) is to use samba to shared the music directory and add the shared directory in Itunes on a windows client.
And because I am a control freak (my character flaw) The share is only accessible true that windows client. The music is accessible through streaming :)

---

### Post by AboveTheLogic on 2009-04-29
There are reports of people successfully synching with iTunes using Wine, but I suppose if your goal is to have MythTV do it then that doesn't help you.

You could always use a remote session to do that kind of stuff from another PC, but you would need to still plug the device into the myth machine... so I guess that's not a very good solution (other than the fact that you keep all the data centralized).

---

### Post by Rafiek on 2009-10-16
I have tried installing Itunes on Ubuntu using wine, It works as a media player, but I'm not able to sync with my Ipod. 
So that is out of the question.

---

