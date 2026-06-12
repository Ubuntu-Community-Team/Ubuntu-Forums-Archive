---
title: "More post-update problems - no evolution now"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-02-18
After running today's updates (minus the 40 or so I can't run, having an Nvidia card) I now find that a couple of top panel items have gone walkabout (battery and wireless applet) and evolution won't start at all.
I've tried launching it via cairo-dock (the usual way), via unity sidebar and via applications. It seems to start (it appears in conky display briefly) then fails to launch.
Starting it via terminal gives the folowing
```
nattyalpha@nattyalpha-VGN-AR51SU:~$ evolution
Inconsistency detected by ld.so: dl-deps.c: 622: _dl_map_object_deps: Assertion `nlist > 1' failed!

```
Any pointers for me?  Thanks.

---

### Post by dino99 on 2011-02-18
except the 7 xorg(s) packages, all the other packages can be installed without issue, just use synaptic to know about changes if you try to install them.

---

### Post by portis on 2011-02-18
It's due to the new version of eglibc


> **Quackers said:**
> After running today's updates (minus the 40 or so I can't run, having an Nvidia card) I now find that a couple of top panel items have gone walkabout (battery and wireless applet) and evolution won't start at all.
I've tried launching it via cairo-dock (the usual way), via unity sidebar and via applications. It seems to start (it appears in conky display briefly) then fails to launch.
Starting it via terminal gives the folowing
```
nattyalpha@nattyalpha-VGN-AR51SU:~$ evolution
Inconsistency detected by ld.so: dl-deps.c: 622: _dl_map_object_deps: Assertion `nlist > 1' failed!

```
Any pointers for me?  Thanks.

---

### Post by Quackers on 2011-02-18
> **dino99 said:**
> except the 7 xorg(s) packages, all the other packages can be installed without issue, just use synaptic to know about changes if you try to install them.

I thought they all wanted to remove nvidia-current. Or at least some of them did. And I've been there already :wink:

---

### Post by Quackers on 2011-02-18
> **portis said:**
> It's due to the new version of eglibc

And? Downgrade to the previous version? Just another downgrade? Or am I waiting for an upgraded upgrade? :-)

---

### Post by portis on 2011-02-18
I found an "ugly" patch from here:
[http://sourceware.org/bugzilla/show_bug.cgi?id=12454]("http://sourceware.org/bugzilla/show_bug.cgi?id=12454")
It works.

> **Quackers said:**
> And? Downgrade to the previous version? Just another downgrade? Or am I waiting for an upgraded upgrade? :-)

---

### Post by Quackers on 2011-02-18
ugly is ok :-) Thanks for the link.
I think I'll just give up on Natty. There's too much of this - releasing packages that break fundamental utilities. It's not very good, imo. I know Natty's for testing, but to effectively remove half your testers (or at least a big percentage of them) for a month or more, by releasing a new xserver version that can't be run by nvidia-current users is a step too far for me. It shows a decided lack of forethought in my view.
I fear for the final view of Natty if you're a nvidia user.
Now no email either. Shabby, very shabby.
Thanks again though peoples :-)

---

### Post by portis on 2011-02-18
I agree.
Testing alpha is not such pleasant experience, especially for natty.
I won't do it for the next release cycle.

---

### Post by Quackers on 2011-02-18
I've got 2 Natty installs and when an update broke one, I just booted up the other install and didn't run the updates until the problem was fixed. That way I always had one working Natty to use daily.
Now I'm just thinking it's a waste of good hard drive space. I can use Maverick or Lucid instead.

---

### Post by jennybrew on 2011-02-18
Its early days yet hang on in.
Im not over enamoured of the way its shaping up myself. I still cant begin to like the lack of user feedback and the lack of a desktop parable but Im going to see it through before I make my mind up.
Be fair ..Evolution isnt such a loss anyhow for a few days. Im sure itll reappear fully functional :)

---

### Post by Quackers on 2011-02-18
What gets me is, didn't somebody realise that evolution would be unusable before they issued the eglib update? Aren't these things tested at all?
It's alright saying that evolution isn't much of a loss for a few days, but it isn't. It is a problem that is easily got around, no denying, but should we have to?
And "be fair"? Really? Maybe that should be directed to the devs.

It's not "early days", it's two and a half months to release! And for the last 3 weeks I have had to hold upgrades or risk having no unity or desktop at all! And there's no end in sight to the nvidia problem! These are no small things.

---

### Post by plun on 2011-02-18
> **Quackers said:**
> What gets me is, didn't somebody realise that evolution would be unusable before they issued the eglib update? Aren't these things tested at all?
It's alright saying that evolution isn't much of a loss for a few days, but it isn't. It is a problem that is easily got around, no denying, but should we have to?
And "be fair"? Really? Maybe that should be directed to the devs.

Well I gave up Evolution years ago... and don't miss it !
```

sudo apt-get install thunderbird
```

and be happy....;)

---

### Post by Quackers on 2011-02-18
Thunderbird never worked well for me. I tried that early on :-)
When it works, evolution does what I need. It's good enough.

---

### Post by jennybrew on 2011-02-18
> **Quackers said:**
> 
It's not "early days", it's two and a half months to release! 


alpha release + two and a half months to final release = Early Days !!
I promise you it does :D

The best thing with these pre release releases (;)) is not to use them for important tasks such as sending and receiving e-mail. There is a lot of work to be done yet.

On this machine I have 10.04, 10.10 as well as 11.04. I have my e-mail client on 10.04 and ..its not Evolution.

Do be patient and Im sure you will have a functional system by the end of April. Then and only then its time to make up your mind. 

:D

---

### Post by jennybrew on 2011-02-18
> **Quackers said:**
> Thunderbird never worked well for me. I tried that early on :-)
When it works, evolution does what I need. It's good enough.

Apologies here for straying off topic but you might like to try Thunderbird again. 
There is a very good reason ..it works with Exchange Server and Evolution doesnt.

---

### Post by mc4man on 2011-02-18
> I think I'll just give up on Natty. There's too much of this 
If you change your mind then I'd not bother sitting behind the X update, quite likely your card will now work with the nouveau 3d drivers in the unity login.
While the nvidia drivers are superior, nouveau is ok for the moment, better to get current and nvidia will show up at some point. 
> I fear for the final view of Natty if you're a nvidia user.
Not at all

The only unfortunate thing was that the  nouveau drivers weren't 'fixed' earlier - it was a simple replacement of 1 line
```
@@ -1130,7 +1130,7 @@
    case TGSI_FILE_INPUT:
       res = bld_saved_input(bld, idx, swz);
       if (res && (insn->Instruction.Opcode != TGSI_OPCODE_TXP))
-         return res;
+         break;
```

> ]What gets me is, didn't somebody realise that evolution would be unusable before they issued the eglib update? Aren't these things tested at all?

Stuff like this happens, not every thing can always be accounted for, it gets reported and fixed

---

### Post by Quackers on 2011-02-18
What might Exchange Server be? And why would that be of interest to me?

With regard to testing I would say that I tested Maverick. I personally, don't see how you can test a system unless you use it all the time - for everything. That's why I have 2 Nattys. One to use and the other to risk breaking - until a fix is found.

---

### Post by Quackers on 2011-02-18
mc4man, I tried nouveau 3D on a previous install and found that I couldn't use unity (except 2d) and it was somewhat laggy. Cairo-dock animations, for instance, would hang half way through and just stay where they stopped. They were also very slow. Does the update you speak of help in this respect? Thanks.

---

### Post by mc4man on 2011-02-18
> I tried nouveau 3D on a previous install and found that I couldn't use unity
The update of libgl1-mesa-dri-experimental to 7.10.1~git20110215.cc1636b6-0ubuntu1 should allow you to run unity on pci-e cards (or at least some, can't vouch for what I don't have
No lag here on either of 2 installs, though don't use Cairo-dock
(both installs are A2 completely updated

---

### Post by cariboo on 2011-02-18
I would suggest trying Thunderbird again to, I have 9 email accounts, that It manages quite well. I keep moving the original email directory from version to version, so I never have to set things up on a new install.

I've used Thunderbird since it was called Minotaur.

---

### Post by cjwatson on 2011-02-18
> **Quackers said:**
> ```
nattyalpha@nattyalpha-VGN-AR51SU:~$ evolution
Inconsistency detected by ld.so: dl-deps.c: 622: _dl_map_object_deps: Assertion `nlist > 1' failed!

```

Matthias and I have put together an upload that fixes this (eglibc 2.13-0ubuntu1).  It should be available from mirrors in a few hours.

---

### Post by Quackers on 2011-02-18
Thanks cjwatson for your efforts :-)
I did notice that some of the updates I ran in the other install are not now available (error 404 given in Synaptic) which is probably best for the moment :wink:
I have returned to my other Natty for the moment and, due to mc4man's suggestion, dumped nvidia-current et al and renamed xorg.conf, then installed the experimental 3D driver. Althought not perfect, it is a much more usable beast than it was a week or so ago.  Cairo dock animations are still a bit laggy and freeze up, but it's definitely much better to use. Also, Unity 3D appears to be up and running again. Very nice :-)
I depend on cairo dock quite heavily as, if unity throws a wobbler, I can't do anything without it. Alt+F2 doesn't do anything and neither does ctrl+alt+t.
Again thanks all.

---

### Post by mc4man on 2011-02-18
> neither does ctrl+alt+t
It should work, but..
Once a keyboard shortcut stops working in the unity login it can be quite a pita to fix. For the most part i've given up as a waste of time.

And anyway I always install nautilus-open-terminal which is more useful.

So - on my laptop Ctrl+Alt+t works, on my desktop it doesn't (unity login
Though  on the desktop install, if I create a new user then it works.
Had the same thing happen once with screenshots way back, gave up trying to find out how to fix.
anyway the point is, -  it 'can' work.
( at this point compiz isn't crashing here unless I overuse the search function in dash or the 2 places, otherwise quite stable.

Ot. - and of low interest
There is a dconf-editor that allows almost no actual settings changes atm, though a useful one here is to add the date to the clock area in unity.
(found in com > canonical > indicator > datetime

---

