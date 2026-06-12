---
title: "Flash problem - BBC Proms Programme Notes"
date: 2012-07-16
forum: Multimedia Software
---

### Post by heyup on 2012-07-16
I have problem viewing programme notes for BBC Proms 2012 such as:

[http://www.bbc.co.uk/proms/whats-on/2012/july-14/14187/programme-notes](http://www.bbc.co.uk/proms/whats-on/2012/july-14/14187/programme-notes)

The web page requires javascript enabled and flash installed. The programme notes fail to load. Seems to be a flash problem.

Can anyone else get the programme notes without this problem?

I'm using:
Lucid 10.04 
Firefox 13.0.1
Flash & Javascript enabled.

---

### Post by claracc on 2012-07-16
No problem here, I can see it perfectly well.

lucid lynx 10.04.04, firefox 13.0.1, flash plugin 11.2r202, oracle java 1.7.0.05

I  think it could be a java problem, not a flash one.

---

### Post by ajgreeny on 2012-07-16
For some reason your link did not work, but I can get this page to work OK direct from a google search.
[http://www.bbc.co.uk/proms/whats-on/2012/july-14/14187/programme-notes](http://www.bbc.co.uk/proms/whats-on/2012/july-14/14187/programme-notes)

Your link
[http://www.bbc.co.uk/proms/whats-on/2012/july-14/14187/programme-notes](http://www.bbc.co.uk/proms/whats-on/2012/july-14/14187/programme-notes)
 was exactly the same, so I am baffled.

I am using Lubuntu 12.04 on a netbook at the moment with java openjdk7 and flash installed in Firefox 13.0.1.

I wonder if you have flashblock or noscript add-ons for firefox, as I have found it difficult to get the BBC mediaplayer (flash) to work with those enabled, so the BBC sites are in the whitelist for flashblock, meaning flash works on BBC sites.  Do you also have the java plugin installed, either oracle-java-plugin or icedtea plugin, both obviously work OK.

---

### Post by heyup on 2012-07-16
Thanks for pointing me in the right direction, but I'm still having problem loading the programme notes.

Checked Firefox plugins in Firefox preferences. It stated I had an outdated version of Java installed, which was automatically disabled by Firefox.

Installed Icedtea6 plugin. No longer get message about outdated Java, but still cannot load the programme notes. I have openjdk6 installed.

I don't have flashblock or noscript add-ons installed.

---

### Post by bobsan on 2012-07-16
Nothing to do with java. java doesn't work at all in Chrome for my laptop (see screenshot for java test), but I can still see the programme notes perfectly well (see second screenshot)

p.s. I can see the program notes in Firefox as well, but since java IS working in my Firefox install it doesn't help in eliminating java as a culprit.

---

### Post by heyup on 2012-07-16
> **bobsan said:**
> Nothing to do with java. java doesn't work at all in Chrome for my laptop (see screenshot for java test), but I can still see the programme notes perfectly well (see second screenshot)

Thanks for that. So Java isn't the culprit.

Reinstalled Adobe Flash. That hasn't solved the problem. I still think Flash is the likely cause of the fault.

I don't recall having any problem last year viewing the Proms programme notes in Firefox, other than it required Flash and Javascript enabled. In previous years, the Proms programme notes were available as text documents (it is frustrating that the BBC should now use Flash).

---

### Post by bobsan on 2012-07-16
How did you install flash? Does flash work on other sites (say Youtube)? 

Try install the flash-aid addon for Firefox (Open Firefox, go to Tools > Add-Ons > Get Add-Ons and search for flash-aid) Restart, look for the pink icon with the 'f' on the addon  bar, click it to run the script in the Wizard mode, it will clean up conflicting versions of flash that might have been installed in your system and reinstall the latest flash. 

After that restart FF and see if it helps.

---

### Post by heyup on 2012-07-17
> **bobsan said:**
> 
Try install the flash-aid addon for Firefox (Open Firefox, go to Tools > Add-Ons > Get Add-Ons and search for flash-aid) Restart, look for the pink icon with the 'f' on the addon  bar, click it to run the script in the Wizard mode, it will clean up conflicting versions of flash that might have been installed in your system and reinstall the latest flash.

Unfortunately flash-aid didn't solve the problem.

I removed both firefox and flash, purged them from the cache, and reinstalled by downloading from repository (not the cache). That didn't solve problem.

Installed flash-aid add-on. That removed adobe-flashplugin and then installed flashplugin-installer. That didn't solve the problem either.

Edit. Flash not working on youtube.

---

### Post by bobsan on 2012-07-17
If Youtube doesn't work also you clearly have a flash problem. Unfortunately I don't know what else to do if flash-aid doesn't work. Maybe you should post a new thread just saying flash doesn't work in your 12.04 system, hopefully others will give you better advice.


P.S. By "removing Firefox" did you just remove it with apt-get or did you also remove the hidden .mozilla folder in your home directory? You need to remove the latter to get rid of old configurations, otherwise reinstalling will not fix the problem of corrupted configuration.

---

### Post by ajgreeny on 2012-07-17
> **heyup said:**
> Unfortunately flash-aid didn't solve the problem.

I removed both firefox and flash, purged them from the cache, and reinstalled by downloading from repository (not the cache). That didn't solve problem.

Installed flash-aid add-on. That removed adobe-flashplugin and then installed flashplugin-installer. That didn't solve the problem either.

Edit. Flash not working on youtube.
You may have the same problem that I have with the most recent flash version, 11.2.202, which totally refuses to show anything on my main desktop machine.

I solved that problem by using the earlier 11.1.102-63 version of flash which can be downloaded from a link in lovinglinux's post at [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) and then installed using flash-aid, Advanced mode as instructed in that same post.  If you install flash that way it will not show as installed in the system package manager, and there will be no further updates to break flash.

---

### Post by rizal23 on 2012-07-17
> **heyup said:**
> I have problem viewing programme notes for BBC Proms 2012 such as:

[http://www.bbc.co.uk/proms/whats-on/2012/july-14/14187/programme-notes](http://www.bbc.co.uk/proms/whats-on/2012/july-14/14187/programme-notes)

The web page requires javascript enabled and flash installed. The programme notes fail to load. Seems to be a flash problem.

Can anyone else get the programme notes without this problem?

I'm using:
Lucid 10.04 
Firefox 13.0.1
Flash & Javascript enabled.

you try to update your flash use and customize to your firefox version.

---

### Post by ajgreeny on 2012-07-18
> **rizal23 said:**
> you try to update your flash use and customize to your firefox version.
??

What do you mean by that?

---

### Post by heyup on 2012-07-18
> **ajgreeny said:**
> You may have the same problem that I have with the most recent flash version, 11.2.202, which totally refuses to show anything on my main desktop machine.

I solved that problem by using the earlier 11.1.102-63 version of flash which can be downloaded from a link in lovinglinux's post at [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) and then installed using flash-aid, Advanced mode as instructed in that same post.  If you install flash that way it will not show as installed in the system package manager, and there will be no further updates to break flash.

That has solved the problem. Downgraded to 11.1.102-63 and installed noscript. Flash now works again, and the BBC Proms programme notes download.

Anyone know how I can save the Proms programme notes? Can't find them in /tmp but they must be somewhere!

---

### Post by ajgreeny on 2012-07-18
> **heyup said:**
> That has solved the problem. Downgraded to 11.1.102-63 and installed noscript. Flash now works again, and the BBC Proms programme notes download.

Anyone know how I can save the Proms programme notes? Can't find them in /tmp but they must be somewhere!
I don't think it's possible in the normal way.

The only way that I have managed to do it, and it's a bit convoluted, is by using the "Select text" button at the bottom of the flash window, copying the text and then using "Paste special" -> Unformatted text in Libreoffice, as a normal paste does not seem to work at all in LO, though it does in abiword, though there the text is unformatted by default.

It's a real pain as that way there is a complete loss of formatting, but it is a start, I suppose for any text that you really need.  I can't, however, get any pictures to copy.

---

### Post by heyup on 2012-07-19
> **heyup said:**
> 
Anyone know how I can save the Proms programme notes? Can't find them in /tmp but they must be somewhere!

Haven't found the cache files using Firefox, but in Opera they are in /user/.opera/cache/sesn

Unfortunately the files are not a in user friendly format. Some files are jpeg image and others shockwave flash.

Shame the BBC doesn't make these Proms programme notes available in pdf format rather than awful flash.

---

### Post by ajgreeny on 2012-07-19
Another alternative way would be to make screenshots of each page and save them, and then if you want them all in one file to put them all in a libreoffice document, and finally export as a pdf, if that's your desired file type.

Clunky, but it would get there.

---

### Post by heyup on 2012-07-21
> **ajgreeny said:**
> Another alternative way would be to make screenshots of each page and save them, and then if you want them all in one file to put them all in a libreoffice document, and finally export as a pdf, if that's your desired file type.

Great idea. Worked a treat!

---

