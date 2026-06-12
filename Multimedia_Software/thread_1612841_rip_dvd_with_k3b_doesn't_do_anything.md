---
title: "rip dvd with k3b doesn't do anything?"
date: 2010-11-03
forum: Multimedia Software
---

### Post by Antenne on 2010-11-03
I installed Kubuntu 10.10 these days and am impressed with the overall setup and performance. Things simply work - but one (so far). 

With some additional storage, I decided that I want to backup my favourite DVDs to this. Installed required packages from medibuntu, can view the DVDs in question with dragon. Starting k3b, RMB on the DVD title, select "Rip Video DVD" - waitcursor spinning for about 1 second - and nothing. No dialog, no message, no error. Nothing.

Settings -> Configure K3b -> Programs: all there but "eMovix" and "normalize-audio".

Starting on commandline:
  $> k3b --videodvdrip /dev/dvd

Nothing (useful).

Starting on commandline as above and capturing strace output - 50.000 lines, but no real result.

Any ideas?

---

### Post by tommcd on 2010-11-04
See this for ripping DVDs in Kubuntu:
[http://www.kubuntu.org/doc/7.10/musicvideophotos/C/burning-cds.html](http://www.kubuntu.org/doc/7.10/musicvideophotos/C/burning-cds.html)
You could also try installing **DVD:Rip**, **K9Copy**, or **Handbrake** to rip DVDs. See this also:
[https://help.ubuntu.com/community/DVD%3A%3ARip](https://help.ubuntu.com/community/DVD%3A%3ARip)
Hope this helps.

---

### Post by Antenne on 2010-11-04
> **tommcd said:**
> See this for ripping DVDs in Kubuntu:
[http://www.kubuntu.org/doc/7.10/musicvideophotos/C/burning-cds.html](http://www.kubuntu.org/doc/7.10/musicvideophotos/C/burning-cds.html)
Hi tommcd.

Sure found this link myself. 

It says: "Follow the [How to rip a DVD and encode it into an MPEG-4 AVI with K3b (Local system documentation link)]("help:/k3b/howtos.html#videointroduction") located in the K3b Handbook."

The handbook of k3b nowadays points to [http://userbase.kde.org/K3b](http://userbase.kde.org/K3b) which does not provide the information any more.

I also found the alternatives. However, k3b does (generally) provide the functionality, but it does not work as expected, i.e. not at all. Before moving on, I'd like to understand why - and what to do to fix it.

---

### Post by tommcd on 2010-11-04
> **Antenne said:**
> 
 However, k3b does (generally) provide the functionality, but it does not work as expected, i.e. not at all. Before moving on, I'd like to understand why - and what to do to fix it.
This page from Launchpad is 3 years old, but it does provide an answer why K3B will not rip DVDs:
[https://answers.launchpad.net/ubuntu/+source/k3b/+question/8903](https://answers.launchpad.net/ubuntu/+source/k3b/+question/8903)
It is at the bottom of the page:
> Apparently K3b is not compiled with libdvdread-dev:
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/99448](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/99448)
After compiling K3b with libdvdread-dev, it works as expected.
Some distros ship K3B with DVD ripping disabled due to those evil software patents, or the desire to use only free software. Slackware (developed in the USA) also does this.
So you can't just install libdvdread-dev and expect K3B to rip DVDs. You would have to install libdvdread-dev and then recompile K3B.
I think it would be better to just go with one of the alternatives for ripping DVDs that I mentioned. Perhaps there is a PPA repo that has a libdvdread-dev compiled K3B available. The only alternative would be to compile K3B yourself from source code.

I don't use Kubuntu or K3B in Ubuntu, so I can't verify any of this.

---

### Post by Antenne on 2010-11-05
> **tommcd said:**
> The only alternative would be to compile K3B yourself from source code.
I compiled KDE from sources before and ran Gentoo for years before I came to [K]Ubuntu, but there is a reason for this switch. It  just takes too much time to compile all the stuff myself. As CPU cycles and storage are not a real reason any more to exclude unwanted dependencies, apt makes things so much easier.

However, one should probably file a PR against k3b to disable the menu entry if that feature is missing, then.

Thanks for your input.

And k9copy almost works -- besides that the .mpg is all blurry compared to the original :(

---

### Post by tommcd on 2010-11-05
> **Antenne said:**
> 
And k9copy almost works -- besides that the .mpg is all blurry compared to the original :(
Although I have never used it, I have read that Handbrake works very well for ripping DVDs.
[http://handbrake.fr/](http://handbrake.fr/)
Handbrake does not seem to be in the Ubuntu repos; but there is a PPA repo for the development builds here:
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)
Also, this article from linux.com may be helpful:
[http://www.linux.com/news/software/applications/325648-choose-the-dvd-ripper-thats-right-for-you](http://www.linux.com/news/software/applications/325648-choose-the-dvd-ripper-thats-right-for-you)

---

