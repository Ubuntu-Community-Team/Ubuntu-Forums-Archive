---
title: "[SOLVED] audacity crashes w/ zoom h4 audio i/o"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by scholzilla on 2007-12-24
I just bought this Zoom H4 recorder that seems pretty nifty. I installed audacity cause it's touted as user friendly, and I have no problem importing files stored on the H4's soundcard (via usb) to audacity for editing. The problem is that when I try to record (audacity capturing H4's mics), audacity simply crashes. Do I need some sort of driver to handle real-time audio input with audacity? I couldn't scare up anything on the audacity web site that answers this.

I have about a day to test drive this H4 before I can't return it, so quick responses are appreciated.

---

### Post by gruhland on 2008-01-12
I had no problems. You have to tell Audacity which input device to use. Connect the Zoom H4 to the computer (use the connect menu in the h4 to tell that it should work as audio i/o device and NOT as card reader). Then start Audacity and do the following
Menu  Edit --> Settings --> Audio I/O --> ALSA : usb h4  (or something like that)
That worked fine. If you look now in Audacity. There is a small microphone in the upper part. Click on the down arrow close to the right of the micro --> activate display.
Now you should see an input signal of the H4.

Good luck
Götz

---

### Post by scholzilla on 2008-01-12
Danke sehr! That worked well. For the benefit of those with my version of audacity, the menu options to select are Edit --> Preferences ---> Audio I/O. Under playback I used ALSA: HD ATI SB and under record I used the setting mentioned above. Now I'm very happy!

macht's guet

---

### Post by gruhland on 2008-01-13
Fine, that it's working . Sorry for the bad translation but I have installed the german version of audacity and it's always the question how the menu points will be translated. In this case it's not SETTINGS but PREFERENCES.

I was impressed how easy it was to connect the H4 to Ubuntu Gutsy. No additional drivers, no editing in any configuration files. Just "out of the box". And until now I'm not very experienced neither with Gutsy nor with the H4 which I got three weeks ago.

Have fun!
Regards
Götz

---

