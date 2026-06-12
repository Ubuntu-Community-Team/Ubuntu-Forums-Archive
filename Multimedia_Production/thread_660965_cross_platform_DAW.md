---
title: "cross platform DAW"
date: 2008-01-07
forum: Multimedia Production
---

### Post by staticvoid on 2008-01-07
...like audacity, which seems to have frozen development... but works on mac, windows and linux... cool!  :)

I like reaper, but its only for windows. I've never seen ardour, because I could never get JACK properly set up... and rose garden... is for MIDI mostly?

Anyway, what are** some good open source cross-platform digital audio work stations that I have not heard of?** So I can say "go to this website and download the software" to 20 people using different OS's.

Oh, and off topic, what would be a **good CMS for online music collaboration?**

Thanks a ton!

SV

---

### Post by eye208 on 2008-01-07
By the way, Reaper works very well with WINE.

Edit: Ah sorry, you probably knew that already. :)

---

### Post by staticvoid on 2008-01-08
yea, i've played around with it in WINE, but could never get my tascam us-122 working with it... but thats a whole nother story..  ;)

---

### Post by steevc on 2008-01-08
More of an Audacity clone than a full DAW, but I just read about this one today

[http://www.xowave.com/](http://www.xowave.com/)

I've not used it yet. It uses Java. I'm not too impressed with the layout of their web site, but there does seem to be some useful general recording information buried there.

---

### Post by dveble on 2008-01-08
energyXT2
[http://www.energy-xt.com/download/](http://www.energy-xt.com/download/)

---

### Post by staticvoid on 2008-01-08
XOwave looks like its not for windows... just mac and linux? and its a little wierd...

energyXT2... a demo version only? it looks super cool though... maybe if I had a tutorial on using it :) I love the demo projects though!!  :D and completly java based.

oh, do I need like a real time sound kernal or something..?

Thanks a ton for the suggestions guys :)

**keep 'em coming**, I'm checking all these out. energyxt2 is intersting for me , as MIDI is something I would love to get into.  

sv

---

### Post by staticvoid on 2008-01-08
i found [traverso]("http://traverso-daw.org/") on google... looks promising.. :D

still looking though.

open source, cross-platform DAW :)

sv

---

### Post by staticvoid on 2008-01-08
hmm... maybe not...

---

### Post by aeto on 2008-01-08
DAW? If you mean one program which does it all, a la Pro Tools, then no. However, JACK is a supreme being, surpassed only by God. JACK enslaves people like Ardour, Hydrogen, LMMS, Rosegarden and Audacity (or ReZound) to work together so that the world is once again peaceful. You can use Reaper under Wine, so that counts since Wine is after all a compatiblity layer. Many linux and non-linux musicians/producers swear upon it. JACK is just about the sample and period. Set your sample to 512 and period to 3 and you'll be flying and loving it.

[http://wiki.archlinux.org/index.php/Pro_Audio_Commercial_Alternatives](http://wiki.archlinux.org/index.php/Pro_Audio_Commercial_Alternatives)

All you want to know right there.

I lied.

Anyway, yeah, Traverso is promising. [www.traverso-daw.org](www.traverso-daw.org) I really love LMMS. Its UI is beaten by no other. Out-of-the-box VST(i) capability with just Wine is just amazing. Rosegarden? Well, these 2 apps (along with Muse and such) are like Cubase and such. For both MIDI and analog audio recording. Combine Ardour with LMMS and you have the sexiest couple. Before you know it, you may just be asking for too much :)

---

### Post by staticvoid on 2008-01-09
Hey!

Thanks a bunch for the reading. On my little, sony vaio pcg-tr3a, ardour JACK and LMMS might do the trick If I can get JACK set up, I don't want to fail a 3rd time :( 

 But, Perhaps I should have put more emphasis on cross platform then on DAW, as I will be the only one needing a DAW, and my friends need something like audacity, but better.

Thanks a ton, I'm reading about ardour more and LMMS now :)

sv

---

### Post by staticvoid on 2008-01-09
I got ardour open, it looks great!

**I still need a DAW that can run on windows, mac and linux though**, or at least two which work similiarly and are compatible.


sv

p.s.  how do I get the LMMS essentials all in one go? it says I need libc6.. hmm

> Essentials
    * Qt 3.x (multithreaded!)

---

### Post by aeto on 2008-01-09
:)

Nah, I guess currently only Audacity fits that requirement. In the future, maybe Traverso would catch up. Who knows ja? Aside from that, give Reaper one more try in Linux.

Btw, just pull in Ubuntu Studio. I remember you could do that from within an Ubuntu installation..or not. Makes things much easier and you'd have everything to try out!

Oh yeah, and Ardour won't really do *everything*, especially editing stuff. It's after all studio-grade HD recorder, not editor. So something like Audacity or ReZound still has to come into the equation.

---

### Post by staticvoid on 2008-01-09
Hi Aeto,

Yes, I hope audacity grows. I wonder what is the up and up on it. Maybe they need some help transalating the spftware? lol. I'd be glad to help out.

Yeah, I'll reaper again :) But,  I think if I get:

Ardour  
ReZound
and a driver for my tascam us-122 usb sound input box

then I'll be set. oh and again, **should I get like a sound realtime kernal or something?**

sv  :D

---

### Post by staticvoid on 2008-01-09
found this, if anybodies interested,

[http://youtube.com/watch?v=AxeE_Yg2UME](http://youtube.com/watch?v=AxeE_Yg2UME)

tell me about more daws :) I'm still interested :D

---

### Post by staticvoid on 2008-01-10
bump

---

### Post by aeto on 2008-01-11
That's about all there is to "DAW" among free and freeware alike, so all you could do is maybe wish everyone some good ol' luck :) 

And yes, stock kernels are as bad with audio work as Windows < XP. A higher timer frequency and real-time patches are needed to cut down on latency, mostly for recording purposes. You could however, run LMMS without one. It's the only app I use outside of JACK, aside from Audacity, using ALSA as output - and a normal kernel.

---

### Post by archolman on 2008-01-11
Computer Music magazine have a complete studio  on the cover DVD every month. it works for windows & mac:)

---

### Post by staticvoid on 2008-01-11
well, ok, i geuss thats all then..  :)

thanks a bunch!!

sv

and best of luck ya'll!!

---

### Post by steevc on 2008-01-14
I'm checking out an alternative solution in the form of pure:dyne

[https://devel.goto10.org/puredyne](https://devel.goto10.org/puredyne)

I'm not sure why the site uses https.

Basically it is a live distro with a bias to audio and video production. I had a quick look last night. It uses one of the minimalist window managers where you right click for a menu. I didn't get very far with it as I didn't work out how to get Jack to play audio cleanly and didn't manage to record anything. I need to learn more about how Jack works to sort those out. I also could not get it to run in a decent resolution on my nvidia board.

There is not too much in the way of documentation on that site. A friend used it on a course, so I will consult him.

If I get it working well there are options to run it from an existing hard drive partition for better performance.

---

