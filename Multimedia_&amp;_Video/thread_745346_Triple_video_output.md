---
title: "Triple video output??"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by Rizla on 2008-04-04
**This post could be related to an Ubuntu bug filed at**: 4 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Does anyone know if its possible to have 3 modes of output with ubuntu?  I currently have a dual monitor setup via my NVIDIA card.  I've been using it for over a year now and works great.  I got a projector setup in the living room now and want to pipe my desktop to it whenever i feel like messing around.  I have my standard vga port on my motherboard that I want to use with a vga > component cable.

Is it possible to set up a mirror of my desktop, and ouput it via the onboard vga with a different resolution?

Awkward question.. i know.

---

### Post by lavinog on 2008-04-04
would a video multiplexer (splitter) work better instead of using the on board video?

---

### Post by Rizla on 2008-04-04
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **lavinog said:**
> would a video multiplexer (splitter) work better instead of using the on board video?

I thought about that, but the fact is i have dual monitor out on my vid card.  If i were to use a multiplexer on one of the outputs, i'd only get one screen to show up.  Also the resolution settings would probably not suite the 1080i input on the tv..  hence me just wanting to use the onboard and have seperate resolution settings for that. 

I have a feeling this wont work..

---

### Post by Whiffle on 2008-04-04
Sure you can make it work. its linux.  It just might take a while ;) 

There may be a GUI for this, I don't know.  But if it were me, I'd be looking into making an Xorg.conf that includes your onboard card and its settings.  

This is where I would start:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

---

### Post by Rizla on 2008-04-04
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Whiffle said:**
> Sure you can make it work. its linux.  It just might take a while ;) 

There may be a GUI for this, I don't know.  But if it were me, I'd be looking into making an Xorg.conf that includes your onboard card and its settings.  

This is where I would start:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

Very true, but man, this past week i've lost a lot of sleep setting up my new server because linux wouldnt play nice with certain things.  Everything's been a learning process.  I feel like im going through information overload.  BUT, once everything is configured, its a beaut!  I'm never going back to windoze. EVER!  

The funny thing is there's no real NEED for this.  Its just a quirkly little thing I want to do.  

Linux is truely a tinkerer's OS.   

I'll take a look at that link.  I dont even have my cable ordered yet so I may have created this thread a bit too early.

---

### Post by lavinog on 2008-04-04
> **Rizla said:**
> 
I thought about that, but the fact is i have dual monitor out on my vid card.  If i were to use a multiplexer on one of the outputs, i'd only get one screen to show up.  Also the resolution settings would probably not suite the 1080i input on the tv..  hence me just wanting to use the onboard and have seperate resolution settings for that. 

I have a feeling this wont work..

does your onboard card support HD output?
is there really a vga > component cable? where does one find one?

I think in order to mirror 2 screens of desktop onto a third screen you will have to reduce the resolution of your 2 screens so the 2 screens can fit onto one...in other words you will have no benefit of running two screens if you want the third screen.
To my knowledge you can't have 2 monitors mirror each other at different resolutions.

Mirroring usually is only available through the same video card also...to mirror the output from one video card to another could probably be done with software but would put too large of a strain on the cpu to be useful 

Does your projector offer Picture by Picture...if it does you could use two multiplexers that way.
just make sure you get the right picture on the right side...boy could that be interesting.

---

### Post by Rizla on 2008-06-06
> **lavinog said:**
> does your onboard card support HD output?
is there really a vga > component cable? where does one find one?

I think in order to mirror 2 screens of desktop onto a third screen you will have to reduce the resolution of your 2 screens so the 2 screens can fit onto one...in other words you will have no benefit of running two screens if you want the third screen.
To my knowledge you can't have 2 monitors mirror each other at different resolutions.

Mirroring usually is only available through the same video card also...to mirror the output from one video card to another could probably be done with software but would put too large of a strain on the cpu to be useful 

Does your projector offer Picture by Picture...if it does you could use two multiplexers that way.
just make sure you get the right picture on the right side...boy could that be interesting.

Ridiculously late reply to this, but i've given up on the idea.  I decided to go with a NMT (network media tank), specifically the iStarHD to watch the videos on my projector.  Initially i just wanted to display the content of my comp onto the projector and watch movies that way, but it woudl have been a bit cumbersome.  

I stumbled apon these new devices called Network media tanks.  They're basically headless linux appliances the size of an overweight dvd case and stream HD/stanard def/xvid/mpeg/avi/etc (practically every video codec out now) to whatever input source you want.  It offers HDMI 1.3 out or standard VGA.

My projector didnt have a HDMI input (few years old), so i bought a VGA to component cable.  Yes, they exist, you're just going from analog to analog.  I picked them up at monoprice.com for cheaps (awesome site for cheeeap cabling, **** monster cables).  And now i've got all my dvd's playing off my nas to the projector. 

No one will probably read this so i dunno why i'm even responding.. oh yea its late and i'm toasted.

---

### Post by lavinog on 2008-06-11
> **Rizla said:**
> 
No one will probably read this so i dunno why i'm even responding.. oh yea its late and i'm toasted.
Ha, I read it!
cool idea...i should check these nmt things out.

---

### Post by zieglerj on 2008-06-21
I'm looking to do a similar thing with my nvidia but only mirroring one of my monitors to my TV through the s-video port. I've even figured out a way to get sound but I just cant get my nvidia to accept three outputs or even a mirror setup of one.

---

