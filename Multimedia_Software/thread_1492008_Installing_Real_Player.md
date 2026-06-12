---
title: "Installing Real Player"
date: 2010-05-24
forum: Multimedia Software
---

### Post by peterconway on 2010-05-24
Hi,

I'm running 9.04 and having problem installing Real Player(any version).I've tries using Synaptic it can't find realplayer in repository(Medibuntu is installed & ticked in 3rd party repository, two versions there-one with 'source' after Medibuntu?)

Also tried d/loading realplayer.deb from site and saving to d/top - then when trying to install I get error message 'Error: Dependency is not satisfiable: libasound2 (>> 1.0.22)' Tried to make it executable by entering 'chmod a+x RealPlayer11GOLD.bin' in terminal, but says can't find file? 

I have gone through the help at [https://help.ubuntu.com/community/RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods)
but still can't get it to install and show in a repository or in applications. I've installed the Codecs and and many stations play ok.

My main requirement is for playing Internet radio - a lot of stations use Realplayer. Also it's pride thing now!!

Hope some one can help me with what I'm doing wrong/missing!?

Peter

---

### Post by WinterRain on 2010-05-24
[Here]("http://packages.ubuntu.com/search?keywords=libasound2&searchon=names&suite=lucid&section=all") is libasound2.

---

### Post by peterconway on 2010-05-24
Hi wnter rain,

 Installing libasound2 cured the fault, then I could install Realplayer in the terminal.
 
Thanks for the help!

Peter

---

