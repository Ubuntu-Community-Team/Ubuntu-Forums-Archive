---
title: "[SOLVED] sound won't output from USB speakers"
date: 2008-10-03
forum: Multimedia Software
---

### Post by Doug77 on 2008-10-03
I'm running Ubuntu Hardy Heron 64-bit, dual booted with Vista, on a Dell Inspiron 1525 laptop.  I just bought some Logitech S-150 USB speakers and I'm having problems getting them to work in Ubuntu (they work in Vista fine, so it's not a speaker problem).  

In Ubuntu, when I plugged them in, they immediately gave me the Ubuntu drum sound through the speakers, but sound from music and movies and everything still came through the laptop speakers.  I switched all the audio to "USB Audio" in sound preferences, but the sound still came out of the laptop speakers; however, when I clicked the "test" button in sound preferences, when it was set to USB, the sound did come through the USB speakers.  

I looked the web around for some solutions, and ended up typing "asoundconf list" in Terminal, which gave me two sound devices: Intel and default.  I typed "sudo asoundconf set-default-card default" as I thought "default" would be my USB speakers (when I type "asoundconf list" without the USB speakers plugged in, there is just "Intel").  I got this note: "Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences." and my USB speakers still didn't work.  However, in addition, now when I click on "test" in the sound preferences, when "USB Audio" is selected, I get no sound!  Now I get this error message instead: 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

When I unplug the speakers and plug them back in, they still give me the nice Ubuntu drum sound though.  I tried typing "asoundconf set-default-sound Intel" to try to reverse the changes, but I still have the same problem!  

I'd really appreciate some help with this one!  I'm quite frustrated that I WAS able to get a sound when clicking "test" in sound preferences, but now I can't - is there any way to revert my changes?  Can anyone help me out here?  Any suggestions would be greatly appreciated.

---

### Post by markbuntu on 2008-10-04
You need to change the default in PulseAudio Volume Control/Output Devices (pavucontrol) by selecting the usb device and right clicking on it. You can look in my guide here about using the Pulse Audio Volume Control:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Doug77 on 2008-10-05
Thank you so much!!  This solved my problem.  Specifically, entering "pavucontrol" from alt-f2, then right clicking on a stream and selecting "move stream" to the USB option.  It had to be when an application was playing, and I had to do it for every application I wanted to play through the USB, but it's working great now.  Thank you so much!!

---

### Post by markbuntu on 2008-10-06
You can change the defauly in the Output Devices section of pavucontrol by right clicking on the usb device. This will default your applications to the speakers and is easily changed back. This will not effect already running applications, but you already know how to change those.

---

### Post by justinjstark on 2008-10-16
Awesome.  Thank you.  Now I need to work on getting these Logitech V10's working with flash.  Any pointers???

---

### Post by markbuntu on 2008-10-16
Flash is just another audio stream and should show up in pavucontrol like any other stream.

---

### Post by justinjstark on 2008-10-16
> **markbuntu said:**
> Flash is just another audio stream and should show up in pavucontrol like any other stream.

Ya, it works now to.  Thank you guys.

---

### Post by markbuntu on 2008-10-16
Hey Doug, could you mark this thread as solved using the thread tools. It will help people out if you would do that.

Thanks,

Mark

---

### Post by erikthedrink on 2009-09-08
You can also try this.  I've got logitech usb speakers too.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

### Post by mermaid on 2009-09-18
Hi,
I've got the same problem with my speakers. I typed the command  in terminal, but the answer was: "no command found". What should I do then??? I'm a  very new user of Ubuntu, not very handy with it. Thanks for any help.
Mermaid, the girl

---

