---
title: "Having problems with screen resolution."
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by dormot on 2007-01-08
I just installed and my resolution is really low. I have a 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) 
I found a faq on how to fix my problem but the guy's monitor is different and I am not sure what values to enter for the monitor. Here is the web page [https://launchpad.net/ubuntu/+ticket/2751](https://launchpad.net/ubuntu/+ticket/2751) (the information Im using is the last post on the bottom). My monitor is a "15 inch triniton multiscan 100es" Can someone give me a push in the right direction? 
I am new at this so please explain in simple terms. Thanks

---

### Post by spin2cool on 2007-01-08
One thing to try is to reconfigure the x-server.  

Hit Ctrl-Alt-F1, then type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
(Always good to have a backup, so that you can at least get a working display again if things go awry)

Then do:
```
sudo dpkg-reconfigure xserver-xorg
```

Follow the prompts and be sure to check off the boxes containing some of the higher resolutions.  If all goes well, you can reboot and have mroe resolution options.

If doing the reconfig doesn't help you, you'll have to edit your xorg.conf manually.  Poke around the forums and look at some of the xorg.conf files other people have posted (this problem isn't uncommon).  I can almost guarantee the answer is on these boards somewhere.

---

