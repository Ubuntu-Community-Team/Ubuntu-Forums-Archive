---
title: "PulseAudio Volume Control. Connection failed:Connection refused"
date: 2010-07-04
forum: Multimedia Software
---

### Post by slipknott on 2010-07-04
Hello, 

I tried to finally set-up surround sound on my Ubuntu 10.04 machine and i was successful in doing so after a while of changing settings and tinkering.  After doing so though, i was later in the day not able to get into the Pulseaudio Volume Control, therefore, everything is stuck where it is and i can't change anything. When i try to open Pulseaudio Volume Control i get the error message, Connection failed, Connection refused. My programs still play sound and i can control the sound of the programs through the programs, but i cant control the sound of the sorround sound now and my main sound bar only affects my stereo speakers, not the surround ones. 

I believe this may have happened after the random disk check on restart, but i can't 100% confirm that and i'm not even sure if they are related. I still have sound, but i have no way to control the volume of my entire system at once.  I did some looking around online and saw that others are having or had the same issue, and it was through different versions of Linux also. Listed below is everything i have tried so hopefully someone here will be able to help me resolve the issue, or at least be able to somehow reset everything so i can access PAVC and start over . I also tried steps listed in another thread here on the same topic, but they weren't working and it also seemed to be for older Ubuntu versions. If any other info is required please let me know, thanks!



When i try to open Pulseaudio Device chooser, nothing happens
Pulseaudio Equalizer will open, and i can still enable the EQ

killall pulseaudio  seems to work, but both of the next commands reply with an error message

pulseaudio --start 
E: main.c: Daemon startup failed.

pulseaudio -D
E: main.c: Daemon startup failed.

pulseaudio
E: main.c: Daemon startup without any loaded modules, refusing to work.

I have renamed the /etc/pulse folder to pulse2, re-installed and let pulse recreate the pulse folder

I have re-installed everything in the synaptic package manager that looks like it is associated with pulse

When trying to access Preferences > Sound, a prompt comes up saying "Waiting for sound system to respond", and nothing happens, i just have to cancel out of it.

In Preferences > Startup Applications, Pulseaudio Sound System is listed and checked, the Command is start-pulseaudio-x11  When running this command seperately, it doesn't work.

---

### Post by lilychef on 2010-07-05
I'm in exactly the same boat, and am getting really tired of it.  Everything slipknott describes is exactly as my system appears.  As I've said in many posts, what frustrates me most is that everything worked AWESOME when I first upgraded to Lucid - I had surround when I never had it before in previous versions of Ubuntu, and an awesome sound control board.  But it was after an update to the system (that we're supposed to just blindly accept and perform, becasue we don't know any better) when the problems appeared.  Afrodeity describes some recent gstreamer updates that "borked" his sound _[here]("http://ubuntuforums.org/showthread.php?p=9546758#post9546758")_, but after prodding him/her about that he/she has not elaborated (yet)...

Frustration is actually a really nice word at this point.

Oh - and when I go to the Pulseaudio device chooser, it begins to load, then quits loading.  Then when I try to open Pulseaudio Volume Control, I can see the panel, but a window pops up with an error message that says, "Connection failed. Connection refused"

asla -l gives this:

**** List of PLAYBACK Hardware Devices ****
card 0: AV710 [Chaintech AV-710], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AV710 [Chaintech AV-710], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AV710 [Chaintech AV-710], device 2: ICE1724 Surrounds [ICE1724 Surround PCM]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

Why does it show three devices????

---

### Post by lilychef on 2010-07-05
One more thing - my system doesn't have a plain asound.conf file, but does have a asound.conf_jack and a asound.conf_oss files.  Whassup with that?  Did I read that asound.conf was eliminated in Lucid?

---

### Post by lilychef on 2010-07-06
Just trying to keep the thread alive... I'm all about a reinstall at this point...  The question is WHICH update screwed it all up?  Becasue that's the one to avoid and to complain about...

---

### Post by afrodeity on 2010-07-11
Last time my sound was actually stable was in hardy. Karmic wasn't too bad. But with lucid its quite terrible. Keeps quitting. I think it has something to asound.conf

---

### Post by OdracirAlv on 2010-10-15
I have exactly the some problem.
 I had everything working on 9.10. Than  I made the upgrade to 10.04 and my sound bottons and micro stopped to work exactly as you described.
 

 Annoying.

---

### Post by hugo1967 on 2011-03-06
I had all of those same problems.  I tried solutions from all over the forums with no luck.  I finally solved the problem by 'purging' pulseaudio rather than just re-installing:

sudo apt-get purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove

I rebooted just for grins, then 

sudo apt-get install pulseaudio

Now all is right in the world!!  Hope this helps

---

### Post by sanjeevpunj on 2011-06-16
I tried this and got the following results-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  pulseaudio-esound-compat pulseaudio-module-x11
Suggested packages:
  paprefs pulseaudio-module-raop
The following NEW packages will be installed:
  pulseaudio pulseaudio-esound-compat pulseaudio-module-x11
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 673 kB of archives.
After this operation, 2,843 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main pulseaudio i386 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 [624 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main pulseaudio-esound-compat i386 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 [31.9 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main pulseaudio-module-x11 i386 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 [16.6 kB]
Fetched 673 kB in 3s (175 kB/s)                 
Selecting previously deselected package pulseaudio.
(Reading database ... 159341 files and directories currently installed.)
Unpacking pulseaudio (from .../pulseaudio_1%3a0.9.22+stable-queue-24-g67d18-0ubuntu3.1_i386.deb) ...
Selecting previously deselected package pulseaudio-esound-compat.
Unpacking pulseaudio-esound-compat (from .../pulseaudio-esound-compat_1%3a0.9.22+stable-queue-24-g67d18-0ubuntu3.1_i386.deb) ...
Selecting previously deselected package pulseaudio-module-x11.
Unpacking pulseaudio-module-x11 (from .../pulseaudio-module-x11_1%3a0.9.22+stable-queue-24-g67d18-0ubuntu3.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up pulseaudio (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1) ...
Adding user pulse to group audio
 * PulseAudio configured for per-user sessions
Setting up pulseaudio-esound-compat (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1) ...
Setting up pulseaudio-module-x11 (1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: Cannot lstat /usr/lib/libpanel-applet-2.so.0.2.73: Input/output error


------------------------------------------------------------------------------------

Sometimes my Sound card (PCI card M-Audio Deltaphile) works even despite all this, but I do not find the option for changing my sound preferences conclusively(when i click on the pulseaudio volume control application, it opens, with the message-Connection Failed,Connection refused, When I click on the Sound Application, nothing happens, just I get the message "Waiting for sound system to respond"Still sound is heard and it is strange that the system chooses its own sound output device, does not let me make a choice.

---

### Post by lidex on 2011-06-18
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Now this - Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by osmundi on 2011-09-12
Ok, I have also the same problem and did the tasks descriped above. Nothing has changed. Here's the link from ALSA [http://www.alsa-project.org/db/?f=0a5a7a88d15c76136f8e38e904522e91052bb611](http://www.alsa-project.org/db/?f=0a5a7a88d15c76136f8e38e904522e91052bb611)

---

### Post by lidex on 2011-09-14
> **osmundi said:**
> Ok, I have also the same problem and did the tasks descriped above. Nothing has changed. Here's the link from ALSA [http://www.alsa-project.org/db/?f=0a5a7a88d15c76136f8e38e904522e91052bb611](http://www.alsa-project.org/db/?f=0a5a7a88d15c76136f8e38e904522e91052bb611)

What is the output of this:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by blogmaniak on 2011-11-20
> **lidex said:**
> What is the output of this:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

Bringing this back, as I am at the same place with pulseaudio on 10.04.

vibhu@bhanubuntu:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 0c77921126d70db08ff486c54cde904c.
I: main.c: Session ID is 0c77921126d70db08ff486c54cde904c-1321814674.799293-1911626371.
E: core-util.c: Home directory /home/vibhu not ours.

---

