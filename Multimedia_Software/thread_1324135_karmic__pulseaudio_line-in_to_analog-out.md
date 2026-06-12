---
title: "karmic  pulseaudio line-in to analog-out"
date: 2009-11-12
forum: Multimedia Software
---

### Post by rusty0101 on 2009-11-12
First I'm not being critical of pulseaudio. Just trying to get my system to do what I would like. Preferably with the tools that come with Karmic.

I have a mixing board that I use to select various radio sources depending on what I wish to do. Ham radio in one feed, or another, shortwave, xm-radio, mic, and so on.

There are times when I want to listen to one of those sources. I'm not really interested in recording from them at the time, or building a patch bay that I have to change every time I want to change what I'm doing.

Under 9.04, I could right click on the volume control, select Preferences, select the Input tab, use the pull-down to select Line-In, click the checkbox to monitor, adjust the levels as needed, and I was listening to the source in question.

I'm not running into anything quite so simple under 9.10. The volume control applet will allow me to change the volume of the default-out sink, which is fin, or mute it, also fine, or even pull up the 'preference' for it, which lets me also adjust the volume. Ok. Nice, but not what I'm looking for. So I select the PulseAudio Device Chooser from the Applications > Sound & Video menu, and it very nicely throws up another PulseAudio Device Chooser close to the Volume control in the appropriate panel. Not really quite what I was expecting of an app in a menu, but OK. Close the spares and click on the remaining device chooser in the panel, and I have to admit, I'm not getting very far with the various options.

PulseAudio Manager looks like the logical place to go, However I'm not seeing anything that looks like a way to enable monitoring through Internal analog-out, anything on Internal Line-In. 

Well, perhaps it's in the PulseAudio Device Chooser Volume control. Well, yes I can see the device there, I can even see that the bar meeter is fluctuating with the input level, however I don't see any way to pass the audio from there through to the default output sink. 

In all honesty I suspect it's a brief python script that would like the two, acting as an application that acts as a sink for the Line-In, then pipes that to a source for the Default output sink for the system. The truth is that I don't think it should need to be created as a stand alone application, or even as a user installed plug-in to the pulse audio system. I'm thinking it should be an 'option' for any input device to be fed directly to the default output sink either at any time, or as a user configured permanent configured default

---

### Post by markbuntu on 2009-11-12
In the Karmic pulseaudio version there is a pulseaudio module-loopback which will let you connect sources to sinks. 

I do not think this module is loaded by default.

---

### Post by rusty0101 on 2009-11-13
WARNING: I am including command line commands to make modifications to my system. Do not blindly do this yourself. If you do not understand what the commands are doing, please review the manual entries for each command, and review the parameters carefully. A poorly constructed command or one maliciously constructed can leave your system in an unreliable or even unusable state.

For future reference, the link I followed to get the following information was [https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/83742](https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/83742)

To add the loopback module to the running instance of Pulse Audio I used the command:
$ pactl load-module module-loopback

To make the module automatically load in the future, I used the command:
$ sudo sh -c ' echo "load-module module-loopback" >> /etc/pulse/default.pa '

Once module-loopback was loaded, the pulse audio Volume Control panel adds an option to the Recording tab that allows you to select the input you wish to use on the loopback device.

I'm of the opinion that this should be a cleaner setup. If you have a TV Capture card, or as I do, radios that you want to be able to listen to, and at other times want to be able to record podcasts,etc through the same interface, it's a bit difficult to do without the module loaded. It could be muted by default, perhaps with a hovering help lable indicating what the features or functions of the device are. For many there will be no interest in the device. That's OK too.

---

### Post by maaaatteo on 2009-11-26
> **rusty0101 said:**
> 
To add the loopback module to the running instance of Pulse Audio I used the command:
$ pactl load-module module-loopback

To make the module automatically load in the future, I used the command:
$ sudo sh -c ' echo "load-module module-loopback" >> /etc/pulse/default.pa '


You are the man, man!

> **rusty0101 said:**
> 
I'm of the opinion that this should be a cleaner setup.


You are a gentleman too, because if i were you, i'd use more blasphemy in my reply. So its' better if i send *this* reply without adding any comment.

---

### Post by kylehase on 2009-12-19
I'd like to enable line-in to analog-out in Xubuntu Karmic but the module loading command returns:

[FONT="Courier New"]Connection failure: Connection refused[/FONT]

Looks like Xubuntu doesn't use Pulse by default.  Anyone know how to enable this in Xubuntu?

---

### Post by rusty0101 on 2009-12-20
I haven't looked at xubuntu under 9.10 to tell for sure, so take this with the understanding that you may need to modify the instructions for the actuall platform.

If you don't have the pulse audio system installed, you usually need to simply go to the 'recording' tab of the audio control panel and select the 'line-in' input as the 'recording' input. I suspect that by default 'mic' or 'mic-in' is selected. Depending on the mixer you may have to unmute the control and adjust the level as well. Which view that is on will depend on the control panel.

---

### Post by kylehase on 2009-12-20
Rusty, unfortunately that didn't work.  I've decided to just purchase a cheap audio switcher instead.  Thanks for the response.

---

### Post by mocha on 2009-12-20
Why is there a problem?  Just install gnome-alsa-mixer or use the command line alsamixer like "alsamixer -Dhw:0", and go in and adjust line-in volume and analog mix volume.  I agree karmic screwed up because they forgot to include the line-in and mic mixer settings in the new pulseaudio stuff, but at least you can still get to it.

---

### Post by Gege251 on 2010-02-25
I have a similar problem, but a little bit different. So, I'm a bass player, and lately I used my computer, with Windows XP on it,  for practicing. I just plugged it in to the line-in, and set the volume control to monitor the input. It was hardware monitoring, without latency. Now, I changed to Linux, and I can't find any reasonable solution. I tried JACK, but I had a lot of overruns, and after a while it started to distort. Tried Pulseaudio with module-loopback, but it has a latency. I'm just about to give up, and buy a better soundcard, but I'm sure that my hardware is available for hardware input monitoring.

---

### Post by memay1 on 2010-03-17
The easiest thing I've used is alsamixer. Just open a terminal and type alsamixer and then you can adjust the input or mic volume and make sure it is unmuted by pressing m.

---

### Post by Lypka on 2010-05-27
Gege251, I had the same problem using my guitar after setting up module-loopback. Solved by opening Pulse>Volume Manager> Recording Tab and setting it to monitor all streams. You should then be able to hear your bass with relativley no latency. The only problem I found with this is that I have to keep the Recording Moinitor window open or else it resets back to high latency mode. Not sure why this is, but as long as I keep the window open I can hear myself play and even record in Audacity. Hope this helps.

---

### Post by browny_amiga on 2010-06-13
If you are a newbie, alsamixer can be straight from hell ;-)

Do install gnome-alsamixer, much friendlier and does not look like alsamixergui straight from 1937.

sudo aptitude install gnome-alsamixer


and start with gnome-alsamixer, because you probably won't be able to find it in the menus (where is that menu search function in Gnome??)

---

### Post by Alex_L33 on 2010-06-30
In response to those suggesting just unmuting the line-in or microphone in alsamixer - this only works if the desired output device is on the same soundcard as the input, so is not a complete solution, and in fact does not work on my laptop even from on-board sound card line-in to on-board speakers.

---

### Post by Time Master on 2010-09-11
> **browny_amiga said:**
> If you are a newbie, alsamixer can be straight from hell ;-)

Do install gnome-alsamixer, much friendlier and does not look like alsamixergui straight from 1937.

sudo aptitude install gnome-alsamixer


and start with gnome-alsamixer, because you probably won't be able to find it in the menus (where is that menu search function in Gnome??)
Thank you! That did the trick for me. My line in and micro where muted.

---

### Post by rocketman221 on 2011-08-30
> **memay1 said:**
> The easiest thing I've used is alsamixer. Just open a terminal and type alsamixer and then you can adjust the input or mic volume and make sure it is unmuted by pressing m.
That works great. Thanks
I connect my record player to the mic jack to play it in my computer speakers.

---

### Post by asylumed on 2011-10-02
Works perfectly.

Thank you

---

