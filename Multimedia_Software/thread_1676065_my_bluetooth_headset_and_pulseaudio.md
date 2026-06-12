---
title: "my bluetooth headset and pulseaudio"
date: 2011-01-26
forum: Multimedia Software
---

### Post by nerdy_kid on 2011-01-26
I have a bluetooth headset that I use for G-talk and skype, basically I want it so that when I turn on the headset, everything plays/records out of it.  Then, when I turn the headset off, my laptop's audio card takes over.  I tried setting the bluetooth as the default sink/source via paman, but all new apps that try to make a noise crash cause the headset connection is not there.  I tried setting my laptop card as the fallback device in pavucontrol, but the settings are lost as soon as I disconnect the headset.  Help?? :confused:

---

### Post by nerdy_kid on 2011-01-28
bump...

---

### Post by nerdy_kid on 2011-01-29
bump...

---

### Post by nerdy_kid on 2011-01-31
no way to do something like this?

---

### Post by rosencrantz on 2011-02-01
Did you check this [howto]("http://superuser.com/questions/28174/ubuntu-bluetooth-headset-and-skype") and this [thread]("http://superuser.com/questions/28174/ubuntu-bluetooth-headset-and-skype")?
When I tried last (nearly a year ago), I couldn't get my headset to work due to a bug in Skype, but then I was on SuSE and alsa, and apparently you have a better chance with pulseaudio. I'm starting another attempt on 32bit Kubuntu right now, will post again when I find out anything new.

Cheers,
rosencrantz

---

### Post by rosencrantz on 2011-02-01
OK, I'm back. Good news: it works. Bad news (for you, sort of): it worked out of the box with Kubuntu Maverick's default pulseaudio settings.(Skype Beta 2.1.0.81, Sony Ericsson HBH-PV703, generic BT dongle from sitecom). 
Pulseaudio was even capable of quite intelligent hot switching like automatically selecting the headset for Skype while sending Amarok output to the sound card and falling back to the sound card on disconnect. Sounds like what you were looking for.
I'm not a pulseaudio expert, but have you tried a configuration backup and resetting to system defaults ([Pulseaudio guide for Jaunty]("http://ubuntuforums.org/showthread.php?t=843012"))?

---

### Post by nerdy_kid on 2011-02-02
hmm strange, thanks for the info.  I'll try reseting my config then!

---

### Post by nerdy_kid on 2011-02-02
skype seems to work fine, but Google voice doesn't -- perhaps because its running in the browser -- idk.  Maybe google will fix it, it doesn't seem that pulseaudio can do anything about it.

---

### Post by rosencrantz on 2011-02-02
Which browser are you using? Maybe you have more success with a system integrated one like rekonq? Although I've no idea which technology GTalk is using and how its audio streams are routed in detail.

---

### Post by nerdy_kid on 2011-02-03
I'm using Chrome, rekonq/konqueror wont load the google talk plugin correctly.

---

