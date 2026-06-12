---
title: "Cannot click on any feature on youtube 9.10"
date: 2009-11-11
forum: Multimedia Software
---

### Post by OO_Donut on 2009-11-11
Ok, First let me say that I am new to ubuntu. This is the first version that I have used, and I have gotten a hang of alot of the things via tutorials, and videos. 

So here is my problem - When I go to youtube the video will play fine. Now what doesnt work is clicking on anything related to flash  in the video section. (the box that you control the video from. play pause volume HD HQ and even if I right click and select settings, once again I cannot click on anything int he little box)

I have reinstalled ubuntu 3 times trying to figure it out, each time with a different way to install all of the codecs and plugin players, I dont want to install a 4th time, but I dont really know how to successfully uninstall anything I have added to ubuntu this far so it might be my only option. 

I am using x64 ubuntu Distro if you need any more information just ask. 

Also if there is a fully automated way to install anything needed like codecs and plugins I would be willing to go that route as long as it fixes this problem.

Thank you very much!!!
Nathan

---

### Post by jimk351c on 2009-11-11
I just installed 9.10 today and am having the same problem. It seems to happen with all sites utilizing FLASH.

---

### Post by OO_Donut on 2009-11-11
Ok, So I have been playing around with everything for a couple hours now, and I cannot see any rhyme or reason for this. 

I uninstall adobe flash, reinstall adobe flash through **Applications>Ubuntu software center** and try youtube, Hey look everything works. I then Click on another link and lone behold, It doesnt work again. So I repeat the process to see if it works the first time only, and guess what? It doesnt work. 

I am not giving up yet, I want to figure this out. I like ubuntu so far, I just hate that I am having this problem. It is making me want to just go back to windows 7, But I want to be able to use both equally well, I guess you could say this is a learning experiance for me to truble shoot and use the terminal alot in ubuntu =]

Please help!!!

---

### Post by HappyFeet on 2009-11-11
OK, settle down. Since you are using 64bit ubuntu, we're going to go a different route.

First, uninstall flash. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

I do this, and it works every time. Let us know how it goes.

---

### Post by michy99 on 2009-11-11
A bit of searching turns up this:```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```Add this before the last line of text```
export GDK_NATIVE_WINDOWS=1
```then save and restart firefox.

---

### Post by HappyFeet on 2009-11-11
> **michy99 said:**
> A bit of searching turns up this:```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```Add this before the last line of text```
export GDK_NATIVE_WINDOWS=1
```then save and restart firefox.

That is just a workaround. My method is the preferred way to install the proper flash file. Actually, you can install the flash file via GUI also, but it's just as many instructions.

---

### Post by /usr/bin/hacked? on 2009-11-11
rawr!

---

### Post by HappyFeet on 2009-11-11
> **/usr/bin/hacked? said:**
> rawr!

Please keep comments like that confined to the community cafe. People need help here, not silly comments.

---

### Post by OO_Donut on 2009-11-11
Ok, I didnt think I would ever say this, but thank you happy feet!!! 

ok, so I had wubi on my laptop, and the first thing I did was what you said, and it works!!! =] so I had messed with my install on my desktop so much that when I tried what you said, when I would go to youtube, the firefox browser would just close, and it would go to other websites fine, so i figured a fresh install would be best. I will let you know how it works, but I think it will work fine. =]

I know your prolly thinking that a full install was a little overkill but right now I am still working on getting around ubuntu so I dont think I would be able to fix whatever I messed up. 

So with that being said is there any other things that 64 bit will have a problem with? in ways of codecs and such? should I just install the other ones normally?

Once Again, Thank you!

---

### Post by HappyFeet on 2009-11-12
It's all pretty much the same as far as codecs and such. I find 64bit ubuntu a bit more stable and robust. YMMV. And in 32bit ubuntu, you can download the regular tar.gz and put it in /usr/lib/mozilla/plugins

It's the same for opera too, you just obviously need to change the path to /usr/lib/opera/plugins

Have fun and don't hesitate to ask any questions.

---

### Post by HappyFeet on 2009-11-12
But as far as the reinstalling bit, take no shame in it. Installing OS's is an undervalued skill. I remember reinstalling a bunch of times when I first started, but after a while you just know what NOT to do, and enjoy your OS.

Edit: make sure to install the medibuntu repos.

---

### Post by Inferiority Complex on 2009-11-12
> **HappyFeet said:**
> OK, settle down. Since you are using 64bit ubuntu, we're going to go a different route.

First, uninstall flash. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

I do this, and it works every time. Let us know how it goes.

I've been having Flash clicking trouble since the upgrade to 9.10 and I just thought I'd say thank you for providing this info - worked a treat for me.

I was fairly certain I already had the 64-bit flash player already but perhaps I didn't...

---

### Post by OO_Donut on 2009-11-12
@ Inferiority Complex - I am glad that my question helped someone else as well =]

@ HappyFeet -  
> make sure to install the medibuntu repos.     Do you mean medibuntu community documentation? ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu))

and if so, Just to make sure, I am going to list the ones here that I will want to run in terminal. Correct me if im wrong =]

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update[/quote][quote]sudo apt-get install libdvdcss2

or

wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

```I dont know if i should do the whole thing, or just the amd 64 part
```
sudo apt-get install w64codecs
```And I dont know if i need this last one or not -

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb
sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb
```

---

### Post by DesertBlade on 2009-11-13
Seems like I need to do this with every update of Ubuntu. At least in 9.10 Flash actually kinda worked out the box.

> **HappyFeet said:**
> OK, settle down. Since you are using 64bit ubuntu, we're going to go a different route.

First, uninstall flash. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

I do this, and it works every time. Let us know how it goes.

---

### Post by OO_Donut on 2009-11-14
I still am not sure about my last post. I still dont have everything on there yet, being as i dont want to screw up again.

Any suggestions?

---

### Post by fostytou on 2009-11-15
Thanks happyfeet!  Fixed my Pandora problem too.

---

### Post by jimbosyn on 2009-11-15
> **fostytou said:**
> Thanks happyfeet!  Fixed my Pandora problem too.

FYI... This fixed my issues as well!  Thanks for the help.

---

### Post by R0manus on 2009-11-19
Thank you sir! As I am a brand new ubuntu user and the help I got from the community, I will now install Ubuntu on my 70 year old mother in law's computer. I will tell her , it is is the new thing, and she has no choice. force learn is a good trick.

> **HappyFeet said:**
> OK, settle down. Since you are using 64bit ubuntu, we're going to go a different route.

First, uninstall flash. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

I do this, and it works every time. Let us know how it goes.

---

### Post by DragonlordP on 2009-11-23
How do I "uninstall flash" in the first place? I have only installed ubuntu-restricted-extras which includes it.

---

### Post by parsim on 2009-11-23
From [the Ubuntu bug report](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407):

> So here the bug and workarounds.

For example on youtube, whilst it recognises my mouse moving over various buttons, actual mouse clicks are not recognised. I can navigate using 'tab' but this is very painful. I can also right click. The problem doesn't occur with other flash players, e.g. swfdec-mozilla.

WORKAROUND 1: Disable compiz
WORKAROUND 2: Remove flashplugin-nonfree / flashplugin-installer and install from adobe
WORKAROUND 3: Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

Note: The only workaround for Chrome/Chromium users is to disable compiz.

Workaround #3 seems to be the most painless option atm.

---

### Post by DragonlordP on 2009-11-24
Thanks a lot, that did the trick.

---

### Post by touchlikefire on 2009-11-24
> **HappyFeet said:**
> OK, settle down. Since you are using 64bit ubuntu, we're going to go a different route.

First, uninstall flash. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

I do this, and it works every time. Let us know how it goes.
I've installed 64bit flash from:
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

(Which seems to be the same as your instructions)

However, I'm still getting wacky behavior out of youtube and the like, similar to the OP (unable to press buttons in the flash frame/module).  Also, when flash is active, I get **npviewer.bin** showing in my process list.

Isn't npviewer.bin the 32-bit flash?

Otherwise, do you have any suggestions or could you walk me through complete removal of Flash and reinstallation? Synaptic doesn't list any of the flashes are installed, so I'm not sure how I'd go about removing them on my own.

---

### Post by parsim on 2009-11-24
> **touchlikefire said:**
> Otherwise, do you have any suggestions or could you walk me through complete removal of Flash and reinstallation?

Did you read my post? There are 3 ways to fix this problem, and the link I posted includes plenty of description on how to remove Flash, if that's the route you choose (e.g. [this comment](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407/comments/16)).

---

### Post by touchlikefire on 2009-11-24
I read this entire thread, in fact.  Let me rephrase my question. Karmic installed the ndis-wrapped 32-bit version of the Flash plugin, which everybody knows sucks.

So I went about getting rid of it, per the instructions in my link.  However, I suspect that it is not really gone, since even though I've installed the 64bit Adobe plugin alpha, I get weird behavior from flash websites, similar to the OP.  Also, when I ```
top
``` I get **npviewer.bin** near the top, which I was under the impression was the 32-bit plugin.

So my intuition is that FFx is actually using the 32bit plugin instead of the 64bit. Since ```
aptitude search flash
``` shows nothing is installed, I'm not sure how else to verify this.

My question, then, is:
If I've already installed the 64bit flash, and I'm getting the aforementioned problems, how do I check if the 32bit flash is in use or installed, and if so, how do I remove it manually?

---

### Post by parsim on 2009-11-24
Well, the link I pointed you at last post says: 

> there were many steps to kill the old Flash plugin. Here's the commands I ran from my history (after extracting the adobe .tar.gz download to ~/Temp):

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

sudo cp ~/Temp/libflashplayer.so /usr/lib/mozilla/plugins/
sudo cp ~/Temp/libflashplayer.so /usr/lib/firefox-addons/plugins

I'm now able to watch fullscreen HD from Youtube & scroll around, play/pause without issues.

So that's how you get rid of the 32-bit flash. But, like I said in my post before that, this seems like a lot of trouble when you can solve the original problem via a simpler method.

---

### Post by touchlikefire on 2009-11-24
I apparently I didn't click through the link to see that information, thanks.

I've got a big problem now, however. Flash doesn't work at all. I entered the remove commands above, then copied the file to the listed locations, and...no dice.

I've gone through this tutorial, and the one here: [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102) but I don't know what I'm doing wrong.

---

### Post by touchlikefire on 2009-11-24
Fixed by removing everything again by the above commands, and then installing the **flash-installer** package from Synaptic. I'll then try these steps over.

---

### Post by the4thamigo_uk on 2009-12-16
Thanks HappyFeet this is an excellent workaround. I had problems after an auto update of flash which caused my working flash plugin to stop responding to mouse clicks on plugin buttons. Now it works. Thank you!

---

### Post by Dirjel on 2010-02-02
> **parsim said:**
> From [the Ubuntu bug report](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407):



Workaround #3 seems to be the most painless option atm.

Most painless *and* effective.

Workaround #2, the one suggested by HappyFeet, did not work for me.

Of course, disabling compiz might've worked also, but I didn't want to do that >.>

Thanks, ubuntuforums ^_^

---

