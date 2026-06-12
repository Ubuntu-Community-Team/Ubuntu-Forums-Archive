---
title: "How do I Stream Video over my Home Network"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by Galactus on 2006-07-26
I installed Ubuntu 6.06 LTS on my HP ze4805us laptop last night. Everything went fairly well, with the exception of setting up my wireless (it took me over an hour to get it working using the command line and NDISWRAPPER). Altogether, everything was set up and working in about 4 hours (included in that time was the install of a new hard drive). 

Anyway, one of the main things I use the laptop for is to view IPTV shows over my home network that I have downloaded onto my desktop. I was able to get to the files on my windows box no problem  , however I can't get them to stream properly in Ubuntu. 
- VLC won't stream anything over the network.
- Mplayer will stream everything except .mov files, however the play is jerky (it keeps stopping to rebuffer).
- Totem also will stream everything except .mov files, and it too is jerky (same buffer problem).
- I tried just about every player that I could find in the repositiories and nothing worked.

I believe I had kaffeine playing video over my network on another machine (which I've since uninstalled) but that was in a KDE environment and I am now using Gnome on the laptop.

Is there any player that is able to stream video over a home network without the stopping and starting. The convenience of being able to watch my video streamed over the netowrk all over my house (inside and out) is major for me. Without that capability I might have to go back to using Window (DAMN!!!NOOOOOOOOOOOOO - I don't want that!!!!Window =:evil:   )

---

### Post by fabiand on 2006-07-27
Hey,

I wonder why vlc didn't work.
You should give it another try...

---

### Post by Bonez56 on 2006-08-01
Kaffeine works perfectly on Gnome, like most other KDE applications.

sudo apt-get install kaffeine

it even adds a shortcut to your applications menu :)

I use it for watching DVB tv and streaming it over my LAN to other windows pc's..

---

