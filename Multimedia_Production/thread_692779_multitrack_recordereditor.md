---
title: "multitrack recorder/editor?"
date: 2008-02-10
forum: Multimedia Production
---

### Post by MadsRH on 2008-02-10
Hi
I'm a Gusty user looking for and multitrack recorder/editor and some notation software.

I use Cubase SX on Windows and I also know macs Logic. I've heard about Ardour on Ubuntu Studio, but do I need the Studio edition to run multitrack software?

I use Finale and Sibilius for music notation. Has anyone tried on of these on Wine or is there a worthy substitute for linux?

Thanks for reading/replying :) 
**MadsRH**

---

### Post by xarquid on 2008-02-10
No, you do not need the Studio Edition to run multitrack software at all.

Ardour is the closest to Cubase SX. Actually, it is considered one of its arch-rivals in many music circles around the globe. An article worth reading:

[http://weblog.infoworld.com/dickerson/001063.html](http://weblog.infoworld.com/dickerson/001063.html)
-and-
[http://blogs.oreilly.com/digitalmedia/2007/05/free-opensource-multitrack-rec.html](http://blogs.oreilly.com/digitalmedia/2007/05/free-opensource-multitrack-rec.html)

Where they note its "becoming" in Info World. Pretty powerful article if you ask me.

I would stick with Ardour.

And to tell you the truth, I am running Hardy Heron. It is in Hardy Heron's repositories...if it's not in Fiesty's available for easy installation via synaptic -- it might be soon with the soon-to-be upgrade.

It should be pretty easy to find a Debian (.deb) build of Ardour somewhere out there on the web for an easy install.

Sincerely,

Craig Huffstetler / xq / xarquid
Ubuntu SC Team Leader
"One Carolinian at a time..."

---

### Post by xarquid on 2008-02-10
I did a little bit more research into this for you.

I believe Ardour was available as early as Dapper and was still available in Feisty. This is according to repos I am looking at. It should be in the Universe repository, so if this not enabled, please make sure it is "checked"  in Synaptic or NOT commented out in your sources.list file. 

Then do an apt-get update before looking for it. You should clearly see it in Synaptic for apt-get install ardour for easy installation. 

If not, you may have to *temporarily *add the Feisty Universe Repository to your apt sources.list and grab it from there. This will ensure one of the newest copies for you and I think the best bet...
(See [this thread]("http://ubuntuforums.org/showthread.php?t=470154") for some information on what other users encountered concerning this).

Sincerely and hopefully,

Craig Huffstetler

P.S. I got two friend's opinions and am going to link what they have used in the past below (they currently use Ardour). But, I have a philosophy of trying most things and finding what fits for you. So here you are just in case you have the same philosophy as myself:

[http://createdigitalmusic.com/2005/02/18/a-free-cubase-rosegarden-10-pclinux/](http://createdigitalmusic.com/2005/02/18/a-free-cubase-rosegarden-10-pclinux/)

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

---

### Post by nalmeth on 2008-02-10
I think he's running gutsy.. In any case Ardour is available in the repos.

To use Ardour, you will need to install the JACK audio engine. Install the qjackctl package that configures and starts JACK, and all other dependencies should be installed. 

You may want to install some/all of the LADSPA plugins. If you want to use VST's with Ardour, you will have to compile Ardour with VST support because of the lisencing restrictions. I would start with the LADSPA plugins.

I use TuxGuitar for notation, I'm not sure if it is equivalent to the programs you're used to, nor have I tried them in WINE.

There are many alternatives, just search for notation + linux

---

### Post by Stochastic on 2008-02-10
Yes, ardour is god when it comes to multitrack audio, though there are a couple other options out there.

UbuntuStudio is not needed to run ardour or any other audio app, but it does help.  If you find yourself getting bad latency times or dropouts in your audio I'd install UbuntuStudio.  Its main feature (besides the sweet theme) is its realtime kernel, which can give audio processing a higher priority in the kernel stack.

As for notation, I've heard stories that finale and sibelius can be run through wine but I haven't bothered to try.  I personally write all my scores with a lightweight text-based notation program called lilypond.  It's quite flexible and once you get the hang of things it's faster to write with than finale or sibelius - but the learning curve (as with most text-based apps) is a little steep.  There are some native graphical notation editors for linux but from what I've experienced, heard, and seen, they're nowhere near finale or sibelius.

hope this helps, and welcome.

---

### Post by MadsRH on 2008-02-11
Thank you so much for all your answers - It's a great help.
[B]
MadsRH[/B]

---

### Post by lapcat66 on 2008-02-11
Since version 2, I've found Ardour to be excellent as a hard disk recorder.  If you want to edit midi in a notation window, Rosegarden is very good.  They can be sync'ed together with jack, meaning they act like one app.  

Also, I'd like to name-check Hydrogen for drums, and if you're into synths, QSynth and AmSynth.

I agree with Stochastic's comment about having fewer issues installing from the Ubuntu Studio dvd.

---

### Post by Liet_Kynes on 2008-02-11
I just checked and the version of ardour in the feist repos are 0.99 
:|

---

### Post by Stochastic on 2008-02-11
> **Liet_Kynes said:**
> I just checked and the version of ardour in the feist repos are 0.99 
:|

I thought it was already discussed that MadsRH is a gutsy user.

---

### Post by MadsRH on 2008-02-11
> **Liet_Kynes said:**
> I just checked and the version of ardour in the feist repos are 0.99 
:|

With Hardy comeing soon I'm sure the repos is up to date ;)
Thanks again for shareing your knowledge **MadsRH**

---

