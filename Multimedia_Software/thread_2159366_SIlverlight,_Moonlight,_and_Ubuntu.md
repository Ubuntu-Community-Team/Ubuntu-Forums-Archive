---
title: "SIlverlight, Moonlight, and Ubuntu"
date: 2013-07-02
forum: Multimedia Software
---

### Post by RedStarYellowSun on 2013-07-02
One of my last graduation-required classes is an online-only classes with only Silverlight[SUP]®[/SUP]-formatted video-lectures, which my Ubuntu 13.04 cannot play. (I tried asking if they had other formats, but they had none.)

Apparently, a program called "Moonlight" was developed for Linux systems, but has been abandoned. Nonetheless, I went to [http://mono-project.com/Moonlight]("http://mono-project.com/Moonlight"), which brought me to [http://www.go-mono.com/moonlight]("http://www.go-mono.com/moonlight"). But, that brings me:
```
**403 Forbidden**
**[SIZE=5]Forbidden[/SIZE]**

You don't have permission to access /moonlight on this server.
[HR][/HR]
Apache/2.2.22 (Ubuntu) Server at www.go-mono.com Port 80
```

Are the Mono™ people still together? I sent them an e-mail requesting for access to the installation file, but are they still together? Just in case, does anyone here have a copy of the file I can use?

Any assistance would be greatly appreciated.
Thank you for your time.

Take care,
RedStarYellowSun

---

### Post by Irihapeti on 2013-07-02
I can't answer your question about the project team.

But I've had experience with moonlight and Silverlight-formatted files.

If they're created with the latest version of Silverlight, moonlight won't play them.

Unfortunately, and it's probably not what you want to hear, you need to use Silverlight in Windows if you want to access these files.

---

### Post by RedStarYellowSun on 2013-07-02
> **Irihapeti said:**
> I can't answer your question about the project team.

But I've had experience with moonlight and Silverlight-formatted files.

If they're created with the latest version of Silverlight, moonlight won't play them.

Unfortunately, and it's probably not what you want to hear, you need to use Silverlight in Windows if you want to access these files.

Thanks for the reply.
I'll use the public computers, then.
Thanks again.

Take care,
RedStarYellowSun

---

### Post by sanderj on 2013-07-03
Did you check [http://www.go-mono.com/mono-downloads/download.html](http://www.go-mono.com/mono-downloads/download.html) ?

However: don't expect it to work. Silverlight-with-DRM is what they use, and that's not available on non-Microsoft systems.

Workarounds:
- ask the content providers for an open site, using HTML5 or flash
- install WinXP in a virtual machine, and access the site from WinXP
- if there is an Android App for the site, use an Android device (or emulator) to access the content

---

### Post by ksatta1 on 2013-07-03
I also decided to try moonlight yesterday, all the moonlight links give 403 forbidden and all the moonlight-x packages have been deleted from Ubuntu repos? (Moonlight was in the repos for older ubuntu versions like 10.x, but now they show they've been deleted).

Anyone know what's going on? Microsoft has probably found some way to sue Moonlight devs and forced them to remove everything or something :D Must be some very sensible reason like "it hurts our Windows sales", which is ofcourse illegal in their opinion.

I don't know why Silverlight is still being used, even Microsoft is ditching it..

I just registered for an online billing site for my company and for some crazy reason it uses Silverlight, already sent them an angry email :)

---

### Post by Frogs Hair on 2013-07-03
Moonlight stopped development two years ago . Siverlight , also wasting  away , has proprietary packages that Moonlight could never include because it was open source and the license prohibited that . That is why Moonlight never worked with certain media or websites. It was not a matter of Moonlight being out of date it was crippled to begin with.

---

### Post by cmygeHm on 2013-08-28
You can download plugin here [[FONT=Segoe UI]http://mokeke.sytes.net/downloads/linux/Novell_Moonlight/[/FONT]]("http://mokeke.sytes.net/downloads/linux/Novell_Moonlight/")

---

### Post by evilsoup on 2013-08-28
Slightly old thread, but since it's been bumped already I think I should mention [Pipelight](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html), which claims to allow the playing of Silverlight videos in the browser.

---

### Post by 9-eric on 2013-09-06
> **evilsoup said:**
> Slightly old thread, but since it's been bumped already I think I should mention [Pipelight]("http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html"), which claims to allow the playing of Silverlight videos in the browser.

Thanks Evilsoup! I was searching everywhere for a solution to this. Moonlight didnt work for me because it doesnt support the newest versions of silverlight.  I am also trying to get my online schooling going and it is only in silverlight. Pipelight worked for me, there are some formatting issues but everything seems to be working. Thanks again!

---

### Post by mbohets on 2013-09-09
Pipelight works fine for me, I use it to watch online TV from the Belgian cabletv provider Telenet.

You can find install instructions here
[http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html](http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html)

To install, use following ppa and instructions
Stop Firefox
sudo apt-add-repository ppa:ehoover/compholio 
sudo apt-add-repository ppa:mqchael/pipelight 
sudo apt-get update 
sudo apt-get install pipelight

Start Firefox and install the Firefox addon UACONTROL and set the browers agent for [http://yelotv.be](http://yelotv.be) to IE8

After  this, firefox reacted very slow and often freezed, after a reboot Firefox  works normally and it is now possible to watch TV via [http://yelotv.be](http://yelotv.be)

---

### Post by foosean0102 on 2013-09-09
Thanks for posting about pipelight evilsoup!  I am running Kubuntu 12.04 and had been unable to get some of my wife's coursework for nursing school to run properly.  I installed pipelight and had it working within a few minutes.  I wish I could +1 ya!

---

### Post by kaffee2 on 2013-10-23
Thank you very much! Pipeline works great and it was easy to install.

---

### Post by TheKLF99 on 2013-10-27
> **Irihapeti said:**
> Unfortunately, and it's probably not what you want to hear, you need to use Silverlight in Windows if you want to access these files.

I'm also annoyed - I just subscribe to "Sky Go Extra" so I could watch my movies on my laptop which runs Puppy Linux, and it said I needed Silverlight.

Went to Microsoft's "OFFICIAL" Silverlight website and this is what they say

"Microsoft Silverlight is a free web-browser plug-in that enables  interactive media experiences, rich business applications and immersive  mobile apps.
            Windows? Check. Mac? Check.** Linux? Check**. Silverlight  **works on all major OS's** plus **all major browsers**, including **Firefox,  Google Chrome**, Safari, and yes, Internet Explorer."

Microsoft are obviously doing this so they don't get done again for forcing people to use their OS, it makes them look good, either that or they can't be bothered updating their information correctly, which is pretty poor for such a large company as Microsoft.

You'd think that if they claim to support Linux with Silverlight they'd at least develop the plugin for it not just rely on a third party company to develop a similar plugin which doesn't support half the stuff that Silverlight does.  It would be like Adobe with Flash not making their own plugin for Linux and just relying on a third party to do it.

Very disappointed, but then again it is Microsoft so what else can I expect from them.  As for Sky they're not much better than Microsoft - making it that you must use their cheap junk Amstrad/Thomson Sky box to view Sky, making their dishes too small so you can't receive any other satellite systems, banning CAM manufacturers from creating CAMS so you can use a Sky card in a Freesat TV, forcing you to use their own cheap junk wireless router (another piece of Amstrad's junk), and now forcing people to install Silverlight and Windows just to watch Sky Go.  Quite sure Rupert Murdoch, Alan Sugar and Bill Gates all work together on this one.

---

### Post by Elfy on 2013-10-27
If you need support start a new thread. Closed.

---

