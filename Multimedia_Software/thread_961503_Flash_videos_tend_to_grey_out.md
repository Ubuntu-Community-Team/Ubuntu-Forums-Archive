---
title: "Flash videos tend to grey out"
date: 2008-10-28
forum: Multimedia Software
---

### Post by johnuk on 2008-10-28
I have non-free installed, as well as the drivers for my NVidia GeForce 6000 series and flash works. But I've noticed if I open a few tabs with other videos in them - if I'm browsing youtube - they tend to grey out. I loose the control bar and the entire flash window goes grey. But the sound will continue to play.

I'm wondering if this is a memory error, as it'll free up if I just close some of the other pages. I'll sometimes have to hit refresh a few times.

I only need to have two or three videos open at once for it to do it, not tens.

I have a gig of ram and am rarely doing anything more than looking at a couple of pages, so it can't be that I've burnt out all the resources.

Curiously, I've been having an issue I think might be related to this (memory allocation in relation to graphics) with XSane and scanning.

[Scanner problem]("http://ubuntuforums.org/showthread.php?p=6050492#post6050492")

Has anyone had this and solved?

Thanks!

---

### Post by aeiah on 2008-10-28
i just have a gig of ram too and firefox can grey out (does the whole of your browser grey out or is it just the video area?). you could try looking to see how your ram or cpu is doing when this happens i suppose. and make sure your swap is running properly. 
```
cat /proc/swaps
```

if your cpu usage shoots up when it happens, you could look at your dmesg log or run firefox from a terminal and see if that pops up any errors or anything.

---

### Post by dvanderson on 2008-10-28
FWIW, I just started having the same problem today.  I have 8GB RAM so memory isn't a problem.  With me, the videos start when I start-up firefox (restoring previous session) but upon pressing pause on one of them, all flash greys out and does not return until I restart.  The problem seems to have appeared after the latest updates were applied (i.e. no problems yesterday...)

David

---

### Post by johnuk on 2008-10-28
It's just the flash box it's self that grey out on mine and it's definitly not a loading greyout, it's a flat opaque crashed grey. The image and control bar don't return regardless of how long it's left.

I'm hoping this has a similar solution to my scanner problem. It's almost as if Ubuntu has misread the memory allocation in both situations.

---

### Post by zobcat on 2008-10-28
If you double-click the white area of the webpage, does that make the picture resume?

---

### Post by dvanderson on 2008-10-28
Once the flash box greys out, it is greyed out for all tabs/windows having flash in that browser.  Reloading the page or clicking around has no effect.  Restarting the browser will cause the flash to work again for a short time.

I'm using 8.04 (fully updated) 64-bit, with Firefox 3.03

---

### Post by zobcat on 2008-10-28
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

If you haven't yet, download Flash 10. They have ubuntu .debs on their site.

---

### Post by johnuk on 2008-10-29
Double clicking open space doesn't seem to help. Mine will clear up if i close any other flashes and reload

I'm trying Flash 10 - will report back

---

### Post by johnuk on 2008-10-29
I get a 'wrong architechture i386' error when I run the .deb

---

### Post by zobcat on 2008-10-29
Sounds like you've got 64 bit. If that is true, then follow the instructions below.

Just enter [Alejandro's script]("http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/") into a terminal:

```
wget http://queleimporta.com/downloads/flash10_en.sh && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh


```

That should take care of the entire installation.

---

### Post by johnuk on 2008-10-29
you're right, and the script works like a dream

will let you know how it gets on

---

### Post by dvanderson on 2008-10-29
The script worked for me as well.  I had to get rid of a defunct npviewer process first before flash worked but it hasn't had any problem since then.

---

### Post by Jeffa on 2008-10-30
That script did the trick for me. I'm running 64 bit. Thanks!

---

### Post by AnotherDave on 2008-10-30
The script doesn't work for me. Firefox says I either have JavaScript turned off or an old version of Flash. Entering about:plugins in the URL line shows that Flash is not installed.

I have Ibex upgraded from Heron on a 64-bit system, and I've tried all the "fixes" I could find. Best I get is Flash for a while, then the grey background only. Now I don't even get that.

I'd hoped that the new Ibex would take care of the problem, but nooo.

---

### Post by zobcat on 2008-10-30
@AnotherDave

I'm assuming that with all the so-called fixes you've tried, that you must have tried removing flash before trying the script. But, in case you haven't, try this:

```
sudo apt-get remove flashplugin-nonfree
```

And then try the script again.

Good luck!

---

### Post by AnotherDave on 2008-10-30
Same results.

I did remove previous Flash with Synaptic. Your script reports that flashplugin-nonfree was NOT installed, which is odd. So I ran the install script again (and it also has an uninstaller which reports that flashplugin-nonfree was not installed). 

Again, no Flash, and about:plugins also shows none installed.

Reinstalling, there were script warnings about /usr/lib/firefox/plugins, /usr/lib/nspluginwrapper/plugins, and /usr/lib/nspluginwrapper not being empty so not removed. And at this point I get confused.

Thanks for your help!

---

### Post by zobcat on 2008-10-31
Try these:

```
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

```

Then run the script again.

It's gonna work this time. I can feel it.

---

### Post by AnotherDave on 2008-10-31
No joy. "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player."

JavaScript is turned on, and we know that the Flash version is current, right? Seems like this might be a configuration problem. I admit to trying several published "fixes" before this one, some of which I didn't understand. 

Merely browsing to YouTube or Adobe will bring up scads of errors in my Error Console. "Unknown property 'behavior'", "Expected declaration but found '*'", etc.

---

### Post by zobcat on 2008-10-31
Try going to about:plugins again. Does it show anything about Java? If not, go to Edit>Preferences>Content Tab and make sure you have it checked.

---

### Post by AnotherDave on 2008-10-31
about:plugins shows no Java, and no JavaScript installed. Tried the Java test site, which was negative. Installed the JRE with Synaptic, and tried both of the above again; negative, negative.

It appears that there is a 64-bit problem with Java as well as with Flash. But is Java needed? And why would Synaptic allow an incorrect wordsize install?

The rest of Intrepid is sooo nice, and stable.

---

### Post by AnotherDave on 2008-10-31
Oh! The enable boxes for Java and JavaScript are both checked.

---

### Post by zobcat on 2008-10-31
I'm out of ideas. And apparently a lot of other people are too. Java's working on this issue. You might want to resort to Intrepid 32-bit.

Check out this [thread]("http://ubuntuforums.org/showthread.php?t=964958").

---

### Post by AnotherDave on 2008-10-31
The thing is, I DID have it working for a while. With no Java installed. Then it did the grey-screen thing. Then I "fixed" it and it worked again for awhile.

I think it's just getting lost, somewhere.

Anyway, thanks for the help!

---

### Post by AnotherDave on 2008-11-07
It appears to be a problem with the VIA K8M890 chipset that I have. My solution was to go back to 8.04. And I got Xubuntu this time. Works fine.

---

