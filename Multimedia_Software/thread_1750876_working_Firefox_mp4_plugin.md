---
title: "working Firefox mp4 plugin?"
date: 2011-05-06
forum: Multimedia Software
---

### Post by chconnor on 2011-05-06
Hi - Firefox 4.0.1 on 11.04, radeon driver for an older ATI card in a Dell Inspiron 6000 laptop... I'm fed up with slow flash on linux and was exploring the FlashVideoReplacer plugin.

Unfortunately, I can't seem to find an mp4 plugin for Firefox that works.

VLC seems to be broken. I get the error described at these links:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/722690](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/722690)
[http://www.walecha.net/content/buggy-vlcs-mozilla-plugin](http://www.walecha.net/content/buggy-vlcs-mozilla-plugin)

The net seems weirdly silent about that issue.

Kaffeine plugin doesn't work for me (at least for a youtube mp4).

The Quicktime/totem plugin doesn't work.

When I set the plugin to launch a separate player (namely VLC) it doesn't work because the link, I assume, needs some cookie context in order to work properly.

... so now I'm stuck with flash again.

I did try the html5 version of youtube, which worked (except for full screen) but used almost as much CPU, which says to me that maybe this is more about my CPU than flash anyway, but I wanted to give another plugin a try...

Thanks for any tips!

---

### Post by lovinglinux on 2011-05-06
Hi, 

I am the developer of FlashVideoReplacer.

The recommended plugin to use with my extension is gecko-mediaplayer.

Totem works if you set the mime type in the extension preferences to x-mplayer2.

Although the standalone VLC player is one of the best, the plugin never worked for me. I don't recommend it.

About the cookie issue, that only affects YouTube. I am still working on this issue. 

BTW, I have released a new version today, to solve changes in the YouTube site that broke the extension. Make sure you have version 2.1.9. Even better, get the latest version from the Beta Channel (2.1.10pre). It is updated as soon as I receive reports that a site no longer works and since the Beta Channel doesn't need to go through Mozilla review process, it is updated more frequently.

About html5, it also uses too much CPU on my machine.

The problem is not your hardware, but it helps to have powerful CPU and video card. The main issue with flash is that it can't use the xv output like gecko-mediaplayer and totem. I don't know why the html5 player also uses too much CPU, but could be the browser fault.

I also recommend that you install and run my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension to upgrade flash and apply some performance tweaks.

Let me know if you need further assistance.

Cheers

---

### Post by handy on 2011-05-06
**@lovinglinux:** Hi, this is the first I've heard of your great add-on FlashVideoReplacer. I just installed the beta version on my Arch 64bit machine running Firefox 4.0.1, & it allowed me to watch vids that I've had Bookmarked for ages, though have been unable to view recently for whatever strange Flash related reason. (I could previously view some but not others, now I can view all I tested. :))

So thanks very much for making it so easy for me to escape these Flash problems, & to be able to see these vids that are of value to me; their quality is great - they look fantastic. =D>

If you would like to email me your BSB & Account number I'll send you a little money. I don't use Paypal.

---

### Post by lovinglinux on 2011-05-06
> **handy said:**
> **@lovinglinux:** Hi, this is the first I've heard of your great add-on FlashVideoReplacer. I just installed the beta version on my Arch 64bit machine running Firefox 4.0.1, & it allowed me to watch vids that I've had Bookmarked for ages, though have been unable to view recently for whatever strange Flash related reason. (I could previously view some but not others, now I can view all I tested. :))

So thanks very much for making it so easy for me to escape these Flash problems, & to be able to see these vids that are of value to me; their quality is great - they look fantastic. =D>

You are welcome.

> **handy said:**
> If you would like to email me your BSB & Account number I'll send you a little money. I don't use Paypal.

Don't worry. I am glad it makes you happy. :-)

---

### Post by chconnor on 2011-05-06
Brilliant, thanks for the reply. The gecko mediaplayer plugin did the trick. I can see 720p again on my computer. :-) Must have missed/ignored the suggestion when I was reading up on the add-on.

$5 and 5-star review just sent your way. Keep it up. :-)

Feature requests/notes:

- the middle-click disable of FVR via the button is great, but the icon barely changes color (and doesn't change shape) so it's hard to tell that anything happened. Might want to also add a "disable"/"enable" option in the button drop-down in case people don't guess the middle click functionality (can Mac users even middle click at all?).

- I like that I can choose the embed/tab/window/standalone option in the window before playing. How about also being able to select the media quality/type, and maybe other options as well? I frequently need to change media quality depending on how cranky my computer is at the moment, and having to go into the prefs to do it is kind of a pain.

- tool-tip explanations of the prefs when hovering (or similar) would be helpful (e.g. is it setting the mime type reported to the plugin but not of the video itself?)

Bravo,
-c

---

### Post by lovinglinux on 2011-05-06
> **chconnor said:**
> Brilliant, thanks for the reply. The gecko mediaplayer plugin did the trick. I can see 720p again on my computer. :-) Must have missed/ignored the suggestion when I was reading up on the add-on.

$5 and 5-star review just sent your way. Keep it up. :-)



Thank you very much.

I don't know if Mac users can middle click. Never thought about that. :oops:

> **chconnor said:**
> - tool-tip explanations of the prefs when hovering (or similar) would be helpful (e.g. is it setting the mime type reported to the plugin but not of the video itself?)

Implemented!

> **chconnor said:**
> - I like that I can choose the embed/tab/window/standalone option in the window before playing. How about also being able to select the media quality/type, and maybe other options as well? I frequently need to change media quality depending on how cranky my computer is at the moment, and having to go into the prefs to do it is kind of a pain.

Implemented via toolbar icon menu!

> **chconnor said:**
> - the middle-click disable of FVR via the button is great, but the icon barely changes color (and doesn't change shape) so it's hard to tell that anything happened. Might want to also add a "disable"/"enable" option in the button drop-down in case people don't guess the middle click functionality (can Mac users even middle click at all?).

Implemented. Not exactly what you want, but when viewing a video page, if you toggle the extension status via middle-click the page will reload. This only works for the active tab, but can be handy if you want to easily watch a video with flash that has already been replaced or replace a video quickly, if the extension is disabled.

Version 2.1.10pre1 available in the Beta Channel.

---

