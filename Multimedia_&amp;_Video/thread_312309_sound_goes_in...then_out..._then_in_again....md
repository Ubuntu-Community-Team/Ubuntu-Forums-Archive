---
title: "sound goes in...then out... then in again..."
date: 2006-12-04
forum: Multimedia &amp; Video
---

### Post by olivesmarch4th on 2006-12-04
All right, I'm getting a little sick of this.

In Dapper Drake my sound works just fine in all other capacities except through flash.  I went through all the help literature and I installed the plugin it told me to (I did this more than once), but nothing happened.  Then a friend suggested I open my Multiverse repositories--I did that, and my sound worked for about two weeks.  Now it's not working again, I suspect it has to do with a recent update, but I want to find out what the f*** is going on so I can fix it for good instead of taking random shots in the dark and hoping it works.

I'm pretty new to Linux.

So if anybody has any idea please let me know.

thanks ever so much,
Christy

---

### Post by an.echte.trilingue on 2006-12-04
> **olivesmarch4th said:**
> taking random shots in the dark and hoping it works.

Welcome to Linux.





HAHAHA I crack me up sometimes ... <sniff> ... ahhhhh ... sorry.

Anyways, back to your problem, when you say that you have followed every guide you can think of, it would help if you were a little more specific and let us know which guide you followed so that we can see what it is you did; specifically, did you follow [this guide]("https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3")?  I did and it always works perfectly for me.  That page is also how I got all other media formats working.

As for enabling universe and multiverse, those are software repositories, but simply enabling them will not do anything unless you install software from them.  Be sure to read the wiki pages on installing software and managing repositories if you have not already.

Take care,
-mat

---

### Post by Temis on 2006-12-04
I don't think its funny. After the recent automatic update of Flash the sound
on Google video and Youtube does not work.Before it worked perfectly.
Do not bother I read all the guides and checked all the settings. 
To no avail.

---

### Post by an.echte.trilingue on 2006-12-04
I am sorry you do not think that my joke is funny.

However, I am using 6.06 like the OP and I just did an update and flash works fine for me.  If the OP will post what he/she has already done, somebody might be able to help... same for you...

---

### Post by olivesmarch4th on 2006-12-04
Trilingue:  Awesome user name and icon!  People who speak more than one language are all right in my book (I speak Spanish as a second language. :)

Ok, this is what I have done.  I followed the instructions here.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

I definitely got confirmation in Terminal that I successfully installed it.

When I enabled the Multiverse repositories, I did, indeed download some new software, and it seemed to work beautifully, to my astonishment.  If I knew what I was doing, I would have some idea what I downloaded from the Multiverse that worked.  But alas.

I checked out your link and the Troubleshooting page links to exactly what I already did-also, predictably, the provided "auto-install" code didn't work probably because that file is already installed.  My uncle/friend told me that the solutions to flash problems with Linux generally aren't open-source or provided by Adobe--hence opening up the Multiverse repositories.

What the hell is the difference between AMD64, PPC and i386, and is this relevant to my problem?

I understand there is more troubleshooting stuff on this page, but it doesn't make a lot of sense to me.  I admire all of you who so delicately tweak the internal workings of your systems.  To me, it feels like I'm hacking at my system with an axe.

Thank you infinitely,
Christy

---

### Post by an.echte.trilingue on 2006-12-06
First off, PPC, AMD-64, i386 are processor architectures.  i386 is for any pentuim class processor (or applicable clone from AMD), AMD64 is for 64 bit processors from AMD, SMP is for multi-core processors (such as the pentuim D) and PPC is for the powerPC architecture most frequently seen in Macintoshes until recently.  Right now, there is no flash for 64 bit processors or PPC that I know of; if you have that you will have to use the slightly less functional swf-player instead.  

As for your problem:  software that is written for a "linux" and not for "Fedora Core" or "Ubuntu" or "SuSE" almost never works, especially not something as complicated as flash.  The reason for this is that each linux distribution is made to do something slightly different and as such different pieces of the OS are located in different places or are different versions.  

Slightly different from what your friend said, flash itself is proprietary but thanks to the GPL, the flash installer itself (AFAIK) is open source, and so the maintainers of Ubuntu can tweak it to fit to their version of linux.  This is why it is always better to install software from the repositories of any given distribution whenever possible.  I would be willing to bet money that a symbolic link between flash and your sound daemon is all that is missing, but I do not know for sure.

Please note that there are a couple of open-source alternatives to flash, such as swf-player.  If you really cannot get macromedia flash working, that may be a viable alternative.  I have not used it in a long time, but I understand it is still somewhat less functional than macro-media's offering.

Anyway, in the case of the flash installer, I think the first step for you would be to uninstall the flash installer.  From the readme:

>  Uninstall instructions
---------------------

To remove the Plug-in Player for Linux:

For root users:
- Quit the browser.
- Navigate to the browser's plug-in directory (i.e. /usr/local/mozilla/plugins).
- Remove libflashplayer.so and flashplayer.xpt.

 

For non-root users:
- Quit the browser.
- Navigate to your home directory and locate the folder named .mozilla.
- From that folder, open the folder named plugin and remove libflashplayer.so, flashplayer.xpt and x-shockwave-flash.desktop.

Then open synaptic if you are using Ubuntu and Adept if you are using Kubuntu.  Make sure that you have [Universe and Multiverse enabled]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096").  Now, search for the package flashplugin-nonfree or something along those lines.  If it is not installed, install it, if it is installed, mark it for reinstallation since the removal process above will have messed it up if it was installed.  Once it has downloaded, a popup window will appear to let you know that synaptic is working on installing it.  Now, Flash has a license agreement that you have to agree to.  In some versions of synaptic, you will get another popup that will ask you to agree, but in mine, you have to click on the "details" button on the progress window to see the agreement.  Once you agree, it will finish installing.  Then type this in a terminal:

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd 
sudo gedit /etc/rc.local
```

When gedit opens, put this line **before** the line that says "exit 0":
```
ln -s /tmp/.esd-1000 /tmp/.esd 
```

Now, flash should be working in Firefox.  If it isn't let me know and we'll try to dig a little deeper into logs and stuff.

Good Luck and Go Blue!
-mat

---

