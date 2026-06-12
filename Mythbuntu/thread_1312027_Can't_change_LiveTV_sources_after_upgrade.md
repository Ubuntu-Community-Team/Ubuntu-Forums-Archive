---
title: "Can't change LiveTV sources after upgrade"
date: 2009-11-02
forum: Mythbuntu
---

### Post by zoiks on 2009-11-02
After upgrading to mythbuntu 9.10, I can no longer switch to "Next Source" using the "Y" key like I used to, during live TV.

Y is set to be my key that takes me to the next source, and I have verified this is still set in the key bindings. Specifically, Y would switch me from HDHomeRun to HDPVR and back. Now, it does absolutely nothing. The way myth is set up is to default to the HDHomeRun when I first go to LiveTV.

There are no errors in the backend or frontend log when I press it. Myth *will* record from the HDPVR if I schedule a recording. Also, if I occupy both tuners on the HDHomeRun with recordings, then go to LiveTV, it will go straight to the HDPVR, correctly. Only thing is I can't get it to actually switch sources like it's supposed to, when it starts off on the HDHomeRun.

Any ideas?

---

### Post by kja999 on 2009-11-03
Can you switch input by using the screen menu ?
(I.e. prove the functionality is there, then we know there is a keybinding issue)

---

### Post by Boppy3125 on 2009-11-03
I noticed the same thing with my Dvico and PVR150.  I can switch from the menu or also open the EPG and pick a channel on a different source.  (My case has SD channels from one card and HD on the other on different channel numbers.)  But "Y" doesn't do it anymore.

---

### Post by zoiks on 2009-11-03
> **kja999 said:**
> Can you switch input by using the screen menu ?
(I.e. prove the functionality is there, then we know there is a keybinding issue)

Thanks, good idea. I tried this and it worked.

Menu -> Switch Source -> HDPVR Source (or HDHR)

So, yeah, it seems to be only switching by hitting "Y" is the problem, not the functionality itself.

I could live with having to switch sources the long way, but it would be nice if I got the single-key switching back. What should I check next?

---

### Post by kja999 on 2009-11-03
Now I have got home and had a chance to try it on my setup .. I actually have the same issue, so looks like a regression.

Looks like next stage might be to get a bug raised with mythtv... [http://svn.mythtv.org/trac/wiki/TicketHowTo](http://svn.mythtv.org/trac/wiki/TicketHowTo)

---

### Post by zoiks on 2009-11-10
> **kja999 said:**
> Now I have got home and had a chance to try it on my setup .. I actually have the same issue, so looks like a regression.

Looks like next stage might be to get a bug raised with mythtv... [http://svn.mythtv.org/trac/wiki/TicketHowTo](http://svn.mythtv.org/trac/wiki/TicketHowTo)

OK, I've been trying to connect to mythtv.org lately to submit a bug, but it seems like the server's been down for a couple of days. Anyone else able to get to the site?

---

