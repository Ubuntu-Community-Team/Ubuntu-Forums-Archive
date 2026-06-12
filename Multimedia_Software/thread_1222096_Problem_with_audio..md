---
title: "Problem with audio."
date: 2009-07-24
forum: Multimedia Software
---

### Post by riisimaria on 2009-07-24
Hello I have just switched from Windows XP to ubuntu. Everything works fine except playing music. I can play music using rhythmbox but it doesn't play 'smoothly'; it is choppy.This remains the case when I use other players and internet radio.

I have tried several things, like: playing around with audio settings, trying to install an audio driver from Realtek (although not sure did i succeed since this whole ubuntu is totally new to me..).

I have a Fujitsu Siemens Amilo A1650G with a ATI IXP card with a Realtek ALC655 rev 0 chip...

I would really appreciate any help. I seem to be hopeless with these things!

---

### Post by jerrrys on 2009-07-24
did you install Ubuntu Restricted Extras, located in Synaptic Package Manager?

System>Administration>Synaptic

---

### Post by riisimaria on 2009-07-25
i gave that a go and the music is still choppy :( any other ideas???

---

### Post by martinbaselier on 2009-07-25
what soundcard do you have? 

open a terminal and paste this command to it. (right mouse button, paste)
**lspci | grep Audio -i**

Just paste the output here
keep the terminal open and run
**top**
This will show you the cpu usage (and a lot more)
what happens when you play music, is there a high raise in cpu usage?
If so which process causes it?

---

### Post by riisimaria on 2009-07-26
This is the souncard i have: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)

And here's a snapshot when put top into the terminal..

top - 11:03:39 up 20 min,  2 users,  load average: 0.98, 1.01, 0.82
Tasks: 121 total,   2 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s): 34.3%us,  7.9%sy,  0.0%ni, 57.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    378708k total,   359084k used,    19624k free,     8396k buffers
Swap:  1108444k total,    38252k used,  1070192k free,   105228k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3185 kristina  20   0  156m 3524 2692 S 10.3  0.9   1:03.60 pulseaudio         
 3428 kristina  20   0  252m  81m  19m S 10.3 22.0   3:44.93 firefox            
 4125 kristina  20   0  195m  36m  20m S  9.6 10.0   0:07.26 rhythmbox          
 3762 kristina  20   0 33864  14m 9548 S  7.0  3.8   0:07.35 gnome-terminal     
 2595 root      20   0  404m  28m  10m R  3.6  7.7   1:07.90 Xorg               
 3288 kristina  20   0 27376  12m 4284 S  0.3  3.3   0:12.27 compiz.real        
 4123 kristina  20   0  2448 1180  912 R  0.3  0.3   0:00.89 top                
    1 root      20   0  1904  536  484 S  0.0  0.1   0:02.06 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0   

Thanks for helping me :)

---

### Post by martinbaselier on 2009-07-26
I had hoped you did it the other way around, paste the soundcard data and summarize the output of top. The top snapshot is kind of hard to read. I had to copy it to a text editor and then into open office, to read it easily. Anyway it shows no cpu overload. 

I am curious to the ouput of:
**sudo lspci -v -s cardnumber**
cardnumber is the first number you seen on lspci. 

If you try:
**sudo killall -KILL pulseaudio**
And then try to play sound, how's the sound quality then?

---

### Post by igorzwx on 2009-07-26
Martin!

Just info.
If you kill pulse, and start Audacity,
pulse is restarted.
You kill pulse once more.
Start playback in Audacity, and pulse is running again.
You should always check which processes are running.
Pulse is a very tricky thing,
it behaves like a trojan.

---

### Post by khelben1979 on 2009-07-26
> **riisimaria said:**
> I have a Fujitsu Siemens Amilo A1650G with a ATI IXP card with a Realtek ALC655 rev 0 chip...

Is it like [this]("http://www.blocket.se/jonkoping/35st_beg_Fujitsu_Amilo_A1650_AMD_3200__22463145.htm") laptop when it comes to the hardware specifications?

---

### Post by riisimaria on 2009-07-26
Heh sorry bout that..

With the cardnumber i got:
kristina@kristina-laptop:~$ sudo lspci -v -s cardnumber
lspci: -s: Invalid slot number

With killing pulseaudio i got this:
 kristina@kristina-laptop:~$ sudo killall -KILL pulseaudio
pulseaudio: no process killed

Those are not the expected responses are they??

And yes my laptop hardware is similar to that one..

So what should i do now??

---

### Post by martinbaselier on 2009-07-26
You need to replace cardnumber with your cardnumber.

Example:
```

tin@lappy:~$ lspci | grep Audio -i
**00:1b.0** Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
tin@lappy:~$ sudo lspci -s **00:1b.0** -v
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint,MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: oss_hdaudio

```

about pulse: 
Top shows pulseaudio is running.

does **ps -e | grep pulse** show anything?

**pulseaudio --kill**
would be the correct way to do it. 
But you must make sure there is no application that's using sound through pulse, otherwise it resurrects. 

I wonder if you still have the problem, when not using pulse.

---

### Post by riisimaria on 2009-07-26
ok that makes sense..u see im hopeless with this stuff! but hey im learning :)

so this is what i got with the cardnumber:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Fujitsu Siemens Computers Device 1092
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp


**ps -e | grep pulse, **doesn't show anything..

and umm with audiopulse got this.. 

kristina@kristina-laptop:~$ pulseaudio --kill
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: main.c: Failed to kill daemon: No such file or directory

---

### Post by igorzwx on 2009-07-26
Fantastic!

Make this:

System -> preferences -> Startup Aplications

disable PolicyKit

reboot

sudo killall pulseaudio

---

### Post by riisimaria on 2009-07-26
umm i can't find PolicyKit from the startup applications..

---

### Post by igorzwx on 2009-07-26
It is OK.
It is there in Ubuntu 9.10 Alpha 3.
Sorry.

simply this:

sudo killall pulseaudio

this should be enough

---

### Post by martinbaselier on 2009-07-26
So pulse is not running. It's definitely not the cause of the problem then. It's probably the sound driver. There are more reports of this problem. 

In a terminal run:
**sudo gedit /etc/modprobe.d/ac97.conf**
and past the following into it. 

options snd-atiixp ac97_quirk=alc_jack
options snd-atiixp ac97_codec=0


@ Igor:

Your comment is not helpful: We already established pulse was not running, so it's absolute useless to suggest it.

---

### Post by riisimaria on 2009-07-26
ok pasted it into gedit..now what? do i need to save it or something?

---

### Post by martinbaselier on 2009-07-26
Yes, save (I forgot to say that) and then reboot.

---

### Post by igorzwx on 2009-07-26
Hi!

Martin seems to be busy now.

I may try to explain.

Fist of all, you should be sure that PulseAudio is not
among running processes.

To see processes
System -> Administration -> System Monitor -> Processes

To kill PulseAudio
you should execute this command:

sudo killall pulseaudio

Then you can edit that file with text editor (gedit = Gnome Text Editor)

---

### Post by khelben1979 on 2009-07-27
I found [this]("http://forums.linuxmint.com/viewtopic.php?f=49&t=19217") from Linux Mint.

gnome-volume-control
switches
uncheck the check box

Try the above.

---

### Post by riisimaria on 2009-07-27
ok guys i did all that and still nothing :(

saved gedit and rebooted..

Pulseaudio isn't among running processes and the command sudo killall pulseaudio doesn't do anything..

and there is no box to be unchecked in the volume control, have already tried the tips for volume control and none of them work...

so next step?

---

### Post by khelben1979 on 2009-07-27
You can post how your sound settings looks like with alsamixergui.

```
sudo apt-get install alsamixergui
```
if it's not already installed.

What happens if you play an mp3 file with for example mpg123 in non graphical mode? (I'm a bit curious about to see if there is something messed up with your graphical enviroment which creates problems, perhaps slow graphics drivers which slows everything down? Who knows what it could be..)

```
sudo apt-get install mpg123
```
to install this one too.

```

ctrl + alt + f1
```
to enter the first text console and

```
ctrl + alt + f7
```
to go back to the x-server.

---

### Post by riisimaria on 2009-07-27
umm i got this..

kristina@kristina-laptop:~$ sudo apt-get install alsamixergui
[sudo] password for kristina: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by khelben1979 on 2009-07-27
> **riisimaria said:**
> umm i got this..

kristina@kristina-laptop:~$ sudo apt-get install alsamixergui
[sudo] password for kristina: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

There are 2 ways to solve this:

1. reboot the computer (the easy way)

2. Locate the application which is up and running and close it down. It might be that you have [the Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") up and running.

---

### Post by riisimaria on 2009-07-27
ok rebooting helped :)

i installed the alsamixergui and it only showed volume..

and installed mpg123 with the code but after that im lost... when i tried ctrl+alt+F1 it caused my comp to crash...

---

### Post by khelben1979 on 2009-07-27
> **riisimaria said:**
> ok rebooting helped :)

i installed the alsamixergui and it only showed volume..

and installed mpg123 with the code but after that im lost... when i tried ctrl+alt+F1 it caused my comp to crash...

Okay, that sounds really bad. I have never experienced a Linux distribution where I'm unable to go to a text console. But no matter, the most important thing here is that you have a working system I guess.

To use mpg123 you then need a text shell such as [xterm]("http://en.wikipedia.org/wiki/Xterm") or some other text shell application which you can have running on the desktop.

The alsamixergui application is only a program to adjust your volume meters, that's right.

---

### Post by martinbaselier on 2009-07-27
Could you post the output of?
lsmod | grep snd

---

### Post by riisimaria on 2009-07-27
kristina@kristina-laptop:~$ lsmod | grep snd
snd_atiixp             24204  4 
snd_seq_dummy          10756  0 
snd_atiixp_modem       20360  0 
snd_seq_oss            37760  0 
snd_ac97_codec        112292  2 snd_atiixp,snd_atiixp_modem
snd_seq_midi           14336  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_pcm                82948  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29704  2 snd_pcm,snd_seq
snd                    62628  18 snd_atiixp,snd_atiixp_modem,snd_seq_oss,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              15200  1 snd
snd_page_alloc         16904  3 snd_atiixp,snd_atiixp_modem,snd_pcm


Do you think changing to a different Linux distribution would help?

---

### Post by khelben1979 on 2009-07-27
What version of Ubuntu are you using?

---

### Post by riisimaria on 2009-07-27
im using the newest ubuntu jaunty jack 9.04

---

### Post by martinbaselier on 2009-07-27
The problem probably is:
snd_atiixp_modem

**sudo modprobe -r snd_atiixp_modem**
will disable it temporarily (until reboot

It's normally blacklisted. It is on my machine. 

Does that help?

---

### Post by riisimaria on 2009-07-27
not sure does that command work cause nothing happened...

---

### Post by martinbaselier on 2009-07-27
It won't output anything. It just removes the module from the running kernel. 

If you do the lsmod command again, you will see the module is removed. 

About switching distribution : It's a problem with the driver (that is the kernel module) for this card. So using a different distribution will probably not make much difference, unless they use a different kernel. 

Since this module has been in the kernel for a long time, I doubt there have been many recent changes to it.

---

### Post by martinbaselier on 2009-07-27
I found the suggested solution here:

[http://ubuntuforums.org/showthread.php?t=1075893](http://ubuntuforums.org/showthread.php?t=1075893)

Here is a link with more info about driver settings:
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

relevant parts:
> 1948	AC97 Quirk Option
1949	=================
1950	
1951	The ac97_quirk option is used to enable/override the workaround for
1952	specific devices on drivers for on-board AC'97 controllers like
1953	snd-intel8x0.  Some hardware have swapped output pins between Master
1954	and Headphone, or Surround (thanks to confusion of AC'97
1955	specifications from version to version :-)
1956	
1957	The driver provides the auto-detection of known problematic devices,
1958	but some might be unknown or wrongly detected.  In such a case, pass
1959	the proper value with this option.
1960	
1961	The following strings are accepted:
1962	    - default	Don't override the default setting
1963	    - none	Disable the quirk
1964	    - hp_only	Bind Master and Headphone controls as a single control
1965	    - swap_hp	Swap headphone and master controls
1966	    - swap_surround  Swap master and surround controls
1967	    - ad_sharing  For AD1985, turn on OMS bit and use headphone
1968	    - alc_jack	For ALC65x, turn on the jack sense mode
1969	    - inv_eapd	Inverted EAPD implementation
1970	    - mute_led	Bind EAPD bit for turning on/off mute LED
1971	
1972	For backward compatibility, the corresponding integer value -1, 0,
1973	... are  accepted, too.
1974	
1975	For example, if "Master" volume control has no effect on your device
1976	but only "Headphone" does, pass ac97_quirk=hp_only module option.

> 
1948	AC97 Quirk Option
1949	=================
1950	
1951	The ac97_quirk option is used to enable/override the workaround for
1952	specific devices on drivers for on-board AC'97 controllers like
1953	snd-intel8x0.  Some hardware have swapped output pins between Master
1954	and Headphone, or Surround (thanks to confusion of AC'97
1955	specifications from version to version :-)
1956	
1957	The driver provides the auto-detection of known problematic devices,
1958	but some might be unknown or wrongly detected.  In such a case, pass
1959	the proper value with this option.
1960	
1961	The following strings are accepted:
1962	    - default	Don't override the default setting
1963	    - none	Disable the quirk
1964	    - hp_only	Bind Master and Headphone controls as a single control
1965	    - swap_hp	Swap headphone and master controls
1966	    - swap_surround  Swap master and surround controls
1967	    - ad_sharing  For AD1985, turn on OMS bit and use headphone
1968	    - alc_jack	For ALC65x, turn on the jack sense mode
1969	    - inv_eapd	Inverted EAPD implementation
1970	    - mute_led	Bind EAPD bit for turning on/off mute LED
1971	
1972	For backward compatibility, the corresponding integer value -1, 0,
1973	... are  accepted, too.
1974	
1975	For example, if "Master" volume control has no effect on your device
1976	but only "Headphone" does, pass ac97_quirk=hp_only module option.


---

### Post by riisimaria on 2009-07-27
The music is still choppy after doing **sudo modprobe -r snd_atiixp_modem**... so could the problem be something else?

---

### Post by martinbaselier on 2009-07-27
Those were the solutions I found for alsa. Your card is supported by OSSv4. So I can only suggest to try to follow one of the guides in my signature. I'm willing to help if it doesn't work. Sound is not working for you now anyway, so trying OSS will definitely not break your audio. 

I think they're pretty easy to follow. Please let me know if there are parts which are hard to understand.

---

### Post by riisimaria on 2009-07-27
I followed your signature link to get OSSv4 and installed it though im not sure did i do it completely the right way..

But i got this in the terminal :
kristina@kristina-laptop:~$ lsmod | grep oss
oss_usb               117132  4 
oss_atiaudio           21744  12 
osscore               561844  2 oss_usb,oss_atiaudio

and...the choppiness is gone!!!!!!! wohooooo!! though there is a small "static" sound with some songs, a bit like my speakers can't handle the bass or something..most likely my speakers..

But thank you so much! u don't know frustrated i was getting! i just hope its not a temporary fix! :D

---

### Post by jerrrys on 2009-07-27
:)

---

### Post by martinbaselier on 2009-07-27
about the static sound: try ossxmix from a terminal and check the volume settings. A tip: add it to the applications that start on default.

---

### Post by riisimaria on 2009-07-28
ok i think i spoke too soon..

The music isn't as choppy as before but there tiny tiny glitches..they are almost bearable but still not ideal...

oh and about the static sound, it seems to be coming just from my right speaker.. i tried adjusting the volume but still the same..

---

### Post by martinbaselier on 2009-07-28
Could you post a screenshot of your volume settings? 
Which music player do you use?

---

### Post by riisimaria on 2009-07-28
ok stupid question..how do i get a screenshot of the volume settings?..

im using rhythmbox...

---

### Post by igorzwx on 2009-07-28
**How to Take a Screenshot in Linux (Ubuntu)**

[http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux](http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux)
[http://maketecheasier.com/ways-to-grab-screenshots-in-ubuntu/2008/11/11](http://maketecheasier.com/ways-to-grab-screenshots-in-ubuntu/2008/11/11)

---

### Post by martinbaselier on 2009-07-28
I've got an application called xfce4-screenshoter, but as the name says it's for xfce4. I thought it was installed by default. I guess I use gnome too little. I hope the links will provide info. Gnome must have something similar. 

Have you tried another music player. I think banshee is quite nice. And the ultimate player is of course vlc (plays life the universe and everything; just don't forget to bring your towel and a bag of peanuts)

---

### Post by riisimaria on 2009-07-29
[IMG]file:///home/kristina/Desktop/Screenshot-ossxmix.png[/IMG]/home/kristina/Desktop/Screenshot-ossxmix.png

---

### Post by riisimaria on 2009-07-29
heh oops...yeah managed to get a screenshot but another stupid question..how do i post it here?! :D

---

### Post by martinbaselier on 2009-07-29
:) you can upload it to [http://tinypic.com](http://tinypic.com) 

After oploading just copy the BB code for use on forums.

---

### Post by riisimaria on 2009-07-30
ok lets give it a go..

[IMG]http://i25.tinypic.com/llbiu.png[/IMG]

---

### Post by martinbaselier on 2009-07-31
It looks rather pink. 

I'd advise you to turn down the volume of line, cd, aux1 and mono. You could turn off micboost too for the moment and maybe igain.  This way you won't have interference from external sources. 

I still wonder what the cause of the glitches might be. Have you tried vlc to see if it makes any difference. Do the glitches occur with all formats? (mp3/ogg/flac) To try different formats you can check 
[http://www.archive.org/details/opensource_audio](http://www.archive.org/details/opensource_audio) 
Most stuff there is in mp3 and ogg.

---

### Post by martinbaselier on 2009-08-02
I just had an idea. If you follow the multimedia guide in my signature, it might help solve some problems. It helps to make ubuntu more multimedia ready, makes sure all the codecs are installed etc. This might be helpful and it certainly won't be a bad thing to do.

---

