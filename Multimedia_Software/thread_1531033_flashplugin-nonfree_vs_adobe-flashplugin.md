---
title: "flashplugin-nonfree vs adobe-flashplugin"
date: 2010-07-14
forum: Multimedia Software
---

### Post by Lucky75 on 2010-07-14
Hey,

I'm having some issues with my flash in 10.04. I just upgraded from 9.10 and had audio working fine. However, I had issues with flash and fullscreen where it would load on the wrong monitor and with the wrong aspect ratio/offset.

Now that I installed 10.04, flash seems to actually be working fine, loading on the correct screen, etc, but I don't have any audio! It turns out that I had *adobe-flashplugin *installed.

I then purged that and installed *flashplugin-nonfree*, and my sound works now, but it's back to the same fullscreen problems that I had before!!

Is there any way I can get audio working with *adobe-flashplugin*? Or fullscreen working with *flashplugin-nonfree*?

And how do I tell if I'm using *alsa* or *pulse*, and which one should I be using? Thanks for the help!

---

### Post by gandaran on 2010-07-14
> **Lucky75 said:**
> Hey,

I'm having some issues with my flash in 10.04. I just upgraded from 9.10 and had audio working fine. However, I had issues with flash and fullscreen where it would load on the wrong monitor and with the wrong aspect ratio/offset.

Now that I installed 10.04, flash seems to actually be working fine, loading on the correct screen, etc, but I don't have any audio! It turns out that I had *adobe-flashplugin *installed.

I then purged that and installed *flashplugin-nonfree*, and my sound works now, but it's back to the same fullscreen problems that I had before!!

Is there any way I can get audio working with *adobe-flashplugin*? Or fullscreen working with *flashplugin-nonfree*?

And how do I tell if I'm using *alsa* or *pulse*, and which one should I be using? Thanks for the help!
theres no deference between the two, they both install the same adobe flash plugin, the problem with adobe-flashplugin is if you downloaded the package from adobe.com it wont get updated if you don't download the package again with the new flash version, while flashplugin-nonfree gets updated every-time.

---

### Post by Lucky75 on 2010-07-14
Hmm, it's odd that my flash decided to go back to not working properly though,

I ran the following command(s):

```

sudo apt-get --yes purge swfdec-mozilla
sudo apt-get --yes purge mozilla-plugin-gnash
sudo apt-get --yes purge adobe-flashplugin
sudo apt-get --yes purge flashplugin-nonfree
sudo apt-get --yes purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo apt-get --yes install flashplugin-nonfree && sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so

```

Why would the video screen/position stop working all of a sudden, but the audio started working unless they were different?

---

### Post by lovinglinux on 2010-07-14
> **Lucky75 said:**
> Hmm, it's odd that my flash decided to go back to not working properly though,

I ran the following command(s):

```

sudo apt-get --yes purge swfdec-mozilla
sudo apt-get --yes purge mozilla-plugin-gnash
sudo apt-get --yes purge adobe-flashplugin
sudo apt-get --yes purge flashplugin-nonfree
sudo apt-get --yes purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo apt-get --yes install flashplugin-nonfree && sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so

```

Did it stopp after running those commands?


> **Lucky75 said:**
> Why would the video screen/position stop working all of a sudden, but the audio started working unless they were different?

They are not different. Sometimes re-installing flash fixes the missing audio issue. I don't know why.

---

### Post by Lucky75 on 2010-07-15
> **lovinglinux said:**
> Did it stopp after running those commands?




They are not different. Sometimes re-installing flash fixes the missing audio issue. I don't know why.

Yeah, the positioning problem came back after running the above commands, but the audio was fixed :s

---

### Post by lovinglinux on 2010-07-15
> **Lucky75 said:**
> Yeah, the positioning problem came back after running the above commands, but the audio was fixed :s

Remove flashplugin-nonfree and install adobe-flashplugin again. Check if you get proper display and no sound then try [this](http://ubuntuforums.org/showpost.php?p=9131334&postcount=1).

---

### Post by Lucky75 on 2010-07-15
Hmm,no, now the display still isn't proper again. It only changed after I ran those commands above though..how can that be? Some settings somewhere?

---

### Post by lovinglinux on 2010-07-15
> **Lucky75 said:**
> Hmm,no, now the display still isn't proper again. It only changed after I ran those commands above though..how can that be? Some settings somewhere?

Probably. Unfortunately, I don't have multiple displays, so I don't know how to troubleshoot that.

---

### Post by Lucky75 on 2010-07-19
up

---

