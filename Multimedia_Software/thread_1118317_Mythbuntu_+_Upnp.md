---
title: "Mythbuntu + Upnp"
date: 2009-04-06
forum: Multimedia Software
---

### Post by pattersondm85 on 2009-04-06
Hello all!

So here is the deal

I have a Mythbuntu backend on its own computer, and a mythbuntu frontend as well (not relivent to this post).

The backend is running mythbuntu 8.10 (frontend is running 8.04).

I had been using my oginal xbox to view my movies in my living-room till about a month ago when it dies. So about a week ago I started looking into the idea of using my xbox 360 to watch my movies. I couldn't figure out how to use the Mythtv Upnp so I install uShare. Ushare worked great until I tried to play a HD file in the .mkv format. Ushare isn't able to transcode OTF.

I am trying to setup my mythbuntu to us the upnp so I can watch .mkv format movies on my xbox 360. Thus far I haven't been able to figure it out. I had read that the frontend packages needed to be install. So I installed the fronend (on the backend) and still didn't see any options to setup the upnp server.

I found on a different thread this message 
> Just the "packages" for the frontend software have to be installed on the backend to get this fix. 

You may want to edit /etc/default/mythtv-backend on both backends.

Replace #ARGS="" with ARGS="-v important,general,upnp" and restart the backend on each. You will now get logging in /var/log/mythtv/mythbackend.log that you should be able to debug as you connect to find out which one actually runs the UPNP (if only one does) and hopefully where things are going south.

I tried that and didn't see an difference at all.

Does anyone have success setting up the upnp server on mythbuntu? I am willing to do the foot work but I don't really see where to start. Since I love watch HD content since it looks so much better.

Thank you in advance for your help.
Pattersondm

---

### Post by pattersondm85 on 2009-04-08
bumb please anyone using mythtv and UPNP please lend a hand.

---

