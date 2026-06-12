---
title: "Last 2 issues - choppy recordings, no audio"
date: 2012-01-17
forum: Mythbuntu
---

### Post by carrucha on 2012-01-17
Updated my backend to a dual-core 2.4 instead of a single core 3.0? P4.  Mostly I just couldn't handle how loud the other machine was in our bedroom.  So my setup is as following:  

Backend/Frontend
Mythbuntu 11.10
Compaq SR5510F
Athlon 64 X2 5000+ 2.4GHz
3GB DDR2
1.5TB 5400 RPM
NVIDIA GeForce 6150 SE 128MB?

Frontend
Mythbuntu 11.10
3.0? P4
2GB DDR
40GB
Decent video card, not sure what

TV
60" DLP via HDMI

Tuner
HD Homerun dual tuner (older model)

My questions are if my backend should be strong enough to handle recording 2 HD programs simultaneously?  It seems to handle 1 fine, but it's dropping frames or something it seems whenever it records 2 at once.  If it won't be able to handle it that's fine, I can upgrade or record a single program.  Just wasn't sure if I should be able to get it working or not.  All the requirements pages I have seen are extremely outdated or gone.  

A second question is that my recordings on the backend are fine and play fine, but on the frontend I get no audio.  I'm connected with hdmi.  Is there something special I need to be doing?  My audio works other than that on the machine and alsamixer seems to show things properly.

Thanks!

---

### Post by carrucha on 2012-01-19
Hurry - American Idol has started!  OK, just kidding.  

Anyone have any thoughts?

---

### Post by larsolav on 2012-01-19
Your backend should be able to record two HD streams fine as it should just save the stream from the HD homerun straight to disk. What does the backend log say when you record two program at a time? For your backend I would spend a few bucks on a VDPAU compatible Nvidia  video card...

On the frontend, is the video card a VDPAU capable Nvidia card? Don't know if a P4 can handle rendering HD video on its own... 
Also, make sure the HDMI is unmuted in alsamixer.
What does "aplay -l" and "aplay -L" give in terminal?
Have you scanned for audio devices in the frontend general setup menu?

Good luck!

---

### Post by carrucha on 2012-01-20
Thanks for the input.

The frontend and backend seem to play the files fine if the recordings are good, so I don't think it's my video card.  The P4 is 3GHz I think and seems to do fine playing the video.  

I'll have a look at the other stuff.

---

### Post by carrucha on 2012-01-29
OK, I figured out that mythcommflag was using up my cpu, so I turned off commercial flagging and set max jobs to 1, down from 2.  Then I recorded 2 HD shows at once and didn't get over a .5 load.  I've never had a problem with commercial flagging before, but I guess I was doing SD programming before now.  I'll see if I can get it working either by scheduling it later or keeping it at 1 job max.

For the video card, I've been looking at these two:

$13 after MIR - ASUS GeForce 8400 GS 1GB [http://www.newegg.com/Product/Product.aspx?Item=N82E16814121473](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121473)

$20 after MIR - ASUS GeForce 210 1GB [http://www.newegg.com/Product/Product.aspx?Item=N82E16814121422](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121422)

I like the first one but wasn't sure if it's too old.  My notes say it has feature set A of VDPAU and I wasn't sure if that was enough.

The second one has feature set C according to my notes.  Someone mentioned somewhere that it didn't have enough power to do the job.

Opinions?  Or recommendations for other cards?

I'll be getting two of them whatever they are.  I was also thinking about changing my setup since I'm not live just yet to be the following:

Frontend #1 and Frontend #2
Mythbuntu 11.10
Compaq SR5510F
Athlon 64 X2 5000+ 2.4GHz
2GB DDR2
40GB IDE HD or so

Backend
Mythbuntu 11.10
P4 3.0Ghz
2GB DDR
1.5TB 5400 RPM

Tuner HD Homerun dual tuner

Any thoughts about this setup?  I still might want to upgrade the backend if for nothing else to get it to be quiet.  Or does it need to be beefier than it is?

Thanks!

---

### Post by carrucha on 2012-01-31
Or should I go with one of these instead?

$21 after MIR GeForce GT 220 1GB Fanless [http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=7297818&CatId=3669](http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=7297818&CatId=3669)

or

$20 after MIR GeForce GT 220 1GB Fan [http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=1781500&CatId=3669](http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=1781500&CatId=3669)

Rebate lasts until today only, so I'll have to jump on these if they sound like a good choice.

Thanks!

---

### Post by nickrout on 2012-02-03
> **carrucha said:**
> Or should I go with one of these instead?

$21 after MIR GeForce GT 220 1GB Fanless [http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=7297818&CatId=3669](http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=7297818&CatId=3669)

or

$20 after MIR GeForce GT 220 1GB Fan [http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=1781500&CatId=3669](http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=1781500&CatId=3669)

Rebate lasts until today only, so I'll have to jump on these if they sound like a good choice.

Thanks!

220 is FAR better than 210. go for the 220

---

### Post by carrucha on 2012-02-03
That's what I decided.  I ended up going with the GT 430 though in the end.  More than I wanted to spend, but that's OK.  I noticed a lot of people complaining about the fanless ones not working well, so I decided on one with a fan and awesome reviews.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814133356](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133356)

---

