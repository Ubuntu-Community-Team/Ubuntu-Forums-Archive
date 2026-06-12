---
title: "flash:  Works in Chrome, not in Firefox"
date: 2010-05-07
forum: Multimedia Software
---

### Post by shortmort37 on 2010-05-07
I recently upgraded to 10.04 LTS.  Flash no longer works in Firefox, although it does in Chrome.  I've tried the sudo apt-get approach:

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/)

I've tried the libflashplayer.so in plugin directory approach:

[http://www.youtube.com/watch?v=hwc_0cRnczs](http://www.youtube.com/watch?v=hwc_0cRnczs)

I've tried disabling/enabling the plugins from the Tools menu (it indicates there are two versions -- 10.1 r53 and 10.0 r32 (I've disabled r32); they remain in the Tools menu regardless of whether the .so is in the plugin directory, or whether I've done an apt-get remove or not, so I don't know what that's all about.

There appear to be 47 different approaches to fixing this problem, but all the ones I've tried fail to work.  Rather than guess, is there a way to diagnose the problem?

One other interesting bit of information:  When you choose manage content plug-ins from the Tools menu, most of the MIME types indicate an icon to the left of the plugin -- except for Shockwave Flash.  Seems implicated to me, but I don't know how.

Dan

---

### Post by flyingmonkey35 on 2010-05-07
get it straight from the source

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

im running flash 10, with no issues.

---

### Post by shortmort37 on 2010-05-07
Oh yeah, I did that too (I can't tell you how many of the 47 things I've seen, that I've tried).  I chose the APT for Ubuntu 9.04+ install.  Didn't work.  Which did you try?

...which gets back to one of my questions:  Is there a way to Dx the problem, instead of recursing on N+1 install procedures in the hope that eventually one of them will actually work?

Dan

---

### Post by WinterRain on 2010-05-07
Sounds like a problem with firefox. I would completely remove firefox, and if you don't mind losing your bookmarks and settings, remove your .mozilla file too.

Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then reinstall firefox and flash. Are you using 64bit ubuntu?

---

### Post by shortmort37 on 2010-05-07
> **WinterRain said:**
> Sounds like a problem with firefox. I would completely remove firefox, and if you don't mind losing your bookmarks and settings, remove your .mozilla file too.

You mean, .mozilla folder, right?  Or is there a .mozilla file somewhere else?

What's the best way to remove filezilla -- uncheck it in Synaptic App Mgr?

> **WinterRain said:**
> Are you using 64bit ubuntu?

No.

Thanks
Dan

---

### Post by lovinglinux on 2010-05-07
> **shortmort37 said:**
> You mean, .mozilla folder, right?  Or is there a .mozilla file somewhere else?

What's the best way to remove filezilla -- uncheck it in Synaptic App Mgr?

No.

Thanks
Dan

Don't do that yet. First, remove all flash versions and install the default one following the instructions from my tutorial (also delete flash plugin from ~/.mozilla/plugins if you have one).

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

If that doesn't help, then delete the file **pluginreg.dat** from your profile at ~/.mozilla/firefox/<profilename>

Don't forget to close Firefox before poking around with profile files and to restart Firefox to see flash changes.

---

### Post by shortmort37 on 2010-05-07
> **lovinglinux said:**
> Don't do that yet. First, remove all flash versions and install the default one following the instructions from my tutorial (also delete flash plugin from ~/.mozilla/plugins if you have one).

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). 

OK - did that, it didn't fix it.

> **lovinglinux said:**
> If that doesn't help, then delete the file **pluginreg.dat** from your profile at ~/.mozilla/firefox/<profilename>

Don't forget to close Firefox before poking around with profile files and to restart Firefox to see flash changes.

Yeah; that didn't fix it either.  Threw in a reboot for good measure.

Aren't the reports from manage content and add-ons (attached) curious?

Also, when I click on a YouTube vid, I get "Transferring data from i1.ytimg.com..." in the marquee -- and it hangs there.

Dan

---

### Post by lovinglinux on 2010-05-07
> **shortmort37 said:**
> OK - did that, it didn't fix it.

Yeah; that didn't fix it either.  Threw in a reboot for good measure.

Aren't the reports from manage content and add-ons (attached) curious?

Also, when I click on a YouTube vid, I get "Transferring data from i1.ytimg.com..." in the marquee -- and it hangs there.

Dan

Please post the output of the command below:

```
locate libflashplayer.so
```

---

### Post by shortmort37 on 2010-05-07
dan@ubuntu:~$ locate libflashplayer.so
/home/dan/.mozilla/plugins/libflashplayer.so
/usr/lib/chromium-browser/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

---

### Post by timjthomas on 2010-05-07
Same issue -- just did a clean upgrade to 10.04 and no flash.  Firefox says it's installed.  No idea how to install it in Chrome.

Not sure how it can work in a previous version and not in 10.04.

I'm running 64-bit.

---

### Post by lovinglinux on 2010-05-07
> **shortmort37 said:**
> /home/dan/.mozilla/plugins/libflashplayer.so

I told you to delete that one, but you didn't. Close Firefox, then run these commands:

```
rm /home/dan/.mozilla/plugins/libflashplayer.so
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

Restart Firefox.

If that doesn't work, then check your network. Disable [ipv6](http://lovinglinux.megabyet.net/?page_id=220#Web-sites-keeps-loading-but-never-show-up-2) and [Firefox “Block reported attack sites” and “Block reported web forgeries”](http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-(grey)-frequently-2). Also make sure that Adblock plus or any other add blocking extension is not blocking the flash content.

---

### Post by lovinglinux on 2010-05-07
> **timjthomas said:**
> I'm running 64-bit.

See the 64bit section of the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by shortmort37 on 2010-05-07
> **lovinglinux said:**
> I told you to delete that one, but you didn't. 

I ***did*** do what you said.  I ***did*** delete it:

[B][I]dan@ubuntu:~$ rm /home/dan/.mozilla/plugins/libflashplayer.so
rm: cannot remove `/home/dan/.mozilla/plugins/libflashplayer.so': No such file or directory[/I][/B]

Yet, locate still reports it:

[B][I]dan@ubuntu:~/.mozilla/plugins$ locate libflashplayer.so
***[COLOR="Red"]/home/dan/.mozilla/plugins/libflashplayer.so[/COLOR]***
/usr/lib/chromium-browser/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so[/I][/B]

Perhaps that's the problem?

I'll wait for you to comment on this twist, before I execute your subsequent instructions.

Dan

---

### Post by RJARRRPCGP on 2010-05-07
> **shortmort37 said:**
> 

Also, when I click on a YouTube vid, I get "Transferring data from i1.ytimg.com..." in the marquee -- and it hangs there.



The first thing I would do is check your internet connection. You may have a cabling problem.

---

### Post by shortmort37 on 2010-05-07
> **RJARRRPCGP said:**
> The first thing I would do is check your internet connection. You may have a cabling problem.

Huh?  Check the title of this thread.  Flash works with the Chromium browser.  It's not a cabling problem.  It's an issue with Firefox.

---

### Post by lovinglinux on 2010-05-07
> **shortmort37 said:**
> I ***did*** do what you said.  I ***did*** delete it:

[B][I]dan@ubuntu:~$ rm /home/dan/.mozilla/plugins/libflashplayer.so
rm: cannot remove `/home/dan/.mozilla/plugins/libflashplayer.so': No such file or directory[/I][/B]

Yet, locate still reports it:

[B][I]dan@ubuntu:~/.mozilla/plugins$ locate libflashplayer.so
***[COLOR="Red"]/home/dan/.mozilla/plugins/libflashplayer.so[/COLOR]***
/usr/lib/chromium-browser/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so[/I][/B]

Perhaps that's the problem?

I'll wait for you to comment on this twist, before I execute your subsequent instructions.

Dan

Weird. Try [this tool](http://ubuntuforums.org/showthread.php?t=1414595) to remove flash and then install again. It is important to use the Remove button first.

---

### Post by shortmort37 on 2010-05-07
> **lovinglinux said:**
> Weird. Try [this tool](http://ubuntuforums.org/showthread.php?t=1414595) to remove flash and then install again. It is important to use the Remove button first.

Um... OK.  But [noob alert] how do I execute it?  I noted:

[QUOTE=carlee] your supposed to double click on it. [/QUOTE]

But when I do that, I get

[B][I]Could not display "/home/dan/Downloads/adobe_flash_installer-ubuntu".

There is no application installed for executable files[/I][/B]

Dan

---

### Post by lovinglinux on 2010-05-07
> **shortmort37 said:**
> Um... OK.  But [noob alert] how do I execute it?  I noted:

But when I do that, I get

[B][I]Could not display "/home/dan/Downloads/adobe_flash_installer-ubuntu".

There is no application installed for executable files[/I][/B]

Dan

Extract the file somewhere, then right-click on the extracted file, select Properties, go to the permissions tab, then tick the option to allow to run as program/application/executable. Click OK, then double click the file.

---

### Post by shortmort37 on 2010-05-07
> **lovinglinux said:**
> Weird. Try [this tool](http://ubuntuforums.org/showthread.php?t=1414595) to remove flash and then install again. It is important to use the Remove button first.

OK, I ran the tool and removed Flash.  I then used to tool to install Flash; it didn't work.

I reran the tool to remove Flash, and then did

sudo apt-get install flashplugin-nonfree

It didn't work.

I've removed Flash using the tool; here's the output of locate:

[B][I]dan@ubuntu:~$ locate libflashplayer.so
[COLOR="Red"]/home/dan/.mozilla/plugins/libflashplayer.so[/COLOR]
/usr/lib/chromium-browser/plugins/libflashplayer.so[/I][/B]

locate still thinks it's installed in the .mozilla folder.

Dan

---

### Post by lovinglinux on 2010-05-07
> **shortmort37 said:**
> OK, I ran the tool and removed Flash.  I then used to tool to install Flash; it didn't work.

I reran the tool to remove Flash, and then did

sudo apt-get install flashplugin-nonfree

It didn't work.

I've removed Flash using the tool; here's the output of locate:

[B][I]dan@ubuntu:~$ locate libflashplayer.so
[COLOR="Red"]/home/dan/.mozilla/plugins/libflashplayer.so[/COLOR]
/usr/lib/chromium-browser/plugins/libflashplayer.so[/I][/B]

locate still thinks it's installed in the .mozilla folder.

Dan

Type **about[noparse]:[/noparse]plugins** in the address bar and check what version of Shockwave Flash you have installed. Paste it here.

Also open /home/dan/.mozilla/plugins/ and check if libflashplayer.so is really not there. If it is, delete it. Restart Firefox.

---

### Post by shortmort37 on 2010-05-07
> **lovinglinux said:**
> Type **about[noparse]:[/noparse]plugins** in the address bar and check what version of Shockwave Flash you have installed. Paste it here.

Also open /home/dan/.mozilla/plugins/ and check if libflashplayer.so is really not there. If it is, delete it. Restart Firefox.

Nothing to delete - it wasn't there.

Screenshot attached.

Dan

---

### Post by lovinglinux on 2010-05-07
> **shortmort37 said:**
> Nothing to delete - it wasn't there.

Screenshot attached.

Dan

It seems you have installed a Windows version of Flash. Are you using a Windows version of Firefox and Chrome too? 

That's not how things should be done in Linux. Wine offers the possibility of installing Windows applications, that might work or not, but is not intended to replace all applications. It should be used only when you don't have an alternative native application.

How many applications you have installed using Wine? I'm asking this because I'm about to suggest deleting the folder ~/.wine, which would delete all applications installed by it.

---

### Post by shortmort37 on 2010-05-07
> **lovinglinux said:**
> It seems you have installed a Windows version of Flash. Are you using a Windows version of Firefox and Chrome too? 

That's not how things should be done in Linux. Wine offers the possibility of installing Windows applications, that might work or not, but is not intended to replace all applications. It should be used only when you don't have an alternative native application.

How many applications you have installed using Wine? I'm asking this because I'm about to suggest deleting the folder ~/.wine, which would delete all applications installed by it.

No, I'm not using a Windows version of Firefox and Chrome.  And yes, I do have Crossover installed.  But I don't recall ever installing Flash for Windows; I've only installed Office, Dreamweaver, and a few other M$ apps I find useful.

Flash was working fine under 9.10, with both Chrome and Firefox.  I upgraded; it busted.  If the suggestion is to delete wine to fix Firefox -- because there's simply no other way to fix it -- I'll just use Chrome and forget Firefox, thanks very much.

Dan

---

### Post by lovinglinux on 2010-05-07
> **shortmort37 said:**
> No, I'm not using a Windows version of Firefox and Chrome.  And yes, I do have Crossover installed.  But I don't recall ever installing Flash for Windows; I've only installed Office, Dreamweaver, and a few other M$ apps I find useful.

Flash was working fine under 9.10, with both Chrome and Firefox.  I upgraded; it busted.  If the suggestion is to delete wine to fix Firefox -- because there's simply no other way to fix it -- I'll just use Chrome and forget Firefox, thanks very much.

Dan

Try to remove it through Wine. I'm not sure why it is showing up in your native Firefox, but that is certainly the problem.

---

### Post by shortmort37 on 2010-05-07
> **lovinglinux said:**
> Try to remove it through Wine. I'm not sure why it is showing up in your native Firefox, but that is certainly the problem.

YES!  I didn't have an option to remove it, but it was enabled in a Win2000 bottle.  I disabled it, did

sudo apt-get install flashplugin-nonfree

again (having last deinstalled it), and ***it works!***

Not sure why Crossover got in the way as a result of the upgrade -- or, when that plugin got installed -- but that was the trick.  Thank you.

Dan

---

### Post by lovinglinux on 2010-05-07
> **shortmort37 said:**
> YES!  I didn't have an option to remove it, but it was enabled in a Win2000 bottle.  I disabled it, did

sudo apt-get install flashplugin-nonfree

again (having last deinstalled it), and ***it works!***

Not sure why Crossover got in the way as a result of the upgrade -- or, when that plugin got installed -- but that was the trick.  Thank you.

Dan

You are welcome.

This one was hard to troubleshoot, but at least I know I should ask for a about[noparse]:[/noparse]plugins screenshot more frequently :)

---

### Post by shortmort37 on 2010-07-26
OK - not sure if this is related to Crossover, or not.  But, I can't get .wmv files to play in Firefox, either -- although, when launched from my desktop, they *do* play.  What I get in Firefox with an embedded .wmv is "Xine" in the display, with "Buffering... 0%" in the upper left corner.

I checked all of my Crossover bottles, I don't see anything related to Windows Media being enabled.  How can I Dx what is going wrong?

adTHANKSvance,
Dan

---

