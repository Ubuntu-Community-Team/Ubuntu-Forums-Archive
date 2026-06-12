---
title: "Sound seems very quiet"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Novacaine on 2007-04-30
Hey all,

Just finished installing Ubuntu Feisty over the weekend and starting to iron out some of the wrinkles that have cropped up. My main problem at the moment is the audio seems way too quiet compares to running through Windows which leads me to believe it could be a driver issue or maybe I need to configure alsa/oss properly.

Also, this may be on the same point, I have a 5.1 setup but lack any sound from any speakers other than the front. After googling for the answer I found editing my ~/.asoundrc file was to be the answer, followed by setting the "Duplicate Front" setting in aslamixer on (As described[ here]("http://www.halfgaar.net/surround-sound-in-linux") and [here]("http://gentoo-wiki.com/HOWTO_Surround_Sound").)

Well that was the start of the problem, as I don't seem to have that option when I start alsamixer. and none of the configs that I found altered the sound at all (though to be honest, I didn't think they would as they were for different setups).

So I have come in search for direction on where to look for a solution. My audio in built onto the motherboard [GA-M61VME-S2]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2381&ProductName=GA-M61VME-S2") and looks like it's a Realtek ALC883.

Any help would be great.

Thx

---

### Post by Novacaine on 2007-04-30
Ok, bit of an update.

After following the comprehensive guide [here]("http://ubuntuforums.org/showthread.php?t=205449") I still cannot find the "Duplicate Front" setting in alsamixer, nor is the sound playing on my subwoofer or rear & center speakers.

---

### Post by Foxblood on 2007-04-30
Bump

---

### Post by reclusivemonkey on 2007-05-04
I never had to mess around with any ~/.asoundrc file, just the plain old gnome mixer worked for me. Just tick the right boxes in "Preferences" and you should be good to go. I would delete the ~/.asoundrc file just in case, or at least change the name if the above method doesn't work.

---

### Post by Jugalator on 2007-05-08
I had the same problem, with a device running as  Realtek ALC883 (OSS Mixer).
It's the integrated audio device on a MSI P965 Platinum motherboard in my case.

I resolved the problem by running alsamixer from the command line, navigating with the left/right arrows to the PCM slider and pulling it all the way to 100% with the up/down keys. For some reason, this slider wasn't available in the Gnome volume UI. It was set at something like 0% and I only barely heard things when maxing out the slider in the Gnome UI before. Now it's similar to Windows' audio levels, leading me to believe PCM audio "should" really be at 100% by default.

---

### Post by Novacaine on 2007-05-10
Sorry it's been so long with me updating this - life got in the way.

> **reclusivemonkey said:**
> I never had to mess around with any ~/.asoundrc file, just the plain old gnome mixer worked for me. Just tick the right boxes in "Preferences" and you should be good to go. I would delete the ~/.asoundrc file just in case, or at least change the name if the above method doesn't work.

I don't see the screen you posted - is this using Gnome Alsa Mixer? That looks like it would fix my problem if I could find the tab :S

@Jugalator:

My motherboard is a Gigabyte, but it should essentially be the same. While the sound is audible, I would also like to replicate it to the rear speakers.

---

### Post by reclusivemonkey on 2007-05-10
> **Novacaine said:**
> Sorry it's been so long with me updating this - life got in the way.



I don't see the screen you posted - is this using Gnome Alsa Mixer? That looks like it would fix my problem if I could find the tab :S



Yes, just right click on the volume control in gnome and go to preferences.

---

### Post by Novacaine on 2007-05-21
^^ It doesn't bring up the same window. All I get is this

[IMG]http://img337.imageshack.us/img337/5382/screenshotvolumecontrolbb8.png[/IMG]

And if I click on Open Volume Control I get these:

[IMG]http://img337.imageshack.us/img337/295/screenshotvolumecontrolgw3.png[/IMG]
[IMG]http://img337.imageshack.us/img337/3962/screenshotvolumecontrolzx0.png[/IMG]

---

### Post by reclusivemonkey on 2007-05-22
Edit --> Preferences

---

### Post by Novacaine on 2007-05-22
Still no dice, Edit->Preferences brings up this window. Thanks anyways.

[IMG]http://img340.imageshack.us/img340/2013/screenshotvolumecontrolsz2.png[/IMG]

---

### Post by reclusivemonkey on 2007-05-22
What version of Ubuntu are you using?

---

### Post by Novacaine on 2007-05-22
Feisty - I was having issues with edgy(? v6) as it wasn't detecting my network or sound, but Feisty detected everything after install so I went with that.

I'm currently at work so if there is any in depth stuff you would like I'll have to post it in about 8 hours time :S

---

### Post by Der-3 on 2007-07-23
Hi.

I had the same problem. I made this to solve it : 
Follow this tutorial : [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

When last version of ALSA is installed, put this line in /etc/modprobe.d/alsa-base : 
```
options snd-hda-intel model=3stack-6ch-dig
```

Reboot your computer, you can now activate 5.1 sound thanks to "Channel mode".
[IMG]http://romain.dervaux.free.fr/divers/cap1.png[/IMG]
[IMG]http://romain.dervaux.free.fr/divers/cap2.png[/IMG]
[IMG]http://romain.dervaux.free.fr/divers/cap3.png[/IMG]

Hope it helps

---

