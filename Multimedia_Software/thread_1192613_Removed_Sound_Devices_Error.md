---
title: "Removed Sound Devices Error"
date: 2009-06-20
forum: Multimedia Software
---

### Post by AlphaLexman on 2009-06-20
I was doing some work and listening to music in Xfce (i also have KDE 4.2) and got this Message:

     KDE detected that one or more internal sound devices were removed.
     Do you want KDE to permanently forget about these devices?
     This is the list of devices KDE thinks can be removed:

          Output: HDA ATI HDMI, ATI HDMI (HDMI Audio Output)


                                     Yes        No        Manage Devices


I really don't have any audio issues in either Xfce or KDE.
I just wondered what is going on or this might be a bug.

Thanx

---

### Post by AlphaLexman on 2009-06-20
Figured it out.

I have two audio outputs, one analog (3.5mm plugs) and a digital (fiber optic) 

Didn't know what that little black square ever was!

---

### Post by dragonflyFZX on 2009-11-19
great, but how did you solve it? Cause I have the same problem. What box are you talking about?

---

### Post by depaulmatthew on 2009-11-20
I have a similar sound problem after updating to 9.10 from 9.04. Any clues on getting it fixed?

---

### Post by AlphaLexman on 2009-11-20
It's really a B.S. error. It is telling you that nothing is plugged in to your digital output.

I have a motherboard that has digital [optical] output and standard analog output. My speakers are analog, (3.5 mm plug), back then I was using ALSA audio drivers, now I'm using pulseaudio drivers.

Goto: Applications, System Tools, System Settings, Computer Administration, Multimedia, Audio Output to change ALSA / pulseaudio priorities.

---

### Post by tiggsy on 2009-11-27
Although i can get as far as Admin, System Tools, the rest of your list of commands is not available. Can someone suggest an alternative path to the fix (and what to do once you get there would also be helpful, perhaps), please.

---

### Post by TechnoJunky on 2009-12-06
Computer Administration is the bottom section of the "General tab" in System Settings.  Multimedia is in the last row of icons.  But what are you supposed to do once you get there?  How do you stop the bogus error messages?  I get them every time I log into KDE, and everytime I start VMPlayer.  I don't just get one message either, I get a dozen each time.

---

### Post by AlphaLexman on 2009-12-07
My earlier ALSA/PulseAudio instructions were for gnome. It appears you are using KDE.

I seem to remember answering yes to letting KDE permanently forget these devices.

I haven't seen the same error message since.

---

### Post by jremy on 2010-07-09
I had this message come up. not sure what i should do 



KDE detected that one or more internal sound devices were removed.
    Do you want KDE to permanently forget about these devices?

    This is the list of devices KDE thinks can be removed:

 
[LIST]
[*]Capture: HDA NVidia (ALC888 Analog)
[*]Output: HDA NVidia (ALC888 Analog)
[/LIST]

---

### Post by tdn on 2011-08-27
I get this error all the time. Often when I dock or undock my laptop (Thinkpad T61p). After the dialog, the sounds does not work. This is extremely annoying. 

I tried removing pulseaudio. That did not help.

The dialog is here:
[http://i.imgur.com/EK1Wo.png](http://i.imgur.com/EK1Wo.png)

And KDE MAnage devices is here:
[http://i.imgur.com/uAdPX.png](http://i.imgur.com/uAdPX.png)

Does anything look wrong?


I hope you can help me fix this.

---

### Post by icegood on 2012-07-31
Still obtain that error. Please, remove [SOLVED] status from this thread.

---

### Post by masuch on 2012-11-01
Any workaround please ? It is really annoying and even KDE forum staff do not have the answer.

---

### Post by fetchingTurtle on 2013-01-24
I have the same problem. When I open amarok I'm met with that same "One or more internal devices was unplugged. Do you want KDE to forget about these devices?" message. Then it lists my headphone jack inputs, and the HDMI audio output device. Then if I go to play music in amarok, it plays faintly through my laptop speakers. If I go to unplug (or plug-in) any other output device, then it starts playing through the HDMI output to my 2.1 sound system. This is maddening. I noticed it happened after the latest kernel update. I'm in Ubuntu 12.10, in gnome.

---

### Post by RombusEvilBones on 2013-06-20
Any fix on this? 
When I get this error I can't use my default soundcard, so I have no sound.
This is my workarround (still very annoying), but at least I can have sound back with out rebooting:
I made a script that restarts alsa, pulseaudio and kmix.

```
# Restarts alsa
sudo alsa force-reload

# Restarts pulseaudio
pulseaudio --kill;
pulseaudio -D;

# Restarts kmix
killall kmix;
kmix > /dev/null 2>&1

# Popup notification
zenity --info --text="All done"
```

I've added the "sudo alsa force-reload" to run without prompting for password, so that you can only doble click the shortcut and have sound back in seconds (All your apps that uses sound need to be restarted also). You need zenity for the popup notification, you can remove that last line if you want.

---

