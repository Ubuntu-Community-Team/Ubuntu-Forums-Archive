---
title: "Samba for new users"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by andyfraser on 2006-07-12
Background: I've received my Ubuntu CDs and now plan to set up a system for my Dad and possibly my brother-in-law. My Dad has finally had enough of Windows, has played with Mandrake 10 a bit and is currently thinking of buying a Mac. Linux would save him some money but he's convinced it will be too much hassle hence the thoughts of a Mac.

One thing they will want to do is set up Samba shares. I'm an experienced Linux user and normally use the command line to do this but for them a GUI would be preferable so that's what I've been researching. I'm not that familiar with using Gnome for sys admin tasks.

I can get as far as setting up a share with System -> Administration -> Shared Folders. This prompted to install Samba. Fair enough, this is a fresh install and Samba wasn't installed. I had to restart Samba from the Services applet before the share would appear on my Mac. Not too troubling.

When I tried to connect to the share I had problems which from experience I knew meant that I needed to add my user with smbpasswd. After I'd done this I could connect exactly as I expect.

My question is this: is there a way to do the whole thing from the GUI? My Dad might not have problems with the command line but he'll moan about it. My brother-in-law will be totally lost. I'll probably do this myself but there's a chance that I'll forget or we'll run out of time and they might have to do it after I've gone home.

I've Googled and searched these forums and can't find an answer so any help would be much appreciated.

---

### Post by closeyourwindows on 2006-07-12
as far as I know there is a work in progress on this, however you can install jags.  'sudo apt-get install jags' will install a gui for a workgroup and edit the samba.conf file automatically.  its pretty easy to use, just make sure you have a samba user and password setup.

---

### Post by andyfraser on 2006-07-13
Thanks for that info. Unfortunately it's the Samba username and password bit I need either automated or a GUI for.

Today I remembered that Webmin had something that could work and sure enough there are two useful options: "Convert Unix users to Samba users" and "Configure automatic Unix and Samba user synchronisation". I'm going to try and work out the second can be set up as default for these systems. The first might be a good alternative that both my Dad and brother-in-law can handle, especially if I set up a link to launch Webmin from the desktop or something like that.

---

