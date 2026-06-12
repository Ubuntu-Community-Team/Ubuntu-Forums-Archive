---
title: "Can you disable a soundcard completely?"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by Nazosan on 2007-06-01
I've been having some problems with frequent lockups and such.  It seems to be at least somewhat sound related because I hooked up an external soundcard and switched as many things as I could to using it instead and the frequency of the problem decreased some tenfold.  It still occurs, but at least I have it almost safe to leave the system running for a while while I'm not around to shut it down after a lockup.  I was thinking that it might just be possible that the lockups are completely soundcard related and would like to try disabling the onboard card.  This is a laptop, so the BIOS lacks the option to disable onboard sound (as well as a large number of other options as well...  But that's the sort of quality one can expect from a BIOS these days.)  Well, besides the whole lockup aspect, there are the facts that the external soundcard is better and that I get really tired of accidentally running something such as VLC twice and it deciding to use the other sound device, so suddenly late at night while I'm wearing headphones people nearby get to hear the sound suddenly coming out of the speakers...  I wouldn't mind being given an error or anything like that (though it shouldn't do that because I told it to use esound, which is supposed to allow multiple things to produce sound at once...)

Any ideas on how to disable it completely?  I realize I could probably comment out some module somewhere or something, but what I'd like to do is disable it in such a way that no autodetection scripts or anything like that will suddenly reenable it or something.

---

### Post by DracoPsycho on 2007-06-01
If you know which module handles your onboard card you can add it in **/etc/modprobe.d/blacklist** file. The module won't be loaded after reboot. 

Done it myself when wanted to disable my onbaord card, so to use just my SB card.

---

### Post by Nazosan on 2007-06-01
Ah, a blacklist?  That never even occured to me...  I think that may be exactly the solution I need.  It's unlikely any sort of autodetection or anything would mess with that...

---

### Post by DracoPsycho on 2007-06-01
I don't think there is ANY possibility to overcome this :) Unless something changes the blacklist file ;)

---

