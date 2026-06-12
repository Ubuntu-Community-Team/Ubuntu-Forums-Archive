---
title: "HOW-TO:  Getting the WinTV-HVR 950 to work WITH AUDIO in ANALOG Mode"
date: 2008-04-22
forum: Mythbuntu
---

### Post by punkrawker82 on 2008-04-22
I was building a MythTV box for a friend and was having issues with the AverMedia M-150 D they had installed.  I had audio and video working in analog with that card, but the framerate was horrible.  It was absolutely unwatchable.  My friend informed me he also had a Hauppauge WinTV-HVR 950 I could try, so...

[LIST]
[*]I plugged it in

[*]Performed a fresh install of Mythbuntu 7.10

[*]Followed the Fiesty Fawn instructions located here:

[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html")
[/LIST]

And I couldn't get audio to work with analog using the WinTV-HVR 950.  So, I went back to a site I had looked at for the Avermedia M-150 D which discussed the index of audio devices located here:

[http://mythtv.org/wiki/index.php/PCI_TV_audio]("http://mythtv.org/wiki/index.php/PCI_TV_audio")  

I remembered having to manually set my cx88 device to an index of 1 when working with the avermedia tuner.  But in the case of the WinTV-HVR 950 I needed the EM28xx to have an index of 1, so...

I ran the command 

sudo cat /proc/asound/cards

Sure enough, my audigy sound card had index 0 (which it should), the cx88 had index 1, and the EM28xx had an index of 2.  I needed to flip the cx88 and EM28xx so that the EM28xx has an index of 1 and the cx88 has an index of 2.  From the audio site it stated the EM28xx uses the snd-usb-audio module.  You can control what index an audio device receives by manually editing /etc/modprobe.d/alsa-base

I ran the command

sudo nano /etc/modprobe.d/alsa-base

The WinTV-HVR 950 uses the snd-usb-audio module.  So I located the line:

options snd-usb-audio index=-2

and changed the index of -2 to an index of 1.  I also changed the index of my cx88 based avermedia tuner from an index of -2 to an index of 2.  I then saved my chnges and rebooted.

After I rebooted, I ran the mythtv backend once again and made sure the setting for my Audio Device within the Analog Capture Card Setup was set to /dev/dsp1 as we set the EM28xx/snd-usb-audio to use index 1.

In my MythTV frontend General settings I'm using the ALSA Default.

There you have it, the WinTV-HVR 950 setup in analog with working Audio and Video.:-D

Let me know if it works for you guys!

---

### Post by raphy3 on 2008-06-15
This thread probably isn't checked anymore, but could you give some more detailed instructions on how you did this?
For some reason on mine I only have the one sound card in my system. I don't have a /dev/dsp2 for my HVR 950, even though analog video works fine; no sound whatever I try.

---

### Post by punkrawker82 on 2008-07-22
> **raphy3 said:**
> This thread probably isn't checked anymore, but could you give some more detailed instructions on how you did this?
For some reason on mine I only have the one sound card in my system. I don't have a /dev/dsp2 for my HVR 950, even though analog video works fine; no sound whatever I try.

I still check from time to time :)

In your case your normal sound card should be set to index 0, and your HVR 950's sound should have an index of 1.

Run:

```
sudo cat /proc/asound/cards
```

And determine if this is the case.  You should see your normal sound card and your HVR 950's sound found.  It has been a while and I don't have the system to check as it was my friends, but the HVR 950's sound should be something like "EM28xx".  Run:

```
sudo nano /etc/modprobe.d/alsa-base
```

Find the line for the HVR 950 sound module.  It should be:

```
options snd-usb-audio index=-2
```

Change this line so that it becomes:

```
options snd-usb-audio index=1
```

Reboot and then run the mythtv backend once again and make sure the setting for my Audio Device within the Analog Capture Card Setup is set to /dev/dsp1 since you set the EM28xx/snd-usb-audio to use the index of 1.  

Basically make sure the /dev/dsp number in MythTV is set to the same number as the index you manually set in /etc/modprobe.d/alsa-base.  When I didn't manually define the index the different sound devices would be assigned random indexes each boot.  The -2 that they have by default seems to be like a first come first serve basis.

It should work fine with MythTV frontend General settings set to use ALSA Default.

I hope that helps :)

---

