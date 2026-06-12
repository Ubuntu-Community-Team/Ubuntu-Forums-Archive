---
title: "Ubuntu 64 bit Flash issue"
date: 2010-01-26
forum: Multimedia Software
---

### Post by pepsifx357 on 2010-01-26
So I'm glad they've made it to where most of the flash issues such as studdering are gone, however some flash pages and, of course, youtube are still glitchy. You can't click inside the imbedded flash.  It gets really annoying after a while.  You can't click pause without first clicking inside of the imbedded player and hitting the space bar.  You can't choose between low quality and HD and you certainly can't make the video full screen or change the volume level.  I've been using the desktop zoom function to alleviate this problem.  I have also visited a few web pages built completely in flash where you can't click anything.  Flash games are also affected by this problem.

Does anyone else suffer from this?  And if so, has anyone found a solution?

---

### Post by adam814 on 2010-01-26
Have you tried the 64-bit flash alpha refresh?  I use it without problems on YouTube/Vimeo/Google Video.  Hulu has issues with it, but almost everything else works.

---

### Post by pepsifx357 on 2010-01-26
Wow, thanks for the quick reply.  No, I haven't tried that.  I just got through reinstalling the package and I though that fixed it, until I watched a few YT videos and it started back up again.  Where is the package that you are talking about located?

---

### Post by adam814 on 2010-01-26
[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by HappyFeet on 2010-01-26
First, uninstall the flash you have. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

---

### Post by pepsifx357 on 2010-01-27
It works.  Only time will tell if it fixed the problem.  Many thanks to you guys.

---

### Post by pepsifx357 on 2010-01-27
still working great, I think that fixed it!  Thank you again.

---

### Post by pepsifx357 on 2010-02-03
Update:

The flash was working for a few days.  Now everything is broken.  If I use the flash solution presented in this thread, flash videos loose sound after while ```
sudo /etc/init.d/alsa-utils restart
``` does not fix the problem.  I uninstalled it and reverted back to the synaptic flash installer.  Now, not only can I not click inside flash content, but the videos loose sound, pause, are choppy, and I can't find a way to watch videos.  I've tried using a different browser, "Opera;" same thing happens.

---

### Post by adam814 on 2010-02-03
Hmm...I haven't run into that problem.  At least I haven't yet.

One difference I notice is that I have mine installed in /usr/lib/mozilla/plugins as well as /usr/lib64/mozilla/plugins, but I don't see why that should make a difference (at least if it worked for a while).

Regarding the sound problem:
Could one of your channels be muted?  It might be worth running alsamixer to check.

---

### Post by pepsifx357 on 2010-02-03
There's nothing wrong with the sound.  As soon as I quit firefox, I get the drum roll asking me if I want to save.

---

### Post by TBABill on 2010-02-03
Have you tried using Swiftfox? It is modified to various processors (Intel and AMD) so you download and install the correct one. I am currently using Mandriva and Flash is almost flawless with Swiftfox while it is a bit more glitchy and slow to scroll in Firefox. Chromium is a bit better than Firefox, but Swiftfox is awesome so far.

---

### Post by dralokyn on 2010-02-03
i'm having similar problems with 9.10 64-bit. the most aggravating part is that it isn't consistent. sometimes i can pause a video, sometimes not. mostly, though, i can't use anything that does flash unless it's passive. i've tried the things described in this thread so far, but nothing really works longer than one session of firefox.

---

### Post by HappyFeet on 2010-02-03
> **dralokyn said:**
> i'm having similar problems with 9.10 64-bit. the most aggravating part is that it isn't consistent. sometimes i can pause a video, sometimes not. mostly, though, i can't use anything that does flash unless it's passive. i've tried the things described in this thread so far, but nothing really works longer than one session of firefox.

First, uninstall the flash you have. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

---

### Post by pepsifx357 on 2010-02-04
Swiftfox....hmmm.  I shall try.

edit:  Very speedy. However, I'm having trouble installing the adobe flash.  I tried the normal method and it doesn't seem to work.  I noticed in the lib/swiftfox/plugins folder, that flash was already in there.  Why isn't it working?

Going to tools -> Addons -> plugins -> plugincheck shows no plugins installed.  Both lib and lib64 directories have plugins in them.

Edit:  Turns out swoftfox is a 32bit program and wasn't able to work with the already installed 64 bit flash.  I deleted the flash and downloaded the 32 bit flash 10 from adobe and it works now.  Well see how long it lasts this time.

Edit:  No dice.  5 minutes after watching youtube videos the sound has now started to cut off again.  Same problem.  I'm running out of options here.  There must be something installed, or something running that is causing this.  I don't think it is flash that is causing it.

---

### Post by pepsifx357 on 2010-02-05
I uninstalled a few things, but still nothing fixed it.

---

### Post by adam814 on 2010-02-05
Hmm...what add-ons are you using with Firefox?

Have you tried creating a new profile?
[http://support.mozilla.com/en-US/kb/Managing+profiles#Starting_the_Profile_Manager](http://support.mozilla.com/en-US/kb/Managing+profiles#Starting_the_Profile_Manager)

---

### Post by pepsifx357 on 2010-02-05
Add Ons

Download Helper
Download Status Bar

---

### Post by llawwehttam on 2010-02-05
I have been using 64-bit flash since karmic was released and I have had no problems. Your problems may not be related to the flash plugin. Could possible be to do with graphics/sound drivers?

---

### Post by Foxcow on 2010-02-05
> **pepsifx357 said:**
> I uninstalled a few things, but still nothing fixed it.



-Open Ubuntu Software Center

-Type "flash" into search field.  With the exception of Ubuntu Restricted Extras, remove all installed flash plugins; they are all garbage.

-Do this:

```

sudo apt-get clean && sudo apt-get autoremove

```

Then get the 64bit flash file.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Right click it and extract here. You will be left with libflashplayer.so file. Put the libflashplayer.so file in your home folder.

Then:
```


sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins

```
Make sure to put your name where I wrote your_user_name.

Restart firefox if open.

---

### Post by pepsifx357 on 2010-02-05
> **llawwehttam said:**
> I have been using 64-bit flash since karmic was released and I have had no problems. Your problems may not be related to the flash plugin. Could possible be to do with graphics/sound drivers?

You might be on to something there.  I had a professional sound card installed not too long ago that I have recently taken out.  How would I remove that driver, or would I have to?  Come to think of it, I might know the problem.  I'm running the RT kernel.  You think that might be it?

As for video, I've got an Nvidia 8800GTS  nothing special.

---

### Post by adam814 on 2010-02-05
> **llawwehttam said:**
> I have been using 64-bit flash since karmic was released and I have had no problems. Your problems may not be related to the flash plugin. Could possible be to do with graphics/sound drivers?

That's what I'm starting to think.  I haven't had any of those issues and I've been using the 64-bit flash alpha since it's been out (at least since Intrepid).

---

### Post by pepsifx357 on 2010-02-05
I booted up in the normal kernel.  It still skips every now and then, but I haven't heard the sound cut off yet.  Do you get skipping?

---

### Post by pepsifx357 on 2010-02-07
Ok, so for the record, DO NOT use flash with 64 bit Ubuntu Real Time Kernel!

---

### Post by TBABill on 2010-02-08
When I mentioned Swiftfox I was using Mandriva and the version of Firefox I was running was 3.6. When I downloaded Swiftfox it was also 3.6 so there was no problem and it was very fast.
 
However, I decided to give the fix threads a try for 64 bit flash and it runs great now on my machine. However, Firefox is nowhere near as fast as Swiftfox, and that's where my problem began. I wanted to stick with the repositories so I was not using Firefox 3.6, but the download of Swiftfox WAS 3.6....and that's the compatibility problem I had with plugins. They didn't work with Swiftfox and I was not really wanting to get Firefox outside the repository because I was unsure of update issues.
 
Question: Is there a trustworthy repository (and key) I can add that includes the latest Firefox version? If so, the issue with Swiftfox will go away and I can just reinstall it.

---

### Post by VertexPusher on 2010-02-08
If you take a closer look at the system requirements of the Adobe Flash plugin (both 32 and 64 bit versions), you'll see that the plugin uses ALSA. Not PulseAudio, OSS, Esound or what-have-you, but plain ALSA. The drop-outs and glitches you experience are caused by a plugin that routes audio from ALSA client applications to the PulseAudio daemon.

If you remove PulseAudio, audio playback in all applications, including Flash, will be glitch-free. You can uninstall PulseAudio by entering the following two commands in a terminal window:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```
To get PulseAudio back, enter this:
```
sudo apt-get install ubuntu-desktop
```
Using the above commands, you can switch back and forth between PulseAudio and plain ALSA. Compare and see for yourself which setup works better.

---

### Post by sleepee on 2010-02-22
> **VertexPusher said:**
> If you take a closer look at the system requirements of the Adobe Flash plugin (both 32 and 64 bit versions), you'll see that the plugin uses ALSA. Not PulseAudio, OSS, Esound or what-have-you, but plain ALSA. The drop-outs and glitches you experience are caused by a plugin that routes audio from ALSA client applications to the PulseAudio daemon.

If you remove PulseAudio, audio playback in all applications, including Flash, will be glitch-free. You can uninstall PulseAudio by entering the following two commands in a terminal window:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```
To get PulseAudio back, enter this:
```
sudo apt-get install ubuntu-desktop
```
Using the above commands, you can switch back and forth between PulseAudio and plain ALSA. Compare and see for yourself which setup works better.


well, i finally decided to be a man and set aside my fear of removing PA.

and it works!!! well, at least so far...
the only thing i miss.... well, the volume control.
i can't control the volume control from the applet from the panel at the top, nor from the keyboard multimedia keys/slider.
i tried looking for something in the Ubuntu Software Center, but i couldn't find anything..
also when i go to System -> Preferences -> Sound, nothing happens.  nothing pops up...
i kinda want to take away some system sounds, like minimizing windows sounds, opening apps sounds, etc...
any ideas???

anyway, thanx for the workaround... so far it's working great..
if anything happens, i'll be sure to let you guys know..

Edit:
mic doesn't respond... tried in cheese and sound recorder.
do i need to install something else to make alsa work with the mic??

---

### Post by Baneblade on 2010-02-22
The 64bit alpha works fine for me. Only issue I have noticed is with Zattoo. It doesn't seem to detect the alpha, so I have had to revert back to forcing the stable 32bit release instead. Not a very clean solution, but it seems viable in the mean time while we wait for Adobe to pull their finger out and give us a proper stable pack.

---

### Post by sleepee on 2010-02-22
> **sleepee said:**
> well, i finally decided to be a man and set aside my fear of removing PA.

and it works!!! well, at least so far...
the only thing i miss.... well, the volume control.
i can't control the volume control from the applet from the panel at the top, nor from the keyboard multimedia keys/slider.
i tried looking for something in the Ubuntu Software Center, but i couldn't find anything..
also when i go to System -> Preferences -> Sound, nothing happens.  nothing pops up...
i kinda want to take away some system sounds, like minimizing windows sounds, opening apps sounds, etc...
any ideas???

anyway, thanx for the workaround... so far it's working great..
if anything happens, i'll be sure to let you guys know..

Edit:
mic doesn't respond... tried in cheese and sound recorder.
do i need to install something else to make alsa work with the mic??


never mind.  i ran alsaconf and now the keyboard volume control and sound preferences work....
the mic works.. sort of...when i record, the playback sounds scratchy, but it works
now i just gotta find a way to configure movie player to play sounds...

---

### Post by sleepee on 2010-02-23
ok... i take it back... after a bit more testing..
it didn't work for me...
it's weird, because when i first did it, it worked fine... then i ran alsaconf, rebooted, and i had the same problem again...
oh well..
:(

---

