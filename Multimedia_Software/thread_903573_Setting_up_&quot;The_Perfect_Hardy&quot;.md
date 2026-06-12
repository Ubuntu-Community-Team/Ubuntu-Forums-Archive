---
title: "Setting up &quot;The Perfect Hardy&quot;"
date: 2008-08-28
forum: Multimedia Software
---

### Post by djRobbieF on 2008-08-28
Hey everyone!

When Hardy was released, I wrote a tutorial called "The Perfect Hardy", where I taught in a copy-and-paste style document how to do all the things we used to do with Automatix.

Stuff like installing DVD necessities, multimedia codecs, etc.

While it's very helpful for new Linux users to find that tutorial, I decided today that I would make it useful for other Ubuntu Hardy users as well, and build it into a Linux script.

So now, this terminal-based script is available [here]("http://www.category5.tv/content/view/124/77/") if you'd like a copy.

It's obviously free... just a bash script to simplify the installation of some great extras in Ubuntu Hardy.

[LIST=1]
[*]DVD Decoder and Necessary Software
[*]Multimedia Codecs and Restricted Extras
[*]A huge amount of true-type fonts
[*]wine
[*]Skype
[*]Spam filters
[*]Support for 7z, ZIP, Zip64, CAB, RAR, ARJ," echo "GZIP, BZIP2, TAR, CPIO, RPM, ISO and DEB archives in file-roller
[*]XDMCP support
[*]... and more
[/LIST]

I will keep the script up to date, and have intentions to grow it into something of a great resource tool for Ubuntu Hardy users.

It's nothing fancy; it's just a tool.  Hope you like it, and find it useful.  It should really help you out if you often have to install Ubuntu (OEMs, people who experiment, etc), as it will cut down a lot of time in setting up some of the extras.

All the best!!
-Robbie

---

### Post by obitori on 2008-09-23
Great script.  Saved me a lot of pain...One small glitch.  I'm running Ubuntu on an AMD64 machine and the script tried to install w32codecs instead of w64codecs.

Thanks for the help, tho.  The above didn't stop the rest from installing and I already had installed the right codecs for my box.

Obitori

---

### Post by djRobbieF on 2008-10-05
That's not a bug.  It was developed for Ubuntu 32-bit.  Sorry; I should have made that clear on the site!!  My bad.

However, I am already working on the updates for both the 64-bit and integration into Intrepid Ibex.  Intrepid support (32-bit) will be ready around the release of 8.10, where the 64-bit will be a bit later, but coming!!

Thanks!!

---

### Post by Vertoxic on 2008-10-05
> **djRobbieF said:**
> That's not a bug.  It was developed for Ubuntu 32-bit.  Sorry; I should have made that clear on the site!!  My bad.

However, I am already working on the updates for both the 64-bit and integration into Intrepid Ibex.  Intrepid support (32-bit) will be ready around the release of 8.10, where the 64-bit will be a bit later, but coming!!

Thanks!!
thx i cant wait for the 64 bit :)

---

### Post by obitori on 2008-11-17
djRobbieF:

I took a crack at a script for Intrepid.  Take a look at the attached and see what you think.  It uses Intrepid repositories and asks if you want to install w32 or w64codecs.  If it's useable, please use as you deem fit...

[http://taiotoshi.org/intrep64mm.sh]("http://taiotoshi.org/intrep64mm.sh")

Regards,

Obitori

---

### Post by djRobbieF on 2008-12-08
Hey obitori.
We actually deprecated "The Perfect Hardy" when Intrepid was released, and released the "perfectbuntu" script, which automatically detects Hardy/Intrepid, 32/64-bit, and runs accordingly.

Please see:  [http://www.category5.tv/content/view/164/77/](http://www.category5.tv/content/view/164/77/)

Sorry that we already did it  :)  But I'm sure your time wasn't in vain.  Let me know if there's anything you want changed on the perfectbuntu.

All the best,
Robbie

---

