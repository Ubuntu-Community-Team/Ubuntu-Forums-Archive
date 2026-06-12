---
title: "Networking with other Ubuntu boxes and Windows boxes, too."
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by BLTicklemonster on 2011-03-17
Okay, so I've been banging my head against this stuff for what, almost 6 years now, and I can say that I have finally gotten it down pat. So I guess Canonical can go change it now... but in the meantime, if you want to share files simply with other computers around the house, even Windows 7 computers, here's what I do.

Step the number uno: right click on a folder to share it. In the dialogue that opens, you will see three places where you can check. Start at the top and work your way down. You'll be prompted to install some files, do this. Once that's done, samba out to restart itself, or you will be logged out and have to log back in. Go back in and redo everything you just started if you were logged out. (I've seen it do both) Check all the boxes, agree to anything it asks to do permission-wise, and you've shared a folder. 

Sort of.

Now you need to open the terminal and type 

```
sudo gedit /etc/samba/smb.conf
```

and enter your password.

Scroll down to line 42, or the area that looks like this:
```

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = [COLOR="Red"]MSHOME[/COLOR]
   netbios name = [COLOR="Red"]Server[/COLOR]
```

Notice the red lettering. Windows will want to be on MSHOME, so just go with the flow, right? And netbios name can be anything you want it to be. 

Save, close, reboot, and do this to the rest of the Ubuntu boxes (naming each a different netbios name, of course), and voila.

(arguably the worst how to ever, but what the heck, I'm proud of myself for finally getting it down pat)
:P

---

