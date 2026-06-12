---
title: "Spotify Linux Preview, local files codec missing?"
date: 2010-08-30
forum: Multimedia Software
---

### Post by LarsEriksson on 2010-08-30
Im using spotify for Linux Preview, importing of local files is working now, but i can not play them.

I get this error message:
"There is a problem with the sound decoder. Spotify can't play music"


Soo... what codec am i missing?
I can play those mp3-files in other programs(Totem, Rhytmbox) with no problems at all.

---

### Post by peakshysteria on 2010-09-06
Same problem at my end. Imported my local library. Now it want play any songs which is in my library (212 GB).

---

### Post by peakshysteria on 2010-09-09
*bump*

---

### Post by peakshysteria on 2010-09-14
*bump*

---

### Post by peakshysteria on 2010-09-15
*bump*

---

### Post by GH68 on 2010-10-30
Spotify still claims it is unsupported, but maybe they have something coming up since obviously the functionality has been changed?

---

### Post by UltraAnders on 2011-04-14
Still isn't sorted, if you haven't already, please register as having the issue here: [http://getsatisfaction.com/spotify/topics/ubuntu_lucid_spotify_linux_preview_local_files_problem_with_sound_decoder](http://getsatisfaction.com/spotify/topics/ubuntu_lucid_spotify_linux_preview_local_files_problem_with_sound_decoder). Cheers.

---

### Post by hyperandy on 2011-10-27
Anyone find a solution, same problem here.

---

### Post by GH68 on 2011-10-27
For me it just works on two computers running Ubuntu although Spotify still claims it is unsupported. Have you tried downloading the latest version, for me it did not work before.

---

### Post by beew on 2011-10-27
Why do you  want to use that piece of drm crap? Installing it  removes packages with enriched contents to read restricted formats and install the vanilla ones (like removing libavcodec-extra and installing libavcodec) so your multimedia is crippled.

If you must use it get the Windows version and use it in  WINE so at least it doesn't mess up your system.

---

### Post by hyperandy on 2011-10-27
Found a solution here.  Yes DRM is horrible but I buy music like crazy and I am pretty sick of organizing the hundreds of gigs myself.Spotify fills my music void. [http://getsatisfaction.com/spotify/topics/local_music_support_wont_works_if_latest_libavcodec_dev_package_ffmpeg_is_installed](http://getsatisfaction.com/spotify/topics/local_music_support_wont_works_if_latest_libavcodec_dev_package_ffmpeg_is_installed)

---

### Post by GH68 on 2011-10-27
Running Spotify under Wine is better in many ways, also quicker and using less memory. The only problem for me is that the most recent Windows version crashes at start up, and this seems to be a problem I share with man other users.

---

### Post by shantiq on 2011-10-28
good tip
plays swimmingly under wine altho frankly with moronic ads every 3 tunes not sure it is worth the trip     160k ogg is the output which is not high audio but decent

good to check a new band or listen to six hour of Hendrix legally without having to bankrupt yourself  :KS

---

### Post by WonderStivi on 2011-10-28
There's a step-by-step solution in this thread, if anyone should still need it:
[http://ubuntuforums.org/showthread.php?t=1870376](http://ubuntuforums.org/showthread.php?t=1870376)

---

### Post by sbourdelais on 2011-11-18
> **hyperandy said:**
> Found a solution here.  Yes DRM is horrible but I buy music like crazy and I am pretty sick of organizing the hundreds of gigs myself.Spotify fills my music void. [http://getsatisfaction.com/spotify/topics/local_music_support_wont_works_if_latest_libavcodec_dev_package_ffmpeg_is_installed](http://getsatisfaction.com/spotify/topics/local_music_support_wont_works_if_latest_libavcodec_dev_package_ffmpeg_is_installed)

worked for me, thanks. would rather do it that way than through Wine, i've had trouble with wine.

---

### Post by fazeoff on 2011-11-18
> **WonderStivi said:**
> There's a step-by-step solution in this thread, if anyone should still need it:
[http://ubuntuforums.org/showthread.php?t=1870376](http://ubuntuforums.org/showthread.php?t=1870376)

Thanks, I have been experiencing the same problem....

will try this method...

---

### Post by i3lackh3art on 2012-02-17
The spotify preview version is WAY better than running under wine. First off, if installed CORRECTLY, It decreases the number of processes running, therefore its faster. No playonlinux or wine in the background just waiting to crash as soon as you open it. Only thing is, you gotta PAY for spotify to get the desired experience from the non-free stable oneiric version (the one i use). works like wonders. And if it messes up, re-install. No problem. AHHHHHHHHHH linux, i love penguins.

---

### Post by GH68 on 2012-02-18
> **i3lackh3art said:**
> The spotify preview version is WAY better than running under wine. First off, if installed CORRECTLY, It decreases the number of processes running, therefore its faster. No playonlinux or wine in the background just waiting to crash as soon as you open it. Only thing is, you gotta PAY for spotify to get the desired experience from the non-free stable oneiric version (the one i use). works like wonders. And if it messes up, re-install. No problem. AHHHHHHHHHH linux, i love penguins.

So why was the Wine version much faster on my PC when I had both running? Now its history anyway since the Wine version crashes  on startup, so I have to rely on the native version which has a slow startup and behaves slower in general. It also always starts with error messages. Moreover, in contrast to the Wine version I cannot even resize the height of the window to fit on my 7 inch netbook screen which otherwise is the perfect music player for my stereo. Linux is nice, but Spotify unfortunately doesn't support it very well.

---

### Post by bdombro on 2012-03-15
This article was awesomely descriptive and worked perfect: [http://www.webupd8.org/2011/12/how-to-install-native-spotify-linux.html]](http://www.webupd8.org/2011/12/how-to-install-native-spotify-linux.html])

---

