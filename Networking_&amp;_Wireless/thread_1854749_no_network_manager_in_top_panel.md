---
title: "no network manager in top panel"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by ronaldalanbarberjr on 2011-10-05
Hi just installed ubuntu 11 and there is no network manager in the top panel.  hit alt f2 and typed nm-applet and nothing.  went to the dash and typed terminal and then nm-applet and it said  an instance of nm-applet is already running  warning  couldn't initialize the d-bus manager.  now what?

---

### Post by ronaldalanbarberjr on 2011-10-05
Hi i'm one day into the new ubuntu and i'm completely lost!  there's no newtork manager in my top panel and i've tried alt f2 nm-applet and nothing.  then the dash typed terminal and then nm-applet and it said  an instance of nm-applet is already running  warning  couldn't initialize the d-bus manager.  any ideas?  thanks so much

---

### Post by amjjawad on 2011-10-05
> **ronaldalanbarberjr said:**
> Hi i'm one day into the new ubuntu and i'm completely lost!  there's no newtork manager in my top panel and i've tried alt f2 nm-applet and nothing.  then the dash typed terminal and then nm-applet and it said  an instance of nm-applet is already running  warning  couldn't initialize the d-bus manager.  any ideas?  thanks so much

Hello and Welcome :)

More details will be helpful so that no one will help you blindly based on guess :)

What Release are you using?
Is this Normal or Wubi Installation? 
Are you trying to connect to the Internet via Wire or Wireless Connection?

This will help you for faster answers: [www.googlubuntu.com](www.googlubuntu.com)
Or just try the regular website: [www.google.com](www.google.com)

---

### Post by ubupirate on 2011-10-05
If you are on 10.04 or 10.10, give this a try and see what happens:

```
gconftool --recursive-unset /apps/panel && rm -rf ~/.gconf/apps/panel && pkill gnome-panel
```

Also note this will remove any customizations you've made to the gnome panel, so you may want to backup of your panel first.

---

### Post by ronaldalanbarberjr on 2011-10-07
I just installed 11.04 for the first time ever, and I'm having a problem getting online.  I cannot search for available wireless networks, and the network manager in the top panel beside the volume is not highlighted for use.  I've searched some other threads and some new user info without success.  Can someone please give me some help?  I'm using Ubuntu alongside XP.  My wifi is on and the router works in windows.  My wireless card is a Broadcom 802.11n

---

### Post by wildmanne39 on 2011-10-07
Hi, welcome to the forum! Please open a terminal ctrl+alt+t then copy and paste the commands into it, then paste the output here:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mörgæs on 2011-10-07
Please don't create multiple threads on the same problem. 
Have merged your three threads.

---

### Post by ronaldalanbarberjr on 2011-10-07
Thanks for the response.  Sorry, but I can't seem to get back into Ubuntu.  Before, I could restart my computer and i would have to choose between Ubuntu and XP.  Now, when I restart it just goes straight to XP.  The Ubuntu files are still there, and I don't think I've changed anything.  Help!

---

### Post by wildmanne39 on 2011-10-07
Hi, for the new issue you should start a new thread with a title that describes the problem in installation and upgrades or general section, you will get more help that way for the new issue.
Thank you

---

### Post by ronaldalanbarberjr on 2011-10-08
thanks so much.  I'll keep trying.  Once I get back in I'll do what you've asked.

---

### Post by wildmanne39 on 2011-10-08
Hi, okay I will keep a check on this thread.
Thank you

---

### Post by ronaldalanbarberjr on 2011-10-08
OK, how am I supposed to copy and paste all of that info from ubuntu back here to xp?  I'm having to switch back and forth.  Is there a way, or do I have to just write it down?  thank you for your response

---

### Post by wildmanne39 on 2011-10-08
Hi, copy to a flash drive then post the information here.
Thank you

---

### Post by ronaldalanbarberjr on 2011-10-08
distrib_id=ubuntu
distrib_release=11.04
distrib_codename=natty
distrib_description="ubuntu 11.04"
linux ubuntu 2.6.38-8-generic #42 ubuntu smp mon apr 11 3:31 utc 2011 i686 i686 i386 gnu.linux

-mm produce machine readable output single -m for obsolete format
-t show bus tree
-v be verbose -vv for very verbose
-k show kernel drivers handlling each device
-x show hex dump of the standard part of the config space
-xxx show hex dump of the whole config space danger root only
-xxxx show hex dump of the 4096 byte extended config space root only
-b bus centric view addresses and irq's as seen by the bus
-D always show domain numbers
-n show numeric id's
-nn show both textual and numeric id's names and numbers
-q query the pci id database for unknown id's via dns
-qq as above bur re-query locally cached entries
-Q query the pci id database for all id's via dns

---

### Post by ronaldalanbarberjr on 2011-10-08
i dont have a flash drive how about a cd?

---

### Post by wildmanne39 on 2011-10-08
Hi, I do not know if you can use a cd or not you can try it, but I suspect it will not work before you install restricted drivers.

When you are able to post the code please copy and paste so the code will be correct.
Thank you

---

