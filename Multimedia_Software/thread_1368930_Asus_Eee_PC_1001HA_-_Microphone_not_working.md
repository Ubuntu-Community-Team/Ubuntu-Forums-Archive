---
title: "Asus Eee PC 1001HA - Microphone not working"
date: 2009-12-31
forum: Multimedia Software
---

### Post by Bernhard63 on 2009-12-31
Hi @ll,

I am a complete Linux Newbie but want to get away from MS. So I am running UNR V 9.10 on my Asus Eee PC 1001HA and I am quite fascinated. Besides WLAN (working now) and microphone everything worked right away.

My remaining problem is still the microphone. it simply does not work. Not the integrated mic and also not when I connect an external headset. I searched a number of forums but could not find a solution for my problem.

The netbook uses "Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)". Since I badly need the microphone for skype communication I hope that someone can help me to get this sorted out since I would really prefer to stay with Ubuntu rather than going back to Microsoft.

Thanks in advance for any help. As said, I am a newbie so I hope that there will be a simple solution since I am far away from being able to compile a Kernel or stuff like this :-)

To all of you all the best for the upcoming New Year

Thx Bernhard

---

### Post by Julita on 2010-01-04
Hi, Bernhard! I am so sad that your micro doesn't work...Since it works for me, please look at my screenshots of

```
alsamixer
```

[IMG]http://s40.radikal.ru/i090/1001/d1/66a7aee0306d.jpg[/IMG]
[IMG]http://s16.radikal.ru/i190/1001/64/1cc67ce1ed6d.jpg[/IMG]

Please make it the same as mine.

UPD: I have also adjusted the programme:

[IMG]http://s13.radikal.ru/i186/1001/b1/401a0224032b.png[/IMG]

---

### Post by Bernhard63 on 2010-01-05
Hi Julie, thanks for your help. I have tried this but in the first screen shot I only got 3 bars 100<>100   CAPTUR             Front Mi
<Front Mi>  100<>100
                  Capture              Input So

I do not get the bar "Digital"

Also in the second screenshot. You have a total 10 bars, I have 9. Again the bar "Digital" is missing.

Now when I go in Skype, I have behind "Microphone", "Speakers" and "Ringing" always "PulseAudio server (local)" and I cannot change this setting like you to HDA Intel or Default device.

No idea what I am doing wrong :-( :confused:

---

### Post by Julita on 2010-01-05
Bernhard, if you haven't removed pulseaudio, please do so by

```
sudo apt-get remove pulseaudio
```

because skype in most cases doesn't work with it. When you remove it, reboot your computer and go once more to the "sound devices" in skype; you will be able to choose more options.

As to bar "digital," it is the feature of Alsa. When you remove pulseaudio and make Alsa your default in

[[IMG]http://i081.radikal.ru/1001/9d/b109fcc293dbt.jpg[/IMG]](http://radikal.ru/F/i081.radikal.ru/1001/9d/b109fcc293db.jpg.html)


(in the upper row, third from the left) it should appear.

---

### Post by Bernhard63 on 2010-01-05
As to bar "digital," it is the feature of Alsa. When you remove pulseaudio and make Alsa your default in

[[IMG]http://i081.radikal.ru/1001/9d/b109fcc293dbt.jpg[/IMG]]("http://radikal.ru/F/i081.radikal.ru/1001/9d/b109fcc293db.jpg.html")


(in the upper row, third from the left) it should appear.[/quote]

---------------------------------

Hi Julie, I believe we are on a good way. Thanks for your advise. I did all you said and now I have a number of devices to select under skype. 

Within the Alsamixer I choose exactly your settings from above and the same I did in Skype. 

Results:

1) Internal Micro is still not working (external I did not test since I don't want to use)
2) I have a permanent hissing noise in the background
3) The icon and as a result the program you mention in the above screen shot (I cannot read the name since it is in Russian) does not appear on my GUI

I am sorry when I drive you gracy ](*,)

---

### Post by Julita on 2010-01-05
Hissing sound disappears when you mute the bar "Front M" (it will appear without green 00) with the keybutton "m." The ones with green 00 are on, without it - muted. Have you enabled/muted with the keybutton "m" all the bars that I have? Alsa is automatically enabled when you have removed pulseaudio, so everything is fine now (the bar "Digital" is not quite important, at least I see no difference  when the numbers are high or low.)

---

### Post by Bernhard63 on 2010-01-07
Hi Julie,

I have done all your settings but still no micro is working :confused:

I can only imagine that I need to install another software or another software package to make the micro working. As mentioned above I do not have this program which appears on your screenshot (the one with Russian name). Maybe I need to install this? What is the English name for it?

Also what synaptic packets have you installed?

Cheers 

Bernhard

---

### Post by Julita on 2010-01-07
Dear Bernhard,

run in terminal
```
gnome-volume-control
``` You will see the table where you can configure your sound. Please, tell if you can get something out of it.

As to the programme you have mentioned, its name (according to HELP) is GStreamer v2, but there is no package with such name, so I guess it is the GUI for another gstreamer app that I have installed (some of them have been installed already, though) :

[IMG]http://i070.radikal.ru/1001/b9/eda1d4908684.png[/IMG]

Additionally, I have also the following packages: linux-sound-base, alsa-base and alsa-utils. 

Have you tried all the options in Skype?

I have also the configuration in [IMG]http://i055.radikal.ru/1001/80/174b4a87cdfb.png[/IMG], where I can choose [IMG]http://s61.radikal.ru/i172/1001/c0/208dee1ef242.png[/IMG] Maybe you have another icon for settings, but the sound should be... Wherever it is, choose ALSA.

---

### Post by Bernhard63 on 2010-01-08
Hi Julie,

thanks for the info. When inserting "gnome-volume-control" I get the following result "** gnome-volume-control: 1829): WARNING **: Connection failed - reconnecting ..."

It seems after deleting the pulseaudio I have, besides "audiomixer" no other tool to change audio settings. speakers are working but still no microphone. Tried all settings in Skype.

I will proceed trying.

Thx Bernhard

---

### Post by Julita on 2010-01-08
Bernhard, there have been reports about microphone not working properly. The bug has been reported frequently. One of the solutions is

```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

This might help. Please tell me if that helps.

---

### Post by Bernhard63 on 2010-01-09
Hi Julie, just tried this, result;

[I]"linux-backports-modules-alsa-karmic-generic is already the latest version.
Following packets were automatically installed and are no longer required:
audacity-data libflac++6 lobgconfmm-2.6-1c2 libglademm-2.4-1c2a
Use >>apt-get autoremove<< to delete them"[/I]

I removed this 3 files with above command and rebooted. Still no micro and when I enter "gnome-volume-control" I get the following result 

*"** gnome-volume-control: 1918: WARNING **: Connection failed - reconnecting ..."*

Also when I click on the programm icon "Sound" (sorry I don't know how to copy and paste the icons :-( ), I get a pop-up saying *"waiting for answer of Audiosystem"*

---

### Post by Julita on 2010-01-10
Bernhard, the messages you have posted indicate that you have pulseaudio leftovers. Please go to Synaptic package manager and remove all the installed packages that are related to pulseaudio name (except for those that remove the whole system, of course, but they are not many), then install the packages **gnome-media,  gnome-media-common, libgnome-media, gnome-applets-data, gnome-applets** Try cicking on the icon once more!

---

### Post by Bernhard63 on 2010-01-11
Julie, I have removed the remaining pulseaudio stuff, when I however try to install the packets **gnome-media,  gnome-media-common, libgnome-media, gnome-applets-data, gnome-applets **the synaptic packets administration tells me always that with these individual packets always packets from pulseaudio will be installed.

I believe that I need to install it via the console. Is this possible and how is it done?

thx

---

### Post by Julita on 2010-01-11
Oh my... I guess you can't escape PulseAudio in your case :) You have to

```
sudo apt-get install gnome-media gnome-media-common libgnome-media gnome-applets-data gnome-applets
```

and try running

```
gnome-volume-control
``` from terminal.

---

### Post by Bernhard63 on 2010-01-12
uuups - achieved dramatic result after deleting the pulseaudio stuff #-o

The netbook did not boot anymore correctly. Saw the Ubuntu start screen and then it went not into the nice GUI but just in a small terminal window.

When I did the installation of the gnome packets as described by you from this small terminal window and rebooted, the system came back, but I saw already during the gnome install process that again a number of pulseaudio packets were re-installed ](*,)

I think I may better stop here and ask one of my colleagues to help me here before I get to a point where I have to start new from scratch.

Thanks for your help and the time you invested, I am sorry that I could not make it. :icon_frown:

Cheers Bernhard):P

---

### Post by bambii7 on 2011-03-24
found this link in the bug tracker [http://www.ubuntu-es.org/node/137762?destination=node%2F137762](http://www.ubuntu-es.org/node/137762?destination=node%2F137762)
(used google translate)

the fix worked for me on Asus eee pc 1001px without doing the mentioned step of installing and messing with alsa
Using netbook edition 10.10 (I think that was the most recent download, not 10.04)
I had tried fixing the problem earlier though by uninstalling pulseaudio and a few of the unrequired pulseaudio synpatic packages, so can't verify if that influenced the fix.

in terminal:
sudo gedit /etc/modprobe.d/alsa-base.conf

add this line at the end of the file:
options snd-hda-intel model=lifebook

reboot

To get skype working left the mic device as default, turned OFF allow skype to DJ. Open alsa in terminal (type 'alsamixer') and set capture levels to about 50%

---

### Post by Julita on 2011-03-24
**Bambii7,** thank you very much for the tutorial! I'll give it a try when I have a chance. I also have the issue with microphone, only with skype of the latest verison. I had to downgrade Skype, and the mic would work just fine, but I like to use the newest version, though.

---

### Post by irpsit on 2011-12-31
This is one big problem in ASUS laptops with no solution in sight. I have been waiting for a solution for more than 2 years; and I have tried everything.

---

