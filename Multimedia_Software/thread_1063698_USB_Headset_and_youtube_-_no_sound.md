---
title: "USB Headset and youtube - no sound"
date: 2009-02-08
forum: Multimedia Software
---

### Post by sobepmp on 2009-02-08
I cant get any sound from my USB headset while watching any video with Firefox.  I've read about 50 different posts on the subject.  From what I can tell its because of a bug in the Flash plugin.  I've tried every solution I could find but nothing worked for me.  Anyone have any suggestions?

---

### Post by kostkon on 2009-02-08
What version of Ubuntu do you have?

---

### Post by sobepmp on 2009-02-08
I have 8.10 32bit

---

### Post by kostkon on 2009-02-08
Install the *PulseAudio Device Chooser* (it will have a menu item in *Applications &#8594; Sound & Video*). Run it and left-click on its icon in the system tray and select *Volume Control*.

Start a Flash video, for example, and in the *Playback* tab you should see the audio stream of this Flash video. Right-click on it and select *Move Stream...* to move its audio stream to your USB headset. *PulseAudio* will remember your choice.

You can do the same for any application that produces audio.

In the *Output Devices* and in the* Input Devices* tab you can set the default device you want for input and output.

For this to work, you need to set your sound playbacks in your sound preferences (*System &#8594; Preferences &#8594; Sound*) to *Autodetect*.

You can do the same for your sound inputs and then set a default input device from the *PulseAudio* volume control.

If you want, you can set *PulseAudio Device Chooser* to start every time you login from its preferences.

Hope that helps.

---

### Post by sobepmp on 2009-02-08
WOW!!!  That worked.  Thank you so much.

---

### Post by rugbeeprop on 2009-03-18
Thanks for the tips... now it works for me.

UPDATE: another way to ensure that the USB Headset works without the above tweaks is to hook up the USB Headset during installation.
What I have done to test my theory was to reinstall Ubuntu with the headset attached during installation. After the installation, I didn't have to do anything as the sound goes directly to the headset without having to do any configuration.

---

### Post by retrovertigo on 2009-03-26
> **rugbeeprop said:**
> Thanks for the tips... now it works for me.

UPDATE: another way to ensure that the USB Headset works without the above tweaks is to hook up the USB Headset during installation.
What I have done to test my theory was to reinstall Ubuntu with the headset attached during installation. After the installation, I didn't have to do anything as the sound goes directly to the headset without having to do any configuration.

This may sound like a silly question, but as I haven't bought a USB headset yet I can't test for myself.  If PulseAudio is sending the audio stream to your headset by default, will it fall back to the speakers when the headset is not attached?  I would assume that it would, but like I said I can't test.  I'm looking to get a headset for Skype and want to know that I'll be able to use it successfully.

---

### Post by rugbeeprop on 2009-03-27
> **retrovertigo said:**
> This may sound like a silly question, but as I haven't bought a USB headset yet I can't test for myself.  If PulseAudio is sending the audio stream to your headset by default, will it fall back to the speakers when the headset is not attached?  I would assume that it would, but like I said I can't test.  I'm looking to get a headset for Skype and want to know that I'll be able to use it successfully.

This is very interesting...

After a few days of reinstall, I unplugged the USB Headset. I have been using it without the Headset for a few weeks now and the sounds did fall back to the speakers.

I just plugged the headset back in, and the issue continues... I had to set the sound to USB Headset etc etc. And the system sounds did not go to the headset.

When I first reinstalled, everything went to the headset without any modification, i.e. all the setting was "Auto Detect".

---

### Post by markbuntu on 2009-03-27
You really need to be using pulseaudio and the pa volume control for multiple sound devices. It just makes life a lot easier. 

Your applications will play on the last device they used but you can change that in the pa volume control with a few clicks once the app is playing again.

The autodetect setting can give you problems with multiple applications and multiple devices. If you want everything to work properly so you have control over it go here


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by rugbeeprop on 2009-03-28
Thanks Mark.

Do you know of any future plan that will eliminate all of these steps?

---

### Post by Sir Noob on 2009-03-28
> **kostkon said:**
> Install the *PulseAudio Device Chooser* (it will have a menu item in *Applications &#8594; Sound & Video*). Run it and left-click on its icon in the system tray and select *Volume Control*.....

Ah thank you so much!

---

### Post by rugbeeprop on 2009-05-12
Found another solution which I think is better because it automatically detect and connect the headset:
[http://blueman-project.org/forum/viewtopic.php?f=5&t=111](http://blueman-project.org/forum/viewtopic.php?f=5&t=111)

---

### Post by sambita on 2009-06-11
Thanks very much for this post! extremely helpful

---

