---
title: "No sound for Songbird or RhythmBox"
date: 2008-06-20
forum: Multimedia Software
---

### Post by Mijder on 2008-06-20
So...
Suddenly I am getting no sound when attempting to play songs or podcasts in Songbird.  Sounds still works with Totem, but not these other two programs.
Even VLC is playing the songs, but not these two.

---

### Post by zizzdude on 2008-06-20
yeah, I'm having the same problem. some reason, the track would not play at all.

---

### Post by Mijder on 2008-06-20
The track seems to playing.  The ticker ticks.  I'm just not hearing anything.

---

### Post by cozmicharlie on 2008-06-20
It is probably a problem with the pulse audio.  Some have been able to get sound back just by starting the app in the terminal.

---

### Post by papayaninja on 2008-06-20
This is the exact problem I'm having [here.]("http://ubuntuforums.org/showthread.php?t=826112")  I just installed VLC and it also works for me.  Starting them from the terminal does not help.

---

### Post by Mijder on 2008-06-20
Indeed, the terminal solution is a no go.

---

### Post by hanniph on 2008-06-24
Something similar here. After having installed system updates, Songbird refused to play mp3 anymore. Other players work fine. I have all necessary gstreamer libs installed. Also tried to reinstall Songbird, but that didn't help.

---

### Post by hanniph on 2008-06-29
The solution I found was to install gst-plugins-good (which can be found at [http://gstreamer.freedesktop.org/src/gst-plugins-good/]("http://gstreamer.freedesktop.org/src/gst-plugins-good/")) and set audio output to ALSA in gstreamer-properties. (run in terminal "gstreamer-properties")

---

### Post by math_phy on 2008-06-30
Another solution that worked for me was to enable the "hardy-proposed" updates in the update section and upgrade. I guess some problem with the old gst-plugins.

---

### Post by slugicide on 2008-07-01
I have this same problem with songbird.  I don't want to switch to alsa, and I already have "hardy proposed" enabled.

---

### Post by ellon on 2008-07-01
welcome to [www.38dugame.com](www.38dugame.com)!!!!!!!!!   the cheapest maple story mesos and the smooth fast delivery !!!!!
microsoft.public.windows.vista.games

---

### Post by slugicide on 2008-07-02
> **hanniph said:**
> The solution I found was to install gst-plugins-good (which can be found at [http://gstreamer.freedesktop.org/src/gst-plugins-good/]("http://gstreamer.freedesktop.org/src/gst-plugins-good/")) and set audio output to ALSA in gstreamer-properties. (run in terminal "gstreamer-properties")

This worked for me.  Thanks for the workaround.

---

### Post by papayaninja on 2008-07-02
I did both fixes and so am not sure which actually did it, but Songbird now works.  Banshee and Exaile and Listen are still broken, but Songbird is fine with me.  Thanks!

---

### Post by KillerKellerjr on 2008-09-09
I had the same problem, here is what I did to fix my issue and I believe it works for both. Go into the Ubuntu (8.04 for me) Audio Control Panel (System > Preferences > Sound) It should have a bunch of inputs and output, and a selector of how they should be routed (examples: CD Audio - Auto, PCM Sound - Auto). The "Autodetect" should be selected currently in all drop down menus. Go to each drop down and select your sound card instead of "Autodetect". If you are confused by which of the options is your sound card, try one, test it, and if it doesn't work, try another. Don't mess with the Sound Capture one as it's for a microphone.

Once I found the correct one Songbird worked like it should not only if I can get the RSS working then I have an iTunes replacement!

Hope that helps everyone out!

---

