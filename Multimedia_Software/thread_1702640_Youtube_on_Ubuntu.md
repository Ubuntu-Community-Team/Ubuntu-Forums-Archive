---
title: "Youtube on Ubuntu"
date: 2011-03-08
forum: Multimedia Software
---

### Post by faozhi on 2011-03-08
Hi guys,

I just installed Ubuntu. First time user of Ubuntu. 
Anyway, everything seems fine and dandy, until I went to firefox and tried watching videos on youtube.
Adobe flash required for viewing youtube videos. So i went to Ubuntu Software Centre and installed the Adobe Flash plugin. Tried watching youtube videos again. However, the videos hang somewhere around 1-2mins and stays there with the buffering icon. This has happened several times and getting kind of irritating. *especially when you are just about to get into the groove of the music*.

Appreciate any help. Cheers.

---

### Post by drpjkurian on 2011-03-08
I am not sure but i guess it may be due to net download speed

---

### Post by shantiq on 2011-03-08
hi fao not sure you have installed the restricted-extras yet


you need to do this on ubuntu to get all your sound and video going

applications/ubuntu software center/


see image


if you already have just ignore

---

### Post by faozhi on 2011-03-08
> **drpjkurian said:**
> I am not sure but i guess it may be due to net download speed

Don't think it is download speed. I am using an edu connection.

---

### Post by faozhi on 2011-03-08
Thanks for the reply. Installed that, but the youtube videos are still stuck at 1 minute +.
Cheers

> **shantiq said:**
> hi fao not sure you have installed the restricted-extras yet


you need to do this on ubuntu to get all your sound and video going

applications/ubuntu software center/


see image


if you already have just ignore

---

### Post by mikewhatever on 2011-03-08
> **faozhi said:**
> Don't think it is download speed. I am using an edu connection.

Some educational institution deliberately block video hosting sites to conserve bandwidth and prevent students from endlessly procrastinating. Try taking youtube's speed test.

---

### Post by slooksterpsv on 2011-03-08
> **faozhi said:**
> Hi guys,

I just installed Ubuntu. First time user of Ubuntu. 
Anyway, everything seems fine and dandy, until I went to firefox and tried watching videos on youtube.
Adobe flash required for viewing youtube videos. So i went to Ubuntu Software Centre and installed the Adobe Flash plugin. Tried watching youtube videos again. However, the videos hang somewhere around 1-2mins and stays there with the buffering icon. This has happened several times and getting kind of irritating. *especially when you are just about to get into the groove of the music*.

Appreciate any help. Cheers.

I've had this problem on both Ubuntu and Windows. It looks like there may have been an issue with Youtube. Also, sometimes a FULL refresh helps (CTRL+R) or the Refresh button, don't just click in the address bar and hit Enter, doesn't work.

---

### Post by faozhi on 2011-03-08
I didn't have this problem when I was using Windows though. :(


> **slooksterpsv said:**
> I've had this problem on both Ubuntu and Windows. It looks like there may have been an issue with Youtube. Also, sometimes a FULL refresh helps (CTRL+R) or the Refresh button, don't just click in the address bar and hit Enter, doesn't work.

---

### Post by gmchaffie on 2011-03-19
> **faozhi said:**
> Hi guys,

I just installed Ubuntu. First time user of Ubuntu. 
Anyway, everything seems fine and dandy, until I went to firefox and tried watching videos on youtube.
Adobe flash required for viewing youtube videos. So i went to Ubuntu Software Centre and installed the Adobe Flash plugin. Tried watching youtube videos again. However, the videos hang somewhere around 1-2mins and stays there with the buffering icon. This has happened several times and getting kind of irritating. *especially when you are just about to get into the groove of the music*.

Appreciate any help. Cheers.

I just started having this problem about a week ago.  It's not the internet connection.  I haven't messed around with any configuration files in that time.   Download speeds are fine.  Video on my hard drive plays well.  I reinstalled flash, but that didn't help.  Could it be related to an update?  

x86_64 with Maverick
NVIDIA Driver Version: 270.29

---

### Post by oboedad55 on 2011-03-19
I've had better luck with the newer version of flash, "Square". It's simple to install, you can get it here; [http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)
Uninstall the previous version and copy the "libflashplayer.so" into your /usr/lib64/mozilla/plugins directory. You'll need to use "sudo" or be root for the copy.

---

### Post by gmchaffie on 2011-03-19
> **oboedad55 said:**
> I've had better luck with the newer version of flash, "Square". It's simple to install, you can get it here; [http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)
Uninstall the previous version and copy the "libflashplayer.so" into your /usr/lib64/mozilla/plugins directory. You'll need to use "sudo" or be root for the copy.

Thanks, but it didn't help.  I've disabled all other plugins and add ons with no improvement.  Same hiccup of course happens with Chrome.  No idea.

---

### Post by oboedad55 on 2011-03-19
Sorry man, was worth a shot. Sounds like the problems is elsewhere then.

---

### Post by Sodear on 2011-03-19
I had exactly the same problem both with Firefox and Chrome.  I've solved it but I'm not sure I have all the steps, but here goes:
1. Follow Sticky's instructions under Multimedia in Ubuntu forums re enabling medibuntu repository.
It is presumed that you have enabled multiverse, universe and restricted repositories: these are enabled by default in Maverick.
2.  Obliged to another Ubuntu-Answers for the following: In Applications-Accessories-Terminal type in sudo apt-get remove --purge flashplugin-nonfree and when that's done type in sudo apt-get install flashplugin-nonfree
Now visit adobe.com/shockwave/welcome and follow instructions to find out which version you have installed.  
Check whether you can see youtube on Firefox first.  Then try Chrome.
At this stage, Youtube worked on Firefox but crashed in Chrome.
3. In the Chrome browser bar type in 'about:plugins'  A list of plugins will appear, so check whether there are two  plugins of Shockwave Flash or Adobe Flash.  
4. Disable one of them and try Youtube and if it doesn't work enable it again and disable the other.
That's as much as I remember and I hope it works for you.  

Is your chromium icon blue/darkblue or is it red yellow green?  If the former - remove chrome using synaptic package manager under System-Admin and cruise over to google.com and download chrome for Linux.  I don't know if this actually amounts to much, but that was one of the steps I took at the beginning.  That way Chrome comes from Google, rather than from the available packages in the software center.

I'll add the following information I printed out from another source:
1. Install Google Chrome
2. sudo apt-get install flashplugin-nonfree
3 sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/chromium-browser/plugins
4. Right click the Chrome icon, click on Properties and in the command line enter  chromium-browser --enable-plugins

That did not work for me since Ubuntu could not find usr/lin/flashplugin etc.

---

### Post by gmchaffie on 2011-03-25
I tried everything suggested and nothing worked.  Flash just had an update and voila, I can stream video again.

---

### Post by andrew.46 on 2011-03-26
Mind you there is another option these days. Make sure you are using a modern browser like Firefox 4 and then change [your preferences in youtube]("http://www.youtube.com/html5") to try the webm/HTML5 videos. Much more stable than Flash :).

Andrew

---

