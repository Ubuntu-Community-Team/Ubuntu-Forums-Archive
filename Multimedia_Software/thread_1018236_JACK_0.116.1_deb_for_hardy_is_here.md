---
title: "JACK 0.116.1 deb for hardy is here"
date: 2008-12-21
forum: Multimedia Software
---

### Post by steve167 on 2008-12-21
So jackd 0.109.2 from the Hardy repo is pretty borked.  I've confirmed this through personal pain while recording as well as working my way through various audio forums which all agree the 109.x release from JACK is nothing but problems.  Try to grab any more recent version from the repos and you'll find that they're built against later versions of some core libraries that are part of Hardy -- translation -- the debs for JACK(jackd and libjack0) beyond 0.109.2 from Ubuntu repo won't work with Hardy.

I've gone ahead and built a deb that will install JACK 0.116.1 *ALONG SIDE* the previous installs of the jackd 0.109.2 and libjack0 0.109.2 packages.  You still need to have the installs of these aforementioned packages to keep synaptic & dpkg happy since my deb is not set up to report the dependent items that it supplies.  I basically took the regular "install" step for the manual build of JACK and performed it with "checkinstall" to produce my deb.  I then opened up the deb and made some minor changes to the control file -- mostly instructions that can be viewed from synaptic and a post-install step which symlinks the install location of the libraries(/usr/local/) from the standard Ubuntu search path(/usr/).  The new binary jackd will be in /usr/local/bin so if you're using qjack for your jack controller then be sure to update the binary path.

to install:

sudo dpkg -i jackd-extra_0.116.1.deb

Enjoy.

---

### Post by m.sant on 2008-12-23
Hi,

I'd like to make the same for Ubuntu Intrepid Ibex.

Could you explain better all the steps? I really need to install JACK 0.116, but it doesn't work if I compile it with the standard configure/make/checkinstall.

Thanks,
Marco

---

### Post by carlosmoraes on 2009-01-09
Hey, Steve ...
I tryed your packaged and jack starts all right.
But all clients I try to connect to it (Ardour, Hydrogen, Qjacktcl) make it throw a message like this:
JACK protocol mismatch (22 vs 24)
cannot complete client connection process

So I will stick with buggy version 0.109.2 for now as I don't want to check for configuration options a compile it myself. That's the main reason I switched from Slackware to Ubuntu anyway: got tired of compiling stuff! ;)

If you know of a way to fix this please let me know.

---

### Post by originalsynthesis on 2009-01-14
glad i found this thread, although it happened a little too late. I just recently upgraded Jack up to 0.116.2 from source. I want to try your deb, steve, but im wondering how to get rid of the new version without deleting and reinstalling from synaptic.  Is that going to be the only way to do it? Do i need to?  

Plus, im pretty miffed that ubuntu 8.04 doesnt support new versions of Jack, we need to bugger those guys into an upgrade for this.  

Thanks for the post, it saved me a lot of trial and error hell.

---

### Post by Sandsound on 2009-01-14
All I get is this :

JACK protocol mismatch (22 vs 24)

edit:
Been fumbling around with the .asoundrc and for some reason it works now, can't really say what it was that did the trick thou, but at least it works :-)

Thanks for making this deb

---

