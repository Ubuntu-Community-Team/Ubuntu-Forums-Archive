---
title: "Best method to bring media from my PC to my home theater?"
date: 2008-08-20
forum: Multimedia Software
---

### Post by modestmelody on 2008-08-20
There seems to be a tremendous variety of methods to bring media from my computer/network to my HDTV and surround sound setup.  What methods have you used?  What works best?  Is a cheap mini-computer easier/better than some of the hardware available specifically designed for this task?  What specifically designed boxes play well with Linux?

Thanks :D :guitar:

---

### Post by cheddercaveman on 2008-08-20
Others may have more specifics than I do, but so far that best method that I've seen from some researching is to run a uPNP server (you can do this on your PC, doesn't need to be a dedicated server) and get a PS3.  PS3 will recognize a uPNP server and allow you to play your audio/video through your home theatre.

Alternatively, on the PS3 you can also install Linux, and again have the same functionality.

With that then you get the advantage of having a game console, blu-ray player, and multimedia station for ~$400.  I think that you'd be pretty hard pressed to build a media center type PC for less than that with the same features.

---

### Post by ilrudie on 2008-08-21
I do the same thing with my Xbox360 and ushare on my pc.  It works great.

---

### Post by nhasian on 2008-08-21
Hello modestmelody,

I'll try to shed some light on the subject.  

The best method is to have a HTPC (Home theater PC) as you suggested attached to your tv.  This option is the most expensive but gives you the most flexibility.  You could install MythTV and use the pc as a TiVo if you add a TV Tuner to the PC.  You could also run emulators like MAME or Snes9x to play games. and finally you can play back any video or audio filetype.  Ultimately I would like to do this with my setup, but i'm waiting for Tru2Way cablecards before building my HTPC.

The next option is to stream the video to your TV which is what i'm doing now.  I have both a PS3 and an xbox360.  The xbox360 plays back a lot more divx/xvid files than the PS3 does.  Plus its a lot cheaper.  The core system is $199 new i think now.  You can find them used on craig's list even cheaper.

Finally the software you can use for streaming:

ushare [http://ushare.geexbox.org/]("http://ushare.geexbox.org/") works on both PS3 and Xbox360.  Its free, and the most stable in my testing. *Does not transcode files.*

TwonkyMedia [http://www.twonkyvision.de/Products/TwonkyMedia/index.html]("http://www.twonkyvision.de/Products/TwonkyMedia/index.html") works on both PS3 and Xbox360.  Free 30 day trial, afterwards is $40.  *Does not transcode files.*

Fuppes [http://fuppes.ulrich-voelkel.de/]("http://fuppes.ulrich-voelkel.de/") Also free and works on PS3 and Xbox360.  Development seems to have stalled, and we havent heard from the author in about 5 months.  Project has been forked as Fuppex: [https://sourceforge.net/projects/fuppex/]("https://sourceforge.net/projects/fuppex/") Fuppes/Fuppex is the most flexible of the these software and does support transcoding but its also the most difficult to configure (and a bit buggy).  Also i havent tested the forked fuppex yet.

So bottom line, I use xbox360 with ushare to watch my divx/xvid videos.  Unfortunately the 360 does not support MKV file container which is very popular for high definition videos.  If you want to playback MKV files the best way is with an HTPC.

Hope this helps some people

---

### Post by modestmelody on 2008-08-23
So my question is, if HTPC is clearly the most flexible choice, what good, inexpensive front end exist right now?  What is the way to go about having the ideal hardware-- inexpensive, small, and powerful enough to output 720p (potentially with HDMI)?

---

### Post by xarquid on 2008-08-23
So basically, to sum everything up:

[LIST]
[*]You keep running Linux (Ubuntu, Debian, what have you...) and you install a front-end application in Linux and on the XBox OR PS3.
[*]One of these applications can be GeeXboX or TwonkyVision, for example.
[*]These do not transcode videos (such as DVDs). So what do we rely on for this?
[*]I do know that the XBox360 relies on Windows Media Player as its solution to read from for videos (such as AVI and MPG files) -- this is how my friends streams his videos to his TV. How do these solutions work in scenarios like this? How about for audio?
[*]--- Do you use RhythmBox or another media player? Or what's out there that's like iTunes or something good for video & audio for Linux? -- and can handle streaming to an XBox360/PS3?
[/LIST]

I guess I'm just trying to comprehend this and perhaps write my own mini-how to (for myself or for others).

I know you will need the applications mentioned to act as a one-way server on the Linux machine, but what rests on the side of the XBox or PS3? How does it transcode the file it is being sent and read the signal (so to speak)?

Anyway, nice post! I'm just trying to figure it all out because I'm contemplating buying an XBox with all of the NetFlix streaming coming up soon...and I really want to have all of my ducks in a row :)

Sincerely,

Craig

---

### Post by ilrudie on 2008-08-24
Don't know about the ps3 but on the xbox360 there is nothing special.  The regular xbox360 dashboard's media player can play video streamed from ushare.

---

### Post by nhasian on 2008-08-25
afaik, all the retail HTPC are kinda pricy.  I havent priced them recently as I'm still waiting for the Tru2Way cablecards before taking the plunge.  any old computer will do though.  Someone correct me if i'm wrong but i think the minimum requirement to playback 1080p content is 2Ghz.  You should have minimum of 1Gig of ram.  if you dont already have an old pc or laptop with the minimum specs, you can check on craig's list :)

> **modestmelody said:**
> So my question is, if HTPC is clearly the most flexible choice, what good, inexpensive front end exist right now?  What is the way to go about having the ideal hardware-- inexpensive, small, and powerful enough to output 720p (potentially with HDMI)?

---

### Post by ugm6hr on 2008-08-25
Building your own HTPC is more economical than buying a pre-specified device.

Something like this: [http://www.miffteevee.co.uk/build/](http://www.miffteevee.co.uk/build/)

---

### Post by modestmelody on 2008-08-25
I wouldn't have thought such a low spec machine could output 720p smoothly to a television.  It's been three years since I built my desktop, has integrated video come that far?

---

### Post by ugm6hr on 2008-08-25
> **modestmelody said:**
> I wouldn't have thought such a low spec machine could output 720p smoothly to a television.  It's been three years since I built my desktop, has integrated video come that far?

Don't know - but the various reviews suggest so: [http://www.vr-zone.com/articles/Biostar_TA690G_AMD_690G_Motherboard_Review/4726-1.html](http://www.vr-zone.com/articles/Biostar_TA690G_AMD_690G_Motherboard_Review/4726-1.html)

This is the mobo I have used, but I haven't got a HDTV yet.

---

### Post by speed32219 on 2008-08-25
Well, you can start off ($125) with an Xbox soft moded with Xbmc.  I have this setup along with a Ubuntu file server (2.5TB) and I watch SD movies, TV streams including You tube, apple trailers, weather, Pictures, Video's, Mp3 music, etc. with the best front end interface on the market period. It currently is being ported to hardy and soon will be the leading media center within linux.  It has won many numerous awards over the years for a free and open system not to mention the best there is.

If you want to try the alpha XBMC on 8.04 hardy you can go here to get the deb and key. (It has bugs, but will give you and idea of what it looks like on the firmly stable hacked Xbox which even runs a version of Mplayer with custom scalling to fill your screen if you so desire)

[http://xbmc.org/forum/showthread.php?t=33327](http://xbmc.org/forum/showthread.php?t=33327) 
Post #104 for files and directions.

Link for HDTV Xbox Xbmc read 1st post with pics.
[http://www.avsforum.com/avs-vb/showthread.php?t=635294](http://www.avsforum.com/avs-vb/showthread.php?t=635294)

That post was made in 1/23/06 so you can imagine what it does now.  That site has just about everything you could ask for for hdtv, HD, HTPC's, inclduing MythTV and 150" screens.  I run mine on a 110" diagonal screen and the video quality is excellent.

I am currently running both the Xbox Xbmc (Never have problems including with the 5.1 surrond) with the Ubuntu 8.04 server as my video server and also use the Ubuntu box as an HTPC to eventually replace the Xbox which will be re-located to another room and still be networked.

As far as MB's go, I prefer a Ubuntu HTPC frontend with the Intel G45 HD chipset and integrated graphics coupled with a core2duo E4700 2.6Ghz to 3Ghz processor and 1-2 GB fast DDR2 800+ OC to 1600.  I currently have a Intel 2.8Ghz Celeron with Intel P5PE-VM MB and a Evga AGP 8X Geforce Nvida with DVI to HDMI output, 1 GB DDR 400 pc3200 and works great with everything but will not be powerfull enough for 1080P and BD formats.  I want integrated HD graphics, low power processors and DDR2 Memory so I can reduce noise and heat in the HT room and keeping the WOW factor.

here is one that I'm interested in upgrading to. (Need to keep an eye on driver support, but being Intel it should be here already)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128353](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128353)

Good luck

PS.  Even though I do run Mplayer and VLC (98% of Movies are ISO based 4.3 GB files)now and then, they just do not compare or compete with the Xbox XBMC center.  Once XBMC is fully released and mostly bug free using Ubuntu, that's when I'm upgrading my HW and moving into the HD/BD realm even though I dislike supporting licensed/closed (Espically sony) media. DRM

---

### Post by Freddie.Ruddick on 2008-08-25
Just to throw another viewpoint in. If you don't want to hack around with an XBox/PS3, you could get a [Neuros OSD](http://www.neurostechnology.com/), which is a custom-designed device for recording and streaming media to/from a TV/Home Theatre. The software the device runs off is open-source.

I've never used one myself, but I've heard good things about it...

---

### Post by ipburbank on 2008-08-25
i like a mac mini for that, the mac os having great multimedia tools. front row is really nice for a home theater, and then if you want to play a power point or something you have a platform which is capable of doing so.

---

### Post by MrWES on 2008-08-26
Have you looked into a UPnP capable network media player? Newegg has several that are reasonably priced:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833181078](http://www.newegg.com/Product/Product.aspx?Item=N82E16833181078)

That's a link to  ZyXEL DMA1100P HD Digital Media Theater With built in 200 Mbps HomePlug AV Powerline Adapter - Retail 

$169, plus they have a version just below that (no wireless) for $149.

Bill

---

### Post by onesojourner on 2008-08-26
Here is a big fat vote for xbmc on ubuntu. You can set up a dedicated box or pick up a 50-60ft hdmi cable and run it to your theater. Its beta right now but I use it daily. Crashes are few and far between.

[img]http://www.aeonproject.com/images/screen_nowplaying2.jpg[/img]

Music
[img]http://www.aeonproject.com/images/screen_musicroller.jpg[/img]

wall view
[img]http://www.aeonproject.com/images/screen_posterwall.jpg[/img]

TV
[img]http://www.aeonproject.com/images/aeon_seasons1.jpg[/img]

movies
[img]http://www.aeonproject.com/images/aeon_showcase1.jpg[/img]

[img]http://www.aeonproject.com/images/aeon_showcase3.jpg[/img]

Coming soon...
[IMG]http://http://www.aeonproject.com/dropbin/aeonstark_skyline.jpg[/IMG]

---

### Post by onesojourner on 2008-08-26
[http://www.aeonproject.com/dropbin/aeonstark_skyline.jpg]("http://www.aeonproject.com/dropbin/aeonstark_skyline.jpg")

---

### Post by nhasian on 2008-08-28
you can even playback 720p avi videos on an old modded xbox (Pentium III 733Mhz) with XBMC :)

> **modestmelody said:**
> I wouldn't have thought such a low spec machine could output 720p smoothly to a television.  It's been three years since I built my desktop, has integrated video come that far?

---

### Post by ilrudie on 2008-08-28
> **nhasian said:**
> you can even playback 720p avi videos on an old modded xbox (Pentium III 733Mhz) with XBMC :)

I have not had great success playing back 720p content on my xbox w/xbmc.  It can push the dashboard 720p no problem but mine has trouble with 720p movies.

---

### Post by modestmelody on 2008-08-28
> **ilrudie said:**
> I have not had great success playing back 720p content on my xbox w/xbmc.  It can push the dashboard 720p no problem but mine has trouble with 720p movies.

Any more people have experience with this?  You can pick up a used XBox for $60 at a Gamestop so if I could play 720p that would seem ideal...

---

### Post by speed32219 on 2008-08-28
> **modestmelody said:**
> Any more people have experience with this?  You can pick up a used XBox for $60 at a Gamestop so if I could play 720p that would seem ideal...


The Xbox will handle 480i/p upscaling to 720P and 1080i (Using a version of Mplayer with great codecs I believe with no probelm ).  Decoding/encoding 720P takes you into the 2Ghz -2.5Ghz dual core processor arena and the little ole Xbox just can't do it.  But for anything else it is a fantastic unit.  Best of the best for video scaling and rendering, it is actually better than what comes with Mplyaer, vlc, ffmpeg, zine, etc for ease of scaling 16:9. 14:9, normal, custom with slide bars, etc.).  

Now, if you want 480/720p and 1080i/p then download the Linux version and your good to go provided you have the HW to support it.  They are working very hard on the port and it is coming along just great, I've been using both and the Linux version is much more powerful inclduing additional features.  Read my post prior to this one for links.  Also, I just picked up an Xbox from Gamestop for $60.  But you also need to pick up a MS (Only) HD pack for component and optical audio connections along with an Xbox MCE to make life easy. Plus if you do the soft mod you will need splinter cell game, 8 MB memory stick (Its for the games joystick).  All in all around $120 total, to get the screenshots from the prior post. If you have questions go the the first link in post above, they are very helpful.

---

### Post by onesojourner on 2008-08-29
the old xbox is only good for really low bitrate 720p content. if you plan to play h.264 encodes don't even try with the xbox. xbmc is really great on ubuntu and plenty stable for every day use. It could not be easier to intall.

Just add these two lines to your repos and you are good to go.

system> software sources:

```

deb http://ppa.launchpad.net/team-xbmc-svn/ubuntu hardy main

```
```

deb-src http://ppa.launchpad.net/team-xbmc-svn/ubuntu hardy main

```

reload them and then search for xbmc in synaptic (system> synaptic)

---

### Post by foresto on 2008-08-29
I'd suggest some sort of set-top box.  A Playstation 3 or XBox 360 might do the trick, or you might look at a device specifically made for the purpose.  This one is getting great reviews:

[http://www.popcornhour.com/](http://www.popcornhour.com/)

---

