---
title: "Flash plugin issue in 7.10"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by anantgowerdhan on 2007-12-23
Hi,

I've installed Ubuntu 7.10 at the day of its release and that ISO worked fine. To enable Flash Video in browser I installed ubuntu-restricted-extras (as guided) and it worked fine. After couple of days I had some issues in my partition and I re-installed Ubuntu but the ISO what I used this time is the latest available on site (just a week back I downloaded new ISO).

 Now after installing ubuntu-restricted-extra I opened Firefox and started Youtube but I was amazed to see that it is saying that "required plug in is missing" when I go further it ask me to install "Flash plug in for firefox or Gnash SWF" and if I use Flash Plug in it says its already installed..............

Please help me to get this fixed.

Regards,
Anant

---

### Post by Metaljaz on 2007-12-23
This guide maybe helpful. it worked for me even though it was under feisty:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

or

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by phatty420 on 2007-12-23
I was having the same issue, and tried both of those guides and neither one of them mention anything about this bug or how to fix it.  However I did figure out a way:

In Firefox, go to 'tools > add-ons' .  You will see 'ubufox beta', disable it.  then goto synaptic and uninstall gnash-mozilla-plugin (that is if you installed it earlier). then restart Firefox, go to a page that needs flash and install the plugin, and it will just start working, no need to restart Firefox.

I hope this helps you as it just (not 5 minutes ago) solved the same problem for me

---

### Post by Richardinho on 2007-12-24
I couldn't install Flash in the usual way. A bit of research later it transpired that there is some kind of bug.

I went to the Flash site, downloaded the Linux version and followed their instruction; result-Youtube heaven last few days!

Strikes me that having a bug that stops you playing Flash videos is just about as serious as it could be in terms of the casual internet user  and something the developers should be working day and night to solve!

But there you go..

---

### Post by jacob733 on 2007-12-24
It seems that the third-party download taking place during installation of flashplugin-nonfree is broken. It complains about md5sum mismatch in the file. It would suggest that the file on the macromedia site has been updated, but flashplugin-nonfree is still the old version.

I agree that this is a critical bug that has existed for a few days. I was hoping that it was solved by now, but no luck.

---

### Post by captaink on 2007-12-24
Hello all,

There has been a chat for this bug on launchpad:

[https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890)

On that page there is an updated package that has not come to get into repos yet. I don't know if it still works.

Anyway, I prefered to install a 32-bit version of firefox, 32-bit Java plugin will work there too. Refer to: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

Until adobe makes a 64-bit version available and Sun a plugin for 64-bit browsers, this is the best solution!

---

