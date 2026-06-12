---
title: "PulseAudio alternatives for 9.10?"
date: 2009-11-07
forum: Multimedia Software
---

### Post by Hans Olo on 2009-11-07
In both 9.04 and in my recent upgrade to 9.10, I have had problems with PulseAudio.

Pertinent info about my system: I have a motherboard with a VIA chipset with on-board sound, which I have disabled in BIOS because I use a PCI SoundBlaster LIVE! card. Of course Linux sees the on-board sound anyways, so I blacklisted the via sound modules from loading.

In the 9.04 release, I was able to bypass PulseAudio, and I could enjoy smooth sound performance, instead of the popping/jittery sound I was getting. And it ran fine like that until I upgraded to 9.10.

I play some windows games under Wine. The sound is either fine for a few minutes, or choppy, and then it stops working all together. If I close the app, and kill the pulseaudio process, let it re-start itself, and re-start my wine app, sound works fine for a few more minutes. I also have sound problems with Flash on Firefox.

I tried removing PulseAudio all together, but it seems that Gnome requires it, as sound does not work at all without it. I long for the days when you could just use Alsa and sound worked!

I have no interest in all the fancy things PulseAudio can do. I switched to Linux exclusively back in 2001 because I wanted choice. It seems as though my choices are being limited here with the latest Ubuntu release, as the Preferences->Sound dialogs have been changed to prevent any sound server selection.

If there is ANY way to get rid of PulseAudio on 9.10, please point me in the right direction.

If I were a user fed up with Vista, and I tried Ubuntu with something as commonplace as sound not working right, I'd look elsewhere. But I'm not, so I will stick it out for a while until I can find a solution, before I switch back to Debian.

---

### Post by isoToxin on 2009-11-07
I was having pulseaudio problems in 9.10 whereby it was hanging my cpu whenever I switched between fullscreen / windowed modes in apps.  I just ended up disabling the pulseaudio daemon process, which cured my problem.  It usually respawns itself whenever you kill it, but you can easily add a config file to stop this from happening.  I didn't uninstall the modules or anything, and with the pusleaudio daemon disabled I still get sound output fine (presumably via ALSA).  

To do this, first add a new config file called client.conf at this location:
~/.pulse/

Add a single line to this config file:

autospawn = no

Then from a command line, kill pulseaudio daemon using:

pulseaudio -k

It should now stay disabled.  If your sound stops working then I'm not sure what to try, but in my case I still got sound playing fine and my problems with fullscreen switching went away.  

To restart the deamon process again, use:

pulseaudio -D

This method is safe because you don't actually remove pulseaudio by doing this, and thus leave ubuntu fully functional.  The only thing you will lose is the volume applet, but you can use either alsamixer or alsamixergui for this whenever pulse is disabled.

I'm giving pulseaudio the benefit of the doubt too, as it's definitely a good featureset, it just seems a bit buggy still on a lot of hardware.  Hopefully it will mature over time.  There do seem to be a lot of people having issues with it at the moment though.

---

### Post by Truckerpunk on 2009-11-07
I have the exact same problem. I'm not able to have multiple audiostreams running if one of these are either an Java-app or a Flash-app. Pulseaudio just doesn't support multiple audioplayback.. Not too linux-like. Pulesaudio is more like a "finders-keeper" soundinterpreter, whoever gets it first gets to keep it. If I have a java- or flash-app running my other audio-apps won't have sound and vise versa. In Jaunty I could just start my applications with "aoss application-name" and all was good, but this doesn't work in Karmic. I tried to remove pluse altogether, and as described with the deamon, but without luck. I also tried to install esound which sould be desigened to handle multiple audioplaybacks... But still no luck. GIVE US BACK ALSA-WRAPPER!! I'm on the edge to drop Ubuntu because of the trouble for setting up something as simple as audio. It has been like this in all the distros of Ubuntu I've tried. None of them support multiple audioplayback. I really need help to fix this.

---

### Post by hazz on 2009-11-07
I personally think pulse audio is a usability disaster. I just broke my system trying to remove it.

Trying to configure all the different applications to use it for someone who is not very linux savvy is painful at best. I consider my self knowledgeable and it took me ages trying to get skype to work with my usb phone instead of the soundcard so now I'm going to reinstall it like u suggested and then disable it and see if sound works again.

---

### Post by Hans Olo on 2009-11-07
Thanks to isoToxin for the hints on preventing pulseaudio from restarting on it's own.

Unfortunately, I still get no sound when pulseaudio isn't running. So I think the problem has to reside in Alsa. I located the **/usr/share/alsa** folder, where a grep for pulse shows the config files that reference it.

I tried commenting the line in the **alsa.conf** file that mentions pre-loading pulse.conf, restarted alsa, and still no sound.

Another interesting file is also in **/usr/share/alsa/pulse-alsa.conf** -- where it is supposed to  "set pulseaudio as the default output plugin for applications using alsa when PulseAudio is running." So it seems to be failing to detect that pulse is NOT running! 

I hope someone reading this is more familiar with alsa configuration, and can point us to a solution.

---

### Post by Hans Olo on 2009-11-07
Thanks to a commenter, Demagog on this page: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

I am now running on ALSA without that Pulse CRAP :D

His instructions were missing a step or two, so I will attempt to fill in the blanks:

# Remove PulseAudio and reboot!
sudo killall pulseaudio
sudo apt-get purge pulseaudio 
sudo reboot     # or reboot through the Gnome dialogs

# Install asoundconf-gtk and aumix-gtk
sudo apt-get install aumix-gtk 
sudo apt-get install asoundconf-gtk

# Download the missing 'asoundconf' binary, as it is no longer in the alsa-utils package!!!
Get alsa-utils_1.0.18-1ubuntu11_i386.deb from here (64-bit version also on the page):
[http://packages.ubuntu.com/jaunty/alsa-utils](http://packages.ubuntu.com/jaunty/alsa-utils)

 Extract  asoundconf  from alsa-utils*.deb with Archive Manager
 Then install it to the proper place:
 sudo cp asoundconf /usr/bin/
 
# Type on Terminal, or from your run dialog:
asoundconf-gtk

# Select your sound card from the list. Mine showed "LIVE", as I have a Sound Blaster Live! card.

# Run aumix-gtk, from the menu->Sound & Video->aumix
Make the window larger so you can see the sliders better. I had turn "PCM2" way up before I could hear anything. (I believe this is due to PulseAudio volumes being higer than alsa volumes?)

I now have working sound, and my system seems to be more responsive. The only problem still, is the stupid Gnome volume control only works with Pulse!! But I would rather have working sound and no volume control applet, than an applet and crappy sound. I'll just run aumix until the volume control is fixed.


Now I must note that before I did all of this, I tried using the 'pasuspender' binary before the command to run my wine games, which resulted in no sound. It's possible that would have worked if I had run the aumix app to adjust volumes... BUT, I'm not about to re-install PulseAudio to find out.

---

### Post by isoToxin on 2009-11-07
Good info to know.  Thanks for the update and fix.  If I ever need to completely ditch pulse, it will come in handy.  :)

---

### Post by Truckerpunk on 2009-11-07
tried Hans Olo's solution... But once again without luck. I still can't gets ound from a java-app simultaneously as anything else. I can't belive it is taht difficult... I'm running out of hope to get the working.

---

### Post by Hans Olo on 2009-11-08
> **Truckerpunk said:**
> tried Hans Olo's solution... But once again without luck. I still can't gets ound from a java-app simultaneously as anything else. I can't belive it is taht difficult... I'm running out of hope to get the working.

Some sound cards (and a lot of built-in sound chips) can only handle one audio source/program at a time. This, I think, is one of the reasons why they've implemented a sound servers like esound and pulseaudio. To do the mixing of sources before the sound is sent to the card. I recall running into that back in 2001, which is why I've used "Sound Blaster Live!" cards  ever since, because they can handle the mixing on-board. But of course that has screwed me now with PulseAudio.

Perhaps if pulseaudio isn't working for you, you could try esound? (Sorry, can't be of much help there, never used it.)

---

### Post by Truckerpunk on 2009-11-08
Thanks for taking time to try to help out. But sadly I've already tried esound, but still no success. I actually have a Sound blaster live card lying 'round, but when I tried to plug it in in Jaunty, my system refused to boot. Perhaps I can give it another shot in Karmic. One quick question Hans; Are you able to playback music, say from rythembox, while having a Sun java application running, on your soundblaster Live card? Cheers, and thanks for the help in advance.

---

### Post by isoToxin on 2009-11-08
One more piece of info I've found is where pulse audio is launched from in ubuntu.  It seems it's started when X11 is launched from a script here:

/etc/X11/Xsession.d/70pulseaudio

You can prevent it from starting in the first place by moving that script file out of that folder and keeping it somewhere else (e.g. your home folder).  Whenever you login to gnome from then on, pulse won't load.

Seems I'm lucky enough to have a sound card that can handle hardware mixing too, as I can run multiple apps at the same time and hear sound from them all.

I will see what happens when running a sun java app & rhythmbox at the same time a bit later too and report back.

---

### Post by Edgewalker_001 on 2009-11-08
> **isoToxin said:**
> I was having pulseaudio problems in 9.10 whereby it was hanging my cpu whenever I switched between fullscreen / windowed modes in apps.  I just ended up disabling the pulseaudio daemon process, which cured my problem.  It usually respawns itself whenever you kill it, but you can easily add a config file to stop this from happening.  I didn't uninstall the modules or anything, and with the pusleaudio daemon disabled I still get sound output fine (presumably via ALSA).  

To do this, first add a new config file called client.conf at this location:
~/.pulse/

Add a single line to this config file:

autospawn = no

Then from a command line, kill pulseaudio daemon using:

pulseaudio -k

It should now stay disabled.  If your sound stops working then I'm not sure what to try, but in my case I still got sound playing fine and my problems with fullscreen switching went away.  

To restart the deamon process again, use:

pulseaudio -D

This method is safe because you don't actually remove pulseaudio by doing this, and thus leave ubuntu fully functional.  The only thing you will lose is the volume applet, but you can use either alsamixer or alsamixergui for this whenever pulse is disabled.

I'm giving pulseaudio the benefit of the doubt too, as it's definitely a good featureset, it just seems a bit buggy still on a lot of hardware.  Hopefully it will mature over time.  There do seem to be a lot of people having issues with it at the moment though.


I tried this method, it didn't give me any sound in TF2 and now when I play sound from audacious it's choppy and crackly, something it WASN'T before...

Does anyone have a solution?

Ok, problem solved, Audacious apparently have an option for using the ALSA drivers instead, I wish it was THAT easy with wine...

---

### Post by Yellow Pasque on 2009-11-09
> Ok, problem solved, Audacious apparently have an option for using the ALSA drivers instead, I wish it was THAT easy with wine...

So you tried running this from a terminal and selecting ALSA under the 'Audio' tab?:
```
winecfg
```

---

### Post by p.suierveld on 2009-12-18
> **isoToxin said:**
> I was having pulseaudio problems in 9.10 whereby it was hanging my cpu whenever I switched between fullscreen / windowed modes in apps.  I just ended up disabling the pulseaudio daemon process, which cured my problem.  It usually respawns itself whenever you kill it, but you can easily add a config file to stop this from happening.  I didn't uninstall the modules or anything, and with the pusleaudio daemon disabled I still get sound output fine (presumably via ALSA).  

To do this, first add a new config file called client.conf at this location:
~/.pulse/

Add a single line to this config file:

autospawn = no

Then from a command line, kill pulseaudio daemon using:

pulseaudio -k

It should now stay disabled.  If your sound stops working then I'm not sure what to try, but in my case I still got sound playing fine and my problems with fullscreen switching went away.  

To restart the deamon process again, use:

pulseaudio -D

This method is safe because you don't actually remove pulseaudio by doing this, and thus leave ubuntu fully functional.  The only thing you will lose is the volume applet, but you can use either alsamixer or alsamixergui for this whenever pulse is disabled.

I'm giving pulseaudio the benefit of the doubt too, as it's definitely a good featureset, it just seems a bit buggy still on a lot of hardware.  Hopefully it will mature over time.  There do seem to be a lot of people having issues with it at the moment though.


works like a charm!!! I&#7743; so happy everything works fine now even video runs better.

Tnx a lot!!!

regards Peter

---

