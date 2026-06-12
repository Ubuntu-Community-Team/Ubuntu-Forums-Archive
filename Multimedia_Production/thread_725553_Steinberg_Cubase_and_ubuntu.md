---
title: "Steinberg Cubase and ubuntu?"
date: 2008-03-15
forum: Multimedia Production
---

### Post by JeppeV on 2008-03-15
Hey all:)

I'm giving ubuntu another shot(Didn't work out the last time:()

Do any of you guys know if I can run Steinbergs Cubase on ubuntu? Maybe with wine?

Oh, another question. What should I expect of wine? I've heard alot of different things about it, mixed opinions etc.

What about the x64? How is the support for it ?

I know this is alot of questions, but I will really appreciate any answers:)

Thanks.

---

### Post by NightwishFan on 2008-03-15
If you wish to see if a program works, try the Wine application database. Wine works better than I can hope for it to, and it works on 64-bit.

I no longer use it, however. I try to be Linux only for everything.

---

### Post by russo.mic on 2008-03-15
I run a commercial recording studio, and am forced to use either OS X or Windows, of which I choose Windows Vista.  The reason is because I'm using Steinburg Cubase 4, which is a absolutely wonderful recording platform.

I would be more than happy if they would release Cubase for linux.  RME has developed linux drivers for there high end interfaces, what is stopping MOTU, M-Audio (well, digidesign is stopping them), Edroil, or any other company from doing the same?  If enough companies supported the linux platform with there hardware, I can't think it would be far behind for Steinburg to do the same.  And they would be the first, as there not tied to an operating system like protools or logic.

That being said, I highly doubt you would be able to get Nuendo or Cubase to run under Wine or a VM.  the memory management is to intense.  Still, I would love to be proven wrong!  

Good Luck!

Russo

---

### Post by JeppeV on 2008-03-15
Wow, quick reply! Thanks guys. Sorry to hear about the bad support of the platforms though:(
Guess i'll dual-boot then.
Thanks again.

---

### Post by robeast on 2008-03-17
On the freebob wiki it says that RME has been hostile toward the idea of linux drivers. Is this outdated information?

---

### Post by Stochastic on 2008-03-17
> **robeast said:**
> On the freebob wiki it says that RME has been hostile toward the idea of linux drivers. Is this outdated information?

It's kinda outdated as the info on [www.ffado.org](www.ffado.org) is now the current info for freebob, but their stance on firewire hasn't changed.
I think russo.mic is referring to their PCI cards that tend to be well supported with ALSA drivers.


As for the main topic of this thread, Cuebase, I'd suggest giving Rosegarden a try.  I'm not a huge fan of it, but I'm also not a huge fan of Cuebase, and many say those programs are quite similar (but don't expect everything to work the same).

Ardour (and JACK) is still hands down what makes Linux Audio so great IMHO, totally stable apps that knock the socks off any mac/windows versions - particularly when it comes to multi-channel mixes and price points.

---

### Post by russo.mic on 2008-04-07
Well,  PCI cards that are supported by ALSA, sure, but why can't I get my MOTU 24 I/O in linux?

Why can't I get a Firewire interface such as as an M-Audio 1814, or whatever?

Why doesn't Digidesign compile a Linux kernel to run Protools on?  Then they could focus more on improving their product, and less on keeping up with OS X.  

Because of Manufacturer support.  ALSA ain't bad, JACK is for pro audio, but ASIO drivers that are DESIGNED FOR THE HARDWARE THEY'RE RUNNING are def. lower latency.  When I'm piping 16 or 24 channels of digital audio in and out of my computer realtime as the band is playing it, milliseconds start to matter quite a bit.

there is no reason all of this couldn't work in linux, and in alot of ways work better, should the hardware and software makers start giving us this choice.
Keep in mind, I'm talking about more than a personal project studio.  I'm running a commercial recording studio.  But right now I'm just pissed because I'm stuck on WinXP, and I hate it.  
As far as Cubase goes, the VST format of plugins is by far the lowest latency, and most processor efficient, and works best with Nuendo and Cubase as they invented it.  As far as the GUI goes, it takes some getting used to, but the definable shortcut keys and variable workspaces make it worth it.

Just my thoughts!  The only thing I love more than talking Linux is talking recording and audio stuff, the topic of combining the two is very interesting to me.  so please, any other opinions, lets keep this thread going!

Russo

---

### Post by thorgal on 2008-04-07
I think you should wait a bit more for ardour 3 to come up and mature a little. The big thing with ardour 3 is MIDI editing support.

Regarding VSTs ... this is a bit of a lottery ... I run successfully Addictive Drums and Pianoteq as dssi guests (dssi is an open plugin standard and provide a VST host called dssi-vst in which you can run VSTs) but other VSTs fail miserably, which I don't explain at all since most of them are closed-source. Misuse of the Steinberg API by VST plugin devs ?? no clue!

Anyway, switching to linux requires at least one thing : giving up windows habits and work the best out of what linux can offer. It's a steep learning curve if you did not grow up with unix based systems ... but not impossible to do. It is definitely worth the effort.

---

### Post by russo.mic on 2008-04-09
As far as VST succeeding or failing, check your VST version number in the plugin's info vs. what host your using.  For example, I have a set of plugins that is a bit later in version compared to what my host is running.  They worked, but whenever the GUI was visible, the entire program would run TERRIBLE!!!

as far as switching to linux and such, When you realize that there could easily be a distro JUST FOR THIS PURPOSE, I think it could be made to be pretty easy.

---

### Post by senorkasio on 2008-04-10
At the risk of being a Judas, you might want to look into running Reaper 2.0 on Open Suse.  I've tried Reaper under windows and it's a very powerful DAW.  Based largely on Sony Acid.  My friend has tried it on Suse.  He says the latency is wonderful.  Unbelievably low.  It might work on Ubuntu as well...  Worth looking into :-)

I'm a cubase user myself and I'm not in the mood (or too old and cranky) to plunge into a whole new workstation so I'm holding off.  I love Ubuntu though and the second they make Cubase or Nuendo available, I'm on it!

SrK

---

### Post by russo.mic on 2008-04-12
I suppose the problem is compatibility.  Clients want to know they can fly the tracks to ProTools, Logic, or whatever else.  Do Ardor or Reaper do OMF files?  Anybody know?  

Also, I HAVE to be able to do at least 24 channels in and out.  And frankly, I'm about to have to upgrade to more.  I don't know of any hardware that ls linux friendly and capable of that.  RME stuff maybe?

Russo

---

### Post by yrrapt on 2008-04-25
Im currently trying set up a mini studio using a phonic helix mkII 24 mixer and ardour. But since you were saying about your profesional studio and how linux is unsuitable i thought id post a link to this article, i dont know if any of you guys have seen it, but here it is:
[http://www.soundonsound.com/sos/feb04/articles/mirrorimage.htm](http://www.soundonsound.com/sos/feb04/articles/mirrorimage.htm)
Deffinetly some food for thought

---

### Post by longcatspace on 2008-05-21
well thankyou folks, it's refreshing to read this thread,

i'm a musician who records music & edits video every week, and i'm dipping my toes into ubuntu, currently i'm assuming that i'll still keep my XP cubase/vegas machine until linux can give me the same/better and it's interesting to read what you cats have to say...

my ubuntu is very new and on my old machine, primarily networking,

i look forward to the day when ubuntu (or another linix divo) runs on all my machines, with my M-audio card happily driven through linux, a cubase or another linux app for audio and a vegas or another linux app for video...

hurry on that day x

---

### Post by Miano on 2008-05-24
i too am also a musician who recently switched to Ubuntu and am loving it.  however the same problem is haunting me; i miss my cubase!

---

