---
title: "Sound problem on Ubuntu 10.10"
date: 2010-10-25
forum: Multimedia Software
---

### Post by deshank on 2010-10-25
I am having this peculiar sound problem on Ubuntu 10.10 (freshly installed). Whenever i am listening to music or watching a movie, after some time it happens that sound starts coming with pauses as if you are listening to music from an old, tampered tape. Interestingly, once this problem has started, all my music players respond with the same problem. Normal operations as maximizing a window starts slowing down. Finally when I try shutting down my PC, it takes long time to shut down requiring lots of 'Esc' and 'Ctrl+Alt+Del' presses. Please Help.

---

### Post by lidex on 2010-10-25
There have been issues with this plugin:
```
gstreamer0.10-pulseaudio
```
Try uninstalling it.

---

### Post by ccoupe on 2010-10-28
I've got a similar problem in UbuntuStudio 10.4 and removing gstreamer-10-pulseaudio didn't fix it.

Audio plays for around 7-10 minutes and then drops out. Rhythmbox then skips thru all rest of the Album. In Flash vidoes the sound just drops out but the video continues. Same with VLC. Doesn't seem to be related to the power saver settings.

---

### Post by lidex on 2010-10-28
> **ccoupe said:**
> I've got a similar problem in UbuntuStudio 10.4 and removing gstreamer-10-pulseaudio didn't fix it.

Audio plays for around 7-10 minutes and then drops out. Rhythmbox then skips thru all rest of the Album. In Flash vidoes the sound just drops out but the video continues. Same with VLC. Doesn't seem to be related to the power saver settings.

Post this output please:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by ccoupe on 2010-10-28
```
ccoupe@twb:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: setpriority() worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 13:40:34 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 650851bb0ec0af0126ef9df449f31403.
I: main.c: Session ID is 650851bb0ec0af0126ef9df449f31403-1288238612.239811-1233201475.
I: main.c: Using runtime directory /home/ccoupe/.pulse/650851bb0ec0af0126ef9df449f31403-runtime.
I: main.c: Using state directory /home/ccoupe/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
ccoupe@twb:~$ man pkill

```

---

### Post by ccoupe on 2010-10-28
Same error messages when run as sudo

---

### Post by ccoupe on 2010-10-28
Also, when it stops playing the following shows up in syslog

```
Oct 28 17:56:18 twb pulseaudio[8609]: pid.c: Stale PID file, overwriting.
Oct 28 17:56:19 twb pulseaudio[8628]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8629]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8630]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8631]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8632]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8633]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8634]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8635]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8636]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8637]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8638]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8639]: pid.c: Daemon already running.
Oct 28 17:56:19 twb pulseaudio[8640]: pid.c: Daemon already running.

```

---

### Post by lidex on 2010-10-28
Try removing old audio config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by ccoupe on 2010-10-28
That almost worked. An album played to around the 30 minute mark and when I launched Firefox Gnome froze solid with electronic sputter in the speakers. HW reset and boot and then it dropped out around the 7 minute mark just like before. Tried again, failed - about 7 minutes of audio is all I get. That freeze bothers me - its been a long time since I've had to hit the HW reset in Linux.

---

### Post by herophuong on 2010-10-29
Same problem with me! Is there any work around yet? If not, I have to downgrade to 10.04 if I want to listen to music.
*Update*: The lidex's method works like a charm, although I don't have .asound dir and asound.conf file. Thanks very much.

---

### Post by ccoupe on 2010-10-29
After looking around the forum, this is a problem that affects some 10.4 (UbuntuStudio folks like me) 
and some 10.10 users (of any variety Ubuntu) like you. 

With a little bravery and a reboot or two, you can remove the PulseAudio succubus:
[http://art.ubuntuforums.org/showthread.php?p=9202903](http://art.ubuntuforums.org/showthread.php?p=9202903)

You'll want to edit away some stuff away in the Gnome menus that calls PulseAudio/Ubuntu 
and put in the ALSA equivalents. 

I think it sounds better too. I could be talking nonsense about that. 
I kind of remember now that I had to remove PulseAudio in UbuntuStudio 9.10

---

### Post by LouReed on 2010-11-01
Hi,

I'm not entirely sure I should post this here but :

I had the exact same problems when I updated my Ubuntu 10.04 to 10.10 last week.
Sound would drop after a while on pretty much any program I try to use.
Sound was getting jerky and the whole system froze etc..

So I did a clean reinstall of 10.10 and now Rhythmbox and Movie player work like a charm.
In firefox youtube works perfectly so does Deezer.

Everything is perfect but for this really peculiar phenomenon :

When I tried to play a video with vlc I had perfect video, the music and the sound effects were perfect too, but the voices of the characters speaking were just non-existent.

I tried to play it with movieplayer and it worked with the voices and all.
So I'm confronted to a very disturbing phenomenon and I was kind of hoping someone would have an answer to this.

---

### Post by brynhildur on 2010-11-01
I found this on [another thread]("http://ubuntuforums.org/showthread.php?t=1476573&page=3"), and it worked perfectly and I can finally watch videos in VLC with perfect sound (my problem was that sound worked perfectly when listening or watching files online, but sound was choppy or nonexistant in media players): 
[INDENT]Without running any codes in terminal, what helped me was the following:

1. Go to 'Home' folder by clicking the 'Places' menu
2. press Ctrl + H to reveal hidden folders
3. delete the '.pulse' folder
4. restart

Hope this helps someone
[/INDENT]This was after trying many many different solutions offered on these forums. Often it is the simple ones which work. 

I wonder, though, why this problem is appearing in 10.10. I have previously used 9.04 and 9.10 and there was no problem with sound at all in those installations!

---

### Post by Ampi on 2010-11-01
Oh my god thanks :)
I was just planning on starting on thread because my youtube and vimeo videos suddenly for no reason had no sound and went on double speed.. 
Deleting this folder also helps in this problem apparently. Now I hope my videos will also be less choppy ;)

---

### Post by dude4linux on 2010-11-01
Thanks, that seems to have worked for me as well.  I've been having intermittent sound (sometimes works, sometimes doesn't) since upgrading to 10.4 and the latest version of adobe flash.  Removing the .pulse folder and rebooting allows the pulse audio config to be rebuilt.  

new.pulse
77f787cf9384f17b372a5b00472d2470-card-database.tdb
77f787cf9384f17b372a5b00472d2470-default-sink
77f787cf9384f17b372a5b00472d2470-default-source
77f787cf9384f17b372a5b00472d2470-device-volumes.tdb
77f787cf9384f17b372a5b00472d2470-runtime
77f787cf9384f17b372a5b00472d2470-stream-volumes.tdb

old.pulse
77f787cf9384f17b372a5b00472d2470-card-database.tdb
77f787cf9384f17b372a5b00472d2470-default-sink
77f787cf9384f17b372a5b00472d2470:default-sink
77f787cf9384f17b372a5b00472d2470-default-source
77f787cf9384f17b372a5b00472d2470:default-source
77f787cf9384f17b372a5b00472d2470:device-volumes.i486-pc-linux-gnu.gdbm
77f787cf9384f17b372a5b00472d2470-device-volumes.tdb
77f787cf9384f17b372a5b00472d2470-runtime
77f787cf9384f17b372a5b00472d2470:runtime
77f787cf9384f17b372a5b00472d2470:stream-volumes.i486-pc-linux-gnu.gdbm
77f787cf9384f17b372a5b00472d2470-stream-volumes.tdb

Notice the extra files with the ':' instead of '-'.  I think they were left behind by the upgrade process and my have confused pulseaudio.  I'll be watching to see if this has fixed all my sound issues. :)

Update #1
Apparently removing the .pulse folder and rebooting did not solve the problem.  It worked fine for two days, but the next time I started the Chromium browser I noticed that sound was broken again.  I rebooted without changing the .pulse folder and got sound back.  Must be related to my version of Chromium which is a development build.  At least I have a clue as to what caused my problem.

---

### Post by RheaHS on 2010-11-01
None of this has worked for me, and I still have no audio in anything other than Firefox.

---

### Post by md.nazri on 2010-11-02
I had the same issue (sound & video jerky) and this is what I did to resolve the issue - download and install the latest Maverick kernel at

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/) in order (depend on your architecture i.e, amd vs intel):

a. linux-headers-2.6.36-020636_2.6.36-020636.201010210905_all.deb
b. linux-headers-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb
c. linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb

Reboot the system to complete the installation.

The result.. so far so good :-)

nazri@SUT:~$ uname -a
Linux SUT 2.6.36-020636-generic #201010210905 SMP Thu Oct 21 10:17:53 UTC 2010 i686 GNU/Linux

---

### Post by RheaHS on 2010-11-02
Again, didn't fix the problem, still the same. I've got a few extra options in sound preferences, but that's about it. I've tried getting new drivers from Realtek as well for the 268, but I'm confused, as when I try to install them, the file ends abruptly, it seems like something is missing.

---

### Post by lidex on 2010-11-02
> **RheaHS said:**
> Again, didn't fix the problem, still the same. I've got a few extra options in sound preferences, but that's about it. I've tried getting new drivers from Realtek as well for the 268, but I'm confused, as when I try to install them, the file ends abruptly, it seems like something is missing.

Boot into your default kernel and run the alsa-info script please.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by md.nazri on 2010-11-02
On Ubuntu 10.10, we can switch between alsa or pulseaudio using Multimedia System Selector. From terminal, run -> gstreamer-properties

---

### Post by RheaHS on 2010-11-03
> **lidex said:**
> Boot into your default kernel and run the alsa-info script please.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

[http://www.alsa-project.org/db/?f=49c7912635f13e28261a59e1e378072990abc90c](http://www.alsa-project.org/db/?f=49c7912635f13e28261a59e1e378072990abc90c)

Had a major problem last night, lost the sound card completely, this is getting majorly annoying now. It's back, but still back to square one.

---

### Post by lidex on 2010-11-03
> **RheaHS said:**
> [http://www.alsa-project.org/db/?f=49c7912635f13e28261a59e1e378072990abc90c](http://www.alsa-project.org/db/?f=49c7912635f13e28261a59e1e378072990abc90c)

Had a major problem last night, lost the sound card completely, this is getting majorly annoying now. It's back, but still back to square one.

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Other models:
```
acer
acer-dmic
auto
```

---

### Post by kalalnavin on 2010-11-04
will someone help me from this problem.....I really need urjent help on thisssssssssssssssss:mad::mad::mad::mad:

init:failed to spawn plymouth main process:unable to execute:exec format error
init:failed to spawn hwclock main process:unable to execute:exec format error
init:failed to spawn mountall main process:unable to execute:exec format error
init:failed to spawn mountall post-stop process:unable to execute:exec format error


thanks in advanceeeeeee

---

### Post by RheaHS on 2010-11-04
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Other models:
```
acer
acer-dmic
auto
```

OK, for anyone else with this problem and hardware, using this method and option solved my problem. Thankyou very much.

---

### Post by Mgiacchetti on 2010-11-04
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Other models:
```
acer
acer-dmic
auto
```


Would love to see what this is supposed to look like for a non-intel audio card...
like the Creative EMU10k1X??

---

### Post by kaspar42 on 2010-11-11
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack 
```
Save. Close. Reboot. 


I had a similar problem: My sound was 'scratched', becoming progressively worse until next reboot. The above seemed to have solved it completely.

Oddly enough in 9.04 the magic line that fixed my sound was:
```
 options snd-hda-intel model=laptop 
```

---

### Post by butanuki on 2010-11-11
I had a lot of hickups only using VLC-player.

I tried:

Try removing old audio config files:
Using a Terminal="Applications->Accessories->Terminal"
 	Code:
 	rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf 
And this worked PERFECTLY. Thanks!

---

### Post by deshank on 2010-11-13
Still the same problem.....
[http://www.alsa-project.org/db/?f=310cf0f7f522f58747da154c17317c35a146d689](http://www.alsa-project.org/db/?f=310cf0f7f522f58747da154c17317c35a146d689)
...
Plz Help......

---

### Post by lidex on 2010-11-13
> **deshank said:**
> Still the same problem.....
[http://www.alsa-project.org/db/?f=310cf0f7f522f58747da154c17317c35a146d689](http://www.alsa-project.org/db/?f=310cf0f7f522f58747da154c17317c35a146d689)
...
Plz Help......

That model option not for you OP. Your best to try:
```
acer
acer-aspire
auto
```

---

### Post by deshank on 2010-11-18
Not solved.....tried all the models...

---

### Post by deshank on 2010-12-04
thanx to all......my problem is finally solved.......i compiled the latest maverick kernel and it solved the problem!!!

---

### Post by Qdlaty on 2010-12-25
> **deshank said:**
> thanx to all......my problem is finally solved.......i compiled the latest maverick kernel and it solved the problem!!!

What is the kernel version you have compiled to fix it?
I cannot get rid of the choppy sound even with "tsched=0" option or/and kernel version 2.6.36-020636.

Edit.
No luck with 2.6.37-rc7 either.

Running out of ideas :/

---

### Post by lafskelton on 2011-01-30
Hi, i have the same problem exept NO SOUND no soud atALL
it occured after installing macbuntu and now i can only log on as root :cry: But the macbuntu F***ed it self up and well HELP :KS

---

### Post by South_Canadian_Denizen on 2011-02-24
It works perfectly, just as you said. Many thanks for the Post and the useful info.

---

### Post by forestwalkerjoe on 2011-08-24
ok.. I have already done the [remove pulse audio stuff.]("http://ubuntuforums.org/showthread.php?t=1316634&highlight=no+sound"). dont ask me how to get that back.. no idea.. done the install alsa.. stuff.. did the edit adding the line looking for [B]options snd-hda-intel probe_mask=1 model=auto
[/B]Nothing. 
I have gone to do the **systems preferences SOUND.. **and it says it is trying to activate sound. Never comes on.. and I have No icons above for sound.[B]
I did find [this page]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure").. looks like a more informed mind and it also looks pretty complete. IF it is not a fix.. I am sure to have messed it all up. anyone like to add any helps here ? 

[/B]

---

### Post by lidex on 2011-08-24
> **forestwalkerjoe said:**
> ok.. I have already done the [remove pulse audio stuff.]("http://ubuntuforums.org/showthread.php?t=1316634&highlight=no+sound"). dont ask me how to get that back.. no idea.. done the install alsa.. stuff.. did the edit adding the line looking for [B]options snd-hda-intel probe_mask=1 model=auto
[/B]Nothing. 
I have gone to do the **systems preferences SOUND.. **and it says it is trying to activate sound. Never comes on.. and I have No icons above for sound.[B]
I did find [this page]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure").. looks like a more informed mind and it also looks pretty complete. IF it is not a fix.. I am sure to have messed it all up. anyone like to add any helps here ? 

[/B]

You have not supplied any useful info for troubleshooting. It would be helpful if you started a new thread and detail your issue, providing this:
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by acidblue on 2012-02-24
I have tried every thing and still having skipping problems.
I have removed pulseaudio and replaced it with alsa.

Here is my alsa info:
[http://www.alsa-project.org/db/?f=b328a5d17d2aaff78f39989059516fc63bad6dae](http://www.alsa-project.org/db/?f=b328a5d17d2aaff78f39989059516fc63bad6dae)
I've tried acer, acer-travelmate, auto, laptop, pretty much everything.
Still no dice :(
I can no longer access "System>Preferences>Sound. I get the 'Waiting for sound system to respond'
Please help.

---

