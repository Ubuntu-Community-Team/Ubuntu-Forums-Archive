---
title: "adobe flash player"
date: 2009-05-17
forum: Multimedia Software
---

### Post by andyubu on 2009-05-17
Hi there: 

I just bought an Acer Aspire AX 3200 having 3 CPUs AMD 64 and 4GB 

then I installed Ubuntu 9.04 64 bits

I follow the tutorial here to install everything related to video & sound

(except the package adobe-flashplugin, which couldn't be found, even when I include the Canonical partner repository) 

Every works fine, except Adobe Flash Player for some websites such as BNN, CTV, PBS

Video from other sites (youtube, yahoo, google, dailymotion, cnn, msn) works fine

Everything looks normal: frame, controls  (see attached screen shots), but the streaming data never happens. 

I am sure that Adobe Flash Plugin is installed successfully. But the problem looks like it couldn't fetch the content (or it even doesn't recognize that it needs to fetch it, since the counter is always 00:00|00:00 and system monitor doesn't show any incoming data at all)

In some websites, when there is a commercial that is preloaded with the page, the commercial plays without any problem, then the clip does not show anything since no streaming data takes place. 

Any help is highly appreciate

Thank you very much

---

### Post by gandaran on 2009-05-17
I tried the same video from your shot but it only played the commercial, the video only plays for Canada residents so I cant help you! 
theres no need to install the adobe-flashplugin and I believe this package doesn't exist yet for 64-bits systems and if it did it would install exactly the same adobe flash plugin as the one you have already installed.

---

### Post by bumanie on 2009-05-17
Try [this]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html"), it works on 9.04 64bit

---

### Post by andyubu on 2009-05-17
still doesn't work

I've already checked about:plugins to verify again that flash player is successfully installed (see attached)  

furthermore, the two facts:
a) it works fine with many websites 
b) even in those websites where it doesn't work, the commercials (not being streamed) still work fine 
suggest that the issue is with the streaming.

I also find this note in "known issues" at   
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

*The prerelease version of the 64-bit Adobe Flash Player 10 for Linux may not be able to play some streaming video content. The 64-bit Flash Player is not yet compatible with the RTMP security measures introduced in the FMS 3.0.3 and 3.5.1 Service Packs, and content delivered using those measures will not play.*

I wonder if this problem is related to this issue. 
That leads to the next question: 

how can I know if these websites (bnn.ca, ctv.ca ...) use those measures (RTMP security measures introduced in the FMS 3.0.3 and 3.5.1 Service Packs) or not?

If they do, then we can do nothing? Just wait until the issue is fix!

Thank you very much

---

### Post by andyubu on 2009-05-17
Hi:

sorry, when I follow the link above ([http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)), I just copied all the command to a script and run it. I didn't verify that it failed to run due to some out of date stuff (such as flashplayer10_install_linux_051508.tar.gz).
 
However, I also realize that I already had the file libflashplayer.so (the latest version), but not in /usr/libs/mozilla/plugins/
so, I copy copy it there

Then I try 
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

this fails with the message
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

There is no point to continue, since this fails, the file 
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
is not created. 

It seems that I get stuck here.

Then I launch firefox again, and happen to re-open the site bnn.ca
Nowm, it works perfectly! 
I try again with other sites ctv.ca, pbs.org... it works just fine. 

The problem is solved, still I am not sure how it was fixed

Thank you

---

### Post by Rentius on 2009-05-24
> **bumanie said:**
> Try [this]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html"), it works on 9.04 64bit

Thanks this has allowed me to install flash player, now to search more threads as to why it's not working on Youtube :confused:

---

