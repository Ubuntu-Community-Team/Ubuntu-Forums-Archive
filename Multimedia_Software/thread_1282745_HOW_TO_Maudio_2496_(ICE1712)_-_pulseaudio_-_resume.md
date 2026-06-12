---
title: "HOW TO: Maudio 2496 (ICE1712) - pulseaudio - resume from suspend hibernate workaround"
date: 2009-10-04
forum: Multimedia Software
---

### Post by bboydushko on 2009-10-04
Hello crazy kids!

I decided to write this 'how to' for all of you that can't get the **M-Audio Audiophile 2496** sound card working in Ubuntu. I'm using Ubuntu Hardy 8.04 x64, but this may work for others too. I've read many other guides and bug threads that helped me to get it working finally.
The fresh installed Ubuntu will normally detect this card and audio works straight away... ...but soon you will want to have full control over your audio (especially if you have more than one sound device) therefore you will probably end up installing **pulseaudio** and this is where the trouble begins.
Pulseaudio has a good way for controlling output and input audio streams over your sound devices in Ubuntu however audiophile 2496 card is not visible in **pulseaudio volume control** by default. The second bad thing about this card (which some of you might have noticed already) is that it won't work when you resume your previously suspended or hibernated system. For me this was a real nightmare. I was not able to hibernate in new Ubuntu 9 - Jauty Jackalope and because I use the hibernation all the time I had to stay with older Ubuntu Hardy. Finding that my sound is gone when resuming in Hardy was a real 'kick into my smiling face'. Anyway this is what I've done to get it working:

1.) First of all you'll need to **install and setup the pulseadio**. I will give you the link to the excellent guide but also will show you the steps I've taken from there. Please note this guide ends with step 4. log out & log in back again. Before you do so you'll need to add some lines into the **default.pa** file so that M-Audio 2496 will show up in the pulseaudio volume control. default.pa file is a configuration file for pulseaudio. So, [COLOR=Blue]_[SIZE=3][here]("http://ubuntuforums.org/showthread.php?t=789578")[/SIZE]_[/COLOR] is the link to the guide and these are the steps I've done (steps for Hardy Heron x64):

All steps from section A in short:

```
$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound*
$ sudo rm /etc/asound.conf

$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
```Steps from section B:

Install **getlibs-all** (64-bit users only). The link for wget in that guide is broken so I downloaded the getlibs-all.deb from[COLOR=Blue] _[SIZE=3][here]("http://www.hotshare.net/en/file/61002-6358541df0.html")[/SIZE]_[/COLOR], clicked right mouse button on the file and installed it with 'GDebi Package Installer'. After this was done I run:
```
$ sudo getlibs -p libnss3-1d libnspr4-0d libcurl3 libasound2-plugins
```Edit /etc/apt/sources.list:
```
$ gksudo gedit /etc/apt/sources.list
```If they don't already exist, add the following lines to the end of this file and save:
```
# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main
```Add the authentication key for my PPA, update your repositories and upgrade packages:
```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16AE4E77 && sudo apt-get update && sudo apt-get dist-upgrade
```Enable the PulseAudio ALSA plugins:
```
$ asoundconf set-pulseaudio
```**The next step is to open your pulseaudio config file:**
```
$ sudo gedit /etc/pulse/default.pa
```Select, copy and paste following lines at the end of the file (more info about this workaround can be found[COLOR=Blue] _[SIZE=3][here]("http://ubuntuforums.org/showpost.php?p=6449370&postcount=989")[/SIZE]_[/COLOR] or [SIZE=3][COLOR=Blue][here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7")[/COLOR][/SIZE]):
```
# Workaround for MAudio Audiophile
# Added comment rod40cool - (STA Audio Media 7.1 card uses same ICE1712 driver)
# Added comment rod40cool - Run command "asoundconf list" to determine what to add after "device=hw:????"
# Added comment rod40cool - Make sure after pasting that there are only 2 lines below starting each with "load-module module..." 
load-module module-alsa-sink sink_name=M2496_out device=hw:M2496 format=s32le channels=10 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
load-module module-alsa-source source_name=M2496_in device=hw:M2496 format=s32le channels=12 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
```Save the file, log out and log in back.

Now you should have your pulseaudio and M-Audio 2496 working fine and be able to switch input and output audio streams over your audio devices.

There is however no sound after you resume from hibernate or suspend. Actually you can see the whole application that you try to play audio/video in is going slow, video picture jumps quickly or there is something similar happening. This is - from what I read - due to the linux driver. Driver lacks the support for resume on this sound card basically. 
The only way I found to get around this is to reload the driver module for this card after you resume your system. Then restart the pulseaudio and set mixer levels up (not the main volume). Because of the module reload the applications that were using the audio have to be restarted after the resume. That's quite annoying. Luckily in Firefox the complete restart is not necessary. If you had youtube opened just reopen the tab again. For example Skype also doesn't need the restart and can survive driver reload and pulseaudio restart.

**Follow these steps to bring the sound back on resume from hibernate/suspend:**

In order to be able to reload the driver module all the processes that are currently using any audio devices must be killed:
```
$ sudo fuser -s -k /dev/snd/*
```Shut down and start again the maudio soundcard module:
```
$ sudo rmmod snd_ice1712
$ sudo modprobe snd_ice1712
```Kill the pulseaudio:
```
$ sudo killall pulseaudio
```Start the pulse audio deamon back again:
```
$ sudo pulseaudio -D
```Because the pulseaudio restart cause the volume drop on DAC and ADC it is necessary to set these mixer levels up again (main volume is not affected which is good):
```
$ amixer -q -c 0 set 'DAC',0 100%
$ amixer -q -c 0 set 'DAC',1 100%
```Please make sure the argument in two commands above after the '-c' option is the number of maudio sound card. In my case it is 0. If you are unsure what number your card has then do:
```
asoundconf list
```and you will get the list of your audio devices. They are indexed from the top starting from zero. So if you see the **M2496** on the top the argument after the '-c' should be 0.

Ok that's it. Don't forget to restart the applications that were using the audio before. You should have your sound working fine now again.

Almost done. Now you don't want to run all those commands every time you resume the system, do you? Neither do I. So, I have written the resume script to do it for you crazy kids. There is however an issue with this. In order to get pulseaudio daemon in the resume script back it has to be started in **'system mode' **otherwise startup fails because the user is not logged in yet basically. You can google for 'pulseaudio system mode' if you want to know more and what does it mean for you. Please note the script must have resume-hook format so don't change its structure when you edit it. Also I found annoying that my other sound devices (motherboard sound card and web cam mic) sometimes don't show up in the pulseaudio volume control after it is killed and started again and the sound card number is sometimes not 0. Because of this I shut down and start up my other audio devices modules as well. Actually in my case it's one more module named 'snd_usb_audio'. To find your own modules use command '**lsmod**'.

This is the final script I use:
```
#!/bin/bash

. /usr/lib/pm-utils/functions

resume_maudio() {
    sudo fuser -s -k /dev/snd/*
    sudo rmmod snd_ice1712
    sudo modprobe snd_ice1712
    sudo rmmod snd_usb_audio
    sudo modprobe snd_usb_audio
    sudo killall pulseaudio
    sudo pulseaudio --system -D
    amixer -q -c 0 set 'DAC',0 100%
    amixer -q -c 0 set 'DAC',1 100%
}

case "$1" in
    hibernate|suspend)        
        ;;
    thaw|resume)
        resume_maudio
        ;;
    *)
        ;;
esac

exit $?

```To use my script in your system start the text editor as root:
```
$ sudo gedit 01maudio_resume
```I named the script '01maudio_resume' purposely. The prefix '01' will cause the script to be executed at the end of the resume process.

Select, copy and paste the text from the script above into your editor window. Then do file -> save as. Navigate to the **/etc/pm/sleep.d/** and save the file in that folder. Normally the folder will be empty before.

Make the script executable:
```
$ sudo chmod +x /etc/pm/sleep.d/01maudio_resume
```Because the pulseaudio is using separate configuration file '**system.pa**' for running in system mode we'll create the copy of the 'default.pa' and name it 'system.pa':
```
$ sudo cp /etc/pulse/default.pa /etc/pulse/system.pa
```That's all crazy kids. Next time you resume play your music loud! ;)

---

### Post by pierocol on 2009-11-28
Thank you for your guide. Let me start by saying I am a novice. I just installed ubuntu karmic on a PC I just bought. I have an audiophile 2496 and sound does not work on resume from suspend. When I suspend I hear a crackling noise from my speakers. I followed your instructions from "Follow these steps to bring the sound back on resume from hibernate/suspend:"
Pulseaudio is already installed and it is version 1:0.0.19.
I tried first to execute the commands of your script one by one.
The command "pulseaudio -D" generates "E: main.c: Daemon startup failed."
I would really appreciate your help!

---

