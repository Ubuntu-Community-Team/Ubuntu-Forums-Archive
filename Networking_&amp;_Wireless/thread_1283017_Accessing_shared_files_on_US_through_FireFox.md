---
title: "Accessing shared files on US through FireFox"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by tempomental on 2009-10-05
Hey all,

Here's an interesting question for you:

I have an Ubuntu Server 9.04 file server running and sharing successfully with a Vista and an XP machine. I also have a regular old Ubuntu 9.04 machine that I would like to play nicer with the server.

Here's what I'm looking to do: I want to set it up so that certain files on the server are one-click accessible from the Ubuntu machine... something similar to the "Mount network location" I've pulled off on the Windows machines. I'd then like to build links to the files so they can be accessible through an html file - building a dashboard page of sorts so the user can click and play the shared video.

Something like ```
<a href="smb://alpha/movies/movie.avi">play</a>
```, where "alpha" is the name of the server. Entering "smb://alpha" into the server will get me a listing of the shared directories, but I can't get any further than that. I know there's got to be an easier way to accomplish this.

Thanks for your help,
tm

---

