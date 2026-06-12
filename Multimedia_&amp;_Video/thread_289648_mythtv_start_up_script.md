---
title: "mythtv start up script"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by lerrup on 2006-10-31
As it says at the top, I have mythtv installed from marios debs which work very well, BUT mythbackend won't start from scratch.

The script is there and there are links in place.

Any ideas anyone- I am desperate!

Cheers!

---

### Post by dannyboy79 on 2006-10-31
i am curious, are you using Edgy or Dapper cause I really want to setup Myth and would love to be able to use .deb's. Also, which TV Card do you have, I have the PVR-350 from Haugepauge. Also, I don't know what script you're talking about but is it added in your sessions, then programs to start upon startup area? or is it something that gets added to init.d, like samba does?

---

### Post by lerrup on 2006-10-31
I'm using dapper with the 0.20 debs from Mario's repository (he's a member on these forums) and they are pretty good.

i am using a couple of DVB cards - do you have DVB-T in the states?  if you do avoid the twinhan card as it is a pain although it was cheap.  I have no experience of analogue cards - the kernel handles digital and so, in theory, they are straightforward.

The script is indeed an init.d script and for some reason this part of Myth won't work when it worked under the 0.19 version.

---

### Post by dannyboy79 on 2006-11-01
why don't you send mario a private message, I have been talking with him in various threads about me using his deb's and what I need to do to setup a complete front and back end/desktop on my dapper machine and he has been very helpful, i am sure he would answer your question. i don't know what a dvb-t card is, i have the Haugepauge PVR-350 and lspci -v states this about it, 0000:00:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
Subsystem: Hauppauge computer works Inc. WinTV PVR-350
Flags: bus master, medium devsel, latency 32, IRQ 129
Memory at e4000000 (32-bit, prefetchable) [size=64M]
Capabilities: [44] Power Management version 2

---

### Post by superm1 on 2006-11-02
lerrup,

What sort of thing is happening when launching mythbackend through the init script?

so, if you try to start it by

```
sudo /etc/init.d/mythtv-backend start
```

Is the process running afterwords?

If not, check
```
tail -n 100 /var/log/mythtv/mythbackend.log
```

It should be rather informative about why myth doesn't like you :)

---

### Post by dannyboy79 on 2006-11-02
I think he is saying that when he starts his computer mythtv backend isn't starting automatically. now I don't know if that's suppose to happen or not but I think that's what he wants. hi statement, "BUT mythbackend won't start from scratch." would leave me to believe that he wants mythtv to start when he logs onto his machine.

---

### Post by lerrup on 2006-11-05
Thanks for the suggestions.

I have now solved the problem.  The script is fine but something went wrong with the symlinks to start the script.  I removed them using rc.d and recreated and now its all working as it should.

Cheers!

---

### Post by superm1 on 2006-11-09
Lerrup, 

I have been seeing some other people having similar problems with the symlinks getting broken.  How exactly did you resolve this, and what do you think was causing it?

---

### Post by Lem on 2006-11-10
> **lerrup said:**
>  if you do avoid the twinhan card as it is a pain although it was cheap.

Twinhan card works fine in edgy/myth .20

Just add;

dvb-bt8xx 
dst
dvb_core

in /etc/modules 

and all is good :)

---

