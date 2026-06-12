---
title: "Plantronics headset + Sb-Live audigy problems."
date: 2009-02-03
forum: Multimedia Software
---

### Post by hexdsl on 2009-02-03
hi all, i have searched the forums and google and although there are alot of results i cant find a solution, le me explain my setup

i am a new linux user, i have an ubuntu 8.10 setup running.
i have an audidgy SE 2 PC~I sound card in my machine that appears to work perfectly, even got the keyboard volume controls working with some fiddling.

now i have moved on to setting up my Plantronics headet. it is a .audio625 headset (i think) it connects via analogue plugs into a USB sound card dongle. works perfectly in windows (that i have now left as i am 100% ubuntu)  with no drivers to be installed. 

it works in Skype, mono (right ear only) and mic works perfectly (i record a podcast so is has been tested well lol) but as a for all other application it is mute, i have not managed to get it to even make a beep. 

ideally i would like ALL sounds hat my seyem makes to come out of soundblaster AND headset (without loosing keyboard volume control) 

so my questions are:
how can i make my headset work and be able to easerly switch from soundcard to headset (or just use both at same time) ? 

thank you for your time, hope i have included all the information that anyone would need to help me. thanks.

---

### Post by kostkon on 2009-02-03
Install the *PulseAudio Device Chooser*. Run it and then left-click on its icon in your tray and select *Volume Control*. From there you will be able to select the default output audio device (in the *Output Devices* tab) and in the *Applications* tab send the audio of an application from your one device to another by right clicking on the stream of your application and selecting *Move stream to*... In the list that will appear you should see your sound card and headset listed.

To have both devices (in your case your soundcard and USB headset) outputting your audio at the same time, left-click on the *PulseAudio Device Chooser*'s icon and select *Configure Local Sound Server*. Select the *Simultaneous Output* and enable the option that exists there. After doing this you will find a virtual device in the *Output Devices* tab that will represent all of your devices.

You will then be able to send (in the *Applications* tab as already said) the audio of an application to this virtual device (i.e. to all of your devices at the same time). You can even set this virtual device as the default so an all of your sounds will play on all of your devices at the same time by default.

For this to work, you should set your sound playbacks in your sound preferences (i.e *System &#8594; Preferences &#8594; Sound*) to *Autodetect*, in case you have changed them to something else...

Ah, yes, you also need in *Skype* to go to its preferences and set the *Sound Out* and *Ringing* to the *pulse* device.

Hope that helps.

---

### Post by hexdsl on 2009-02-04
Thank you, followed your adive and everything is working 100% :P

i have set the pulse control application to load on gnome start and have removed teh standard volume control applet. all in all its a better setup now. everything works how its logically expected. 

thanks VERY much for the help! 

now to see if i can fix my video problem lol
[http://ubuntuforums.org/showthread.php?p=6671829#post6671829]("http://ubuntuforums.org/showthread.php?p=6671829#post6671829")

---

### Post by KiRBY66 on 2009-03-12
Hi Guys,

  I was having same issue but followed the advise in this post and worked great !
Just one thing, being very very new to linux, how do I set the pulse device chooser to auto load on start up ?
and, how do I remove the standard volume control ?

BiG Thanks

---

### Post by markbuntu on 2009-03-12
the pulseaudio device chooser will start on startup if you check the startup box in preferences.

I have that same headset and plugged in some nice sony headphones. They sound much better than the ones that come with it.

---

