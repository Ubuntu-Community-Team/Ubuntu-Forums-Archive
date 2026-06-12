---
title: "Silverlight for Ubuntu"
date: 2012-07-19
forum: Multimedia Software
---

### Post by Kols on 2012-07-19
Hi all!

I've read a bit about that Moonlight is a pretty poor replacement for Silverlight, and that the project is more or less dead.

I really need Silverlight for streaming TV, are there really no alternatives out there? Or workarounds? I'm thinking I could try running Windows Firefox with Silverlight Plugin in Wine or something. 

Any suggestions?

-Kols

---

### Post by Dngrsone on 2012-07-19
Unfortunately, for DRM reasons, moonlight will not substitute for Silverlight, nor is there any public workaround for getting Silverlight to run in Linux.

You can run a Windows virtual machine from within Ubuntu to play your Netflix or whatever; that's the only workaround we have.

---

### Post by Kols on 2012-07-19
> **Dngrsone said:**
> Unfortunately, for DRM reasons, moonlight will not substitute for Silverlight, nor is there any public workaround for getting Silverlight to run in Linux.

You can run a Windows virtual machine from within Ubuntu to play your Netflix or whatever; that's the only workaround we have.

Yeah.. I just installed Windows-Firefox in Wine, and then downloaded Silverlight using said Firefox. Install seems to be going fine, until 99%, where Silverlight (in Wine) outputs "Install failed" and Wine returns "Invalid Parameters". 
Dang! Well, I guess I'll just use the Windows-partition to use Viaplay (same as Netflix, I guess). 

What a let-down! It really enrages me that EVERYTHING isn't open source - I'd even pay for some applications, as long as I weren't condemned to the only two OS-options out there; Win or OSX.

I wish I were a developer.

---

### Post by Kols on 2012-07-19
I haven't read it yet, but supposedly SL version 3 is supposed to run in Wine. Check link!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17241](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17241)

---

### Post by Dngrsone on 2012-07-19
It doesn't.  This could be due to lack of DirectX, which Silverlight requires, or a .net component...

---

### Post by Kols on 2012-07-19
> **Dngrsone said:**
> It doesn't.  This could be due to lack of DirectX, which Silverlight requires, or a .net component...

well, is it possible to install direct x, then?

---

### Post by Dngrsone on 2012-07-19
[DirectX and Wine](http://wiki.winehq.org/DirectX-ToDo)
[.net 2.0 Framework and Wine](http://appdb.winehq.org/appview.php?iVersionId=3754)

If you get things to work, you shall be hailed a hero by Linux users worldwide.  Be sure to promulgate your results far and wide.

---

### Post by oldfred on 2012-07-19
I would not be using Silverlight if I was  a vendor.

[http://news.slashdot.org/story/11/11/09/1920247/microsoft-killing-silverlight](http://news.slashdot.org/story/11/11/09/1920247/microsoft-killing-silverlight)
> *"Silverlight 5 might be last version released by Microsoft.*

---

### Post by kartook on 2012-07-20
Still there is no alternative ... :(  

WIndows alternative is Ubuntu ... ubuntu dont have any alternative solutions for silverlight ... as said moonlight is not working :(((:((:((:(:(::((((

Keep searching .................

---

### Post by Kols on 2012-07-29
I'm marking this thread as solved, as there doesn't seem to be a solution out there to implement silverlight in Linux.

---

### Post by Sergey Kurdakov on 2012-08-11
While the thread is closed with SOLVED as of there is no opportunity to run Silverlight under wine, today I seen in Ubuntu a working silverlight

I installed winetricks dotnet20 , latest dev Wine and used firefox 14 for windows
then installed latest Silverlight 5 and the things, I need, worked.

I cannot say if it works for all silverlight applications, but I had a success ( which I had not for a long time ).

edit: latest dev Wine again broke sl support - but it was here, so hopefully it will be back and work for all sl apps

---

### Post by Krepang on 2012-08-15
> **Sergey Kurdakov said:**
> While the thread is closed with SOLVED as of there is no opportunity to run Silverlight under wine, today I seen in Ubuntu a working silverlight

I installed winetricks dotnet20 , latest dev Wine and used firefox 14 for windows
then installed latest Silverlight 5 and the things, I need, worked.

I cannot say if it works for all silverlight applications, but I had a success ( which I had not for a long time ).

edit: latest dev Wine again broke sl support - but it was here, so hopefully it will be back and work for all sl apps

What version of wine was this? i'd like to lock it to this specific version in synaptics so I can use silverlight.

---

### Post by Sergey Kurdakov on 2012-08-22
> **Krepang said:**
> What version of wine was this? i'd like to lock it to this specific version in synaptics so I can use silverlight.

current version 1.5.11 works for almost all sl apps I tried  on Ubuntu 12.04

---

### Post by Dngrsone on 2012-11-30
There is a working PPA [here](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html), which will get you Netflix running under Wine.

I ran it and had Netflix playing on my HP G72 running Ubuntu 12.04-desktop-AMD64 in a manner of minutes with no major glitches.

---

### Post by zoebatty on 2013-01-15
> **Dngrsone said:**
> There is a working PPA [here]("http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html"), which will get you Netflix running under Wine.

I ran it and had Netflix playing on my HP G72 running Ubuntu 12.04-desktop-AMD64 in a manner of minutes with no major glitches.


Thank you for posting this link. It worked great for me :D

---

### Post by Dngrsone on 2013-01-16
> **zoebatty said:**
> Thank you for posting this link. It worked great for me :D

Might be useful if you listed what equipment and OS you are using.

---

### Post by tsi25 on 2013-04-06
am running ubuntu 12.10, 64 bit on a System 76 Lemur Ultra. 

ive been getting netflix to run using that PPA for a couple months now, but just recently it started asking me for a silverlight update, and it wont play anything anymore. ive tried uninstalling and reinstalling netflix desktop, ive tried uninstalling and reinstalling the ppa and netflix desktop, ive tried downloading and trying to run the given silverlight .exe file.... absolutely nothing seems to be working. has anyone come up with any other work arounds? or figured out how to fix this issue? or know when that PPA will be updated?

---

### Post by coldraven on 2013-04-06
I found a solution, don't watch anything that needs Silverlight. 
In the UK, 4OD will not stream nicely using Flash on Ubuntu, their loss, I shall watch something else.
None of these programs are going away, they are still airing the Flintstones from the 1960s.
I suppose that I'm in the minority that threw out their TV some years ago due to the amount of trash being shown.
grumble grumble :)

---

### Post by topdisc on 2013-04-14
> **tsi25 said:**
> am running ubuntu 12.10, 64 bit on a System 76 Lemur Ultra. 

ive been getting netflix to run using that PPA for a couple months now, but just recently it started asking me for a silverlight update, and it wont play anything anymore. ive tried uninstalling and reinstalling netflix desktop, ive tried uninstalling and reinstalling the ppa and netflix desktop, ive tried downloading and trying to run the given silverlight .exe file.... absolutely nothing seems to be working. has anyone come up with any other work arounds? or figured out how to fix this issue? or know when that PPA will be updated?

I created a script which will remove netflix-desktop and associated files and then reinstall everything.  It works but the only problem is that I have to do it all over again the following day.  I think netflix checks for silverlight version every 24 hours or so which causes the "You must upgrade" page to appear on netflix.  I called it 'netflixFix'.

```

#!/bin/bash
## This is how you fix netflix when a silverlight upgrade is required
sudo apt-get purge netflix-desktop
wait
sudo apt-get purge wine-compholio:i386
wait
sudo rm -rf /home/joshua/.wine-browser
wait
sudo rm -rf /usr/share/wine-browser-installer
wait
sudo rm -rf /usr/share/package-data-downloads/wine-browser-installer
wait
sudo rm -rf /var/lib/update-notifier/package-data-downloads/wine-browser-installer
wait 
sudo rm -rf /var/cache/apt/archives/wine-browser-installer*
wait
sudo apt-get autoclean
wait
sudo apt-get autoremove
wait
sudo apt-get update
wait
sudo apt-get -f install
wait
sudo apt-get install netflix-desktop
echo 
echo "Done"
sleep 3
exit

```

---

### Post by Pilot6 on 2013-09-22
Finally it is completely solved for all sites. Not only Netflix.
[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by b6Q8Ats on 2013-09-22
Ill second that Pilot been running that foe a couple a weeks now, works for Skygo as well.

Roy:D

---

### Post by Abbie_A. on 2013-09-23
This could be very good news indeed. Does any one know if Pipelight works for Amazon video? I use Linux at work and want to convert my home theater PC at home.

[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)
[http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html](http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html)

---

### Post by SeijiSensei on 2013-09-24
You can watch Amazon Instant Video in a web browser with Flash after installing the deprecated **hal** and **libhal1** packages.  I don't know whether that will enable it to work with something like XBMC though.

---

### Post by Nickjpost on 2013-10-07
> **Dngrsone said:**
> [DirectX and Wine]("http://wiki.winehq.org/DirectX-ToDo")
[.net 2.0 Framework and Wine]("http://appdb.winehq.org/appview.php?iVersionId=3754")

If you get things to work, you shall be hailed a hero by Linux users worldwide.  Be sure to promulgate your results far and wide.

I have netflix working using pipelight....a project that will no doubt get my financial thanks!

Reference: [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by andy-muss on 2013-12-29
I have read this thread with interest as I was looking at using Blinkbox (uses Silverlight) but since decided not to use.

For your information and for those interested whilst I was researching the use of Blinkbox, I found this article : "Pipelight - Silverlight in Linux Got a New Ubuntu PPA."

Go to UbuntuHandbook.org and search "Silverlight" - ("http://ubuntuhandbook.org/?s=silverlight")

Pipelight, is described as a browser plug-in of which allows Silverlight in your Linux browser the PPA of which includes the required Wine packages. The PPA supports Ubuntu 14.04 Trusty, Ubuntu 13.10 Saucy, Ubuntu  13.04 Raring, Ubuntu 12.10 Quantal, Ubuntu 12.04, Linux Mint and their  derivatives.

I don’t know if this works but thought you guys may want to take a look.

Regards 

andy.muss

"Too much Glass to break in Windows"

---

### Post by fwilhelm on 2014-02-02
Solution to the Silverlight problem is available at [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by cschroter on 2014-02-13
Works using instructions at previous post's link.

Noob here, got stumped by the EULA <ok>, TAB -> ENTER to accept.

Ubuntu 12.04 LTS.

---

