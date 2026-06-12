---
title: "jackd 1.0.9.xx &amp; alsa 1.0.16.xx-any idea WHEN?"
date: 2008-04-14
forum: Multimedia Production
---

### Post by funkster on 2008-04-14
Hi there,
thought I'd ask if anybody is in the know about the release/packaging for Ubuntu repos of above mentioned packages?
Ubuntu is now a few version behind the last stable releases of alsa and jackd, but unfortunately I haven't yet been able to compile my own packages. So it would be nice to know if these are planned (surely must be?) for inclusion on gutsy still?

TIA folks
Raphael ;)
:guitar:

---

### Post by Stochastic on 2008-04-15
If memory serves correct, the ubuntu policy is that new releases are not included into the repositories (only updates) unless there is a major security fix or huge bug fix.  On the positive side it looks like both of these versions you're requesting will be in use in Hardy's April 24th release (though alsa version numbers show a mix of 1.0.15.xx & 1.0.16.xx at [http://packages.ubuntu.com](http://packages.ubuntu.com) depending on which alsa package you're looking at).

---

### Post by funkster on 2008-04-15
Thanks a lot stochastic.
You seem to be a very knowledgeable guy. Are you participating in the dev. process?

Cheers
Raphael ;)

---

### Post by funkster on 2008-04-15
Well, alsa 1.0.16 installed without a hickup. Nice.
But jackd & qjackctl won't install because of an seemingly dependency problem concerning 'lic6'. libc6 however IS installed on my system (incl. dev files). So once again I'm lost.

The exact message in GDebi is: ***"Error: Dependency is not satisfiable: lic6"*** (for both jackd & qjackctl
Anybody in the know how to solve this?

Raphael ;)

Edit:
Never mind. I have added the hardy repo to my sources and all has been installed, lean 'n mean. :D 
No to go solve the performance probs I have.

---

### Post by Stochastic on 2008-04-15
Nope, I'm no dev - though I've been playing around with an icon set (similar to my avatar) that might make its way into the DIY theme that MMA wants for Ubuntu Studio one day.  I just have been working with linux long enough that I know my way around, and this forum is my way of giving back to the community that's saved me thousands in software costs for my studio (leaves me more money for nice condenser mics).

Oh and you really shouldn't mix your repos!  Though it may solve a temporary problem, it can cause really nasty bugs and security issues without any fix.  Danger! Danger!

---

### Post by funkster on 2008-04-18
You're prbably right. Mixing repos is surely not THE thing to consider. Though I think that in my test case scenario it doesn't matter that much.
I'm using some GNU/Linux flavor since almost a year know, and while I find so many things so pleasant, intriguing, better working, I'm still not able to compile my own packages. 
And then of course the audio side of things is the last missing piece for me, for which I absolutely need Windows. Audio useability/stabilty/complexity is the one thing I don't really grasp yet under linux. Not even talking about monetary reasons (what to do with all the aoftware I "bought" for windows? Some licences are transferable/sellable, but many are not). 
And then I have some awful performance problems, which I can't get solved apparently. It's a pity. 
But yeah, give some of my money back to buy again into some more hardware (mics, Outboard FX, synth, a new GUITAR pleeeeease :D )

Cheers
Raphael ;)

---

### Post by Stochastic on 2008-04-18
No, mixing repos is VERY DANGEROUS!!!!  I don't think I was emphatic enough about this the first time I said it.  DON'T DO IT!!!  Do you really need the newer versions of these drivers?

The linux world of audio is a very flexible one but with that comes inherent complexities that take a bit to understand.  I'd recommend running Ardour, Rosegarden, Hydrogen, and Jamin to start and as you work you'll stumble upon feature after feature after program after program that will help you along the way.

Oh and to compile your own packages you'll need to make sure the dev versions of all the dependant libraries are installed before you begin, then just follow any instructions given in the README file.  I'd start with compiling a non-essential program or two to get the hang of things before attempting to muck about with compiling your sound driver.

---

