---
title: "Flash, Video but no sound. No firefoxrc file"
date: 2009-11-18
forum: Multimedia Software
---

### Post by Lolpanda on 2009-11-18
The joys of modern software lol. I installed Kubuntu a few days ago, got a few bugs sorted out, but there is one that I cannot seem to fix. My sound card + Firefox / Konqueror.  I can hear sounds perfectly fine in my desktop but in youtube, there's no audio. 

One person mentioned that it could be an ownership problem for Firefox so i ran it as root once to give it a shot, kept terminal up in the background and as I closed Firefox, i noticed terminal had a looooooooooooong list of errors. All of them repeatably saying



[COLOR=Red]ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave[/COLOR]


Another user mentioned going into etc/firefox/Firefoxrc and editting a line in there. That worked fine up until i actually typed that line into Terminal... and the file was completly empty.  

Another user said to double check the obvious thing and make sure flash was coming up as a firefox plugin. so i went to addons > PLugins. 

Shockwave Flash is listed, Adobe Flash isn't. Perhaps that is the cause of my ails? Perhaps, but according to Synaptic, "adobe-flashplugin" is currently installed, along with all of its dependencies.


Any thoughts anyone?

---

### Post by Dirtpile on 2009-11-18
Adobe flash normally appears as shockwave flash.
Type this "about: plugins" (without the space) nto the adress bar in firefox. That will show you all the plugins installed. Make sure everything is there and enabled.
 
Also if you have gnash or swfdec installed you should purge those, the interfere with adobe.

---

### Post by Lolpanda on 2009-11-19
Thanks for the reply,

All plugins are enabled, and Gnash / Swfdec aren't installed.

---

### Post by Skrim on 2009-11-19
Make sure that the PCM fader in Kmix isn't at set to 0.

---

### Post by Lolpanda on 2009-11-19
where is the PCM fader setting at Skrim? I just oppened up Kmix and i can't seem to find a setting like that anywhere.

New Development lol

Sound in Amarok, but no sound in Dragon Player. Possibly related??

---

### Post by Lolpanda on 2009-11-20
if any other community members have any ideas i would love to hear them >< its pretty bad not being able to listen to even youtube vids

---

### Post by Midahed on 2009-11-21
Me too! Amen to that!

I have exactly the same problem as you.  Amorak is fine, system sounds are fine, but no sound for YouTube.

about: plugins (without the space) shows that the Shockwave flash plugin for Firefox is installed and enabled.  Adobe-flashplugin is installed according to Synaptic.

It's almost enough to cause a re-installation of Windows...  :)

Anyone got any ideas to help us out with this?

Mike

---

### Post by Lolpanda on 2009-11-21
midahed, I actually fixed my own earlier today. If you're running Kubuntu (as I assume you are since you have Amarok) 

Go into Synaptic if you have it. Download Gnash for Konq,  (konqueror-plugin-gnash) and swfdec for firefox (swfdec-mozilla).

 
Tested them both, got them both working under those browsers. Just make sure you only have one of those for each. Like I have JUST gnash for Konq and JUST swfdec for Firefox.

Worked for me, hopefully will work for you.

---

### Post by Midahed on 2009-11-22
Thanks Lolpanda - I'll try that.

But can you explain what you mean when you say:- 

*"Just make sure you only have one of those for each. Like I have JUST gnash for Konq and JUST swfdec for Firefox".*

It sounds like you mean that some other stuff has to be removed - but what?  :)

Thanks for the PM nudging me towards this thread, by the way, but I've set my profile so that I get a mail notification whenever there's a reply to a thread that I've posted to. :)

Mike

---

### Post by Lolpanda on 2009-11-22
Heh alright,    Just wanted to make sure. 

What I mean is that when I open up Synpatic, I don't have the Gnash plugin installed for both Konq and firefox, Just one (Konq). Same with Swfdec, I only installed the package for one of the browsers (firefox)

Was originally a test to see which would work, And that combination of Swfdec on Firefox and Gnash on Konq seemed to get me the best results. And, as Dirtpile posted above, if you have both installed for the same browser, there can be issues.

---

### Post by Lolpanda on 2009-11-22
Well..this is interesting. Seems as though I will have sound for a little while but then it goes out as soon as I close FireFox. If I do a reboot however and then try a song up on youtube, sound's back. 

Anyone know what could be in my tmp or Var folders that is being deleted / created on reboot to make this happen? Or any other explanation really.

---

### Post by Midahed on 2009-11-25
Mmmmmm.  Installing swfdec for Firefox from Synaptic has made no difference. :(

At least your sound has worked.... :)  

Mine remains stubbornly silent (for YouTube and iPlayer, anyway).

---

