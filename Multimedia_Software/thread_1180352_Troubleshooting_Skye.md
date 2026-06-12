---
title: "Troubleshooting Skye"
date: 2009-06-06
forum: Multimedia Software
---

### Post by wb0msz on 2009-06-06
I am trying to use the latest version of Skype on Ubuntu 9.04.

I have no problem using Skype on Windows XP.

The error message from Skype is "problem with audio playback" when I attempt to make a test call.

Within Skype's configuration for Sound Devices I am using the "default device" in the configuration although I have tried all the other options with no success.

On 9.04 my headset works perfectly with Sound Recorder and RhythmBox using the default device with I believe to be ALSA ICH6 mixer.  At least, that is what Sound Recorder reports.

My laptop is a Toshiba Satellite M45.

Any help or guidance will be appreciated.

This is the only application that keeps me bound to Windows.

---

### Post by takayuki on 2009-06-06
Hi,

i just installed 9.04 and skype died as well.  i got it working just now thusly.

*this assumes you installed skype from the standard repo, not the medibuntu repo, and you can use the terminal.*

1. uninstall skype via the terminal
```
sudo apt-get remove skype
```

2. add the medibuntu repo
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

3. install skype-static
```
sudo apt-get install skype-static
```


4. Go here: Psyke83's pulse audio howto is excellent.  check out appendix C:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)



[http://www.lockergnome.com/linux/2009/06/01/the-final-skype-on-ubuntu-904-solution/#comment-91532](http://www.lockergnome.com/linux/2009/06/01/the-final-skype-on-ubuntu-904-solution/#comment-91532)

lemme know if that helped.  good luck!

--takayuki

---

### Post by wb0msz on 2009-06-06
Takayuki,

I have done the three steps you provided and some progress has been made.

I am now able to dial the Echo/ Call Testing service but after connecting and ringing I still get the message from Skype "Problem with Audio Capture".

I also changed my Sound Devices settings for Sound Out and Ringing to "Pulse" as mentioned in [http://www.lockergnome.com/linux/200...#comment-91532]("http://www.lockergnome.com/linux/2009/06/01/the-final-skype-on-ubuntu-904-solution/#comment-91532").

I have not done a fresh install of 9.04. Perhaps I should and then repeat this procedure.

Anymore help would be appreciated.

---

### Post by psyke83 on 2009-06-06
Your problem is with PulseAudio - Skype's default configuration is not compatible, so you need to change it. See my PulseAudio guide for a general overview of PulseAudio itself, and see Appendix C for the specific instructions for Skype.

---

### Post by sigixv on 2009-06-07
go to your audio settings in skype, i found my by simple (and time consuming) try and error

Sound in: HDA Intel (hw:Intel,0)
Sound out: pulse
Ringing: pulse


In GNOME volume control i have HDA Intel (Alsa mixer)


If you make your settings alike (ie: physical hardware setting in the first and pulse for the 2 others), it hopefully will work

---

### Post by sigixv on 2009-06-07
forgot to mention "the obvious" which i forgot while doing my own checks...

make sure all sliders are on 100% in the gnome volume control for testing

---

### Post by wb0msz on 2009-06-07
Many thanks to all of you for your help.

I think I now have Skype working. At least, I now have success calling the Skype call testing service.

The Sound Devices settings within Skype options that work for me are:
Sound In:    Intel ICH6 (hw:ICH6,0)
Sound Out:  pulse
Ringing:      pulse

I have only one Skype friend, so I am awaiting a phone call from him to confirm that all is actually working OK.

I am new to Linux, more specifically Ubuntu (9.04).  I have a lot to learn. The Linux world is certainly different, but fun to learn about. 

Once again many thanks for all your help.  This forum is a great help!

Now on to getting Skype video working.

---

### Post by takayuki on 2009-06-07
Glad you got it working!  Any OS is difficult when you are starting out.  Sounds like you are on your way though.  Keep learning and you'll never look back.

And these forums are a lifesaver!  1000x better support here than some guy reading off a card in a call center.

have fun!

takayuki

---

