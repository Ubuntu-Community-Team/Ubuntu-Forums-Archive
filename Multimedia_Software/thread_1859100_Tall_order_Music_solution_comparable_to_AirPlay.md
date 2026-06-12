---
title: "Tall order: Music solution comparable to AirPlay"
date: 2011-10-13
forum: Multimedia Software
---

### Post by malibu on 2011-10-13
Hi there.  I am looking at setting up a music solution for the house that the entire family can use.  The stereo in the livingroom needs to be headless and I'm looking at using a SheevaPlug connected with a USB sound card to the stereo.  The problem I am having is finding a solution that can be controlled completely from a central server using a console that can be brought up on any system in the house.  I would like the source of the music to be anything.. pandora.com, my music collection, internet radio mainly, which means the server needs to be able to pull sound off a sound card and stream it on my network.  Here are solutions that I have looked at:

AirPlay: (as I do have an AirPort Extreme)
- Must use iTunes as a source which is not my favorite
- iTunes will not take sound off the sound card to my knowledge
- iTunes does have a nice control for where the output goes over AirPlay.  This part is what I am looking for.

ShoutCast/IceCast:
- Must remote to the desktop with the server to control it
- Cannot choose destinations from the server side, must sign into the music player.
- Satisfies my requirement in that it can be configured to replicate anything on the sound card.

uPNP:
- Must be controlled from the client side

DLNA:
- only a subset of uPNP
- must be controlled from the client side.


Really, I would just like my SheevaPlug to sit running a deamon listening for input from a server.  I would like the server to have a web or less preferably X11 based console (but would prefer not to install x-server everywhere).  On the console I would like to be able to select the input and output.  Where input is sound card or music library, and output is any device in the house.

The server can be any OS, though I suppose for the robustness of the driver to be able to redirect the sound it might have to be windows.  The console needs to work on windows xp/7 for sure.  The sheevaplug will be running ubuntu.

Right now I have a netbook on the server running windows 7 / ultravnc but that solution is lacking because no one but me wants to use a vnc client to remote to the desktop.

Does anything like this exist?  If you have done something similar that works for you please explain.  Thanks.

---

### Post by Derek Karpinski on 2011-10-13
Squeezebox.

---

### Post by malibu on 2011-10-14
WOW!

Thanks for the recommendation.  I now have a SqueezeBox server and three players in my house and I am in complete awe that there was such an awesome solution that I didn't know about.

I'd heard of SqueezeBox Players of course but I thought they just took uPNP or something.  I had no idea there was such a robust, free, and open source infrastructure available.

And maybe I sound like an advertisement here but I am completely independent I assure you.  I thought Logitech was a good company before but now.. WOW.

Now I'm thinking I should buy a couple appliances just to support the project.

---

### Post by Derek Karpinski on 2011-10-17
They were their own company before Logitech bought them.  Logitech seems to have done a good job at keeping the server software open source, and supporting the whole project.
 
See if you can find a Squeezebox 2 for sale, and enjoy.

---

### Post by Takkat on 2011-10-20
Another approach similar to squeezebox is to set up an [Icecast2 ]("http://icecast.org/")internet radio server and stream the sound of your soundcard (or, alternatively a playlist)  to **any **"internet radio" capaple device attached to your stereo. Just tune in to your own local radio station.

Icecast2 is mainly a command line tool but with [Stream2ip ]("https://launchpad.net/stream2ip") we have a simple to use graphical frontend for Icecast2 that allows streaming with any Ubuntu music player, streaming playlists or generating UPnP/DLNA shares. The program is under active development and open for your suggestions.

---

