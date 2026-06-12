---
title: "Karmic a2dp with nokia headset BH-501"
date: 2009-11-28
forum: Multimedia Software
---

### Post by xueg0i on 2009-11-28
My experience with ubuntu and bluetooth have been not always been very good. In Karmic it changed for the good, but still it is somewhat fuzzy. I would like to share the experience of connecting a bluetooth stereo headset.

Assuming your bluetooth dongle or internal bluetooth card works, pairing the headset is easy. Right click on the bluetooth icon in the taskbar and select "Set up new device..", set your headset in pairing mode and follow the on-screen instructions.

Now right click on the volume control in the taskbar and select "Sound Preferences". In the hardware tab you should be able to see your bluetooth headset. Select it and make sure the "High Fidelity Playback (A2DP)" profile is selected in the dropdown menu. In the "Output" tab you can now select your headset as the output device for pulsaudio.

So far so good. Now the fuzziness starts. Sometimes I can listen to music without any problem and sometimes it is choppy and stops altogether.

I found two approaches that helped me:

-switch off headset, disable bluetooth/remove dongle, enable bluetooth/insert dongle, switch on headset, right click on bluetooth icon in taskbar and connect to your headset.

-install blueman (sudo apt-get install blueman), startup blueman, left click on blueman icon in taskbar, right click on your connected headset, select "Disconnect Headset Service".

Unfortunately I do not know the cause of the problem, but I hope this helps others to enjoy their music via their stereo bluetooth headset.

---

### Post by Murz on 2009-12-14
Does your headsets connects normally on Karmic?
I have the permission error, even on root too, the bug is here:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/437649](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/437649)
Can you post your bluez version and config files?

---

### Post by pluto4ps on 2009-12-20
Hi,
After pairing headset I am not getting -->Sound Preferences-->Hardware Tab, here my bluetooth device is not listed.
You were telling something about PULSE, what is that? Do I need to install some extra software to get music from Headset?

---

### Post by milam on 2010-01-15
I was able to pair my MotoRokr S9-HD headset and following the same steps as the OP have it playing back in A2DP flawlessly. That is until I make use of my bluetooth mouse, then every time I move the mouse, including the scrollwheel, the sound in the headset cuts out until the mouse stops moving, then sound continues.

Do y'all feel this is a limitation of the netbook (new Acer One AO532h, running the N450 Pineview processor), of the bluetooth USB dongle (Iogear GBU421) or of Ubuntu NBR karmic? I am just using the bluetooth app that comes with NBR, not familiar with  Blueman or how it might make a difference.

On another note, switching the bluetooth profile to telephony duplex allows me to use the headset with Skype, Cheese and Sound Recorder (all the applications I have tried so far), although the sound is not nearly as rich and full as in A2DP mode, natch.

---

### Post by colgate on 2010-01-27
> **milam said:**
> I was able to pair my MotoRokr S9-HD headset and following the same steps as the OP have it playing back in A2DP flawlessly.

I tried with my Motorola S9 (not HD) and it worked at the first attempt! Wonderful! I could even redirect the audio I was listening to, from normal loudspeaker to the just connected Bluetooth headphones (AD2P) without even restarting Totem!
I'm starting to love PulseAudio and Karmic :-)

Federico

---

### Post by Draconis Rex on 2010-02-02
> **milam said:**
> I was able to pair my MotoRokr S9-HD headset and following the same steps as the OP have it playing back in A2DP flawlessly. That is until I make use of my bluetooth mouse, then every time I move the mouse, including the scrollwheel, the sound in the headset cuts out until the mouse stops moving, then sound continues.

What desktop environment are you using? Gnome? I've been trying to get my S9-HD and GBU421 working, and while I can get them to pair I've never gotten audio routed to the headphones. So far none of the instructions I've found on-line have worked. I am however using KDE, so that may play some part in why I'm failing where you succeeded. I'll be trying this sequence when I get home tonight.

Thnx.

**UPDATE:** I've gotten home and switched to Gnome. Procedure as described above works. Switched back to KDE and after starting gnome-volume-control was able to achieve the same result. Anyone know a pure KDE way to do this that works?

Regarding the GBU421, the sound quality sucks. I have my S9-HDs pairing with my laptop at work using its built-in bluetooth. Sound quality is *much* better. Using the GBU421 on Linux produces better results than it did under windoze on my personal laptop, but it is far from impressive. Looks like the GBU421 goes back to Newegg. Anyone have a dongle they recommend?

---

### Post by accumulator on 2010-02-13
> **Draconis Rex said:**
> Anyone know a pure KDE way to do this that works?

Make sure KBluetooth is started, then, go into the bluetooth device manager, search for the headset and add it to the list of known devices.

From then on, when you turn on the headset, pulseaudio will detect it and use it as audio device.

---

