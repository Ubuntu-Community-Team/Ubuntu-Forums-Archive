---
title: "Volume Control Missing from Panel"
date: 2010-05-12
forum: Multimedia Software
---

### Post by UUU1 on 2010-05-12
I just want to point out I tried reseting my panel several times at which point it did reset everything except the volume control is still missing. Everything else is there.

I followed what was said here:
[http://ubuntuforums.org/showthread.php?p=9257307](http://ubuntuforums.org/showthread.php?p=9257307)

yes the volume control icon is still missing. I have no idea why it's not showing up for me. For the love of god please help.

---

### Post by congdonb on 2010-05-12
Here is what I did:

System >> Preferences >> right mouse click on Sound menu icon and then select "Add this launcher to panel"

Bill Congdon

---

### Post by leona on 2010-05-12
Hi

Have the same problem here, the icon use to be there in 8.04 but not in 10.04.
When you clicked on the speaker icon, you got a volume slider, the fix posted above just opens the sound dialogue, I'd like the volume slider back please.

---

### Post by dondiego2 on 2010-05-12
> **UUU1 said:**
> I just want to point out I tried reseting my panel several times at which point it did reset everything except the volume control is still missing. Everything else is there.

I followed what was said here:
[http://ubuntuforums.org/showthread.php?p=9257307](http://ubuntuforums.org/showthread.php?p=9257307)

yes the volume control icon is still missing. I have no idea why it's not showing up for me. For the love of god please help.


Right click an empty space on your panel.  Select 'Add to Panel'.
Pick 'Indicator Applet' from the list.

This will add the volume control and a mail/chat applet.

---

### Post by leona on 2010-05-12
ohh, would you look at that, wow now have icons back, lovely, thank you.

---

### Post by stevehaines on 2010-05-12
Great! The "indicator applet" was exactly what I was looking for . . . Happy again with Lucid and a panel volume slider. Thanks so much!:)

---

### Post by soh on 2010-05-26
Well I got the sound indicator, great.
But also I got an Mail indicator for Evolution (which I dont use)
And my Battery indicator is now taken over by this multi indicator (I cant remove this indicator without the battery indicator goes to).

What do I do if I want the Sound and the Battery indicator, but not the Mail indicator (as I use Thunderbird)?

Thanks.

---

### Post by gogolink on 2010-05-26
You can open a terminal and type:
```
sudo apt-get remove indicator-messages
```
Then make panels reboot:
```
killall gnome-panels
```

...and the little envelope is gone.
Found this here: [https://answers.launchpad.net/indicator-applet/+question/103911]("https://answers.launchpad.net/indicator-applet/+question/103911")
(Thanks to Jan-Christoph Borchardt)

---

### Post by soh on 2010-05-28
Thank a bunch.

---

### Post by ubun2warrior on 2010-05-28
Hey its very simple..
Just right click on the panel on which u like the sound panel to be. Then select add to panel. Then a new window opens. from there select indicator applet. i think that is just what u want.

---

### Post by pgn674 on 2010-05-30
If you have Indicator Applet loaded but it still doesn't have the volume icon, try making sure that indicator-sound is installed in Synaptic Package Manager.

---

### Post by ubeautu on 2010-05-31
> **pgn674 said:**
> If you have Indicator Applet loaded but it still doesn't have the volume icon, try making sure that indicator-sound is installed in Synaptic Package Manager.

Thanks, that advice fixed it for me - i lost the applet when I mucked around trying to delete pulse audio.

---

### Post by tenshikun12 on 2010-06-03
Hi,

I had sound in my system after uninstallung pulseaudio packages. However, the volume control disappeared (but the mail notifier was still there).

> **pgn674 said:**
> If you have Indicator Applet loaded but it still doesn't have the volume icon, try making sure that indicator-sound is installed in Synaptic Package Manager.

This made the volume control return, but sound works well only before I open google chrome. After opening it, some apps do play sound and some others don't, eg.
[LIST]
[*]youtube plays ok
[*]rythmbox does not play anything
[*]totem not only doesn't play sound, but progress bar does not move both for midi sound file and for a avi/flv video files (first snapshot still on screen).
[*]vlc plays the video (the same ones) without sound.
[*]beep command produces the beep (a strange one, but a beep anyway)
[/LIST]

Closing google chrome fixed all these problems, and if I open it with music playing, it keeps on. However, on opening youtube, with music on, the video in yt has no sound and sometimes does not move.

It looks as a flash issue, but I don't know what to do next. Any advice would be great. THanks everyone :)

---

### Post by Yellow Pasque on 2010-06-03
If you removed pulseaudio, you need to configure applications to use ALSA. This should do it for totem and rhythmbox:
```
sudo apt-get install gstreamer0.10-alsa
sudo apt-get remove --purge gstreamer0.10-pulseaudio
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosrc "alsasrc"
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink "alsasink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink "alsasink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink "alsasink"
```
You may need to log out before they take effect.

Also, the gnome packages from this ppa are helpful for gnome systems w/o pulseaudio: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by tenshikun12 on 2010-06-04
Hi,

Following Temüjin's instructions I got it to work, although I already had gstreamer.

Thanks ;)

---

### Post by efball3 on 2010-07-01
My volume control in the panel disappeared when I installed a new soundcard, a Asus Xonar DX.  This uses alsa instead of pulse.  I'm using Ubuntu 9.10

The "add to panel" menu has no volume control.

system -> preferences -> sound gets me a "waiting for sound system to respond" pop-up window.

sound works, the gnome-alsa-mixer works, but no convenient volume control, and no configuration tool for setting up the sound card (stereo, 5.1, etc).

I've been searching lots of places and tried more things than I  can remember.

---

