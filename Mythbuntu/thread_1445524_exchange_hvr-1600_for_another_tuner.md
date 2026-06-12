---
title: "exchange hvr-1600 for another tuner?"
date: 2010-04-02
forum: Mythbuntu
---

### Post by bnhrobotics on 2010-04-02
I have about 2 weeks left on my 30 day return policy for the HVR-1600.

1) The remote does not work.
2) Digital tuning is flaky unless its in my 3 core machine (2.8 GHz single core misses frames. 2.2 GHz is minimum specified requirement)
3) I just put the card into my 3 core desktop... now it does not resume from sleep properly.

Can anyone recommend a tuner that works well with both ATSC and NTSC? I wouldn't mind switching it while I still can for something that might be better supported. And something that I can have in a slower  computer.

Thanks =)

---

### Post by Lepy on 2010-04-02
If you can return the 1600 for no restocking fee and possibly exchange for a version with the usb receiver, that might be your best bet. I can't comment on any other cards though, until the 4 tuner Ceton is released, that is!

I don't think you'll get good results recording HD material using your single core machine with any tuner, unless you use a network tuner (HDHomerun) or recording is the only thing it will be doing at one time.

You might be able to get better results with the card if you manually edit some options in the drivers before compiling. And for resume, if you're running the 32 bit version of mythbuntu with an nvidia card, add vmalloc=256m to the kernel boot options and make sure you have NvAGP "1" set in your xorg.conf.

---

### Post by bnhrobotics on 2010-04-03
That sounds a tad bit out of my ability range. Is that difficult to do for someone who has never compiled a driver before?

I am starting to regret sending the HDhomerun back....

Perhaps I'll go with the HVR-1600 with USB. I just hope it works in the older computers and doesnt give me trouble resuming from a suspend.

---

### Post by Lepy on 2010-04-03
Not at all! The wiki has an excellent guide for installing the latest drivers: [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

Since it seems your hvr is working well (besides when being used in the slower machine), you shouldn't need to tweak the drivers at all, just follow the guide. If you're interested though, you could muck about in the cx18*.c files before executing the make command.

Anyway, don't regret returning the HDHomerun until you've tried your other options. If you can get a usb model of the hvr-1600 with no restocking fee, your remote problem should be solved. You should explore the vmalloc=256m and NvAGP "1" settings I recommended (assuming your using an nvidia card) before throwing in the towel on your 3core machine suspend problem. As for your slower machine, you'll just need to decide if you can get it working how you want or if a multi-system setup will work better. 

I hope this helps you get a nice mythtv system up and enjoying the programming you want to watch.

---

### Post by klc5555 on 2010-04-03
But if you really want to unload the 1600 because of its subpar QAM performance, but want something that should just work out-of-the-box on mythbuntu (US only), the pchdtv-hd5500 may be a pretty good choice at $99. 

There may be two caveats --unlike the 1600, there is only one input connection to handle both atsc and ntsc. This is only an issue if your analog is coming through a STB or digital adapter, since obviously QAM signals won't pass through the STB.

Second, analog signals are handled through software decoding, not hardware decoding, so that it requires a bit of CPU to do analog. To keep the load to a minimum, analog is encoded by default to RTJPEG. But the analog driver has become very reliable since kernel 2.6.25, and the analog output seems equal in quality to that of a 1600 (better than that of a PVR 150) (All of which cards I actually use, plus the AverMedia A180 ...) QAM is handled flawlessly by the 5500.

Anyway, check the 5500's wiki page at [http://www.mythtv.org/wiki/PcHDTV_HD-5500](http://www.mythtv.org/wiki/PcHDTV_HD-5500) for information. I just wish the pchdtv folks would crank out a PCI-express version of the card.

---

### Post by JMcFly on 2010-04-03
Or try running 9.04 instead of 9.10, my HVR-1600 worked perfectly under that version with a 2.4ghz P4.

---

### Post by klc5555 on 2010-04-03
> **JMcFly said:**
> Or try running 9.04 instead of 9.10, my HVR-1600 worked perfectly under that version with a 2.4ghz P4.

It does for some. If the cx18 driver is patched and their QAM signal is strong enough. I still use 9.04 (mythtv 0.21) and finally relegated my two 1600s to analog-only STB capture duty on a secondary backend. QAM on them just wasn't worth the hassle. Particularly when my AverMedia 180s and the hd-5500s could all do QAM perfectly.

---

### Post by tgm4883 on 2010-04-03
> **klc5555 said:**
> But if you really want to unload the 1600 because of its subpar QAM performance, but want something that should just work out-of-the-box on mythbuntu (US only), the pchdtv-hd5500 may be a pretty good choice at $99. 

There may be two caveats --unlike the 1600, there is only one input connection to handle both atsc and ntsc. This is only an issue if your analog is coming through a STB or digital adapter, since obviously QAM signals won't pass through the STB.

Second, analog signals are handled through software **encoding**, not hardware **encoding**, so that it requires a bit of CPU to do analog. To keep the load to a minimum, analog is encoded by default to RTJPEG. But the analog driver has become very reliable since kernel 2.6.25, and the analog output seems equal in quality to that of a 1600 (better than that of a PVR 150) (All of which cards I actually use, plus the AverMedia A180 ...) QAM is handled flawlessly by the 5500.

Anyway, check the 5500's wiki page at [http://www.mythtv.org/wiki/PcHDTV_HD-5500](http://www.mythtv.org/wiki/PcHDTV_HD-5500) for information. I just wish the pchdtv folks would crank out a PCI-express version of the card.

Exactly right (I did correct one part though). 

I've got the 1600 and 5500 and although I only use them for digital they both work really well. Running Mythbuntu 9.10

---

### Post by bnhrobotics on 2010-04-03
Thanks for all of the suggestions!

Lepy: Can you tell me what those optimizations do?


So right now I am considering either getting another HVR-1600 with USB remote, or the hd-5500.

Would you expect that I could tune the analog ok with a 2 MHz or 2.8 MHz machine on the hd-5500 since its using the software encoding? 2 MHz was fine with the HVR-1600.

I mentioned in another thread that I got the tuner to record "Life" on the discovery channel which is NTSC through my cable company. (thats why I sent the HDhomerun back originally). In a month I'll be getting a new apartment and won't be paying for cable so I'll be using OTA ATSC. I suppose that now I am having issues with QAM on the HVR-1600. Is OTA on the 1600 more likely to work with the HVR-1600? I'd like to be able to record the rest of this discovery series, but pretty soon NTSC recording will be useless to me until I am done with school and can afford cable.

Thanks for all the info. =)

---

### Post by bnhrobotics on 2010-04-04
So if I understand correctly 

HVR-1600
analog hardware encoder. digital software encoder

HDTV 5500
analog software encoder. digital hardware encoder

Is that right? Can anyone give me a good comparison? Thanks

Edit: I just read that the 5500 is ALL software for both analog and digital. Is this true? If I cant see perfect digital with the HVR-1600 in a 2.8 GHz machine, I wouldn't be able to with the 5500 either then?

---

### Post by JMcFly on 2010-04-04
> **klc5555 said:**
> It does for some. If the cx18 driver is patched and their QAM signal is strong enough. I still use 9.04 (mythtv 0.21) and finally relegated my two 1600s to analog-only STB capture duty on a secondary backend. QAM on them just wasn't worth the hassle. Particularly when my AverMedia 180s and the hd-5500s could all do QAM perfectly.I was using the ATSC tuner for OTA signals, Comcast in my area changes QAM assignments too often to be useful (and they only broadcast the OTA channes in QAM anyway, so a cheap antenna hidden behind my TV did the trick).

---

### Post by Anita_Tsai on 2010-04-04
> **JMcFly said:**
> Or try running 9.04 instead of 9.10, my HVR-1600 worked perfectly under that version with a 2.4ghz P4.
You can do!

---

### Post by matt06 on 2010-04-05
> **bnhrobotics said:**
> Would you expect that I could tune the analog ok with a 2 MHz or 2.8 MHz machine on the hd-5500 since its using the software encoding? 2 MHz was fine with the HVR-1600.

Just to be clear, playing back HD stuff depends more on your video setup than your capture setup, but different capture devices can use different formats that can potentially affect playback as well.

Keep in mind also that there are people getting satisfactory HD playback using Intel Atom processors under 2.0GHz and NVidia ION graphics since VDPAU playback profiles usually require very little CPU.

---

### Post by tgm4883 on 2010-04-05
> **bnhrobotics said:**
> So if I understand correctly 

HVR-1600
analog hardware encoder. digital software encoder

HDTV 5500
analog software encoder. digital hardware encoder

Is that right? Can anyone give me a good comparison? Thanks

Edit: I just read that the 5500 is ALL software for both analog and digital. Is this true? If I cant see perfect digital with the HVR-1600 in a 2.8 GHz machine, I wouldn't be able to with the 5500 either then?

Wrong


HVR-1600
Digital & Analog tuner. analog hardware encoder. 

HDTV 5500
Digital & Analog tuner. analog software encoder.


Digital signals already come in mpeg format, so the card is just writing them to the disk. There is no encoding necessary.

---

### Post by bnhrobotics on 2010-04-12
Ok I have some good news and bad news. I made the exchange to get another hvr-1600 but the USB IR model. Good news is I figured out how to get VDPAU working and now I can play digital television without any trouble.

The bad news is that the analog picture quality on the new tuner is terrible compared to the old. I have cable television, yet I have ghosting with this new card. I also have a band of horizontal lines which is most noticeable on the ONE channel that I was interested in recording. This happened with the old tuner, but then I moved my graphics card away from it and it worked fine. No such luck with this one. Ill only have cable for a short while longer so I might remove the graphics card altogether while I am recording this analog show. However, I don't know if that is going to fix it or if the ghosting will go away.

Is there anything that I can do?

Thanks

---

### Post by matt06 on 2010-04-12
I have the interference problem and some "channel bleed" where certain analog channels appear ghosted on other channels.  Luckily they are channels that I rarely, if ever, use.

Like you said, resolving it could be as simple as moving the card inside the box itself or you might have to determine if it is indeed interference or signal issues before you can address it.

---

### Post by bnhrobotics on 2010-04-12
Well, I configured it in every combination possible and the way I had it with the old HVR-1600. Same problem each time. I also tried connecting the cable directly to the tv. It had no ghosting or other issues... so its definitely a problem with this card. =(  I wonder if its worth sending back at this point...

---

### Post by thinktyler on 2010-04-13
I'm trying to get my to work as well. I notice the ghosting pictures, I dumped Media Center windows 7, for mythubuntu, but I can't fix this problem.

Is it interference from a graphics card?

---

