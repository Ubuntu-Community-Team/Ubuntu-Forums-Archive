---
title: "Chromium complains flash plug-in out of date"
date: 2011-03-11
forum: Multimedia Software
---

### Post by Oldhacker on 2011-03-11
Using Ubuntu 10.04 64 bit. After the most recent updates were installed, Chromium complains that my flash plug-ins are out of date when I attempt to run a video on YouTube. However, this does not appear to affect Firefox, which plays YouTube as usual.

My question is: Should I accept the flash plug-in offered from Chromium, and if I do will it affect Firefox?

---

### Post by rtimai on 2011-03-11
[http://www.pcworld.com/article/206107/the_17_most_dangerous_places_on_the_web.html](http://www.pcworld.com/article/206107/the_17_most_dangerous_places_on_the_web.html)

Check out the PC World magazine article above. I would not install a video codec from a media hosting site, as this is a common scam embedded in the media file itself to install malware in the guise of a required codec -- note that the contributor is the bad guy, not the host site. I think it's a good policy to only install codecs from repository or the developer site. BTW I'm running Chrome (the unbranded version of Google Chromium) and have not encountered a codec download prompt. So, I don't think your experience is common, and you may be attempting to view a maliciously planted video. Good luck with your viewing.

---

### Post by PoHandle on 2011-03-11
To solve this issue, you can do one of two things:
[LIST=1]
[*]**Update the Flash plugin**
Get the latest Flash plugin from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and copy *libflashplayer.so* to */usr/lib/chromium-browser/plugins/*, then restart Chromium. or
[*]**Disable the warning in Chromium**
Instead of updating the plugin, you can just disable the warning by adding *--allow-outdated-plugins* to the launcher command.  For example, my launcher command line looks like this:
```
/usr/bin/chromium-browser --disable-dev-tools --disable-logging  **[COLOR="DarkRed"]--allow-outdated-plugins[/COLOR]** %U
```
[/LIST]

To comment on rtimai's response:
The issue here has nothing to do with video codecs.  It is an issue with Chromium detecting an out-of-date Flash plugin, and suggesting that the user updates it.  There is no malware involved, and even if there was, it would most likely not affect the user, as most malware is designed to target Windows machines.
This issue surfaced for me after updating my machine less than an hour ago, just like the OP had claimed. Therefore, I think it's unfair to label the problem as uncommon just because it's relatively new.

About Chrome vs Chromium, *Chrome* is Google's *branded* version of the Chromium web browser, not the other way around.  If you are using Chrome, you are using the Google-**branded** browser.

---

### Post by beew on 2011-03-11
Just install the flash-aid plugin for firefox, it will remove conflicting flash versions in your system, get you update flash whenever it is avaliable and it also does some optimization for you.

---

### Post by hno3 on 2011-03-12
I was facing this issue from past few day, but I resolved it today!

This is how I identified the problem:
My chrome was using the flash plugin in the /usr/lib/mozilla/plugins/ directory. Its for firefox but don't know why chrome uses it. This plugin was dated back to 2010-01-27 (thats more than a year). Now, why only chorme is issuing the warning but not the firefox. I surfed and found this website ([http://news.cnet.com/8301-27080_3-20009231-245.html](http://news.cnet.com/8301-27080_3-20009231-245.html)). It reads that chrome will be warning users if they are using any old plugins.

Solution that worked for me:
I tried the solution mentioned by 'PoHandle' but didn't work for me. So I used the synaptic manager and searched the term "adobe" without quotes and found a flash plugin installer for ubuntu 10.04 by Adobe. Installed it and **ISSUE RESOLVED**. I am happy now.:D

---

### Post by dirty_harry on 2011-03-12
Does it look like this:
[IMG]http://2.bp.blogspot.com/-1KqNgxDkP5U/TXbhYsuPkoI/AAAAAAAAAEI/U9-jyQNMsds/s1600/blocked%2Bplugin.png[/IMG]

this a new "security" feature >> [http://blog.chromium.org/2011/03/mini-newsletter-from-your-google-chrome.html](http://blog.chromium.org/2011/03/mini-newsletter-from-your-google-chrome.html)

to get past this simply enable to **Preferences>Content Settings> Plugins - auto allowed or sth**; should look like this:
[http://img269.imageshack.us/i/bildschirmfotoeinstellu.png/](http://img269.imageshack.us/i/bildschirmfotoeinstellu.png/)

sorry, I couldn't find the english version/translation and I'm too lazy to keep trying.

what's interesting is that I didn't even installed flash for chromium or copied over the libflashplayer.so. I just had to type ```
about:plugins
``` in the address bar to enable it.

---

### Post by ron999 on 2011-03-12
Thanks **PoHandle**. For me [COLOR="Red"]--allow-outdated-plugins[/COLOR] was the cure.:)

---

### Post by rtimai on 2011-03-12
Thanks, PoHandle, for the corrections, both noted. Yeah, I am running Chromium as my default browser, although I do use Google Chrome and Firefox as alt browsers. And Oldhacker did state that he was seeing a plug-in error, not a codec prompt. I jumped the gun, and apologize.

---

### Post by FraggyX on 2011-03-13
I was having further problems than what was covered here, so then I visited the about:plugins page suggested by dirty_harry, only to discover that for some reason the updated Chromium browser, in addition to my libflashplayer.so, it seemed to think there existed an old version of flash somewhere that I can't locate and it must have been conflicting with the new version. For now, disabling the old version 9 on the page and a restart of Chromium seems to work, but thorough searches on my system can't find this old version anywhere.

My problems related to this (flash out of date, does not run, even with --allow-outdated-plugins) did not occur until a recent update (3/11) of Chromium. Makes no sense as I doubt flash would be embedded into Chromium, especially a version older than what I had to begin with, but I thought I'd pass that along in case this happens to anyone else out there.

---

### Post by Animal X on 2011-03-13
> **Oldhacker said:**
> Using Ubuntu 10.04 64 bit. After the most recent updates were installed, Chromium complains that my flash plug-ins are out of date when I attempt to run a video on YouTube. However, this does not appear to affect Firefox, which plays YouTube as usual.

My question is: Should I accept the flash plug-in offered from Chromium, and if I do will it affect Firefox?
maybe there is a fix but i notice chrome isnt as robust as firefox(wasn't that the point?lol) and it wont play a lot of streaming media like a simple mp3's, it makes me download it or it stalls in the browser, and all my stuff IS up-to-date, and passes acid test and all that. granted chrome is faster and cleaner, but IMO i just dont think it has as much quality as firefox in this area.

---

### Post by tosbourn on 2011-03-20
> **ron999 said:**
> Thanks **PoHandle**. For me [COLOR="Red"]--allow-outdated-plugins[/COLOR] was the cure.:)

There is a reason it is warning you, simply allowing outdated plugins is dangerous.  

Most of the time plugins get updated to fix security issues and flash has more than it's fair share of them.

What you have done hasn't cured the problem, it has hidden it.

---

### Post by pmorton on 2011-03-22
> **beew said:**
> Just install the flash-aid plugin for firefox, it will remove conflicting flash versions in your system, get you update flash whenever it is avaliable and it also does some optimization for you.

At last, after over 2 months, this has got flash sorted for Firefox 4 on Maverick. Got it working on Chrome at the same time. How come Mozilla then couldn't provide this as an official solution?

---

### Post by ron999 on 2011-03-22
> **tosbourn said:**
> 
What you have done hasn't cured the problem, it has hidden it.

I've hidden the reminder and it's cured the problem.:lolflag:
There's a good reason for using v10.1 flashplugin.
Discussed in the thread here:- [http://ubuntuforums.org/showthread.php?t=1686439](http://ubuntuforums.org/showthread.php?t=1686439)

---

### Post by markackerman8@gmail.com on 2011-04-02
"Just install the flash-aid plugin for firefox" worked for me, and thanks to the guy who mentioned it
:)

Edited !  Nope did NOT work, but what did is entering about:flash in my chromium and disabled the flash plugin (it was even warning in red there)and everything seems to be working fine.  If I don't re-edit this, it means that everything works.

note: this is for ubuntu 64-bit which adobe did not have flash for!

---

### Post by noobie1 on 2011-04-02
I have this issue and am running flash version 10.0.45 64 bit

I'm guessing that chrome wants 10.2 but as far as know there is no such thing for 64 bit.

Anyone know if there is a newer 64 bit version, or if I'm talking rubbish?
Otherwise I think I'll stick to the "hiding it under the carpet approach"

---

### Post by rtimai on 2011-04-03
noobie1, 

I'm not sure if running 64-bit produces this issue, but here's my two cents. I'm running both Chromium and Google Chrome on Maverick 64-bit and not getting the outdated Flash warning. Do you have ubuntu-restricted-extras 42 and flash-plugin-install 10.2.153.1ubuntu0 installed? If you do, then I'm totally clueless.

---

### Post by wolfen69 on 2011-04-03
I've never had to install codecs of any kind in chrome/chromium. By default it will borrow from your mozilla plugins.

> **rtimai said:**
> noobie1, 

I'm not sure if running 64-bit produces this issue, but here's my two cents. I'm running both Chromium and Google Chrome on Maverick 64-bit and **not** getting the outdated Flash warning.
Same for me. I always put libflashplayer.so (64bit) in /usr/lib64/mozilla/plugins and it has worked great for me every time.

---

### Post by rtimai on 2011-04-04
My copy of libflashplayer.so is in
 /usr/lib/flashplugin-installer

I also have two copies of npwrapper.libflashplayer.so, in 
 /var/lib/flashplugin-installer
     and
 /user/share/ubufox/plugins (broken)

I forgot I had Firefox 3.6.16 installed too. In any event I don't seem to be getting the outdated plugin warning in Firefox even with the broken npwrapper, whatever that is. But then I don't use Firefox much any more, and maybe I haven't visited a site that would prompt that warning.

Anyway, I think the ubuntu-restricted-extras 42 and the flashplugin-installer 10.2.153 were the key modules on my system. Again, my two cents.

---

### Post by rickrich on 2011-04-25
$ locate libflashplayer.so
/usr/lib/chromium-browser/plugins/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so

$ ll /usr/lib/adobe-flashplugin/libflashplayer.so
-rw-r--r-- 1 root root 12110428 2011-04-15 13:06 /usr/lib/adobe-flashplugin/libflashplayer.so

$ ll /usr/lib/chromium-browser/plugins/libflashplayer.so
-rw-r--r-- 1 root root 10235940 2010-09-14 21:14 /usr/lib/chromium-browser/plugins/libflashplayer.so

$ sudo mv libflashplayer.so libflashplayer.so.org

$ sudo cp -a /usr/lib/adobe-flashplugin/libflashplayer.so .

Works for me on a Dell Mini-9 netbook running 8.04.

---

### Post by daylife on 2011-05-14
> **rickrich said:**
> $ locate libflashplayer.so
/usr/lib/chromium-browser/plugins/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so

$ ll /usr/lib/adobe-flashplugin/libflashplayer.so
-rw-r--r-- 1 root root 12110428 2011-04-15 13:06 /usr/lib/adobe-flashplugin/libflashplayer.so

$ ll /usr/lib/chromium-browser/plugins/libflashplayer.so
-rw-r--r-- 1 root root 10235940 2010-09-14 21:14 /usr/lib/chromium-browser/plugins/libflashplayer.so

$ sudo mv libflashplayer.so libflashplayer.so.org

$ sudo cp -a /usr/lib/adobe-flashplugin/libflashplayer.so .

Works for me on a Dell Mini-9 netbook running 8.04.
This did the trick for me, with a few small changes.
Locate gave me

~/.mozilla/plugins/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so

Then I did the 'll' commands (what do they do actually?), followed by:

sudo mv ~/.mozilla/plugins/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so.org

sudo cp -a /usr/lib/adobe-flashplugin/libflashplayer.so ~/.mozilla/plugins

I did this after installing the newest plugin from the Adobe website. Gone is the annoying message!

---

### Post by connellc on 2012-01-05
> **hno3 said:**
> I was facing this issue from past few day, but I resolved it today!

This is how I identified the problem:
My chrome was using the flash plugin in the /usr/lib/mozilla/plugins/ directory. Its for firefox but don't know why chrome uses it. This plugin was dated back to 2010-01-27 (thats more than a year). Now, why only chorme is issuing the warning but not the firefox. I surfed and found this website ([http://news.cnet.com/8301-27080_3-20009231-245.html](http://news.cnet.com/8301-27080_3-20009231-245.html)). It reads that chrome will be warning users if they are using any old plugins.

Solution that worked for me:
I tried the solution mentioned by 'PoHandle' but didn't work for me. So I used the synaptic manager and searched the term "adobe" without quotes and found a flash plugin installer for ubuntu 10.04 by Adobe. Installed it and **ISSUE RESOLVED**. I am happy now.:D


Downloading the .tar.gz package for the flashplugin-installer is the package I used to get the libflashplayer.so file into the directory usr/bin/chromium-browser/plugins (which had not existed, by the way).:confused:

However, upon further examination, I noticed that Chrome was not installed into usr/bin/ but into opt/google/chrome. I also copied the libflashplayer.so into the plugin directory that was there. I have yet to see that that that works....

This did not work.:confused:

I had quit Chrome and restarted it. Still did not work.:confused:

Installing adobe-flashplugin using Synaptic does not work. This uninstalls flashplugin-installer, as the packages are mutually exclusive.:(

-------
Okay, so creating a directory called plugins in opt/google/chrome and putting the libflashplayer.so file there does work. I even removed the  "allow outdated plugins" line from my launcher. 

No complaints by Chrome! :-o

:0 :) :-)

---

### Post by bmarius on 2012-01-09
Make sure "adobe-flashplugin" is installed. Open about:plugins in Chrom(e/ium) and find the flash player section. Since I have firefox installed as well, this section lists three files: Chromium's own, Firefox' version and adobe-flashplugin's version. Disable Chromium's and Firefox' and you're golden.

---

### Post by steve_thorley on 2012-04-22
I had this problem too but I just went to the Adobe website and downloaded the latest version of flash.

---

