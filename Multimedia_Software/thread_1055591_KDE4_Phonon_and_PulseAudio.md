---
title: "KDE4 Phonon and PulseAudio"
date: 2009-01-30
forum: Multimedia Software
---

### Post by markbuntu on 2009-01-30
**KDE4 Phonon and PulseAudio on Intrepid and Jaunty**

** Read this entire post before doing anything!!!**

If you are not using KDE4 on Intrepid 8.10 or Jaunty 9.04 do not attempt this. If you are happy with your current Kubuntu Intrepid or Jaunty KDE4 sound setup I strongly suggest that you do not do this. If you have more than one hardware sound device and are having difficulties controlling them all in KDE4/Kubuntu, this may be for you. 

KDE4 comes with Phonon which is the new sound API and sound server for KDE applications. It is a partial replacement for the aRts sound server which was used in previous versions of KDE. Phonon is still very much a work in progress and it is expected that it will improve greatly as it matures so please be patient.

I have two sound cards and a usb headset and a usb webcam with a  mic. I could find no reasonable way to manage all this with Phonon so I use Pulseaudio. Hopefully Phonon will be able to take over many of these functions in the future but for now Pulseaudio will do the work. 

First, an important point, I installed KDE4 on top of Gnome, I use them both so I am probably using quite a few packages  that do not come with the Intrepid or Jaunty Kubuntu install. Just be aware that you may need to get many packages from the repos to satisfy all the dependencies of the packages necessary for this to work if you have installed only Intrepid Kubuntu. If someone could let me know exactly what they needed to install to get all this to work properly it would be much appreciated. 

Here's what I did to get PulseAudio managing all the sound for me in Intrepid  KDE4. 

************************************************************************************************************

** Setting Up Pulse**
First you need to get pulseaudio installed and set up properly if it is not already. You can get all the pulseaudio packages with your package manager. You also need to get a few other items and set up alsa, xine, gstreamer, phonon and  pulseaudio for maximum usability. 

** Launching Pulseaudio**
Pulseaudio does not start by default with KDE (for me anyway) so you need to put a launcher in System Settings/Autostart. I also made a launcher for padevchooser to get the Pulse Audio Applet in the KDE panel. You can also see post #9 in this thread for how to start pulseaudio automatically in KDE4.2

Open System Settings/Advanced/Autostart. Select Add program, type pulseaudio -D in the box and select Run in Terminal and Do not close when command exits click OK. In permissions check Is executable. In Application/Name type Pulseaudio and check that the Command is pulseadio -D so it starts with the defaults from default.pa. click OK. To set up the padevchooser launcher it is basically the same just change pulseaudio to padevchooser.

Log out, log back in and pulseaudio should be running and you should have the Pulse Audio Applet in your panel. Click on the applet and choose Volume Control.
If, when you try to open the volume control you get a message
```

connection refused

```
That means that pulseaudio is not running. This means that something is wrong with the Autostart launcher so you should check that and make sure it is set up correctly.

You can also start the pulseaudio daemon from a terminal with 
```

pulseaudio -D

```
If you need to stop pulseaudio for any reason use this command
```

killall pulseaudio

```

To avoid confusion and difficulties please read through the rest of this post before following the directions in the the link since it was not written with KDE users in mind but will direct you to the the packages you need and give you some basic pulseaudio setup information if you are unfamiliar with it.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

For Jaunty

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

*******************************************************************************
** Setting up KDE4**

In System Settings/Sound make default the first preferred option and in Backend you can prefer either gstreamer or xine since we will set them both up for pulseaudio. If you change these while an application is playing you may lose its sound output and need to restart the application.

**ALSA setup**
In Settings/Default Sound Card asoundconf.gtk choose PulseAudio. This will send everything that goes to alsa to PulseAudio. (asoundconf.gtk is a little gui that sets the alsa default sound card)

**gstreamer Setup**
In Settings/Multimedia System Selector/Audio/plugin select the PulseAudio Sound Server and set Device to Default. 

**xine setup**
Start xine, open the Setup window and select the Audio tab. For audio driver to use select pulseaudio and leave device used for pulseaudio empty.

Log out and log back in and click on the Pulse Audio Applet and choose Volume Control. This will open the pulseaudio volume control. Start up Amarok or some other application that plays sound and make it play something. You should see it in the Volume Control Playback tab and all your hardware sound devices in the Output tab. You can adjust the volume sliders or mute the stream or right click on the stream and change its Output Device. 

In the Settings menu you should now have  Pulse Audio Preferences Sound Server Preferences. You can open that and in the Simultaneous Output tab check the box "Add virtual device for simultaneous output on all local sound cards" and have a virtual device in the Pulseaudio Volume Control/Output Devices that will direct the sound to all your sound hardware at the same time, you can direct a stream to it and control the volume like with any other output device, not a bad thing.


** Sound Capture and recording**
Phonon does not currently offer a alsa default device or a pulseaudio device for sound capture and recording in System Settings/Sound.  For applications using Phonon there is currently no way to direct them to use the  pulseaudio input devices so for now you are stuck with choosing hardware devices in System Settings/Sound for sound capture/recording. This is not so bad because Phonon gives you a lot of choices including the ability to capture hardware output streams as well as inputs.

************************************************************************

If you are having more general problems with setting up your sound or want some more in depth information you can always go to the 10,000 page guide here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)


If this does not work for you or you have questions or comments or something to add concerning KDE4 and sound, please post here. This is very much a first draft but everything has to start somewhere.....and the first thing I need to know is if this creates a total nightmare for Kubuntu Intrepid users.

Best regards,
mark

---

### Post by Syniurge on 2009-01-31
Nice attempt to make things about Phonon and PulseAudio clearer for Kubuntu users :D

I've been curious about pulseaudio integration in Kubuntu too. In fact Phonon isn't a sound server, PulseAudio is (see [http://en.opensuse.org/Sound-concepts#Phonon](http://en.opensuse.org/Sound-concepts#Phonon)). And contrary to the claim in the wiki [https://wiki.kubuntu.org/Kubuntu/UbuntuFeatureParity#line-52](https://wiki.kubuntu.org/Kubuntu/UbuntuFeatureParity#line-52) , PulseAudio is neither installed nor set up for Kubuntu users.
One problem then is that Amarok for KDE3 and other non-Phonon apps prevent Phonon to output sound since by default it uses the "plughw" devices and there is no software mixing (there is a workaround to make it use DMix, the ALSA way to do software mixing, but this isn't the right way to go, PulseAudio is).


Your guide is correct, other than the xine part. The "xine" command for the GUI from xine-ui has a seperate config file unrelated to Phonon.

And some additional input: to make PulseAudio appear in KDE sound panel you have to check "Show advanced devices" at the bottom-left in the panel, it's the proper way to make Phonon use PulseAudio, instead of passing through ALSA (which redirects input to PulseAudio anyway after it is configured with asoundconf.gtk).


edit: Amarok 1.x for KDE3 also has its own "xine-like" config file, so pulseaudio should be selected in Amarok settings.

re-edit: actually you dn't need to configure anything with asoundconf.gtk, Ubuntu ALSA lib already remaps to pulseaudio by default, I just catched this.

---

### Post by markbuntu on 2009-02-01
First of all, thanks for your input. I am still trying to figure out exactly where Phonon fits in the sound scheme. It seems that the ultimate goal is for it to be the sound server for KDE4 so, even though it is not there yet, I mention it as such.

Due to the way I went about installing KDE4 I was unsure about Kubunutu and pulseaudio in Intrepid. I know that pulseaudio was not included in Kubuntu Hardy.

> 
re-edit: actually you dn't need to configure anything with asoundconf.gtk, Ubuntu ALSA lib already remaps to pulseaudio by default, I just catched this.


This was not my experience with Hardy. Some alsa apps still try to address the alsa hardware drivers directly, asoundconf ensures redirection of these apps to pulseaudio. If the alsa libs now take care of all this then asoundconf does no harm in its redundancy.

The xine-ui configures the ./xine file which is where the user defaults for the xine engine are found. If I am mistaken about this (which is entirely possible), please tell me where these defaults are written and how they can be configured.

---

### Post by Syniurge on 2009-02-01
> **markbuntu said:**
> TSome alsa apps still try to address the alsa hardware drivers directly, **asoundconf ensures redirection of these apps to pulseaudio**. If the alsa libs now take care of all this then asoundconf does no harm in its redundancy.
I don't know about Hardy, but asoundconf produces a .asoundrc that does the same than /usr/share/alsa/pulse-alsa.conf in Intrepid.
So it is harmless but useless. 


> **markbuntu said:**
> The xine-ui configures the ./xine file which is where the user defaults for the xine engine are found. If I am mistaken about this (which is entirely possible), please tell me where these defaults are written and how they can be configured.
That could be indeed, my mistake to have been so affirmative.
I can't tell you since I don't know either and haven't found anything after a quick google trip.

---

### Post by markbuntu on 2009-02-01
> **Syniurge said:**
> I don't know about Hardy, but asoundconf produces a .asoundrc that does the same than /usr/share/alsa/pulse-alsa.conf in Intrepid.
So it is harmless but useless. 

Well that is good to know. A lot of people misapply these sort of posts to the wrong distribution so I will probably leave that in for a while to preclude them from causing themselves and me trouble.

> 
That could be indeed, my mistake to have been so affirmative.
I can't tell you since I don't know either and haven't found anything after a quick google trip.

It would be nice if xine had a separate configuration gui like the Multimedia System Selector that gstreamer has. Without one we can get confused with questions like "Does the xine gui configure the xine engine?" The only reason I installed the xine player was that configuring the xine engine seemed a little obscure and I figured the xine player would clear that up.

---

### Post by Killerah on 2009-02-02
Man, you're awesome! I've been looking for a way to get my audio working properly in KDE after switching over and your guide really helped me out and helped me understand what was going on with my audio better. Thanks a ton.

---

### Post by Arathorn on 2009-02-09
Thank you! I've gotten very irritated with sound just not working on Kubuntu but when fiddling with the Pulseaudio volume control it finally worked.
Btw, wasn;t there some thank you function on this board? I can't find it anymore.

---

### Post by hihihi on 2009-03-06
markbuntu, u are my hero!!

i switched over to KDE, like u installing KDE-desktop on top of GNOME-irntrerprirdr irbrerxr (what a name) some weeks ago...

i followed your text quite closely and now i understand what i could just guess... pulseaudio is not a standard installation in kde.
aha...
making autostart pulseaudio -D did the whole trick.
i am able now to do all kinds of stuff as before on gnome, but with a beautiful breathtaking look :)

thank you!!!!!!!!!!
:popcorn::KS;):D:):P:o

---

### Post by Syniurge on 2009-03-06
markbuntu's post was for KDE 4.1.
As of KDE 4.2 (available in the backports), the only thing needed to get PulseAudio working within KDE is making "pulse-session" run before KDE launches using the following command in a terminal: 
```
cp /usr/bin/pulse-session ~/.kde/env/pulse-session.sh
```

Then after restarting KDE, Phonon devices(not just the "PulseAudio" device) will map to PulseAudio devices instead of ALSA devices.

---

### Post by markbuntu on 2009-03-06
Well thanks for that. I have not delved into KDE4.2 yet but I expect to be doing so soon. Then I will include specific instructions for KDE4.2.

---

### Post by hihihi on 2009-03-07
> **Syniurge said:**
> markbuntu's post was for KDE 4.1.
As of KDE 4.2 (available in the backports), the only thing needed to get PulseAudio working within KDE is making "pulse-session" run before KDE launches using the following command in a terminal: 
```
cp /usr/bin/pulse-session ~/.kde/env/pulse-session.sh
```

Then after restarting KDE, Phonon devices(not just the "PulseAudio" device) will map to PulseAudio devices instead of ALSA devices.

i am also on kde4.2 and  making autostart pulseaudio -D did the whole trick.
i ask myself if this is not good enough?
for now everything is working again that wasnt before.

---

### Post by Syniurge on 2009-03-07
> **hihihi said:**
> i am also on kde4.2 and  making autostart pulseaudio -D did the whole trick.
i ask myself if this is not good enough?
for now everything is working again that wasnt before.
The difference is that the scripts located in ~/.kde/env/ run before Phonon initialization, early enough to play the startup sound.
That and I had some problems when PulseAudio was autostarted with KDE (PulseAudio not getting detected by Phonon for ex.).

---

### Post by markbuntu on 2009-03-14
Well, I just tried the script and disabled the autostart commands it seems to make no difference with KDE4.1. Startup and shutdown sounds play and there is still no pulse device in system settings/sound but selecting default directs the sound to pulse. 

System Settings/Advanced/Autostart shows the autostart commands in **Desktop file** and the script in **Script file**. The script is run on Pre-KDE startup so prehaps this is an advantage that is not available from using autostart. A close investigation into the KDE init process may be warranted to find which is actually better or if this is just a difference without distinction.

---

### Post by Syniurge on 2009-03-15
> **markbuntu said:**
> Well, I just tried the script and disabled the autostart commands it seems to make no difference with KDE4.1. Startup and shutdown sounds play and there is still no pulse device in system settings/sound but selecting default directs the sound to pulse. 

System Settings/Advanced/Autostart shows the autostart commands in **Desktop file** and the script in **Script file**. The script is run on Pre-KDE startup so prehaps this is an advantage that is not available from using autostart. A close investigation into the KDE init process may be warranted to find which is actually better or if this is just a difference without distinction.
To clarify, starting from KDE 4.2 Phonon tries to map ALL the devices in system settings/sound to PulseAudio devices. Autostarting PulseAudio instead of using .kde/env sometimes causes Phonon not detecting PulseAudio and reverting to ALSA devices instead.

---

### Post by markbuntu on 2009-03-23
> **Syniurge said:**
> To clarify, starting from KDE 4.2 Phonon tries to map ALL the devices in system settings/sound to PulseAudio devices. Autostarting PulseAudio instead of using .kde/env sometimes causes Phonon not detecting PulseAudio and reverting to ALSA devices instead.

Well, that makes sense. But we still do not know why pulse does not appear  in KDE4.1 even with the script. I could swear I saw pulse in there when I first installed KDE4.1 in Intrepid but then after some update it was no longer there.....

---

### Post by hyper_ch on 2009-04-05
well, this seems not to be working for me on KDE 4.2.2 on jaunty 64bit. In System Settings / Multimedia I have an Intel and PulseAudio entry. The Intel one works fine (plays music) the PulseAudio one doesn't.

I used that ~/.kde/env approach.

---

### Post by markbuntu on 2009-04-05
> **hyper_ch said:**
> well, this seems not to be working for me on KDE 4.2.2 on jaunty 64bit. In System Settings / Multimedia I have an Intel and PulseAudio entry. The Intel one works fine (plays music) the PulseAudio one doesn't.

I used that ~/.kde/env approach.

Getting pulse to work with KDE is also dependent on having pulse set up properly and using the pulse volume control to direct the applications.

---

### Post by hyper_ch on 2009-04-05
actually ones I updated pulseaudio with the PPA repos it started working now.

---

### Post by srbaldomero on 2009-05-18
Hello, I have kubuntu 9.04 64bits and after following the instructions (basically adding the autostart command) I didn't get any progress at all.

Since I am not sure if I am missing some pulseaudio package (and I do not want to install anything I do not need), I attach some screenshots from KpackageKit and Adept:

[[IMG]http://i20.photobucket.com/albums/b227/srbaldomero/th_pulseaudio3.png[/IMG]](http://s20.photobucket.com/albums/b227/srbaldomero/?action=view&current=pulseaudio3.png)

[[IMG]http://i20.photobucket.com/albums/b227/srbaldomero/th_pulseaudio.png[/IMG]](http://s20.photobucket.com/albums/b227/srbaldomero/?action=view&current=pulseaudio.png)

[[IMG]http://i20.photobucket.com/albums/b227/srbaldomero/th_pulseaudio2.png[/IMG]](http://s20.photobucket.com/albums/b227/srbaldomero/?action=view&current=pulseaudio2.png)

I also attach my multimedia configuration

[[IMG]http://i20.photobucket.com/albums/b227/srbaldomero/th_multimedia.png[/IMG]](http://s20.photobucket.com/albums/b227/srbaldomero/?action=view&current=multimedia.png)

And the problem I get after trying to reproduce a sound in amarok

[[IMG]http://i20.photobucket.com/albums/b227/srbaldomero/th_error.png[/IMG]](http://s20.photobucket.com/albums/b227/srbaldomero/?action=view&current=error.png)

Hopefully you can help me with this really annoying problem, which seems to be quite common though.

Thanks a lot!

---

### Post by markbuntu on 2009-05-19
Do you have the pulsaudio volume control?
(those screenshots were very  fuzzy and hard to see)
If you do open that up and see what is going on. Also read the link in the OP for setting up pulseaudio.

---

### Post by srbaldomero on 2009-05-21
Thanks for answering, Markbuntu

I didn't have pulseaudio volume control, so I installed it and changed all multimedia devices to PulseAudio and it seems to work, although kopete is not making any sound nor gmail's chat... it seems that some aplications work but others aren't.

What's the problem with PulseAudio? (I know, I read your post, but didn't understand what the problem is) I've found too many people having problems and the official solution seems to be to uninstall it and install alsa...

PS: by the way, if you click in one of the images a bigger view is displayed.

Edit: it seems that it worked now. I forgot to put pulseaudio as default for all multimedia tabs, not only "music"

---

### Post by markbuntu on 2009-05-22
The problem is not so much pulseaudio but its faulty implementation in Ubuntu.  I still cannot understand why in Ubuntu the pulseaudio daemon starts by default but the sound scheme is not set up for pulseaudio to actually control all the applications and the pulseaudio volume control is not installed so users can control their sound. 

It is really crazy and it has been going on since hardy and it looks like it will continue with koala. The really crazy thing is that fixing it is sooo simple, a few packages, a few minor changes in configs.

Users of other distributions do not have anywhere near so much trouble with pulseaudio as Ubuntu users. Fedora and Mandriva adopted pulseaudio and have consolidated sound control to pulseaudio a long time ago.

---

### Post by Syniurge on 2009-05-31
Regression since Jaunty, Phonon doesn't map PulseAudio devices to "physical" devices anymore..: [https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/382141](https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/382141)

Does this affect everyone or just me ?


Besides just an update to my old posts: there's no need for autostart or .kde/env script anymore since Jaunty, Phonon automatically starts pulseaudio if installed.

---

### Post by chandra on 2009-06-01
This might be a bit off-topic, but on my system running Kubuntu Jaunty on an AMD 64 installing pulseaudio is incompatible with a functional Skype from medibuntu.

It appears that the standard options on kmixer do not allow the input sources and microphones to be displayed. Once these are selected, and activated, Skype works without hassles.

My thanks to everyone, especially, Markbuntu, for this thread.

---

### Post by wayward4now on 2009-08-13
> **markbuntu said:**
> Well thanks for that. I have not delved into KDE4.2 yet but I expect to be doing so soon. Then I will include specific instructions for KDE4.2.

I followed the instructions, my sound flat out quit with Kubuntu Karmic. I finally removed pulseaudio completely, re-installed alsa and my sound works just fine. The degree of complexity is un-called for, when newbies are called to hand edit conf files. Anything that gets between me and my space games is under the bus! :lolflag:

---

### Post by markbuntu on 2009-08-14
> **wayward4now said:**
> I followed the instructions, my sound flat out quit with Kubuntu Karmic. I finally removed pulseaudio completely, re-installed alsa and my sound works just fine. The degree of complexity is un-called for, when newbies are called to hand edit conf files. Anything that gets between me and my space games is under the bus! :lolflag:

"If you are not using KDE4 on Intrepid 8.10 or Jaunty 9.04 do not attempt this."

That is the first sentence in the OP.

There are a lot of changes in the sound scheme with karmic, both with KDE/phonon and with pulseaudio. 

I would be surprised if it did work.

---

### Post by wayward4now on 2009-08-15
> **markbuntu said:**
> "If you are not using KDE4 on Intrepid 8.10 or Jaunty 9.04 do not attempt this."

That is the first sentence in the OP.

There are a lot of changes in the sound scheme with karmic, both with KDE/phonon and with pulseaudio. 

I would be surprised if it did work.

I did read that, but thought you were referring to KDE3 and/or Hardy version or lower.  So, what will it take to play nice with KDE4 and Gnome both installed in Karmic?? Please note I tried diligently to enable pulse. Again, it really needs to work out of the box for general acceptance. I have friends running other distros who tell me it works a charm. So, I did give it a try. Ric

---

### Post by markbuntu on 2009-08-17
I have not gotten into karmic yet so I cannot say but I will be doing so soon and write something up when I figure it out. Probably sometime in the next few weeks.

---

### Post by chronus_aurelius on 2009-09-04
I followed the instruction from [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/")

But it did not work to get skype to listen to my mic.  So, I turned off pulseaudio as mentioned at the beggining of this post (I did not read the whole thing :-) ), and now it works.  

I know pulseaudio is the future, but I was happy with simple Alsa when using Hardy (now I moved to Jaunty).  I'll probably try to migrate to pulseaudio next time I upgrade the distro, and hopefully it will be seemless by them.

Also, digital out (spdif) was an issue with pulseaudio for my Nvidia audio card (Mobo Asus M2N-SLI Deluxe)

---

### Post by fougas on 2009-09-16
> **Syniurge said:**
> markbuntu's post was for KDE 4.1.
As of KDE 4.2 (available in the backports), the only thing needed to get PulseAudio working within KDE is making "pulse-session" run before KDE launches using the following command in a terminal: 
```
cp /usr/bin/pulse-session ~/.kde/env/pulse-session.sh
```Then after restarting KDE, Phonon devices(not just the "PulseAudio" device) will map to PulseAudio devices instead of ALSA devices.

On fresh installation of kubuntu, and after updating and installing kde 4.3.1 i installed skype and it was working perfectly. Then i installed kubuntu restricted extras and pulse audio appeared at sound settings. At skype sound settings i had no option to choose sound devices cause pulseaudio was the only option. I updated pulseaudio and run tht command you give and everything is working nicely again. Thx to all. :)

:guitar:

---

### Post by Syniurge on 2009-09-16
Hi fougas,

Yes indeed, Skype 2.1 choices are quite narrow with PulseAudio running.. It doesn't allow choosing a different ouput for ringing anymore (I've mentioned the issue to Skype support). There's no solution other than revert to Skype 2.0x (e.g the package from Medibuntu repo).

---

### Post by fougas on 2009-09-16
No . I did what you said and skype (2.1.0.47) is working now nicely. I have sound and i can call.

---

### Post by fougas on 2009-09-16
But why before installing restricted extras, skype was working and after installing the package, pulseaudio appeared and messed my sound? 

Im linux newbie and possibly i ll not understand the answer but im trying. :)

---

### Post by koldo6420 on 2009-09-27
> **markbuntu said:**
> **KDE4 Phonon and PulseAudio on Intrepid and Jaunty**

** Read this entire post before doing anything!!!**

If you are not using KDE4 on Intrepid 8.10 or Jaunty 9.04 do not attempt this. If you are happy with your current Kubuntu Intrepid or Jaunty KDE4 sound setup I strongly suggest that you do not do this. If you have more than one hardware sound device and are having difficulties controlling them all in KDE4/Kubuntu, this may be for you. 

KDE4 comes with Phonon which is the new sound API and sound server for KDE applications. It is a partial replacement for the aRts sound server which was used in previous versions of KDE. Phonon is still very much a work in progress and it is expected that it will improve greatly as it matures so please be patient.

I have two sound cards and a usb headset and a usb webcam with a  mic. I could find no reasonable way to manage all this with Phonon so I use Pulseaudio. Hopefully Phonon will be able to take over many of these functions in the future but for now Pulseaudio will do the work. 

First, an important point, I installed KDE4 on top of Gnome, I use them both so I am probably using quite a few packages  that do not come with the Intrepid or Jaunty Kubuntu install. Just be aware that you may need to get many packages from the repos to satisfy all the dependencies of the packages necessary for this to work if you have installed only Intrepid Kubuntu. If someone could let me know exactly what they needed to install to get all this to work properly it would be much appreciated. 

Here's what I did to get PulseAudio managing all the sound for me in Intrepid  KDE4. 

************************************************************************************************************

** Setting Up Pulse**
First you need to get pulseaudio installed and set up properly if it is not already. You can get all the pulseaudio packages with your package manager. You also need to get a few other items and set up alsa, xine, gstreamer, phonon and  pulseaudio for maximum usability. 

** Launching Pulseaudio**
Pulseaudio does not start by default with KDE (for me anyway) so you need to put a launcher in System Settings/Autostart. I also made a launcher for padevchooser to get the Pulse Audio Applet in the KDE panel. You can also see post #9 in this thread for how to start pulseaudio automatically in KDE4.2

Open System Settings/Advanced/Autostart. Select Add program, type pulseaudio -D in the box and select Run in Terminal and Do not close when command exits click OK. In permissions check Is executable. In Application/Name type Pulseaudio and check that the Command is pulseadio -D so it starts with the defaults from default.pa. click OK. To set up the padevchooser launcher it is basically the same just change pulseaudio to padevchooser.

Log out, log back in and pulseaudio should be running and you should have the Pulse Audio Applet in your panel. Click on the applet and choose Volume Control.
If, when you try to open the volume control you get a message
```

connection refused

```
That means that pulseaudio is not running. This means that something is wrong with the Autostart launcher so you should check that and make sure it is set up correctly.

You can also start the pulseaudio daemon from a terminal with 
```

pulseaudio -D

```
If you need to stop pulseaudio for any reason use this command
```

killall pulseaudio

```

To avoid confusion and difficulties please read through the rest of this post before following the directions in the the link since it was not written with KDE users in mind but will direct you to the the packages you need and give you some basic pulseaudio setup information if you are unfamiliar with it.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

For Jaunty

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

*******************************************************************************
** Setting up KDE4**

In System Settings/Sound make default the first preferred option and in Backend you can prefer either gstreamer or xine since we will set them both up for pulseaudio. If you change these while an application is playing you may lose its sound output and need to restart the application.

**ALSA setup**
In Settings/Default Sound Card asoundconf.gtk choose PulseAudio. This will send everything that goes to alsa to PulseAudio. (asoundconf.gtk is a little gui that sets the alsa default sound card)

**gstreamer Setup**
In Settings/Multimedia System Selector/Audio/plugin select the PulseAudio Sound Server and set Device to Default. 

**xine setup**
Start xine, open the Setup window and select the Audio tab. For audio driver to use select pulseaudio and leave device used for pulseaudio empty.

Log out and log back in and click on the Pulse Audio Applet and choose Volume Control. This will open the pulseaudio volume control. Start up Amarok or some other application that plays sound and make it play something. You should see it in the Volume Control Playback tab and all your hardware sound devices in the Output tab. You can adjust the volume sliders or mute the stream or right click on the stream and change its Output Device. 

In the Settings menu you should now have  Pulse Audio Preferences Sound Server Preferences. You can open that and in the Simultaneous Output tab check the box "Add virtual device for simultaneous output on all local sound cards" and have a virtual device in the Pulseaudio Volume Control/Output Devices that will direct the sound to all your sound hardware at the same time, you can direct a stream to it and control the volume like with any other output device, not a bad thing.


** Sound Capture and recording**
Phonon does not currently offer a alsa default device or a pulseaudio device for sound capture and recording in System Settings/Sound.  For applications using Phonon there is currently no way to direct them to use the  pulseaudio input devices so for now you are stuck with choosing hardware devices in System Settings/Sound for sound capture/recording. This is not so bad because Phonon gives you a lot of choices including the ability to capture hardware output streams as well as inputs.

************************************************************************

If you are having more general problems with setting up your sound or want some more in depth information you can always go to the 10,000 page guide here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)


If this does not work for you or you have questions or comments or something to add concerning KDE4 and sound, please post here. This is very much a first draft but everything has to start somewhere.....and the first thing I need to know is if this creates a total nightmare for Kubuntu Intrepid users.

Best regards,
mark

:P thank you so much!:P

---

### Post by CupofDice on 2009-10-23
I am wondering if I should use the methods here.

I get sound and video in Dragon Player with .wmv, .flv, .rmvb, and so on. System sound is fine too. I do not get sound in Konqueror or Firefox, though the flash video is just fine. Apple Trailer videos do not play at all.

Edit: My sound is now fixed. According to a thread here, it was a pcm bug.

---

### Post by markbuntu on 2009-10-23
> **CupofDice said:**
> I am wondering if I should use the methods here.

I get sound and video in Dragon Player with .wmv, .flv, .rmvb, and so on. System sound is fine too. I do not get sound in Konqueror or Firefox, though the flash video is just fine. Apple Trailer videos do not play at all.

Probably not if everything else is working. That is more likely a flash player problem

---

### Post by CupofDice on 2009-10-23
markbuntu, it was a bug. [http://ubuntuforums.org/showthread.php?t=1297265](http://ubuntuforums.org/showthread.php?t=1297265)

---

### Post by Syniurge on 2009-10-23
Unlikely related, PulseAudio might be useful to you if you want sound from Amarok and Flash player playing simultaneously for example, but won't fix your codec problems.

Do you have you the Medibuntu repo ? (google it). It contains packages for proprietary codecs.

---

### Post by postadelmaga on 2009-11-29
look at [http://www.pulseaudio.org/wiki/PerfectSetup#Xine](http://www.pulseaudio.org/wiki/PerfectSetup#Xine)

there are some official pulseaudio guide on xine  and other program 

i solved  adding that to my $HOME/.xine/config :

```
audio.driver:pulse
```

---

### Post by wd5gnr on 2009-12-06
Strange problem. I had KDE4 and phonon working 100% finally. This went on for a few months until today. I flashed my BIOS (long unrelated story) and forgot to turn on my onboard audio. So, of course, KDE offers to remove it for me and I said no, rebooted, and turned on the audio.

Pulseaudio was fine. Phonon was not. After a bit of coaxing, I now have where the "test" audio works as does audio from amarok. But the KDE notifications do not work unless I use an external player. I can watch the playback tab on the PA volume control and nothing happens so I know it isn't just going to the wrong card. Like I say, I got this to work before.

The key to getting most of it to work, btw, were removing the phonon files in ~/.config/kde-org. I don't think I knew those were there before.

My notifications used to work. Any idea what happened?

Nevermind. Mysteriously started working. Time to go to bed.

---

### Post by wayward4now on 2010-08-16
Mark, with regards to Lucid, I installed Ubuntu first. Then I configured pulse under Gnome. THEN I installed KDE desktop. Pulse works just peachy!!! I've hated pulse since the days when Fedora first added it. Then pulse blew up my favorite space games. NO!!!!

But, I figured that since it was looking like it wasn't going away, I ditched installing Kubuntu and installed Ubuntu instead, later adding KDE4 desktop. Works like a charm!!! I am impressed. Ric

---

### Post by yanaek on 2011-08-01
If i get it right:

Skype works* with ubuntu + kubuntu dekstop packages installed (using KDE4)

Skype doesn't work* with Kubuntu ?

* means, there is no audio capture


Maybe in Kubuntu docs or howto there should be official article, what to do to get Skype working?

---

