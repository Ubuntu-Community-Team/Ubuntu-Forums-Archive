---
title: "Howto Install Flash 10 on AMD 64 Easily"
date: 2008-11-21
forum: Multimedia Software
---

### Post by digitalbenji on 2008-11-21
I had been having a real pain with this, but I just noticed that on November 17th (just a few days ago), adobe released an Alpha version of 64bit Flash!!!
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
This is really easy to do.  

Do this:
First, clean up all the flash junk that you have around:
```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge flashplugin-nonfree
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/nsplug***
sudo rm -f /usr/lib/firefox-addons/plugins/nsplug***
sudo rm -f /usr/lib/firefox-3.0.4/plugins/libflashplayer.so
sudo rm -f /usr/lib/firefox-3.0.4/plugins/nsplug***
sudo rm -f /usr/lib/iceaweasel/plugins/libflashplayer.so
sudo rm -f /usr/lib/iceaweasel/plugins/nsplug***
rm -rf ~/.macromedia

```
Basically, you want to get rid of every instance of flashplayer and the nsplugged wrapper that may exist.  Look around if this doesn't work.

Now, get the new flash player and unzip it:

```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
tar -xvzf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
```

Now, copy it to where it needs to be:
```
sudo cp libflashplayer.so /usr/lib/iceaweasel/plugins/
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo cp libflashplayer.so /usr/lib/firefox-3.0.4/plugins/

```

Then install some stuff I needed to get sound working:
```
sudo apt-get install libflashsupport
```

Then restart firefox:
```
killall firefox
```

And it should work, it did for me!

---

### Post by Yellow Pasque on 2008-11-21
Just some notes:
- The firefox-3.0.x directory is just a symlink to firefox-addons, so you're essentially copying (and rm'ing) stuff twice.
- For those using OSS4, don't install the repo version of libflashsupport; use the attached libflashsupport.so (copy to /usr/lib). Also install libssl0.9.8 and libnss-mdns packages.

---

### Post by m0bilitee on 2008-11-21
No worky for me. Where to begin debug?

Tools-Addons->Plugins does show Shockwave Flash 10.0 d20.

---

### Post by digitalbenji on 2008-11-21
What doesn't work, flash, or flash with sound?

Can you print the output of the following:
```
ls /usr/lib/firefox-addons/plugins/
```

As well asL
```
ls /usr/lib/mozilla/plugins/
```


THanks,

---

### Post by Arup on 2008-11-22
The easiest way is to do a --purge remove of old flashplugin and nsplugin. Then download flash 10x64, untar, mv libflashplayer.so to /usr/lib/mozilla/plugins and it works nicely for FF and Opera, nothing else to do.

---

### Post by don_xvi on 2008-11-22
Current status: firefox won't start.

LoadPlugin: failed to initialize shared library /home/q2user/.mozilla/plugins/libflashplayer.so [/home/q2user/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

Does this mean I need to copy the new libflashplayer.so into this directory ?  Maybe I'm looking at an old 32 bit version ?  As with any attempt to make linux work... I'm beginning to research.  Edits as they become available.

Update:
OK, I tried copying the libflashplayer.so into the location I seemed to be referencing it at, no help. Then I thought to try starting fresh rather than restoring my old pages I'd been looking at and it starts, and it plays youtube, but firefox crashes when I try to access citicards.com.
Will try alternate method suggested.

Update:
Tried process listed immediately above and in a similar note in another thread.  Still crashes on citicards.com.  A terminal page full of errors with NP_GetMIMEDescription, NP GetValue, ..... Segmentation fault.

Or is this just as good as the new plugin is at this point ?  Can someone that's satisfied with their performance try going to citicards.com and check ?  Or freep.com, that's the website for the Detroit Free Press which has a link to video embedded on its homepage.  It may shut your browser down....

Summary: It's all mucked up now, I just want something that'll work.  I got the same problems with the 32 bit Flash 10, eventually cleared a bunch of things out and got back to where I was before with Flash 9.  I'd orignally undertaken this all to improve the appearance of citicards.com, as with Flash activated it clears my entire screen and I have to turn it off, then reload the page to do my online banking.  :(

---

### Post by rv65 on 2008-11-22
> **Temüjin said:**
> Just some notes:
- The firefox-3.0.x directory is just a symlink to firefox-addons, so you're essentially copying (and rm'ing) stuff twice.
- For those using OSS4, don't install the repo version of libflashsupport; use the attached libflashsupport.so (copy to /usr/lib). Also install libssl0.9.8 and libnss-mdns packages.

I actually a custom libflashsupport.so and it works well. Not that hard to do.

---

### Post by psyke83 on 2008-11-22
Please don't use *any* version of libflashsuppport - it causes instability in Firefox. See [bug #192888]("https://bugs.launchpad.net/bugs/192888").

To make PulseAudio work properly with Flash, you only need to ensure the PulseAudio ALSA plugins are enabled.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by m0bilitee on 2008-11-22
> **digitalbenji said:**
> What doesn't work, flash, or flash with sound?

Can you print the output of the following:
```
ls /usr/lib/firefox-addons/plugins/
```

As well asL
```
ls /usr/lib/mozilla/plugins/
```


THanks,

me@here:/usr/lib/firefox-addons/plugins$ ls -l
total 9320
-rwxr-xr-x 1 root root 9525320 2008-11-21 19:12 libflashplayer.so

me@here:/usr/lib/mozilla/plugins$ ls -l
total 9320
-rwxr-xr-x 1 root root 9525320 2008-11-21 19:12 libflashplayer.so

---

### Post by m0bilitee on 2008-11-22
Ah! Fixed mine. I had a residual install of the old npwrapper stuff in ~/.mozilla/plugins. So in addition to above make sure you purge local user installs.

:-)

---

### Post by Yellow Pasque on 2008-11-22
> **psyke83 said:**
> Please don't use *any* version of libflashsupport - it causes instability in Firefox. See [bug #192888]("https://bugs.launchpad.net/bugs/192888")
That's an oversimplified statement. For those running Ubuntu Hardy (and/or Flash 9), they'll need libflashsupport from the repo.

For those running OSS4, they'll need to build a libflashsupport with OSS defined.

---

### Post by psyke83 on 2008-11-23
> **Temüjin said:**
> That's an oversimplified statement. For those running Ubuntu Hardy (and/or Flash 9), they'll need libflashsupport from the repo.

For those running OSS4, they'll need to build a libflashsupport with OSS defined.

It's not an oversimplified statement, it's a statement of fact. The version you advocate using, which I assume is the original libflashsupport reference code from Adobe, still causes instability in Firefox.

The only way to get a stable Flash experience is via Flash 10 and the PA ALSA plugins (in the case of ALSA & PulseAudio). 

I'm not aware of any solutions for OSSv4, except using libflashsupport and nspluginwrapper together (also for 32bit users). When the Flash process is isolated from Firefox, the plugin can crash without causing a segmentation in Firefox itself. Newer releases of nspluginwrapper also auto-restart plugins upon crashing. My PPA has a recent build if anyone's interested.

Note: this is still not a perfect solution, as Flash will intermittently crash and re-appear on websites.

---

### Post by digitalbenji on 2008-12-04
Yes, having used this libflashsupport for some time, I can say the following:
1) Firefox is not unstable (this thread is about AMD 64 Flash 10 only, all this 32 bit stuff is off topic in my opinion)
2) Flash tends to buffer for about the first minute of a video, then hang out.  I think this has to do with the /tmp being filled up and pointing to some strange place instead of actually referencing the swap at /dev/shm.  I've made some manual edits to try to fix this, but they don't seem to have the desired effect.  

To the person who says that the computer doesn't boot: I'm sorry, but I imagine you're just joshing on me anyway (I hope so at least).

---

### Post by don_xvi on 2008-12-05
Actually, I think that was me that clicked that option for "computer doesn't boot".  It wasn't exactly true, the computer would boot but Firefox wouldn't start.  Eventually, I seem to recall purging a bunch of things and got it to restart again, then finally wound up with the only thing I've been able to make work at all, using Flash 9 32 bit with the wrapper which works >50% of the time, and sometimes forces me to restart Firefox if I want to see Flash.  Maybe this will all work better if I do that fresh install of ubuntu this weekend like I want to.

---

