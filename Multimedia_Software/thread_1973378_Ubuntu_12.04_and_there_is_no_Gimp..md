---
title: "Ubuntu 12.04 and there is no Gimp."
date: 2012-05-04
forum: Multimedia Software
---

### Post by Bao2 on 2012-05-04
I was using Gimp 2.7.4 from an unofficial repository in Ubuntu 11.10.

Now in Ubuntu 12.04 you get only Gimp 2.6 or nothing. Because no repository has an updated gimp.

---

### Post by sparhawkthesecond on 2012-05-04
I've spent about an hour trying to find a repository containing the most-recent, stable Gimp 2.8.0. It's quite frustrating! FWIW I found two possible leads, but neither is what I want exactly. A few sites mention [this repository]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn?field.series_filter=precise"). Unfortunately, it's not the latest stable build, but rather nightlies that "are not [built] every night automatically [but] rather built whenever I get around to it, which might be several builds per day or one build per week." In any case, it doesn't contain builds for Precise.

The other option is [this repository]("https://launchpad.net/%7Eotto-kesselgulasch/+archive/gimp?field.series_filter=precise"). This contains 2.8.0 for precise, which is great, but the description says > CAUTION! This PPA could break your installed OS. There are dependency issues  especially for Oneiric (11.10). Only use it if you know what you do! I'm  working with others on a stable and reliable solution. I'm not sure what this implies for the Precise version, as perhaps this message is just outdated. Anyway, I've contacted the owner of the ppa, so we can wait and see what he says. Otherwise, if anyone has a good alternative, please post it!

---

### Post by EatenSniperGuy on 2012-05-04
[http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html](http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html). There you go!

---

### Post by sparhawkthesecond on 2012-05-05
> **EatenSniperGuy said:**
> [http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html](http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html). There you go!

Thanks for the reply, but that's identical to the second repository that I linked to in my earlier comment. Also, in your links, the owner also says "Remember: Be aware of side effects." but I'm not sure if he's referring to anything specific, or just a general "this is untested" warning.

---

### Post by andrew.46 on 2012-05-05
Mind you it is still very early days, Gimp 2.8 was only released 2 days ago :).

---

### Post by sparhawkthesecond on 2012-05-05
> **andrew.46 said:**
> Mind you it is still very early days, Gimp 2.8 was only released 2 days ago :).
True, but AFAIK there was never a repo that attempted to build the latest stable version anyway. (I just can't wait to get my hands on single-window mode!)

---

### Post by andrew.46 on 2012-05-05
> **sparhawkthesecond said:**
>  (I just can't wait to get my hands on single-window mode!)

Me too :).

---

### Post by SeijiSensei on 2012-05-05
All that warning says is that you may have problems installing the 2.8 package on versions of Ubuntu earlier than Precise because of dependency issues.  That's true for just about any package.  I don't see that as a reason not to use that repository if you're running 12.04.

Usually packages for older Ubuntu versions will run on newer ones, but the reverse is rarely true.

---

### Post by sparhawkthesecond on 2012-05-07
> **SeijiSensei said:**
> All that warning says is that you may have problems installing the 2.8 package on versions of Ubuntu earlier than Precise because of dependency issues.  That's true for just about any package.  I don't see that as a reason not to use that repository if you're running 12.04.

Usually packages for older Ubuntu versions will run on newer ones, but the reverse is rarely true.

That makes sense, but I guess I don't know enough about Linux to understand the implications of "This PPA could break your installed OS"? Surely if it were just dependencies that Gimp relied on, one could just revert Gimp if it was broken?

Cheers.

---

### Post by SeijiSensei on 2012-05-07
I think that comment is a bit extreme myself.  My guess is that the developer is worried that installing GIMP 2.8 for Precise might install some dependent libraries that other programs use.  It's possible that these newer libraries would be incompatible with the older programs.  Usually that's not the case, though.  

As I said in another thread about GIMP 2.8, I'd recommend just updating first to 12.04 and then installing GIMP.  12.04 has long-term support so it should be the preferred choice of most people unless they like to experiment with new distributions each time one is released.

---

### Post by sparhawkthesecond on 2012-05-07
> **SeijiSensei said:**
> I think that comment is a bit extreme myself.

Thank you for your opinion on the matter. I'm confident enough to give it a go now! Also, when I went to add the repo, I noticed it has been updated to mention "There should be no problems in Precise Pangoline (12.04)."

Cheers.

---

### Post by Hylas de Niall on 2012-05-07
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

^^^ Worked fine for me on 12.04 ^^^


Posted bu Joey on **OMG! Ubuntu!**  [http://www.omgubuntu.co.uk/?p=56665](http://www.omgubuntu.co.uk/?p=56665)

---

### Post by sparhawkthesecond on 2012-05-07
Seems to be working well for me too, so far.

---

### Post by iMurshaq on 2012-05-08
[http://www.youtube.com/watch?v=Y67ZmMbi85s](http://www.youtube.com/watch?v=Y67ZmMbi85s) - a tutorial for the people...

---

