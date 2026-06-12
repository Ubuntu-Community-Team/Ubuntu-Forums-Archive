---
title: "Logitech V20 USB Speakers don't work on Gutsy"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by vnetha on 2007-11-02
Hi,

I recently installed Gutsy on my old DELL OptiPlex GX280.
I got my internet working with great difficulty.
Then I tried to plug my Logitech V20 USB speakers.
Not only do they not work,
I think they're messing with my internet connection also.

The little blue light on top of the speakers glows.
And if I try to adjust volume, I get a screen increasing and decreasing volume.
but since I'm not getting any sound anyway, I can't tell if any of the buttons are working or not.

could someone please give some step-by-step instructions on how to get them working...


thanks,
Vivek.

---

### Post by sonofusion82 on 2007-11-02
Perhaps you could try these instructions. [http://www.michaeldolan.com/258](http://www.michaeldolan.com/258)

---

### Post by MrFSL on 2007-11-02
Click:

**System > Preferences > Sound**

Then adjust for your default sound output.

If the speakers are identified they should be listed.

---

### Post by vnetha on 2007-11-08
Ok, so i have Beep Media Player installed.
I am able to get the speakers to work if I change the settings within Beep itself.

but if I change my default preferences under Sytem->Preferences->Sound,
I see no changes. meaning, if i play something on lets say YouTube,
no sound comes out of the USB speakers.

does anyone know how to fix this problem?

Vivek.

---

### Post by MrFSL on 2007-11-08
Running Feisty.

Just blew the dust off an old set of Altec Lansing USB speakers and am noticing the same problem. They worked perfect in Edgy. When you plugged them in you would get a popup saying that they were detected and if you wanted to use them etc.

Nothing now. I can also configure and application that allows to use them, but adjusting the default preferences doesn't seem to work.

---

### Post by Angelbeast on 2007-11-19
I am having problems with my V20 speakers too...If i look in the sound prefs they are detected and selected but the sound still comes out of the built in speakers...i also notice that system sounds do come out of the usb speakers as well as the sound test noise...help *LOL*

---

### Post by flashm on 2007-12-15
Having the same issue myself... I have a pair of Logitech USB speakers that took me forever to get to work of Feisty. Looks like I'll have the same headache with Gutsy

---

### Post by flashm on 2007-12-15
WAIT!!!  I take it all back. From another forum I got:

       asoundconf list

Which gave me:

 NVidia
 Speaker

Then I ran:

       sudo asoundconf set-default-card Speaker

Turned up the volume and that was it! Done! 

I had already set everything in System -> Preferences -> Sound to ALSA and the default mixer card to the Logitech card. These USB speakers have a built in sound card that you need to point your system at.

All working now.

---

### Post by mbuller10 on 2008-01-20
Id been trying for 2 months to get my speakers to work with no avail, and here your idea worked for me in 5 minutes, omg, i praise you, you are my best friend

---

