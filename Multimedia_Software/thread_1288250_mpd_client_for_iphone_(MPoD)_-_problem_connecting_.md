---
title: "mpd client for iphone (MPoD) - problem connecting to mpd"
date: 2009-10-11
forum: Multimedia Software
---

### Post by thereallos on 2009-10-11
I have an app for the iphone called MPoD which is a client for mpd. I almost have it working, but there is a niggle that I'm hoping someone can help me out with.

The app wont connect to the mpd server unless I ping the iphone's IP address immediately before I want to use it. It essentially renders the app useless to me if I have to go to my computer and ping the iphone first every time I want to use it.

Does anyone have any ideas why this would happen and perhaps help me fix it?

---

### Post by mcduck on 2009-10-11
Are you using any kind of firewall (software or one in your router)?

That pretty much sounds like a firewall stopping incoming connections to your computer. It works after a ping because the firewall might threat the incoming connection as a response when you have first created a connection from the computer to the remote machine (your phone).

If you are using a firewall, the solution is f course to configure it to allow connections from your iPhone's IP address.

---

### Post by thereallos on 2009-10-11
Thanks for the reply .... I completely turned off the firewall on my router and I don't have a software firewall installed, yet I'm still having the same problem.

It's not a problem with the client on the iPhone either because I have the same issue with another remote pc running sonata (all on the internal network).

---

