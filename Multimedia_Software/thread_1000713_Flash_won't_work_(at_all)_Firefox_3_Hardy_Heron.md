---
title: "Flash won't work (at all) Firefox 3 Hardy Heron"
date: 2008-12-03
forum: Multimedia Software
---

### Post by fwallace99 on 2008-12-03
Flash is not running at all.

I installed (clean new wipe HD install) Hardy Heron on my laptop that had run Feisty for over a year, no problem with Flash running on Firefox 2.

Now, with Firefox 3 I can't get Flash to work AT ALL. I've looked at the comprehensive thread Multimedia and Video, followed the instructions, no go.

I've purged gnash and the other free player, tried the flash-non-free plugin and the .deb from Adobe (Flash 10). I am running 32 bit Hardy Heron, this should be a no-brainer. Other than that I like Hardy a lot.

I really, really need Flash running. It's frustrating because I *should* have everything running. 

Has ANYONE got Flash to run at ALL on Firefox 3? I can't get Flash running either on Galeon or Opera, FWIW.

Any help at all appreciated.

---

### Post by el-mar01 on 2008-12-03
Have you tried to download the .tar.gz version of Flash 10 and moved the Flashplayer.so file into /home/<yourusername>/.mozilla/plugins ??

---

### Post by gandaran on 2008-12-03
> Has ANYONE got Flash to run at ALL on Firefox 3? I can't get Flash running either on Galeon or Opera, FWIW.
of course adobe flash works on firefox, just make sure you don't have any other flash (gnash and swfdec) installed but just one adobe package, the flashplugin-nonfree you can find in synaptic!
if it still doesn't work then try reinstall firefox and flash and reboot

---

### Post by fwallace99 on 2008-12-03
I'll try completely re-installing Firefox. Like I said, I feel frustrated and stupid, because I *HAD* Flash 10 working on Firefox 2, Galeon, and Opera in my Feisty Install.

It was not any big deal. I can't figure out why Hardy Heron has this problem (though overall I'd rate the release highly, the desktop effects are to die for).

I've completely un-installed the Gnash and other freeware swfdec player and the non-free player and re-installed, then removed all the flash plugins and used the Adobe official .deb package. I've also tried the .tar.gz package with the shell installer. No go.

I'm going to completely un-install Firefox, but I still don't see why that would affect either Galeon or Opera which as I mentioned was working fine under my former Feisty Fawn install.

---

### Post by gandaran on 2008-12-03
are you running ubuntu 32-bits or 64-bits?
post the output of **locate libflash**
do you have flashblock installed?

---

### Post by fwallace99 on 2008-12-03
Gandaran -- I am running 32 bit.

I "sort-of" fixed the problem. Here's what I did:

A. Searched Synaptic for Flash. Uninstalled: ubuntu-restricted-extras (version 15.2) which was the only "flash" related item installed.

B. Installed the official Adobe Flash 10 from the .deb package downloaded directly from adobe.com .

It works, in all browsers, including Galeon and Opera. 

I don't understand why the package was installed because I followed the terminal instructions in the multimedia howto to the letter. Weird. 

However, it's working. I guess I will have to deal with mp3s, aac's DVD, etc. later. The package description for ubuntu-restricted-extras mentions it has some Flash plugins that apparently broke or prevented the Flash plugin for Adobe from installing/working.

I would have replied sooner but the forums are wonky, I seem unable to get to much of the pages. Weird.

Also, for those with widescreen laptops like mine, the hint here:

[http://wiki.msiwind.net/index.php/Ubuntu_8.04_Tweaks#Enabling_and_Customizing_Compiz_Fusion](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Tweaks#Enabling_and_Customizing_Compiz_Fusion)

to adjust fonts to 83 pixels from the default 96 is a LOT better. That seems to have been done in default in Feisty, but not on Hardy. The difference is STRIKING.

Weird. I can play mp3s and aacs (m4as) so I guess it's all working.

Thanks. The suggestion to check Synaptic was GOLD.

---

