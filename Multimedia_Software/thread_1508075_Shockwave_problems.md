---
title: "Shockwave problems:"
date: 2010-06-12
forum: Multimedia Software
---

### Post by mpolito1969 on 2010-06-12
I have the most common problem on the internet: Firefox doesn't play sound in Youtube (Ubuntu 10.04, Firefox 3.6.3).

I read tons of pages, one of these is:

[http://kb.mozillazine.org/Video_or_audio_does_not_play](http://kb.mozillazine.org/Video_or_audio_does_not_play)

using the "Testing plugins" link on the bottom of the page I can see that all plugins work except for "Shockwave".

In the "about:plugins" page I can see

> Shockwave Flash

    File: /home/max/.mozilla/plugins/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

(I've enabled "plugin.expose_full_path" in about:config)

If I go here:

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

I can't see anything below the line "Adobe Shockwave Player", which makes me think Shockwave is not working.

Any help to have this plugin in working?

Ciao,
Max

---

### Post by gandaran on 2010-06-12
what version of ubuntu, 32-bits or 64-bits? if 64-bits install 64-bits adobe flash, the 32-bits flash from the repositories does not work very well for some users running 64-bits ubuntu system.

---

### Post by BobLand on 2010-06-12
I gave up with Firefox after it stopped allowing me to control anything in YouTube or any flash for that matter.  Loaded Chrome.  Can't believe the difference.  No stuttering, view in any mode.  Firefox is a dying elephant.

On top of that, most of the Firefox add-ons that I use are in Chrome.  I still don't trust Google but they made one heck of a browser.

---

### Post by gandaran on 2010-06-12
> I still don't trust Google but they made one heck of a browser.
install the open source Chromium, it's exactly the same fast browser as Chrome but without the  google spyware.

---

### Post by lovinglinux on 2010-06-12
@mpolito1969

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **gandaran said:**
> what version of ubuntu, 32-bits or 64-bits? if 64-bits install 64-bits adobe flash, the 32-bits flash from the repositories does not work very well for some users running 64-bits ubuntu system.

Adobe is not releasing more 64bit flash plugin versions and all available versions at the moment have a critical vulnerability. Users should be oriented to install version 10.1.53.64 from the repositories, which unfortunately is 32bits.

> **BobLand said:**
> Firefox is a dying elephant.

No, is not. You just need to treat it well. I have more than 50 extensions installed and Firefox works perfectly.

Although Chrome has some neat features and concept, is far from being better than Firefox, specially for those users who like full control of the interface and need power features provided by extensions. Chrome customization and functionality is a joke next to Firefox. Extensions are limited in functionality and interface. 

See [this video](http://lovinglinuxblog.blogspot.com/2010/05/browser-speed-test.html) comparing both browsers speeds.

---

### Post by mpolito1969 on 2010-06-13
> **lovinglinux said:**
> @mpolito1969

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 


I did it. It made some work in a terminal window than asked me to restart Firefox.

Nothing has changed, Youtube keeps being silent and this page:

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

keeps having nothing below the "Adobe Shockwave Player" line.

The nicest thing is that everything worked perfectly before the upgrade to Ubuntu 10.04. I will never never never never update an operating system again. In Italy we say "never touch a winning team". I touched it and I'm paying for that...](*,)

Ciao,
Max

---

### Post by lovinglinux on 2010-06-13
> **mpolito1969 said:**
> I did it. It made some work in a terminal window than asked me to restart Firefox.

Nothing has changed, Youtube keeps being silent...

That was just to make sure you have the correct version of flash installed system wide instead of the profile folder. If you check Shockwave path in the **about[noparse]:[/noparse]plugins** you will see it no longer points to /home/max/.mozilla/plugins/libflashplayer.so. Please also verify that it says version 10.1 r53. This is important, since older versions have a critical vulnerability.

> **mpolito1969 said:**
> ...and this page:

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

keeps having nothing below the "Adobe Shockwave Player" line.

Don't worry, I don't get anything there either and my flash plays just fine.

Now that we know you have the correct plugin in the correct place, we need to fix the sound issue.

Try the following commands and reboot:

```
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

> **mpolito1969 said:**
> 
The nicest thing is that everything worked perfectly before the upgrade to Ubuntu 10.04. I will never never never never update an operating system again. In Italy we say "never touch a winning team". I touched it and I'm paying for that...](*,)

Create a separate home partition, so you can preserve you personal files when doing a clean install. I only do clean installations of every new Ubuntu release.

---

### Post by mpolito1969 on 2010-06-13
> **lovinglinux said:**
> 
Now that we know you have the correct plugin in the correct place, we need to fix the sound issue.

Try the following commands and reboot:

```
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```


Done it: Youtube is still mute.

Any idea?

Ciao,
Max

---

### Post by lovinglinux on 2010-06-13
Try this:

[http://ubuntuforums.org/showthread.php?t=1412153](http://ubuntuforums.org/showthread.php?t=1412153)

---

### Post by mpolito1969 on 2010-06-14
> **lovinglinux said:**
> Try this:

[http://ubuntuforums.org/showthread.php?t=1412153](http://ubuntuforums.org/showthread.php?t=1412153)

It didn't work.

I tried to install the package but the system told it was already there.

Neverthless, I created the file, copied in it the specified content and rebooted.

Unluckily it didn't change the situation.

Ciao,
Max

---

### Post by lovinglinux on 2010-06-14
> **mpolito1969 said:**
> It didn't work.

I tried to install the package but the system told it was already there.

Neverthless, I created the file, copied in it the specified content and rebooted.

Unluckily it didn't change the situation.

Ciao,
Max

Have you checked if the PCM volume is all the way up?

---

### Post by mpolito1969 on 2010-06-15
> **lovinglinux said:**
> Have you checked if the PCM volume is all the way up?

I think it is, as all audio works except for Youtube video in Firefox.

Moreover, when I'm on a Youtube video there is a small red cross on the speaker icon in the bottom left of the video frame, where you can adjust the video volume, which makes me think there is something wrong with the plugin.

Anyway, I'll check it. I must use alsamixer for that, right?

Ciao,
Max

---

### Post by lovinglinux on 2010-06-15
> **mpolito1969 said:**
> Moreover, when I'm on a Youtube video there is a small red cross on the speaker icon in the bottom left of the video frame, where you can adjust the video volume, which makes me think there is something wrong with the plugin.

Have you clicked to see if it toggles the mute?

> **mpolito1969 said:**
> Anyway, I'll check it. I must use alsamixer for that, right?

I guess so. I use KDE, so I'm not very familiar with current Gnome settings, but alsamixer should be able to do it.

---

### Post by LiteralKaiser on 2010-06-16
I gave up on getting flash to work even 50% of the time in Ubuntu a long time ago, for me, it refuses to click at all half the time, and reloading does nothing.

---

### Post by lovinglinux on 2010-06-16
> **LiteralKaiser said:**
> I gave up on getting flash to work even 50% of the time in Ubuntu a long time ago, for me, it refuses to click at all half the time, and reloading does nothing.

I presume you are using a 64bit browser. 

To fix the issue with flash buttons do this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by mpolito1969 on 2010-06-20
> **lovinglinux said:**
> Have you clicked to see if it toggles the mute?



I guess so. I use KDE, so I'm not very familiar with current Gnome settings, but alsamixer should be able to do it.

Done, it doesn't toggle anything, it's mute mute mute.

I checked with alsamixer and PCM volume is at the highest level.

Ciao,
Max

---

### Post by ahso4271 on 2010-06-20
That was my solution:
[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

---

### Post by mpolito1969 on 2010-06-20
> **ahso4271 said:**
> That was my solution:
[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

It says to modify file /usr/lib/nspluginwrapper/i386/linux/npviewer but, on my system, directory /usr/lib/nspluginwrapper only contains dirs.d, no directory i386 is there.

Ciao,
Max

---

### Post by lovinglinux on 2010-06-20
> **mpolito1969 said:**
> It says to modify file /usr/lib/nspluginwrapper/i386/linux/npviewer but, on my system, directory /usr/lib/nspluginwrapper only contains dirs.d, no directory i386 is there.

Ciao,
Max

That fix is for LiteralKaiser, who hijacked your thread and is the same solution I provided on post #15. It should be used to fix the problem with unclickable buttons when using 32bit flash on a 64bit system.

---

### Post by mpolito1969 on 2010-06-21
Now what?

---

### Post by mpolito1969 on 2010-06-25
OK... my experience with Firefox has come to an end. I'll try Cromium.

Thanks to all.

Ciao,
Max

---

### Post by ttakun on 2010-06-25
Same problem with my Kubuntu, 64 bits, ...
No sound playing flash in youtube ... neither in Firefox nor in Chromium
I fixed it last week, after reading tons os pages and it worked once. After turning off and on the computer it went mute again ...
This sucks :confused:

Post Edition: In my laptop, where I have Ubuntu 10.04, 32 bits, it works and it sounds perfectly well :-k

---

### Post by mpolito1969 on 2010-06-26
Youtube audio doesn't work in Chromium either.

The most stupid thing I have ever done in my life has been installing this damned 10.04. Everything worked perfectly with 9.10, I've lost both UMTS connection and Youtube audio with just a couple of clicks.

Is that possibile there is NO WAY AT ALL to solve this problem? I've been using Linux for more then ten years now, I NEVER NEVER NEVER had all the insolvable problems I had during the last month...

Ciao,
Max

---

### Post by lovinglinux on 2010-06-26
> **mpolito1969 said:**
> Youtube audio doesn't work in Chromium either.

The most stupid thing I have ever done in my life has been installing this damned 10.04. Everything worked perfectly with 9.10, I've lost both UMTS connection and Youtube audio with just a couple of clicks.

Is that possibile there is NO WAY AT ALL to solve this problem? I've been using Linux for more then ten years now, I NEVER NEVER NEVER had all the insolvable problems I had during the last month...

Ciao,
Max

Have you tried to create a new Ubuntu user, log with that account an check if sound works?

I'm currently in the process of compiling a list of flash issues and solutions. Unfortunately this will take some time, since I need to review hundreds of threads (my memory is not very good). See [http://ubuntuforums.org/showthread.php?t=1517564](http://ubuntuforums.org/showthread.php?t=1517564)

---

