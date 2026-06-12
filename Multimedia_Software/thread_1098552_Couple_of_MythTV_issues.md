---
title: "Couple of MythTV issues"
date: 2009-03-17
forum: Multimedia Software
---

### Post by kadafi69 on 2009-03-17
Ive had MythTV installed for a couple of weeks now, and ive just got it configured to how I like it (although that will probably change in a couple of days). But ive come across a couple of issues.

Firstly when the system boots up it logs into MythTV, however, once the loading phase is finished 1) you can still see the menu bar across the top, 2) I have to click on the MythTV menu to start using it, inconvenient as I'd like to start using it straight away with my remote...which brings me to point 2...

Secondly, I have a streamZap remote. I have this configured, set-up and working on my root account (and works with MythTV when I start the frontend from the root account) however it doesnt work from the MythTV account.

Thirdly, when trying to watch the films and TV programmes stored on the system, they play however there is no sound to them. (playback of music and recorded programmes works (there is some popping when playing music, but ive narrowed that down to an audio setting within MythTV)).

Can anyone help me with any of these problems?

---

### Post by kadafi69 on 2009-03-18
bump

---

### Post by bon_the_one on 2009-03-18
Hi


*Firstly when the system boots up it logs into MythTV, however, once the loading phase is finished 1) you can still see the menu bar across the top, 2) I have to click on the MythTV menu to start using it, inconvenient as I'd like to start using it straight away with my remote.*

Is there anything else loading from your autostart that maybe grabbing focus? I have AMSN & Firefox also loading at start and sometimes they can grab focus as they start after mythfrontend.

*Secondly, I have a streamZap remote. I have this configured, set-up and working on my root account (and works with MythTV when I start the frontend from the root account) however it doesnt work from the MythTV account.*

Try copying /root/.lircrc and the directory /root/.lirc into /home/mythtv. I had the same and copying the lirc config & directory into the Mythtv home directories solved it. Don't forget to check permissions on the folders once copied so your Mythtv user can read them.

*Thirdly, when trying to watch the films and TV programmes stored on the system, they play however there is no sound to them. (playback of music and recorded programmes works (there is some popping when playing music, but ive narrowed that down to an audio setting within MythTV)).*

As a test, go into Media settings and change your default player from mplayer to "internal". If mplayer is having problems, but Myth's internal player for TV & Music works, changing the default Video player to the internal software may help.

Hope thats of some help,

Ian

---

### Post by kadafi69 on 2009-03-18
> 
Is there anything else loading from your autostart that maybe grabbing focus? I have AMSN & Firefox also loading at start and sometimes they can grab focus as they start after mythfrontend.

Yeah its transmission, i'd like to keep it running in the background, any ideas how to stop it from grabbing focus?

> Try copying /root/.lircrc and the directory /root/.lirc into /home/mythtv. I had the same and copying the lirc config & directory into the Mythtv home directories solved it. Don't forget to check permissions on the folders once copied so your Mythtv user can read them.

That worked a treat, thanks. Although ive noticed some of the buttons dont work, especially when watching film etc, is this a conflict with xine?

> As a test, go into Media settings and change your default player from mplayer to "internal". If mplayer is having problems, but Myth's internal player for TV & Music works, changing the default Video player to the internal software may help.

The default player was set to xine, i tried internal but no luck, i then tried vlc which worked but was a pop up, ill try changing the settings in vlc.

I tried playing with the internal audio settings to try get music to stop popping but that didnt work either, so I have no idea what to do with that.

---

### Post by bon_the_one on 2009-03-18
*Yeah its transmission, i'd like to keep it running in the background, any ideas how to stop it from grabbing focus?*

From the shell, starting Transmission with a '-m' flag gets it to open just in the tray. You should be able to edit the autostart to get this flag passed on.

*That worked a treat, thanks. Although ive noticed some of the buttons dont work, especially when watching film etc, is this a conflict with xine?*

You might need to edit some of the configs to your exact set-up. I'm not sure how Xine would be conflicting, as each app has an lirc profile in your ~/.lirc/ directory. have a look at ~/.lirc/mythtv and check all the button mappings are how you would expect them to be. I have a Windows 'Phillips' remote, and had to edit the default config to fit my wants properly. 
Xine shouldn't be launching from within Myth if you are using the internal player, but if you are running Xine at the same time as Myth, I 'believe' Lirc knows which app has focus and uses the correct config file in ~/.lirc

[I]the default player is already set to internal, i tried switching it to mplayer, but to no effect.
I tried playing with the internal audio settings to try get music to stop popping but that didnt work either, so I have no idea what to do with that.[/I]

Try launching mythfrontend.real from a shell and doing some playback of tv and/or videos. You might see a 'buffer under run' error being logged to the shell window. This generally indicates a problem with your sound card drivers. Try changing 'Aggressive Sound Card Buffering', or setting everything to ALSA:Default, and at worst, try setting to /dev/dsp and /dev/mixer which might make some difference. You'd need to really see what gets thrown out to the shell window when running myth from the command line to get a better idea of whats going on.

---

### Post by kadafi69 on 2009-03-18
> From the shell, starting Transmission with a '-m' flag gets it to open just in the tray. You should be able to edit the autostart to get this flag passed on.

Yep that worked. Thanks.

> You might need to edit some of the configs to your exact set-up. I'm not sure how Xine would be conflicting, as each app has an lirc profile in your ~/.lirc/ directory. have a look at ~/.lirc/mythtv and check all the button mappings are how you would expect them to be. I have a Windows 'Phillips' remote, and had to edit the default config to fit my wants properly. 
Xine shouldn't be launching from within Myth if you are using the internal player, but if you are running Xine at the same time as Myth, I 'believe' Lirc knows which app has focus and uses the correct config file in ~/.lirc

Looks like thats what im gona have to do, I'll leave it for today tho.


> Try launching mythfrontend.real from a shell and doing some playback of tv and/or videos. You might see a 'buffer under run' error being logged to the shell window. This generally indicates a problem with your sound card drivers. Try changing 'Aggressive Sound Card Buffering', or setting everything to ALSA:Default, and at worst, try setting to /dev/dsp and /dev/mixer which might make some difference. You'd need to really see what gets thrown out to the shell window when running myth from the command line to get a better idea of whats going on.

It was on ALSA: Defualt so I had a bit of a fiddle and running it on /dev/dsp doesnt give me any problems.

Thanks for your help.

---

### Post by bon_the_one on 2009-03-18
Glad I could help! Hope you enjoy Myth!

---

