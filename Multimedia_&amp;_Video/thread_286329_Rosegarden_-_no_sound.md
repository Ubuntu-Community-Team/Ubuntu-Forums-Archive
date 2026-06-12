---
title: "Rosegarden - no sound"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by Tomlin on 2006-10-27
Hey all,

I'm trying to play around with Rosegarden and maybe compose a song or two. I don't have any midi instruments to plug in, I just want to try my hand at composing. However, I can't get it to produce any sounds.

XMMS, Xine, mplayer, and hydrogen all work. I've tried using JACK (actually QJackCtl), but I don't know 'JACK' about hooking what to where. Do I need to even use JACK?

Can anyone help me out?

Thanks.

---

### Post by cage cat donnie on 2006-10-28
Ditto


EDIT:  I got it going by folowing the instructions for loading timidity.

[http://www.cs.cornell.edu/~djm/ubuntu/#timidity](http://www.cs.cornell.edu/~djm/ubuntu/#timidity)

I confess I don't know what about it make rosegarden work, but something happened...

EDIT #2:  I spoke too soon.  What ever I did quit working after reboot.  It must have been some combination of packages I loaded manually prior to the timidity thing.  I know somehow I have the stuff to make it work on my system, but I have no idea how to do it, lol.

---

### Post by Tomlin on 2006-11-02
ccd,

Good luck trying to get your sound back again. I'm still stuck.](*,)  Let me know if you succeed.

Anyone else?

---

### Post by aonegodman on 2007-12-26
> **cage cat donnie said:**
> Ditto


EDIT:  I got it going by folowing the instructions for loading timidity.

[http://www.cs.cornell.edu/~djm/ubuntu/#timidity](http://www.cs.cornell.edu/~djm/ubuntu/#timidity)

I confess I don't know what about it make rosegarden work, but something happened...

EDIT #2:  I spoke too soon.  What ever I did quit working after reboot.  It must have been some combination of packages I loaded manually prior to the timidity thing.  I know somehow I have the stuff to make it work on my system, but I have no idea how to do it, lol.

I took a look at your link at cornell.edu and I was able to cut-n-paste the suggestions and make the modifications. I haven't retried or rebooted my system yet to see if it works. If it does, believe me I'll be back with bells on my toes to let everyone know.  Thanks!

:)

---

### Post by aonegodman on 2007-12-26
Hello! \\:D/  Can you hear them bells ringing? \\:D/

I've got sound coming out of Rosegarden. Yeah. That's the good news.

Here's the next issue:  JACK don't like it.  [-(  Crashes and NO SOUND with JACK Server.

Shut down JACK and I got sound coming out of Rosegarden. Now the thing is Rosegarden wants JACK and starts it automatically on start up. But I have to shut it down in order to get sound back.  What's going here?  Any help on this? Thanks!

tinkle . . . tinkle ... tinkle . . . bells still ringing though cause I'm making progress :)

---

