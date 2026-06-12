---
title: "HOW-TO configure PulseAudio to work with USB Audio Devices."
date: 2011-01-18
forum: Multimedia Software
---

### Post by Cotopaxi on 2011-01-18
Some two years ago, I had to remove PulseAudio, because that was the only way to get Skype working.

Following a recommendation from a forum member, I re-installed PulseAudio (“pulseaudio” in the repositories) and also the “PulseAudio Volume Control” (“pavucontrol” in the repositories)

Now this PulseAudio Volume Control is doing such a fantastic job, I just wanted to give a thumbs up to this device.

This HOW-TO is written for Kubuntu, Ubuntu users should not have major difficulties in performing all instructions under Ubuntu. If anyone wants to re-write this for Ubuntu, please go ahead!

In this example, we will configure a generic USB Headset (Headphone & Microphone) to work with Skype (Voip device). If you are using USB loudspeakers or a USB home cinema, follow the instructions anyhow, you will easily find your product in PulseAudio Volume Control.

If you DO NOT use Skype, no problem, you just skip Steps 5a to 5d,
You just go on with Step 5e & 5f, but DO make take these two steps!

So, here goes the “HOW-TO”
 1. Download “pulseaudio” and “pavucontrol”, they are in the repositories.
 a) PulseAudio device chooser, “padevchooser” should already be marked for installation. If it isn't, mark it for installation.


 2. Now open Pulse Audio Volume Control; >Applications>Multimedia>”PulseAudio Volume Control” and don't do anything yet.


 3. Go to >System Settings>Multimedia and switch all Audio Output and Audio Input devices to use “playback/recording through PulseAudio sound server”.


 4. BEFORE we switch to Skype or your multimedia application: First: Make sure your headphones, or your USB sound device, are plugged into a USB port. If you have to switch your USB sound device ON, switch it on now. Second: Switch to the PulseAudio window, which you have already open. You will find a window with five tabs: “Playback”, “Recording”, “Output Devices”, “Input Devices” & “Configuration”. We will concentrate on “Output Devices” & “Input Devices”.

 a) Click on the tab “Output Devices”. You will find two groups of two sliders: “Internal Audio Analog Stereo”, and (in my case) “USB VoIP Device Analog Stereo”. Here your USB device should appear, IF you plugged it in and (if needed) switched it on!
At the right hand side of the sliders (Left & Right channel) you will find two buttons: “Lock channels together” locks left & right channel into one only slider, so both sliders move in parallel. Feel free to select it.
The other button “Set as fallback” is the button that tells PulseAudio to use this USB device predominantly. Select it!

 b) Click on Input Devices. Again, you will find “Internal Audio Analog Stereo” and “USB VoIP Device Analog Mono”, again:
On your USB device click again on the right button “set as fallback”, to use this microphone predominantly.
Set the Microphone Capture slider to maximum. You can tune it down anytime later.


 5. Now open Skype &:
 a)  go to > Options > Sound Devices. In all three menus (“Microphone”, “Speakers” & “Ringing”), the option “PulseAudio Server (local) should now be the only option available.
UNCHECK the box “Allow Skype to automatically adjust my mixer levels”. If you leave this box checked, Skype will tune down your microphone and other people won't hear you!

 b) Now make sure you have the Skype window and the PulseAudio window side by side, so you can work on them simultaneously.

 c) On the PulseAudio window click on the “Playback” tab. Here, at the moment, you will only find a volume slider for “System Sounds”, that's ok so far.
On the very bottom of this tab, you will find a selection menu titled “show”: select “Applications”

 d) On the Skype Window, click on “Skype Test Call”. If it is not in your contact list, click on “add or search for Skype Contacts” (green button, bottom left of window) and type in “echo123”. Add this contact to your contact list.
Dial this “Skype Test Call”, a voice will tell you to record a message, afterwards your message will be played back to you and, if you hear the voice and your message, everything went fine. As soon as you clicked on the call button for the “Skype Test Call”:

 e) Switch to the “Playback” Tab of the PulseAudio Volume Control and you will notice that a
second volume slider pops up called: “Skype Output on”, with a selection menu with two options: 1) “Internal Audio Analog Stereo” & 2) “USB VoIP Device Analog Stereo” or your own USB sound device.
Select “USB VoIP Device Analog Stereo” or your USB sound device.
You can also select the button: “Lock channels together”

 f) On this “Playback” Tab, you will have the option to choose the sound output for each program that is sending sound to PulseAudio,  be it the flash application in your browser, be it a video player, etc.


Ok, your USB sound device should be working now! Enjoy!!! ;) :D

---

### Post by Ashrael on 2011-09-06
Good HOWTO, thanks.

But, I wanted my skype to play the ringing sound over my speakers while I want to have the conversation over my headset. I took me quite a while to get to an answer so I decided to share the knowledge.

Thanks to Jim Hunziker for figuring it out!

At first glance (and even at second and third) it seems impossible to set the ringing sound to speakers and the conversation to usb headset.

But follow above HOWTO and then:

1) open pavucontrol and skype>options>sound devices next to each other.
2) press "make a test sound" and (be fast) you will be able to choose (in pavucontrol) the sounddevice to route the ringing sound to, e.g.: Internal audio ananlog stereo.
3) press make a test call and route the call sounds to a usb headset.

DONE!

---

### Post by sembagdod on 2011-12-03
Well, it didn't work for me, if i change the sound in "Test Call" it will be changed for "Test Sound" as well. 
and vise versa , appreciate if anyone have other solution


Regards

---

