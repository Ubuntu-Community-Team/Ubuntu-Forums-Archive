---
title: "K3b won't burn dual layer dvd (9.10 x64)"
date: 2009-11-05
forum: Multimedia Software
---

### Post by jeebustrain on 2009-11-05
I really like K3b and I've used it for a while to back up and duplicate my DVDs. When I built my new Karmic x64 Ubuntu Studio Machine, I had to install it. I installed all of the restricted extras and codecs as well.

The problem is that whenever I try to put in a dual layer DVD to duplicate to a new disk, I get this error:
```

Growisofs >= 5.20 is needed to write Double Layer DVD+R

```

Now, I can't find this library (assuming it's a library) on its own on the machine or in synaptic. I tried removing/readding K3b and it had no effect. The weird thing though is taht I can do the "create image only" option and dump it to an .iso file just fine. It's just when I do a DVD -> DVD duplication that it fails. I'll have to double check with my wife too, but I'm pretty sure single layer DVDs dupe fine.

I can't seem to find ANYTHING on this message, nor can I figure out how I can upgrade growisofs manually. Any ideas?

---

### Post by ajgreeny on 2009-11-05
I suspect this is a version problem.  Check yiou have already got dvd+rw-tools installed, as this contains growisofs.  If you don't have it, install it and try again.  If you do have it already, then it must be the wrong version, I think. However as the version in jaunty is 7.1, it must be at least that in karmic, so I am a little baffled, as it appears you only need version 5.2 or higher.

---

### Post by jeebustrain on 2009-11-06
thanks, I double checked last night and I have the tools installed. Just for good measure I removed/readded them and it made no difference. According to Synaptic, it's 7.1-4.

---

### Post by jeebustrain on 2009-11-11
weird... I just rebuilt my box last night (due to an unrelated issue) and used the full RTM release of Studio x64 Karmic. I installed the restricted-extras and enabled DVD playback and installed k3b (and verified that the dvd+rw-tools are on there) and when I launch K3b it doesn't even recognize that I have any disk drives (I have 2x dvdrw). The drives work fine in normal space (I can insert a DVD, browse and play a movie in VLC just fine), but no matter what I try in K3b it doesn't recognize them.

I even tried running k3b as root and it still didn't recognize them. They were recognized fine in my previous install (although had the above problem) and everything worked absolutely perfectly when I was running OpenSUSE 11.1 x86 about 3 weeks ago.

---

### Post by jeebustrain on 2009-11-13
well, I just figured my second issue out. For some reason, "rw" wasn't a mount attribute on either of the drives inside /etc/fstab. I can now rip DVDs. Up next is trying to burn dual layer.

---

### Post by jeebustrain on 2009-11-13
and that's a negative. still the same growisofs error.

---

### Post by donal on 2009-11-13
anybody know if there is a bug logged for this or what the exact limitations are?

I am on ubuntu 9.10 (32bit) been trying to burn a dvd + R dual layer. tried k3b, brassero and even imgburn via wine but no joy. 

the DVDs i have are memorex - someone suggested  trying with verbatim dvds instead but i am reluctant to go and buy more blank dvds. 

Would rather not have to go back to my sisters house and beg to use her windows machine cos ubuntu couldn't do it - i would never hear the end of it :-)

thanks
Dónal

---

### Post by jeebustrain on 2009-11-13
I learned a long time ago (even when using Windows machines) that the only Dual Layer DVD+R discs around are the Singapore made Verbatim ones. They've since stopped making them and are now being manufactured in India. The quality control is crap and you're going to get 2-3 coasters out of every 5 you try. Your best bet is to look on Ebay (that's where I go) to find the Singapore made ones.

I've tried the Memorex ones as well and those are even worse than the Indian Verbatims. I think I got a 25pk and got maybe 3-4 successful burns out of the whole thing. 

Note: this only applies when burning movie ISOs to be played in a dvd player. Regular data works just fine on them. 



Are you getting this same error as I? My next step is to try to use K9copy and see if I have any better luck tonight.

---

### Post by funnyname on 2009-11-14
Moved by self due to wrong posting.  Sorry for this.  I need to read more carefully.

---

### Post by jeebustrain on 2009-11-15
well, Brasero seems to work just fine. Guess I'll have to just get used to that. I was reading around on Ars Technica and apparently I'm not the only one having probs w/ K3b.

---

