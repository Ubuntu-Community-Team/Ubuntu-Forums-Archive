---
title: "Noob UPNP questions"
date: 2008-06-12
forum: Multimedia Software
---

### Post by bryanchicken on 2008-06-12
Ok, been looking around on the old net for a definitive answer to this and either i'm stupid (most probably) or i just can't find it.

Been looking into UPNP and would like someone to clear some stuff up for me if they can?

1 -  What i can gather so far is you have a UPNP server running that shares and streams your media to any compatible renderer on the network. Correct?

2 - So you connect to the UPNP share and you can browse and play any media shared on the client you're using. Correct?

3 - Is it possible to use the client to control what is playing on the server? So basically hava a UPNP server on the PC and use something like a PDA or mobile phone to browse the library and control what the PC is playing?? Ie, not stream it to the client.


If that is possible, what software do i need? Currently i'm using Rhythmbox on my PC but as far as i can tell the UPNP plugin only allows you to connect to shares rather than serving them up and making it controllable


Cheers for the help.

---

### Post by aeiah on 2008-06-12
UPnP isnt what you need. as you said, it is for streaming media over a network. 

what you want is to control your computer from another. there are many ways you can do this. you could send bluetooth messages from your pda to your pc if they both have bluetooth for instance, or use the network for it.

you may be able to find apps written in java or python that will send commands to control MPD (music player daemon, a command line music player) or perhaps GUI music players (probably just rhythmbox and amarok, the two most popular).

what does your pda run? have you looked for remote control software for it?

---

### Post by Jussi Kukkonen on 2008-06-13
> **bryanchicken said:**
> 3 - Is it possible to use the client to control what is playing on the server? So basically hava a UPNP server on the PC and use something like a PDA or mobile phone to browse the library and control what the PC is playing?? Ie, not stream it to the client.


Oh yes, this is one the promises of UPnP that unfortunately hasn't realised fully (not too many devices available). There are three parts in a typical upnp av-system: Mediarenderer, Mediaserver (contentdirectory) and Controlpoint. These can of course be integrated, but they can also all be different devices -- I have a MediaStreamer software (closed source unfortunately) on my Nokia N810 that shows me all media on all servers in my network and can either play stuff locally or control a remote media renderer.

The difficult part of this seems to be finding a remotely controllable media renderer. This is not that surprising considering that security is UPnPs problem area... Most UPnP devices don't support any security protocols, which means your neighbour can change the song on your stereos :(

> **aeiah said:**
> UPnP isnt what you need. as you said, it is for streaming media over a network. 

As probably became evident, I strongly disagree.

---

### Post by bryanchicken on 2008-06-13
aeiah - my computer currently doesn't have bluetooth, i suppose i could add a dongle though.

With regards to controlling rhythmbox and amarok using python/java - are there any things around that would allow me to browse the library on the computer from the phone, without having to turn the monitor on an actually sit at the computer?

Jussi - its a shame that it seems so hard to find these remote controllable media renderers, as that sounds like exactly what i want.
I'll have to have a look around for one unless you have a suggestion?


Thanks for your help guys.

---

### Post by Jussi Kukkonen on 2008-06-13
> **bryanchicken said:**
> aeiah - my computer currently doesn't have bluetooth, i suppose i could add a dongle though.

With regards to controlling rhythmbox and amarok using python/java - are there any things around that would allow me to browse the library on the computer from the phone, without having to turn the monitor on an actually sit at the computer?

I think neither of the upnp-plugins for rhythmbox allow remote control, they're just mediaservers/contentdirectories at the moment.

This may interest you: [http://code.google.com/soc/2008/kde/appinfo.html?csaid=2D3B1B767BA3C580](http://code.google.com/soc/2008/kde/appinfo.html?csaid=2D3B1B767BA3C580)
It's fairly ambitious for a gsoc project, I'd say, but could be interesting.

> 
Jussi - its a shame that it seems so hard to find these remote controllable media renderers, as that sounds like exactly what i want.
I'll have to have a look around for one unless you have a suggestion?


The security situation with upnp is truly a shame -- upnp would be such a good solution for your situation if the security options weren't 
   A) No security
   B) Security so complex that no-one bothers to implement it
Stuff like this wouldn't need public key crypto, a button for "allow this control point" would be enough...

---

### Post by bryanchicken on 2008-06-13
This sort of thing would be ideal:
[http://www.allaboutsymbian.com/reviews/item/Nokia_N95-part_1_Music_Focus.php](http://www.allaboutsymbian.com/reviews/item/Nokia_N95-part_1_Music_Focus.php)

If you can't be bothered to read. Its basically a Nokia N95 controlling a PC UPNP server/renderer and also being able to control other UPNP clients on the network.

Shame you seem to have to use Simple Center (presumably Nokia's own) and i'm guessing that is Windows based :-(

---

