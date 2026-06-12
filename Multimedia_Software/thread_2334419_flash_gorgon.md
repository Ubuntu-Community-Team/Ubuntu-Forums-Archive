---
title: "flash gorgon?"
date: 2016-08-19
forum: Multimedia Software
---

### Post by maclenin on 2016-08-19
Flash does NOT run properly in google-chrome on a xubuntu 16.04.1 desktop installation.

Flash DOES run properly in google-chrome on a xubuntu 14.04.5 laptop installation.

google-chrome and flash versions and chrome://components/ and chrome://plugins/ configurations seem identical on the desktop (16.04) and laptop (14.04) installations.

google-chrome version:
52.0.2743.116 (64-bit)

flash version:
22.0.0.209

flash location:
/opt/google/chrome/PepperFlash/libpepflashplayer.so

pepper_flash version:
22.0.0.209

I have soldiered down the...
```
sudo aptitude install browser-plugin-freshplayer-pepperflash 
```
...and the...
```
sudo aptitude install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```
...starting with the...
```
sudo aptitude install adobe-flashplugin
```
...paths to no avail!

Thanks for any guidance!

NB: Flash (version: 11.2.202.632) DOES run properly in firefox (version: 48.0) on both the desktop (16.04) and laptop (14.04) installations.

---

### Post by maclenin on 2016-09-17
The issue remains the same with google-chrome version 53.0.2785.116 (64-bit).

Flash does **not** work (using bbc iplayer, for example) on the desktop 16.04.

Flash **does** work (using bbc iplayer, for example) on the laptop 14.04.

Thanks for any guidance!

---

### Post by &amp;KyT$0P# on 2016-09-17
In what way(s) exactly does it not work?

---

### Post by maclenin on 2016-09-18
Fair question.

When the "play" triangle over the video "start" image is clicked, a "load circle" spins, but in a stuttered, start - stop fashion. Video is eventually displayed, but also in a stuttered - stop - freeze - start - slide-show-like fashion.

Audio plays over top the stuttering video (seemingly) without issue.

Thanks for any thoughts!

---

### Post by &amp;KyT$0P# on 2016-09-18
> **maclenin said:**
> When the "play" triangle over the video 
What video?

Have you tried the latest Chrome beta or the Chromium in the Ubuntu package repositories?  If so, any different?

---

### Post by maclenin on 2016-09-19
Try this link - [http://www.bbc.co.uk/news/video_and_audio/video](http://www.bbc.co.uk/news/video_and_audio/video) - and you'll see the "play" triangle on the lower left corner of ANY video thumbnail - this problem affects ALL video (on this page, certainly)....

Not very hopeful re: beta - and am happy with google-chrome - so, will try to resolve the issue in this current configuration.

Happy to wait for updates to see whether problems are fixed when a "beta" is finally released....

One beta has already been released - see my trail above - since I first noticed the issue (after installing 16.04) - without difference!

Cheers!

---

### Post by Yellow Pasque on 2016-09-20
> **maclenin said:**
> google-chrome and flash versions and chrome://components/ and chrome://plugins/ configurations seem identical on the desktop (16.04) and laptop (14.04) installations.

How about chrome://gpu and chrome://flags ?

> I have soldiered down the...  ...paths to no avail!

Flash is built into Chrome rather than an external plugin. None of those commands are relevant to Chrome (though you need pepperflash for chromium). Speaking of chromium, does it exhibit the same behavior?

---

### Post by maclenin on 2016-10-10
I have yet to "diff" the (google-) chrome: //gpu and //flags (between laptop and desktop) - however, the issue persists with google-chrome version 53.0.2785.143 (64-bit).

...and - alas - chromium-browser version 53.0.2785.143 (64-bit) exhibits the same (undesirable) behavior:

> When the "play" triangle over the video "start" image is clicked, a "load circle" spins, but in a stuttered, start - stop fashion. Video is eventually displayed, but also in a stuttered - stop - freeze - start - slide-show-like fashion.

Audio plays over top the stuttering video (seemingly) without issue.

---

### Post by maclenin on 2016-10-15
*The issue* persists in google-chrome version 54.0.2840.59 (64-bit)
*The issue* persists in chromium-browser version 53.0.2785.143-0ubuntu0.16.04.1.1254

**The issue:**
> **maclenin said:**
> When the "play" triangle over the video "start" image is clicked, a "load circle" spins, but in a stuttered, start - stop fashion. Video is eventually displayed, but also in a stuttered - stop - freeze - start - slide-show-like fashion.

Audio plays over top the stuttering video (seemingly) without issue.

**Possible clue?**

The following appears in the terminal after running the browser from the terminal, attempting to play video and then closing the browser:
```
$ **google-chrome**
A Parser-blocking, cross-origin script, http://service.maxymiser.net/cdn/mbbccoUK/js/mmcore.js, is invoked via document.write. This may be blocked by the browser if the device has poor network connectivity.
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED
$
```
```
$ **chromium-browser**
A Parser-blocking, cross-origin script, http://service.maxymiser.net/cdn/mbbccoUK/js/mmcore.js, is invoked via document.write. This may be blocked by the browser if the device has poor network connectivity.
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED
Vector smash protection is enabled.
$
```

Thanks, again, for any thoughts!

---

### Post by maclenin on 2016-11-21
The issue is now [SOLVED] in google-chrome version 54.0.2840.100 (64-bit)
The issue is now [SOLVED] in chromium-browser version 53.0.2785.143 (64-bit)

The resolution seems to be related to a 'hardware acceleration' bug - both of which I happened upon [here]("http://askubuntu.com/questions/583806/about-chrome-page-loading-issue?noredirect=1&lq=1") while investigating google-chrome and chromium-browser generally sluggish performance (i.e. slow page loads).

The solution resolved both the slow page load and video playback issues.

---

