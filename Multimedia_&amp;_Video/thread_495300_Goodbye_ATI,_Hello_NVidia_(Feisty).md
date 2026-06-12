---
title: "Goodbye ATI, Hello NVidia (Feisty)"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by fido777 on 2007-07-07
I've had enough ATI/Linux issues, and just ordered a Geforce 8600 GT (got one without a fan!).  What is the **most painless** way to switch them out?  My current plan is to switch cards, boot to a root shell and run "dpkg-reconfigure xserver-xorg", then reboot.  That should get me the xorg nv drivers.  Next, I have to switch to the nvidia drivers.  

I've seen links to scripts and long pages of commands.  Will I have to do that since my card is new?  Or will the "restricted driver" thing somehow work?  So far I have un-installed the ATI fglrx driver and I'm using the non-proprietary ati xorg driver.  I'm running amd64.

---

### Post by southernman on 2007-07-07
I don't think you'll need to do anything spectacular. When the new card arrives, shut down your system and swap out the cards. When you power on your system again, at the grub page simply choose the repair/recovery kernel... once your dumped into the console just run:

```
dpkg-reconfigure xserver-xorg
```

The system will make a backup of your xorg.conf file for you (with a date/time code appended) and write the new file.

That should at get your xserver working so you can login and then choose to use (or not) the restricted driver (if any are available) from the gui.

Maybe because my best vcard is an older model (read: ATI 8500 AIW) I have had no issues with it. Don't use a RD for it, either. It just works, period.

Anyhow... good luck with the new card. I understand sometime enough is just plain 'ole enough.

*edited - I just now saw your using two monitors. Can't help with that portion, but someone who knows will be along at some point.

---

### Post by Anonii on 2007-07-07
> **fido777 said:**
> I've had enough ATI/Linux issues, and just ordered a Geforce 8600 GT (got one without a fan!).  What is the **most painless** way to switch them out?  

[LIST]
[*]What do I do before the switch?  Specifically, xorg.conf and driver installs.
[*]What do I do after the switch?
[/LIST]

I'm running amd64 with two monitors, and want a single big desktop.  I've seen links to scripts and long pages of commands.  Will I have to do that since my card is new?  Or will the "restricted driver" thing somehow work?  So far I have un-installed the ATI fglrx driver and I'm using the non-proprietary ati xorg driver.
Good choice sir. Good choice. I'll switch from ATI to Nvidia in the Christmas. 
Unfortunately I can't help you with these two monitors of yours, but I just wanted to congratulate you.

---

### Post by reset3x on 2007-07-07
> **fido777 said:**
> I've had enough ATI/Linux issues, and just ordered a Geforce 8600 GT (got one without a fan!).  What is the **most painless** way to switch them out?  My current plan is to switch cards, boot to a root shell and run "dpkg-reconfigure xserver-xorg", then reboot.  That should get me the xorg nv drivers.  Next, I have to switch to the nvidia drivers.  

I've seen links to scripts and long pages of commands.  Will I have to do that since my card is new?  Or will the "restricted driver" thing somehow work?  So far I have un-installed the ATI fglrx driver and I'm using the non-proprietary ati xorg driver.  I'm running amd64.

You're going to need the newer nVidia drivers for the 8000 series cards..... The drivers that come with Ubuntu won't work... I suggest you install Envy prior to installing your new card.... After you have the card installed boot up and X will probably fail to start.... 

```
sudo envy -t
```

Will let you start envy in text mode... You can then install the newest drivers.. Envy will also configure xorg for you....

---

