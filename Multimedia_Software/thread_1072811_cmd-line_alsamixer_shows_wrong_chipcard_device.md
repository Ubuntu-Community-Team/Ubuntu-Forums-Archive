---
title: "cmd-line alsamixer shows wrong chip/card device"
date: 2009-02-17
forum: Multimedia Software
---

### Post by lenards on 2009-02-17
My issue is that I cannot record sound ([http://ubuntuforums.org/showthread.php?t=1071180]("http://ubuntuforums.org/showthread.php?t=1071180")).  The system plays back sound just fine.  

One of the sub-parts that does not make sense to me is why when I run `alsamixer` from a terminal it reports that my chip/card is PulseAudio. 

[{screenshot: alsamixer}]("http://gigism.com/alsamixer.png")

I would expect that to report something like "HDA Intel" or "HDA Intel ALC880". 

Is there a way to change this?  

In System > Sound > Preferences, I have ALSA selected as my device for sound capture 

[{screenshot: sound prefs}]("http://gigism.com/sound_preferences.png")

Here's the specifics on my sound card: 

> 
lenards@deedee:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0


---

### Post by ajgreeny on 2009-02-17
Right click on the volume icon in your panel and choose Preferences then you can change your device.  This is for 8.04, it may be different in 8.10, but I suspect it is somewhere in the same area.  That may help you and let alsamixer show a lot more sliders than your two, including the microphone, line in, and Mix, that you may need for recording, depending on your sound source.

---

### Post by lenards on 2009-02-17
I am running Intrepid (recently updated at my LoCo's InstallFest).  

I've got HDA Intel selected as my device from the Volume Control 

Shown here: [http://gigism.com/volume_control_playback_tab.png]("http://gigism.com/volume_control_playback_tab.png")

And I still see PulseAudio as card/chip.

---

### Post by Reeman on 2009-02-17
> **lenards said:**
> My issue is that I cannot record sound ([http://ubuntuforums.org/showthread.php?t=1071180]("http://ubuntuforums.org/showthread.php?t=1071180")).  The system plays back sound just fine.  

One of the sub-parts that does not make sense to me is why when I run `alsamixer` from a terminal it reports that my chip/card is PulseAudio. 

[{screenshot: alsamixer}]("http://gigism.com/alsamixer.png")

I would expect that to report something like "HDA Intel" or "HDA Intel ALC880". 

Is there a way to change this?  

In System > Sound > Preferences, I have ALSA selected as my device for sound capture 

[{screenshot: sound prefs}]("http://gigism.com/sound_preferences.png")

Here's the specifics on my sound card:
Try **alsamixer -c 0 **instead of just alsamixer by default ubuntu just borks everything to pulse...but the real devices are still there! With alsamixer the ncurses commands are in man. A good old **$man alsamixer** will tell you all you have to know.

---

### Post by markbuntu on 2009-02-17
When you have your alsa default sound card set to pulseaudio that is what the alsamixer will show you. There is nothing wrong.

If you want to control your hardware use the panel volume control or the gnome-alsamixer both of which are easier to use than the command line alsamixer.

---

### Post by lenards on 2009-02-17
I appreciate the reply markbuntu. 

> **markbuntu said:**
> When you have your alsa default sound card set to pulseaudio that is what the alsamixer will show you. There is nothing wrong.


But I have my default set to ALSA, so I would expect card/chip as ALSA or HDA Intel & Realtek ACL880.

> **markbuntu said:**
> 
If you want to control your hardware use the panel volume control or the gnome-alsamixer both of which are easier to use than the command line alsamixer.

This is a sub-part of a bigger issue that I'm working on ([http://ubuntuforums.org/showthread.php?p=6742409]("http://ubuntuforums.org/showthread.php?p=6742409"))

I would normally just use the volume control - but I'm trying to get my sound recording working.  I've went through several walk-through posts on troubleshooting, and I've wrote up (in the above link) what I've tried but nothing is working.  One of the guides mentioned using alsamixer, making changes to get capture inputs working - and then saving the result.  With PulseAudio showing, I couldn't do any of the that.  So that's why I was spelunking in the reaches of `alsamixer`

I still am not able to record sound, and I need to be able to screencast for a project I'm doing for my job.

---

### Post by Tyche on 2009-02-17
> **markbuntu said:**
> When you have your alsa default sound card set to pulseaudio that is what the alsamixer will show you. There is nothing wrong.

If you want to control your hardware use the panel volume control or the gnome-alsamixer both of which are easier to use than the command line alsamixer.

markbuntu,

Your post was not helpful.  From my own experience I know that PulseAudio is borked - that is, it does not function correctly, nor does it recognize much of the functionality of a sound card. Since it cannot recognize the functionality of the sound card, one ends up with issues of no ability to record (because it does not recognize a microphone) and all sound comes out in monoral.  The answer is to stop PulseAudio from loading, and to change settings to ALSA, which DOES recognize sound card functionality.

---

### Post by lenards on 2009-02-17
> **Reeman said:**
> Try **alsamixer -c 0 **instead of just alsamixer by default ubuntu just borks everything to pulse...but the real devices are still there! With alsamixer the ncurses commands are in man. A good old **$man alsamixer** will tell you all you have to know.

Thanks Reeman!  I really appreciate the information!  I should have went back to the basics and checked out `man alsamixer`

---

### Post by lenards on 2009-02-17
I'm not sure how to mark this [SOLVED] - but this question has been answered... 

Thanks

---

### Post by Reeman on 2009-02-17
Your welcome! You will also find that you can run multiple instances of alsamixer in small terminal windows with control of different sections of the sound card at the same time. I use multiple sound cards and have for years found that the best way to directly control things is with the native alsamixer..period. 

I currently have three sound cards working all at the same time and through the jack and other interfaces direct sound data to different dsps or record from multiple sources at the same time. Good ol' alsamixer is indispensable. See this [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1070935") about sound cards and how you can really use features in different ways. Or [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1072663") posting about multiple sound cards. If your mike is muted then there is most likely something blocking access to the function in the /dev directory, sound server deamons like the artsd and the deamons used by pulse do put locks on things in the /dev directory and they can be a real PITA to track down!](*,)](*,) 

I am in the process of writing some scripts to set things up so that I can off the /dev locks by running a simple shell script.

I will not post them because of the fact that this site is starting to get linux wanabee jerks that post garbage like fork bombs. What I will do is package them for use with a gtk wrapper and then submit them to the Ubuntu Studio devs.

---

### Post by keyboardslave on 2009-02-18
Tyche, How would i go about stoping pulseaudio from loading?

---

### Post by Tyche on 2009-02-18
> **keyboardslave said:**
> Tyche, How would i go about stoping pulseaudio from loading?

1.  In System -> Preferences select "Sessions".  To it, add the command "Disable Pulseaudio" as a name.  For command, add "pkill pulseaudio".  For a comment, something like "This will prevent PulseAudio from launching at startup."  Then make sure it's selected (checkbox).

2.  Also in "Sessions", make sure that all instances of PulseAudio are Un-selected (unchecked)

3.  In System -> Preferences select "Sound" and on the Devices tab make sure that ALSA is selected for everything.

4.  In System -> Preferences select "Multimedia Systems Selector" make sure that ALSA is selected for input and output.

5.  Reboot

---

