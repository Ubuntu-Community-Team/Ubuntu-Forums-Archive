---
title: "Can't get flashplugin-nonfree to work"
date: 2008-05-25
forum: Multimedia Software
---

### Post by MES5464 on 2008-05-25
Here is my problem. I have a computer with a new install of Ubuntu 8.04. I wanted to install Adobe's Flash plugin. I attempted both the repos and Adobe's installer. Neither of them have worked. Finally, I figured I have a mess of an install so I followed the instructions I found at [Bug #173890]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890") to try and clean up the install and start again. Nothing I have done so far has worked. Any suggestions on how I can clean up my mess?

---

### Post by konungursvia on 2008-05-25
I'm assuming you tried using them in your browser, firefox. Is that correct? If so, do you have any extensions running, such as Noscript? You will need to allow scripts to run on a given web page in order for your flash to work.

---

### Post by MES5464 on 2008-05-25
> **konungursvia said:**
> I'm assuming you tried using them in your browser, firefox. Is that correct? If so, do you have any extensions running, such as Noscript? You will need to allow scripts to run on a given web page in order for your flash to work.

Yes, I am using the 32bit version of Ubuntu 8.04 out of the box and I am trying to view [www.adobe.com](www.adobe.com) using Firefox. No modifications have been made except attempting to install flashplugin-nonfree. I do not have anything running like Noscript.

---

### Post by lud666 on 2008-05-25
Try uninstalling flashplugin-nonfree and pointing firefox at something like youtube.  You should be prompted to install flash through the browser. This will automaticaly set up the symbolic links that are needed.

---

### Post by MES5464 on 2008-05-25
> **lud666 said:**
> Try uninstalling flashplugin-nonfree and pointing firefox at something like youtube.  You should be prompted to install flash through the browser. This will automaticaly set up the symbolic links that are needed.

Ok. I took this advice. First, I used about:plugins in the address bar to find out which plugin Firefox was using for swf files. It was a file (I wish I had written it down) that was probably one of the opensource swf plugins. I then opened a terminal and used "locate <filename>" to find where it was on my computer. Then I deleted it (and the folder it was in as that was all that was in it). Then I opened Firefox and went to YouTube. No luck, it didn't prompt for a plugin. It didn't do anything. Then I went to adobe.com, and nothing happened. So, I tried to reinstall flashplugin-nonfree and it told me I already had it installed. So, I purged it and then installed it again. I then opened Firefox and went to adobe.com and it worked like a champ. Thank you for the idea. I was nervous about how to clean up the flash plugin installs (as I obviously had the opensource and non-free at the same time). By deleting the opensource and purging the adobe plugin, I finally got it to work correctly. Thank you so much!

---

