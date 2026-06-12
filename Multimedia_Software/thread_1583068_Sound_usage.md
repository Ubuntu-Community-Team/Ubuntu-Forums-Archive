---
title: "Sound usage"
date: 2010-09-27
forum: Multimedia Software
---

### Post by Colo2 on 2010-09-27
Hello

I have ubuntu studio installed downstairs, and this puzzled me. It's a problem I've had before on Ubuntu.

We have 2 x Delta 1010s and I've managed to get the sound working. There is no pulseaudio > removed.

The "Jack" application fails to start if the sound is in use. It seems. Jack won't start if I'm listening to an MP3, Audour won't start when I'm listening to an MP3 because it wants to launch jack. 

If Jack is running, the MP3 will not output any sound.

Can only one application use sound at the same time? If so, this is no good for a recording studio :P

Any solutions would be greatly appreciated

thanks ;)

Tom.

---

### Post by cchhrriiss121212 on 2010-09-27
Hi Tom,
Welcome to the ungainly world of Linux audio. 
Jack is not an application per se, it is a sound server. Pulse is also a sound server, and it is running all the time. Jack is for audio work (Ardour etc.), and pulse is for regular usage (mp3 playback, firefox etc.). Both servers work with or on top of ALSA.
When you start up jack, pulse must be suspended as it is a good idea to have only one sound server running at a time. Trying to start jack when you are using pulse is like trying to switch shoes while you are still running.

To answer your other question, you can run as many programs or sounds as you like at the same time if you are using jack (pulse cannot handle it AFAIK). 
But the programs you use must be designed to run on the correct sound server, for example Rhythmbox does not work with jack and Ardour does not work with Pulse.
So if you want to listen to an mp3 while running Ardour, you will need a program that works with jack. Alsaplayer is what I use for this.

If you'd like to know more about how sound in Ubuntu works, or what jack does then let me know. I found it to be very confusing and needlessly complex when I started, but now I have things set up I have a very stable and flexible system.

---

### Post by Colo2 on 2010-09-27
Hello. Thank you for your reply.

I think I understand. So correct me if I'm wrong?

PulseAudio is a sound server which they shove on ubuntu to make every day audio tasks possible

Jack is also a sound server which is more professional and capable of more complex audio tasks. 

And alsa is...? The base system that runs the audio server?

The computer in question has no internet access, so all apps I want to install there, I need to take over on a USB key. I'll download alsaplayer .deb file, and install that. I'll see if it gives me any joy.

I also noticed that when Jack is running, system sound's don't work.

Any solution for that?

Thanks

---

### Post by Colo2 on 2010-09-27
Can someone give me a solution, because I can't think of one.

So Ubuntu Studio is shipped with half of it's apps running on PulseAudio, and the other half wanting Jack sound server? And both sound servers refuse to run together?

Is there any way to scrap the both and just use alsa?

And another thing. I was pretty sure I uninstalled PulseAudio. It's gone! So what the hell is going on here? :|

I really don't want to take this system back to Windows, but I can see this being a massive problem

Thanks

Tom

---

### Post by Colo2 on 2010-09-27
bumpo

---

### Post by cchhrriiss121212 on 2010-09-27
> I think I understand. So correct me if I'm wrong?

PulseAudio is a sound server which they shove on ubuntu to make every day audio tasks possible

Jack is also a sound server which is more professional and capable of more complex audio tasks. 

And alsa is...? The base system that runs the audio server?
Correct. The audio chain looks like this:
Soundcard > ALSA > Pulse/Jack > Software

> The computer in question has no internet access, so all apps I want to  install there, I need to take over on a USB key. I'll download  alsaplayer .deb file, and install that. I'll see if it gives me any joy.

You may get dependency errors doing that, as the alsaplayer package may rely on other packages to run. It would be easier if you could hook it up temporarily.
> I also noticed that when Jack is running, system sound's don't work.

Any solution for that?
No, system sounds will not go through jack. I don't think people want to hear system sounds when they are recording or producing music.

> 
So Ubuntu Studio is shipped with half of it's apps running on  PulseAudio, and the other half wanting Jack sound server? And both sound  servers refuse to run together?
Yes and no. You can get both to run at the same time, but it is complicated and not worth it IMO.
> 
Is there any way to scrap the both and just use alsa?
Yes, this is what I do on my machine. But if you want to record things with Ardour for example you will need jack. Pulse is disposable, jack is a useful tool.
> 
And another thing. I was pretty sure I uninstalled PulseAudio. It's gone! So what the hell is going on here? :neutral:
I can't really say what is going on, as I have no way of knowing what you have done unless you explain the steps you took. Did you follow a guide somewhere?

> I really don't want to take this system back to Windows, but I can see this being a massive problem

Most users feel that way when they encounter their first bug or undesirable part of Ubuntu, I certainly did. The best part of Linux is that you have the freedom to change whatever you don't like to suit your own needs.
The advice I would give to you would be to try Ubuntu out slowly so you are not overwhelmed with the new way of doing things. You need to be prepared to learn a new way of using your computer, and if it is getting irritable. then take a break from it, post on the forums about what issues you have and fix one problem at a time. It may take you 2 months to learn how to use jack and other apps, but it will be worth it if you have a completely free system that you can use for the next 10+ years.

---

### Post by Colo2 on 2010-09-27
Hey
Thank you for your reply :)

I will completely explain my situation to you.

After ubuntu studio was installed, I installed the drivers for my 2 Delta 1010s - no sound on system. A bit of research told me that PulseAudio conflicts with the deltas

So:

> sudo apt-get remove pulseaudio
I disabled it from the startup list like someone suggested, installed "esound" or something? and restarted

BINGO. Sound worked. However, ever since then, I am having a general problem ^ as you know. 

According to [this post](http://ubuntuforums.org/showpost.php?p=9685433&postcount=8) I shouldn't have uninstalled pulse like that. So I may well have screwed everything up.

Apparently, according to this guy:
> **chaanakya_chiraag said:**
> If you install the Jack modules for pulseaudio, you can have pulse play through Jack by using ```
pactl load-module module-jack-source
pactl load-module module-jack-sink
``` and going into pavucontrol (install it if you don't have it) and setting the Jack sink and source as defaults.


I guess that's what I need to do? However I've removed PulseAudio, so I'm guessing the modules won't work anymore?

Should I re-install ubuntu studio?

Thanks :)

---

### Post by Yellow Pasque on 2010-09-27
> Jack won't start if I'm listening to an MP3, Audour won't start when I'm listening to an MP3 because it wants to launch jack
ALSA has a hardware driver component and is also an API that apps can use.
Jack wants access to the sound device, and it can't get that if you're using it without mixing. You can set up ALSA to use its software mixer (dmix), but it's not good with latency and doesn't use the highest quality resampling algorithms. Pulseaudio solves the mixing problem and has better audio quality available, but it has its own set of drawbacks (doesn't run with your hardware as you've discovered).

I think the best solution for you is to route all audio through jack. Make sure you have the libasound2-plugins package installed and use this /etc/asound.conf to route the output of all of your apps through jack:
```
pcm.jackplug {
    type plug
    slave { pcm "jack" }
}

pcm.jack {
    type jack
    playback_ports {
        0 alsa_pcm:playback_1
        1 alsa_pcm:playback_2
    }
    capture_ports {
        0 alsa_pcm:capture_1
        1 alsa_pcm:capture_2
    }
}
```
Reference: [http://www.articleworld.org/index.php?title=How_to_force_ALSA_applications_to_use_JACK&printable=yes](http://www.articleworld.org/index.php?title=How_to_force_ALSA_applications_to_use_JACK&printable=yes)

Oh, and if you can't get your ALSA setup working properly, please try OSS4 before going back to Windows: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Colo2 on 2010-09-27
> **Temüjin said:**
> ALSA has a hardware driver component and is also an API that apps can use.
Jack wants access to the sound device, and it can't get that if you're using it without mixing. You can set up ALSA to use its software mixer (dmix), but it's not good with latency and doesn't use the highest quality resampling algorithms. Pulseaudio solves the mixing problem and has better audio quality available, but it has its own set of drawbacks (doesn't run with your hardware as you've discovered).

I think the best solution for you is to route all audio through jack. Make sure you have the libasound2-plugins package installed and use this /etc/asound.conf to route the output of all of your apps through jack:
```
pcm.jackplug {
    type plug
    slave { pcm "jack" }
}

pcm.jack {
    type jack
    playback_ports {
        0 alsa_pcm:playback_1
        1 alsa_pcm:playback_2
    }
    capture_ports {
        0 alsa_pcm:capture_1
        1 alsa_pcm:capture_2
    }
}
```
Reference: [http://www.articleworld.org/index.php?title=How_to_force_ALSA_applications_to_use_JACK&printable=yes](http://www.articleworld.org/index.php?title=How_to_force_ALSA_applications_to_use_JACK&printable=yes)

Oh, and if you can't get your ALSA setup working properly, please try OSS4 before going back to Windows: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)


Hello. I tried this.

I made sure that the module was installed - it is.
I created the asound.conf file - It went in without replacing anything because the file didn't exist in /etc/.

No difference. Everything is still coming through Pulse.

:(

---

### Post by Yellow Pasque on 2010-09-27
But you removed pulseaudio.. so you need to configure your apps to use either ALSA or JACK. Note that you also need to restart the system (or restart ALSA) before the conf file takes effect.

---

### Post by Colo2 on 2010-09-27
> **Temüjin said:**
> But you removed pulseaudio.. so you need to configure your apps to use either ALSA or JACK. Note that you also need to restart the system (or restart ALSA) before the conf file takes effect.

I did restart.

If I re-installed Ubuntu Studio, (hence restoring pulse to it's original state), would the above suggestion with the asound.conf work?

---

### Post by cchhrriiss121212 on 2010-09-27
> **Colo2 said:**
> Hey
Thank you for your reply :)

I will completely explain my situation to you.

*snip*

I guess that's what I need to do? However I've removed PulseAudio, so I'm guessing the modules won't work anymore?

Should I re-install ubuntu studio?

Thanks :)
Can't say I've ever used esound, so I could only offer you help with a fresh install, it's up to you. I would say that ALSA+Jack can do everything you want with your card even though it means you will have to remove or disable pulse.

Here are the steps I take when using my Delta card on a fresh install:
Check that it is recognised with aplay -l in a terminal
Set the sound levels using analogue volume tab of envy24control, they are always muted by default
Remove pulse using synaptic (as you heard seen this is risky, but has not caused me any issues so far)
reboot
Set up jack

---

### Post by cbilljones on 2010-09-27
Im thinking maybe oss4 is the way to go; it also takes a bit of setting up, but i used it for a long time till i was comfortable with pulse. Good wright up here if you want to try it:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Colo2 on 2010-09-27
Hey

Thanks for the reply

Ok, I'll see if my dad is ok with me doing a fresh Install.

Once the install is complete, I'll do as you said above.

One thing which puzzles me. In envy24control, they all say mute, but the audio works fine

Is this normal?

and P.S, did you get your drivers from [http://opensound.com/](http://opensound.com/) ?

thanks

---

### Post by cbilljones on 2010-09-27
> **Colo2 said:**
> Hey

Thanks for the reply

Ok, I'll see if my dad is ok with me doing a fresh Install.

Once the install is complete, I'll do as you said above.

One thing which puzzles me. In envy24control, they all say mute, but the audio works fine

Is this normal?

and P.S, did you get your drivers from [http://opensound.com/](http://opensound.com/) ?

thanks

yes you get the deb file from [http://opensound.com/](http://opensound.com/)  you could prob follow that guide without reinstalling; it will blacklist alsa and purge pulse. OSS4 and Jack will work together if you need that.

---

### Post by Colo2 on 2010-09-27
thanks for helping guys :)

Re-installing as we speak. 

I'll post back the results :)

Thanks

---

### Post by Colo2 on 2010-09-27
Hello again

I followed the following tutorial
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

And my system isn't detecting my soundcards :(

Ardour gives an NO DEVICE FOUND FOR OSS error when starting

A DVD seems to be playing ok, but I don't know if the sound is working as I don't have the breakout boxes or speakers here.

**The PC isn't connected to it's breakout boxes.**
Could this be why it's not detecting the cards?

if not, what have I done wrong?

Thanks

---

### Post by Colo2 on 2010-09-27
> APLAY -L
> aplay: device_list:223: no soundcards found....

---

### Post by Yellow Pasque on 2010-09-27
```
ossinfo
```
.

---

### Post by cbilljones on 2010-09-27
run "ossxmix" for mixer
run "gstreamer-properties" and set do OSS, do a test
your kinda going to need speakers or headphones to know if you have sound:rolleyes:

Some apps you will have to set to OSS, VLC for instance; there is no one fix for all

aplay is an alsa command, if you followed the tutorial you blacklisted alsa.

---

### Post by Colo2 on 2010-09-27
> ossinfo
No /dev/mixer device available in your system
Perhaps open sound system isn't installed or running

> ossmixer
ossmixer: command not found

> test, in gstreamer-properties
OSS - Open Sound System: Could not open audio device for playback

:|

---

### Post by cbilljones on 2010-09-27
Sounds like OSS4 is not installed, did you download and install the .deb file?

---

### Post by Colo2 on 2010-09-27
> **cbilljones said:**
> Sounds like OSS4 is not installed, did you download and install the .deb file?


yes

---

### Post by Colo2 on 2010-09-27
Status: Same version is already installed - Reinstall Package

---

### Post by cbilljones on 2010-09-27
> **Colo2 said:**
> yes

Did you install from the terminal with "sudo dpkg -i oss-linux*.deb"?

If so, could you uninstall with synaptic and try again, and post the output here?

As soon as installation is done you should have sound

---

### Post by Colo2 on 2010-09-27
> **cbilljones said:**
> Did you install from the terminal with "sudo dpkg -i oss-linux*.deb"?

If so, could you uninstall with synaptic and try again, and post the output here?

Nah, I used GDebi

---

### Post by cbilljones on 2010-09-27
> **Colo2 said:**
> Nah, I used GDebi
Uninstall it and follow the tutorial.

post the output of "sudo dpkg -i oss-linux*.deb"

Also, did you do everything the tutorial said?

---

### Post by Colo2 on 2010-09-27
At a glance, it looks normal, but now that I look closer into the terminal window, I notice this:

Failed to compile OSS
make -C /lib/modules/............
make: *** /lib/modules/........./build: No such file or directory. Stop.
make: *** [default] Error 2

Relinking the OSS kernel modules failed

---

### Post by cbilljones on 2010-09-27
> **Colo2 said:**
> At a glance, it looks normal, but now that I look closer into the terminal window, I notice this:

Failed to compile OSS
make -C /lib/modules/............
make: *** /lib/modules/........./build: No such file or directory. Stop.
make: *** [default] Error 2

Relinking the OSS kernel modules failed

Failed to compile is normal:confused: Did you do every single other thing the wiki said?
did you run "sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio"
did you run "sudo /etc/init.d/alsa-utils stop
sudo apt-get remove alsa-base alsa-utils"
did you run "sudo dpkg-reconfigure linux-sound-base" and select oss?
Did you reboot before installing OSS4?

If the answer is no, im going to suggest reinstall ubuntu then follow the wiki to the letter.

---

### Post by Colo2 on 2010-09-27
Ubuntu Studio takes about 2 hours to install. I can't re-install.

Forgetting to reboot before installing OSS4 couldn't have caused this surely... :|

---

### Post by cbilljones on 2010-09-27
> **Colo2 said:**
> Ubuntu Studio takes about 2 hours to install. I can't re-install.

Forgetting to reboot before installing OSS4 couldn't have caused this surely... :|

What other steps did you ignore? People write excellent detailed tutorials for a reason.

You said "I followed the following tutorial
https://help.ubuntu.com/community/OpenSound"

It seems that was not at all the case, its tough to help you when i have to guess at what you have done.

---

### Post by Colo2 on 2010-09-27
I didn't ignore them. I followed it carefully.

> Configure ALSA Apps to Use OSS (OPTIONAL)
In general, it's better to have applications use the OSS API or a higher level sound API/library with OSS4, but if you have the libasound2-plugins package (it's pre-installed on standard Ubuntu installs), it is possible to have ALSA applications output to OSS with this workaround (the first method).

Didn't do that

> sudo apt-get install -y gstreamer0.10-plugins-bad

Didn't do that

the rest I did...

---

### Post by Colo2 on 2010-09-27
> But if you receive an ugly error message on sudo dpkg -i oss*.deb, try

NO_WARNING_CHECKS=yes /opt/oss-devel/configure --enable-libsalsa=NO
make
sudo make install

that's interesting. But it's only something to try if you're building from source :(

---

### Post by cbilljones on 2010-09-27
> **Colo2 said:**
> I didn't ignore them. I followed it carefully.



Didn't do that



Didn't do that

the rest I did...
Uninstall OSS4, review the wiki and start at the top, read very carefully; after rebooting install from the terminal, post the **entire** output here.

---

### Post by Colo2 on 2010-09-27
Call me stupid if you like, but I can't work out how to uninstall it.

---

### Post by cbilljones on 2010-09-27
> **Colo2 said:**
> Call me stupid if you like, but I can't work out how to uninstall it.

Use synaptic package manager

You don't need to do anything that says optional, you **need** to do everything else; no shortcuts.

---

### Post by Colo2 on 2010-09-27
Going back over the tutorial, there's nothing else I can do but uninstall it, and re-install it. All the other steps include removing files, blacklisting etc... It's already been done.

Same error anyway.

---

### Post by cbilljones on 2010-09-27
> **Colo2 said:**
> Going back over the tutorial, there's nothing else I can do but uninstall it, and re-install it. All the other steps include removing files, blacklisting etc... It's already been done.

Same error anyway.

Run every command anyway
then reboot
Then install from terminal
Then post the entire output here

What do you mean same error anyway? This is your first attempt, i know because you needed to ask how to remove it.Ill await your post with the output of "sudo dpkg -i oss-linux*.deb"

---

### Post by Colo2 on 2010-09-27
> cpigshed@studio:~$ cd /home/pigshed/Desktop
pigshed@studio:~/Desktop$ sudo dpkg -i oss-linux-4.2-2003_i386.deb
[sudo] password for pigshed: 
Selecting previously deselected package oss-linux.
(Reading database ... 181514 files and directories currently installed.)
Unpacking oss-linux (from oss-linux-4.2-2003_i386.deb) ...
Setting up oss-linux (4.2-2003) ...
Building OSS Modules for Linux-unknown 2.6.32-21-generic

OSS build environment set up for REGPARM kernels


Warning: Cannot locate the Linux kernel development package for
         Linux kernel version  2.6.32-21-generic
         Please install the kernel development package if linking the
         OSS modules fails.

The kernel development package may be called kernel-devel, kernel-smp-devel,
kernel-sources, kernel-headers or something like that. Please refer
to the documentation of your Linux distribution if there are any
difficulties in installing the kernel/driver development environment.

For your Linux distribution the right kernel source package
might be kernel-source.

Under Ubuntu you may need to prepare the kernel environment
after downloading the kernel sources using

  sudo apt-get install linux-headers-2.6.32-21-generic
  cd /usr/src/linux-headers-2.6.32-21-generic/

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/oss/build modules
make: *** /lib/modules/2.6.32-21-generic/build: No such file or directory. Stop.
make: *** [default] Error 2
Forcing re-detection of installed soundcards
Starting Open Sound System
Relinking OSS kernel modules for "2.6.32-21-generic SMP mod_unload modversions 586 "
This may take few moments - please stand by...

OSS build environment set up for REGPARM kernels


Warning: Cannot locate the Linux kernel development package for
         Linux kernel version  2.6.32-21-generic
         Please install the kernel development package if linking the
         OSS modules fails.

The kernel development package may be called kernel-devel, kernel-smp-devel,
kernel-sources, kernel-headers or something like that. Please refer
to the documentation of your Linux distribution if there are any
difficulties in installing the kernel/driver development environment.

For your Linux distribution the right kernel source package
might be kernel-source.

Under Ubuntu you may need to prepare the kernel environment
after downloading the kernel sources using

  sudo apt-get install linux-headers-2.6.32-21-generic
  cd /usr/src/linux-headers-2.6.32-21-generic/

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/oss/build modules
make: *** /lib/modules/2.6.32-21-generic/build: No such file or directory. Stop.
make: *** [default] Error 2

Relinking the OSS kernel modules failed

Processing triggers for man-db ...
pigshed@studio:~/Desktop$ 


I meant, I tried installing it again, without removing it

---

### Post by cbilljones on 2010-09-27
It says to try and installing the kernal headers, open synaptic package manager and search for appropriate headers:

"The kernel development package may be called kernel-devel, kernel-smp-devel,
kernel-sources, kernel-headers or something like that. "

So look for the headers for the kernel your running and try again.

Try searching for "linux-headers" you will need the headers for the kernel your running

"uname -r" will tell you what kernel

---

### Post by Colo2 on 2010-09-27
installed the right headers, and restarted. It's booting now.

---

### Post by Colo2 on 2010-09-27
same problem

---

### Post by Colo2 on 2010-09-27
I'd better get to bed. It's late. I'll review it tomorrow, with a fresh mind :P

thank you for your help, and sleep well!

---

### Post by cbilljones on 2010-09-27
this seems to be a tough one, maybe try ti install from source, instructions are on the wiki, have a good sleep

---

