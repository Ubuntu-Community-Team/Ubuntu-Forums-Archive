---
title: "No prompts or labels displayed for audacity"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by aloshbennett on 2007-04-24
I can see the icons, but no text. The problem is there with xmms too.

Help!! :-(

ps: I've attached the screenshot.

---

### Post by sayash on 2007-05-08
Please tell me if you managed to solve the problem. On my fresh installation of feisty kubuntu, i used apt-get to install audacity. But when I run it, there's no text. Text does appear in some places like the shortcut keys and status bar. This problem was present with XMMS too. So must be a gtk1 problem. I googled and searched for other threads. Their suggestion of modifying the .gtkrc(-1.2gnome2, etc) had no effect. One more launchpad report recommended changing Xorg font paths. They were all properly set up.
I'm getting quite frustrated now. Help if you found a solution.

sayash

---

### Post by tgalati4 on 2007-05-08
Upon first use of Audacity, it asks you for your native language.  Perhaps there's a setting in .audacityrc that got screwed up.  Also check your language setting in Gnome Control Panel.

---

### Post by aloshbennett on 2007-05-22
I'd my LANG set to en_IN. I changed the locale to use en_US 

( edited /var/lib/locales/supported.d/local
and ran sudo dpkg-reconfigure locale)

and the prompts are back!
 :-)

---

### Post by tgalati4 on 2007-05-22
Thanks for sharing.  We knew you could fix it.

---

### Post by pimpaulogy on 2007-06-07
Unfortunately, after trying what is suggested above, I still have the issue.  The only difference is that instead of not have any labels, all of the characters are "squares".

Any suggestions?

---

### Post by pimpaulogy on 2007-06-07
Figured this out.  My permissions on my home directory were all jacked up.  Fixed those and deleted the .dmrc file and we are all good.  I didn't realize the error until I actually sat in front of the machine and logged in.  When I was getting the error, I was using NX to log in remotely so I wasn't getting the permissions error.

---

### Post by ddrake on 2007-06-25
Hi there,

 I recently moved from kubuntu 6.10 to 7.04.  I have used audacity in 6.10 but I have the same
problem - no menu fonts or labels visible (though the shortcuts are visible). 

I reinstalled audacity - but the problem would not go.
I tried deleting the ~/.audacity file contents - The language parameter was set to 'en'.... I tried
changing it to 'en_US'   - this did not help.

I tried editing the file: /var/lib/locales/supported.d/local  - I removed the first line.  it was:
%more local
en_IN UTF-8
en_US.UTF-8 UTF-8
%

 I deleted the first line and tried running: sudo dpkg-reconfigure locales
but that did not help  -   

I used adept manager to reinstall 'locales' as well as 'localization-config'.
This was successful.

And yet.............
............... there is .no change in my audacity label/font/menu commands display. The
problem remains! No display!

Has this problem been solved? Look forward to a clean solution....
[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

thanks
ddrake

---

### Post by Bhavanishankar on 2007-07-04
I had the same problem. So, I just checked my $LANG variable. It was en_IN.

So, I changed to en_US.UTF-8 by 'export LANG=en_US.UTF-8' in my bash prompt. After this the labels and prompts started appearing in all the applications which earlier had problems.

I think the LANG setting can be made permanent by editing /etc/environment.

HTH,
Bhavanishankar

---

### Post by gOLdenHaWK3D on 2007-09-04
I faced the same problem, and fixed it by using your suggestions guys. 
I just changes the LANG from en_IN to en_US in the file /etc/environment
Just had to restart the X Server after doing this.

Thanx guys :) Audacity now runs perfectly fine.

---

