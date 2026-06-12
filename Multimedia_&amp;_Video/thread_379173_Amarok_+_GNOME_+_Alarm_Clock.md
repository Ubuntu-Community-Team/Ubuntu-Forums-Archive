---
title: "Amarok + GNOME + Alarm Clock"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by DizzyTech on 2007-03-08
Alright, I have put together the following command to run Amarok and my playlist, which works in GNOME and KDE.
```
amarokapp ~/alarmclock.m3u; dcop amarok player setVolume 100; dcop amarok player play
```

I wouldn't mind messing with the above command to open AmaroK every night, run my playlist, and then tell AmaroK to play from where it stopped (which I believe would just leave it at "dcop amarok player play").

I've tried KAlarm and cron, but neither work in GNOME.  I need an alarm-like program that allows me to run a command, namely the above one, at a time like 5:55 AM every weekday.  This is one of the things that forces me back into Windows each weekend.

Note:  I use Scheduled Tasks in Windows, which is configured to start a similar .wpl playlist in WiMP.  The task is configured to wake my computer out of sleep, and run it using my password.  All I have to do to stop it is open my laptop and enter my password again (its at mslogon) and I'm back into Windows.

Are there any GNOME-based applets or otherwise that allow me to run a command at a scheduled time.  If so, is it possible for it to work with gnome-power-manager to wake from standby to execute the action?

---

### Post by jamere on 2007-03-10
Yeah, it would be nice if Amarok had a built-in alarm clock like BMP or XMMS. :( 

Jim M

---

### Post by mrWoot on 2007-03-16
> **jamere said:**
> Yeah, it would be nice if Amarok had a built-in alarm clock like BMP or XMMS. :( 

Jim M
There is a plugin for it. Check out the script part of Amarok. It's actually pretty nice.

---

### Post by jamere on 2007-03-16
mrwoot, thanks for the reply. Glad to hear there's a plugin for an alarm clock. I checked out the scripts section and didn't find anything that looked like it might be an alarm script. Do you have the script/plugin name for the alarm? 

Thanks much,
Jim

---

### Post by shingalated on 2007-03-16
I have it set up to run that command daily as an alarm in Evolution, works like a charm. :)

---

### Post by DizzyTech on 2007-03-18
These methods sound great, but can the alarm wake up from sleep?  Power is expensive, so I want to put my computer to sleep and have it wake up alarm time.

Here's my motto:  If Windows can do it, so can Ubuntu!

---

### Post by Chymera on 2007-08-24
if you are on gnome that script won't work for you. I find it annoying that ubuntu like all linux distros has the habit to blow at the most simple tasks.... especially now that i dont have any windows...

---

### Post by Bend3r on 2007-12-22
I have the same problem. I use PC Alarm Cock in XP and I want a similar program in my Ubuntu. I installed kalarm but it doesn't play the sound file (at least there is no sound) although there are people who have kalarm up and working in gnome. I don't understand this.

If someone knows how to configure kalarm in gnome please help us.

Regards.

---

### Post by johj on 2007-12-24
Hi,

I've just released GNOME Alarm Clock Applet 0.1 which does exactly what you're describing :) The only feature it misses is waking the computer up from sleep, which I'm aiming to support in the next release. I would love some feedback!

[Get it here]("http://joh.deworks.net/blog/?page_id=58"), post [your comments here]("http://joh.deworks.net/blog/?p=65").

---

