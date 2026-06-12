---
title: "Flash problems and firefox?"
date: 2009-02-11
forum: Multimedia Software
---

### Post by Kain000 on 2009-02-11
Hey everyone, 

I think i've got a problem with flash on my system, I must have used a different plugin on my old system as i never had this issue before, but when I look at a webpage that has a video or animation it just apears as a grey block with a play button.  I want it to load with the page like it would normaly,    i'm using swfdec flash play plugin for firefox and gnome.

I've tried the adobe one but no luck.

---

### Post by redroad55 on 2009-02-11
read this guide .. particularly the section on Trouble Shooting :adobe flash  
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

 > --TROUBLESHOOTING--


ADOBE FLASH PLAYER


On occasion, installing Adobe Flash Player and/or watching online Flash streams successfully isn't as simple as it might ordinarily be. If you have tried installing it already, and are having issues, read on. First of all, please disable any ad-blocking Firefox extensions you have installed, such as Adblock Plus, as they can sometimes interfere with the Flash content you actually want to see. If you are still having issues after disabling the extension(s), you should now completely purge Adobe Flash Player from your system, along with any other packages which may be interfering with it, reinstall only Adobe Flash Player, restart your web browser, and then test Flash performance again. Will both 32-bit and 64-bit users copy and paste this command into the terminal:

sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree

Still no joy? I would suggest following the instructions below for your particular Ubuntu version and architecture.


UBUNTU FAMILY 8.04+ USERS ONLY


Note: You can safely install the Ubuntu package (flashplugin-nonfree), or a Deb archive over the top of the Tar installation method at a later date - I've tested it several times. There's absolutely no need to remove any of the manually installed files, as they will simply be overwritten.

First of all, copy and paste the following command into the terminal and remove the package installed by Ubuntu:

sudo apt-get purge flashplugin-nonfree

32-Bit Users Only: Those of you running the 32-bit version of Ubuntu can install the Flash Player plug-in by selecting and downloading the Deb archive in the drop-down menu on this page of Adobe's site, then executing it and entering your root password when prompted.

32/64-bit Users: Alternatively, 32-bit users can download the Tar archive from the same link provided above and follow my instructions below. If you're a 64-bit Ubuntu user, download the Tar archive of the 64-bit Flash Player plug-in from the bottom of this page to your desktop.

Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then both 32-bit and 64-bit users execute the following command in the terminal:

sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart your web browser and use the plugin.


PRE-UBUNTU FAMILY 8.04 USERS ONLY


Note: You can safely install the Ubuntu package (flashplugin-nonfree), or a Deb archive over the top of the Tar installation method at a later date - I've tested it several times. There's absolutely no need to remove any of the manually installed files, as they will simply be overwritten.

First of all, copy and paste the following command into the terminal and remove the package installed by Ubuntu:

sudo apt-get purge flashplugin-nonfree

Install the Flash Player plug-in manually by selecting and downloading the Tar archive in the drop-down menu on this page of Adobe's site if you're a 32-bit Ubuntu user, and from the bottom of this page if you're a 64-bit Ubuntu user.

Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then execute the following command in the terminal:

sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so

You may now restart your web browser and use the plugin.


Post back any results and or questions .. Best to you

---

### Post by obscur156 on 2009-02-11
Do you have "ubuntu restricted extras" installed ???

Usually its working great.If not you can install it via ADD/REMOVE or SYNAPTIC MANAGER.

Good luck,regards.

---

### Post by gandaran on 2009-02-11
> **Kain000 said:**
> Hey everyone, 

I think i've got a problem with flash on my system, I must have used a different plugin on my old system as i never had this issue before, but when I look at a webpage that has a video or animation it just apears as a grey block with a play button.  I want it to load with the page like it would normaly,    i'm using swfdec flash play plugin for firefox and gnome.

I've tried the adobe one but no luck.

you shouldn't be using swfdec flash, thats why you have that big play button, can you provide system details (ubuntu 32-bits or 64-bits, ubuntu 8.04 or 8.10) we will help you remove swfdec and install adobe flash.

---

### Post by redroad55 on 2009-02-11
the problem I have here is what you currently have is multiple installs of flash .. How you got there is reading posts like the one above and people like myself are left helping you untangle the mess .. Weekly here on this forum its the same story .. A purge is needed 98% of the time .. I say this so in a couple of days ..I'm not trying to help you unwind it all..Peace out

---

### Post by redroad55 on 2009-02-11
Wasn't talking about you gandaran

---

### Post by gandaran on 2009-02-11
> **redroad55 said:**
> the problem I have here is what you currently have is multiple installs of flash .. How you got there is reading posts like the one above and people like myself are left helping you untangle the mess .. Weekly here on this forum its the same story .. A purge is needed 98% of the time .. I say this so in a couple of days ..I'm not trying to help you unwind it all..Peace out
+ one 
install this, install that, it works great! this is the kind of help you get here 90% of times which just adds to the mess up without getting to root problem.

---

### Post by Kain000 on 2009-02-11
> **redroad55 said:**
> the problem I have here is what you currently have is multiple installs of flash .. How you got there is reading posts like the one above and people like myself are left helping you untangle the mess .. Weekly here on this forum its the same story .. A purge is needed 98% of the time .. I say this so in a couple of days ..I'm not trying to help you unwind it all..Peace out

right right, 
I purged the default flash install per the article you suggested.

So as to more info it's ubuntu 8.10 32 bit.

should I run a 

sudo apt -purge swfdec?

then install adobe's flash per the article?

---

### Post by redroad55 on 2009-02-11
this removes everything:
> sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla
 either of these 2 methods work for install:
 > 32-Bit Users Only: Those of you running the 32-bit version of Ubuntu can install the Flash Player plug-in by selecting and downloading the Deb archive in the drop-down menu on this page of Adobe's site, then executing it and entering your root password when prompted.

32/64-bit Users: Alternatively, 32-bit users can download the Tar archive from the same link provided above and follow my instructions below. If you're a 64-bit Ubuntu user, download the Tar archive of the 64-bit Flash Player plug-in from the bottom of this page to your desktop.

Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then both 32-bit and 64-bit users execute the following command in the terminal:

sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart your web browser and use the plugin.

this is the adobe link for your download:
   [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

select .deb for Ubuntu 8.04 pkg. in drop down
Post back

---

### Post by Kain000 on 2009-02-11
you sir are a gentleman and a scholar!  

Things are back to normal now thanks alot.


so what is swtdc for anyway?

---

### Post by Kar.ma on 2009-02-13
Hi, I want to share my solution.


I have Ubuntu 8.10 and Firefox 3.0.6
I could see most Flash applets, but not YouTube, which was crashing.

In this "about" page [http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/) I saw Flash 9.0.999 (or similar) even if I had already installed Flash 10.0.15.3 (you can get latest from [http://get.adobe.com/it/flashplayer/](http://get.adobe.com/it/flashplayer/) )

I fixed all my problems this way:
1) close firefox
2) sudo mv /usr/lib/swfdec-mozilla/libswfdecmozilla.so /usr/lib/swfdec-mozilla/libswfdecmozilla.so.old
3) open firefox and go to "about" page (see above) and choose to install plugin named "Adobe Flash Mozilla Player" (or similar, but starting with "Adobe")
4) restart browser and verify your version in the about page

that's all!

---

### Post by mrche on 2009-08-08
THANK YOU. THIS WORKS WONDER!

I have no idea why no one else bother to post back but this works like a charm for me ! :guitar:

> **Kar.ma said:**
> Hi, I want to share my solution.


I have Ubuntu 8.10 and Firefox 3.0.6
I could see most Flash applets, but not YouTube, which was crashing.

In this "about" page [http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/) I saw Flash 9.0.999 (or similar) even if I had already installed Flash 10.0.15.3 (you can get latest from [http://get.adobe.com/it/flashplayer/](http://get.adobe.com/it/flashplayer/) )

I fixed all my problems this way:
1) close firefox
2) sudo mv /usr/lib/swfdec-mozilla/libswfdecmozilla.so /usr/lib/swfdec-mozilla/libswfdecmozilla.so.old
3) open firefox and go to "about" page (see above) and choose to install plugin named "Adobe Flash Mozilla Player" (or similar, but starting with "Adobe")
4) restart browser and verify your version in the about page

that's all!

---

