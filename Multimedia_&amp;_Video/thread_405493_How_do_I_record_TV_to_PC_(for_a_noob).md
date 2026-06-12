---
title: "How do I record TV to PC (for a noob)??"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by herbster on 2007-04-09
I have a nVidia 7600 GS card on my PC right now, and I'm wondering if there is some device that I can get that would allow me to capture/record (dunno the official term hehe) TV into my computer. So just to be clear, **I want to keep my current card but add-on some type of device that can capture TV into my PC.**

Any help appreciated, thanks!

---

### Post by Syke on 2007-04-10
You're probably looking for a TV tuner. [Hauppauge PVR-150]("http://www.hauppauge.com/Pages/products/data_pvr150.html") does a good job.

---

### Post by GregaS on 2007-04-10
Does anyone know any good software for capturing video on linux?

---

### Post by ffxr on 2007-04-10
what type of video..?

if your looking to capture tv ... have a look at tvtime, freevo and mythtv

---

### Post by ffxr on 2007-04-10
as regards the original question, PVR 150 also get my vote..   as an analogue tv capture device..

try and get a hauppauge capture card (they seem to be better supported in linux) and one with hardware mpeg encoding.. i have been dissapointed with performance of cards that require the CPU to do the encoding... and i like PCI cards over usb devices...

[just my rambling thoughts]

---

### Post by herbster on 2007-04-10
So I can use the Hauppauge capture card **along with** my nVidia card? Again I'm looking for an add-on, NOT a replacement card.

---

### Post by ffxr on 2007-04-10
yeah you need both to be able to watch/record tv... your assumption is correct..

this is database of what sort of setup ppl are using to on linux based PVRs' (personal video recorders)... it might clear a little of the murk for you...

[http://pvrhw.goldfish.org/tiki-pvrhwdb.php?offset=50&sort_mode=rating_desc](http://pvrhw.goldfish.org/tiki-pvrhwdb.php?offset=50&sort_mode=rating_desc)

---

### Post by herbster on 2007-04-10
ffxr,

You seem knowledgeable on this, thanks for your help. The link you gave gives me an idea of what I'll need, but in terms of what I need to do to get it going if I get the Hauppauge card, I am a bit confused.

I want to do 3 things basically:

1. I am currently using dual monitors w/nVidia Twinview, so I'd like to have 1 monitor have TV going while I work on the other.
2. Record TV into my PC, like a VCR. Have it scheduled/timed to record certain programs, etc.
3. Capture my Camera footage into my computer.

I have looked into MythTV before, and even began the installation process (and stopped upon realizing I didn't have a tuner card lol), but it seemed to me that MythTV needed to use my PC as a server or something, like it had to be on all the time as a MythTV box, but I need to use my PC for work and everything, so I didn't think that made sense.

I guess to be able to do those 3 above with some decent, possibly simple software that allows for it in Ubuntu??

---

### Post by newlinux on 2007-04-10
The mythbackend process doesn't take up many cpu cycles when it isn't recording anything, so you can easily run myth while doing other things. It doesn't need to be running all the time, just when you want to record something, but again, it really isn't processor intensive for it to just run. I run myth on a few computers that I do other things on (including the computer I'm using right now). You don't need to run the mythfrontend unless you are watching something. You don't need it running to record (just the backend). You can do things you want to do with myth - but for some it takes some time to configure - how much time depends on how much you want to accomplish. Most of the basic functionality is quick to setup.

What type of processor do you have? what type of monitors? The hauppage 350 has a hardware decoder tv-out that can be used make the load on your processor really minimal.

You might want to look into kino or cinelerra for camera capture. Kino is great for miniDV, and cinelerra supports HDV as well.

---

### Post by newlinux on 2007-04-10
If you want to go the myth route in Ubuntu, most everything you need is right here:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by herbster on 2007-04-10
> **newlinux said:**
> What type of processor do you have? what type of monitors? The hauppage 350 has a hardware decoder tv-out that can be used make the load on your processor really minimal.


I have a P4 2.0ghz, 1.2gb ram, 2 x 320gb SATA, BFG 7600 GS 512MB card and monitors = 1 NEC Multisync and 1 Samsung Syncmaster.

So then if I install MythTV, it's like any other program? Like I can open it at 7:59pm to start recording an 8:00pm show or whatever, let it go in the background while I do stuff on the PC, then watch the video later??

---

### Post by newlinux on 2007-04-10
> **herbster said:**
> I have a P4 2.0ghz, 1.2gb ram, 2 x 320gb SATA, BFG 7600 GS 512MB card and monitors = 1 NEC Multisync and 1 Samsung Syncmaster.

So then if I install MythTV, it's like any other program? Like I can open it at 7:59pm to start recording an 8:00pm show or whatever, let it go in the background while I do stuff on the PC, then watch the video later??

Yes, you can run it that way. Myth generally installs the backend to run whenever the computer is booted by default. But you can manually stop and start it - yes. The frontend (which needs to have the backend running to work) can be started and stopped at any time. In my opinion, there really is no need to stop and start the backend unless you want to configure it. just let it run all the time... And then run the frontend when you want to watch something. The backend doesn't do much of anything cpu intensive unless you want it to do something, such as record something. If you get a hauppage that won't take up many cycles because the tvcard will do most of the work. It can record when you aren't watching anything for you to watch later... If you are really worried about CPU cycles, just be sure not run the commercial flagger (easy to specify when you start a recording, or you can have it default to not run).

So you can do what you are asking, or you could just in advance schedule the recording to start at 8 and leave the backend running and at 8 it will start recording, whether you are watching or not.

---

### Post by cblanquer on 2007-04-21
I have installed a Hauppage 1300 which allows analogue tuning, digital tuning (for Terrestrial Digital TV, or DVB-T in case you have in Canada) and a video input, in my case my sat box.
I actually run Gnome desktop but use Kaffeine player to record from TDT, timers can be successfully set up. 
This version has a built-in MPEG-2 decoder. There is a cheaper version which does no thave the H/W thing and a more expensive version able to catch also a satellite antenna input and decode it into DVB-S.
Only bad thing for me is that I could not get yet selecting the language (TDT often broadcasts dual band films). This does no thappen with the proprietary program on MS Windows.
Undertitles fail sometimes, also in Windows.

---

