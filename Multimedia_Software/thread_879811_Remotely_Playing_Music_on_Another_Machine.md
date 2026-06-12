---
title: "Remotely Playing Music on Another Machine"
date: 2008-08-04
forum: Multimedia Software
---

### Post by raublekick on 2008-08-04
I came up with a project I'd like to do, but I'm not sure how to do it.

I have a spare computer I plan on using as a file server. Setting up the file server is easy enough. But I also have a stereo system in my living room that can currently only play records and anything with a 1/8" output.

I want the server set up as a file server so that I can play music from it on my laptop, but I'd also like to be able to remotely control the server with my laptop to have the server play music through the stereo. I'm sure there are plenty of command line solutions to this, but I'd prefer a GUI solution since I'm not the only one in the house that would use this. I would also like to make it library based rather than file based but that's not 100% necessary.

This would be using Ubuntu 8.04 Server (no gui)

If anyone has any ideas, please let me know! I'll even write up a tutorial when (if) I get it working.

P.S. I wasn't sure if this fit more in the Multimedia or Networking forums...

---

### Post by MrHippocampus on 2008-08-04
For playing music out of the server to your stereo Mpd ([website]("http://www.musicpd.org")) is probably what your after, it runs as a daemon on the server and you can control it remotely with loads of different clients, including web based ones (and even a command line one).

---

