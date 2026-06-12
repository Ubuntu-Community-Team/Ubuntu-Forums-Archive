---
title: "[TIP] TV-Viewer, GUI for Hauppauge PVR and other ivtv based TV cards."
date: 2008-04-23
forum: Multimedia Software
---

### Post by saedelaere on 2008-04-23
Hi,

so first of all I want to say hello. I am new to this forum. Normally I post in german forums so excuse my english.

I am developing a program called TV-Viewer. It is a small GUI to control TV Cards like the Hauppauge PVR 150 and [_others_]("http://home.arcor.de/saedelaere/info_eng.html#Supported_devices:").
The reason for me to start with this program was because standard applications like tvtime or kdetv do not support these devices. MythTV or Freevo are good programs but overkill for just wathing tv on your machine.

TV-Viewer is written in Tcl/Tk. It is an easy to use programming language which allows you to develop sophisticated programs and graphical user interfaces.
One big advantage is that software based on Tcl/Tk nearly runs on every platform without big adaptions to the code. However TV-Viewer will only be developed for Linux.

So whats this all about?
In generally you should know, that this is not a complete viewer for wathing tv on Linux. With the gui I am developing you can get rid of using a terminal with pvr devices and it provides some more advantages.
Still you'll have to use one of the provided video players like MPlayer, Kaffeine, Vlc or Xine.

Features:
[LIST]
[*] Easy to use gui to control your device.
[*] Automatic installation (There are no packages for major distributions yet).
[*] Configuration wizard for all relevant settings.
[*] Simple configuration file for your channels. This can be applied by using an automatic channel search with the build in "channel editor". There you can activate or deactivate channels, rename them or change their order.
[*] Volume control.
[*] "On screen display", that shows the actual channel and the volume on your screen.
[*] Videocard control (Hue, Saturation, Brightness and Contrast)
[*] Support for your remote control using Lirc.
[*] Build in user guide.
[*] And many more ;)
[/LIST]

The most recent version of TV-Viewer is 0.7.5-1 which you can download [_here_]("http://home.arcor.de/saedelaere/download_eng.html")
In order to use the program your system has to fullfill the [_minimum requirements_]("http://home.arcor.de/saedelaere/download_eng.html#system_requirements").
Please follow the installation instructions carefully!
You want to see how TV-Viewer looks like? No problem just refer to the [_screenhots_]("http://home.arcor.de/saedelaere/shots_eng.html") section.

Since this is my first release with different languages I wont post the changes from the last version here. They can be found in the [_news_]("http://home.arcor.de/saedelaere/index_eng.html").
I will keep you updated about new versions in this thread. News about future releases and the development stage can also be found on the [_homepage_]("http://home.arcor.de/saedelaere/index_eng.html").

So I hope you'll like the program. If there are any questions please feel free to [_contact_]("http://home.arcor.de/saedelaere/contact_eng.html") me or to post them here.

Regards
Saedelaere

@Admin
If there is a better location for this thread please place it there! Thanks

---

### Post by saedelaere on 2008-05-29
Hi,

this is the first bugfix release for 0.7.5

Bugfixes:
[LIST]
[*] Activation of "Increase Bitrate" in the "Configuration-Wizard" resulted in a serious bug. The main interface did not start anymore.
[*] Automatic station search did not work on some systems because it was not possible to define the VBI device node. For that reason I added a corresponding option in the "Configuration-Wizard".
[*] With Tcl/Tk 8.5 installed the font"DejaVu Sans Mono" could not be recognized though it is installed.
[/LIST]
New features:
[LIST]
[*] Update-Daemon and search for updates manually
[/LIST]

The new version can be downloaded [_here_]("http://home.arcor.de/saedelaere/download_eng.html").
You may read the complete news [_here_]("http://home.arcor.de/saedelaere/index_eng.html").
In addition I enhanced the user guide in some sections with more informations about installation and usage of TV-Viewer.

Have fun with the new version

Saedelaere

---

### Post by Porpoise on 2008-06-15
Great so far! I've got further than I had with any other package - I at least have the tuner working now with VLC, along with my VCR (to copy old VHS tapes onto DVD). The only remaining problem is that I have no sound!

Any ideas on how I can get the sound working too?

I too just want a simple programme like yourself, so I can watch TV in a small window whilst working, and to have a basic PVR function. I went the route of installing myth, ivtv, and every other package I could find. So far, this is the only one that I've even managed to get the stations tuned and have pictures - just the sound issue remains. Once that's fixed I shall be an extremely happy bunny and will finally probably be able to kick windows into touch permanently.

Cheers,
Steve

---

### Post by wolfen69 on 2008-06-15
your sound issue might be fixed [here]("http://ubuntuforums.org/showthread.php?t=776739")

---

### Post by Porpoise on 2008-06-15
Thanks for the pointer. In the meantime, however, it's managed to sort itself out!?! After the fifth install  it just worked! How bizarre is that? Anyway, thanks for your input. All I need to do know is to figure out how I can record the stream...

Cheers,
Steve

---

### Post by Return Privacy on 2008-06-16
Hi all,
I read this post and think it is a great idea. I just want to add that SageTV has a version for Linux. It will allow you to watch tv, and record shows on the computer. I haven't tried the linux version yet, but I have been using the windoze version for 2 years. It really works well. As soon as I learn more about Ubuntu, and linux in general, I will try the linux version of SageTV. Oh, by the way, SageTV recommends hauppauge pvr 150 and other model tv cards. The remote control also works quite well. The support is great from SageTv, they usually answer email questions in 1 day. THey also have a forum like this one that is very helpful.
Just thought you might want to know about the program.

---

### Post by herteljt on 2008-06-16
Thanks for another great tv viewing option!  I initially had trouble with the sound, but I followed wolfen69's link and got everything working.  Looking forward to the record option! :)

EDIT:  After a system reinstall I then reinstalled tv-viewer.  I did not do anything to the sound and instead rebooted.  After reboot the sound worked without any problems.

---

### Post by HappyFeet on 2008-06-16
i tried installing tv-viewer with no luck. it says command not found. any ideas? here's my terminal output:
```
happy@mythbuntu:~$ ls
Desktop    fsv-0.9     level1.txt  Pictures  Shared     tv-viewer075-2
Documents  Incomplete  Music       Public    Templates  Videos
happy@mythbuntu:~$ cd tv-viewer075-2
happy@mythbuntu:~/tv-viewer075-2$ ls
install_data  tv-viewer_install.sh
happy@mythbuntu:~/tv-viewer075-2$ tv-viewer_install.sh
bash: **tv-viewer_install.sh: command not found**
happy@mythbuntu:~/tv-viewer075-2$ 


```

thanks.

---

### Post by ljonesj on 2008-06-16
thats what i get

---

### Post by herteljt on 2008-06-16
> **HappyFeet said:**
> i tried installing tv-viewer with no luck. it says command not found. any ideas? here's my terminal output:
```
happy@mythbuntu:~$ ls
Desktop    fsv-0.9     level1.txt  Pictures  Shared     tv-viewer075-2
Documents  Incomplete  Music       Public    Templates  Videos
happy@mythbuntu:~$ cd tv-viewer075-2
happy@mythbuntu:~/tv-viewer075-2$ ls
install_data  tv-viewer_install.sh
happy@mythbuntu:~/tv-viewer075-2$ tv-viewer_install.sh
bash: **tv-viewer_install.sh: command not found**
happy@mythbuntu:~/tv-viewer075-2$ 


```

thanks.

Did you put a ./ in front of the script name?  Your output doesn't have this.

./tv-viewer_install.sh

---

### Post by Jovec on 2008-06-16
When I was lazy I would just open the /dev/video0 file in VLC/Totem/etc (you might need to "show all files") and then change channels with ivtvtune -cXX from a terminal.  You could always make a symlink to /dev/video0 called livetv.mpg or similar for easier access.

---

### Post by saedelaere on 2008-06-17
> **Porpoise said:**
> Thanks for the pointer. In the meantime, however, it's managed to sort itself out!?! After the fifth install  it just worked! How bizarre is that? Anyway, thanks for your input. All I need to do know is to figure out how I can record the stream...

Cheers,
Steve

Hi Steve,

what did you install five times? TV-Viewer? There shouldn't be any problems with audio, but sometimes my PVR 150 mutes itself. Especially if I did an automatic channel search. I don't understand why but its always worth to try:
```

v4l2-ctl --set-ctrl=mute=0

```
After that I always have sound. On the other side there might also be some problems with pulseaudio. I can't tell you much about that because I'am using openSUSE with KDE. But I think wolfen69 provided you with some good help.


> **Return Privacy said:**
> Hi all,
I read this post and think it is a great idea. I just want to add that SageTV has a version for Linux. It will allow you to watch tv, and record shows on the computer. I haven't tried the linux version yet, but I have been using the windoze version for 2 years. It really works well. As soon as I learn more about Ubuntu, and linux in general, I will try the linux version of SageTV. Oh, by the way, SageTV recommends hauppauge pvr 150 and other model tv cards. The remote control also works quite well. The support is great from SageTv, they usually answer email questions in 1 day. THey also have a forum like this one that is very helpful.
Just thought you might want to know about the program.

I had a closer look on this sageTV. I think there are two things you forgot to mention.

1. One license costs 80 $.
2. It looks exactly like mythTV and you can get mythTV for free.

> **herteljt said:**
> Thanks for another great tv viewing option!  I initially had trouble with the sound, but I followed wolfen69's link and got everything working.  Looking forward to the record option! :)

I'am glad it works for you. In the meantime you can record with cat.

```

cat /dev/video0 > mympegfile.mpeg

```

Now the channel you've tuned will be recorded.
The record wizard for TV-Viewer already exists in my mind. But I think the execution of my plans will take some time.

> **HappyFeet said:**
> i tried installing tv-viewer with no luck. it says command not found. any ideas? here's my terminal output:
```
happy@mythbuntu:~$ ls
Desktop    fsv-0.9     level1.txt  Pictures  Shared     tv-viewer075-2
Documents  Incomplete  Music       Public    Templates  Videos
happy@mythbuntu:~$ cd tv-viewer075-2
happy@mythbuntu:~/tv-viewer075-2$ ls
install_data  tv-viewer_install.sh
happy@mythbuntu:~/tv-viewer075-2$ tv-viewer_install.sh
bash: **tv-viewer_install.sh: command not found**
happy@mythbuntu:~/tv-viewer075-2$ 


```

thanks.

> **ljonesj said:**
> thats what i get

> **herteljt said:**
> Did you put a ./ in front of the script name?  Your output doesn't have this.

./tv-viewer_install.sh

Like herteljt told you you have to put a ./ or sh in front of the script.
```

sh tv-viewer_install.sh

```

> **Jovec said:**
> When I was lazy I would just open the /dev/video0 file in VLC/Totem/etc (you might need to "show all files") and then change channels with ivtvtune -cXX from a terminal.  You could always make a symlink to /dev/video0 called livetv.mpg or similar for easier access.

Jovec you are right,

but I wanted to have more than this. I wanted to have a fontend, with support for my remote control and some more things. My girlfriend often uses my pc to watch tv although she is used to linux she doesn't like a terminal very much ;)

To each his own :)

Best regards

---

### Post by Porpoise on 2008-06-17
> **saedelaere said:**
> Hi Steve,

what did you install five times? TV-Viewer? There shouldn't be any problems with audio, but sometimes my PVR 150 mutes itself. Especially if I did an automatic channel search. I don't understand why but its always worth to try:
```

v4l2-ctl --set-ctrl=mute=0

```After that I always have sound. On the other side there might also be some problems with pulseaudio. I can't tell you much about that because I'am using openSUSE with KDE. But I think wolfen69 provided you with some good help.


I installed TV-Viewer 4 or 5 times - bizarre! Anyway, it's working fine now.

> 

I'am glad it works for you. In the meantime you can record with cat.

```

cat /dev/video0 > mympegfile.mpeg

```Now the channel you've tuned will be recorded.
The record wizard for TV-Viewer already exists in my mind. But I think the execution of my plans will take some time.


At the moment, I'm recording with VLC - the only problem is not being able to see what I'm recording. Will the above allow me to record whilst viewing with VLC? Or is there some way to get VLC to record at the same time as letting you view?

Many thanks for your help
Steve

---

### Post by saedelaere on 2008-06-17
If you are using the cat command you will have to wait about 30 seconds. After that you can open the mpeg file with any video player you want. So you can see what is being recorded. 
But you can't change stations now, because you only got one tuner.
This may also work with vlc but I'am not used to it.

Regards

---

### Post by Actionslacks on 2008-06-20
I seem to have installed TV-Viewer and all the other components ok. But when I start it up by typing TV-Viewer in a terminal it does the set up checks and fails on "Temporal". I can't find anything that says what the values for temporal should be or how to make it work.

---

### Post by saedelaere on 2008-06-20
> **Actionslacks said:**
> I seem to have installed TV-Viewer and all the other components ok. But when I start it up by typing TV-Viewer in a terminal it does the set up checks and fails on "Temporal". I can't find anything that says what the values for temporal should be or how to make it work.

Hi,

could you please open a terminal and post the output of the commands

```

 v4l2-ctl -l

```

```

v4l2-ctl --get-ctrl=temporal_filter

```

And please post the complete ouput of tv-viewer (terminal). Than its easier for me to analyze your problem!

Regards
Saedelaere

---

### Post by Actionslacks on 2008-06-20
> **saedelaere said:**
> Hi,

could you please open a terminal and post the output of the commands

```

 v4l2-ctl -l

```


```

brightness (int)  : min=0 max=255 step=1 default=128 value=128
                       contrast (int)  : min=0 max=127 step=1 default=68 value=68
                     saturation (int)  : min=0 max=127 step=1 default=64 value=64
                            hue (int)  : min=-128 max=127 step=1 default=0 value=0
                         volume (int)  : min=-15 max=15 step=1 default=0 value=0
                           mute (bool) : default=0 value=1
                         mirror (bool) : default=0 value=0
                         invert (bool) : default=0 value=0
             y_offset_odd_field (int)  : min=0 max=128 step=0 default=0 value=0
            y_offset_even_field (int)  : min=0 max=128 step=0 default=0 value=0
                       automute (bool) : default=1 value=1

```




> **saedelaere said:**
> 
```

v4l2-ctl --get-ctrl=temporal_filter

```

And please post the complete ouput of tv-viewer (terminal). Than its easier for me to analyze your problem!

Regards
Saedelaere

```

unknown control 'temporal_filter'

```


At a guess, does that mean I need to install temporal_filter?

---

### Post by saedelaere on 2008-06-20
Hmm what tv-card do you have?
Sure it is supported by ivtv?

Please post the output of 
```

lspci -v

```

May be you will have to try the above as root as well.

```

dmesg | grep ivtv

```

This one would also be good :)
oh and no the temporal filter can't be installed.

Bye

---

### Post by Actionslacks on 2008-06-20
> **saedelaere said:**
> Hmm what tv-card do you have?
Sure it is supported by ivtv?

Probably not. :D I'm almost embarassed to say it's a Hauppauge WinTV HVR 1110. :neutral: Lots of problems with this card, even in Windows using the Hauppauge software.


> **saedelaere said:**
> 
Please post the output of 
```

lspci -v

```

May be you will have to try the above as root as well.


I expect this is the bit you're after.
```

05:02.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Hauppauge computer works Inc. Unknown device 6701
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at f8102000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>


```

> **saedelaere said:**
> 
```

dmesg | grep ivtv

```

This one would also be good :)
oh and no the temporal filter can't be installed.

Bye

That one does nothing.


I have a feeling it's just that it's a rubbish TV card.:( I got Klear to work with it except when I change channels it either crashes or loses sound, but that's for another thread. ;)

---

### Post by saedelaere on 2008-06-20
I'am sorry but with this device TV-Viewer won't work. 

For analogue calbe you may use KDETV or TV-Time. But there you might get some problems with audio. 
For digital signals I would recommend using Kaffeine.
[Here]("http://en.opensuse.org/Hauppauge_HVR-1110_TV-DVB_card") i found an article concerning openSUSE 10.3 and HVR-1110.
This article might also be useful for other distributions.

---

### Post by Porpoise on 2008-06-26
> **saedelaere said:**
> If you are using the cat command you will have to wait about 30 seconds. After that you can open the mpeg file with any video player you want. So you can see what is being recorded. 
But you can't change stations now, because you only got one tuner.
This may also work with vlc but I'am not used to it.

Regards
:smile:
I've done a bit of experimenting and this method also works with VLC. (With respect to another tuner - I have one built into my monitor, so I can watch something else while the system is recording from the Hauppauge). 

My next step is to work out a script to allow me to do timed recordings via a cron. :confused:

Anyone have any suggestions, please?

Thanks for such a great, simple programme. I think it may be time to un-install MythTV and stuff!:KS

:edit
I forgot to mention, by adding a channel for my VHS VCR, I can also record off tapes in the same manner. I am currently using this method to archive some old tapes to DVD.

---

### Post by Porpoise on 2008-06-29
> **Jovec said:**
> When I was lazy I would just open the /dev/video0 file in VLC/Totem/etc (you might need to "show all files") and then change channels with ivtvtune -cXX from a terminal.  You could always make a symlink to /dev/video0 called livetv.mpg or similar for easier access.

I've just tried this method and all I get is static on all channels - when I use TV-Viewer, it changes channels correctly

PS.  It's ivtv-tune  (with a hyphen).

---

### Post by Porpoise on 2008-07-04
After a bit more detective work and trial&error, I've managed to get the command-line channel changing sorted (using VLC and v4l2 instead of ivtv-tune) - also worked out how to use the composite input (from VCR) for better picture quality when recording from VHS tapes:

To set input for Hauppauge PVR-150:  /dev/video0
```

Tuner 1:     v4l2-ctl --set-input=0
S-Video 1:      v4l2-ctl --set-input=1
Composite 1:      v4l2-ctl --set-input=2
S-Video 2:      v4l2-ctl --set-input=3
Composite 2:      v4l2-ctl --set-input=4

```If using the Tuner input, here's how to set the Channel/Frequency:
```

Frequency: 11380 (711.250000 MHz) (BBC 1)  =>  v4l2-ctl -f 711.250
Frequency: 10484 (655.250000 MHz) (BBC 2)  =>  v4l2-ctl -f 655.250
Frequency: 10100 (631.250000 MHz) (ITV 1)  =>  v4l2-ctl -f 631.250
Frequency: 10868 (679.250000 MHz) (CHA 4)  =>  v4l2-ctl -f 679.250

```This is for UK PAL of course - you will need to use the relevant frequencies for your area.

The command-line for recording the stream:
```

vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'

```Obviously, you will need to set the path according to your own system setup.


So, the full sequence, if you wanted to record, say, BBC1, would be:
```

v4l2-ctl --set-input=0
v4l2-ctl -f 711.250

vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'

```The next step is to work out how to enable VLC to view whilst recording, then to work out setting timed recordings

](*,)

---

### Post by Porpoise on 2008-07-06
Phew! Finally figured out how to get VLC to display the stream whilst recording:

```
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'
```Just needed to add "dst=display" into the correct position in the command line.

Although I've slightly hijacked this thread (it was originally for TV-Viewer - sorry saedelaere) I feel that there are probably other people out there that maybe reading this thread, that are trying to do the same thing and may benefit from this information.

(You can still benefit from using TV-Viewer to change Channel)

:) Steve

---

### Post by redchief on 2008-07-06
E: /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.1_all.deb: subprocess pre-installation script returned error exit status 1
hmmmm
 punt?

---

### Post by redchief on 2008-07-06
won't let me log into server...
back to the manual.....

---

### Post by saedelaere on 2008-07-08
> **redchief said:**
> E: /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.1_all.deb: subprocess pre-installation script returned error exit status 1
hmmmm
 punt?

> **redchief said:**
> won't let me log into server...
back to the manual.....

Are you sure you wanted to post in this Thread?

---

### Post by saedelaere on 2008-07-24
Today I make a new version of TV-Viewer available. Actually the next planed release was Version 0.8. But the new gui is'nt ready yet and this may take a bit more time. Meanwhile lot's of users asked for a record function so I decided to bring the development of this feature forward.

Bugfixes:
[list]
[*] TV-Cards which do not provide a VBI device node could no longer be used. This problem has been solved.
[*] The tool v4l2-ctl was not recognized by the configuration wizard from version 1.2.0 (ivtv) upwards. Fixed.
[*] Some text improvements.
[*] Smaller things in the source code.
[/list]
New features:
[list]
[*] Record wizard, which can be operated from a terminal. Time controlled recordings  and many more.
[*] TV-Viewer was previously installed into the users home directory. This has been changed. Now only the configuration files are located there.
[*] Diagnostic routine is now part of TV-Viewer and can be started from within the GUI.
[*] New installer.
[*] Packages for various distributions.
[/list]
The installation has changed, more informations in the [_Download_]("http://home.arcor.de/saedelaere/download_eng.html") section and in the [_user guide_]("http://home.arcor.de/saedelaere/doc_eng.html").
The record-wizard only supports recordings from the tuner of the tv-card. This will be changed soon see [_roadmap_]("http://home.arcor.de/saedelaere/info_eng.html#Roadmap:").
New Screenshots are available soon.
If you encounter any problems, or you have improvement suggestions, [_contact_]("http://home.arcor.de/saedelaere/contact_eng.html") me.

Best regards
Saedelaere

---

### Post by herteljt on 2008-07-24
Thank you so much for all the work.  I have been using tv-viewer for the last month and absolutely loving it!  I just installed the updated version and I am trying out the recording option.

---

### Post by saedelaere on 2008-07-26
It's good to hear something like that :)

Please let me know what you think of the record function. Don't forget to read the user guide it provides some really important infos.

Best Regards

---

### Post by wolfen69 on 2008-07-26
> **Porpoise said:**
> Phew! Finally figured out how to get VLC to display the stream whilst recording:

```
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'
```Just needed to add "dst=display" into the correct position in the command line.

Although I've slightly hijacked this thread (it was originally for TV-Viewer - sorry saedelaere) I feel that there are probably other people out there that maybe reading this thread, that are trying to do the same thing and may benefit from this information.

(You can still benefit from using TV-Viewer to change Channel)

:) Steve

thanks for the info. i had been looking for a way to do just that. worked perfectly.

---

### Post by Porpoise on 2008-07-26
> **wolfen69 said:**
> thanks for the info. i had been looking for a way to do just that. worked perfectly.

I'm glad someone else has found it useful. I've also used Gnome Schedule 2.0.2 to set up cron templates for PVR scheduled recording and channel changing. If anyone is interested in that, let me know and I'll post the info.

I find it easier than saedelaere's command-line approach but, hopefully, he'll sort out a GUI for it soon. Keep cranking saedelaere - your efforts are greatly appreciated by lot's of people here!


Here's a screenshot of the list of templates (some are commands - some run a script). All you have to do (once the templates are setup) is edit the templates and set the times you want them to run. All very easy in a GUI.

[IMG]http://www.srenterprises.co.uk/images/gnome_schedule_screenshot.png[/IMG]

I use the Start TV for starting the TV in the morning... :)

---

### Post by saedelaere on 2008-07-27
> **Porpoise said:**
> I'm glad someone else has found it useful. I've also used Gnome Schedule 2.0.2 to set up cron templates for PVR scheduled recording and channel changing. If anyone is interested in that, let me know and I'll post the info.

I find it easier than saedelaere's command-line approach but, hopefully, he'll sort out a GUI for it soon. Keep cranking saedelaere - your efforts are greatly appreciated by lot's of people here!


Here's a screenshot of the list of templates (some are commands - some run a script). All you have to do (once the templates are setup) is edit the templates and set the times you want them to run. All very easy in a GUI.

[IMG]http://www.srenterprises.co.uk/images/gnome_schedule_screenshot.png[/IMG]

I use the Start TV for starting the TV in the morning... :)

Yes you`re right a gui is in most cases better.
But I wanted so start with my record wizard now, because so many people asked for one. Let's see how it works.
I appreciate your efforts in showing some alternatives.

Regards
Saedelaere

---

### Post by revealed on 2008-07-27
Hi there!

My Name is revaled. Im originally using OpenSuSE 10.3, too. I just wanted to popp up and tell you that i am using TV-Viewer too, since early beta.

Personally im adding Videotextfunction button by hand.

Also im starting TV-Viewer as Tray application.

Heres how i start as tray:
```
cd /home/user
```
```
touch TVviewer.sh
```
content:
```
#!/bin/sh
xterm -e su -c /home/user/ivtvreload.sh && ksystraycmd --ownicon --icon /home/user/YourpersonaltrayICON.png tv-viewer --v4l2audio
```
Why this?::
Due to kopete hijacking Videodevicenode as Webcam:
```
cd /home/user
```
```
touch ivtvreload.sh
```
content:
```
#!/bin/sh
# Workaround after kopete has started.
echo "Unloading ivtv!"
rmmod ivtv
echo "Reloading module ivtv!"
modprobe ivtv
echo "in 3 seconds you can watch TV even if Kopete is running! ... starting Frontend..."
sleep 3
# /EDF

```
On Desktop i placed an Icon which points to:
```
'/home/user/TVviewer.sh'
```
It is holding the ICON for TV-Viewer. (Tux with a tv-control).


How i add Videotext Function each release till now:
You will need MTT4 Packages for this purpose and /dev/vbi0 enabled;;
-> Edit tv-viewer.tcl and add the following new lines: (no need to delete any);
**+778-781** (Button optics and command)
```
        button $base.button_vbi \
                -command vbi \
                -text Videotext \
                -width 11
```

**+975-975** (Button placement)
```
grid $base.button_vbi -in $base.frame#6 -row 1 -column 2
```
**+ 1452 - 1455** (Definition of the command)
```
proc vbi {} {
exec mtt4 /dev/vbi0 &
}
```

In hope any except me enjoys this little mod; 
Dear Greetings,

R

PS.: My personal Trayicon is the tv-control which is held by Tux in the desktop icon. So if the taste was like mine it could look like in the attached screen of the half part of my desktop.
PPS.: If anyone knowing a good way to fake a videodevice to set within Kopete in order it leaves fingers from my PVR, please let me know.

---

### Post by saedelaere on 2008-10-14
Here it is. The probably last version of the 0.7.x development branch. Nevertheless there will be one more version (probably beta), which allows the use of frequencies instead channels. This is because some users asked for it and with this feature you may be able to finetune your stations.
But now to the new version. There are no big changes this time.

Bugfixes:
[list]
[*] After an automatic station search the tv-card gets muted. Fixed.
[*] Smaller things in the source code.
[/list]

New features:
[list]
[*] A standard "cat" is now used to perform recordings. This means mencoder is no longer needed.
[*] If you try to start TV-Viewer Gui while a recording you'll be asked if the recording should be canceled.
[*] Command line option --vresolution replaces --vaspect in tv-viewer_rec. You may now specifie the resolution of the recording.
[/list]

The project is now also hosted on [_sourceforge.net_](https://sourceforge.net/projects/tv-viewer/). But the old website will stay active. I mainly use sourceforge.net to host the downloads and to provide a [_forum_](https://sourceforge.net/forum/?group_id=238442) and a [_bugtracker_](https://sourceforge.net/forum/?group_id=238442).

Work on Version 0.8.x suffers at the moment from my lack of time. Check back for any news on this version.

But for now you may want to enjoy [_version 0.7.6.2_](http://home.arcor.de/saedelaere/download_eng.html)

Best regards

---

### Post by of_darkness on 2008-10-19
> No valid channels_europe-west.conf
Please create one

Starting automatic station search, please wait!
PAL-BGH: not found


when running the wizard... live in Sweden (and i have analog cable-tv)
so  i should have PAL-BGH

and i have a wintv-350 tvcard and ivtv is installed and working

```
[ anomander-rake: ~ ]$ dmesg | grep ivtv
[   19.969034] ivtv:  Start initialization, version 1.4.0
[   19.969087] ivtv0: Initializing card #0
[   19.969092] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   19.969144] ivtv 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.023259] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   20.149712] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   20.336869] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   20.347503] msp3400 0-0040: MSP4418G-B3 found @ 0x80 (ivtv i2c driver #0)
[   20.422976] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   20.458852] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   20.518317] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   20.518344] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   20.518374] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   20.518398] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   20.518422] ivtv0: Registered device radio0 for encoder radio
[   20.518446] ivtv0: Registered device video16 for decoder MPG (1024 kB)
[   20.518470] ivtv0: Registered device vbi8 for decoder VBI (64 kB)
[   20.518497] ivtv0: Registered device vbi16 for decoder VOUT
[   20.518521] ivtv0: Registered device video48 for decoder YUV (1024 kB)
[   20.518523] ivtv0: Initialized card #0: Hauppauge WinTV PVR-350
[   20.518570] ivtv:  End initialization
[   52.722734] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   52.764128] ivtv0: Loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   52.960932] ivtv0: Encoder revision: 0x02060039
[   52.961084] ivtv0: Decoder revision: 0x02020023
[   53.054942] ivtv0: Loaded v4l-cx2341x-init.mpg firmware (155648 bytes)

```

and im running ubuntu intrepid whit kde3.5.10 as desktop.

---

### Post by saedelaere on 2008-10-19
Hi,

please try the following command:
```

scantv -c /dev/video0 -C /dev/vbi0 -f europe-west -n PAL-BGH

```

Does this command work for you?

Can you add Stations manually with the "Station-Editor"?

Regards

---

### Post by saedelaere on 2008-10-20
At the moment I'am working on an automatic station serch which does not depend on scantv. This could also fix your problem. 

Regards

---

### Post by of_darkness on 2008-10-20
> **saedelaere said:**
> Hi,

please try the following command:
```

scantv -c /dev/video0 -C /dev/vbi0 -f europe-west -n PAL-BGH

```Does this command work for you?

Can you add Stations manually with the "Station-Editor"?

Regards

> [ anomander-rake: ~ ]$ scantv -c /dev/video0 -C /dev/vbi0 -f europe-west -n PAL-BGH
PAL-BGH: not found
[ anomander-rake: ~ ]$


Well if i knew any stations to add icould test it but as i dont know any stations..

---

### Post by of_darkness on 2008-10-20
> **saedelaere said:**
> At the moment I'am working on an automatic station serch which does not depend on scantv. This could also fix your problem. 

Regards

ahh sounds intresting:) would love to be able to use my tv card:) as it is it jsut sits there since sevreal months back cause i couldent make it work whit any tools:/

---

### Post by saedelaere on 2008-10-21
> **of_darkness said:**
> Well if i knew any stations to add icould test it but as i dont know any stations..

Interesting that the scantv command did not work. This is either a bug of ivtv or ubuntu intrepid.You could start scantv without any command line options.
```

scantv -o scans.tmp

```
If it works, it creates a file with all your stations. The you could add them manually. 

> **of_darkness said:**
> ahh sounds intresting:) would love to be able to use my tv card:) as it is it jsut sits there since sevreal months back cause i couldent make it work whit any tools:/

I have to admit, I already finished it yesterday. But it's not completely tested. I will send you something this evening, which you can work with.

Regards

---

### Post by saedelaere on 2008-10-21
> **saedelaere said:**
> Interesting that the scantv command did not work. This is either a bug of ivtv or ubuntu intrepid.You could start scantv without any command line options.
```

scantv -o scans.tmp

```
If it works, it creates a file with all your stations. The you could add them manually. 



I have to admit, I already finished it yesterday. But it's not completely tested. I will send you something this evening, which you can work with.

Regards

ok I would send you something if I could :)
I decided to change some more things. This could take some more days. Sorry for that.

---

### Post by of_darkness on 2008-10-21
> **saedelaere said:**
> ok I would send you something if I could :)
I decided to change some more things. This could take some more days. Sorry for that.
ahh:) take your time :) i have vaited this long i can shourly wait a wile longer if it makes the app better ore more stable or so:)

---

### Post by of_darkness on 2008-10-22
> **saedelaere said:**
> Interesting that the scantv command did not work. This is either a bug of ivtv or ubuntu intrepid.You could start scantv without any command line options.
```

scantv -o scans.tmp

```
If it works, it creates a file with all your stations. The you could add them manually. 



I have to admit, I already finished it yesterday. But it's not completely tested. I will send you something this evening, which you can work with.

Regards

```
[ anomander-rake: ~ ]$ scantv -o scans.tmp

please select your TV norm
   0: NTSC
   1: NTSC-M
   2: NTSC-M-JP
   3: NTSC-M-KR
   4: NTSC-443
   5: PAL
   6: PAL-BG
   7: PAL-H
   8: PAL-I
   9: PAL-DK
  10: PAL-M
  11: PAL-N
  12: PAL-Nc
  13: PAL-60
  14: SECAM
  15: SECAM-B
nr ? 6

please select a frequency table
   0: us-bcast
   1: us-cable
   2: us-cable-hrc
   3: japan-bcast
   4: japan-cable
   5: europe-west
   6: europe-east
   7: italy
   8: newzealand
   9: australia
  10: ireland
  11: france
  12: china-bcast
  13: southafrica
  14: argentina
  15: australia-optus
  16: russia
nr ? 5
invalid value for input: Television
valid choices for "input": "Tuner 1", "S-Video 1", "Composite 1", "S-Video 2", "Composite 2", "Composite 3"
vbi: open failed [/dev/vbi]
open /dev/vbi: No such file or directory
[ anomander-rake: ~ ]$     
```

so it seams that i jhave 2 wait 4 your app:P

---

### Post by saedelaere on 2008-10-22
> **of_darkness said:**
> ```
[ anomander-rake: ~ ]$ scantv -o scans.tmp

please select your TV norm
   0: NTSC
   1: NTSC-M
   2: NTSC-M-JP
   3: NTSC-M-KR
   4: NTSC-443
   5: PAL
   6: PAL-BG
   7: PAL-H
   8: PAL-I
   9: PAL-DK
  10: PAL-M
  11: PAL-N
  12: PAL-Nc
  13: PAL-60
  14: SECAM
  15: SECAM-B
nr ? 6

please select a frequency table
   0: us-bcast
   1: us-cable
   2: us-cable-hrc
   3: japan-bcast
   4: japan-cable
   5: europe-west
   6: europe-east
   7: italy
   8: newzealand
   9: australia
  10: ireland
  11: france
  12: china-bcast
  13: southafrica
  14: argentina
  15: australia-optus
  16: russia
nr ? 5
invalid value for input: Television
valid choices for "input": "Tuner 1", "S-Video 1", "Composite 1", "S-Video 2", "Composite 2", "Composite 3"
vbi: open failed [/dev/vbi]
open /dev/vbi: No such file or directory
[ anomander-rake: ~ ]$     
```

so it seams that i jhave 2 wait 4 your app:P

Its nearly finished. Perhaps you may have it later today. 

Regards

---

### Post by cchester on 2008-10-23
Hello,

Thanks for the program. I was looking for something like this.

I ran sudo ./sudo tv-viewer_install.sh and I get the following error : exec: 3: wish: not found. I did this in Ubuntu 8.04.

What does this error mean?

Also is there any way you can make a .deb file for Ubuntu or teach/tell me how to do it so I can use your program?

Thanks for any help.

---

### Post by saedelaere on 2008-10-23
> **cchester said:**
> Hello,

Thanks for the program. I was looking for something like this.

I ran sudo ./sudo tv-viewer_install.sh and I get the following error : exec: 3: wish: not found. I did this in Ubuntu 8.04.

What does this error mean?

Also is there any way you can make a .deb file for Ubuntu or teach/tell me how to do it so I can use your program?

Thanks for any help.

Hi,

in the [download section]("http://home.arcor.de/saedelaere/download_eng.html#system_requirements") on my Homepage you can see what is necessary to run the Program. In the [user guide]("http://home.arcor.de/saedelaere/doc/TV-Viewer_0.7_help_file_eng.html#Specific_informations_for_different_") is a detailed list of packages you'll need for ubuntu.

So start synaptics and install:
ivtv-utils tcl tk libtk-img xosd-bin xdg-utils and scantv

After that the installation should work.
The user guide provides some more help about recent questions and how to use the software. Oh and be sure to use one of the [supported tv-cards]("http://home.arcor.de/saedelaere/info_eng.html#Supported_devices:") ;)

For the *.deb file. I already tried that. But it is nit that easy and at the moment I don't have time for this task. If you want to build one PERFECT, but I can't tell you how :cool:

Regards

EDIT: There may be different version of Tcl/Tk in synaptics. Be sure to install version >= 8.5, because the next version will only run on that version.

---

### Post by cchester on 2008-10-23
Hello,

Thanks for the reply.

Ok I did like you said and made sure the following were installed ivtv-utils tcl tk libtk-img xosd-bin xdg-utils and scantv and then the ones that were not installed I installed.

Then I ran sudo ./tv-viewer_install.sh and everything went great (by the way I think your instruction to use ./sudo tv-viewer_install.sh is wrong because that wouldn't work for me I had to type it the other way).

So I then ran tv-viewer and got the following error :
Program error.
There is a missing dependency.
Please install the package tkimg!

Have a closer look to the user guide for the system requirements.

I did everything like your instructions said and still no luck. Can you help me out some more please?

I did try to install from source tkimg but after I run configure it wont go any further.

This is what I get from running ./configure
loading cache ./config.cache
checking for Cygwin environment... (cached) no
checking for mingw32 environment... (cached) no
checking how to run the C preprocessor... (cached) cc -E
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking if the compiler understands -pipe... yes
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether make sets ${MAKE}... (cached) yes
checking for ranlib... (cached) ranlib
checking for object suffix... (cached) o
checking for executable suffix... (cached) no
checking for required early compiler flags... (cached) (cached)  _LARGEFILE64_SOURCE
checking for 64-bit integer type... (cached) long long
checking for struct dirent64... (cached) no
checking for struct stat64... (cached) yes
checking for off64_t... (cached) yes
configuring in libz/tcl
running /bin/sh ./configure  --cache-file=../.././config.cache --srcdir=. 
loading cache ../.././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in libpng/tcl
running /bin/sh ./configure  --cache-file=../.././config.cache --srcdir=. --with-zlibtcl=/home/chris/tkimg1.3/libz/tcl
loading cache ../.././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in libtiff/tcl
running /bin/sh ./configure  --cache-file=../.././config.cache --srcdir=. 
loading cache ../.././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in libjpeg/tcl
running /bin/sh ./configure  --cache-file=../.././config.cache --srcdir=. 
loading cache ../.././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in base
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. 
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in bmp
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in gif
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in ico
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in jpeg
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base --with-jpegtcl=/home/chris/tkimg1.3/libjpeg/tcl
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in pcx
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in pixmap
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in png
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base --with-pngtcl=/home/chris/tkimg1.3/libpng/tcl --with-zlibtcl=/home/chris/tkimg1.3/libz/tcl
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in ppm
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in ps
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in sgi
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in sun
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in tga
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in tiff
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base --with-tifftcl=/home/chris/tkimg1.3/libtiff/tcl --with-zlibtcl=/home/chris/tkimg1.3/libz/tcl --with-jpegtcl=/home/chris/tkimg1.3/libjpeg/tcl
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in window
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in xbm
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
configuring in xpm
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=. --with-tkimg=/home/chris/tkimg1.3/base
loading cache .././config.cache
checking for correct TEA configuration... ok
checking for Tcl configuration... configure: warning: Cannot find Tcl configuration definitions
creating ./config.status
creating Makefile

Any ideas because I can't run the next step.

Oh I know my card should be ok because I have run it under mythbuntu.

Here is what lspci -v says:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: f4000000-f7ffffff
	Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f03c:2a58
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 221
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c400 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a58
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 150
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

01:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem
	Subsystem: Conexant Unknown device 200c
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at fdee0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at bc00 [size=8]
	Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Unknown device 196e:0523
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ac00 [size=128]
	[virtual] Expansion ROM at fbfe0000 [disabled] [size=128K]
	Capabilities: <access denied>


This is what dmesg | grep ivtv says:

[   49.412428] ivtv:  Start initialization, version 1.1.0
[   49.412539] ivtv0: Initializing card #0
[   49.412543] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   49.421518] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   49.498224] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   49.596296] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   49.599293] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   49.659895] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   49.822348] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   50.147566] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   50.147578] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   50.147593] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   50.147605] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   50.147616] ivtv0: Registered device radio0 for encoder radio
[   50.147618] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   50.147632] ivtv:  End initialization
[   63.479198] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   63.556221] ivtv0: Encoder revision: 0x02060039


I hope that any of this helps in try to get this working for me because I am so close and hate that I am stuck and can't get any further.

Please help. Thanks.

---

### Post by cchester on 2008-10-23
Hello,

Ok I got this working by doing a manual install of TCL. I just followed the directions at the beginning.

Works great by the way. I finally have what i wanted a simple tv viewer.

I can't wait for the option to record. Once that is implemented then this will be awesome to have.

Thanks again for the program and have you thought about adding it to launchpad?

---

### Post by of_darkness on 2008-10-23
> **saedelaere said:**
> Its nearly finished. Perhaps you may have it later today. 

Regards

Ohh sounds good:)

---

### Post by saedelaere on 2008-10-24
> **cchester said:**
> Hello,

Ok I got this working by doing a manual install of TCL. I just followed the directions at the beginning.

Works great by the way. I finally have what i wanted a simple tv viewer.

I can't wait for the option to record. Once that is implemented then this will be awesome to have.

Thanks again for the program and have you thought about adding it to launchpad?

So you installed activestate Tcl? I use this one myself. Glad it worked for you. On the other hand I tried to install and run the program on ubuntu 8.04 with the packages I mentioned. It worked perfectly and the package libtk-img was found. Don't know what went wrong with your setup?

Tv-Viewer already has a record function but it is command line only. I will write a gui sometimes. 

I just added the program to sourceforge.net, launchpad is new to me. Will have a look on it.

> **of_darkness said:**
> Ohh sounds good:)

Currently I'am doing some final tests. So this evening it will be released, unless I'll face bigger problems during the testing !

Regards

---

### Post by cchester on 2008-10-24
Yeah I don't know what was up with Tcl and having to install the it manualy considering that after doing and checking what you said everything went smooth but sure enough once it was there everything was fine.

I will be trying it again once 8.10 is officially released. About the recording I like the button you have there and being able to just click on it and it record than having do the command line record thing but I can do that for the time being.

I just though maybe Launchpad because you would get more attention and more people might see it and try it or use it and help test it. Plus if it becomes popular enough Ubuntu might put it in the repository. Ya never know.

I am going to like using this either way and see it progress. Like I said this is something I have wanted for a while after getting my card and having to use other methods to get it to work.

Thanks.

---

### Post by herteljt on 2008-10-26
Hi all,
Just and FYI if you are using tv-viewer with vlc and plan to update to Ubuntu 8.10.  I just updated to Ubuntu 8.10 and in the process updated VLC to version 0.9.4.  TV-Viewer 0.7.6.2 was working fine before the update, but after my update VLC would not open up properly.

I changed the videoplayer options line to read
```
 pvr:// pvr:
```  
and this solved the problem.

Thanks again for a great program!

---

### Post by saedelaere on 2008-10-28
TV-Viewer 0.7.7b1

The first beta version for public use. It brings some new features as well as some bugfixes. Nevertheless it is beta release. So there could be some problems :)

Bugfixes:
[LIST]
[*] Translation issues.
[*] The scheduler produced an error when the video device is already in use.
[*] Minor things in the code.
[/LIST]
New features:
[LIST]
[*] Now using frequencies instead channels. This will allow you to use finetuning.
[*] Automatic station search no longer depends on scantv or a working VBI device node. Now all users should be able to use it.
[*] Update-Daemon is now a News-Reader.
[*] Videocard control options (Hue, saturation...) and video standard (Pal, secam, ntsc) will only be changed if necessary.
[*] Splash screen.
[/LIST]
In fact I've changed hundred of lines of code. Not all changes are visible to the user, but it should be worth to upgrade. Note that TV-Viewer now depends on Tcl/Tk version 8.5 or higher. If this version is not provided by your distribution you may use [ActiveTcl]("http://www.activestate.com/Products/activetcl/index.mhtml") from ActiveState.
These new features are a preparatory work for version 0.8.x.
Normaly BETA versions are only announced on the website and with the News-Reader of TV-Viewer. As this version brings lot's of changes I will announce it the same way as always.

See the [download section]("http://home.arcor.de/saedelaere/download_eng.html#Beta_releases") on how to get this version.

Some ultimate words to the last version of TV-Viewer. Until today [sourceforge.net]("https://sourceforge.net/project/stats/detail.php?group_id=238442&ugn=tv-viewer&type=prdownload&mode=60day&package_id=0") registrated 154 downloads of this version. This is far more as I expected and it motivates me to begin as early as possible with the 0.8.x development branch.

Best regards
Saedelaere

---

### Post by saedelaere on 2008-10-29
> **herteljt said:**
> Hi all,
Just and FYI if you are using tv-viewer with vlc and plan to update to Ubuntu 8.10.  I just updated to Ubuntu 8.10 and in the process updated VLC to version 0.9.4.  TV-Viewer 0.7.6.2 was working fine before the update, but after my update VLC would not open up properly.

I changed the videoplayer options line to read
```
 pvr:// pvr:
```  
and this solved the problem.

Thanks again for a great program!

Thanks for your feedback. I changed the standard options for vlc to pvr:// and the tooltip now informs you which option you should use.

> **of_darkness said:**
> Ohh sounds good:)

Please let me know if the new automatic station search works for you!

---

### Post by maasnet@chello.nl on 2008-10-29
After installation release 0.7.7b1 I get this error:

maasnet@ubuntu:~$ tv-viewer

-------------------------------

TV-Viewer is starting

You've installed a new version of TV-Viewer.

Could not locate a configuration file!
Will use standard values.
Error in startup script: can't read "option(brightness)": no such element in array
    while executing
"info exists $option($opt)"
    ("foreach" body line 2)
    invoked from within
"foreach opt [split $config_options] {
		if {[info exists $option($opt)]} {
			puts "$opt\: $option($opt)"
		}
	}"
    invoked from within
"if {[file exists "$where_is_home/config/tv-viewer.conf"]} {
	set open_config_file [open "$where_is_home/config/tv-viewer.conf" r]
	while {[gets $open_..."
    (file "/usr/bin/tv-viewer" line 180)

---

### Post by saedelaere on 2008-10-29
> **maasnet@chello.nl said:**
> After installation release 0.7.7b1 I get this error:

maasnet@ubuntu:~$ tv-viewer

-------------------------------

TV-Viewer is starting

You've installed a new version of TV-Viewer.

Could not locate a configuration file!
Will use standard values.
Error in startup script: can't read "option(brightness)": no such element in array
    while executing
"info exists $option($opt)"
    ("foreach" body line 2)
    invoked from within
"foreach opt [split $config_options] {
		if {[info exists $option($opt)]} {
			puts "$opt\: $option($opt)"
		}
	}"
    invoked from within
"if {[file exists "$where_is_home/config/tv-viewer.conf"]} {
	set open_config_file [open "$where_is_home/config/tv-viewer.conf" r]
	while {[gets $open_..."
    (file "/usr/bin/tv-viewer" line 180)


Like I said it is a BETA version :cool:
I already discovered this bug and some more myself. Sorry for that. I uploaded a new Version 0.7.7b2

Please give me a short note if it works now!

Regards

---

### Post by cchester on 2008-10-30
Hello,

I just installed tv-viewer-0.7.7b2 and I ran the wizard and station stuff and now I am getting nothing but a black screen and static on every channel.

Any ideas. This was working great before.

Thanks for any help.

Oh this is what I get when I run the station editor.

Station-Editor is starting
Error in startup script: couldn't open "/home/saedelaere/Eigene Webs/TV-Gui_buttons/Bildbearbeitung/arrow_up_green.png": no such file or directory
    while executing
"image create photo -file "/home/saedelaere/Eigene Webs/TV-Gui_buttons/Bildbearbeitung/arrow_up_green.png""
    invoked from within
"set arrow_up [image create photo -file "/home/saedelaere/Eigene Webs/TV-Gui_buttons/Bildbearbeitung/arrow_up_green.png"]"
    (file "/usr/share/tv-viewer/data/channel_edit.tcl" line 198)

Hope it helps.

---

### Post by saedelaere on 2008-10-30
> **cchester said:**
> Hello,

I just installed tv-viewer-0.7.7b2 and I ran the wizard and station stuff and now I am getting nothing but a black screen and static on every channel.

Any ideas. This was working great before.

Thanks for any help.

Oh this is what I get when I run the station editor.

Station-Editor is starting
Error in startup script: couldn't open "/home/saedelaere/Eigene Webs/TV-Gui_buttons/Bildbearbeitung/arrow_up_green.png": no such file or directory
    while executing
"image create photo -file "/home/saedelaere/Eigene Webs/TV-Gui_buttons/Bildbearbeitung/arrow_up_green.png""
    invoked from within
"set arrow_up [image create photo -file "/home/saedelaere/Eigene Webs/TV-Gui_buttons/Bildbearbeitung/arrow_up_green.png"]"
    (file "/usr/share/tv-viewer/data/channel_edit.tcl" line 198)

Hope it helps.

First of all there is new version online 0.7.7b3
Sorry for these major bugs, but now it should work.

Second tv-viewer now uses standard configuration values if you don't specifie your own configuration. Configuration files from tv-viewer <= 0.7.6.2 can no longer be used. 

Third the format of the stations config file has been changed. So your old file won't work out of the box. After creating your own configuration with the wizard you should start the stations-editor. If you had a stations file it will be read in. As you can see older station files used Channels instead of frequencies.
Now use Options --> Convert stations list
Your stations list will be transformed. Save the list and exit the Editor.
You should be fine wathing tv.

Regards

---

### Post by maasnet@chello.nl on 2008-10-30
Hello,

It works now very good.

The station-editor make this conf:

Station-Editor is starting

Initializing main window

No valid channels_europe-west.conf
Please create one

Starting automatic station search, please wait!
Signal detected on 182.250 MHz.
Signal detected on 224.250 MHz.
Signal detected on 231.250 MHz.
Signal detected on 238.250 MHz.
Signal detected on 280.250 MHz.
Signal detected on 519.250 MHz.
Signal detected on 527.250 MHz.
Signal detected on 535.250 MHz.
Signal detected on 543.250 MHz.
Signal detected on 551.250 MHz.
Signal detected on 559.250 MHz.
Signal detected on 567.250 MHz.
Signal detected on 623.250 MHz.
Signal detected on 631.250 MHz.
Signal detected on 671.250 MHz.
Signal detected on 719.250 MHz.
Signal detected on 727.250 MHz.
Signal detected on 735.250 MHz.
Signal detected on 751.250 MHz.
Signal detected on 767.250 MHz.
Signal detected on 783.250 MHz.
Signal detected on 791.250 MHz.
Signal detected on 799.250 MHz.
Signal detected on 815.250 MHz.

Tried to tune for
Error message: Invalid channel for 'europe-west'
child process exited abnormally

Station searched finished.

I edit the conf manually and gives now a perfect signal:

<Ned1> 216.000
<Ned2> 184.000
<Ned3> 192.000
<RTL4> 720.000
<RTL5> 728.000
<SBS6> 792.000
<RTL7> 736.000
<RTL8> 536.000
<Veronica/Jetix> 672.000
<Net5> 784.000
<LO Ede> 256.000
<TV Gelderland> 264.000
<UPC> 176.000
<Lokal Plus> 552.000
<VRT1> 200.000
<Ketnet/Canvas> 208.000
<BBC1> 272.000
<BBC2> 280.000
<ARD> 224.000
<ZDF> 232.000
<WDR> 240.000
<NDR> 624.000
<CNN> 752.000
<Discovery Channel> 800.000
<Euro News> 528.000
<Eurosport> 816.000
<MTV> 768.000
<TMF> 568.000
<Nickelodeon> 560.000
<RAI Uno> 520.000
<Animal Planet> 632.000

Thanks for the program!!

[IMG]http://www.ubuntu-pics.de/bild/5003/screenshot_02_jtUwOF.jpg[/IMG]

---

### Post by saedelaere on 2008-10-30
Glad to hear it works for you!

So far I did not hear of any new bugs. So I can continue with development of TV-Viewer

---

### Post by of_darkness on 2008-10-31
found one station 1time but it vasent wiebable, second time searching for stations none found

terminal ouput 

```

Could not locate a configuration file!
Will use standard values.
video_player: Kaffeine
frequency_table: europe-west
video_bitrate_high: 0
video_device: /dev/video0
osd_enabled: 0
videoplayer_options: -m
temporal_filter: 0
video_standard_v4l2: 0x000000000000000F
video_standard_scantv: PAL-BGH
mixer_channel:
update_daemon_enabled: 1
language: English
video_standard_query: 0x0000000f

Choosen video-player Kaffeine

OSD disabled

No valid channels_europe-west.conf
Please create one using the Station-Editor.
Make sure you checked the configuration first!

Temporal filter set to 0

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

News-Reader started.
Last check: 31.10.2008
Offset: 0 Years 0 Months 0 Days

Next automatic check in 3 day(s)
[ anomander-rake: ~/tv-viewer-0.7.7b3 ]$
-------------------------------

Configuration-Wizard is starting

Could not locate a configuration file!
Will use standard values.
video_player: Kaffeine
frequency_table: europe-west
video_bitrate_high: 0
video_device: /dev/video0
osd_enabled: 1
videoplayer_options: -m
temporal_filter: 0
video_standard_v4l2: 0x000000000000000F
video_standard_scantv: PAL-BGH
mixer_channel:
update_daemon_enabled: 1
language: English
video_standard_query: 0x0000000f

Amixer found
Reading audio channels

Initializing main window

Selected video-player OK

Device node /dev/video0 successfully tested

v4l2-ctl successfully tested

ivtv-tune successfully tested

osd_cat successfully tested

Dejavu sans mono is installed on this system

Writing config file... DONE

-------------------------------

TV-Viewer is starting

Choosen video-player Kaffeine

OSD enabled

No valid channels_europe-west.conf
Please create one using the Station-Editor.
Make sure you checked the configuration first!

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

News-Reader started.
Last check: 31.10.2008
Offset: 0 Years 0 Months 0 Days

Next automatic check in 3 day(s)

-------------------------------

Station-Editor is starting

Video standard set to PAL-BGH

Initializing main window

No valid channels_europe-west.conf
Please create one

Starting automatic station search, please wait!
Signal detected on 273.250 MHz.

Tried to tune for
Error message: Invalid channel for 'europe-west'
child process exited abnormally

Station searched finished.

Tried to tune station unknown(SE17)
No signal detected on 273.250 Mhz.

Tried to tune station unknown(SE17)
No signal detected on 273.250 Mhz.
Tuning station unknown(SE17) on 273.250 Mhz.

-------------------------------

TV-Viewer is starting

Choosen video-player Kaffeine

OSD enabled

Valid channels_europe-west.conf found with 1 stations.


Tried to tune unknown(SE17)
No signal detected on 273.250 Mhz

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

-------------------------------

Configuration-Wizard is starting

Amixer found
Reading audio channels

Initializing main window

Selected video-player OK

Device node /dev/video0 successfully tested

v4l2-ctl successfully tested

ivtv-tune successfully tested

osd_cat successfully tested

Dejavu sans mono is installed on this system

Writing config file... DONE

-------------------------------

TV-Viewer is starting

Choosen video-player MPlayer

OSD enabled

Valid channels_europe-west.conf found with 1 stations.

Tuning station unknown(SE17) on 273.250 Mhz.

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

News-Reader started.
Last check: 31.10.2008
Offset: 0 Years 0 Months 0 Days

Next automatic check in 3 day(s)
Tuning station unknown(SE17) on 273.250 Mhz.

22531
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.


MPlayer interrupted by signal 15 in module: demux_open

-------------------------------

Station-Editor is starting

Video standard set to PAL-BGH

Initializing main window

Found a valid channels_europe-west.conf
Reading stations and frequencies.

Starting automatic station search, please wait!

Tried to tune for
Error message: Invalid channel for 'europe-west'
child process exited abnormally

Station searched finished.

Starting automatic station search, please wait!
Signal detected on 238.250 MHz.
Signal detected on 280.250 MHz.

Tried to tune for
Error message: Invalid channel for 'europe-west'
child process exited abnormally

Station searched finished.

-------------------------------

TV-Viewer is starting

Choosen video-player MPlayer

OSD enabled

Valid channels_europe-west.conf found with 1 stations.


Tried to tune unknown(SE17)
No signal detected on 273.250 Mhz

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

```

---

### Post by saedelaere on 2008-10-31
> **of_darkness said:**
> found one station 1time but it vasent wiebable, second time searching for stations none found

terminal ouput 

```

Could not locate a configuration file!
Will use standard values.
video_player: Kaffeine
frequency_table: europe-west
video_bitrate_high: 0
video_device: /dev/video0
osd_enabled: 0
videoplayer_options: -m
temporal_filter: 0
video_standard_v4l2: 0x000000000000000F
video_standard_scantv: PAL-BGH
mixer_channel:
update_daemon_enabled: 1
language: English
video_standard_query: 0x0000000f

Choosen video-player Kaffeine

OSD disabled

No valid channels_europe-west.conf
Please create one using the Station-Editor.
Make sure you checked the configuration first!

Temporal filter set to 0

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

News-Reader started.
Last check: 31.10.2008
Offset: 0 Years 0 Months 0 Days

Next automatic check in 3 day(s)
[ anomander-rake: ~/tv-viewer-0.7.7b3 ]$
-------------------------------

Configuration-Wizard is starting

Could not locate a configuration file!
Will use standard values.
video_player: Kaffeine
frequency_table: europe-west
video_bitrate_high: 0
video_device: /dev/video0
osd_enabled: 1
videoplayer_options: -m
temporal_filter: 0
video_standard_v4l2: 0x000000000000000F
video_standard_scantv: PAL-BGH
mixer_channel:
update_daemon_enabled: 1
language: English
video_standard_query: 0x0000000f

Amixer found
Reading audio channels

Initializing main window

Selected video-player OK

Device node /dev/video0 successfully tested

v4l2-ctl successfully tested

ivtv-tune successfully tested

osd_cat successfully tested

Dejavu sans mono is installed on this system

Writing config file... DONE

-------------------------------

TV-Viewer is starting

Choosen video-player Kaffeine

OSD enabled

No valid channels_europe-west.conf
Please create one using the Station-Editor.
Make sure you checked the configuration first!

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

News-Reader started.
Last check: 31.10.2008
Offset: 0 Years 0 Months 0 Days

Next automatic check in 3 day(s)

-------------------------------

Station-Editor is starting

Video standard set to PAL-BGH

Initializing main window

No valid channels_europe-west.conf
Please create one

Starting automatic station search, please wait!
Signal detected on 273.250 MHz.

Tried to tune for
Error message: Invalid channel for 'europe-west'
child process exited abnormally

Station searched finished.

Tried to tune station unknown(SE17)
No signal detected on 273.250 Mhz.

Tried to tune station unknown(SE17)
No signal detected on 273.250 Mhz.
Tuning station unknown(SE17) on 273.250 Mhz.

-------------------------------

TV-Viewer is starting

Choosen video-player Kaffeine

OSD enabled

Valid channels_europe-west.conf found with 1 stations.


Tried to tune unknown(SE17)
No signal detected on 273.250 Mhz

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

-------------------------------

Configuration-Wizard is starting

Amixer found
Reading audio channels

Initializing main window

Selected video-player OK

Device node /dev/video0 successfully tested

v4l2-ctl successfully tested

ivtv-tune successfully tested

osd_cat successfully tested

Dejavu sans mono is installed on this system

Writing config file... DONE

-------------------------------

TV-Viewer is starting

Choosen video-player MPlayer

OSD enabled

Valid channels_europe-west.conf found with 1 stations.

Tuning station unknown(SE17) on 273.250 Mhz.

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

News-Reader started.
Last check: 31.10.2008
Offset: 0 Years 0 Months 0 Days

Next automatic check in 3 day(s)
Tuning station unknown(SE17) on 273.250 Mhz.

22531
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.


MPlayer interrupted by signal 15 in module: demux_open

-------------------------------

Station-Editor is starting

Video standard set to PAL-BGH

Initializing main window

Found a valid channels_europe-west.conf
Reading stations and frequencies.

Starting automatic station search, please wait!

Tried to tune for
Error message: Invalid channel for 'europe-west'
child process exited abnormally

Station searched finished.

Starting automatic station search, please wait!
Signal detected on 238.250 MHz.
Signal detected on 280.250 MHz.

Tried to tune for
Error message: Invalid channel for 'europe-west'
child process exited abnormally

Station searched finished.

-------------------------------

TV-Viewer is starting

Choosen video-player MPlayer

OSD enabled

Valid channels_europe-west.conf found with 1 stations.


Tried to tune unknown(SE17)
No signal detected on 273.250 Mhz

Video standard set to PAL-BGH

Initializing main interface

TV-Browser not found on your system.
Disabling corresponding button

```

Hmm are you sure your tv-card works and there is a signal? Could you check with windows? 
Second you should use the configuration-wizard first to create a working config. Because the standard values might not work for you. 
Third, is PAL-BGH and europe-west correct for your region? Your cable provider should have a frequency list. You could use it to add stations manually.

Regards

---

### Post by of_darkness on 2008-11-01
> **saedelaere said:**
> Hmm are you sure your tv-card works and there is a signal? Could you check with windows? 
Second you should use the configuration-wizard first to create a working config. Because the standard values might not work for you. 
Third, is PAL-BGH and europe-west correct for your region? Your cable provider should have a frequency list. You could use it to add stations manually.

Regards

Well i have not gotten an clean image from the card yeat no,but its corrctly identified and driver is starting.

and about the wizard, i ran it one time first and it found 1channel but the next times no channel.

and i can get not a pure image but a blurred image but like where youre only getting a part of the signal by ```
v4l2-ctl -f 160.900
``` ```
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 2pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/home/anomander-rake/filename.mpg"}}' 
```

and i got this by some comand that i found (this is the refind result whit no non fiound lines) ```
[ anomander-rake: ~ ]$ cat signaler.txt
/dev/video0: 134.000 MHz  (Signal Detected)
/dev/video0: 139.000 MHz  (Signal Detected)
/dev/video0: 140.000 MHz  (Signal Detected)
/dev/video0: 141.000 MHz  (Signal Detected)
/dev/video0: 146.000 MHz  (Signal Detected)
/dev/video0: 147.000 MHz  (Signal Detected)
/dev/video0: 148.000 MHz  (Signal Detected)
/dev/video0: 153.000 MHz  (Signal Detected)
/dev/video0: 154.000 MHz  (Signal Detected)
/dev/video0: 155.000 MHz  (Signal Detected)
/dev/video0: 160.000 MHz  (Signal Detected)
/dev/video0: 161.000 MHz  (Signal Detected)
/dev/video0: 162.000 MHz  (Signal Detected)
/dev/video0: 167.000 MHz  (Signal Detected)
/dev/video0: 168.000 MHz  (Signal Detected)
/dev/video0: 169.000 MHz  (Signal Detected)
/dev/video0: 174.000 MHz  (Signal Detected)
/dev/video0: 175.000 MHz  (Signal Detected)
/dev/video0: 176.000 MHz  (Signal Detected)
/dev/video0: 181.000 MHz  (Signal Detected)
/dev/video0: 182.000 MHz  (Signal Detected)
/dev/video0: 183.000 MHz  (Signal Detected)
/dev/video0: 188.000 MHz  (Signal Detected)
/dev/video0: 189.000 MHz  (Signal Detected)
/dev/video0: 190.000 MHz  (Signal Detected)
/dev/video0: 195.000 MHz  (Signal Detected)
/dev/video0: 196.000 MHz  (Signal Detected)
/dev/video0: 197.000 MHz  (Signal Detected)
/dev/video0: 202.000 MHz  (Signal Detected)
/dev/video0: 203.000 MHz  (Signal Detected)
/dev/video0: 204.000 MHz  (Signal Detected)
/dev/video0: 209.000 MHz  (Signal Detected)
/dev/video0: 210.000 MHz  (Signal Detected)
/dev/video0: 211.000 MHz  (Signal Detected)
/dev/video0: 216.000 MHz  (Signal Detected)
/dev/video0: 217.000 MHz  (Signal Detected)
/dev/video0: 218.000 MHz  (Signal Detected)
/dev/video0: 223.000 MHz  (Signal Detected)
/dev/video0: 224.000 MHz  (Signal Detected)
/dev/video0: 225.000 MHz  (Signal Detected)
/dev/video0: 230.000 MHz  (Signal Detected)
/dev/video0: 231.000 MHz  (Signal Detected)
/dev/video0: 232.000 MHz  (Signal Detected)
/dev/video0: 237.000 MHz  (Signal Detected)
/dev/video0: 238.000 MHz  (Signal Detected)
/dev/video0: 239.000 MHz  (Signal Detected)
/dev/video0: 244.000 MHz  (Signal Detected)
/dev/video0: 245.000 MHz  (Signal Detected)
/dev/video0: 246.000 MHz  (Signal Detected)
/dev/video0: 251.000 MHz  (Signal Detected)
/dev/video0: 252.000 MHz  (Signal Detected)
/dev/video0: 253.000 MHz  (Signal Detected)
/dev/video0: 258.000 MHz  (Signal Detected)
/dev/video0: 259.000 MHz  (Signal Detected)
/dev/video0: 260.000 MHz  (Signal Detected)
/dev/video0: 265.000 MHz  (Signal Detected)
/dev/video0: 266.000 MHz  (Signal Detected)
/dev/video0: 267.000 MHz  (Signal Detected)
/dev/video0: 272.000 MHz  (Signal Detected)
/dev/video0: 273.000 MHz  (Signal Detected)
/dev/video0: 274.000 MHz  (Signal Detected)
/dev/video0: 279.000 MHz  (Signal Detected)
/dev/video0: 280.000 MHz  (Signal Detected)
/dev/video0: 281.000 MHz  (Signal Detected)
/dev/video0: 286.000 MHz  (Signal Detected)
/dev/video0: 287.000 MHz  (Signal Detected)
/dev/video0: 288.000 MHz  (Signal Detected)
/dev/video0: 293.000 MHz  (Signal Detected)
/dev/video0: 294.000 MHz  (Signal Detected)
/dev/video0: 295.000 MHz  (Signal Detected)
[ anomander-rake: ~ ]$  
```

and i don not have any windows.
and yeas as fara as i have found on my research PAL-BGH and europe-west was correct when the national sednings where analog,they are now digital.

But i have a cable tv provider so i dont neead a digital box on my tv 2 se tv.
Nop ther isent any frekvency list only S12. E9 etc that i could find, or i found one but its not for my cable operator [http://www.barhall.com/web/for%20oss%20i%20barhall/frekvenser%20till%20tv.htm](http://www.barhall.com/web/for%20oss%20i%20barhall/frekvenser%20till%20tv.htm) 

but they worked some what whit vlc i got sound but vlc quiqly stops displaying any form of image or sound when i get some..

but i found now that tv-viwer found some channelsas you se in the comandline here but they could not get inte to the window or when chosing them manuly it says it dossent find any channel..

```
Station-Editor is starting

Video standard set to PAL-BGH

Initializing main window

Found a valid channels_europe-west.conf
Reading stations and frequencies.

Starting automatic station search, please wait!
Signal detected on 48.250 MHz.
Signal detected on 273.250 MHz.
Signal detected on 280.250 MHz.
Signal detected on 287.250 MHz.

Tried to tune for
Error message: Invalid channel for 'europe-west'
child process exited abnormally

Station searched finished.

Tried to tune station tv4 e8
No signal detected on 196MHz Mhz.

Tried to tune station test
No signal detected on 48.250 Mhz.

Tried to tune station test
No signal detected on 175 Mhz.

Tried to tune station test
No signal detected on 175.000 Mhz.

-------------------------------

TV-Viewer is starting

Choosen video-player MPlayer

OSD enabled

Valid channels_europe-west.conf found with  stations.

Error in startup script: can't read "kanalcall(1)": no such variable
    while executing
"puts -nonewline $fileId "<$kanalid(1)> $kanalcall(1) 1""
    invoked from within
"if !{[file exists "$::where_is_home/config/channels_$::option(frequency_table).conf"]} {
        puts "
No valid channels_$::option(frequency_table).conf
Ple..."
    (file "/usr/share/tv-viewer/tv-viewer.tcl" line 569)
                                                               
```

---

### Post by saedelaere on 2008-11-01
> **of_darkness said:**
> Well i have not gotten an clean image from the card yeat no,but its corrctly identified and driver is starting.

and about the wizard, i ran it one time first and it found 1channel but the next times no channel.

and i can get not a pure image but a blurred image but like where youre only getting a part of the signal by ```
v4l2-ctl -f 160.900
``` ```
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 2pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/home/anomander-rake/filename.mpg"}}' 
```

and i got this by some comand that i found (this is the refind result whit no non fiound lines) ```
[ anomander-rake: ~ ]$ cat signaler.txt
/dev/video0: 134.000 MHz  (Signal Detected)
/dev/video0: 139.000 MHz  (Signal Detected)
/dev/video0: 140.000 MHz  (Signal Detected)
/dev/video0: 141.000 MHz  (Signal Detected)
/dev/video0: 146.000 MHz  (Signal Detected)
/dev/video0: 147.000 MHz  (Signal Detected)
/dev/video0: 148.000 MHz  (Signal Detected)
/dev/video0: 153.000 MHz  (Signal Detected)
/dev/video0: 154.000 MHz  (Signal Detected)
/dev/video0: 155.000 MHz  (Signal Detected)
/dev/video0: 160.000 MHz  (Signal Detected)
/dev/video0: 161.000 MHz  (Signal Detected)
/dev/video0: 162.000 MHz  (Signal Detected)
/dev/video0: 167.000 MHz  (Signal Detected)
/dev/video0: 168.000 MHz  (Signal Detected)
/dev/video0: 169.000 MHz  (Signal Detected)
/dev/video0: 174.000 MHz  (Signal Detected)
/dev/video0: 175.000 MHz  (Signal Detected)
/dev/video0: 176.000 MHz  (Signal Detected)
/dev/video0: 181.000 MHz  (Signal Detected)
/dev/video0: 182.000 MHz  (Signal Detected)
/dev/video0: 183.000 MHz  (Signal Detected)
/dev/video0: 188.000 MHz  (Signal Detected)
/dev/video0: 189.000 MHz  (Signal Detected)
/dev/video0: 190.000 MHz  (Signal Detected)
/dev/video0: 195.000 MHz  (Signal Detected)
/dev/video0: 196.000 MHz  (Signal Detected)
/dev/video0: 197.000 MHz  (Signal Detected)
/dev/video0: 202.000 MHz  (Signal Detected)
/dev/video0: 203.000 MHz  (Signal Detected)
/dev/video0: 204.000 MHz  (Signal Detected)
/dev/video0: 209.000 MHz  (Signal Detected)
/dev/video0: 210.000 MHz  (Signal Detected)
/dev/video0: 211.000 MHz  (Signal Detected)
/dev/video0: 216.000 MHz  (Signal Detected)
/dev/video0: 217.000 MHz  (Signal Detected)
/dev/video0: 218.000 MHz  (Signal Detected)
/dev/video0: 223.000 MHz  (Signal Detected)
/dev/video0: 224.000 MHz  (Signal Detected)
/dev/video0: 225.000 MHz  (Signal Detected)
/dev/video0: 230.000 MHz  (Signal Detected)
/dev/video0: 231.000 MHz  (Signal Detected)
/dev/video0: 232.000 MHz  (Signal Detected)
/dev/video0: 237.000 MHz  (Signal Detected)
/dev/video0: 238.000 MHz  (Signal Detected)
/dev/video0: 239.000 MHz  (Signal Detected)
/dev/video0: 244.000 MHz  (Signal Detected)
/dev/video0: 245.000 MHz  (Signal Detected)
/dev/video0: 246.000 MHz  (Signal Detected)
/dev/video0: 251.000 MHz  (Signal Detected)
/dev/video0: 252.000 MHz  (Signal Detected)
/dev/video0: 253.000 MHz  (Signal Detected)
/dev/video0: 258.000 MHz  (Signal Detected)
/dev/video0: 259.000 MHz  (Signal Detected)
/dev/video0: 260.000 MHz  (Signal Detected)
/dev/video0: 265.000 MHz  (Signal Detected)
/dev/video0: 266.000 MHz  (Signal Detected)
/dev/video0: 267.000 MHz  (Signal Detected)
/dev/video0: 272.000 MHz  (Signal Detected)
/dev/video0: 273.000 MHz  (Signal Detected)
/dev/video0: 274.000 MHz  (Signal Detected)
/dev/video0: 279.000 MHz  (Signal Detected)
/dev/video0: 280.000 MHz  (Signal Detected)
/dev/video0: 281.000 MHz  (Signal Detected)
/dev/video0: 286.000 MHz  (Signal Detected)
/dev/video0: 287.000 MHz  (Signal Detected)
/dev/video0: 288.000 MHz  (Signal Detected)
/dev/video0: 293.000 MHz  (Signal Detected)
/dev/video0: 294.000 MHz  (Signal Detected)
/dev/video0: 295.000 MHz  (Signal Detected)
[ anomander-rake: ~ ]$  
```

and i don not have any windows.
and yeas as fara as i have found on my research PAL-BGH and europe-west was correct when the national sednings where analog,they are now digital.

But i have a cable tv provider so i dont neead a digital box on my tv 2 se tv.
Nop ther isent any frekvency list only S12. E9 etc that i could find, or i found one but its not for my cable operator [http://www.barhall.com/web/for%20oss%20i%20barhall/frekvenser%20till%20tv.htm](http://www.barhall.com/web/for%20oss%20i%20barhall/frekvenser%20till%20tv.htm) 

but they worked some what whit vlc i got sound but vlc quiqly stops displaying any form of image or sound when i get some..

but i found now that tv-viwer found some channelsas you se in the comandline here but they could not get inte to the window or when chosing them manuly it says it dossent find any channel..

```
Station-Editor is starting

Video standard set to PAL-BGH

Initializing main window

Found a valid channels_europe-west.conf
Reading stations and frequencies.

Starting automatic station search, please wait!
Signal detected on 48.250 MHz.
Signal detected on 273.250 MHz.
Signal detected on 280.250 MHz.
Signal detected on 287.250 MHz.

Tried to tune for
Error message: Invalid channel for 'europe-west'
child process exited abnormally

Station searched finished.

Tried to tune station tv4 e8
No signal detected on 196MHz Mhz.

Tried to tune station test
No signal detected on 48.250 Mhz.

Tried to tune station test
No signal detected on 175 Mhz.

Tried to tune station test
No signal detected on 175.000 Mhz.

-------------------------------

TV-Viewer is starting

Choosen video-player MPlayer

OSD enabled

Valid channels_europe-west.conf found with  stations.

Error in startup script: can't read "kanalcall(1)": no such variable
    while executing
"puts -nonewline $fileId "<$kanalid(1)> $kanalcall(1) 1""
    invoked from within
"if !{[file exists "$::where_is_home/config/channels_$::option(frequency_table).conf"]} {
        puts "
No valid channels_$::option(frequency_table).conf
Ple..."
    (file "/usr/share/tv-viewer/tv-viewer.tcl" line 569)
                                                               
```

So first of all sorry for the bug. I already fixed it. But this can only happen if the Station-File you've created is empty. Did you save it before exiting the station-editor?
I'am  now quite sure that sweden has PAl-BGH and europe-west so this should be correct.
Second if your cable provider gots a list with the channels (E5 E6 S12 ...)
than do the following.

```

ivtv-tune -t europe-west -l

```

This command shows you all Frequency/Channel pairs.

Now let's say your cable provider says there should be a station on channel S12. Look in the list to find the corresponding frequency and 
```

ivtv-tune -t europe-west -f 238.250

```

Now open vlc with
```

vlc pvr:///dev/video0

```

Do you have a picture now?

try with the other stations your cable provider provides. And if you don't get a good picture set the frequency manually one Mhz higher or lower. 
If all this doesn't help then there is something wrong with yout tv-card or the connection or or or

I don't think this is problem of TV-Viewer. The programm scans all available channels for europe-west.

Regards

---

### Post by saedelaere on 2008-11-09
@of_darkness

You could try to use the latest beta vesion (0.7.7b4)

Regards

---

### Post by cchester on 2008-11-11
Hello,

Here is a deb I created from inside my Ubuntu 8.10 system based on the most recent version of tv-viewer 0.7.7b4.

I hope it works for everyone. It worked on mine.

Hope this is ok from the creator.

---

### Post by arron on 2008-11-11
Im tryen this out with my haupaquge 500.  I set it so i can see and hear my rca inputs, but there is a fuzzy line at the bottom, like 1/4 of the window.

the feed is clean when i checked, i set it on ntsc, what else could it be?

Thanks for the app, very nice.

---

### Post by saedelaere on 2008-11-12
> **cchester said:**
> Hello,

Here is a deb I created from inside my Ubuntu 8.10 system based on the most recent version of tv-viewer 0.7.7b4.

I hope it works for everyone. It worked on mine.

Hope this is ok from the creator.

Hi,

thanks for the package. Normally I don't want to make packages for beta version due to the lack of time. It wiuld be very nice if you could make a package of the upcoming version 0.7.7 so I can put it on the homepage and make it availlable to all users.

> **arron said:**
> Im tryen this out with my haupaquge 500.  I set it so i can see and hear my rca inputs, but there is a fuzzy line at the bottom, like 1/4 of the window.

the feed is clean when i checked, i set it on ntsc, what else could it be?

Thanks for the app, very nice.

Did you set "Increase Videobitrate" in the configuration wizard. If yes please disable it. Could you post a screenshot of this fuzzy line?
It would be good to have the the ouput of the diagnostic routines too.
(See Main-interface --> options --> Diagnostic routine)

Regards

EDIT:

One more thing, after starting tv-viewer. Could use please execute the command
```
v4l2-ctl --device=/dev/video0 --set-standard=ntsc
```
Note just execute tv-viewer do not start tv playback before executing the metioned command. Otherwise it has no effect. After executing the command you should start playback. Is the picture better now?

---

### Post by Riffer on 2008-11-16
Tried to install one of the dependencies "gkimg" and I can't get it to install.  Any ideas

---

### Post by saedelaere on 2008-11-16
The package you are searching for is libtk-img

Regards

---

### Post by Riffer on 2008-11-17
Thanks for the tip.  I saw the reference later in an earlier post.  Worked a treat except getting past the configuration wizard.  I keep getting stuck on VBI, I seem not to have such a file and the default (/dev/vbi0) doesn't work.  BTW I'm trying this with a Hauppauge HVR 1800 tv card which it seems to be problematic at best.

---

### Post by saedelaere on 2008-11-17
> **Riffer said:**
> Thanks for the tip.  I saw the reference later in an earlier post.  Worked a treat except getting past the configuration wizard.  I keep getting stuck on VBI, I seem not to have such a file and the default (/dev/vbi0) doesn't work.  BTW I'm trying this with a Hauppauge HVR 1800 tv card which it seems to be problematic at best.

Hmm deinstall the version you`re using and try the [latest beta]("http://home.arcor.de/saedelaere/download_eng.html#Beta_releases"). 
You do not have to uninstall the old version. Just install the beta version. Please note that you need Tcl/Tk 8.5 to get this to run. 
The VBI device node was used to scan for channels. But for some devices the driver doesn't provide one. So I developed my own channel search which doesn't depend on a working vbi device node. 

Regards

---

### Post by cchester on 2008-11-17
> **saedelaere said:**
> Hi,

thanks for the package. Normally I don't want to make packages for beta version due to the lack of time. It wiuld be very nice if you could make a package of the upcoming version 0.7.7 so I can put it on the homepage and make it availlable to all users.



Hello,

I was basically trying to make a deb package to be tested by others to see if it will install on their systems and decided to use your most recent beta as my test. Yeah I prefer too the final versions for deb files but decided to go this route instead since it had your most recent features.

I am constantly testing out your program and the betas and will gladly offer a deb package for you to post.

I also opened something on launch pad for tv-viewer and would like to work with you on it. That way maybe it will get into the Ubuntu Repository to make things even easier. Can you take a look?

Also did you check out the package to see if it worked?

Just curious because I haven't seen if anyone say if it works or not.

Thanks again for the great program.

---

### Post by Riffer on 2008-11-17
Thanks for the reply.  Still no-go the temporal filter value is failing in the configuration wizard.

---

### Post by saedelaere on 2008-11-17
> **Riffer said:**
> Thanks for the reply.  Still no-go the temporal filter value is failing in the configuration wizard.

Could you please execute in a terminal

```
v4l2-ctl --all
```

and

```
v4l2-ctl -l
```

and

```
dmesg | grep cx18
```

and

```
ls /dev/video*
```

and post the results here.

Regards

---

### Post by Riffer on 2008-11-17
> Driver Info:
	Driver name   : cx23885
	Card type     : Hauppauge WinTV-HVR1800
	Bus info      : PCIe:0000:02:00.0
	Driver version: 1
	Capabilities  : 0x05010011
		Video Capture
		VBI Capture
		Tuner
		Read/Write
		Streaming
Format Video Capture:
	Width/Height  : 320/240
	Pixel Format  : BGR3
	Field         : Interlaced
	Bytes per Line: 960
	Size Image    : 230400
	Colorspace    : Unknown (00000000)
Format VBI Capture:
	Sampling Rate   : 35468950 Hz
	Offset          : 0 samples (0 secs after leading edge)
	Samples per Line: 0
	Sample Format   : 
	Start 1st Field : 6
	Count 1st Field : 0
	Start 2nd Field : 318
	Count 2nd Field : 0
Video input : 0 (Television)
Frequency: 6400 (400.000000 MHz)
Video Standard = 0x000000f7
	PAL-B/B1/G/I/D/D1/K
Tuner:
	Capabilities         : 62.5 kHz multi-standard 
	Frequency range      : 0.0 MHz - 268435455.9 MHz
	Signal strength      : 99%
	Current audio mode   : mono
	Available subchannels: 


> Driver Info:
	Driver name   : cx23885
	Card type     : Hauppauge WinTV-HVR1800
	Bus info      : PCIe:0000:02:00.0
	Driver version: 1
	Capabilities  : 0x05010011
		Video Capture
		VBI Capture
		Tuner
		Read/Write
		Streaming
Format Video Capture:
	Width/Height  : 320/240
	Pixel Format  : BGR3
	Field         : Interlaced
	Bytes per Line: 960
	Size Image    : 230400
	Colorspace    : Unknown (00000000)
Format VBI Capture:
	Sampling Rate   : 35468950 Hz
	Offset          : 0 samples (0 secs after leading edge)
	Samples per Line: 0
	Sample Format   : 
	Start 1st Field : 6
	Count 1st Field : 0
	Start 2nd Field : 318
	Count 2nd Field : 0
Video input : 0 (Television)
Frequency: 6400 (400.000000 MHz)
Video Standard = 0x000000f7
	PAL-B/B1/G/I/D/D1/K
Tuner:
	Capabilities         : 62.5 kHz multi-standard 
	Frequency range      : 0.0 MHz - 268435455.9 MHz
	Signal strength      : 99%
	Current audio mode   : mono
	Available subchannels: 
riffraff@stupid1:~$ v4l2-ctl -l
                     brightness (int)  : min=0 max=255 step=1 default=127 value=146
                       contrast (int)  : min=0 max=255 step=1 default=63 value=62
                     saturation (int)  : min=0 max=255 step=1 default=127 value=65
                            hue (int)  : min=0 max=255 step=1 default=127 value=0
                         volume (int)  : min=0 max=63 step=1 default=63 value=60928
                           mute (bool) : default=1 value=0


> /dev/video0  /dev/video1

There was no output for dmesg | grep cx18

---

### Post by arron on 2008-11-17
I tried the tv viewer again on a fresh pc install.  The fuzzy line is gone... Go figure!  But I have the another problem, and going back tothe previous install, there is a video lag of about 2 seconds.

Is there a setting I can do to get this synced?  As well,how far away is having the record portion work?

Thanks, ill try out the package next time.

---

### Post by saedelaere on 2008-11-19
> **arron said:**
> I tried the tv viewer again on a fresh pc install.  The fuzzy line is gone... Go figure!  But I have the another problem, and going back tothe previous install, there is a video lag of about 2 seconds.

Is there a setting I can do to get this synced?  As well,how far away is having the record portion work?

Thanks, ill try out the package next time.

What do you mean by video lag? Is the audio and video not synchron? The record function is already workin you just have to use the command line and this is working quite good. The frontend for the record wizard will come with the 0.9.x development branch. This will take some more month.

Regards

---

### Post by saedelaere on 2008-11-19
> **Riffer said:**
> There was no output for dmesg | grep cx18

Could you please post the ouput of
```
dmesg | grep cx88
```

Your device could be supported by tv-viewer.

Can you open a video steam with cat and can you tune your channels with ivtv-tune?

Regards

---

### Post by saedelaere on 2008-11-19
> **cchester said:**
> Hello,

I was basically trying to make a deb package to be tested by others to see if it will install on their systems and decided to use your most recent beta as my test. Yeah I prefer too the final versions for deb files but decided to go this route instead since it had your most recent features.

I am constantly testing out your program and the betas and will gladly offer a deb package for you to post.

I also opened something on launch pad for tv-viewer and would like to work with you on it. That way maybe it will get into the Ubuntu Repository to make things even easier. Can you take a look?

Also did you check out the package to see if it worked?

Just curious because I haven't seen if anyone say if it works or not.

Thanks again for the great program.


Hi,

first of all thanks for your work by building a deb package. I have to admit I did not try to install it. At the moment I have to work very much for the university and in my free time I'am coding ;)
Could you post a link to TV-Viewer on launchpad?

I think it is also time to find a new name for TV-Viewer. One suggestion was mattscheibe. This is a german word for a television. It could also be very simple like "tktv" showing it is running with Tcl/Tk.
TV-Viewer is more like a hypernym for such programs. Do you or anyone else have/has a suggestion?

Regards

EDIT Sorry for three different posts!

---

### Post by cchester on 2008-11-19
Hello,

Here is the link for launchpad [https://launchpad.net/~christopherwchester-embarqmail/+archive]("https://launchpad.net/~christopherwchester-embarqmail/+archive").

I just put it up not to long ago and I am still learning and working on it.

Let me know if you are wanting anything changed or added. I should be able to add you if needed if you want to change anything as well.

Let me know and thanks for the reply.

Chris

---

### Post by saedelaere on 2008-11-20
> **cchester said:**
> Hello,

Here is the link for launchpad [https://launchpad.net/~christopherwchester-embarqmail/+archive]("https://launchpad.net/~christopherwchester-embarqmail/+archive").

I just put it up not to long ago and I am still learning and working on it.

Let me know if you are wanting anything changed or added. I should be able to add you if needed if you want to change anything as well.

Let me know and thanks for the reply.

Chris

That looks ok. I think it wouldn't be bad if I would be able to add or change things myself. Just in case ;)

Any name suggestions? Or are you happy with the current one?

Regards

---

### Post by cchester on 2008-11-20
Hello,

Ok, no problem. I will see how to add you. Remember I am new to using it so I am still learning and trying to actually figure out how to add the packages.

I like the name Tv-Viewer but I do think it may need to be changed only for the fact that if you do a search other things with the same/similar name come up.

There is one thing that bugs me is when I do a search for something and a ton of hits come up for something similar in name along with what I am looking for but the one I am actually looking for is the one buried 30 pages deep. Make things hard sometimes so that is why I would suggest to change the name. Just not sure what to yet even though I do like your idea of TCL/TK Tv-Viewer. That might help or maybe Pvr-Tviewer. Not sure though because that might confuse some to into thinking it is to view your PVR (Tivo/Replay).

Thanks.

---

### Post by saedelaere on 2008-11-20
> **cchester said:**
> Hello,

Ok, no problem. I will see how to add you. Remember I am new to using it so I am still learning and trying to actually figure out how to add the packages.

I like the name Tv-Viewer but I do think it may need to be changed only for the fact that if you do a search other things with the same/similar name come up.

There is one thing that bugs me is when I do a search for something and a ton of hits come up for something similar in name along with what I am looking for but the one I am actually looking for is the one buried 30 pages deep. Make things hard sometimes so that is why I would suggest to change the name. Just not sure what to yet even though I do like your idea of TCL/TK Tv-Viewer. That might help or maybe Pvr-Tviewer. Not sure though because that might confuse some to into thinking it is to view your PVR (Tivo/Replay).

Thanks.

What about tkboob-tube
or         tktube (to many t!?)
or         tktelly  (to many t?)
or         tkflimmerkiste (to long)
or         tkglotze (glotze is somehow an ugly word ;))
or         tkpvr
or         tktv
or         tkviewer
or         tkgoggle-box (looks to much like googel)
or         tkjatv (just another television viewer)

hmm lot's of ideas but non of them is really satisfying

Regards

---

### Post by cchester on 2008-11-20
All sound good to me.

---

### Post by arron on 2008-11-21
> **saedelaere said:**
> What do you mean by video lag? Is the audio and video not synchron? The record function is already workin you just have to use the command line and this is working quite good. The frontend for the record wizard will come with the 0.9.x development branch. This will take some more month.

Regards

The sound seems to be as it comes out of the vcr (when I pause the sound stops).  But the video seems to be a 2 second lag behind the sound.  almost like a bad Chinese dubbed movie.  When I play, the sound comes, the video start about 1-2 seconds later.

Thanks for your work on this useful project.

---

### Post by saedelaere on 2008-11-21
> **arron said:**
> The sound seems to be as it comes out of the vcr (when I pause the sound stops).  But the video seems to be a 2 second lag behind the sound.  almost like a bad Chinese dubbed movie.  When I play, the sound comes, the video start about 1-2 seconds later.

Thanks for your work on this useful project.

Funny that never occured to me. Which video player do you use? Did you try another one?

---

### Post by Riffer on 2008-11-23
> **saedelaere said:**
> Could you please post the ouput of
```
dmesg | grep cx88
```

Your device could be supported by tv-viewer.

Can you open a video steam with cat and can you tune your channels with ivtv-tune?

Regards

Sorry I haven't gotten back to you sooner.  Basically I was trying to get a LCD TV set up as a secondary screen, I have since figured out the tv is broken.

The good news is I've done a re-install, didn't add any new drivers just installed tvtime, and it works!!  Though if I switch workspaces tvtime will freeze and if I close it and restart I get a blue screen in the window (have sound though) and the only way I can get the picture back is to do a reboot.

---

### Post by saedelaere on 2008-11-24
> **Riffer said:**
> Sorry I haven't gotten back to you sooner.  Basically I was trying to get a LCD TV set up as a secondary screen, I have since figured out the tv is broken.

The good news is I've done a re-install, didn't add any new drivers just installed tvtime, and it works!!  Though if I switch workspaces tvtime will freeze and if I close it and restart I get a blue screen in the window (have sound though) and the only way I can get the picture back is to do a reboot.

I just wonder how a tv-card with a build in mpeg encoder could work with tvtime. You should make your own thread concerning your problem. 

Regards

Saedelaere

---

### Post by macadavy on 2008-11-25
> **Riffer said:**
> Thanks for the tip.  I saw the reference later in an earlier post.  Worked a treat except getting past the configuration wizard.  I keep getting stuck on VBI, I seem not to have such a file and the default (/dev/vbi0) doesn't work.  BTW I'm trying this with a Hauppauge HVR 1800 tv card which it seems to be problematic at best.

Hi Riffer,

I'm curious as to how you are managing to use the Hauppauge HVR 1800.  The Hauppauge website states that: "Linux support for the WinTV-HVR-1250 and WinTV-HVR-1800 is in the current kernel 2.6.25 release." I'm using (K)Ubuntu 8.04 which uses the 2.6.24 kernel. Did you do a kernel upgrade to get support for the HVR 1800?  (The release notes for Ubuntu 8.10 don't say what kernel version is used so I don't know if I should do an upgrade.) TIA

---

### Post by wolfen69 on 2008-11-25
the kernel in 8.10 is 2.6.27

you can find out the kernel version by doing: ```
uname -r
```

---

### Post by saedelaere on 2008-11-28
New stable release 0.7.7

After a long beta period, with five beta versions, it is time for the next stable release.
Many things have been changed since 0.7.6.2 Please note the bugfixes and new features mentioned below refer to version 0.7.6.2 and not to the last beta.

Bugfixes:
[LIST]
[*] Removed some mistakes and crudities in the text passages.
[*] The scheduler produced an error if the video device node was already in use and did not try again to finish the job.
[*] Minor things in the source code.
[/LIST]
New Features:
[LIST]
[*] Now using frequencies instead channels. This will allow you to use finetuning.
[*] Automatic station search no longer depends on scantv or a working VBI device node. Now all users should be able to use it.
[*] Update-Daemon is now a News-Reader.
[*] Videocard control options (Hue, saturation...) and video standard (Pal, secam, ntsc) will only be changed if necessary.
[*] Splash screen.
[*] You may now dock TV-Viewer into the system tray (Does not work on Ubuntu).
[*] Added an entry field to the Station-Editor. It may be used to get the frequency of a specific channel.
[*] The record wizard is now able to parse output files with blancs.
[/LIST]
If you want to have a more detailed overview of what has changed since 0.7.6.2, have a look at the [changelog]("http://home.arcor.de/saedelaere/tv-viewerfiles/CHANGELOG").
[Here]("http://home.arcor.de/saedelaere/download_eng.html") you can download the new version. Please note, that some system requirements have been changed!
Older configuration files and station files (< 0.7.7b1) will no longer work with this release. Create a new configuration with the "Configuration-Wizard". Use the "stations-editor" (Options --> convert stations) to convert old station files to the new format.

With this release I'am finishing the 0.7.x development branch. Only if there will be grave bugs i will make a bugfix release.
The planning for 0.8.x is mostly completed. So it is quite sure what will be included in the development branch and how to implent them. Nevertheless most of the code has still to be written. I'am looking forward to release a first alpha version within the next weeks.

Enjoy the new version

---

### Post by macadavy on 2008-11-29
> **wolfen69 said:**
> the kernel in 8.10 is 2.6.27

you can find out the kernel version by doing: ```
uname -r
```
Thanks Wolfen69, looks like an 8.10 upgrade's in my near future! :-)

---

### Post by arron on 2008-12-16
Thanks for your hard work on this project.  It works well for me.  Just a small question, is support planned to be able to watch as you record?  It would be nice, but I can get by with opening the file after it starts to record.

* edit*  I should of mentioned, it would bea big help to have a input selector (cable, composite etc).

Thanks

Arron

---

### Post by arron on 2008-12-16
Can you update your howto for ubuntu, and put this command for adding needed packages (tcl 8.5 is in the repos now)

```

sudo apt-get install tcl8.5 tk8.5 xosd-bin xdg-utils libtk-img ivtv-utils

```

Then followed by this to make it all simple and in one sport for those not to good at this stuff:
```

wget http://downloads.sourceforge.net/tv-viewer/tv-viewer-0.7.7.tar.gz
tar -xvzf tv-viewer-0.7.7.tar.gz
cd tv-viewer-0.7.7
sudo ./tv-viewer_install.sh

```

** NOTE The version number may need to be updated for future versions**

And that *should* be about it, all in 6 commands.

---

### Post by saedelaere on 2008-12-23
> **arron said:**
> Thanks for your hard work on this project.  It works well for me.  Just a small question, is support planned to be able to watch as you record?  It would be nice, but I can get by with opening the file after it starts to record.

* edit*  I should of mentioned, it would bea big help to have a input selector (cable, composite etc).

Thanks

Arron

Glad to hear it works for you :) I'll definitively add the requested feature. Probably in version 0.8x. Also the selection of a different input will be part of the program.

> **arron said:**
> Can you update your howto for ubuntu, and put this command for adding needed packages (tcl 8.5 is in the repos now)

```

sudo apt-get install tcl8.5 tk8.5 xosd-bin xdg-utils libtk-img ivtv-utils

```

Then followed by this to make it all simple and in one sport for those not to good at this stuff:
```

wget http://downloads.sourceforge.net/tv-viewer/tv-viewer-0.7.7.tar.gz
tar -xvzf tv-viewer-0.7.7.tar.gz
cd tv-viewer-0.7.7
sudo ./tv-viewer_install.sh

```

** NOTE The version number may need to be updated for future versions**

And that *should* be about it, all in 6 commands.

Thanks for your simple tutorial on how to install TV-Viewer on Ubuntu. I'll update my instructions as soon as possible. 

Best Regards
Saedelaere

---

### Post by Porpoise on 2008-12-23
> **arron said:**
> Thanks for your hard work on this project.  It works well for me.  Just a small question, is support planned to be able to watch as you record?  It would be nice, but I can get by with opening the file after it starts to record.

* edit*  I should of mentioned, it would bea big help to have a input selector (cable, composite etc).

Thanks

Arron


Hi Arron,

You can use Video4Linux and VideoLan for the purpose until saedelaere manages to update TV-Viewer (keep up the good work saedelaere).  The details below are what I use:
```

#!/bin/bash
#To set device as Hauppauge PVR-150:  /dev/video0
#
#To select inputs:
[code]
v4l2-ctl --set-input=0    #for Tuner 1
v4l2-ctl --set-input=1    #S-Video 1
v4l2-ctl --set-input=2    #Composite 1
v4l2-ctl --set-input=3    #S-Video 2
v4l2-ctl --set-input=4    #Composite 2

```#If using the Tuner as input, then to select channels:
```

v4l2-ctl -f 711.250    #Frequency: 11380 (711.250000 MHz) (BBC 1)
v4l2-ctl -f 655.250    #Frequency: 10484 (655.250000 MHz) (BBC 2)
v4l2-ctl -f 631.250    #Frequency: 10100 (631.250000 MHz) (ITV 1)
v4l2-ctl -f 679.250    #Frequency: 10868 (679.250000 MHz) (CHA 4)

```#VLC Device setting:
```
pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 
```#
#VLC Record setting:
```
:sout=#duplicate{dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}} :sout-display
```#
#Command-line to Record:
```
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'
```#
#To Display whilst recording:
```
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/media/raid/DVCR/TV_Record.mpg"}}'

```or
```
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/media/LaCie VIDEO/VHS_Record.avi"}}'
```Just change your paths to suit, noting that you can set the file format (MPG or AVI) simply by the file extension you use.

You can either run the relevant code directly in a terminal or run the commands you need as scripts.

ie.

```
v4l2-ctl --set-input=2
``` # to set input as Composite 1

```
v4l2-ctl -f 711.250
``` #to set Frequency: 11380 (711.250000 MHz) (BBC 1) - change your frequencies to suit.

```
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/media/LaCie VIDEO/VHS_Record.avi"}}' 
``` # This will display and record simultaneously - just change your path/filename to suit.

Cheers & Merry Christmas,
Steve

---

### Post by floodx on 2009-01-29
Seems like a pretty slick program and very intuitive.

A note on Ubuntu installation - I am using Hardy - tkimg was not in the repositories (not sure why). libtk-img was in the repos but it would only work with tcl/tk8.4 (the default in hardy) not 8.5. I had to download and install tkimg separate - there are deb packages available or you can install from source. Plus I had to set the symlinks from 8.4 to 8.5.

Is there any way to select to select the Composite input from inside the program that I am missing? My v4l2 is set to input 2 however I get static through tv-viewer - sound comes through fine.

cat /dev/video0 > test.mpg works fine so I know it is just a setup issue on my end.

thanks for any help

---

### Post by saedelaere on 2009-01-30
> **floodx said:**
> Seems like a pretty slick program and very intuitive.

A note on Ubuntu installation - I am using Hardy - tkimg was not in the repositories (not sure why). libtk-img was in the repos but it would only work with tcl/tk8.4 (the default in hardy) not 8.5. I had to download and install tkimg separate - there are deb packages available or you can install from source. Plus I had to set the symlinks from 8.4 to 8.5.

Is there any way to select to select the Composite input from inside the program that I am missing? My v4l2 is set to input 2 however I get static through tv-viewer - sound comes through fine.

cat /dev/video0 > test.mpg works fine so I know it is just a setup issue on my end.

thanks for any help

You should read the user guide :)
There I'am mentioning that you need the package libtk-img for Ubuntu. In the backports repo of Hardy is Tcl 8.5 for me it works with the libtk-img that comes shipped with Hardy. Changing the symlink is a known issue if you've installed two different versions of Tcl.

I just uploaded a new alpha release with whom you're able to change the input of your device. Please let me if it works for you!

Regards

---

### Post by amsTaTic on 2009-01-30
First of all, thanks for a great program. I had it installed and working on Ubuntu 8.10 and the Hauppauge HVR-1600 in less than 10 minutes. 

My only problem seems to be how to get the remote working with TV-Viewer and lirc. I have installed lirc and it seems to be working, (I see info when running 'irw' in the terminal and pressing buttons on my Hauppauge_350 remote). I just can't figure out how to make it work with TV-Viewer. I read the lirc section in the user guide, but for some reason I just don't get it.

Any help would be greatly appreciated.

---

### Post by maasnet@chello.nl on 2009-02-01
You've installed a new version of TV-Viewer.
Old version could not be recognized.
Config files from unknown version can be found in:
/home/maasnet/.tv-viewer/backup_folder/unknown_version/
Error in startup script: couldn't read file "/usr/share/tv-viewer/themes/plastik/plastik.tcl": permission denied
    while executing
"source "$where_is/themes/plastik/plastik.tcl""
    (file "/usr/bin/tv-viewer" line 183)

Can you help me?

---

### Post by saedelaere on 2009-02-01
> **maasnet@chello.nl said:**
> You've installed a new version of TV-Viewer.
Old version could not be recognized.
Config files from unknown version can be found in:
/home/maasnet/.tv-viewer/backup_folder/unknown_version/
Error in startup script: couldn't read file "/usr/share/tv-viewer/themes/plastik/plastik.tcl": permission denied
    while executing
"source "$where_is/themes/plastik/plastik.tcl""
    (file "/usr/bin/tv-viewer" line 183)

Can you help me?

Weird, I installed it on many different Systems and never had problems with permissions.

Try this
```
chmod -R -v a+X /usr/share/tv-viewer/themes/*
```

Does it work? Oh you have to do this as root!

Regards

---

### Post by maasnet@chello.nl on 2009-02-01
sudo chmod -R -v a+X /usr/share/tv-viewer/themes/*

The same error:

/home/maasnet/.tv-viewer/config/tv-viewer-0.8a2.ver

Found a config directory in /home/maasnet
Error in startup script: couldn't read directory "/usr/share/tv-viewer/themes/plastik/plastik/": permission denied
    while executing
"glob -directory $imgdir *.gif"
    (procedure "LoadImages" line 3)
    invoked from within
"LoadImages [file join [file dirname [info script]] plastik]"
    (in namespace eval "::ttk::theme::plastik" script line 30)
    invoked from within
"namespace eval ttk::theme::plastik {

    variable version 0.6.1
    package provide ttk::theme::plastik $version

    variable colors
    array set c..."
    (file "/usr/share/tv-viewer/themes/plastik/plastik.tcl" line 13)
    invoked from within
"source "$where_is/themes/plastik/plastik.tcl""
    (file "/usr/bin/tv-viewer" line 183)

---

### Post by saedelaere on 2009-02-01
I don't get it, I installed it on Ubuntu 8.04 and 8.10 and this error didn't occur.

You might also want to try:

```
sudo chmod -R 755 /usr/share/tv-viewer/themes/*
```

EDIT: If it is still not workin please post the output of:

```
ls -l -R /usr/share/tv-viewer/themes/
```

---

### Post by maasnet@chello.nl on 2009-02-01
> **saedelaere said:**
> 

```
sudo chmod -R 755 /usr/share/tv-viewer/themes/*
```



Yes this works fine.

Thank you.

---

### Post by saedelaere on 2009-02-01
It is not a good solution, but as long as it works it is ok ;)

Since this is development snapshot it would be interesting for me what you like/dislike!

Regards

---

### Post by maasnet@chello.nl on 2009-02-01
I'take my snapshots now in VLC with <crtl> p.

I'm missing tv-viewer_rec --station=1 --date=2009.02.01 --time=19:00 --duration=01:00:00 :(

---

### Post by saedelaere on 2009-02-01
> **maasnet@chello.nl said:**
> I'take my snapshots now in VLC with <crtl> p.

I'm missing tv-viewer_rec --station=1 --date=2009.02.01 --time=19:00 --duration=01:00:00 :(

What do you mean by "I'take my snapshots now in VLC with <crtl> p." this keystroke has no effect on my vlc installation.

The record function is not lost it is simply not included in the alpha version. It will be back with the first beta release. If you want to go back to 0.7.7, you can find your old config files in /home/your_user_name/.tv-viewer/backup_folder/tv-viewer0.7.7 :)

Regards

---

### Post by maasnet@chello.nl on 2009-02-01
> **saedelaere said:**
> What do you mean by "I'take my snapshots now in VLC with <crtl> p." this keystroke has no effect on my vlc installation.

The record function is not lost it is simply not included in the alpha version. It will be back with the first beta release. If you want to go back to 0.7.7, you can find your old config files in /home/your_user_name/.tv-viewer/backup_folder/tv-viewer0.7.7 :)

Regards

No problem I will wait for the next beta release.

---

### Post by maasnet@chello.nl on 2009-02-01
I find a little bug;)

When I use the configuration-wizard I can not use the buttom to start VLC.



For the system tray icon of TV-Viewer you can also use --> All Tray.

---

### Post by saedelaere on 2009-02-01
> **maasnet@chello.nl said:**
> I find a little bug;)

When I use the configuration-wizard I can not use the buttom to start VLC.

No error message? You mean you set the video player to vlc using the config wizard. Afterwards you're not able to start tv playback?

---

### Post by maasnet@chello.nl on 2009-02-01
> **saedelaere said:**
> No error message? You mean you set the video player to vlc using the config wizard. Afterwards you're not able to start tv playback?

I get no error and when I use the configuration-wizard and I go exit then it is not possible to click on tv button.

---

### Post by saedelaere on 2009-02-01
> **maasnet@chello.nl said:**
> I get no error and when I use the configuration-wizard and I go exit then it is not possible to click on tv button.

The button is blocked? Or the video player is simply not starting? Are you sure VLC is not already running?
What I did. Opened the config wizard. Chose VLC as Video-Player clicked on apply then exit. No problems starting vlc afterwards. :confused:

---

### Post by maasnet@chello.nl on 2009-02-01
> **saedelaere said:**
> The button is blocked? Or the video player is simply not starting? Are you sure VLC is not already running?
What I did. Opened the config wizard. Chose VLC as Video-Player clicked on apply then exit. No problems starting vlc afterwards. :confused:

Yes the button is blocked.

When I only open the wizard and then apply/exit I must close and opening the program before I can starting VLC.

VLC is not running!

Excuse me for my bad english.

---

### Post by saedelaere on 2009-02-01
> **amsTaTic said:**
> First of all, thanks for a great program. I had it installed and working on Ubuntu 8.10 and the Hauppauge HVR-1600 in less than 10 minutes. 

My only problem seems to be how to get the remote working with TV-Viewer and lirc. I have installed lirc and it seems to be working, (I see info when running 'irw' in the terminal and pressing buttons on my Hauppauge_350 remote). I just can't figure out how to make it work with TV-Viewer. I read the lirc section in the user guide, but for some reason I just don't get it.

Any help would be greatly appreciated.

You're the first one reporting that he successfully uses TV-Viewer with a HVR-1600. Nice.

First of all you need to get your remote control working with lirc. Then my Section in the user guide is of interest for you.

Use irrecord to make a config file for your remote control...
Have to look how I did that. Will report back tomorrow on that issue :p

---

### Post by saedelaere on 2009-02-01
> **maasnet@chello.nl said:**
> Yes the button is blocked.

When I only open the wizard and then apply/exit I must close and opening the program before I can starting VLC.

VLC is not running!

Excuse me for my bad english.

Damn it can't track that back here. Are you using 0.8a2? Are other Buttons blocked to? Or even the whole gui?

You don't have to excuse for your english abilities, mine are not better. ;)

---

### Post by maasnet@chello.nl on 2009-02-01
> **saedelaere said:**
> Damn it can't track that back here. Are you using 0.8a2? Are other Buttons blocked to? Or even the whole gui?

You don't have to excuse for your english abilities, mine are not better. ;)

I'm using 0.8a2 and the other buttons are not blocked.

---

### Post by saedelaere on 2009-02-01
> **maasnet@chello.nl said:**
> I'm using 0.8a2 and the other buttons are not blocked.

And there are no messages in the terminal when you try to click on that button? Sry at the moment I can't help you because, like I mentioned, I can't track this bug here.

But thank you for your feedback

---

### Post by amsTaTic on 2009-02-02
> **saedelaere said:**
> You're the first one reporting that he successfully uses TV-Viewer with a HVR-1600. Nice.

First of all you need to get your remote control working with lirc. Then my Section in the user guide is of interest for you.

Use irrecord to make a config file for your remote control...
Have to look how I did that. Will report back tomorrow on that issue :p

Thanks for the reply.

I *sort of* have it working in TV Viewer.. but only when I run the command *irexec* in a terminal. When I do that, I can start up TV Viewer with the TV button on my remote. Since I have to run *irexec* in a terminal to make it work, I assume it is not running at boot up, but I am not sure.

I have a minimal *.lircrc* file in my home directory:

[I]begin
  prog = irexec
  remote = Hauppauge_350
  button = TV
  repeat = 0
  mode = tv-viewer
  config = tv-viewer --lirc
end

begin tv-viewer

begin
  prog = irexec
  remote = Hauppauge_350
  button = Ch+
  repeat = 0
  config = /usr/share/tv-viewer/data/lirc_empfang.tcl --tv channel_up
end


begin
  prog = irexec
  remote = Hauppauge_350
  button = Ch-
  repeat = 0
  config = /usr/share/tv-viewer/data/lirc_empfang.tcl --tv channel_down
end

end tv-viewer[/I]

I feel that I am close to making this work, and I await your reply.

---

### Post by saedelaere on 2009-02-03
> **amsTaTic said:**
> Thanks for the reply.

I *sort of* have it working in TV Viewer.. but only when I run the command *irexec* in a terminal. When I do that, I can start up TV Viewer with the TV button on my remote. Since I have to run *irexec* in a terminal to make it work, I assume it is not running at boot up, but I am not sure.

I have a minimal *.lircrc* file in my home directory:

[I]begin
  prog = irexec
  remote = Hauppauge_350
  button = TV
  repeat = 0
  mode = tv-viewer
  config = tv-viewer --lirc
end

begin tv-viewer

begin
  prog = irexec
  remote = Hauppauge_350
  button = Ch+
  repeat = 0
  config = /usr/share/tv-viewer/data/lirc_empfang.tcl --tv channel_up
end


begin
  prog = irexec
  remote = Hauppauge_350
  button = Ch-
  repeat = 0
  config = /usr/share/tv-viewer/data/lirc_empfang.tcl --tv channel_down
end

end tv-viewer[/I]

I feel that I am close to making this work, and I await your reply.

Perfect that's all you need. Now you just have to start irexec at the boot of your machine. Gnome provides a posibility 

System -> Preferences -> Sessions -> Startup Programs -> Add!

As command you should add ```
irexec -d
``` tis starts irexec as daemon. More Questions? :)
Oh and don't use the latest alpha if you want to have LIRC support. It is broken there.

---

### Post by amsTaTic on 2009-02-03
> **saedelaere said:**
> Perfect that's all you need. Now you just have to start irexec at the boot of your machine. Gnome provides a posibility 

System -> Preferences -> Sessions -> Startup Programs -> Add!

As command you should add ```
irexec -d
``` tis starts irexec as daemon. More Questions? :)
Oh and don't use the latest alpha if you want to have LIRC support. It is broken there.

Okay, I have *irexec* running at boot, and the *TV* button starts TV Viewer, but the channel buttons don't work. I have also tried adding commands to my *.lirc* file to control the volume, without success. 

Any idea what the problem is? Is there a problem with my *.lirc* file?

Anyway, thanks again for your time, and for a great program. :)

Oh, and I am using TV Viewer v0.7.7..

---

### Post by saedelaere on 2009-02-04
> **amsTaTic said:**
> Okay, I have *irexec* running at boot, and the *TV* button starts TV Viewer, but the channel buttons don't work. I have also tried adding commands to my *.lirc* file to control the volume, without success. 

Any idea what the problem is? Is there a problem with my *.lirc* file?

Anyway, thanks again for your time, and for a great program. :)

Oh, and I am using TV Viewer v0.7.7..

Hi amsTaTic,

```
begin
prog = irexec
remote = Hauppauge_350
button = TV
repeat = 0
mode = tv-viewer
config = tv-viewer --lirc
end
```

change:
config = tv-viewer --lirc

to:
config = tv-viewer --lirc &

If it doesn't help let me know, then i have to reinstall 0.7.7 on my system to check whats wrong there.

Regards

---

### Post by amsTaTic on 2009-02-04
> **saedelaere said:**
> Hi amsTaTic,

```
begin
prog = irexec
remote = Hauppauge_350
button = TV
repeat = 0
mode = tv-viewer
config = tv-viewer --lirc
end
```

change:
config = tv-viewer --lirc

to:
config = tv-viewer --lirc &

If it doesn't help let me know, then i have to reinstall 0.7.7 on my system to check whats wrong there.

Regards

Okay, that helped. Everything seems to work fine now. I can't believe I missed that *&* in the user guide.. doh! I looked at it for hours, too! :oops:

Thanks for your help, saedelaere! :biggrin:

---

### Post by rln526 on 2009-04-01
I hope this is an appropriate post here...

I am pleased to state that TV-Viewer is working very well on my Kubuntu box with a hauppage PVR 150 capture card.  I use VLC as my video application and TV-Viewer as the controller to change channels. The viewer does not seem to increase the CPU load significantly.  I'm using the analog signal from cable.  Though it's not digital, The picture is very clear in the window size I often use.

It took awhile to understand v4l & ivtv, then find the application, but it was well worth it.  I, like many others, wanted a simple interface just to see & hear the news as I work.  It's just what I wanted.  I think that's the advantage of Linux.  If you are willing to do some "work", you'll develop your own unique system built on your preferences.

I do also have a MythTV box which I use to record shows. Multimedia is the only function of that PC.

:D

---

### Post by fdmille on 2009-04-25
Just installed TV-Viewer 0.8b1 on my new Jaunty 9.04 installation and TV-Viewer works great.  I like the new interface of TV-Viewer, especially the "Zap among the last two stations" button.  Thank you, Christian Rapp! :popcorn:

---

### Post by Moonshade on 2009-05-10
After some woes with ivtv driver, got it working with AverTV MCE 116 Plus.

Also installed TV-Viewer 0.8b1 :) Best lightweight GUI for ivtv so far, rocking job!

Things to mention:
1) Would be nice to have main window and station editor resizeable, scrolling through the list of 50+ channels isn't much fun.
2) Ability to group channels in some kind of folders/subfolders, move them easily by drag'n'drop. Definitely required if you ever plan to support DVB cards, managing hundreds of DVB-S sats channels will be pain!
3) Perhaps more like a mplayer problem, but ability ivtv buffer underflow/overflow gracefully is non-existant. In case of big system load, lets say compiling big project, either player starves on resources and ivtv 4Mb buffer overflows, or ivtv driver itself stops filling buffer for a moment. In either case, playback just freezes or stops with mplayer EOF message in log :(
4) Station search: none of predefined frequency tables fit my situation, had to add some channels manualy. Could add ability to scan frequency range from 44.0 Mhz to 958.0 Mhz with a defined step (0.25 Mhz or so).

---

### Post by saedelaere on 2009-05-13
> **Moonshade said:**
> After some woes with ivtv driver, got it working with AverTV MCE 116 Plus.

Also installed TV-Viewer 0.8b1 :) Best lightweight GUI for ivtv so far, rocking job!

Things to mention:
1) Would be nice to have main window and station editor resizeable, scrolling through the list of 50+ channels isn't much fun.
2) Ability to group channels in some kind of folders/subfolders, move them easily by drag'n'drop. Definitely required if you ever plan to support DVB cards, managing hundreds of DVB-S sats channels will be pain!
3) Perhaps more like a mplayer problem, but ability ivtv buffer underflow/overflow gracefully is non-existant. In case of big system load, lets say compiling big project, either player starves on resources and ivtv 4Mb buffer overflows, or ivtv driver itself stops filling buffer for a moment. In either case, playback just freezes or stops with mplayer EOF message in log :(
4) Station search: none of predefined frequency tables fit my situation, had to add some channels manualy. Could add ability to scan frequency range from 44.0 Mhz to 958.0 Mhz with a defined step (0.25 Mhz or so).


1. That is a good suggestion I will see what I can do.

2. Yes that is correct. But I don't think I will integrate that soon.

3. That problem doesn't occur here. When I watch TV and generate a very high system load TV works perfect. Perhaps you should try to increase the cache for MPlayer. I will make further tests on this matter.

4. Hmm, where do you live? I thought of adding a complete frequency check but it would find duplicates of many stations. E.g. a station on 410.000 mhz would also be detected on 409.000 and 411.000 mhz. And the Program could determine if it is the same station. But I will add this feature and see how i could make the procedure reliable.

Thanks for the feedback!!!

Regards

---

### Post by ken_23434 on 2009-05-23
Thanks for creating the application.  I was looking for something simple for just watching TV on my computer.  The other applications I found seemed to dedicated to being a multi-media appliance.

I tried the Beta, but my player quit stopping on me.  I had to keep pressing the button that turns on the "tv" to restart it.  I reinstalled v 0.7.7 and the problem has gone away.

I am fairly new to Ubuntu, and there are many things I have probably done to "break" my system.  So, the application stopping playback might be some issue with my system.

It did seem to be somewhat consistent with me clicking links in my web-browser.  It would stop other times, too.  But, when ever I clicked a link, playback would stop.

I have been watching TV the whole time I searched for this thread and have been replying with no playback problem with 0.7.7.

Now, if anyone knows how to set up the computer for easy recording of shows based on a channel guide...  I used SageTV on my XP setup.  I am not looking for full media center features, just the ability to tell my computer to record X,Y and Z anytime they are on, so I can watch shows later or burn them to disk for keeping.

---

### Post by saedelaere on 2009-05-25
> **ken_23434 said:**
> Thanks for creating the application.  I was looking for something simple for just watching TV on my computer.  The other applications I found seemed to dedicated to being a multi-media appliance.

You're welcome

> I tried the Beta, but my player quit stopping on me.  I had to keep pressing the button that turns on the "tv" to restart it.  I reinstalled v 0.7.7 and the problem has gone away.

I am fairly new to Ubuntu, and there are many things I have probably done to "break" my system.  So, the application stopping playback might be some issue with my system.

Please, the 0.8b1 has two important logfiles and a diagnostic routine. Run the routine and attach the output file and the logfiles to your post. Otherwise I won't be able to help you.

> It did seem to be somewhat consistent with me clicking links in my web-browser.  It would stop other times, too.  But, when ever I clicked a link, playback would stop.

Puuh, there should be no relation between your webbrowser and MPlayer. I've never had the problems you described. Again it would be useful to see the output of the diagnostic routine.

> I have been watching TV the whole time I searched for this thread and have been replying with no playback problem with 0.7.7.

Now, if anyone knows how to set up the computer for easy recording of shows based on a channel guide...  I used SageTV on my XP setup.  I am not looking for full media center features, just the ability to tell my computer to record X,Y and Z anytime they are on, so I can watch shows later or burn them to disk for keeping.

What do you mean by "based on a channel guide"? Have you read the user guide of version 0.7.7? It can record shows at a specific time and so on. The feature was broken in all 0.8x versions. But I will release a new version at the end of this week (at least I hope so :)). This one will include a record wizard as gui.

Regards

---

### Post by ken_23434 on 2009-05-28
Referring to my comment on recording based on a program guide...

When I used SageTV it featured an electronic program guide.  I think I could browse out about 7 days in the future for shows.  By highlighting a selection, I could just click on a button that would program it to record that show.  It also had a feature to make it as a "favorite" so it would record the same "title" or "subject" on any channel at any time until I told it to stop.

The electronic program guide is just handy to find out what to watch.  I know I can pull the data from some websites, but if it was incorporated into the Tv-Viewer application, it would be handier.

NOT complaining... Just voicing a couple desires (based on me being too lazy to do the same things in other ways :D )

---

### Post by saedelaere on 2009-05-29
> **ken_23434 said:**
> Referring to my comment on recording based on a program guide...

When I used SageTV it featured an electronic program guide.  I think I could browse out about 7 days in the future for shows.  By highlighting a selection, I could just click on a button that would program it to record that show.  It also had a feature to make it as a "favorite" so it would record the same "title" or "subject" on any channel at any time until I told it to stop.

The electronic program guide is just handy to find out what to watch.  I know I can pull the data from some websites, but if it was incorporated into the Tv-Viewer application, it would be handier.

NOT complaining... Just voicing a couple desires (based on me being too lazy to do the same things in other ways :D )

Yeah you are right, such a feature or EPG scheduler would be great. I'll see what I can do :)
What about the other things I asked from you?

---

### Post by saedelaere on 2009-12-27
Hi,

today i'am releasing the new stable [version 0.8.1]("http://home.arcor.de/saedelaere/download_eng.html"), after one year of development with several alpha and beta versions. During this period of time TV-Viewer evolved from a simple Gui, able to change stations, to a stand-alone TV Application.
The most important features are listed [here]("http://home.arcor.de/saedelaere/info_eng.html#Features:"), and please note the [screenshots]("http://home.arcor.de/saedelaere/shots_eng.html").

An important hint for all users of TV-Viewer < 0.8.1a1. Please delete the configuration directory "~/.tv-viewer" und create a new stations list and check the configuration before you install the new version. Otherwise problems can be expected.

As always if you find errors or you have something else on your mind, please [contact]("http://home.arcor.de/saedelaere/contact_eng.html") me.

Best regards
Christian

---

### Post by arron on 2010-01-01
This is great news.  I will get it installed and try it out.

Thanks

---

### Post by JarekG on 2010-01-01
If we can only have transparent set-up that would be great.
I just install this and is working great (better than windows...for sure :))

---

### Post by saedelaere on 2010-01-03
> **JarekG said:**
> If we can only have transparent set-up that would be great.
I just install this and is working great (better than windows...for sure :))

Hi,

what is a transparent set-up?

Regards

---

### Post by Uncle Spellbinder on 2010-01-03
Is a .deb be available?. Is there a TV Viewer Ubuntu Repo? A PPA Repo?

---

### Post by saedelaere on 2010-01-03
> **Uncle Spellbinder said:**
> Is a .deb be available?. Is there a TV Viewer Ubuntu Repo? A PPA Repo?

I have a PPA repo yes, but i'am a "programmer" not a package maintainer. The current installation method is very easy and there are only a few dependencies.
At the moment this is in most parts a one man show. So i use all the time i can spare on development.

---

### Post by JarekG on 2010-01-04
> **saedelaere said:**
> Hi,

what is a transparent set-up?

Regards

I think what he means that it would be nice to set transparency of the main window (see through)....so when watching TV you could still work on other stuff and see the other stuff through the TV window...I think one of the Hauppauge apps at one time had future like that.

---

### Post by saedelaere on 2010-01-04
> **JarekG said:**
> I think what he means that it would be nice to set transparency of the main window (see through)....so when watching TV you could still work on other stuff and see the other stuff through the TV window...I think one of the Hauppauge apps at one time had future like that.

Do you really think he meant this? Strange idea, sorry :) In fact Tk may support transparent windows, but only with a working compositor.

Btw
TV-Viewer on [launchpad]("http://launchpad.net/tv-viewer")

Regards

---

### Post by JarekG on 2010-01-04
> **saedelaere said:**
> Do you really think he meant this? Strange idea, sorry :) In fact Tk may support transparent windows, but only with a working compositor.

Btw
TV-Viewer on [launchpad]("http://launchpad.net/tv-viewer")

Regards

I thinks so (I would like that future as well). I'm not a *nix developer (Windows and .NET for me only...sorry) so I'm not sure how hard would that be. In windows is almost build in to framework (in C# and vb.net it is anyway). 
As it is, it's a nice application and since I just installed Ubuntu again (work required me to have windows for a while) I had no problem installing it and it just works (Ubuntu 9.10 x64), use it every day :P

---

### Post by User_Program on 2010-01-27
Thank You!
Very stable. 
Keep up the good work Christian!

---

### Post by saedelaere on 2010-05-12
Hi

I've just released a new stable version 0.8.1.1 

I don't want to write to much here, because all you need to know is located on our [new web site.]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Main_Page") 

Enjoy!

---

### Post by jacrider on 2010-05-27
Many thanks for developing this application.  I was searching for a simple TV viewing application.

I have it up and running in Ubuntu 9.10 with a Hauppauge PVR 150 card I had around.

I am seeking to be able to record old VHS tapes to my computer.

Can I simply do this?

1.  Connect the VCR via coax to the cable input line on the PVR 150.
2.  Set the VCR to transmit on Ch 3
3.  Go to TV-Viewer and tune to Ch 3
4.  "Play" the VCR
5.  Set TV-Viewer to record
6.  Wait for the tape to play through

So, is that right?

What format will the recording be in?  .mp4?

Sorry for so many questions, but thanks for the development work.

---

### Post by WinterRain on 2010-05-27
> **saedelaere said:**
> Hi

I've just released a new stable version 0.8.1.1 

I don't want to write to much here, because all you need to know is located on our [new web site.]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Main_Page") 

Enjoy!

Great job! Thank you very much for this. Before I was using VLC to watch TV, and while vlc did a good job of it, it was difficult to schedule recordings. I was actually using cron for that. :confused:

But anyway, thanks again and keep up the good work.

Edit: after using it for a bit, I find that it doesn't always start up when clicking the menu icon, or from the terminal. It only starts maybe 1 out of every 8 tries. When starting from terminal, I get a Segmentation fault and it won't start. But then I'll go back to the menu, and it will start. Strange. Any ideas?

It is not a deal breaker, as I can get it going, but it's a minor annoyance. Great app though.

---

### Post by saedelaere on 2010-05-31
> **jacrider said:**
> Many thanks for developing this application.  I was searching for a simple TV viewing application.

I have it up and running in Ubuntu 9.10 with a Hauppauge PVR 150 card I had around.

I am seeking to be able to record old VHS tapes to my computer.

Can I simply do this?

1.  Connect the VCR via coax to the cable input line on the PVR 150.
2.  Set the VCR to transmit on Ch 3
3.  Go to TV-Viewer and tune to Ch 3
4.  "Play" the VCR
5.  Set TV-Viewer to record
6.  Wait for the tape to play through

So, is that right?

What format will the recording be in?  .mp4?

Sorry for so many questions, but thanks for the development work.

In general this is correct yes. It might be necessary to perform a station search to find the correct channel. Do this while your vcr is sending a signal. 
To record you can use timeshift mode or the record wizard, all recordings will be in mpeg2 format (mpeg-ps) because this is what the pvr 150 delivers. You can convert the video using avidemux. There is a special guide for ivtv devices and avidemux

[http://www.avidemux.org/admWiki/doku.php?id=tutorial:editing_mpeg_capture](http://www.avidemux.org/admWiki/doku.php?id=tutorial:editing_mpeg_capture)

Regards 

> **WinterRain said:**
> Great job! Thank you very much for this. Before I was using VLC to watch TV, and while vlc did a good job of it, it was difficult to schedule recordings. I was actually using cron for that. :confused:

But anyway, thanks again and keep up the good work.

Edit: after using it for a bit, I find that it doesn't always start up when clicking the menu icon, or from the terminal. It only starts maybe 1 out of every 8 tries. When starting from terminal, I get a Segmentation fault and it won't start. But then I'll go back to the menu, and it will start. Strange. Any ideas?

It is not a deal breaker, as I can get it going, but it's a minor annoyance. Great app though.

This is really strange, never heard about this problem before. Do you use 64bit on Ubuntu 10.04? Please try one thing start TV-Viewer from the command line with the following command

```

tv-viewer --debug

```

Please post the output until the sementation fault occurs.

Best regards
Christian

---

### Post by WinterRain on 2010-05-31
Here is the output:
```
me@me:~$ tv-viewer --debug
This is TV-Viewer 0.8.1.1 Build 89 ...
loading shared libraries
Activating debug messages
Debug: main_readConfig 
Debug: log_viewerCheck 
Debug: create_icons 
Debug: launch_splash_screen 
Debug: launch_splashAnigif  {/usr/local/share/tv-viewer/icons/extras/animated_loading.gif}
Debug: main_readStationFile 
Debug: agrep  {-m} {video}
Debug: main_frontendUiTvviewer 
Debug: main_pic_streamColormControls 
Debug: tooltips  {.bottom_buttons} {.top_buttons} {main}
Debug: settooltip  {.bottom_buttons.button_channelup} {Tune up.}
Debug: settooltip  {.bottom_buttons.button_channeldown} {Tune down.}
Debug: settooltip  {.bottom_buttons.button_channeljumpback} {Zap among the last two stations.}
Debug: settooltip  {.bottom_buttons.button_showslist} {Show/hide station list.}
Debug: settooltip  {.bottom_buttons.scale_volume} {Alter volume.}
Debug: settooltip  {.bottom_buttons.button_mute} {Toggle mute.}
Debug: settooltip  {.top_buttons.button_timeshift} {Start/Stop timeshift.}
Debug: settooltip  {.top_buttons.button_record} {Start/Stop record.}
Debug: settooltip  {.top_buttons.button_epg} {Execute the selected epg application.}
Debug: settooltip  {.top_buttons.button_starttv} {Start/stop tv playback.}
Segmentation fault

```

Mind you, it *does* work. I have a launcher on my panel, and if I click it rapidly, after about 6-8 clicks, it will start. Like I said, not a showstopper.

---

### Post by saedelaere on 2010-06-01
> **WinterRain said:**
> Here is the output:
```
me@me:~$ tv-viewer --debug
This is TV-Viewer 0.8.1.1 Build 89 ...
loading shared libraries
Activating debug messages
Debug: main_readConfig 
Debug: log_viewerCheck 
Debug: create_icons 
Debug: launch_splash_screen 
Debug: launch_splashAnigif  {/usr/local/share/tv-viewer/icons/extras/animated_loading.gif}
Debug: main_readStationFile 
Debug: agrep  {-m} {video}
Debug: main_frontendUiTvviewer 
Debug: main_pic_streamColormControls 
Debug: tooltips  {.bottom_buttons} {.top_buttons} {main}
Debug: settooltip  {.bottom_buttons.button_channelup} {Tune up.}
Debug: settooltip  {.bottom_buttons.button_channeldown} {Tune down.}
Debug: settooltip  {.bottom_buttons.button_channeljumpback} {Zap among the last two stations.}
Debug: settooltip  {.bottom_buttons.button_showslist} {Show/hide station list.}
Debug: settooltip  {.bottom_buttons.scale_volume} {Alter volume.}
Debug: settooltip  {.bottom_buttons.button_mute} {Toggle mute.}
Debug: settooltip  {.top_buttons.button_timeshift} {Start/Stop timeshift.}
Debug: settooltip  {.top_buttons.button_record} {Start/Stop record.}
Debug: settooltip  {.top_buttons.button_epg} {Execute the selected epg application.}
Debug: settooltip  {.top_buttons.button_starttv} {Start/stop tv playback.}
Segmentation fault

```

Mind you, it *does* work. I have a launcher on my panel, and if I click it rapidly, after about 6-8 clicks, it will start. Like I said, not a showstopper.

Ok I tried for myself and you are right. i tested on kubuntu 10.04 and got some segfaults. Not always but sometimes. One thing I realized the application uses fallback icons as window icons, so I tried to create a backtrace and I think I found the cause. The problem is the tk8.5 package from ubuntu, there is patch to fix this issue for 64bit systems but it is not included. I created a [bug report]("https://bugs.launchpad.net/bugs/588377"). Let us hope they will fix the package soon. Currently only 64bit k/x/ubuntu is affected 32bit works without issues. A possible fix is to install [Activetcl]("http://www.activestate.com/activetcl/downloads"). This is quite easy but do not forget to update the symlinks wish and tclsh so they point to the new location. (sudo update alternatives wish || tclsh)

---

### Post by jacrider on 2010-06-02
> **saedelaere said:**
> In general this is correct yes. It might be necessary to perform a station search to find the correct channel. Do this while your vcr is sending a signal. 
To record you can use timeshift mode or the record wizard, all recordings will be in mpeg2 format (mpeg-ps) because this is what the pvr 150 delivers. You can convert the video using avidemux. There is a special guide for ivtv devices and avidemux


Thanks for the reply.  I will give this a go and report back.

---

### Post by saedelaere on 2010-06-03
If someone wants to use ActiveTcl instead of Ubuntu packages I have written a guide available in the [howto section]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Howto#Replacing_included_Tcl.2FTk_packages_with_ActiveTcl")


Regards

---

### Post by saedelaere on 2010-10-11
Hi,

yesterday I finally managed to build my first deb Package. From now on TV-Viewer is available over my [PPA at Launchpad]("https://launchpad.net/~saedelaere/+archive/tv-viewer"). Be sure to uninstall TV-Viewer before you use the deb packages. This will not touch your configuration.

Regards

---

### Post by cariocap on 2010-11-15
Hi all,

Just to help other guys from Brazil to configure TV-Viewer to use in Brazil that has the PAL-M system.

1) Exit TV-Viewer
2) Edit your /etc/youruser/.tv-viewer/tv-viewer.conf and change the line with video_standard to:
video_standard {PAL-M}
3) Run TV-Viewer
4) In Options/Preferences/Analog/Video Standard select Force Standard
5) In frequency table select us-bcast and click in apply

Go to Options / Station Editor and search the stations.
That's all.

---

### Post by saedelaere on 2010-11-16
> **cariocap said:**
> Hi all,

Just to help other guys from Brazil to configure TV-Viewer to use in Brazil that has the PAL-M system.

1) Exit TV-Viewer
2) Edit your /etc/youruser/.tv-viewer/tv-viewer.conf and change the line with video_standard to:
video_standard {PAL-M}
3) Run TV-Viewer
4) In Options/Preferences/Analog/Video Standard select Force Standard
5) In frequency table select us-bcast and click in apply

Go to Options / Station Editor and search the stations.
That's all.


Dear cariocap,

I am bit confused you had to edit the tv-ciewer config file to get this working. If you select PAL in the preferences it should set the color transmission standard automatically to PAL-M. We should do some tests about this, so I know how to fix it. Unfortunately I wont have any time before Thursday. I will post some commands here and it would be nice if you could execute them on your system and post the output here. Is this OK for you?

Best Regards
Christian

---

### Post by cariocap on 2010-11-16
Ok, waiting for the commands

I have a few problems to report, like:

1) Sometimes I have to execute twice tv-viewer for it to work.

2) Error "WARNING:  MPlayer reported end of file. Playback has stopped.", so, no tv output. I have to kill mplayer process for tv-viewer work.

Thanks,
Abel

---

### Post by saedelaere on 2010-11-16
> **cariocap said:**
> Ok, waiting for the commands

I have a few problems to report, like:

1) Sometimes I have to execute twice tv-viewer for it to work.

2) Error "WARNING:  MPlayer reported end of file. Playback has stopped.", so, no tv output. I have to kill mplayer process for tv-viewer work.

Thanks,
Abel

For the first ine, start TV-Viewer from the command line. If it does not start and you see something like segmentation fault you will need to install [activeTCL]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Howto#Replacing_included_Tcl.2FTk_packages_with_ActiveTcl"). The bug is reported but Ubuntu wont fix. Should also be fixed by the next Ubuntu release because then they will ship tcl/tk 8.5.9

In fact I don't understand what you mean by the second problem. You want to start TV playback but it does not work and you get this message? This may happen if you kill TV-Viewer while TV-Playback. Then mplayer continues to run in the background and blocks the hardware device. I will think about a mechanism to circumvent this problem.

Regards

---

### Post by cariocap on 2010-11-16
I started TV-Viewer from the command line and got "Segmentation fault" error.

I installed ActiveTcl following your howto instructions and now it starts ok (only need to run it once).

PS: when I run TV-Viewer from the console I saw the error "can't find package tktray 1.3.3" before starting TV-Viewer.

Again I have to kill mplayer process because TV-Viewer started but without TV output and log the error at tvviewer.log "WARNING:  MPlayer reported end of file. Playback has stopped.".

To exit tv-viewer I'm just clicking on X to close it. I will avoid this and use Options / Exit.

Thanks for your help and keep the good work.

Abel
[B]
 [/B]

---

### Post by saedelaere on 2010-11-21
> **cariocap said:**
> I started TV-Viewer from the command line and got "Segmentation fault" error.

I installed ActiveTcl following your howto instructions and now it starts ok (only need to run it once).

PS: when I run TV-Viewer from the console I saw the error "can't find package tktray 1.3.3" before starting TV-Viewer.

Again I have to kill mplayer process because TV-Viewer started but without TV output and log the error at tvviewer.log "WARNING:  MPlayer reported end of file. Playback has stopped.".

To exit tv-viewer I'm just clicking on X to close it. I will avoid this and use Options / Exit.

Thanks for your help and keep the good work.

Abel
[B]
 [/B]

Hi Abel,

problem is you can not use ActiveTCL and the debian package we are providing. It basically works but things like system tray integration will not. So if you are using ActiveTCL remove the debian package and use the provided installer to install tv-viewer. It is quite easy. With the next release of ubuntu this problems should be solved if they ship tk 8.5.9

You should be able to use the X to exit TV-Viewer and mplayer backend process should be stopped. Although I think there is a bug in version 0.8.1.1 that may prevent this from time to time.

Now the problem with Pal. First we have to reload the ivtv driver to get standard values. therefor you have to stop tv playback and please close TV-Viewer.

```
sudo modprobe -r ivtv
sudo modprobe ivtv
```

then we will ask the device for current settings

```
v4l2-ctl -d /dev/video0 --all
```

Please substitute "/dev/video0" with you video device node if it is different and post the output of this command here. This will help me to see how to fix the problem with PAL-M

Best Regards
Christian

---

### Post by cariocap on 2010-11-21
Hi Christian,

Here is the result of the command 
v4l2-ctl -d /dev/video0 --all
[FONT=monospace]
Driver Info:
    Driver name   : ivtv
    Card type     : Hauppauge WinTV PVR-150
    Bus info      : PCI:0000:03:07.0
    Driver version: 66561
    Capabilities  : 0x01030051
        Video Capture
        VBI Capture
        Sliced VBI Capture
        Tuner
        Audio
        Read/Write
Format Video Capture:
    Width/Height  : 720/480
    Pixel Format  : 'MPEG'
    Field         : Interlaced
    Bytes per Line: 0
    Size Image    : 131072
    Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)
Format Sliced VBI Capture:
    Service Set    : 
    Service Line  0:          /         
    Service Line  1:          /         
    Service Line  2:          /         
    Service Line  3:          /         
    Service Line  4:          /         
    Service Line  5:          /         
    Service Line  6:          /         
    Service Line  7:          /         
    Service Line  8:          /         
    Service Line  9:          /         
    Service Line 10:          /         
    Service Line 11:          /         
    Service Line 12:          /         
    Service Line 13:          /         
    Service Line 14:          /         
    Service Line 15:          /         
    Service Line 16:          /         
    Service Line 17:          /         
    Service Line 18:          /         
    Service Line 19:          /         
    Service Line 20:          /         
    Service Line 21:          /         
    Service Line 22:          /         
    Service Line 23:          /         
    I/O Size       : 0
Format VBI Capture:
    Sampling Rate   : 27000000 Hz
    Offset          : 248 samples (9.18519e-06 secs after leading edge)
    Samples per Line: 1440
    Sample Format   : GREY
    Start 1st Field : 10
    Count 1st Field : 12
    Start 2nd Field : 273
    Count 2nd Field : 12
Crop Capability Video Output:
    Bounds      : Left 0, Top 0, Width 720, Height 480
    Default     : Left 0, Top 0, Width 720, Height 480
    Pixel Aspect: 10/11
Video input : 0 (Tuner 1)
Audio input : 0 (Tuner 1)
Frequency: 1076 (67.250000 MHz)
Video Standard = 0x00001000
    NTSC-M
Tuner:
    Name                 : ivtv TV Tuner
    Capabilities         : 62.5 kHz multi-standard stereo lang1 lang2 
    Frequency range      : 44.0 MHz - 958.0 MHz
    Signal strength/AFC  : 100%/0
    Current audio mode   : lang1
    Available subchannels: mono lang2 

Thanks,
Abel
[/FONT]

---

### Post by saedelaere on 2010-11-21
Ok do the following
```
sudo modprobe -r ivtv
sudo modprobe ivtv
v4l2-ctl --device=/dev/video0 --set-standard=pal
```

then post the ouput of ```
v4l2-ctl --device=/dev/video0 --get-standard
``` here

---

### Post by cariocap on 2010-11-21
abel@ABEL-PC:~$ v4l2-ctl --device=/dev/video0 --get-standard
Video Standard = 0x000000ff
    PAL-B/B1/G/H/I/D/D1/K

---

### Post by saedelaere on 2010-11-21
> **cariocap said:**
> abel@ABEL-PC:~$ v4l2-ctl --device=/dev/video0 --get-standard
Video Standard = 0x000000ff
    PAL-B/B1/G/H/I/D/D1/K

Ok thank you. This is really a missing feature. I thought setting video standard to pal would choose the right video standard automatically. I will add this feature in version 0.8.2. Thank you very much for your cooperation. If I have something ready, I will contact you.

Best Regards
Christian

---

### Post by cariocap on 2010-11-21
I thank you for helping us and made possible for me and other guys to use this TV card.

---

### Post by saedelaere on 2010-12-30
> **cariocap said:**
> I thank you for helping us and made possible for me and other guys to use this TV card.

Cariocap, with TV-Viewer 0.8.2a1 revision 146 it should be possible to change video standard to PAL-M. Please give it a go and report back to me if it works. There is a [howto]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Development_Bazaar") how you can obtain the the latest source code.

Regards

---

### Post by andybnj on 2011-07-28
Christian ... thank you so much for your work on tv-viewer.  

I wrestled with myth for weeks without getting it to work on my desktop (worked on my laptop but I didn't want to run primary backend on my laptop).  When all you want to do is watch tv and maybe record something every now and then, myth is overkill and their approach is not exactly intuitive.  

I tried every linux tv software I found via google (too many to mention), and then I found tv-viewer.  Simple ... easy ... clean ... most importantly IT WORKS!!! 

btw, I am using hauppauge hvr-1950 analog mode, connected to cable converter box

kudos to you for this fine work

---

### Post by bandarman on 2011-11-22
saedelaere, I've registered on this forum just to thank you and to follow developments with TV-Viewer. :)

I've tried everything I could to get TV running on my Linux box without success: mythtv, xine, freevo, tvtime, zapping tv viewer, sagetv, freetuxtv, xino, xawtv, plain ivtv, Me TV, Digital TV Control Center, etc. etc, and all without success, and then I stumbled across TV-Viewer. Phew.

TV-Viewer still has some stability issues (shuts down inexplicably when, for example, I change my frequency table and hit apply, among other setting changes) but it continues to work after restarting. Thank you!!!

Yes, I realize many of the apps I tried are DVB only (found out after trying) while my needs are for an analog tv app. Still, TV-Viewer is much more polished aesthetically, showing how much effort you put into the application. 

For the record I'm on Ubuntu 11.10 (64bit) with TV-Viewer v.8.1.1 (build 89 via PPA, not a self-build) and a Hauppauge WinTV PVR-500, using an analog cable connection in Bhutan. For some reason I'm able to best tune in using PAL as the video standard with japan-cable/us-cable as the frequency table (picture and sound stutters a bit). I will experiment with other freqtables, read up on work arounds discussed here, and will post things others may find useful from time to time.

For the time being, thanks so much again!

---

### Post by bandarman on 2011-11-23
Update:

1) I've tried different freqtables and so far europe-west, us-cable and japan-cable seem to find the most channels off my analog cable connection. However, the sound and video stutters - lots of frames dropped it seems. Any ideas why that may be?

2) TV-Viewer shuts down frequently. Not so much during viewing, and changing channels (thank God :) but definitely between editing channel names, changing freqtables or searching for channels, etc. Do you think it has anything to do with tk/tcl which is mentioned in other posts? I presently don't have tk and tcl  installed.

Thanks in advance.

---

### Post by wolfen69 on 2011-11-23
You may also want to see my tutorial for using vlc player to watch tv. [http://ubuntuforums.org/showthread.php?t=1734916](http://ubuntuforums.org/showthread.php?t=1734916)

---

### Post by bandarman on 2011-11-23
Thanks wolfen69 for your help. I have, however, earlier tried ivtv and vlc together and it worked. However, I was able to get only a very limited number of channels and mostly not properly tuned also. I played with freqtables and other settings using ivtv-tune and v4l2-ctl etc, but was not able to custom search nor manually tune signals from my analog cable connection. Is there any command that allows me to do that, like we can in TV-Viewer? I'm sure we can, since TV-Viewer is built on ivtv, but having gone through the list of ivtv and v4l2-ctl commands, none seemed to point that way. Your tips in this direction will be appreciated.

---

### Post by wolfen69 on 2011-11-23
I know for ivtv, you would do:
```
ivtv-tune -f 61.250 MHz
```
to change frequencies. But you will have to google for your local (PAL) frequencies.

---

### Post by bandarman on 2011-11-23
Thanks wolfen69, I'll try that. Additionally, is there any way to scan for available channels and save the list rather than doing it frequency by frequency?

---

### Post by bandarman on 2011-11-25
There aren't any TV programming standards set where I live as the cable service providers just slap on whatever they like using an assortment of inputs from multiple content sources. So pulling a table of frequencies from a standards body wasn't possible.

Since TV-Viewer is prone to crashing (on my system described a few posts ago) I've found that I can and have to get around by scanning for channels using TV-Viewer, and then editing the populated config files generated by TV-Viewer. This way I can name the channels to suit myself and avoid crashing TV-Viewer. Multiple crashes tend to become unrecoverable (TV-Viewer stops responding, sometimes even after shutting down the mplayer process).

So I basically edited the stations_europe-west.conf, stations_japan-cable.conf (depending on what I was trying to tune via) and had TV-Viewer read it upon running. Sometimes TV-Viewer wouldn't load after such edits - the work around was to toggle the setting for frequency_table in the tv-viewer.conf file. All conf files were in the .tv-viewer directory. One time TV-Viewer wouldn't run even after trying all of this after editing the conf files, so I uninstalled and reinstalled, then replaced the station_x.conf file with my backed up list of channels and frequencies.

This way I get to use the TV-Viewer remote and avoid ivtv-tune intimacy. :) The only bummer is my picture clarity is still poor - got to figure this one out. I've been checking cable line quality as well as connection points, plus signal strength but no luck so far.

---

### Post by saedelaere on 2011-11-27
@bandarman

Tcl/tk is buggy in version 8.5.10, in order to circumvent this problem you have to install the latest beta version of tv-viewer and use one of our tclkits as described in this [howto]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Howto#Using_a_precompiled_Tclkit_to_run_TV-Viewer").

If no frequency table applies to your country, just use the full frequency sweep. It should find all stations that you are able to receive, but it will also find many duplicates that you have to delete yourself. Also you might need to finetune the channels a bit.

Regards

---

### Post by bandarman on 2011-11-27
saedelaere: Thank you for responding here, and more than that, thank you for TV-Viewer! It's a great application, regardless of the small problems I'm having.

Yes, I've resorted to the full frequency sweep already and find that it pretty much finds all the channels available. I also tried fine tuning, but that wasn't very useful as TV-Viewer seemed to have already got it tuned as best as was possible given my signal quality. I'm playing around with the physical splitters and cables coming into my house as that seems to be part of the problem regarding my signal strength.

Regarding using the latest beta builds of TV-Viewer, I realized from some of the earlier posts here that that was worth a go. More so after reading up on the many new features and changes you are bringing in v. 0.8.2. :) I did in fact try a local build but that failed, and I learned that it had to do with tk/tcl. I will read up on how to handle tk/tcl from the link you provided, and get back with my experience on this thread.

For the record I want to say that despite my questions here about the instability of TV-Viewer on my system, after working around on the channel listings in the way I described, TV-Viewer works great for me and I like it very much. It provides everything I was used to in my older Windows Media Center box (time shifting, record scheduling, etc) but with so much of a smaller foot print.

Update: I built v. 0.8.2b1 following the instructions using the pre-built tclkit. TV-Viewer is now stable on my system. Thanks :)

---

### Post by buddy_t on 2011-12-31
This program is great, works, so far as it should, quick and easy set up. Thank you!  I have a Hauppauge HVR-1600 PCI, sound works great as well, 64bit 11.10

Buddy

---

### Post by herteljt on 2012-07-02
Hi,
I am running ver 8.2.x. I was wondering if there was a way to have tv-viewer to record from composite. Is there a command line option to set the video input? I've looked on the wiki, but I could not find an answer.

Thanks!

---

### Post by herteljt on 2012-07-03
I should note for anyone looking to record from composite (and stumbling upon this thread) it can be done using the cat command. Make sure ivtv-utils is installed and then use  v4l2-ctl to change the card to composite. 

```
 v4l2-ctl -i 2

```

```
cat /dev/video > output.mpg

```
I was just wondering if tv-viewer had the capability as well.

---

### Post by saedelaere on 2012-07-19
Sorry for the late answer. TV-Viewer can record from any input, you just have to define a new station, this station uses a different input than Tuner. If you record from this new station the appropriate video input will be used. 

Best Regards
Christian

---

### Post by nomm on 2012-08-28
How to make other start volume level in tv-viewer??? My tv-viewer always starts at level 100% but it is very  not comfortably. I prefer that he memorized a previous level or started from a level for example 5%

---

