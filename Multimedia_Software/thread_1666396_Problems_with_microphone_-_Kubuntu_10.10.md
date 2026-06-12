---
title: "Problems with microphone - Kubuntu 10.10"
date: 2011-01-13
forum: Multimedia Software
---

### Post by esst on 2011-01-13
Hello,
Im using Kubuntu 10.10, and have an external microphone, which im trying to use with skype.
The problem is i cant hear myself, when i speak. I checked alsamixer and KMix, and everything there seems to be fine, but still cant use the mic. This is the link, which ALSA Information Script generated.
[http://www.alsa-project.org/db/?f=847eac11cd4bd1fd0d84e86c9b0b6604a88f5d12](http://www.alsa-project.org/db/?f=847eac11cd4bd1fd0d84e86c9b0b6604a88f5d12)
Thank you very much.

---

### Post by inobe on 2011-01-13
have you set the sound device in skype under options ?

better yet did you install skype from the repo ?

---

### Post by esst on 2011-01-13
The sound device in Skype is "PulseAudio Server (local)", and i cant change it.
I cant use the mic at all, not only with skype.

---

### Post by inobe on 2011-01-13
did you install skype from package manager ?

---

### Post by esst on 2011-01-13
> **inobe said:**
> did you install skype from package manager ?

no, from the skype website.

---

### Post by inobe on 2011-01-13
okay, that rules out it being some skype bug.


thanks for answering that.

here's some problems i faced, i am a kubuntu user as well.

the rear mic works, the front doesn't for whatever reason.

---

### Post by esst on 2011-01-13
i have problems with both - front & rear....

---

### Post by inobe on 2011-01-13
i may have an answer, install pavucontrol.

under config tab choose analog stereo duplex.

in input device hit drop down menu to show hardware input devices.

open skype and make a test call, make sure your under recording tab in pavucontrol, you should see a skype logo appear and see your sound level indicator jumping.


i think there is a serious bug in kmix that should be fixed when kde 4.6 is released.

infact, i bet your mic will work with other apps like audacity.

---

### Post by esst on 2011-01-13
> **inobe said:**
> i may have an answer, install pavucontrol.

under config tab choose analog stereo duplex.

in input device hit drop down menu to show hardware input devices.

open skype and make a test call, make sure your under recording tab in pavucontrol, you should see a skype logo appear and see your sound level indicator jumping.


i think there is a serious bug in kmix that should be fixed when kde 4.6 is released.

infact, i bet your mic will work with other apps like audacity.

it works, i can make a test call with skype and record a message, but still cant hear my voice while im speaking.

---

### Post by inobe on 2011-01-13
> **esst said:**
> it works, i can make a test call with skype and record a message, but still cant hear my voice while im speaking.

i know what your talking about, give me some time to research this.

we know for a fact it's not a driver/ hardware issue. 

and if you look in kmix there are no mic options, mic boost etc ?

---

### Post by esst on 2011-01-13
> **inobe said:**
> i know what your talking about, give me some time to research this.

we know for a fact it's not a driver/ hardware issue. 

and if you look in kmix there are no mic options, mic boost etc ?

there is only the playback volume control, and volume control under "capture devices", but it doesnt work.

---

### Post by inobe on 2011-01-13
try this, open terminal/ konsole and type **alsamixer** and hit enter.

do you see mic levels ?

if yes try to test with that.


this should do till the next version of kde or if you don't upgrade kde, kubuntu.

if you stretch the terminal by dragging, you should see all controls.

---

### Post by esst on 2011-01-14
the problem still persist. this is the ALSA information log. Can anybody check it please ?
[http://www.alsa-project.org/db/?f=847eac11cd4bd1fd0d84e86c9b0b6604a88f5d12](http://www.alsa-project.org/db/?f=847eac11cd4bd1fd0d84e86c9b0b6604a88f5d12)
Thanx !

---

### Post by inobe on 2011-01-16
esst, remove **pulseAudio** and restart, upon restarting kde will ask a question, click **yes**

you will then be able to configure channels appropriately.


pulseaudio is the culprit and not alsa or kmix.

---

### Post by SeijiSensei on 2011-01-16
Don't remove Pulse without trying this first.

Go to System Settings > Sound and Video Configuration > Phonon.

In the Audio Capture section, click on the "Communication" option.  You should see an entry for the microphone.  If it's not the first entry in the list, click on it and use the Prefer/Defer arrow keys to make it first.  Save and try the microphone again.

---

### Post by inobe on 2011-01-16
> **SeijiSensei said:**
> Don't remove Pulse without trying this first.

Go to System Settings > Sound and Video Configuration > Phonon.

In the Audio Capture section, click on the "Communication" option.  You should see an entry for the microphone.  If it's not the first entry in the list, click on it and use the Prefer/Defer arrow keys to make it first.  Save and try the microphone again.

those settings do not exist until pulseaudio is removed, but then to verify my method working, i installed kubuntu on an hp desktop with similar sound chip and upgraded kde to 4.5.5

everything was a complete mess because of pulseaudio, i could not make the changes you described, i could not get skype to work unless i used pavucontrol.

in fact to configure channels, no channels were present to configure, now they are and skype works.

in skype i can choose a device, as before pulse had these settings locked!

---

### Post by esst on 2011-01-16
Great! I removed pulseaudio and it works. Now i can see the mic volume controler in KMix and make skype calls. Thank you very much ! :p

---

### Post by inobe on 2011-01-16
> **esst said:**
> Great! I removed pulseaudio and it works. Now i can see the mic volume controler in KMix and make skype calls. Thank you very much ! :p

i know, i'm just as happy as you are, your welcome :D

i had to try it myself to figure it out, it was well worth the risks to test this for ya, enjoy.

---

### Post by laynor on 2011-01-23
Hi, I had this same problem (mic not working in skype). 
For me it was enough to launch kmix and unmute the device listed in the capture tab.

---

### Post by didig on 2011-02-25
Guys - uninstall Pulse Audio, uninstall pavucontrol (If you've had it installed)... and you are through! All sounds settings will be working. No problem with Skype anymore!!!

---

### Post by inobe on 2011-02-25
> **didig said:**
> Guys - uninstall Pulse Audio, uninstall pavucontrol (If you've had it installed)... and you are through! All sounds settings will be working. No problem with Skype anymore!!!

agreed, it's been great as far.

---

### Post by pwabrahams on 2011-03-02
I had the microphone working just fine a week or so ago.  Now it's dead.  I had pulseaudio installed then.  I just tried removing it and pavucontrol, but that didn't help.  kmix tells me that I have no capture devices, which is also what pavucontrol tells me when it's installed.  Communication Devices under Systems Settings / Multimedia lists just Pulseaudio Sound Server.

I'm somewhat doubtful that removing pulseaudio is really the answer, since it was installed when my mike was working.  

It's maddeningly frustrating when things that were working stop working, most likely because of some update or other.  I guess that keeping my system updated is the way to go, but sometimes the consequences are terrible.

---

### Post by inobe on 2011-03-02
> **pwabrahams said:**
> I had the microphone working just fine a week or so ago.  Now it's dead.  I had pulseaudio installed then.  I just tried removing it and pavucontrol, but that didn't help.  kmix tells me that I have no capture devices, which is also what pavucontrol tells me when it's installed.  Communication Devices under Systems Settings / Multimedia lists just Pulseaudio Sound Server.

I'm somewhat doubtful that removing pulseaudio is really the answer, since it was installed when my mike was working.  

It's maddeningly frustrating when things that were working stop working, most likely because of some update or other.  I guess that keeping my system updated is the way to go, but sometimes the consequences are terrible.


what version are you using, what hardware is that box sporting?

i would imagine something like that being frustrating, updates can sometimes break stuff that worked perfectly before, what updates caused this?

---

### Post by pwabrahams on 2011-03-03
I'm running Kubuntu 10.10 on an Asus K60IJ machine. Here's my sound hardware environment as shown by hwinfo:```
Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x1111 "Santa Cruz Operation"
  SubDevice: pci 0x1043 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"

```
I don't know which update broke it, since there have been several in the last week or so.  I haven't done anything requiring the microphone for that long.

I see the problem both with Skype and audacity.  I've tried the 4 possibilities under System Settoings/Multimedia/Phonon/Audio Capture/Communication, all of which have a hardware type of HDA Intel, VT 1708S Analog.  None work.

---

### Post by inobe on 2011-03-03
my advice would be starting a new thread to get more attention.

include the information you provided in this thread.

but before you do that, run **alsamixer** in terminal, check your levels there.

you hwinfo states you have working modules, i have a gut feeling running alsa in terminal will reveal something.

edit< stretch the terminal window for all slider controls.

---

### Post by huynhhuuhieu on 2013-01-12
Can I record ( then mix) both mic and speaker in the mean time with pavucontrol

---

### Post by howefield on 2013-01-12
Old thread closed.

Feel free to start a fresh one.

---

