---
title: "How do I remove flash 9 and keep flash 10"
date: 2008-11-26
forum: Multimedia Software
---

### Post by beercz on 2008-11-26
I have a real annoyance with flash.

I have flash 9 and 10 installed and want to use flash 10 (10 offers full screen, 9 doesn't).

I have tried removing and reinstalling flash, using adobe's flash 10 deb (and ubuntu wishes to update it using the version in the repositories).

When I go to the [BBC news website]("http://news.bbc.co.uk") for example and watch the live news stream, I an unable to go to full screen.  When I right-click on the video I get 'About flash player 9'.

I attempted to disable the flash 9 plug in (from Firefox's Tools->Addons), but flash would not play at all.

Any ideas as to how I completely remove flash 9 and keep flash 10?

Thanks in advance.

---

### Post by gandaran on 2008-11-26
well how did you install it? from the repositories? if so then just open synaptic package manager, scroll down to flashplugin-nonfree mark for complete removal and click the apply button
or if you installed it by another way post here the output of **locate libflash**

---

### Post by binbash on 2008-11-26
check about:config at firefox and see what version of flash player is firefox using.then locate libflash and remove it.Then install flash player 10

---

### Post by beercz on 2008-11-26
Thanks for the replies.

I installed flash by downloading adobe's deb file and then updated it using the update manager.

The output of locate libflash is:

> ian@wayne:~$ locate libflash
/home/ian/.mozilla/plugins/libflashplayer.so
/home/ian/.mozilla.ubuntu/plugins/libflashplayer.so
/home/ian/.mozilla_backup_2008-11-08T23:44:03+0000/plugins/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
Do I remove all of them?

When I did about:config in firefox, I found no references to the flash player - I tried to filter on flash, player, adobe, macromedia and shockwave, all to no avail.

Yet according to Tools->Add-ons, I have both versions installed, see the following screenshot.

Where do I go from here?

---

### Post by gandaran on 2008-11-26
> /home/ian/.mozilla/plugins/libflashplayer.so
/home/ian/.mozilla.ubuntu/plugins/libflashplayer.so
/home/ian/.mozilla_backup_2008-11-08T23:44:03+0000/plugins/libflashplayer.so
just delete the libflashplayer.so file on these three directories
this flash was installed with the adobe .tar.gz package

the adobe .deb package is adobe_flashplugin, it's installed in /usr/lib/adobe-flashplugin/libflashplayer.so, this is flash 10, don't remove it

it's not about:config but about:plugins

---

### Post by beercz on 2008-11-27
> **gandaran said:**
> just delete the libflashplayer.so file on these three directories
this flash was installed with the adobe .tar.gz package

the adobe .deb package is adobe_flashplugin, it's installed in /usr/lib/adobe-flashplugin/libflashplayer.so, this is flash 10, don't remove it

it's not about:config but about:plugins
Thanks gandaran

All sorted.

I'm a happy bunny now :-)

---

