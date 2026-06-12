---
title: "Bose Companion 5 setup"
date: 2009-04-10
forum: Multimedia Software
---

### Post by glowplug19 on 2009-04-10
I am posting this to help any users with Bose Companion 5 that can't figure out the initial setup. This is pretty much a standard PulseAudio setup, but after hours of fruitless searching for specific help, followed by a good bit of trial-and-error (I'm a noob), I am sure some other noobs could make some use of this.

I did this on Jaunty Jackalope (dev), but I'm sure it works on Intrepid Ibex, and probably Hardy Heron. Don't know about anything earlier than that.

Open Synaptic Package Manager and install **pulseaudio** and **paman**, PulseAudio's manager (if not already installed). Accept any dependencies it requests - padevchooser, pavucontrol, etc.

After installation, go to System > Preferences > Sound. Under the Device tab, assign each playback selection to "PulseAudio Sound Server". Leave capture alone, and assign the Default Mixer to "Playback: Bose USB Audio - USB Audio (PulseAudio Mixer)". Close the window.

Open Applications > Sound & Video > PulseAudio Device Chooser. Or, if it's not there, open in a shell with **padevchooser**. Left-click on the newly displayed icon on your panel, and choose Volume Control...

Under the Output Devices tab, mute all devices except "Bose USB Audio - USB Audio" using the small mute icons next to each device. Click the down arrow next to the Bose entry, and make sure "Default" is checked. Close window.

Open your preferred media player - Rhythmbox, Listen, VLC, etc. Start playing a file from your library. While it's playing, re-open Volume Control. Under the Playback tab, assign Show: to "All Streams". An entry with the file being played should appear. Click the down arrow next to the entry, and select Move Stream... > Bose USB Audio - USB Audio. Adjust the relative shared volume control as necessary.

You'll need to repeat this last step for each application whose audio you want routed to the Companion 5's. The application has to be open and streaming audio to be sure it shows up under the Volume Control Playback tab. It should remember each application's preferred stream route after that; it's a one-time deal.

Hope this helps.

---

### Post by markbuntu on 2009-04-11
Thaks for that. I was sort of wondering if the bose usb speakers worked since the logitech do not.

---

### Post by krazykookmany on 2009-05-03
//

---

### Post by LarryMi on 2009-06-13
I'm considering the new Bose USB Companion 5.  

Does anyone know if 9.04 will auto-detect the Bose system?

The reason I ask is because my sound was working perfectly, so I decided to install **pulseaudio** and **paman **as noted above with all it's dependencies to see if I would continue to hear sounds/music.  Unfortunately, after installing the above, I lost all my sound.

After 2 days of following guides within Ubuntu's forums and getting nowhere, I decided to reinstall 9.04.  I got my sound back, but somewhat unsure if I'll be able to hear anything if I reinstall the pulseaudio files when I install the Bose.

I'm hoping 9.04 will auto-detect the new Bose USB Companion 5 and would appreciate any suggestions/recommendations you may have!

Thank you!

---

### Post by kjetilbmoe on 2009-07-12
Great guide! This truly deserves a bookmark in my browser.

I got this working not on a Bose system, but an aging Sony [pc-link]("http://www.minidisc.org/part_Sony_PCLK-MN10+MN10A.html") [CMT-C5 hifi]("http://www.ecoustics.com/amz/uk-reviews/B000069D0B"). Thanks again!

---

### Post by Samuel Smith III Owner on 2009-10-28
> **LarryMi said:**
> I'm considering the new Bose USB Companion 5. 
 
Does anyone know if 9.04 will auto-detect the Bose system?
 
The reason I ask is because my sound was working perfectly, so I decided to install **pulseaudio** and **paman **as noted above with all it's dependencies to see if I would continue to hear sounds/music. Unfortunately, after installing the above, I lost all my sound.
 
After 2 days of following guides within Ubuntu's forums and getting nowhere, I decided to reinstall 9.04. I got my sound back, but somewhat unsure if I'll be able to hear anything if I reinstall the pulseaudio files when I install the Bose.
 
I'm hoping 9.04 will auto-detect the new Bose USB Companion 5 and would appreciate any suggestions/recommendations you may have!
 
Thank you!
 
Ubuntu 9.04 doesn't auto detect the Bose Compantion 5's, it's the reason I'm actually reading this thread.
 
I'm going to try the PulseAudio method when I get home tonight, and hopefully it'll work.

---

### Post by kjetilbmoe on 2009-10-29
In the new 9.10 this can easily be fixed using the native sound control panel in the Preferences menu. Just select output sound card and you're good to go ...:p

---

### Post by oconnor on 2010-07-03
I'm using Ubuntu 10.04 Lucid Lynx and trying to get the Bose Companion 5 speakers to work.  

I just tried to follow the instructions posted by glowplug19 but there seems to be some missing options in my menus.  For example:  

> Open your preferred media player - Rhythmbox, Listen, VLC, etc. Start playing a file from your library. While it's playing, re-open Volume Control. Under the Playback tab, assign Show: to "All Streams". An entry with the file being played should appear. Click the down arrow next to the entry, and select Move Stream... > Bose USB Audio - USB Audio

When I am in the Volume Control and choose "All Streams" on the Playback tab page I don't get any option to "Move Stream" to Bose USB Audio like the instructions play.

Also I think there must be some other menu differences because in my System -> Preferences -> Sound... I do not have a "Device tab" as described below. 

> After installation, go to System > Preferences > Sound. Under the Device tab, assign each playback selection to "PulseAudio Sound Server". Leave capture alone, and assign the Default Mixer to "Playback: Bose USB Audio - USB Audio (PulseAudio Mixer)". Close the window.

Other than this I think I must be very close.  I have Bose USB Audio Analog Surround 5.1 and there is an active bar bouncing up and down for the Subwoofer.   Under Configuration I have Bose USB Audio under the Internal Audio.  I choose Analog Surround 5.1 Output but have also tried the other options.   I turned the Internal Audio to Off.  

The other interesting thing is that when I plug in headphones to the Bose Companion 5 volume control I get sound through the headphones just fine.  But otherwise just silence.  

Any advice?

---

### Post by Buurmas on 2011-12-20
Another similar (newer) thread:
[http://ubuntuforums.org/showthread.php?p=11553513](http://ubuntuforums.org/showthread.php?p=11553513)

---

### Post by nothingspecial on 2011-12-21
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

