---
title: "Google Music-Manager issue after 12.10 upgrade"
date: 2012-11-23
forum: Multimedia Software
---

### Post by mulkwolf on 2012-11-23
I'm having no luck seeing if anyone else has had this issue. Google Music-Manager seems to install fine. When started does not show up in the notification area at the top. Does not ask for google connection login. System monitor seems to indicate it is running. After starting firefox will not load saying it is already running. My current work around is to leave one of my computers with 12.04, Music Manager works fine there.

---

### Post by sirgeekalot on 2012-11-25
same here.. the first install i got asked me a few questions, but after that.. it doesnt seem like the package does anything..

---

### Post by KL84 on 2012-11-25
Having a similar issue. It installed fine, and I do get it in the notification bar. However, I can't access options and therefore can't specify where to send downloads. There is no upload option in the drop down menu. In fact almost the entire feature set that is supposed to be available according to google's support page, is missing. (Options doesn't work, no upload tab, no advanced tab, etc)

---

### Post by notthenewsreader on 2012-11-27
Exactly the same problem in Linux Mint 14 (based on Ubuntu 12.10)

---

### Post by sirgeekalot on 2012-11-28
is there a bugtracker somewhere where we can report this straight to google? i have contacted the support team via the support pages but i doubt it'll get noticed.

---

### Post by mulkwolf on 2012-11-29
Well at least it looks as if I'm not alone. I suspect something will need to be done at the Google end of things. I'd be interested to hear if it is working for anyone on 12.10.

---

### Post by Steeperton on 2012-11-29
*puts hand up*

Ubuntu 12.10 64bit. Works fine (clean install) - uploaded over 12000 songs, and still going strong

---

### Post by mulkwolf on 2012-11-29
Clean install. This at least is encouraging. So perhaps it is a conflict somewhere. May try that.

---

### Post by notthenewsreader on 2012-11-30
Has anyone had any luck with this? I have tried a fresh install and still have the same problem; once you have chosen your options, the icon appears in the status bar and you can't open the options page again. Anyone know if there is somewhere to submit this as a bug?

---

### Post by Steeperton on 2012-11-30
What version of Google music are you using? I'm on 1.0.51.1573-r0 from their PPA. If you need to update:

add:
```

deb http://dl.google.com/linux/musicmanager/deb/ stable main

```
to your sources.list

then the key: 
```

wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -

```

---

### Post by notthenewsreader on 2012-11-30
I'm using the same one and Linux Mint 14

---

### Post by sirgeekalot on 2012-11-30
same here.

what window managers and architectures are others using? 

i'm on Unity and 32-bit.. i'll try insalling another WM when i'm at home and see if that changes anything but i the only main difference i can see is that the only person with it running in this thread is running 64-bit..

---

### Post by notthenewsreader on 2012-11-30
I'm on 64 bit Mint 14 with Cinnamon, I'll try the MATE version now

---

### Post by notthenewsreader on 2012-11-30
Right, same problem but I think I have a fix - uninstall the music manager. Go into ~/.config and delete the google-music-manager directory then install the package all over again, when the first run wizard begins, click upload and choose an empty directory, go through all the error messages (less than 10 files found, etc) and then once that it done and the icon is in the tray, clicking on it should work. Let me know if this works for you. Regards

---

### Post by mulkwolf on 2012-12-02
Did delete the config file after uninstall. Seemed to act as a new install but got stuck on the login screen. Other issues for me are access to internet is blocked, no firefox or chrome after attempt to run. this occurs even after force quitting music manager.  When loading music manager using the software center it tells me that it is a bad file. This is the same after trying several different downloads from google. Haven't done clean install yet. is previous clean install still working?

:(
Never go back....

---

### Post by sirgeekalot on 2012-12-10
> **notthenewsreader said:**
> Right, same problem but I think I have a fix - uninstall the music manager. Go into ~/.config and delete the google-music-manager directory then install the package all over again, when the first run wizard begins, click upload and choose an empty directory, go through all the error messages (less than 10 files found, etc) and then once that it done and the icon is in the tray, clicking on it should work. Let me know if this works for you. Regards

i have just tried this method and con confirm that, For me, it worked and i can now upload to google music again.. 

i removed with Purge, removed the files from .config folder and reinstalled.

Thanks for the help matey..

---

### Post by kb2001 on 2012-12-12
> **notthenewsreader said:**
> Right, same problem but I think I have a fix - uninstall the music manager. Go into ~/.config and delete the google-music-manager directory then install the package all over again, when the first run wizard begins, click upload and choose an empty directory, go through all the error messages (less than 10 files found, etc) and then once that it done and the icon is in the tray, clicking on it should work. Let me know if this works for you. Regards


This worked for me as well on Mint 14 MATE.  Thanks for the steps to get this done.  I uninstalled through the Software Manager, oddly it didn't fully complete, it got stuck at 99% and then hung.  WHen I launched it again, music manager was still an option to install, but when I clicked it it hung the software manager again.  I reinstalled the package and it works fine now following your steps.

Thanks for posting this, much appreciated

---

### Post by Copper Bezel on 2012-12-19
The bug I experienced was having the "Upload" menu item missing and the "Options" item not doing anything. Reinstalling from the PPA changed nothing, but deleting the config folder worked, and the sync is running. However, it's presently uploading all of my files, instead of syncing directly (although it does not seem to be creating duplicates in the web player.)

Edit: And on the Android-end, it's re-syncing all the locally-stored tracks that are being overwritten. Google is reloading my entire library, twice, so I can move one song to my tablet. Removing the config folder works, but it's not ideal. = P

---

### Post by it_self on 2013-01-12
Very similar problem. Clean install of 12.10 (with Unity). I'm not uploading though, just downloading my library to the new computer. Checking network traffic and the size of my music folder seems to indicate that it is, in fact, working as needed, except I can't access options either (I click it and there is no response). Haven't tried install from PPA yet. Will try that as soon as the download finishes.

---

### Post by mdye on 2013-02-06
I'm having this issue as well and, all due respect to those who propose this workaround (which is better than nothing), deleting the config files really isn't a solution - certainly not a long-term one - since doing so only really starts the process over again.  I delete my config file and it will just let me start syncing over once - what I really want to do is download new songs I've recently purchased and I'd like to be able to open the app, go to settings, and ask it to download again when that happens - not delete the config file, log in and have it download the entire library (or even just my purchased music) when all I really want is to download one album.  Does anyone know what the problem is and what's causing music manager to not work?  I've encountered this in every DE there is - including Unity, GNOME and KDE.  It's discouraging.

---

### Post by mehlmann on 2013-02-15
> **notthenewsreader said:**
> Right, same problem but I think I have a fix - uninstall the music manager. Go into ~/.config and delete the google-music-manager directory then install the package all over again, when the first run wizard begins, click upload and choose an empty directory, go through all the error messages (less than 10 files found, etc) and then once that it done and the icon is in the tray, clicking on it should work. Let me know if this works for you. Regards

Works for me, too. Thanks!!

---

### Post by nogloww on 2013-02-25
> **sirgeekalot said:**
> i have just tried this method and con confirm that, For me, it worked and i can now upload to google music again.. 

i removed with Purge, removed the files from .config folder and reinstalled.

Thanks for the help matey..

Is there a walk through that will tell me how to "go into ~/.config and delete the files"? I'm still pretty new at terminal commands. I figured out how to use the purge command to remove it but I don't know what ~/.config is or how to get to it. Any help would be appreciated. Thanks.

---

### Post by mail929 on 2013-02-27
Just go to your Home folder and press ctrl + h to show hidden folder. .config is in there. Basically . before a folder name means its hidden.

---

### Post by Baldrick_NZ on 2013-04-17
> **notthenewsreader said:**
> Right, same problem but I think I have a fix - uninstall the music manager. Go into ~/.config and delete the google-music-manager directory then install the package all over again, when the first run wizard begins, click upload and choose an empty directory, go through all the error messages (less than 10 files found, etc) and then once that it done and the icon is in the tray, clicking on it should work. Let me know if this works for you. Regards


Awesome work dude!! Works well for 13.04/Gnome Shell 3.6, too!!

---

### Post by Baldrick_NZ on 2013-04-17
> **it_self said:**
> Very similar problem. Clean install of 12.10 (with Unity). I'm not uploading though, just downloading my library to the new computer. Checking network traffic and the size of my music folder seems to indicate that it is, in fact, working as needed, except I can't access options either (I click it and there is no response). Haven't tried install from PPA yet. Will try that as soon as the download finishes.

I was having the exact same prob as well in 13.04, but I followed the workaround supplied by notthenewsreader, and made an empty folder called 'gMusic' and pointed my uploads there. Followed the rest of the questions to the end. The icon settled into the tray, and viola! Right click over options actually worked this time!

So it would seem that even if you have no interest in uploading, you HAVE to set up these options on the first run in order to use the app again. 

BTW... your upload folder is the same as your download folder by default.

Cheers.

---

### Post by Baldrick_NZ on 2013-04-17
> **mdye said:**
> I'm having this issue as well and, all due respect to those who propose this workaround (which is better than nothing), deleting the config files really isn't a solution - certainly not a long-term one - since doing so only really starts the process over again.  I delete my config file and it will just let me start syncing over once - what I really want to do is download new songs I've recently purchased and I'd like to be able to open the app, go to settings, and ask it to download again when that happens - not delete the config file, log in and have it download the entire library (or even just my purchased music) when all I really want is to download one album.  Does anyone know what the problem is and what's causing music manager to not work?  I've encountered this in every DE there is - including Unity, GNOME and KDE.  It's discouraging.

Removing the .config is only a once-off to enable you to get into the first-time set up so you can get the app to behave itself from there on in.

The manager app simply isn't set up to download one song at a time, from what I can see, atm. However, you can do exactly that via the web store itself. I would think that future versions of this app will probably include a 'select a song' for download option.

---

### Post by mlpinto on 2013-05-01
Hi,

Just wanted to say thanks for the fix - worked perfectly for me on 64 bit 13.04

Cheers!

---

### Post by klutzini on 2013-12-24
I am using Xubuntu 13.10 and I deleted the folder in .config, then ran the program again and it all worked well.

---

