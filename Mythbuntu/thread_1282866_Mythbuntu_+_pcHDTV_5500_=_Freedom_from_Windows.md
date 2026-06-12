---
title: "Mythbuntu + pcHDTV 5500 = Freedom from Windows?"
date: 2009-10-04
forum: Mythbuntu
---

### Post by cat2005 on 2009-10-04
_For those using, or knowledgeable of, the following tuner card:  pcHDTV 5500 model_

I have a question:**  Can I use it to receive digital cable TV?** 

 By "digital cable TV" I mean this:  I have a cable coming from my wall.  I can plug it into my Hauppauge PVR-150 (in Windows) and watch local and non-local channels.  Of course, those are analog channels even though my provider (Time Warner) is digital.

I want to do so with the 5500 but receive the digital channels instead of, or in addition to, the analog channels.  Please note, I am only interested in the standard definition stuff coming through the cable, not over-the-air stuff, high definition stuff, etc.  

**Simply put, I want to do in Mythbuntu with a digital cable signal what I could do in Windows with an analog cable signal:  watch and record TV.**

I am sorry if this question is insulting simple, but I have little knowledge of these things and even less understanding.  I would really appreciate your insight.  

TV is the only reason I need Windows.  If I could watch and record TV in linux, then I could (and would) watch the door hit Window's butt on the way out!  I would no longer need Windows!   [U]


Here are my system specs[/U]:
 
1 - Mythbuntu 9.04
2 - p4 cpu @ 2.4 ghz @ 300 - 400 bus
3 - 1 gb ram @ 300 - 400 bus
4 - Nvidia GeForce FX5200 @ 128 mb
5 - Asus mobo P4S800 (PCI support, no PCIe support)
6 - No Sound Card / Blaster
7 - Hauppauge PVR 150 (currently not setup with mythtv, but soon plan to replace this with something to capture digital, or both digital and analog)
8 - Want to display TV output on my computer monitor, currently using standard VGA cable to connect computer to monitor
9 - Speakers and sub-woof
10 - Digital cable via Time Warner

---

### Post by blackoper on 2009-10-06
the pchdtv 5500 will only tune unecrypted qam channels from time warner. If they encrypt their channels in any way you won't get them. If you havn't bought the pchdtv 5500 yet I would recommend getting the silicondust hdhomerun as it's dual tuner and it is networked and doesn't need a pci slot

---

### Post by ConXtionS on 2009-10-06
Howdy
 
I am pretty new to all of this so I could be wrong.... However I happen to own both windows and linux so I have a little bit more to compare than you do.
 
First off, anything I want to watch or record in windows I can now also watch in record in linux. thats the short answer...
 
As for "DIGITAL" .....
 
I have noticed that term gets thrown around in a alot of different ways.... so I want to be clear in my answer to you.
 
OVER THE AIR, OR ANTENNA DIGITAL signals can be captured and watched easily on myth tv. You simply tell the tuner what to watch for and off you go.
 
DIGITAL from your cable provider is a WHOLE DIFFERENT DEAL.....
 
There form of digital really means you "have to use our cable box to decode" the signal.
 
Some complanies have some truely digital programming that they do not require a set top box for, but not many channels in my experience.
 
that said, all is not lost.
 
You can hook your set top box up to both the windows version or myth tv.
 
to make it sound simplier than it is, you hook the box up to your cards input, and you have this thing called an *IR BLASTER* that takes the signal from your remote control, spins it round and round and sends the correct signal to the set top box. Then you can record, watch, whatever program the box sends to mythtv.
 
I hope that made some sense and helpd you bro.
 
Like I said, I am not smart, but at least for me, the linux stuff is managing to do anything the windows stuff can do. Its a lil more FRUSTRATING, but it does work.
 
Good luck
 
Jim

---

### Post by cat2005 on 2009-10-06
> **blackoper said:**
> the pchdtv 5500 will only tune unecrypted qam channels from time warner. If they encrypt their channels in any way you won't get them. If you havn't bought the pchdtv 5500 yet I would recommend getting the silicondust hdhomerun as it's dual tuner and it is networked and doesn't need a pci slot


What do you mean by "dual tuner"?

/ sorry, noob here

---

### Post by cat2005 on 2009-10-06
> **ConXtionS said:**
> Howdy
 
I am pretty new to all of this so I could be wrong.... However I happen to own both windows and linux so I have a little bit more to compare than you do.
 
First off, anything I want to watch or record in windows I can now also watch in record in linux. thats the short answer...
 
As for "DIGITAL" .....
 
I have noticed that term gets thrown around in a alot of different ways.... so I want to be clear in my answer to you.
 
OVER THE AIR, OR ANTENNA DIGITAL signals can be captured and watched easily on myth tv. You simply tell the tuner what to watch for and off you go.
 
DIGITAL from your cable provider is a WHOLE DIFFERENT DEAL.....
 
There form of digital really means you "have to use our cable box to decode" the signal.
 
Some complanies have some truely digital programming that they do not require a set top box for, but not many channels in my experience.
 
that said, all is not lost.
 
You can hook your set top box up to both the windows version or myth tv.
 
to make it sound simplier than it is, you hook the box up to your cards input, and you have this thing called an *IR BLASTER* that takes the signal from your remote control, spins it round and round and sends the correct signal to the set top box. Then you can record, watch, whatever program the box sends to mythtv.
 
I hope that made some sense and helpd you bro.
 
Like I said, I am not smart, but at least for me, the linux stuff is managing to do anything the windows stuff can do. Its a lil more FRUSTRATING, but it does work.
 
Good luck
 
Jim


Yes, cable is confusing but your explanation did help somewhat.  Related question:  Am I required to have an IR blaster, or is it just a nice extra?

---

### Post by ConXtionS on 2009-10-06
> **cat2005 said:**
> Yes, cable is confusing but your explanation did help somewhat. Related question: Am I required to have an IR blaster, or is it just a nice extra?
 
 
I dont suppose you are REQUIRED to have one, but it makes changing the channel alot easier if you have your myth backend and settop box in a closet or something.
 
I think all the ir blaster really does is convert the signal coming from the REMOTE us will use with your tv card (myth tv box) to something that can also control the cable companies set top box.
 
mine is like a tiny tear drop of plastic. you mount it close to your set top box, and then you can control the myth tv box and the set top box with one remote. PLUS
 
if you want to record channel 303 but are not home, myth tv sends the commands out that same blaster to get your set top box on the right channel so myth can record your show.
 
 
Man thats alot of words for something  so simple
 
I hope that helps
 
Jim

---

### Post by blackoper on 2009-10-06
> **cat2005 said:**
> What do you mean by "dual tuner"?

/ sorry, noob here

It has two digital tuners in it. Just means it can record two different digital channels at once. If I had it to do over again, I would have bought the hdhomerun and not the pci hdtv tuner cards I have.
As to an ir blaster you don't need one if you use a cable box that can be tuned by firewire. There is a channel changing script for this called 6200ch in the contrib section of the main mythtv directory.

---

### Post by fwb22 on 2009-11-26
Cat2005,

I think you can do what you want.

Check out this link for some pointers.

[http://www.mythtv.org/wiki/PcHDTV_HD-5500](http://www.mythtv.org/wiki/PcHDTV_HD-5500)

HTH

---

### Post by cat2005 on 2009-11-26
> **fwb22 said:**
> Cat2005,

I think you can do what you want.

Check out this link for some pointers.

[http://www.mythtv.org/wiki/PcHDTV_HD-5500](http://www.mythtv.org/wiki/PcHDTV_HD-5500)

HTH


Thanks!

---

### Post by leeper69 on 2010-03-06
I resiliently purchased a pchdtv 5500 card and am using it to receive ntsc signals from my direct tv box. I use tvtime in Ubuntu 9.10 with kernel 2.6.31.17 and have the card hooked up to the tuner via a coax cable  coming from my Direct tv box with the audio out jack hooked to the line in jack on my sound blaster card.
the picture quality is ok but I cant get the sound to work. you may want to rethink using this card if you aren't going to receive atsc signals for this reason.

PS: I have been fighting the sound issue for two weeks now and still haven't got it working. I got the pchdtv card because it was a Linux card and thought it would just work in Linux now I have no sound and no way to watch tv in any other operating system. I would strongly recommend you to look at another card unless you are a Linux pro.

---

### Post by gordintoronto on 2010-03-06
Have you checked your volume controls to make sure nothing is muted?  On my system, Line In is muted....

---

### Post by tekkitan on 2010-04-28
> **blackoper said:**
> If you havn't bought the pchdtv 5500 yet I would recommend getting the silicondust hdhomerun as it's dual tuner and it is networked and doesn't need a pci slot

For anyone looking at this thread, note that the SiliconDust HDHomeRun ONLY has digital tuners. This means you will not receive the analog channels from your cable company without a separate analog-supporting tuner (which is also what the OP wanted).

---

### Post by enricor77 on 2010-08-22
Hey guys,
I have the same configuration as well, I am planning of removing the PVR-150 because of a static sound under each recording (inside and outside mythtv). 
Did you ever get the PCHDTV-5500 to work? If so could you share an how to?

Thanks a lot,
E.

An update:

I just sent this email to the support:
To the support of PCHDTV,

I have recently purchased the PCHDTV-5500. I have successfully connected the card to the S-Video exit of my Direct Tv box (Analog);however, no audio is captured.
I am using Mythbuntu 9.10 and mythtv 0.22 as player. 
I tried to compile the drivers from the cd or downloaded from the website but I received errors during the make step. The cx88_audio and other modules are loaded automatically by the system. 
I have connected the PCHDTV-5500 audio jack to the Mic or Line In on my audio card with is not muted and working properly.
 I verified that the S-Video exit is sending both audio and video, using a PVR-150.
I have followed the configuration steps on the wiki page to configure the card in mythtv both as analog and digital setting the open on demand flag and the sample rate at 48K.
I read that the card is sometimes shipped with the audio capture feature disabled and there is a way to enabled changing a registry on the cx88 eprom.

If I connect a jack from the composite exit of the directtv box to the line in I get audio, which is out of synch and not present into the recordings, same if I bridge the audio jacks through the card (directtv to PCHDTV , PCHDTV to line-in)
 
What am I missing?

Thank you so much for your help

An additional note:
Selecting /dev/dsp1 as audio device for the V4l Analog I get a static noise which is present also in recordings.

---

