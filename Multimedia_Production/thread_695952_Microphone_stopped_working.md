---
title: "Microphone stopped working"
date: 2008-02-13
forum: Multimedia Production
---

### Post by bigred1 on 2008-02-13
My mic worked, but always recorded too quietly, though I turned up the volume to max.

I installed alsamixergui to adjust this, and simply  set everything to max.

Now, my mic doesn't work at all! Apps like Audacity and Sound Recorder tell me that my settings are wrong and will not play back any recording.

When I try to test using the System->Preferences->Sound I get this
[I]
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
[/I]

Help!

---

### Post by ajgreeny on 2008-02-13
Try adding the Mic Boost +20dB in the alsa mixer or volume control that probably appears on your taskbar.  You may need to add that item to the switches available by using Edit>Preferences.

---

### Post by bigred1 on 2008-02-14
Thanks! 

By turning on all options on the Volume Control I somehow managed to get my mic to work again, and even set it to a good volume (before it was too quiet). 

I didn't see any sort of Mic Boost option, though,

There are still some problems. When I try to test the mic with System->Preferences->Sound->Sound capture->Test I get *Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'*

In Audacity, I can record a track, but when I press Record again.  I get an error message (screenshot attached). In Windows, this would make Audacity record a second track alongside the first.

---

### Post by ajgreeny on 2008-02-15
In volume control go to Edit>Preferences, scroll down and the option to show Mic Boost (20dB) should be there.  Select it with the radio button, click OK, and it will then show on the switches tab of volume control.

---

### Post by bigred1 on 2008-02-15
Thanks for getting back to me on this. 

Unfortunately, I don't see any Mic boost option even after choosing Edit->Preferences in Volume Control (image screenB.png attached) and scrolling down to the bottom of the resultnig dialog (screenC.png attached).

Thjis is also true even when I  change the device from ALSA to ALC888 (OSS Mixer)(screenD.png) attached.

---

### Post by ajgreeny on 2008-02-15
Try using ```
alsamixer
``` in terminal and see if you get any more options.  Perhaps it all depends on your sound card rather than the mixer software.

---

### Post by bigred1 on 2008-02-16
Thanks, I raqn alsomixer, searched all over the program, but  there is no 'boost' option. 

Screenshots from alsamixer are  attached, including the main screen and a hardware info screen.

---

### Post by Fot! on 2008-02-18
> **bigred1 said:**
>  When I try to test the mic with System->Preferences->Sound->Sound capture->Test I get *Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'*


I get the same error!! I've tried almost everything in my sound preferences. My sound recorder doesnt seem to record any sound.

The output of the arecord -l command (if that is any helpful) is:

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 2/2
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
Subdevices: 2/2
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
card 1: default [Camera ], device 0: USB Audio [USB Audio]
Subdevices: 1/1
Subdevice #0: subdevice #0

However, when i test my aMSN audio settings in configuring mic
I have three choices for input device: 1)default, 2)plughw1 and 3)plughw2.
So, when I choose plughw1 I can hear my voice in the test!!!
Please, any ideas?

---

### Post by faultier on 2008-02-19
and I have exacly the same problem with mic... i'v read already a lot of manuals 4 alsa, but no helpfull solution.
I thought, this could help, but it didn't
```

pcm.mixin {
        type dsnoop
        ipc_key 5978293	# must be unique for all dmix plugins!!!!
        ipc_key_add_uid yes
        slave {
                pcm "hw:0,0"
		channels 2
		period_size 1024
		buffer_size 4096
		rate 44100
		periods 0 
		period_time 0
       }
        bindings {
                0 0
                0 1
        }
    }
```


Can anybody give an idea in what direction to look for?

---

### Post by Makcum on 2008-02-20
Same here guys.
I am having this stupid problem for a long time already.
Microphone works for some period of time (this period is always different) and then stops working... I've tried everything to bring it back to life. nothing worked out. only reboot helps.

There are many different subjects in internet about that stuff though, but i have never seen any solution.  Ive tried to update alsa to 0.16 version but it didn't work either.
I am afraid there wont be any solution for this problem at all.. might be some kernel problems, maybe something else.
No matter how hard i try to fix it. nothing works. and it really sucks.. i cannot use my skype because of that thing.

---

### Post by kayosiii on 2008-02-20
Fot! 

I can see you have both an onboard souncard and a usb based soundcard which one are you trying to use....

Linux can sometimes get confused if you have more than one sound device.

All: there are a few other things that can go wrong -  Linux is a *Lot* happier when your soundcard supports hardware mixing. Some onboard soundcards don't which makes it possible for one application to grab the soundcard and stop anybody else from using it.

Also depending on the quality of the recordings you are trying to get it can be worth investing in a preamp for the microphone.

---

### Post by faultier on 2008-02-22
Hello everybody!

This stuff helped me!
[http://ubuntuforums.org/showthread.php?t=657235&highlight=HDA+mic]("http://ubuntuforums.org/showthread.php?t=657235&highlight=HDA+mic")

But i can't find "BOOST" in settings and my mic works too quiet ((

---

