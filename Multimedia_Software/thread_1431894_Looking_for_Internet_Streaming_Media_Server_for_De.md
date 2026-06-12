---
title: "Looking for Internet Streaming Media Server for Debian PPC"
date: 2010-03-17
forum: Multimedia Software
---

### Post by moore.bryan on 2010-03-17
I've tried on a couple of mailing lists to get a decent response, but it's been pretty shabby, so I thought I'd try the expertise of this fine community.

I have a, relatively, ancient iMac G4 "Flowerpot" running Debian Testing and XFCE that I *was* using as a home music server. I write "was" because I could simply mount it using SSHFS from work, but now they have decided to become *very* restrictive with ports and for the life of me I can't get it working. I've already set-up GNUMP3D on it, but that also uses a port work won't allow.

So, in essence, I'm looking for suggestions on a Web-based application I could use to stream my music from home. Flash *does not* work on PPC, so anything Adobe-related is out of the question. Also, Java seems "iffy" at best... 

It's also worth note all of my music is in OGG format, so the program would have to be able to play said format.

Any help would be *greatly* appreciated.

---

### Post by Barriehie on 2010-03-17
Maybe [http://www.icecast.org/index.php](http://www.icecast.org/index.php)

---

### Post by moore.bryan on 2010-03-17
Thanks, Barriehie, Icecast looks interesting for my music. A little digging resulted in me finding it doesn't support video, except for nsv... do you know of anything more multimedia friendly?

I should have put that in the original post...

---

### Post by Barriehie on 2010-03-17
> **moore.bryan said:**
> Thanks, Barriehie, Icecast looks interesting for my music. A little digging resulted in me finding it doesn't support video, except for nsv... do you know of anything more multimedia friendly?

I should have put that in the original post...

No I don't but I'll keep looking.  I feel lucky to have XMMS on here... 8)  So you need audio/OGG format and since I don't know much about video formats is there any special type you're looking for.  I'm still using my VHS vcr as a clock...

Edit: Are you looking for a package to just install or do you/can you compile a package?

---

### Post by Barriehie on 2010-03-17
First hit although I wouldn't call this the 'optimum' choice.  [http://www.cherokee-project.com/](http://www.cherokee-project.com/)  and the link about streaming... [http://www.cherokee-project.com/doc/cookbook_streaming.html](http://www.cherokee-project.com/doc/cookbook_streaming.html)  and the Debian link: [http://packages.debian.org/unstable/web/cherokee](http://packages.debian.org/unstable/web/cherokee)

This one looks good, but you have to compile it:  [http://ushare.geexbox.org/](http://ushare.geexbox.org/)

---

### Post by moore.bryan on 2010-03-18
Thanks again for the links. Icecast doesn't look like it's what I'm looking for because I, basically, have to build a playlist for it to stream; rather, I'd want to be able to browse my media collection. Like I wrote, I _was_ doing this with sshfs, but now my ports are uber-blocked and I have to find an alternative.

Cherokee does look interesting, but is not media-specific and that's kind of what I was hoping for. Jinzora was promising, but couldn't get it to run on the iMac for the life of me.

---

### Post by markbuntu on 2010-03-18
Mediatomb might work for you.

---

### Post by moore.bryan on 2010-03-24
Sorry for being away from the thread for so long... Cherokee is a "no-go;" it just doesn't work well on the PPC. Mediatomb is great for at-home use, but it can't broadcast to the Internet for me to log-in from work. :-(

Has anyone ever had Jinzora work on PPC?

---

