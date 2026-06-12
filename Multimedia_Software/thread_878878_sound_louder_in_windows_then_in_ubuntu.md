---
title: "sound louder in windows then in ubuntu"
date: 2008-08-03
forum: Multimedia Software
---

### Post by SpinningAround on 2008-08-03
I use a double boot on my laptop and when I set the audio settings to max in windows will i get a louder output then what i get when I set the audio to max in ubuntu. So ubuntu are not using the speakers to max, is there any solutions to this?

---

### Post by jualin on 2008-08-03
Have you check all of the volume settings? Something like advanced volume on windows

---

### Post by cprofitt on 2008-08-03
That is true on my system as well.

First... do you have a multi-speaker (surround sound) system? are the rear speakers turned on? Also, the difference in drivers might make a difference. With Creative systems the volume is 100% in Windows, and that is not the case on Ubuntu.

---

### Post by ingeva on 2008-08-03
> **SpinningAround said:**
> I use a double boot on my laptop and when I set the audio settings to max in windows will i get a louder output then what i get when I set the audio to max in ubuntu. So ubuntu are not using the speakers to max, is there any solutions to this?


This is the case here also. In fact the sound is so low that in the beginning I thought there was no sound at all. When I turn the output to max both on the system and on the speaker, I could still want it higher.

I installed totem-gstream to make it work. Are there other players/codecs that might be better?
I need mp3 and wma, video is a plus but not necessary.

---

### Post by jualin on 2008-08-03
You can install the "ubuntu-restricted-extras" for an almost complete support of codecs. Or if you prefer you can install the "bad", the "good" and the "ugly" set of gstreamer plugins which let you play most media formats. I would go for the first choice since it's easier. You can install it via Synaptic Package Manager or via terminal > sudo apt-get install ubuntu-restricted-extras Welcome aboard!

---

### Post by ingeva on 2008-08-04
> **jualin said:**
> You can install the "ubuntu-restricted-extras" for an almost 

Thanks! I'm installing the first option now. Har to wait a long time for a response from sourceforge.net, but at least it's continuing.

This package was quite large.... :)

---

### Post by jualin on 2008-08-04
> **ingeva said:**
> Thanks! I'm installing the first option now. Har to wait a long time for a response from sourceforge.net, but at least it's continuing.

This package was quite large.... :)

It's quite large because it makes the computer install many other separate packages which include all of the plugins and codecs. But it's worth it since it's better than searching for each codec and plugin on Synaptic. :)

---

### Post by ingeva on 2008-08-04
> **jualin said:**
> It's quite large because it makes the computer install many other separate packages which include all of the plugins and codecs. But it's worth it since it's better than searching for each codec and plugin on Synaptic. :)

Well, first it doesn't play wma files; maybe not so surprising but because it's streaming I have quite a lot of those.

And the sound isn't loader at all. Everything turned up to max gives a low volume.

Could this have something to do with the drivers, and not the codecs?

---

### Post by s.recker on 2008-08-05
I did have the exact same problem as you did, I found this link in another post....[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Qoute:

    * Type this into a shell
      Code:

      alsamixer

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.

    * To navigate around:
          o Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen )
          o
            Up and Down Arrow Keys - Increase and decrease volume respectively.
          o
            Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey.

Saving Sound Settings
Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out.-


The above worked for me anyway, good luck.

Scott

---

### Post by ingeva on 2008-08-05
> **s.recker said:**
> I did have the exact same problem as you did, I found this link in another post....[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)



Thanks! The web page wasn't available but I could follow your description.
The sound is a little louder now, but not very much! :(

---

### Post by jualin on 2008-08-06
Maybe your is because of the drivers. Can you please post the results of typing in the terminal> lspci
sudo lshw This will let us know what sound card do you have. Good luck!

---

### Post by jualin on 2008-08-06
And sorry if I take a little longer than usual to answer but I am not currently on my house during this week. But don't worry I'll check the forums at least once a day. Hang in there a little longer!

---

### Post by ingeva on 2008-08-06
> **jualin said:**
> And sorry if I take a little longer than usual to answer but I am not currently on my house during this week. But don't worry I'll check the forums at least once a day. Hang in there a little longer!

That' OK, there has been a night between anyway!

The output from those commands is rather large so here they are as an attachment.
File: ls.txt,  the outputs are separated by an empty line.

---

### Post by jualin on 2008-08-06
Do you have 2 sound cards in your computer? 
Intel Corporation 82801I (ICH9 Family) HD Audio Controller
ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]

---

### Post by jualin on 2008-08-06
Can you also post the output of > aplay -l

---

### Post by ingeva on 2008-08-06
> **jualin said:**
> Do you have 2 sound cards in your computer? 
Intel Corporation 82801I (ICH9 Family) HD Audio Controller
ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]

I don't think so. This is an off-the-shelf computer, and the soundcard is on the motherboard. The only card I have added is the wireless.

---

### Post by ingeva on 2008-08-06
> **jualin said:**
> Can you also post the output of

Here it is. Guess one of those is a Windows modem....
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by lolistar on 2009-02-22
> **s.recker said:**
> I did have the exact same problem as you did, I found this link in another post....[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Qoute:

    * Type this into a shell
      Code:

      alsamixer

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.

    * To navigate around:
          o Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen )
          o
            Up and Down Arrow Keys - Increase and decrease volume respectively.
          o
            Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey.

Saving Sound Settings
Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out.-


The above worked for me anyway, good luck.

Scott


THANK YOU! you totally save me from straining my ears :)

---

### Post by jmmL on 2009-09-14
Thanks s.recker! I wanted to increase the volume of my Logitech AudioHub (which works flawlessly on karmic for those interested). I just used it for the first time in Windows after a few weeks in ubuntu, and after going back to ubuntu it seemed to be quieter. alsamixer -c 1 allowed me to increase the PCM, and now it's back to normal. (could just be my ears getting older I suppose!)

---

### Post by sandy8925 on 2009-09-14
@ingeva:

mplayer plays back anything and everything so it's probably the best thing to install.

Also the second card listed is the HDMI output. HDMI cables provide a single cable for connecting to a TV , through which both audio and video can go. I don't think it's a separate card as such. Not sure though..............

---

### Post by Magnificent 7 on 2009-11-03
> **s.recker said:**
> I did have the exact same problem as you did, I found this link in another post....[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Qoute:

    * Type this into a shell
      Code:

      alsamixer

<snip>

Brilliant.

I felt I had to post thanks to s.recker for this gem. Low sound volume was the last thing bugging me and reminding me of the Windoze days (well that and the general codec 'bingo' that is the lot of anyone using media players in Ubuntu).

Nearly a year and a half of periodically searching the forums against 'low audio volume' turned up nothing like Scott's post. In less than two excited minutes, my media centre's audio is now restored to its pre-HH level.

In my case there were four sliders marked 'VIA DSX', 'VIA DSX 1', 'VIA DSX 2' and 'VIA DSX 3' at the far right of the alsamixer window in the terminal. These were set at -57dB; moving the first up to the top of its travel, -48dB, restored the missing 10dB, but I set them all to max just as a 'belt and braces' measure.

Maybe the mods could tag this so that anyone else searching for low audio level might find it? I stumbled across it while looking for something completely different...

---

### Post by fishbulb1022 on 2009-12-14
It looks like a lot of people have already found fixes, but if anyone hasn't, if your sound works well in windows, make sure you don't leave it on mute (or likely even low volume) when you shut down windows. It sounds stupid, but it gave my brother problems for months.

---

### Post by Mariane on 2010-11-10
I don't have windoze. Alsamixer is a big help but is there anything stronger? I'm using Ubuntu 10.4 and I'm hard of hearing. 

Mariane

---

