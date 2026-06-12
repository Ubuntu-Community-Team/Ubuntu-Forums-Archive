---
title: "remote on hvr-1600"
date: 2010-04-01
forum: Mythbuntu
---

### Post by bnhrobotics on 2010-04-01
I was wondering if anyone has a working remote on 9.10 for the hvr-1600. I did some searching and I saw that people had difficulty getting it working, and when 9.10 came around, kernel issues caused it to stop working again. If anyone has any information on this and whether or not there may be support in the future I would greatly appreciate it. Thanks

---

### Post by Lepy on 2010-04-02
I had the black hvr-1600 remote w/ usb receiver working using the Windows MCE (all) option in control center. That was a few months ago though and the remote has since been replaced (using the usb receiver that came with the hvr-1600) with a faithful Radioshack 15-2116, which is also in the control center.

Check the hvr-1600's discussion tab on the mythtv.org wiki. As it suggests, make sure the cable is plugged in all the way!

---

### Post by bnhrobotics on 2010-04-02
Thanks for your reply. You mentioned USB.. did the black remote match up to a USB receiver? Mine is silver and is not USB. 

I had read that about plugging it in all the way. I hope I didnt break it. The cases to several computers I tried all interfere with the plug. I would like to know if its still possible to get it to work before I drill out a hole in the case so that I can make sure the plug is going in all the way.

I also read that as of mid 2009 the silver remote was not working due to kernel issues. Is that no longer the case?

---

### Post by Lepy on 2010-04-02
Sorry, I have no experience with the silver remote. I acquired my hvr-1600 almost a year ago, and it has no ir connector on the back.

It may very well no longer work, especially since it interfaces through the card itself unlike the usb receiver on the newer models.

The hvr-1600 seems to be quite the troublesome card under mythtv/linux. After months of ATSC/QAM heartache with this card, I think I have finally fixed all the jittery/poppy awfulness...for now. 

Anyway, I hope you can get your remote working!

---

### Post by bnhrobotics on 2010-04-02
Ok. Thanks.

Fortunately, my video quality is fine on this computer (3 2.4 GHz) cores. However, on a 2.8 GHz computer the ATSC decoding was a bit choppy. Hopefully this does not become a problem in future updates. I don't want to have wasted money...

---

### Post by matt06 on 2010-04-02
IIRC, there are many models of the HVR-1600, some of which come with no remote at all.  Mine is a model #1183 retail box which comes with the black MCE remote, USB IR receiver and everything worked out-of-the-box.

Do you know what model your card is or is your remote on this page?  I don't see anything specific mentioned about the 9.10 kernel.

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

---

### Post by bnhrobotics on 2010-04-02
My remote is not pictured in the link you posted. However, if you can access this link, it should be here.
[http://www.newegg.com/Product/ImageGallery.aspx?CurImage=15-116-033-S07&SCList=15-116-033-S01,15-116-033-S02,15-116-033-S03,15-116-033-S04,15-116-033-S05,15-116-033-S06,15-116-033-S07,15-116-033-S08&S7ImageFlag=2&Item=N82E16815116033&Depa=0&WaterMark=1&Description=Hauppauge%20WinTV-HVR-1600%20ATSC/ClearQAM/NTSC%20TV%20Tuner%20PCI%20w/Remote%201199%20PCI%20Interface](http://www.newegg.com/Product/ImageGallery.aspx?CurImage=15-116-033-S07&SCList=15-116-033-S01,15-116-033-S02,15-116-033-S03,15-116-033-S04,15-116-033-S05,15-116-033-S06,15-116-033-S07,15-116-033-S08&S7ImageFlag=2&Item=N82E16815116033&Depa=0&WaterMark=1&Description=Hauppauge%20WinTV-HVR-1600%20ATSC/ClearQAM/NTSC%20TV%20Tuner%20PCI%20w/Remote%201199%20PCI%20Interface)

I bought one in a model 1199 box, but that is not the model that I got. The 1199 does not have FM, but mine does. 

Mine looks like [http://www.hauppauge.com/pics/hvr1600_74031_diagram-s.jpg](http://www.hauppauge.com/pics/hvr1600_74031_diagram-s.jpg) , except its got another coax port above for FM signals. I cant figure out which model that matches to.

---

### Post by matt06 on 2010-04-02
Does that kit come with a remote receiver at all? [1] I did not see one on the newegg page with pictures.  I would not begin to know how to setup the remote for that model.  This is precisely why I nailed down which kit came with a remote that worked flawlessly with Mythtv before I purchased my card..so I didn't have to fight with lirc/remote issues.

I know there are standalone remotes that work with myth (example: [http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001](http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001) )and come with receivers if you just want something that works.

[1] Appears to be part of the ir blaster cable bundle?  I don't know enough about ir receivers/blasters to be able to tell.

---

### Post by bnhrobotics on 2010-04-02
Yeah, thats frustrating. I bought one model, got another. The remote matches the model the box claims. The receiver plugs into the card.

This is what I was supposed to have:
[http://www.newegg.com/Product/ImageGallery.aspx?CurImage=15-116-033-S01&SCList=15-116-033-S01,15-116-033-S02,15-116-033-S03,15-116-033-S04,15-116-033-S05,15-116-033-S06,15-116-033-S07,15-116-033-S08&S7ImageFlag=2&Item=N82E16815116033&Depa=0&WaterMark=1&Description=Hauppauge%20WinTV-HVR-1600%20ATSC/ClearQAM/NTSC%20TV%20Tuner%20PCI%20w/Remote%201199%20PCI%20Interface](http://www.newegg.com/Product/ImageGallery.aspx?CurImage=15-116-033-S01&SCList=15-116-033-S01,15-116-033-S02,15-116-033-S03,15-116-033-S04,15-116-033-S05,15-116-033-S06,15-116-033-S07,15-116-033-S08&S7ImageFlag=2&Item=N82E16815116033&Depa=0&WaterMark=1&Description=Hauppauge%20WinTV-HVR-1600%20ATSC/ClearQAM/NTSC%20TV%20Tuner%20PCI%20w/Remote%201199%20PCI%20Interface)

My remote is the same, card and receiver are different. Card looks IDENTICAL... except one more coax. Receiver is black with 2 IR mechanisms.

I started another thread trying to figure out if I should take this card back or not. I have a 30 day return policy. What are your thoughts on that? Any recommendations on a good myth compatible ATSC/NTSC card?

---

### Post by matt06 on 2010-04-02
That is odd.  Like someone threw a different model card in the box?  If it's not the hardware I thought I was buying I would return it, as much of a PITA that can be.

I have an 1183 model bought from newegg ~1.5 years ago.  It doesn't appear to be any different.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815116010](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116010)

which has a black receiver and blaster cable pictured here

[http://www.newegg.com/Product/ImageGallery.aspx?CurImage=15-116-010-S07&SCList=15-116-010-S01%2c15-116-010-S02%2c15-116-010-S03%2c15-116-010-S04%2c15-116-010-S05%2c15-116-010-S06%2c15-116-010-S07%2c15-116-010-S08%2c15-116-010-S09%2c15-116-010-S10&S7ImageFlag=2&Item=N82E16815116010&Depa=0&WaterMark=1&Description=Hauppauge%20WinTV-HVR-1600%20ATSC%2fClearQAM%2fNTSC%20TV%20Tuner%20MC-Kit%201183%20PCI%20Interface](http://www.newegg.com/Product/ImageGallery.aspx?CurImage=15-116-010-S07&SCList=15-116-010-S01%2c15-116-010-S02%2c15-116-010-S03%2c15-116-010-S04%2c15-116-010-S05%2c15-116-010-S06%2c15-116-010-S07%2c15-116-010-S08%2c15-116-010-S09%2c15-116-010-S10&S7ImageFlag=2&Item=N82E16815116010&Depa=0&WaterMark=1&Description=Hauppauge%20WinTV-HVR-1600%20ATSC%2fClearQAM%2fNTSC%20TV%20Tuner%20MC-Kit%201183%20PCI%20Interface)

I don't even use the blaster since I'm not controlling a box.  I wanted to use the FM receiver to be able to listen in the Myth interface, but I found it to be too much bother.  The only experience I have is with the 1600, so I don't feel comfortable comparing it with anything else, but FWIW, I would not hesitate to purchase another one barring any model/remote issues, of course!

---

### Post by bnhrobotics on 2010-04-02
Ok. I will consider getting another. Fortunately, I bought this tuner card locally. I just called them and they told me there would be no restocking fee. That should be easy to replace.

I bought a HDhomerun from newegg which I sent back because I didnt realize it could not handle NTSC. Now I regret sending it back. Cost me about 30 in restocking and shipping back. Plus I am moving soon, and chances are I'll only be able to get digital signals. I originally bought the thing because I wanted to record a discovery show called "Life" which is analog (another thing I didnt know).

How fast is your computer? It upsets me that I cant do digital tuning on either a 2.0 or 2.8 MHz computer.

---

### Post by matt06 on 2010-04-02
I have set up two systems as combo be/fe with the HVR-1600, one being a 3.0GHz P4 and the other a 2.5GHz AMD dual-core.  My standalone frontend is also a 3.0GHz P4 which I originally tried Celeron 2.0GHz and 2.7GHz CPUs and found they would not handle HD, but I did not try anything to optimize playback either.

I would think a 2.8GHz P4 would be able to playback digital signals, assuming the selection of a proper playback profile and video config.

(btw, afaik Discovery is offered both in analog/SD and digital/HD and whether you get one or both is dependent upon your provider and equipment.  someone correct me if I am wrong.)

---

### Post by Lepy on 2010-04-02
I'd also suggest watching the BBC version of Life. David Attenborough blows Oprah's Discovery narration out of the water, but then again, its David Attenborough.

---

### Post by bnhrobotics on 2010-04-03
I only get SD discovery.. and unfortunately I dont get BBC either. I didn't know they were playing Life. I thought Oprah was a weird choice for narrator anyway.

Oddly enough, I don't really even watch much tv, so this has been a VERY expensive learning process considering how much I watch.

I am going to be moving very soon and I will be paying my own utilities in a single apartment so I won't be getting cable tv. Ill just be getting digital over the air. In that sense I regret sending the HDhomerun back... yet I really wanted to record Life. I'd consider getting the other HVR-1600, but I really want something that would work well in a slower computer than my desktop. I'm also fearful that its going to cause me problems with "suspending" my computer like this one is. Is the HVR-1600 really the only way to go with linux and both analog/digital tuning?

---

### Post by Lepy on 2010-04-03
Any dvr, especially mythtv, will change the way you watch tv. Once you control the schedule, you could find yourself watching quite a bit more. It may be pricey at the onset, but once you get a good setup, you may find it worth the expense. 

I have cable myself, and honestly, I find  ~90% of the programming a waste of time, but thats the beauty of mythtv! For OTA programming, I really only enjoy Lost and stuff on PBS, and interestingly, OTA with a powered antenna and the hvr-1600 has always worked 100% for me, while the ClearQAM cable feed from my provider has been where most of my hvr-1600 problems have arisen.

There are a multitude of other tuner cards you could try, but you'll need to do your research on newegg, the mythwiki, etc. I only use the hvr-1600 because I was able to acquire the kit for ~$60.

If you must use your slower machine for the master backend, you could regulate it to recording only, leaving your desktop (if you mainly use ubuntu) as a secondary backend which could take care of the commercial flagging, transcoding, and other user jobs. 

It sounds like you want to use your slower machine as your main htpc/frontend, though. The HDHomerun and a newer nvidia card (that handles vdpau...though xvmc would be an option with an older model) might be your best bet in this case, but don't take my word for it, experiment and find what works best for you.

---

### Post by JMcFly on 2010-04-03
I just went from 9.04 to 9.10 (not by choice, downloaded updates one day this week and 9.04 went down like the Titantic) and I haven't been able to get my HVR-1600's grey remote to work since. ](*,)

The 1600 might be old, but it seems to be one of the few usable dual-tuners on the market, the comparable PCIe 1x cards are all limited to digital only on Linux due to drivers from what I have seen.

---

### Post by matt06 on 2010-04-04
Perhaps bnhrobotics could try 9.04?  There's nothing wrong with running an old(er) version if your hardware is supported better than with the current release!

---

