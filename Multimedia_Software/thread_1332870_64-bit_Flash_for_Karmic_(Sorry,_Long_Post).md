---
title: "64-bit Flash for Karmic (Sorry, Long Post)"
date: 2009-11-20
forum: Multimedia Software
---

### Post by space-litter on 2009-11-20
The 32-bit "wrapper" for Flash on Karmic is not working for me. The plugin is there and the window loads, but I cannot use any controls in the window, and after about 5 minutes of use my CPU usage goes to 100% and my entire system is bogged until I restart my laptop.

I found what everyone else is saying a perfect fix: first remove all Flash operators (gnash, nonfree, etc) and then install the actual 64-bit version from the Flash website:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I then unpacked it.

Next, I followed the instructions below to install it as the new plugin:

# deinstall all other Flashplayer
# which are installed?:
dpkg -l flashplugin-nonfree mozilla-plugin-gnash swfdec-mozilla
#
# delete installed:
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree
#
# create new folder for Flashplayer:
sudo mkdir /usr/lib/flashplugin-nonfree/
#
# copy the new Flashplayer in the just created folder. change the first
# term to the unpacked path.
# if you unpacked to your Desktop, replace YourDownloadPath with
# /home/YourLoginName/Desktop
sudo cp YourDownloadPath/libflashplayer.so /usr/lib/flashplugin-nonfree/
#
# give Firefox the Flashplayer as Plugin , by creating a symbolic Link
# to the path of the Flashplayers in Plugin-folder from Firefox:
sudo ln -s  /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so


I followed the directions, and all seemed well (the console gave no errors), but no plugin is showing up in Firefox when I look at my addons. I can see the shared link in the mozilla/plugins folder and libflashplayer.so is there in its directory but it just isnt translating into Firefox for some reason?

Any ideas?

It is worth noting that when i unpacked the tar (Nov 20, the above instructions are from Oct 17), it actually made a new directory on my desktop with an additional file “flashplayer-installer” shell script. I copied libflashplayer.so out of the new dir and back onto the desktop so as to follow the above instructions more closely. Perhaps the tar had changed since he posted that? The instructions made no mention of the additional shell script.

---

### Post by HappyFeet on 2009-11-20
First, uninstall flash and everything else flash related. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

---

### Post by space-litter on 2009-11-20
Working so far! Thanks for the help. Let's hope the 64-bit version solves the CPU leak as well. If it doesn't, that will be another thread. Marking solved.

---

### Post by Wilbefast on 2009-11-22
I've now followed about 12 different guides (no exaggeration) for getting flash to work on Karmic 64 bit and none of them, this one included, have helped. At best there's been no difference, but now trying to load a page with flash on it makes the firefox freeze and grey out for a minute or two, and then I have white boxes where flash objects should be.

I have disabled Shockwave Flash 10.0 r32 (the library I copied in lib64/mozilla/plugins) to stop this lag - now there are no boxes at all.

I'm worried that I've wiped and reinstalled flash so many times now that something has been broken somewhere along the way. At any rate I am no closer to fixing this problem.


I find it rather pathetic that Karmic won't run flash properly without a great deal of fiddling, and that even then you're not guaranteed for it to work.

---

### Post by space-litter on 2009-11-22
Honestly I had this problem in Jaunty 32-bit as well (I just now moved up to 64-bit with this install). In fact the last time Flash worked flawlessly for me was in Hardy.

It "works" to varying degrees for me both out-of-the-box and after following this procedure. After a fresh Karmic install, everything loaded and both sound and video were fine (although none of the controls in the Flash window would work). However, after about 5-10 minutes my CPU would shoot to 100% and my entire system would be bogged until a restart, even if I closed Firefox.

Now that I have done this, the controls work and the CPU does not skyrocket, but some sites give me only audio and no video (mostly when I try to stream sports on justintv and atdhe). So, it is a tradeoff. Now when I want to stream a game I just boot into windows. Kind of a PITA, but hey that's why I have dual-boot to begin with.

For me the frustrating thing is not just that it's so buggy, but that it was a known issue before the final release and still wasn't addressed. As they say though, "you get what you pay for," and at least we have the support from fellow users through forums like these.

I am curious, do you happen to have the built-in Intel graphics card? That seems to be a running theme with a lot of Flash issues.

---

### Post by Wilbefast on 2009-11-23
I've got an Nvidia 8400GM I think, but as for getting what you paid for: Jaunty worked really well for me after some configuration. I'm actually considering switching back again :-S

Apparently this is a 64 bit problem though, not a 9.10 one...

---

### Post by nullrend on 2009-11-23
> **Wilbefast said:**
> I've now followed about 12 different guides (no exaggeration) for getting flash to work on Karmic 64 bit and none of them, this one included, have helped. At best there's been no difference, but now trying to load a page with flash on it makes the firefox freeze and grey out for a minute or two, and then I have white boxes where flash objects should be.

I have disabled Shockwave Flash 10.0 r32 (the library I copied in lib64/mozilla/plugins) to stop this lag - now there are no boxes at all.

I'm worried that I've wiped and reinstalled flash so many times now that something has been broken somewhere along the way. At any rate I am no closer to fixing this problem.


I find it rather pathetic that Karmic won't run flash properly without a great deal of fiddling, and that even then you're not guaranteed for it to work.

I am in the same situation. Combined with multiple issues provoked by continued hare-brained handling of the PulseAudio implementation it makes Karmic quite the unworthy update.

I'm currently in the process of switching over to Debian. It's a pain in the ***, but at least I don't get stupidity shoved down my throat.

---

### Post by Wilbefast on 2009-11-23
> **nullrend said:**
> I am in the same situation. Combined with multiple issues provoked by continued hare-brained handling of the PulseAudio implementation it makes Karmic quite the unworthy update.

I'm currently in the process of switching over to Debian. It's a pain in the ***, but at least I don't get stupidity shoved down my throat.

Yeah, I've got the pulseaudio problem(s) too :S

I'm holding out for an update - probably should have known better than to upgrade so soon after release - nothing works perfectly just after release these days, commercial or not: it's a fact of life.

---

### Post by Wilbefast on 2009-12-04
I swapped to Kubuntu 9.10: funny thing is that flash works fine of Konqueror, just not Firefox :S

Really not sure why this would be...

---

### Post by Mr.Kappa on 2010-03-03
Just cleaned up old flash plugins and installed the 64bit native application.. Works perfectly!!:guitar:

Thanks guys!

---

