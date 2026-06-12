---
title: "Pipeline for Ubuntu brings Silverlight 5 to the linux browser - anyone tried this?"
date: 2013-08-19
forum: Multimedia Software
---

### Post by Gilad_Pellaeon on 2013-08-19
Saw today that this was released recently

[http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html](http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html)

From the website:

> 
Today we want to present you our latest project [Pipelight]("https://launchpad.net/pipelight"),  which allows to run your favorite Silverlight application directly  inside your Linux browser. The project combines the effort by [Erich E. Hoover]("http://compholio.com/")  with a new browser plugin that embeds Silverlight directly in any Linux  browser supporting the Netscape Plugin API. He worked on a set of Wine  patches to get Playready DRM protected content working inside Wine and  afterwards created an Ubuntu package called [Netflix Desktop]("https://launchpad.net/netflix-desktop").  This package allows one to use Silverlight inside a Windows version of  Firefox, which works as a temporary solution but is not really  user-friendly and moreover requires Wine to translate all API calls of  the browser. To solve this problem we created Pipelight.
 
Pipelight consists out of two parts: A Linux library which is loaded  into the browser and a Windows program started in Wine. The Windows  program, called pluginloader.exe, simply  simulates a browser and loads the Silverlight DLLs. When you open a page  with a Silverlight application the library will send all commands from  the browser through a pipe to the Windows process and act like a bridge  between your browser and Silverlight. As a user you will not notice  anything from that "magic" and you can simply use Silverlight the same  way as on Windows, like you can see on the following screenshot:


Has anyone been brave enough to try this yet and see if it gives a bigger performance boost compared to netflix-desktop package? I can run netflix-desktop on this 2007 tower but I believe sometimes the framerate might be dipping a bit as I can see tears in the image but yet the audio seems to keep up. It sounds like it might be less resource intensive by just allowing Silverlight 5 to run instead of just running a windows version of firefox plus silverlight 4 under WINE.

---

### Post by Gilad_Pellaeon on 2013-08-20
*UPDATE*

Well I bit the bullet today and tried it. It still needs a lot of work at least on older machines. On my dell optiplex 745 netflix-desktop works pretty much without problems except some video tearing on some shows. Pipeline did make Silverlight 5 show up in my firefox browser but it wasnt properly sending the output of netflix to my browser window even with a user agent switcher active to make it appear I was using 32 bit windows firefox browser.  Removed pipeline with sudo and the repository for it and my browser is back to normal.

---

### Post by slackner2 on 2013-08-21
Hi Gilard_Pellaeon,

I'm one of the developers of Pipelight and we've already a lot of people that confirmed it working well with Netflix.
See for example Alan Pope: [http://t.co/0qMyCEpW3U](http://t.co/0qMyCEpW3U) ;-)

If you've had some problems this might be caused by one of the following issues:

* If you don't see any output on [http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html) (this page doesn't check the user agent) and are using KDE (or some other specific desktop managers): This is a known bug, and has already been fixed in the repositories. The next release will be available soon, nevertheless you can workaround that issue.
See: [https://answers.launchpad.net/pipelight/+faq/2359](https://answers.launchpad.net/pipelight/+faq/2359)

* You might probably not have used a working user agent switcher - not all of them also change the user agent provided via JavaScript correctly. This is required to get Netflix running, otherwise it will refuse to work on Linux.
The FAQ provides some recommended user agent switchers and also some recommended user agent strings.
When getting netflix error N8109: This is also a user agent problem! I recommend using the one for FF15.
See: [https://answers.launchpad.net/pipelight/+faq/2351](https://answers.launchpad.net/pipelight/+faq/2351)

* If none of the FAQs helps you are welcome to either submit a bug report or join #pipelight on IRC freenode (webchat: [http://webchat.freenode.net/?channels=%23pipelight](http://webchat.freenode.net/?channels=%23pipelight) ) - we always try to answer all requests as soon as possible!

If you are not too frustrated its probably worth giving Pipelight another try with the tips above.

Sebastian

---

### Post by Gilad_Pellaeon on 2013-08-21
> **slackner2 said:**
> Hi Gilard_Pellaeon,

* If you don't see any output on [http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html) (this page doesn't check the user agent) and are using KDE (or some other specific desktop managers): This is a known bug, and has already been fixed in the repositories. The next release will be available soon, nevertheless you can workaround that issue.
See: [https://answers.launchpad.net/pipelight/+faq/2359](https://answers.launchpad.net/pipelight/+faq/2359)


Hi there! I had actually tried the demo at [http://www.iis.net/media/experiencesmoothstreaming](http://www.iis.net/media/experiencesmoothstreaming) and it wouldn't show anything on screen other then what appear to be "Silverlight demo" over and over in text.

> 
* You might probably not have used a working user agent switcher - not all of them also change the user agent provided via JavaScript correctly. This is required to get Netflix running, otherwise it will refuse to work on Linux.
The FAQ provides some recommended user agent switchers and also some recommended user agent strings.
When getting netflix error N8109: This is also a user agent problem! I recommend using the one for FF15.
See: [https://answers.launchpad.net/pipelight/+faq/2351](https://answers.launchpad.net/pipelight/+faq/2351)


I had tried the user agent switcher for firefox mentioned on that page actually which was [https://addons.mozilla.org/en-us/firefox/addon/uacontrol/](https://addons.mozilla.org/en-us/firefox/addon/uacontrol/) since I felt setting it on a site per site basis would be easier in the long run. At that point I had iis.net, netflix.com, and netflix.ca setup in the UA switcher. I visited netflix and tried to watch american dad and I heard the audio playing just saw no video report. The user agent I had used was

```

Mozilla/5.0 (Windows NT 6.1; rv:23.0) Gecko/20131011 Firefox/23.0

```

> 
If you are not too frustrated its probably worth giving Pipelight another try with the tips above.

Sebastian

I might give it a try here today again using the FF15 user agent and see if that will help.

---

### Post by Gilad_Pellaeon on 2013-08-21
> **slackner2 said:**
> Hi Gilard_Pellaeon,

* If you don't see any output on [http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html) (this page doesn't check the user agent) and are using KDE (or some other specific desktop managers): This is a known bug, and has already been fixed in the repositories. The next release will be available soon, nevertheless you can workaround that issue.
See: [https://answers.launchpad.net/pipelight/+faq/2359](https://answers.launchpad.net/pipelight/+faq/2359)


Well as it turns out I am effected by this bug actually I had to change embed from "true" to "false" in the configuration file and it finally showed video output. Using Lubuntu 13.04 with integrated Intel q965 video driver. Tried the iis.net demo and I averaged around 21-24FPS with a lot less tearing compared to netflix but oddly enough the video tearing is a lot more noticable on TV shows and movies such as The Walking Dead compared to say an animated cartoon series such as Bob's Burgers. Go figure. :) Also just now tried netflix on my girlfriends identical tower same to this one im typing on but her's has windows xp on it and sure enough, the same exact video tearing lol. I'm assuming or guessing it's because silverlight 4 and 5 refuse to or can't seem to enable hardware acceleration for netflix streams which is odd.

Oh I also tried the other alternate user agent switcher for firefox and just manually added the Firefox 15 user string in UA Overrider. Easier to just toggle it on and off when needed instead of trying to add it in on a site per site basis perhaps. :)

---

### Post by mbohets on 2013-09-09
Pipelight works fine for me.
It allows me to watch the online tv offer from my cabletv provider Telenet (Belgium)
I found install instructions on [http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html](http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html)

Here is how I installed it:
To install, use following ppa and instructions
Stop Firefox
sudo apt-add-repository ppa:ehoover/compholio 
sudo apt-add-repository ppa:mqchael/pipelight 
sudo apt-get update 
sudo apt-get install pipelight

Start Firefox and install the Firefox addon UACONTROL and set the browers agent for [http://yelotv.be](http://yelotv.be) to IE8

After  this, firefox reacted very slow and often freezed, after a reboot Firefox  works normally and it is now possible to perfectly watch TV via [http://yelotv.be](http://yelotv.be)

---

### Post by edwin-2 on 2014-01-07
how cewl this sounds it sadly requires wine witch by itself isn't at all a problem  if your running some  x86 cpu... but what about  people wanting to intergrate netfix into for xample  arm based computing...  would it be possible  to run a silverlight services on a regular coputer and than streaming the data over a network socket to your browseer so that for xample  my rasberry pi xbcm could enjoy netflix too...

---

### Post by Bucky Ball on 2014-01-07
Yea, great, but forget it. I have never used Wine and wouldn't just for this. I get along fine without Silverlight.

---

### Post by monkeybrain20122 on 2014-01-07
I took a one month trial membership on Netflix just because I want to test pipelight (rather than getting piplelight for neflix. :)). Based on the few times that I used it, it works as good as anything can, I am very impressed! On the other hand Netflix's offerings are pretty crappy, can't understand why it is so popular (but then again maybe it is because I am in Candad so get crappier selections, or maybe it is the trial membership)

---

### Post by sdowney717 on 2014-01-09
What user agent string did you use to make netflix work?

I tried this one.
[http://www.useragentstring.com/Internet%20Explorer9.0_id_16333.php](http://www.useragentstring.com/Internet%20Explorer9.0_id_16333.php)


this one worked for my 64 bit system used ie8
Mozilla/5.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; GTB7.4; InfoPath.2; SV1; .NET CLR 3.3.69573; WOW64; en-US)

netflix is playing with pipeline and silverlight 5.1

Although for this PC with a core2 duo  and and nvidia 8600gs it is not so good, the sound lags the video.
I think it is better with netflix desktop.

---

