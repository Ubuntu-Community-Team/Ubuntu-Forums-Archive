---
title: "Firefox Flash player plugin on Ubuntu 12.04.2 64 bit and Youtube HD videos"
date: 2013-06-19
forum: Multimedia Software
---

### Post by giordan on 2013-06-19
Hi all,

In the past three hours I had several troubles trying to install the Adobe Flash Player plugin for Firefox... I think the previous installation get corrupted or had some other problems, since YouTube videos were reproduced in spurts.
So I removed and reinstalled Flash Player plugin but, even if Firefox can see it, it didn't work since YouTube videos and other sites which relies on Flash didn't work correctly.

Now I installed it through this guide:
[http://ubuntuguide.net/install-adobe-flash-plugin-in-ubuntu-12-04both-3264-bit](http://ubuntuguide.net/install-adobe-flash-plugin-in-ubuntu-12-04both-3264-bit)

and it seems to work fine, even if going on this page:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

it says me that additional plugins are required. However, if I click for installing missing plugins it doesn't find anything, and it remains searching them for several minutes.

However, the thing that I noticed doesn't work is that when switching to full screen mode on an YouTube video it doesn't switch to HD but to 480p. I'm pretty sure that with the previous installation of Flash Player video get switched automatically to HD, but now not.

Can this be related to my installation of Flash Player? However if I manually click on 720p it works fine.

And another question, what can be the reasons of my difficulties in installing Flash Player and in the impossibility for Firefox to find missing plugins?

Thanks in advance. :)

---

### Post by sum1nil on 2013-06-21
I am unsure if the the Linux and Flash relationship extends to HD video. I am unsure of those tutorials as they don't even give the right permissions to flash:
[U]2.) Change file permission via:

sudo chmod 775 /usr/lib/flash-plugin/libflashplayer.so
[/U] - mine are 644 along with my other plug-ins and I did the same procedure when I had 12.04...just saying.

Go here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download the .tar.gz to your ~/home/Downloads. Fire up file roller with 'sudo file-roller'. Extract all the files and follow/read the readme. The Firefox plug-in folder is here '/usr/lib/mozilla/plugins' so do 'cp libflashplayer.so /usr/lib/mozilla/plugins/' from your Downloads folder.

Make sure the plug-in owner is root and permissions are rw-r-r

Follow the readme to a tee especially these line(s):
Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
		+ sudo cp -r usr/* /usr

This is in a terminal working from the folder where flash was extracted. I didn't have to make links or cupcakes like in the tutorial.

You should have flash. If not, I would go back to that tutorial and undo every step it had you do. Also , email that person to not use Salvia in the mornings :P

Best of luck.

---

### Post by MadmanRB on 2013-06-21
I say forget about flash in firefox, flash for linux is dead.
Sadly the only real alternative is to use google chrome now with pepperflash.
Until flash is dead and replaced with HTML5.

---

### Post by monkeybrain2012 on 2013-06-21
I have no problem playing HD videos on FF with flash. I just installed flashplugin-installer from the repo, nothing fancy, However I prefer not to use flash for Youtube and many other sites, [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
  to use that you should also Install gecko-mediaplayer (otherwise the totem plugin works too)

99% of flash contents on the web play well on Firefox and there is no need for pepper flash. I installed Chrome just in case, but never need to use it for flash.

---

