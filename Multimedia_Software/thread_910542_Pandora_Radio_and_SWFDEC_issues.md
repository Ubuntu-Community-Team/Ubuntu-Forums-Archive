---
title: "Pandora Radio and SWFDEC issues"
date: 2008-09-04
forum: Multimedia Software
---

### Post by melodicrevival on 2008-09-04
First off, I'm incredibly new to using Ubuntu. My friend was raving about how wonderful it was so I decided to give it a try. I've been trying to teach myself how to operate it and it's a slow process for sure.

My problem is that I installed Ubuntu and then installed SWFDEC for my flash instead of Adobe. I've been trying to figure out how to uninstall it and haven't managed to do it. I'm tired of having to click on things before I can see them and the like. Mild complaint.

The second problem is when I try to load Pandora radio. I'll click the flash window and it starts to load then it will stop roughly 1/6th of the way through the loading bar. I have no idea why it is doing this.

Any help would be *greatly* appreciated. Thanks.

---

### Post by Dernhelm on 2009-03-03
I am having the same problem (Pandora will not load) directly after installing Jaunty. There are other websites that use flash heavily and also won't work. I thought I might be lacking the flash plugin, but 'Macromedia Flash plugin' is listed as installed on the system, and the test on Adobe's website works fine. It's not listed under add-ons in Firefox, but I assume it's part of 'Ubuntu Firefox Modifications,' which is listed. 

Does anyone have any idea what might be causing this problem?

---

### Post by wolfen69 on 2009-03-03
> **melodicrevival said:**
> 
My problem is that I installed Ubuntu and then installed SWFDEC for my flash instead of Adobe. I've been trying to figure out how to uninstall it and haven't managed to do it.

to uninstall swfdec, go to system>administration>synaptic package manager and search for swfdec. completely remove it. then go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu 8.04+. click to install. restart firefox.

---

### Post by tananaBrian on 2009-04-29
My Pandora failure was completely weird ...It finished loading, then I was presented with an unresponsive (OK button wouldn't work) message (in red/pink) that said something about 'if I don't register with %s then ...blah blah blah'.  I tried the flash installation from Adobe, even though the flash test AT Adobe worked fine ...and no worky.  Then I searched in Synaptic Package Manager for "swfdec" and found that swfdec-mozilla was already installed but swfdec-gnome was NOT installed.  I just clicked the swfdec-gnome and installed it ...voila!  Pandora.com now works fine.  I'm listening to it right now... :popcorn::guitar::P:)

...Hope this helps someone.  Now don't go and listen to my yodeling radio station now.  You'll find out just how weird I am!

Brian

PS: I'm running Jaunty Jackalope, v9.0x ...whatever the latest is.  I just downloaded it this weekend ...and broke Pandora!

---

### Post by Enicko on 2009-04-29
I was running an updated beta version of Jaunty until today when I was forced into a full re-install.  Proir to today Pandora has worked all through Jaunty for me.

Unfortunatly after the fresh install it wasn't. I went into synaptic and loaded the swfdec-gnome package per the instructions above and still a no go - with the same error - pink screen, and some gibberish about %s then no soup for you.

Anyone else out there have this issue? 

Actually, the spell check is turned off on this quick reply section too.  Spooky

---

### Post by tananaBrian on 2009-04-29
Sounds to me like virtually everything having to do with flash needs to be reinstalled for some folks... I'd try completely removing all the swfdec packages, then reinstall and try again.  Have you tested Firefox at Adobe to see if flash is properly installed?

brian

---

### Post by rpwdh on 2009-05-03
I did a clean install of Jaunty today. 

I've installed both swfdec packages and now I get Pandora starting to load and then opening an untitled tab.

No luck yet but maybe this will help someone find a solution. It worked fine in 8.04.

---

### Post by tananaBrian on 2009-05-03
Mine's working now, but if it helps anyone, the following is the response that I got from Pandora on the topic:

"Hello Brian

We're very pro-Linux. In fact, 100% of Pandora's internal systems 
(servers, rippers, databases, etc) are running on Linux. The Pandora 
client does work on many Linux installations. Given the enormous variety 
of Linux distributions and configurations, and the buggyness of the 
Linux Flash Player we can not officially support Pandora for Linux 
desktop clients.

I have been a hard-core Linux desktop user for over a decade. I have 
quite a collection of Linux machines, including my main desktop machine 
which currently has Kubuntu 9.04 AMD64 on it. Pandora is working great 
on that system now, but I did need to do a bit of extra work to make 
that happen.

Here's what I did. I hope this helps you too:

1) Use the Firefox 3 browser and make sure that Pandora is excluded from 
Adblock, Flashblock, or NoScript if you have any of those extensions 
installed.

2) Download the current Flash player for your architecture directly from 
adobe.
    For the AMD64 (64 bit) builds, go here 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
    For all 32 bit builds go here: 
[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz))
    In either case you will be downloading a .gz file. Save it to your 
home directory: /home/<username>

3) Use your graphical file browser (Dolphin, Nautilus, Konqueror, etc)  
to open that downloaded archive file.   
    Within that archive is a file called libflashplayer.so

4) Extract libflashplayer.so to your home directory

5) Get a shell ( for example Menu->Applications->System->Terminal )
    From this point on commands you should type into the shell will be 
proceeded with a $. Do not enter the $ itself.

6) $ mkdir -p ~/.mozilla/plugins
    This creates the required directory to hold the flash plugin

7) $ cp ~/libflashplayer.so ~/.mozilla/plugins
    This copies the extracted plugin from step 4 to the directory where 
Firefox will look for it

8) Shut down and restart Firefox

9) Verify your plugin is installed and working by going to 
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
    You should see version 10.0.xx.yy where xx and yy will vary 
depending on the current release version

10) Go to [www.pandora.com](www.pandora.com) and you should have full Pandora functionality

Let me know how it works out, and what configuration you have. That way 
I can pass the info on to other Linux users.

Thanks for contacting us. We read absolutely everything!"

Enjoy!  Hope it helps!

Brian

---

### Post by dwhamman on 2009-05-04
> **tananaBrian said:**
> 
1) Use the Firefox 3 browser and make sure that Pandora is excluded from 
Adblock, Flashblock, or NoScript if you have any of those extensions 
installed.

2) Download the current Flash player for your architecture directly from 
adobe.
    For the AMD64 (64 bit) builds, go here 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
    For all 32 bit builds go here: 
[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz))
    In either case you will be downloading a .gz file. Save it to your 
home directory: /home/<username>

3) Use your graphical file browser (Dolphin, Nautilus, Konqueror, etc)  
to open that downloaded archive file.   
    Within that archive is a file called libflashplayer.so

4) Extract libflashplayer.so to your home directory

5) Get a shell ( for example Menu->Applications->System->Terminal )
    From this point on commands you should type into the shell will be 
proceeded with a $. Do not enter the $ itself.

6) $ mkdir -p ~/.mozilla/plugins
    This creates the required directory to hold the flash plugin

7) $ cp ~/libflashplayer.so ~/.mozilla/plugins
    This copies the extracted plugin from step 4 to the directory where 
Firefox will look for it

8) Shut down and restart Firefox

9) Verify your plugin is installed and working by going to 
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
    You should see version 10.0.xx.yy where xx and yy will vary 
depending on the current release version

10) Go to [www.pandora.com](www.pandora.com) and you should have full Pandora functionality

Let me know how it works out, and what configuration you have. That way 
I can pass the info on to other Linux users.

Thanks for contacting us. We read absolutely everything!"

Enjoy!  Hope it helps!

Brian

Thanks, Brian!

I have it working now.  In addition to the above procedure, I had to completely remove both SWFDEC packages and reinstall them.

-Dave

---

### Post by nathang1392 on 2009-05-10
all i had to do is delete and reinstall swfdec and then pandora worked fine.

---

### Post by msilis on 2009-05-13
I tried the above suggestions and none of them worked. I ended up removing SWFDEC after installing the current version of Adobe. Seems to be working fine so far. 

Hope this helps.

---

### Post by jswilliams on 2009-05-21
Same issue here, worked in 8.10 (II) but would partially load pandora player and then stop immediately after upgrade to 9.04 (JJ). Installed Adobe Flashplayer from their site, no change. Installed swfdec-gnome in package manager, no change. Completely removed swfdec-gnome and swfdec-mozilla and it worked like a champ. Maybe issues with the swfdec package, it works with adobe??? I dont know, i am fairly new to linux but i ***_REFUSE_*** to go back to winblows [-X I will find a way to make it work or go without it!!

---

### Post by B34N on 2009-05-22
Since I'm a newbie, I thought I would share the mistake that I made in case any other newbies make the same mistake.

To remove Shockwave, you need to use "Synaptic Package Manager" and not the add/remove programs.  Simply search for "swfdec" and then uncheck.  I followed the instructions from Pandora to install shockwave from the .gz file (earlier post in this thread) so I didn't need to reinstall swfdec through Synaptic.  The problem I was originally running into is that I had two versions of Shockwave plugins installed at once and the disable/enable wasn't working for me so I had to actually remove the old version of Shockwave.

---

