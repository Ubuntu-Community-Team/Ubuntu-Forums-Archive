---
title: "LIRC and remote control in 9.04"
date: 2009-04-28
forum: Multimedia Software
---

### Post by diamondnular on 2009-04-28
Hi folks,

I am trying to install LIRC to make my remote control work with 9.04, and I am getting stuck now. Searching the forum and google gave me some information how to install and configure LIRC like follow:

1. Install lirc, lirc-modules-source and module-assistant
2. Configure lircd.conf and hardware.conf in /etc/lirc to enable remote with LIRC (in my case, it is a VLSystem Mplay Blast)
3. start the service lircd (sudo /etc/init.d/lirc start)

Now testing with remote using 'irw', but pressing remote does not produce any output. It seems my computer still does not recognize my remote.

Do I miss any step? Anybody helps please!

Thanks,

D.

---

### Post by lovinglinux on 2009-04-29
Open the file /etc/lirc/lircd.conf

You should see a line like this:

```
include /usr/share/lirc/remotes/yourremotebrand/lircd.conf.brand
```

Make sure the path is quoted like this:

```
include "/usr/share/lirc/remotes/yourremotebrand/lircd.conf.brand"
```

This probably should fix it.

---

### Post by diamondnular on 2009-04-29
It is already like that

```
#Configuration for the VLSystem MPlay Blast remote:
include "/usr/share/lirc/remotes/vlsystem/lircd.conf.mplay"
```

but the problem is still there! Help please!

---

### Post by lovinglinux on 2009-04-29
> **diamondnular said:**
> It is already like that

```
#Configuration for the VLSystem MPlay Blast remote:
include "/usr/share/lirc/remotes/vlsystem/lircd.conf.mplay"
```

but the problem is still there! Help please!

Try commenting that line and paste the content of /usr/share/lirc/remotes/vlsystem/lircd.conf.mplay into this file and save it. See if it works. Worked for me and my situation was similar to yours. Everything was loading properly, but no signal from the remote.

---

### Post by lovinglinux on 2009-04-29
I forgot to mention this on my previous post...

Check if there is a .lircrc file in your home directory and paste the content of the file here.

Also paste the output of this command:

```
cat /var/log/daemon.log | grep lirc
```

---

### Post by diamondnular on 2009-04-29
> **lovinglinux said:**
> I forgot to mention this on my previous post...

Check if there is a .lircrc file in your home directory and paste the content of the file here.

No, I do not have this file. Do I need it? How do I get it?

> **lovinglinux said:**
> 
Also paste the output of this command:

```
cat /var/log/daemon.log | grep lirc
```

Here you go:

```
Apr 27 02:23:59 iQ9300 lircd-0.8.4a[32272]: lircd(mplay) ready
Apr 27 02:32:53 iQ9300 lircd-0.8.4a[32272]: caught signal
Apr 27 02:33:00 iQ9300 lircd-0.8.4a[4347]: lircd(mplay) ready
Apr 27 02:39:57 iQ9300 lircd-0.8.4a[4347]: accepted new client on /dev/lircd
Apr 27 02:41:13 iQ9300 lircd-0.8.4a[4347]: caught signal
Apr 27 02:42:28 iQ9300 lircd-0.8.4a[3598]: lircd(mplay) ready
Apr 27 02:43:03 iQ9300 lircd-0.8.4a[3598]: accepted new client on /dev/lircd
Apr 27 02:43:43 iQ9300 lircd-0.8.4a[3598]: removed client
Apr 27 02:49:13 iQ9300 lircd-0.8.4a[3598]: accepted new client on /dev/lircd
Apr 27 02:49:44 iQ9300 lircd-0.8.4a[3598]: caught signal
Apr 27 02:49:46 iQ9300 lircd-0.8.4a[5000]: lircd(mplay) ready
Apr 27 02:49:52 iQ9300 lircd-0.8.4a[5000]: caught signal
Apr 27 02:49:55 iQ9300 lircd-0.8.4a[5047]: lircd(mplay) ready
Apr 27 02:52:18 iQ9300 lircd-0.8.4a[5047]: accepted new client on /dev/lircd
Apr 27 02:53:53 iQ9300 lircd-0.8.4a[3606]: lircd(mplay) ready
Apr 27 02:58:04 iQ9300 lircd-0.8.4a[3606]: accepted new client on /dev/lircd
Apr 27 02:58:21 iQ9300 lircd-0.8.4a[3606]: accepted new client on /dev/lircd
Apr 27 02:59:36 iQ9300 lircd-0.8.4a[3606]: accepted new client on /dev/lircd
Apr 27 03:03:21 iQ9300 lircd-0.8.4a[3606]: caught signal
Apr 27 03:03:21 iQ9300 lircd-0.8.4a[5415]: lircd(mplay) ready
Apr 27 03:03:25 iQ9300 lircd-0.8.4a[5415]: accepted new client on /dev/lircd
Apr 27 03:03:36 iQ9300 lircd-0.8.4a[5415]: accepted new client on /dev/lircd
Apr 27 19:44:00 iQ9300 lircd-0.8.4a[5415]: accepted new client on /dev/lircd
Apr 27 20:08:08 iQ9300 lircd-0.8.4a[5415]: accepted new client on /dev/lircd
Apr 27 20:12:20 iQ9300 lircd-0.8.4a[5415]: caught signal
Apr 27 20:12:26 iQ9300 lircd-0.8.4a[10140]: lircd(mplay) ready
Apr 27 20:12:40 iQ9300 lircd-0.8.4a[10140]: accepted new client on /dev/lircd
Apr 27 20:12:49 iQ9300 lircd-0.8.4a[10140]: accepted new client on /dev/lircd
Apr 27 21:04:06 iQ9300 lircd-0.8.4a[10140]: accepted new client on /dev/lircd
Apr 27 21:05:36 iQ9300 lircd-0.8.4a[10140]: removed client
Apr 27 21:05:47 iQ9300 lircd-0.8.4a[10140]: accepted new client on /dev/lircd
Apr 27 21:07:01 iQ9300 lircd-0.8.4a[10140]: caught signal
Apr 27 21:07:05 iQ9300 lircd-0.8.4a[11474]: lircd(mplay) ready
Apr 27 21:07:09 iQ9300 lircd-0.8.4a[11474]: accepted new client on /dev/lircd
Apr 27 21:11:58 iQ9300 lircd-0.8.4a[11474]: accepted new client on /dev/lircd
Apr 27 21:22:56 iQ9300 lircd-0.8.4a[11474]: caught signal
Apr 27 21:27:06 iQ9300 lircd-0.8.4a[17814]: lircd(mplay) ready
Apr 27 21:32:22 iQ9300 lircd-0.8.4a[17814]: accepted new client on /dev/lircd
Apr 27 21:32:22 iQ9300 lircd-0.8.4a[17814]: readlink() failed for "/dev/lirc"
Apr 27 21:32:22 iQ9300 lircd-0.8.4a[17814]: No such file or directory 
Apr 27 21:32:22 iQ9300 lircd-0.8.4a[17814]: Could not create the lock file
Apr 27 21:32:22 iQ9300 lircd-0.8.4a[17814]: Failed to initialize hardware
Apr 27 21:32:34 iQ9300 lircd-0.8.4a[17814]: accepted new client on /dev/lircd
Apr 27 21:34:10 iQ9300 lircd-0.8.4a[17814]: caught signal
Apr 27 21:34:12 iQ9300 lircd-0.8.4a[26702]: lircd(mplay) ready
Apr 27 21:34:15 iQ9300 lircd-0.8.4a[26702]: accepted new client on /dev/lircd
Apr 27 21:34:28 iQ9300 lircd-0.8.4a[26702]: accepted new client on /dev/lircd
Apr 27 21:35:42 iQ9300 lircd-0.8.4a[26702]: caught signal
Apr 27 21:35:50 iQ9300 lircd-0.8.4a[26756]: lircd(mplay) ready
Apr 27 21:50:52 iQ9300 lircd-0.8.4a[26756]: caught signal
Apr 27 21:50:53 iQ9300 lircd-0.8.4a[27342]: lircd(mplay) ready
Apr 27 21:50:56 iQ9300 lircd-0.8.4a[27342]: accepted new client on /dev/lircd
Apr 27 22:09:08 iQ9300 lircd-0.8.4a[27342]: accepted new client on /dev/lircd
Apr 27 22:13:33 iQ9300 lircd-0.8.4a[27342]: caught signal
Apr 27 22:13:36 iQ9300 lircd-0.8.4a[27952]: lircd(mplay) ready
Apr 27 22:13:38 iQ9300 lircd-0.8.4a[27952]: accepted new client on /dev/lircd
Apr 27 22:13:49 iQ9300 lircd-0.8.4a[27952]: accepted new client on /dev/lircd
Apr 27 22:32:08 iQ9300 lircd-0.8.4a[27952]: accepted new client on /dev/lircd
Apr 27 22:40:25 iQ9300 lircd-0.8.4a[27952]: removed client
Apr 27 22:40:25 iQ9300 lircd-0.8.4a[27952]: removed client
Apr 27 22:40:27 iQ9300 lircd-0.8.4a[27952]: caught signal
Apr 27 22:41:41 iQ9300 lircd-0.8.4a[2945]: lircd(mplay) ready
Apr 27 22:42:28 iQ9300 lircd-0.8.4a[2945]: accepted new client on /dev/lircd
Apr 27 22:42:45 iQ9300 lircd-0.8.4a[2945]: accepted new client on /dev/lircd
Apr 27 22:43:13 iQ9300 lircd-0.8.4a[2945]: removed client
Apr 27 23:02:52 iQ9300 lircd-0.8.4a[2945]: accepted new client on /dev/lircd
Apr 27 23:03:15 iQ9300 lircd-0.8.4a[2945]: accepted new client on /dev/lircd
Apr 27 23:03:27 iQ9300 lircd-0.8.4a[2945]: removed client
Apr 27 23:03:27 iQ9300 lircd-0.8.4a[2945]: removed client
Apr 28 20:37:40 iQ9300 lircd-0.8.4a[2945]: accepted new client on /dev/lircd
Apr 28 20:48:11 iQ9300 lircd-0.8.4a[2945]: caught signal
Apr 28 20:48:13 iQ9300 lircd-0.8.4a[20092]: lircd(mplay) ready
Apr 28 20:48:16 iQ9300 lircd-0.8.4a[20092]: accepted new client on /dev/lircd
Apr 28 20:48:37 iQ9300 lircd-0.8.4a[20092]: accepted new client on /dev/lircd
Apr 28 21:01:12 iQ9300 lircd-0.8.4a[20092]: accepted new client on /dev/lircd
Apr 28 21:01:41 iQ9300 lircd-0.8.4a[20092]: caught signal
Apr 28 21:01:44 iQ9300 lircd-0.8.4a[20806]: lircd(mplay) ready
Apr 28 21:02:24 iQ9300 lircd-0.8.4a[20806]: accepted new client on /dev/lircd
Apr 28 21:05:35 iQ9300 lircd-0.8.4a[20806]: caught signal
Apr 28 21:05:35 iQ9300 lircd-0.8.4a[20843]: lircd(mplay) ready
Apr 28 21:05:39 iQ9300 lircd-0.8.4a[20843]: caught signal
Apr 28 21:05:42 iQ9300 lircd-0.8.4a[20888]: lircd(mplay) ready
Apr 28 21:06:18 iQ9300 lircd-0.8.4a[20888]: accepted new client on /dev/lircd
```

---

### Post by diamondnular on 2009-04-29
To my understand, lirrc file needed if you want the remote to control some specific application with specific buttons. I have not gone up there. I just want to have my remote recognized by the computer first.

---

### Post by lovinglinux on 2009-04-29
Have you tried the workaround from my post [#4](http://ubuntuforums.org/showpost.php?p=7173908&postcount=4)?

---

### Post by diamondnular on 2009-04-29
Yeah, tried that and no help :(. Its strange.

---

### Post by markdavidoff on 2009-04-29
Are you using a supported remote?
What hardware are you using to receive commands?

irw is only useful once you have the remote set up and working

try using mode2, aiming the remote at the reciever, and pressing buttons. If the reciever is working properly, codes should appear.

If mode2 works, you can try recording your own config file using irrecord

I had a lot of pain getting lirc to work for me. I eventually figured out it was a hardware problem, and built my own serial reciever.

here is my post:
[http://ubuntuforums.org/showthread.php?t=1086533](http://ubuntuforums.org/showthread.php?t=1086533)

I don't know if that will help

---

### Post by diamondnular on 2009-04-29
I have a VLSystem M-Play Blast including one LCD and one remote, and yes, it is supported in LIRC. When installing LIRC, VLSystem MPlay Blast is almost at the end of the choosing list. Also, I have this problem with new 9.04. A month ago I got it working with 8.10 as well, but do not really remember what I did :D. I believe there is something wrong or there is a missing step that I had, but can not figure it out.

Is there a full instruction (very update, not those old wiki ones) that I can try?

By the way, how to try mode2? just type 'mode2' in bash like 'irw'?

Thanks,

D.

---

### Post by diamondnular on 2009-04-29
Hi again,

I just tried 'mode2', and I think I found something:

```
$ mode2
mode2: Entering mplay_init()
mode2: readlink() failed for "/dev/lirc"
mode2: No such file or directory
mode2: Could not create the lock file
mode2: Could not create the lock file
$ ls /dev | grep lir*
lirc0
lircd

```

I am pretty sure the device should be /dev/lirc0, but somehow it becomes /dev/lirc. Is there any way to fix this? How I can tell lirc to load /dev/lirc0 device?

Thanks,

D.

---

### Post by lovinglinux on 2009-04-29
> **diamondnular said:**
> Hi again,

I just tried 'mode2', and I think I found something:

```
$ mode2
mode2: Entering mplay_init()
mode2: readlink() failed for "/dev/lirc"
mode2: No such file or directory
mode2: Could not create the lock file
mode2: Could not create the lock file
$ ls /dev | grep lir*
lirc0
lircd

```

I am pretty sure the device should be /dev/lirc0, but somehow it becomes /dev/lirc. Is there any way to fix this? How I can tell lirc to load /dev/lirc0 device?

Thanks,

D.

Post the content of /etc/lirc/hardware.conf

---

### Post by diamondnular on 2009-04-29
Here you go

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="VLSystem MPlay Blast"
REMOTE_MODULES=""
REMOTE_DRIVER="mplay"
REMOTE_DEVICE="/dev/ttyUSB0"
REMOTE_LIRCD_CONF="vlsystem/lircd.conf.mplay"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

---

### Post by diamondnular on 2009-04-29
Another question. When I followed the below instruction

[https://help.ubuntu.com/community/InstallLirc/Feisty](https://help.ubuntu.com/community/InstallLirc/Feisty)

I do not see lirc-modules-source.conf in my /etc/lirc. Am I supposed to have one?

Thanks,

D.

---

### Post by lovinglinux on 2009-04-29
Replace the following lines

```
REMOTE_MODULES=""
```

with

```
REMOTE_MODULES="false"
```

and

```
LOAD_MODULES="true"
```

with

```
LOAD_MODULES="lirc_dev lirc_mplay"
```

Restart lirc, run the command irw, press the remote buttons and see if it works. If it doesn't then try this line:

```
LOAD_MODULES="lirc_dev"
```

---

### Post by diamondnular on 2009-04-29
Unfortunately none of your solutions worked. Any other ideas?

---

### Post by lovinglinux on 2009-04-29
> **diamondnular said:**
> Another question. When I followed the below instruction

See my previous post for possible soultion.

I took the information below from my previous post, because you might miss it, since I was editing it.

[https://help.ubuntu.com/community/InstallLirc/Feisty](https://help.ubuntu.com/community/InstallLirc/Feisty)

I do not see lirc-modules-source.conf in my /etc/lirc. Am I supposed to have one?

Thanks,

D.

I don't think is a good idea to follow that tutorial, because it is kind of old. It has some stuff about building the modules that I never did to make my control work. Besides, take a look at the Hardy tutorial:

[https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)

We still don't have a tutorial for Intrepid or Jaunty, but I assume nothing changed drastically since Hardy.

---

### Post by diamondnular on 2009-04-29
> **lovinglinux said:**
> I don't think is a good idea to follow that tutorial, because it is kind of old. It has some stuff about building the modules that I never did to make my control work. Besides, take a look at the Hardy tutorial:

[https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)

We still don't have a tutorial for Intrepid or Jaunty, but I assume nothing changed drastically since Hardy.

I didn't. I just read it for reference, and I found a lot of things different. Basically what I did was like the second link you sent: install lirc, chose my device. That's it! The funny thing is with 8.10, my configuration worked, and fresh install of 9.04 with the same configuration does not work. Why is that???

D.

---

### Post by lovinglinux on 2009-04-29
> **diamondnular said:**
> Unfortunately none of your solutions worked. Any other ideas?

Try installing again, using the tutorial for Hardy.

---

### Post by scottuss on 2009-04-29
I don't want to sound defeatist, because everything is worth a try but I've had issues with my remote for a long time on Ubuntu, in the end I just gave in. I blame the hardware, not Ubuntu. Should have checked compatibility first... but then I guess I got the remote before I started using Linux at all so eh what can you do :)

---

### Post by lovinglinux on 2009-04-29
> **scottuss said:**
> I don't want to sound defeatist, because everything is worth a try but I've had issues with my remote for a long time on Ubuntu, in the end I just gave in. I blame the hardware, not Ubuntu. Should have checked compatibility first... but then I guess I got the remote before I started using Linux at all so eh what can you do :)

Sometimes the solution is easier than we think. I almost gave up on lirc, but one day I tried to do it again and found the solution. It wasn't so complicated as many tutorials out there, it was just a wrong value in hardware.conf, that was created by lirc configuration tool.

---

### Post by btd3 on 2009-04-29
You may have already done this, but (based on personal experience) make sure your remote is working. If you have a digital camera, point your remote into the camera and push a button on the remote. If the remote is working it's infrared signal will be visible on the camera's screen.

During the lirc install using synaptic package manager a dialogue window asks you to "Select your custom event interface for your dev/input device." See if you have an option similar to "/dev/input/by-path/pci-0000:01:0a.0-event-ir" and choose that option. 

To choose a different event interface, it might be easiest for you to use synaptic to completely remove lirc and reinstall it. If you choose to completely remove lirc, during the reinstall you will see the remote and custom event interface dialogues again.

After the reinstall open a terminal and type "irw", then try your remote again. Lirc started automatically for me after it was installed.

---

### Post by diamondnular on 2009-04-29
> **lovinglinux said:**
> Try installing again, using the tutorial for Hardy.

OK. I tried to completely remove lirc and lirc-modules-sources. Then reinstall only lirc (following the instruction). Chose my remote (VLSystem Mplay Blast), none to Transmitter. Then edit hardware.conf to have *REMOTE_DEVICE="/dev/ttyUSB0"*. Restart lirc. irw still shows no output. *dmesg | grep -i lirc* shows nothing. 

Then I edited hardware.conf again, followed your above advice (REMOTE_MODULES and LOAD_MODULES), both two suggestions. Still irw no output. Dmesg still shows no output. It seems that some module was not loaded. How do I load it?

THanks,

D.

---

### Post by diamondnular on 2009-04-29
> **btd3 said:**
> You may have already done this, but (based on personal experience) make sure your remote is working. If you have a digital camera, point your remote into the camera and push a button on the remote. If the remote is working it's infrared signal will be visible on the camera's screen.

Interesting. I have a Nikon D40, and pointed my remote to it, press button. Nothing shows up in the screen of D40. Maybe I am too dump, but I wonder how the camera can capture any signal, if you do not press the camera button? In the other hand, if I have to press both remote's button and camera button to take a picture at the same time, then it is not easy job :(.

Anyway, my remote has a power button, and no matter that I have LIRC installed or not, pressing always give the Shutdown options. That means the remote works, right?

> **btd3 said:**
> During the lirc install using synaptic package manager a dialogue window asks you to "Select your custom event interface for your dev/input device." See if you have an option similar to "/dev/input/by-path/pci-0000:01:0a.0-event-ir" and choose that option.

Interesting. Why didnt I remember something similar? I may have to reinstall that again. 

> **btd3 said:**
> To choose a different event interface, it might be easiest for you to use synaptic to completely remove lirc and reinstall it. If you choose to completely remove lirc, during the reinstall you will see the remote and custom event interface dialogues again.

After the reinstall open a terminal and type "irw", then try your remote again. Lirc started automatically for me after it was installed.

Yes, I did use Synaptic to Completely remote LIRC and lirc-modules-source. Then I use terminal to install lirc only. And it does not help :(

---

### Post by diamondnular on 2009-04-29
> **btd3 said:**
> During the lirc install using synaptic package manager a dialogue window asks you to "Select your custom event interface for your dev/input device." See if you have an option similar to "/dev/input/by-path/pci-0000:01:0a.0-event-ir" and choose that option.

:confused: Hummmm... Why dont I see any similar option? It shows just the dialog to choose Remote and Tramsmitter, thats it. Weird! Am I missing something???

---

### Post by lovinglinux on 2009-04-29
> **diamondnular said:**
> :confused: Hummmm... Why dont I see any similar option? It shows just the dialog to choose Remote and Tramsmitter, thats it. Weird! Am I missing something???

I get the same options as you do.

---

### Post by diamondnular on 2009-04-29
OK, I come across LIRC homepage and found this

[http://www.lirc.org/html/table.html](http://www.lirc.org/html/table.html)

Way bottom of the table shows my remote system (VLSystem Mplay Blast), and it shows NONE for required lirc kernel modules. Does this mean I dont need any module to be loaded, and then dmesg | grep lirc shows no output?

Thanks,

D.

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> OK, I come across LIRC homepage and found this

[http://www.lirc.org/html/table.html](http://www.lirc.org/html/table.html)

Way bottom of the table shows my remote system (VLSystem Mplay Blast), and it shows NONE for required lirc kernel modules. Does this mean I dont need any module to be loaded, and then dmesg | grep lirc shows no output?

Thanks,

D.

We found at the same time. I was writing about the exact same thing. :)

I think it means you don't need to load the modules, but I don't know about the dmesg output, because I have to load lirc_dev but demesg gives me nothing.

Anyways,  let's try one more time with:
```

REMOTE_MODULES="false"

LOAD_MODULES="false"
```

Just to make sure, are you restarting lirc between the tests with the following command?

```
sudo /etc/init.d/lirc restart
```

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> I think it means you don't need to load the modules, but I don't know about the dmesg output, because I have to load lirc_dev but demesg gives me nothing.

Anyways,  let's try one more time with:
```

REMOTE_MODULES="false"

LOAD_MODULES="false"
```

Just to make sure, are you restarting lirc between the tests with the following command?

```
sudo /etc/init.d/lirc restart
```

Nope, still does not work. I also notice the output of mode2

```
$ mode2
mode2: Entering mplay_init()
mode2: readlink() failed for "/dev/lirc"
mode2: No such file or directory
mode2: Could not create the lock file
mode2: Could not create the lock file
```

and ls /dev gives

```
$ ls /dev | grep lir*
lircd
```

There is obviously no "/dev/lirc". But now I do have more problems: before ls /dev gave lirc0 and lircd, now it gives lircd only. What did I do to have lirc0? Maybe because I did some modprobe (lirc_dev or serial or i2c before)?

Thanks,

D.

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> There is obviously no "/dev/lirc". But now I do have more problems: before ls /dev gave lirc0 and lircd, now it gives lircd only. What did I do to have lirc0? Maybe because I did some modprobe (lirc_dev or serial or i2c before)?

Thanks,

D.

I don't have lirc0, just lircd and it works. But I use /dev/ttyS0 in the hardware.conf. The tty should redirect the thing, but some people use /dev/lirc0 directly.

You could try changing the device number from /dev/ttyUSB0 to /dev/ttyUSB1. Then restart lirc after changing the number and check if both lines of the output result is [OK]. If you select the wrong device, the output probably will be "fail". Also grep the output of daemon.log to see if there is any changes.

If this not work, change to /dev/ttyUSB2 and so on.

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> I don't have lirc0, just lircd and it works. But I use /dev/ttyS0 in the hardware.conf. The tty should redirect the thing, but some people use /dev/lirc0 directly.

You could try changing the device number from /dev/ttyUSB0 to /dev/ttyUSB1. Then restart lirc after changing the number and check if both lines of the output result is [OK]. If you select the wrong device, the output probably will be "fail". Also grep the output of daemon.log to see if there is any changes.

If this not work, change to /dev/ttyUSB2 and so on.

Actually i have only USB0 :(

```
$ ls /dev | grep ttyUSB*
ttyUSB0
```

What now??? :confused:

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Actually i have only USB0 :(

```
$ ls /dev | grep ttyUSB*
ttyUSB0
```

What now??? :confused:

Ok. Let's breath....and start all over again.

First purge lirc and install it again as you already have. Then check the time of last output in the daemon.log related to lirc so we can use it as starting point.  

Then run 

```
sudo /etc/init.d/lirc stop
```
```
sudo /etc/init.d/lirc start
```

and run 

```
cat /var/log/daemon.log | grep lirc
```

and post the output after the time of the last lirc output before purging it, so we can know exactly the output right now.

Then run irw and tell me if you simply get a new line in the terminal or if irw keeps waiting for the remote input. If it keeps waiting, press the remote keys and check if it gives any output.

---

### Post by diamondnular on 2009-04-30
Here you go:

```
$ cat /var/log/daemon.log | grep lirc
Apr 30 01:08:34 iQ9300 lircd-0.8.4a[9995]: lircd(mplay) ready
Apr 30 01:09:16 iQ9300 lircd-0.8.4a[9995]: caught signal
Apr 30 01:09:19 iQ9300 lircd-0.8.4a[10149]: lircd(mplay) ready
```

After irw, I get new line, with cursor at the beginning of the line

```
cuongkn@iQ9300:~$ irw


```

and pressing remote does not help to show anything. After irw, deamon.log shows one more line, and thats it.

```
Apr 30 01:09:19 iQ9300 lircd-0.8.4a[10149]: lircd(mplay) ready
Apr 30 01:11:49 iQ9300 lircd-0.8.4a[10149]: accepted new client on /dev/lircd
```

Thanks,

D.

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Here you go:

```
$ cat /var/log/daemon.log | grep lirc
Apr 30 01:08:34 iQ9300 lircd-0.8.4a[9995]: lircd(mplay) ready
Apr 30 01:09:16 iQ9300 lircd-0.8.4a[9995]: caught signal
Apr 30 01:09:19 iQ9300 lircd-0.8.4a[10149]: lircd(mplay) ready
```

After irw, I get new line, with cursor at the beginning of the line

```
cuongkn@iQ9300:~$ irw


```

and pressing remote does not help to show anything. After irw, deamon.log shows one more line, and thats it.

```
Apr 30 01:09:19 iQ9300 lircd-0.8.4a[10149]: lircd(mplay) ready
Apr 30 01:11:49 iQ9300 lircd-0.8.4a[10149]: accepted new client on /dev/lircd
```

Thanks,

D.

OK. This is a good start.

Now run

```
sudo /etc/init.d/lirc restart
```

An post what is the output. It should be something like this:

```
 * Stopping remote control daemon(s): LIRC                          [ OK ] 
 * Starting remote control daemon(s) : LIRC                         [ OK ]
```

Then run irw again an check if it gives nothing or waits for input. If it waits for input, test the remote.

---

### Post by lovinglinux on 2009-04-30
Oops, I forgot ...

Then post the output of the daemon log again.

---

### Post by diamondnular on 2009-04-30
Here you go

```
$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC 
```

and output of deamon.log

```
Apr 30 01:22:23 iQ9300 lircd-0.8.4a[10149]: caught signal
Apr 30 01:22:23 iQ9300 lircd-0.8.4a[10660]: lircd(mplay) ready
Apr 30 01:22:37 iQ9300 lircd-0.8.4a[10660]: accepted new client on /dev/lircd
```

irw-ing gives the same output like before, meaning one new line, and no output. It just hangs there until I Ctrl-C to terminate it.

Thanks,

D.

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Here you go

```
$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC 
```

and output of deamon.log

```
Apr 30 01:22:23 iQ9300 lircd-0.8.4a[10149]: caught signal
Apr 30 01:22:23 iQ9300 lircd-0.8.4a[10660]: lircd(mplay) ready
Apr 30 01:22:37 iQ9300 lircd-0.8.4a[10660]: accepted new client on /dev/lircd
```

irw-ing gives the same output like before, meaning one new line, and no output. It just hangs there until I Ctrl-C to terminate it.

Thanks,

D.

That is very good.

Run irw again and when it gives you a new line without any output, test your remote and see if any output appears on the terminal.

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Run irw again and when it gives you a new line without any output, test your remote and see if any output appears on the terminal.

Still no output. Irw acts like it did before :confused:

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Still no output. Irw acts like it did before :confused:

Post the output of daemon.log

When you run irw, does it give you this

```
cuongkn@iQ9300:~$ irw
```

or an empty line?

---

### Post by diamondnular on 2009-04-30
Here is daemon.log 

```
Apr 30 01:22:23 iQ9300 lircd-0.8.4a[10149]: caught signal
Apr 30 01:22:23 iQ9300 lircd-0.8.4a[10660]: lircd(mplay) ready
Apr 30 01:22:37 iQ9300 lircd-0.8.4a[10660]: accepted new client on /dev/lircd
Apr 30 01:22:45 iQ9300 lircd-0.8.4a[10660]: removed client
Apr 30 01:27:38 iQ9300 lircd-0.8.4a[10660]: accepted new client on /dev/lircd
```

When I did irw (irw, and then Enter), it went to new line (because of enter?) and then hung there until I kill it by Ctrl-C.

```
$ irw
^C
$ irw


```

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Here is daemon.log 

```
Apr 30 01:22:23 iQ9300 lircd-0.8.4a[10149]: caught signal
Apr 30 01:22:23 iQ9300 lircd-0.8.4a[10660]: lircd(mplay) ready
Apr 30 01:22:37 iQ9300 lircd-0.8.4a[10660]: accepted new client on /dev/lircd
Apr 30 01:22:45 iQ9300 lircd-0.8.4a[10660]: removed client
Apr 30 01:27:38 iQ9300 lircd-0.8.4a[10660]: accepted new client on /dev/lircd
```

When I did irw (irw, and then Enter), it went to new line (because of enter?) and then hung there until I kill it by Ctrl-C.

```
$ irw
^C
$ irw


```

OK. This is good. It means almost everything is working, but lirc is not capable of capturing the signal from the remote, which suggest the problem is the remote itself or the remote configuration, not the hardware.

Now post the content of 

/etc/lirc/lircd.conf
/usr/share/lirc/remotes/vlsystem/lircd.conf.mplay

---

### Post by diamondnular on 2009-04-30
/etc/lirc/lircd.conf

```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the VLSystem MPlay Blast remote:
include "/usr/share/lirc/remotes/vlsystem/lircd.conf.mplay"

#No default remote configuration was included for Custom
#You will need to include your own custom configuration for
#this transmitter, and file a bug at https://bugs.launchpad.net/ubuntu/+source/lirc/+filebug

```

/etc/lirc/hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="VLSystem MPlay Blast"
REMOTE_MODULES=""
REMOTE_DRIVER="mplay"
REMOTE_DEVICE="/dev/ttyUSB0"
REMOTE_LIRCD_CONF="vlsystem/lircd.conf.mplay"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

and lircd.conf.mplay

```
$ cat /usr/share/lirc/remotes/vlsystem/lircd.conf.mplay
#
# this config file was automatically generated
# using lirc-0.8.2(mplay) on Fri Dec  7 20:04:59 2007
#
# contributed by 
#
# brand:                       VLSystem
# model no. of remote control: MPlay Blast
# devices being controlled by this remote:
#

begin remote

  name  VLSystem_MPlay_Blast
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          211938
  toggle_bit_mask 0x0

      begin codes
          PwrOff                   0x41
          PwrOn                    0x55
          Movies                   0x40
          Television               0x46
          Photos                   0x45
          Music                    0x56
          1                        0x4d
          2                        0x4e
          3                        0x4f
          4                        0x50
          5                        0x51
          6                        0x52
          7                        0x53
          8                        0x03
          9                        0x07
          0                        0x4c
          Vol+                     0x0a
          Vol-                     0x0e
          Ch+_Lang                 0x12
          Ch-_Page                 0x16
          Guide                    0x0f
          Back                     0x0b
          Tv                       0x13
          Ok                       0x42
          Up                       0x19
          Left                     0x54
          Right                    0x43
          Down                     0x1d
          Exit_Click               0x1f
          Task_Quick               0x17
          Run_DClick               0x1b
          Rew                      0x0d
          Play                     0x09
          Ffwd                     0x15
          Prev                     0x1a
          Stop                     0x01
          Next                     0x1e
          Pause                    0x05
          Mute                     0x4a
          Warp_Mouse               0x47
          Rec                      0x11
          DVD_Zoom                 0x14
          Detail                   0x4b
      end codes

end remote
$ 

```

---

### Post by lovinglinux on 2009-04-30
Hang on. I'm analyzing the files.

---

### Post by diamondnular on 2009-04-30
By the way, what is your output of mode2? Mine showed

```
$ mode2
mode2: Entering mplay_init()
mode2: readlink() failed for "/dev/lirc"
mode2: No such file or directory
mode2: Could not create the lock file
mode2: Could not create the lock file

```

If you get different, then that is the problem. If not, then... well I dont know :(

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> By the way, what is your output of mode2? Mine showed

```
$ mode2
mode2: Entering mplay_init()
mode2: readlink() failed for "/dev/lirc"
mode2: No such file or directory
mode2: Could not create the lock file
mode2: Could not create the lock file

```

If you get different, then that is the problem. If not, then... well I dont know :(

Mine is 

```
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory
```

Run the irw again and press the remote Power button.

Check if there is any output on the terminal

Paste the output of daemon.log

---

### Post by diamondnular on 2009-04-30
Funny that you got *almost* the same as mine :)

> **lovinglinux said:**
> Run the irw again and press the remote Power button.

Check if there is any output on the terminal

Paste the output of daemon.log

Still no output with irw, no matter what button is.

```
$ irw
^C
$ 

```

daemon.log

```
Apr 30 02:00:55 iQ9300 lircd-0.8.4a[12078]: accepted new client on /dev/lircd
Apr 30 02:01:28 iQ9300 lircd-0.8.4a[12078]: removed client
```

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Funny that you got *almost* the same as mine :)



Still no output with irw, no matter what button is.

```
$ irw
^C
$ 

```

daemon.log

```
Apr 30 02:00:55 iQ9300 lircd-0.8.4a[12078]: accepted new client on /dev/lircd
Apr 30 02:01:28 iQ9300 lircd-0.8.4a[12078]: removed client
```


Run again 

```
sudo /etc/init.d/lirc restart
```

And check if the daemon.log gives you this:

```
Apr 30 01:09:16 iQ9300 lircd-0.8.4a[9995]: caught signal
Apr 30 01:09:19 iQ9300 lircd-0.8.4a[10149]: lircd(mplay) ready
```

If it does, then run irw again, but don't test the remote and don't hit CTRL+C. First check if the daemon.log gives you something like this:

```
Apr 30 01:11:49 iQ9300 lircd-0.8.4a[10149]: accepted new client on /dev/lircd
```

If it does, then go back to the irw terminal, hit the remote POWER button and check if anything appears on the terminal and if you get the logout window.

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Run again 

```
sudo /etc/init.d/lirc restart
```

And check if the daemon.log gives you this:

```
Apr 30 01:09:16 iQ9300 lircd-0.8.4a[9995]: caught signal
Apr 30 01:09:19 iQ9300 lircd-0.8.4a[10149]: lircd(mplay) ready
```

If it does, then run irw again, but don't test the remote and don't hit CTRL+C. First check if the daemon.log gives you something like this:

```
Apr 30 01:11:49 iQ9300 lircd-0.8.4a[10149]: accepted new client on /dev/lircd
```

Yes. Output

```
Apr 30 02:11:32 iQ9300 lircd-0.8.4a[12078]: caught signal
Apr 30 02:11:32 iQ9300 lircd-0.8.4a[12552]: lircd(mplay) ready
Apr 30 02:11:45 iQ9300 lircd-0.8.4a[12552]: accepted new client on /dev/lircd
```

> **lovinglinux said:**
> If it does, then go back to the irw terminal, hit the remote POWER button and check if anything appears on the terminal and if you get the logout window.

Shutdown (not logout) windows shows up, but nothing appears on terminal. It acts like it did before.

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Yes. Output

```
Apr 30 02:11:32 iQ9300 lircd-0.8.4a[12078]: caught signal
Apr 30 02:11:32 iQ9300 lircd-0.8.4a[12552]: lircd(mplay) ready
Apr 30 02:11:45 iQ9300 lircd-0.8.4a[12552]: accepted new client on /dev/lircd
```



Shutdown (not logout) windows shows up, but nothing appears on terminal. It acts like it did before.

Yay :popcorn:

It's working!!!!! Basically everything we did until now was useless, because the remote was working perfectly since the beginning. The problem is the keymap on your remote.

Run irw again, test the POWER button in the remote just to make sure it is working, then hit all other keys in the remote and check if there is any output in the terminal or if the computer responds to them.

Then we will configure your ~/.lircrc file.

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Yay :popcorn:

It's working!!!!! Basically everything we did until now was useless, because the remote was working perfectly since the beginning. The problem is the keymap on your remote.

How do you know that? Does that mean the lircd.conf.mplay is somehow incorrect?

> **lovinglinux said:**
> Run irw again, test the POWER button in the remote just to make sure it is working, then hit all other keys in the remote and check if there is any output in the terminal or if the computer responds to them.

Then we will configure your ~/.lircrc file.

Yes, Power still works, but all others button do not work. How do I configure ~/.lircrc? I think at least the computer should react to the button I press, right?

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> How do you know that? Does that mean the lircd.conf.mplay is somehow incorrect?

I know because the computer is responding to the POWER button. 

The situation is weird, because irw is not giving you any output, but the computer responds. So I guess the problem is with irw, not lircd.conf.mplay. But we will test this now.

> **diamondnular said:**
> Yes, Power still works, but all others button do not work. How do I configure ~/.lircrc? I think at least the computer should react to the button I press, right?

Run 

```
gedit ~/.lircrc
```

and paste the content of it here. If it is empty, the let me know.

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Run 

```
gedit ~/.lircrc
```

and paste the content of it here. If it is empty, the let me know.

Yes, its empty.

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Yes, its empty.

Paste this into the empty file and save it:

```
# edit the "button =" part for each entry according to your remote,
# and stick this stuff in ~/.lircrc

# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

#begin irexec

begin
    prog = irexec
    button = Play
    config = zenity --info --text "It works"
end
```

Now, restart lirc

```
sudo /etc/init.d/lirc restart
```

Then run this

```
irexec --daemon
```

Now hit the Play button and tell me if you get a message in the screen saying "It works"

---

### Post by lovinglinux on 2009-04-30
Ooops, I missed something...

The content of lircrc should be this

```
# edit the "button =" part for each entry according to your remote,
# and stick this stuff in ~/.lircrc

# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

#begin irexec

begin
    prog = irexec
    button = Play
    config = zenity --info --text "It works"
end

#end irexec
 
# ---------------
# MAIN END (irexec mode end)
# APP MODES BEGIN
# -------

```

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Paste this into the empty file and save it:

```
# edit the "button =" part for each entry according to your remote,
# and stick this stuff in ~/.lircrc

# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

#begin irexec

begin
    prog = irexec
    button = Play
    config = zenity --info --text "It works"
end
```

Now, restart lirc

```
sudo /etc/init.d/lirc restart
```

All done.

> **lovinglinux said:**
> Then run this

```
irexec --daemon
```

Now hit the Play button and tell me if you get a message in the screen saying "It works"

Nope :(. Nothing showed up.

```
$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
$ irexec --daemon
$ 

```

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> All done.



Nope :(. Nothing showed up.

```
$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
$ irexec --daemon
$ 

```

Run this in the terminal and tell me if the window show up or if you get an error in the terminal

```
zenity --info --text "It works"
```

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Run this in the terminal and tell me if the window show up or if you get an error in the terminal

```
zenity --info --text "It works"
```

Yes, "It works" Window showed up, no error!

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Yes, "It works" Window showed up, no error!

Ok. Hold on. I'm preparing a test lircrc file for all buttons. Meanwhile, do this:

Replace the  ~/.lircrc file content with this:

```

# edit the "button =" part for each entry according to your remote,
# and stick this stuff in ~/.lircrc

# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

#begin irexec

begin
    prog = irexec
    button = PwrOff
    config = zenity --info --text "PwrOff Button works"
end

begin
    prog = irexec
    button = PwrOn
    config = zenity --info --text "PwrOn Button works"
end

#end irexec
 
# ---------------
# MAIN END (irexec mode end)
# APP MODES BEGIN
# -------
```

Then restart lirc, then run

```
irexec --daemon
```

and check the daemon.log to see if you get any errors.

If everything looks fine, then hit the POWER Button again.

Check if instead of the logout screen you get a message saying that the button works.

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Ok. Hold on. I'm preparing a test lircrc file for all buttons. Meanwhile, do this:

Replace the  ~/.lircrc file content with this:

```

# edit the "button =" part for each entry according to your remote,
# and stick this stuff in ~/.lircrc

# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

#begin irexec

begin
    prog = irexec
    button = PwrOff
    config = zenity --info --text "PwrOff Button works"
end

begin
    prog = irexec
    button = PwrOn
    config = zenity --info --text "PwrOn Button works"
end

#end irexec
 
# ---------------
# MAIN END (irexec mode end)
# APP MODES BEGIN
# -------
```

Then restart lirc, then run

```
irexec --daemon
```

and check the daemon.log to see if you get any errors.

Nope, I got no error.

> **lovinglinux said:**
> If everything looks fine, then hit the POWER Button again.

Check if instead of the logout screen you get a message saying that the button works.

PowerOn does not show anything, PowerOff shows up Shutdown window (like normal), not the "PwrOff Button works" one.

Honestly, I still have the feeling that the remote (except the PwrOff button) is not recognized.

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Nope, I got no error.



PowerOn does not show anything, PowerOff shows up Shutdown window (like normal), not the "PwrOff Button works" one.

Honestly, I still have the feeling that the remote (except the PwrOff button) is not recognized.

Not necessarily. Please hold on 5 minutes. I need to find the proper code to test if it is only the POWER button that works or not.

Meanwhile, replace the ~/.lircrc with this:

```
# edit the "button =" part for each entry according to your remote,
# and stick this stuff in ~/.lircrc

# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

#begin irexec

begin
    prog = irexec
    button = PwrOff
    config = zenity --info --text "PwrOff Button works"
end

begin
    prog = irexec
    button = PwrOn
    config = zenity --info --text "PwrOn Button works"
end

begin
    prog = irexec
    button = Movies   
    config = zenity --info --text "Movies Button works"
end

begin
    prog = irexec
    button = Television
    config = zenity --info --text "Television Button works"
end

begin
    prog = irexec
    button = Photos
    config = zenity --info --text "Photos Button works"
end

begin
    prog = irexec
    button = Music 
    config = zenity --info --text "Music Button works"
end

begin
    prog = irexec
    button = 0
    config = zenity --info --text "Button 0 works"
end

begin
    prog = irexec
    button = 1
    config = zenity --info --text "Button 1 works"
end

begin
    prog = irexec
    button = 2
    config = zenity --info --text "Button 2 works"
end

begin
    prog = irexec
    button = 3
    config = zenity --info --text "Button 3 works"
end

begin
    prog = irexec
    button = 4
    config = zenity --info --text "Button 4 works"
end

begin
    prog = irexec
    button = 5
    config = zenity --info --text "Button 5 works"
end

begin
    prog = irexec
    button = 6
    config = zenity --info --text "Button 6 works"
end

begin
    prog = irexec
    button = 7
    config = zenity --info --text "Button 7 works"
end

begin
    prog = irexec
    button = 8
    config = zenity --info --text "Button 8 works"
end

begin
    prog = irexec
    button = 9
    config = zenity --info --text "Button 9 works"
end

begin
    prog = irexec
    button = Vol+
    config = zenity --info --text "Vol+ Button works"
end

begin
    prog = irexec
    button = Vol-
    config = zenity --info --text "Vol- Button works"
end

begin
    prog = irexec
    button = Ch+_Lang
    config = zenity --info --text "Ch+_Lang Button works"
end

begin
    prog = irexec
    button = Ch-_Page
    config = zenity --info --text "CCh-_Page Button works"
end

begin
    prog = irexec
    button = Guide
    config = zenity --info --text "Guide Button works"
end

begin
    prog = irexec
    button = Back
    config = zenity --info --text "Back Button works"
end

begin
    prog = irexec
    button = Tv 
    config = zenity --info --text "Tv Button works"
end

begin
    prog = irexec
    button = Ok 
    config = zenity --info --text "Ok Button works"
end

begin
    prog = irexec
    button = Up 
    config = zenity --info --text "Up Button works"
end

begin
    prog = irexec
    button = Left 
    config = zenity --info --text "Left Button works"
end

begin
    prog = irexec
    button = Right
    config = zenity --info --text "Right Button works"
end

begin
    prog = irexec
    button = Down
    config = zenity --info --text "Down Button works"
end

begin
    prog = irexec
    button = Exit_Click
    config = zenity --info --text "Exit_Click Button works"
end

begin
    prog = irexec
    button = Task_Quick
    config = zenity --info --text "Task_Quick Button works"
end

begin
    prog = irexec
    button = Run_DClick
    config = zenity --info --text "Run_DClick Button works"
end

begin
    prog = irexec
    button = Rew
    config = zenity --info --text "Rew Button works"
end

begin
    prog = irexec
    button = Play
    config = zenity --info --text "Play Button works"
end

begin
    prog = irexec
    button = Ffwd 
    config = zenity --info --text "Ffwd Button works"
end

begin
    prog = irexec
    button = Prev
    config = zenity --info --text "Prev Button works"
end

begin
    prog = irexec
    button = Stop
    config = zenity --info --text "Stop Button works"
end

begin
    prog = irexec
    button = Next
    config = zenity --info --text "Next Button works"
end

begin
    prog = irexec
    button = Pause 
    config = zenity --info --text "Pause Button works"
end

begin
    prog = irexec
    button = Mute
    config = zenity --info --text "Mute Button works"
end

begin
    prog = irexec
    button = Warp_Mouse
    config = zenity --info --text "Warp_Mouse Button works"
end

begin
    prog = irexec
    button = Rec
    config = zenity --info --text "Rec Button works"
end

begin
    prog = irexec
    button = DVD_Zoom
    config = zenity --info --text "DVD_Zoom Button works"
end

begin
    prog = irexec
    button = Detail
    config = zenity --info --text "Detail Button works"
end

#end irexec
 
# ---------------
# MAIN END (irexec mode end)

# APP MODES BEGIN
# ---------------
```

---

### Post by lovinglinux on 2009-04-30
Paste the output of 

```
irexec -v
```

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Not necessarily. Please hold on 5 minutes. I need to find the proper code to test if it is only the POWER button that works or not.

Meanwhile, replace the ~/.lircrc with this:

```
# edit the "button =" part for each entry according to your remote,
# and stick this stuff in ~/.lircrc

# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

#begin irexec

begin
    prog = irexec
    button = PwrOff
    config = zenity --info --text "PwrOff Button works"
end

begin
    prog = irexec
    button = PwrOn
    config = zenity --info --text "PwrOn Button works"
end

begin
    prog = irexec
    button = Movies   
    config = zenity --info --text "Movies Button works"
end

begin
    prog = irexec
    button = Television
    config = zenity --info --text "Television Button works"
end

begin
    prog = irexec
    button = Photos
    config = zenity --info --text "Photos Button works"
end

begin
    prog = irexec
    button = Music 
    config = zenity --info --text "Music Button works"
end

begin
    prog = irexec
    button = 0
    config = zenity --info --text "Button 0 works"
end

begin
    prog = irexec
    button = 1
    config = zenity --info --text "Button 1 works"
end

begin
    prog = irexec
    button = 2
    config = zenity --info --text "Button 2 works"
end

begin
    prog = irexec
    button = 3
    config = zenity --info --text "Button 3 works"
end

begin
    prog = irexec
    button = 4
    config = zenity --info --text "Button 4 works"
end

begin
    prog = irexec
    button = 5
    config = zenity --info --text "Button 5 works"
end

begin
    prog = irexec
    button = 6
    config = zenity --info --text "Button 6 works"
end

begin
    prog = irexec
    button = 7
    config = zenity --info --text "Button 7 works"
end

begin
    prog = irexec
    button = 8
    config = zenity --info --text "Button 8 works"
end

begin
    prog = irexec
    button = 9
    config = zenity --info --text "Button 9 works"
end

begin
    prog = irexec
    button = Vol+
    config = zenity --info --text "Vol+ Button works"
end

begin
    prog = irexec
    button = Vol-
    config = zenity --info --text "Vol- Button works"
end

begin
    prog = irexec
    button = Ch+_Lang
    config = zenity --info --text "Ch+_Lang Button works"
end

begin
    prog = irexec
    button = Ch-_Page
    config = zenity --info --text "CCh-_Page Button works"
end

begin
    prog = irexec
    button = Guide
    config = zenity --info --text "Guide Button works"
end

begin
    prog = irexec
    button = Back
    config = zenity --info --text "Back Button works"
end

begin
    prog = irexec
    button = Tv 
    config = zenity --info --text "Tv Button works"
end

begin
    prog = irexec
    button = Ok 
    config = zenity --info --text "Ok Button works"
end

begin
    prog = irexec
    button = Up 
    config = zenity --info --text "Up Button works"
end

begin
    prog = irexec
    button = Left 
    config = zenity --info --text "Left Button works"
end

begin
    prog = irexec
    button = Right
    config = zenity --info --text "Right Button works"
end

begin
    prog = irexec
    button = Down
    config = zenity --info --text "Down Button works"
end

begin
    prog = irexec
    button = Exit_Click
    config = zenity --info --text "Exit_Click Button works"
end

begin
    prog = irexec
    button = Task_Quick
    config = zenity --info --text "Task_Quick Button works"
end

begin
    prog = irexec
    button = Run_DClick
    config = zenity --info --text "Run_DClick Button works"
end

begin
    prog = irexec
    button = Rew
    config = zenity --info --text "Rew Button works"
end

begin
    prog = irexec
    button = Play
    config = zenity --info --text "Play Button works"
end

begin
    prog = irexec
    button = Ffwd 
    config = zenity --info --text "Ffwd Button works"
end

begin
    prog = irexec
    button = Prev
    config = zenity --info --text "Prev Button works"
end

begin
    prog = irexec
    button = Stop
    config = zenity --info --text "Stop Button works"
end

begin
    prog = irexec
    button = Next
    config = zenity --info --text "Next Button works"
end

begin
    prog = irexec
    button = Pause 
    config = zenity --info --text "Pause Button works"
end

begin
    prog = irexec
    button = Mute
    config = zenity --info --text "Mute Button works"
end

begin
    prog = irexec
    button = Warp_Mouse
    config = zenity --info --text "Warp_Mouse Button works"
end

begin
    prog = irexec
    button = Rec
    config = zenity --info --text "Rec Button works"
end

begin
    prog = irexec
    button = DVD_Zoom
    config = zenity --info --text "DVD_Zoom Button works"
end

begin
    prog = irexec
    button = Detail
    config = zenity --info --text "Detail Button works"
end

#end irexec
 
# ---------------
# MAIN END (irexec mode end)

# APP MODES BEGIN
# ---------------
```

I just replaced my old .lircrc file with your code, and tested with all buttons. All button, except PowerOff one, did not work.

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Paste the output of 

```
irexec -v
```

```
$ irexec -v
irexec 0.8.4a
```

---

### Post by lovinglinux on 2009-04-30
Sorry, I missed the previous post.

---

### Post by lovinglinux on 2009-04-30
Reboot the machine and test the remote again.

Don't forget to load irexec with:

```
irexec --daemon
```

---

### Post by markdavidoff on 2009-04-30
I had similar problems with my remote
(as i posted on the first page).

I figured out, that linux had native drivers for my remote interface, and it was responding to commands through it's drivers.

try removing lirc (complete removal using the GUI tool) and pressing the power button on the remote (I think i read that the power button on your remote responded?)
If it still responds to that, then lirc isn't actually interacting with the remote at all! Other buttons that may work without lirc are the volume buttons, and the numbers, if your remote has them.

Another point: mode2 will tell you if your remote is actually being handled by lirc. It will output in raw codes what it is receiving. If you need mode2 to read from a non-default /dev/lirc device, the syntax is:
```

mode2 --device=device
```

eg.

mode2 --device=/dev/lirc0

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> Reboot the machine and test the remote again.

Don't forget to load irexec with:

```
irexec --daemon
```

Yes, I actually did it when I tested the new .lircrc file with all buttons. Thats why it took me a little longer. Still no progress.

---

### Post by lovinglinux on 2009-04-30
> **markdavidoff said:**
> I had similar problems with my remote
(as i posted on the first page).

I figured out, that linux had native drivers for my remote interface, and it was responding to commands through it's drivers.

try removing lirc (complete removal using the GUI tool) and pressing the power button on the remote (I think i read that the power button on your remote responded?)
If it still responds to that, then lirc isn't actually interacting with the remote at all! Other buttons that may work without lirc are the volume buttons, and the numbers, if your remote has them.

Another point: mode2 will tell you if your remote is actually being handled by lirc. It will output in raw codes what it is receiving. If you need mode2 to read from a non-default /dev/lirc device, the syntax is:
```

mode2 --device=device
```

eg.

mode2 --device=/dev/lirc0

OMG :)

Is it possible that lirc does not respond because the remote input is intercepted by mode2?

---

### Post by diamondnular on 2009-04-30
> **markdavidoff said:**
> I had similar problems with my remote
(as i posted on the first page).

I figured out, that linux had native drivers for my remote interface, and it was responding to commands through it's drivers.

try removing lirc (complete removal using the GUI tool) and pressing the power button on the remote (I think i read that the power button on your remote responded?)
If it still responds to that, then lirc isn't actually interacting with the remote at all! Other buttons that may work without lirc are the volume buttons, and the numbers, if your remote has them.

Just did that. Completely uninstall lirc, and yes, the computer still responds to PowerOff button, but only that button. All others do not work.

> **markdavidoff said:**
> Another point: mode2 will tell you if your remote is actually being handled by lirc. It will output in raw codes what it is receiving. If you need mode2 to read from a non-default /dev/lirc device, the syntax is:
```

mode2 --device=device
```

eg.

mode2 --device=/dev/lirc0

Good point. I actually do not know how to run mode2. Now I got

```
$ mode2 --device=/dev/lircd
mode2: Entering mplay_init()
mode2: Could not open the serial port
mode2: Could not open the serial port
mode2: Entering mplay_deinit()
```

and also, if I tried with gnome-lirc-properties, and choose VLSystem, it downloaded file, and then crashed. Also, the list showed that the interface is USB-serial (UART) if I recall it correctly.

Any clues?

---

### Post by markdavidoff on 2009-04-30
> **lovinglinux said:**
> OMG :)

Is it possible that lirc does not respond because the remote input is intercepted by mode2?

Yes, that was the exact, and very confusing problem I was having.

---

### Post by diamondnular on 2009-04-30
> **lovinglinux said:**
> OMG :)

Is it possible that lirc does not respond because the remote input is intercepted by mode2?

Also, I do not have /dev/lirc nor /dev/lirc0. I just have /dev/lircd.

Anyway, how do I disable mode2? What actually is mode2?

---

### Post by markdavidoff on 2009-04-30
Ok, you are having the same problem I had.

The way i solved the problem was by building a serial IR receiver.

---

### Post by markdavidoff on 2009-04-30
> **diamondnular said:**
> Also, I do not have /dev/lirc nor /dev/lirc0. I just have /dev/lircd.

Anyway, how do I disable mode2? What actually is mode2?

Mode2 outputs the raw codes lirc is recieving. It is part of the lirc package.

The fact that your remote works without lirc means that lirc was never working in the first place. The drivers that came with linux might, in fact be interfering with lirc...which was my problem.

Build or buy a serial IR reciever.

---

### Post by diamondnular on 2009-04-30
> **markdavidoff said:**
> Mode2 outputs the raw codes lirc is recieving. It is part of the lirc package.

The fact that your remote works without lirc means that lirc was never working in the first place. The drivers that came with linux might, in fact be interfering with lirc...which was my problem.

How does mode2 is part of lirc, if I completely uninstall LIRC?

> **markdavidoff said:**
> Build or buy a serial IR reciever.

What do you mean by "build"? Build the driver, or what?

---

### Post by markdavidoff on 2009-04-30
> **diamondnular said:**
> How does mode2 is part of lirc, if I completely uninstall LIRC?

Mode2 should be uninstalled if lirc is uninstalled


> **diamondnular said:**
> What do you mean by "build"? Build the driver, or what?

No....physically build one.
[http://stuff.nekhbet.ro/2006/07/10/make-an-infrared-remote-control-for-pc.html](http://stuff.nekhbet.ro/2006/07/10/make-an-infrared-remote-control-for-pc.html)

This will also help:
[http://www.lirc.org/receivers.html](http://www.lirc.org/receivers.html)

---

### Post by lovinglinux on 2009-04-30
I'm not sure I can help any further. Lirc should be working. I have found other users with the same problem:

[http://ubuntuforums.org/showthread.php?t=495900](http://ubuntuforums.org/showthread.php?t=495900)

Anyways, if you manage to solve this puzzle, then you can configure ~/.lirrc to control specific applications through irexec.

You need to run ```
irexec --daemon
``` on start-up. You can do that by adding it to "System >> Preferences >> Startup Applications"

To understand how the lircrc file works, visit the link below:

[http://www.lirc.org/html/configure.html#lircrc_format](http://www.lirc.org/html/configure.html#lircrc_format)

To record input from the remote:

[http://www.lirc.org/html/configure.htm](http://www.lirc.org/html/configure.htm)

More about irexec

[http://www.lirc.org/html/irexec.html](http://www.lirc.org/html/irexec.html)

I think lirc is not broken and your configuration files seems to be fine. If you ever need to re-install lirc again after so many attempts, will be a piece of cake  ;)

Good luck.

---

### Post by diamondnular on 2009-04-30
> **markdavidoff said:**
> Mode2 should be uninstalled if lirc is uninstalled

Very interesting. I used Synaptic to uninstall LIRC, completely. But I still see another lib relating to LIRC called liblircclient0. Uninstall it will remove all my media applications. Maybe this lib is a built-in lirc you meant. 

After uninstalled LIRC, kept liblircclient0, I found that there is no /etc/init.d/lirc anymore, but run lircd still shows some errors (cant open or create /var/run/lircd.pid). Also mode2 still works. That means there IS another LIRC built-in. Good point.

> **markdavidoff said:**
> No....physically build one.
[http://stuff.nekhbet.ro/2006/07/10/make-an-infrared-remote-control-for-pc.html](http://stuff.nekhbet.ro/2006/07/10/make-an-infrared-remote-control-for-pc.html)

This will also help:
[http://www.lirc.org/receivers.html](http://www.lirc.org/receivers.html)

Ha ha, you overestimated me. I am not that genius to build one. But I wont give up. My system just worked fine a month ago with 8.10. There is no reason it will not work anymore in 9.04.

Since it is 4am now, and I have to work tomorrow, so I will be back tomorrow night to fight with my damn-but-sexy 9.04. Great appreciate to lovinglinux and markdavidoff to stay this long and help me :). 

Thanks,

D.

---

### Post by lovinglinux on 2009-04-30
> **diamondnular said:**
> Very interesting. I used Synaptic to uninstall LIRC, completely. But I still see another lib relating to LIRC called liblircclient0. Uninstall it will remove all my media applications. Maybe this lib is a built-in lirc you meant. 

After uninstalled LIRC, kept liblircclient0, I found that there is no /etc/init.d/lirc anymore, but run lircd still shows some errors (cant open or create /var/run/lircd.pid). Also mode2 still works. That means there IS another LIRC built-in. Good point.



Ha ha, you overestimated me. I am not that genius to build one. But I wont give up. My system just worked fine a month ago with 8.10. There is no reason it will not work anymore in 9.04.

Since it is 4am now, and I have to work tomorrow, so I will be back tomorrow night to fight with my damn-but-sexy 9.04. Great appreciate to lovinglinux and markdavidoff to stay this long and help me :). 

Thanks,

D.

You are welcome.

I have additional info from another user trying to configure another remote model.

[QUOTE=Lytse]Hi, I read a different thread in which you assume that a remote is working because the power button is pressed.

On my system this button also works but it is because that specific signal is hardwired towards the PW_SW signal on the motherboard. 

I can also start my system which is in power_off using the remote.

Greetings,

Lytse[/QUOTE]

Lytse also posted a link that suggests that the current lirc version needs to be patched to work properly with his remote. Check it out:

[http://ubuntuforums.org/showthread.php?t=1136697&page=3](http://ubuntuforums.org/showthread.php?t=1136697&page=3)

I don't know if this is the problem with your remote model and don't recommend following that instructions, because is specific for that remote. Anyways, let's wait to see if Lytse manages to fix lirc.

Good luck

---

### Post by btd3 on 2009-04-30
I'm not savvy enough to follow everything in this thread...but based on what your remote is doing I have one more suggestion. Install lirc again and in the Configuring Lirc dialogue choose "Linux input layer (/dev/input/eventX)" instead of your device. Then see if irw gives you any info when you press the remote's keys.

---

### Post by shabazzk on 2009-05-01
I've tried removing and reinstalling lirc, but I do NOT get the dialog again. I did the first time, but accidentally hit the enter key.

How do I start lirc setup dialog manually?

---

### Post by markdavidoff on 2009-05-01
"Completely remove" lirc using the GUI package manager

---

### Post by shabazzk on 2009-05-01
Do you mean check "Mark for Complete Removal?" But that looks like it will get rid of some dependencies that other programs need.

---

### Post by xc3RnbFO8P on 2009-05-01
Do:
> sudo dpkg-reconfigure lirc

---

### Post by shabazzk on 2009-05-08
> **Ringi said:**
> Do:

That's what I was looking for, but I didn't help fix the remote. I know the remote is install right cause I can power on the computer with it. But after the OS loads, the buttons don't do anything and I can't start irw as lircd is not loaded. 

I have reinstalled Ubuntu 9.04 AMD64, so I have a clean install. Will try lirc with any reasonable suggestions this weekend :popcorn:

Here is what I have [Antec Mult-Station Basic Internal IR receiver and remote]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811999191")

This is VERY frustrating, but I'm having a lot of fun:P

---

### Post by Gadgetman on 2009-05-10
I am having a similar problem in that my IR remote ("homebrew" Serial IR) worked fine with 8.10, now on a fresh install of 9.04, I cant get it to work! :confused:

It is a different remote but similar symptoms. I have followed this entire train of posts and done the equivalent commands but for my specific remote.

currently irw outputs nothing.

I have examined the daemon.log (as suggested), 
	cat /var/log/daemon.log | grep lirc
and get the following when I start irw:-
	May 10 21:20:06 pvr-test lircd-0.8.4a[2344]: caught signal
	May 10 21:20:06 pvr-test lircd-0.8.4a[11753]: lircd(default) ready
	May 10 21:20:26 pvr-test lircd-0.8.4a[11753]: accepted new client on /dev/lircd
So this looks "good"?
but no output from irw.

I have a question on mode2 output....I enter the following command:-
        mode2 --device=/dev/lirc0
and get a continuous stream of data (without pressing and buttons):-
  : 
space 637
pulse 354
space 693
pulse 344
space 690
pulse 353
space 633
pulse 422
space 686
pulse 358
space 645
pulse 420
space 684
pulse 346
  :
What does this indicate?

This is my hardware.conf:-
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

You may ask why I am running a hauppauge remote on a serial homebrew IR device? Well I have a separate frontend that I use the remote on. The actual hauppauge TV card is in the backend.

Hope someone can shed light on this issue....I have spent many hours on it. I still have the 8.10 build which is running fine with this remote and IR device, and I have compared config files and all the same....so I dont see why it shouldnt work!! :confused:

---

### Post by lovinglinux on 2009-05-10
Try replacing this

```
LOAD_MODULES="true"
```

with this

```

LOAD_MODULES="lirc_dev lirc_serial"
```

I don't know what else you can do. Lirc is apparently loading properly, but you have the same issue other people have. Nothing happens when testing with irw.

---

### Post by Gadgetman on 2009-05-10
> **lovinglinux said:**
> Try replacing this

```
LOAD_MODULES="true"
```

with this

```

LOAD_MODULES="lirc_dev lirc_serial"
```

I don't know what else you can do. Lirc is apparently loading properly, but you have the same issue other people have. Nothing happens when testing with irw.

Done!
No luck still the same.

---

### Post by Gadgetman on 2009-05-10
What is the significance of mode2 producing a continuous stream of data without any buttons being pushed? 

Shouldnt it be "silent" until a button is pushed?

---

### Post by lovinglinux on 2009-05-10
> **Gadgetman said:**
> What is the significance of mode2 producing a continuous stream of data without any buttons being pushed? 

Shouldnt it be "silent" until a button is pushed?

I have no idea. On Hardy, irw eventually captured some commands from the remote even if I didn't pushed any button. This problem disappeared without explanation tho.

---

### Post by xc3RnbFO8P on 2009-05-10
> I have no idea. On Hardy, irw eventually captured some commands from the remote even if I didn't pushed any button. This problem disappeared without explanation tho.
Could be your mouse or keyboard.
Mouse:
> rig@rig-desktop:~$ irw
111 0 BTN_RIGHT event5
110 0 BTN_LEFT event5
112 0 BTN_MIDDLE event5
Keyboard:
> rig@rig-desktop:~$ irw
73 0 KEY_VOLUMEUP event4
73 0 KEY_VOLUMEUP event4
72 0 KEY_VOLUMEDOWN event4
72 0 KEY_VOLUMEDOWN event4
69 0 KEY_LEFT event3
^[[D6a 0 KEY_RIGHT event3
^[[C67 0 KEY_UP event3
^[[A6c 0 KEY_DOWN event3
^[[Ba4 0 KEY_PLAYPAUSE event4
a5 0 KEY_PREVIOUSSONG event4
a3 0 KEY_NEXTSONG event4
a6 0 KEY_STOPCD event4

---

### Post by xzero1 on 2009-05-15
> **diamondnular said:**
> Very interesting. I used Synaptic to uninstall LIRC, completely. But I still see another lib relating to LIRC called liblircclient0. Uninstall it will remove all my media applications. Maybe this lib is a built-in lirc you meant. 

After uninstalled LIRC, kept liblircclient0, I found that there is no /etc/init.d/lirc anymore, but run lircd still shows some errors (cant open or create /var/run/lircd.pid). Also mode2 still works. That means there IS another LIRC built-in. Good point.



Ha ha, you overestimated me. I am not that genius to build one. But I wont give up. My system just worked fine a month ago with 8.10. There is no reason it will not work anymore in 9.04.

Since it is 4am now, and I have to work tomorrow, so I will be back tomorrow night to fight with my damn-but-sexy 9.04. Great appreciate to lovinglinux and markdavidoff to stay this long and help me :). 

Thanks,

D.

Lirc may not be built in but something similar seems to be there, at least for remotes that *use *the linux-input-layer. After doing a considerable amount of digging for an answer due to lack of and/or outdated documentation:shock:, I have found what appears to going on -- at least in my case. See [https://wiki.ubuntu.com/DesktopTeam/Specs/IRRemoteControlSupport.]("https://wiki.ubuntu.com/DesktopTeam/Specs/IRRemoteControlSupport") Where does this leave lirc? I don't know, it doesn't have any effect on my system even if I configure it with the linux-input-layer. It seems Ubuntu is moving on without us.

Update: (Got it working)

This is what I did. Completely removed lirc via synaptic. Installed gnome-lirc-properties. Selected "linux-input-layer" as remote and   "....event-ir" as interface. 

As a test, running irexec with a .lircrc file of

```
begin
    prog = irexec
    remote = linux-input-layer
        button = AUDIO
        repeat = 0
        config = echo "Hello world!"
end
``` worked for the first time when I pressed the 'AUDIO' button on my remote.:popcorn:

---

### Post by xzero1 on 2009-05-15
I am bumping this because updating the post does not put it back in the front of the queue and I have found some resolution on the issue.

---

### Post by lovinglinux on 2009-05-16
> **xzero1 said:**
> Update: (Got it working)

This is what I did. Completely removed lirc via synaptic. Installed gnome-lirc-properties. Selected "linux-input-layer" as remote and   "....event-ir" as interface. 

As a test, running irexec with a .lircrc file of

```
begin
    prog = irexec
    remote = linux-input-layer
        button = AUDIO
        repeat = 0
        config = echo "Hello world!"
end
``` worked for the first time when I pressed the 'AUDIO' button on my remote.:popcorn:

Interesting.

---

### Post by bgiannes on 2009-05-22
ok, i got my remote working...  irw returns the correct info

now i make a .lircrc file and put it into my home dir, one of the commands eg is

> # Play/Pause

begin

  prog = vlc

  remote = mceusb

  button = Play

  repeat = 2

  config = key-play-pause

end 

saved the file restart lirc....


but when i'm using VLC, the play button on the remote does nothing? if i test the remote again with irw it works?

what am i going wrong?

---

### Post by xc3RnbFO8P on 2009-05-22
This work for me in VLC (.lircrc):
```
begin vlc
	begin
		prog   = vlc
		button = power
		config = key-quit
	end
	begin
		prog   = vlc
		button = up
		config = key-nav-up
	end
	begin
		prog   = vlc
		button = left
		config = key-nav-left
	end
	begin
		prog   = vlc
		button = right
		config = key-nav-right
	end
	begin
		prog   = vlc
		button = down
		config = key-nav-down
	end
	begin
		prog   = vlc
		button = ok
		config = key-nav-activate
	end
	begin
		prog   = vlc
		button = mediacenter
		config = key-fullscreen
	end
	begin
		prog   = vlc
		button = book
		config = key-disc-menu
	end
	begin
		prog   = vlc
		button = vol-
		config = key-vol-down
	end
	begin
		prog   = vlc
		button = vol+
		config = key-vol-up
	end
	begin
		prog   = vlc
		button = mute
		config = key-vol-mute
	end
	begin
		prog   = vlc
		button = ch+
		config = key-next
	end
	begin
		prog   = vlc
		button = ch-
		config = key-prev
	end
	begin
		prog   = vlc
		button = time
		config = key-record
	end
	begin
		prog   = vlc
		button = stop
		config = key-stop
	end
	begin
		prog   = vlc
		button = play
		config = key-play
	end
	begin
		prog   = vlc
		button = pause
		config = key-pause
	end
	begin
		prog   = vlc
		button = rew
		config = key-slower
	end
	begin
		prog   = vlc
		button = ff
		config = key-faster
	end
	begin
		prog   = vlc
		button = back
		config = key-jump-medium
	end
	begin
		prog   = vlc
		button = next
		config = key-jump+medium
	end
end vlc

```

---

### Post by bgiannes on 2009-05-22
it still doesn't work....

here is the irw output eg...


> 000000037ff07bdd 00 OK mceusb
000000037ff07bdd 01 OK mceusb
000000037ff07be0 00 Down mceusb
000000037ff07be0 01 Down mceusb
000000037ff07be9 00 Play mceusb
000000037ff07be9 01 Play mceusb

here is the lirc.conf



> begin remote

  name        mceusb
  bits                 16
  flags  RC6|CONST_LENGTH
  eps                  30
  aeps                100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits        21
  pre_data        0x37FF0
  gap              105000
  toggle_bit           22
  rc6_mask    0x100000000


      begin codes

#unused by HP remote
	Blue	      0x00007ba1
	Yellow	      0x00007ba2
	Green	      0x00007ba3
	Red	      0x00007ba4
	Teletext      0x00007ba5

#ba6 - bae unused 
        BA6           0x00007ba6
        BA7           0x00007ba7
        BA8           0x00007ba8
        BA9           0x00007ba9
        BAA           0x00007baa
        BAB           0x00007bab
        BAC           0x00007bac
        BAD           0x00007bad
        BAE           0x00007bae

        Radio         0x00007baf
        Print         0x00007bb1

#bb2 - bb4 unused  
        BB2           0x00007bb2
        BB3           0x00007bb3
        BB4           0x00007bb4

        Videos        0x00007bb5
        Pictures      0x00007bb6
        RecTV         0x00007bb7
        Music         0x00007bb8
        TV            0x00007bb9

#bba - bbf unused 
        BBA           0x00007bba
        BBB           0x00007bbb
        BBC           0x00007bbc
        BBD           0x00007bbd
        BBE           0x00007bbe
        BBF           0x00007bbf
#bc1 - bca unused 
        BC1           0x00007bc1
        BC2           0x00007bc2
        BC3           0x00007bc3
        BC4           0x00007bc4
        BC5           0x00007bc5
        BC6           0x00007bc6
        BC7           0x00007bc7
        BC8           0x00007bc8
        BC9           0x00007bc9
        BCA           0x00007bca

        Eject         0x00007bcb
        SlideShow     0x00007bcc
        Visualization 0x00007bcd

#bce - bcf unused 
        BCE           0x00007bce
        BCF           0x00007bcf
#bd1 - bd7 unused 
        BD1           0x00007bd1
        BD2           0x00007bd2
        BD3           0x00007bd3
        BD4           0x00007bd4
        BD5           0x00007bd5
        BD6           0x00007bd6
        BD7           0x00007bd7

        Aspect        0x00007bd8
        Guide         0x00007bd9
        LiveTV        0x00007bda
        DVD           0x00007bdb
#NoGap
        Back          0x00007bdc
        OK            0x00007bdd
        Right         0x00007bde
        Left          0x00007bdf
        Down          0x00007be0
        Up            0x00007be1
#NoGap
        Star          0x00007be2
        Hash          0x00007be3
#NoGap
        Replay        0x00007be4
        Skip          0x00007be5
        Stop          0x00007be6
        Pause         0x00007be7
        Record        0x00007be8
        Play          0x00007be9
        Rewind        0x00007bea
        Forward       0x00007beb
#NoGap
        ChanDown      0x00007bec
        ChanUp        0x00007bed
        VolDown       0x00007bee
        VolUp         0x00007bef
#NoGap
        More          0x00007bf0
        Mute          0x00007bf1
        Home          0x00007bf2
        Power         0x00007bf3
#NoGap
        Enter         0x00007bf4
        Clear         0x00007bf5
#NoGap
        Nine          0x00007bf6
        Eight         0x00007bf7
        Seven         0x00007bf8
        Six           0x00007bf9
        Five          0x00007bfa
        Four          0x00007bfb
        Three         0x00007bfc
        Two           0x00007bfd
        One           0x00007bfe
        Zero          0x00007bff
      end codes

end remote

my .lirc file is the same as the one listed above...

what's wrong


update: oh and i'm running 9.04 amd64

---

### Post by ioio85 on 2009-05-24
Hi everybody,

I read a lot of comments and how-tos but I am still didn't fine the solution to my problem:
I have a Hauppauge 350 remote and an IR-Blaster on my serial port and I am running Kubuntu 9.04.

-> The remote work perfectly if I don't configure the  transmitter (i.e sudo dpkg-reconfigure lirc / Hauppauge HVR-1300 / none). irw, Mythtv... everything works

-> If I configure the transmitter as well (i.e sudo dpkg-reconfigure lirc / Hauppauge HVR-1300 / Serial Port (UART) : Motorola cable box) then I can tell that the transmitter is working by using this commmand
 ```
$ sudo irsend -d /dev/lircd1 SEND_ONCE DCT2000 POWER 
``` 
however irw doesn't return anything, only ```
$ sudo mode2 -d /dev/lirc0
``` return some value.

In addition I have ```
$ sudo cat /var/log/syslog | grep lirc
May 24 15:41:12 hal lircd-0.8.4a[10341]: failure connecting to localhost
May 24 15:41:12 hal lircd-0.8.4a[10341]: Connection refused

```

I found out that I could remove this connection failure message by replacing in my hardware.conf the name of the remote by Hauppauge_350 but then the mode2 doesn't work anymore

Here is my lircd.conf ```
[/#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge HVR-1300 remote:
include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

#Configuration for the Serial Port (UART) : Motorola Cable box transmitter:
include "/usr/share/lirc/transmitters/motorola/dctxxxx.conf"

```

and my hardware.conf
```
# /etc/lirc/hardware.conf                                                                                                                                   
#                                                                                                                                                           
#Chosen Remote Control                                                                                                                                      
REMOTE="Hauppauge HVR-1300"                                                                                                                                 
REMOTE_MODULES="lirc_dev lirc_i2c"                                                                                                                          
REMOTE_DRIVER=""                                                                                                                                            
REMOTE_DEVICE="/dev/lirc0"                                                                                                                                  
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"                                                                                                          
REMOTE_LIRCD_ARGS=""                                                                                                                                        

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_serial"           
TRANSMITTER_DRIVER=""                                
TRANSMITTER_DEVICE="/dev/lirc1"                      
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

Any help would be welcome. thanks in advance.

---

### Post by ioio85 on 2009-05-24
Nevermind I just needed to swap the 2 lines for the receiver and the transmitter in the lircd.conf. 

see the full detail here:
[http://ubuntuforums.org/showpost.php?p=5417214&postcount=11](http://ubuntuforums.org/showpost.php?p=5417214&postcount=11)

---

### Post by bgiannes on 2009-05-27
well.... others likely know this, but for lirc newbes like me, fyi.

Once lirc is up and working, ie irw is returning commands to get vlc and mplayer xine etc&#8230;. 

Each program needs a lirc plugin that needs to be turned on and/or install to accept RC commands. note, xine's lirc is on be default

Fyi for vlc once the plugin is on, (in the advanced menu under interfaces) it needs to be executed with this option:

> vlc &#8211;I lirc


mplayer's plugin just works once it's selected

for me full screen switch and pause does&#8217;t work in vlc but I&#8217;m on my way&#8230;

Now I&#8217;m working on elisa and amaork lirc configs/setups


fyi
i just got a Harmony 620 Universal Remote which is now setup to replace the gen RC-6 remote and my other component remotes, which works great



another thing, (correct if i'm wrong) there is a project to bring Lirc setup GUI to gnome

[http://live.gnome.org/gnome-lirc-properties]("http://live.gnome.org/gnome-lirc-properties")

it only seems to half work for me, but the "test" part of the gui does work, which is handy.

---

### Post by bgiannes on 2009-05-27
got elsia working w/ RC


elisa.config 

> [lirc.lirc_input:LircInput]
# the lirc deamon device
device = '/dev/lircd'
# Path to the file containing the lircmapping
input_map = '/home/bgiannes/.lirc/elisa.map'
lirc_rc = '/home/bgiannes/.lirc/elisa'

elisa.map

> mceusb 000000037ff07bed KEY_PAGE_UP
mceusb 000000037ff07bec KEY_PAGE_DOWN
mceusb 000000037ff07bf1 KEY_MUTE
mceusb 000000037ff07beb KEY_SEEK_FORWARD
mceusb 000000037ff07be7 KEY_PAUSE
mceusb 000000037ff07bdf KEY_GO_LEFT
mceusb 000000037ff07be4 KEY_PREVIOUS
mceusb 000000037ff07bdd KEY_OK
mceusb 000000037ff07bf2 KEY_MENU
mceusb 000000037ff07be1 KEY_GO_UP
mceusb 000000037ff07bde KEY_GO_RIGHT
mceusb 000000037ff07bef KEY_VOL_UP
mceusb 000000037ff07bdc KEY_EXIT
mceusb 000000037ff07bee KEY_VOL_DOWN
mceusb 000000037ff07be6 KEY_STOP
mceusb 000000037ff07bea KEY_SEEK_BACKWARD
mceusb 000000037ff07ba3 KEY_INC_PLAYBACK_SPEED
mceusb 000000037ff07be9 KEY_PLAY
mceusb 000000037ff07ba4 KEY_DEC_PLAYBACK_SPEED
mceusb 000000037ff07be5 KEY_NEXT
mceusb 000000037ff07bfa KEY_5
mceusb 000000037ff07bfb KEY_4
mceusb 000000037ff07bf8 KEY_7
mceusb 000000037ff07bf9 KEY_6
mceusb 000000037ff07bfe KEY_1
mceusb 000000037ff07bff KEY_0
mceusb 000000037ff07bfc KEY_3
mceusb 000000037ff07bfd KEY_2
mceusb 000000037ff07bf6 KEY_9
mceusb 000000037ff07bf7 KEY_8
mceusb 000000037ff07be0 KEY_GO_DOWN

elisa  lirc file

> begin
    remote = mceusb
    prog = elisa
    button = Play
    config = toggle_play_pause_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Right
    config = move_right_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = OK
    config = activate_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Power
    config = close_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Mute
    config = toggle_mute_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = VolDown
    config = decrement_volume_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Rewind
    config = seek_backward_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Stop
    config = stop_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Up
    config = move_up_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = VolUp
    config = increment_volume_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Down
    config = move_down_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Pause
    config = pause_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Enter
    config = activate_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Forward
    config = seek_forward_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Home
    config = toggle_menu_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Red
    config = toggle_fullscreen_key
    repeat = 0
    delay = 0.2
end

begin
    remote = mceusb
    prog = elisa
    button = Left
    config = move_left_key
    repeat = 0
    delay = 0.2
end

---

### Post by diamondnular on 2009-05-28
> **xzero1 said:**
> Update: (Got it working)

This is what I did. Completely removed lirc via synaptic. Installed gnome-lirc-properties. Selected "linux-input-layer" as remote and   "....event-ir" as interface. 

As a test, running irexec with a .lircrc file of

```
begin
    prog = irexec
    remote = linux-input-layer
        button = AUDIO
        repeat = 0
        config = echo "Hello world!"
end
``` worked for the first time when I pressed the 'AUDIO' button on my remote.:popcorn:

Sorry guys I have not caught up with the threads (why didn't I get the notification even I registered for it?). Anyway, what version of ubuntu do you have? Is it Jaunty 64? I have Jaunty 64 and gnome-lirc-properties crashes every time when I want to save or change the config. This is a known bug. Also, gnome-lirc-properties is just a GUI for LIRC, so if you know how to configure LIRC properly, you dont need it.

Back to my problem, I *kind of* solved the problem with the *funny* solution. Since gnome-lirc-properties crashes, I can not use it to control LIRC, so I have to manually edit config files. Installation on a virtual machine running 8.10 with gnome-lirc-properties without any problem, I found that I have to add something more in the config files:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="VLSystem MPlay Blast"
REMOTE_MODULES=""
REMOTE_DRIVER="mplay"
REMOTE_DEVICE="/dev/ttyUSB0"
REMOTE_LIRCD_CONF="vlsystem/lircd.conf.mplay"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="MPlay Blast"
REMOTE_VENDOR="VLSystem"
```
and then
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the VLSystem MPlay Blast remote:
include "/usr/share/lirc/remotes/vlsystem/lircd.conf.mplay"

#No default remote configuration was included for Custom
#You will need to include your own custom configuration for
#this transmitter, and file a bug at https://bugs.launchpad.net/ubuntu/+source/lirc/+filebug


# Configuration selected with GNOME LIRC Properties
include "/etc/lirc/lircd.conf.gnome"
```
where the lircd.conf.gnome is nothing more than just /usr/share/lirc/remotes/vlsystem/lircd.conf.mplay.

There is one more thing (IMPORTANT) I have to do in order to get my remote to work: when the system starts, and LIRC is up (I can see it on my LCD display), I HAVE TO press any button on my remote. It seems like doing that will make the remote to be active and then LIRC can see it, otherwise LIRC does not see the remote, then some program/service in the system get hold of controlling of the remote, and because of that, restart LIRC or what ever I do will not have any affection on the remote anymore.

Well, it's... stupid, but I am not sure others people with their remotes have to do the same thing or not, but at least, I got it to work and now I can control XBMC on my 40" HDTV nicely :).

D.

---

### Post by xzero1 on 2009-05-28
> Anyway, what version of ubuntu do you have? Is it Jaunty 64? I have Jaunty 64 and gnome-lirc-properties crashes every time when I want to save or change the config. This is a known bug. Also, gnome-lirc-properties is just a GUI for LIRC, so if you know how to configure LIRC properly, you dont need it.Yes, I use (AMD) Jaunty 64. Though gnome-lirc-properties does crash when I update the codes and won't save the configuraton; I only used it to verify basic operation. For control, I use customized  lircrc files based on codes reported through irw. It seems Ubuntu wants to treat the remote as "extended keycodes" for control. If anyone can find any current documentation on this, it would be most helpful.

---

### Post by diamondnular on 2009-06-02
> **xzero1 said:**
> Yes, I use (AMD) Jaunty 64. Though gnome-lirc-properties does crash when I update the codes and won't save the configuraton; I only used it to verify basic operation. For control, I use customized  lircrc files based on codes reported through irw.

I see. 

> **xzero1 said:**
> It seems Ubuntu wants to treat the remote as "extended keycodes" for control. If anyone can find any current documentation on this, it would be most helpful.

I highly second that. That's why each time my system boot, the remote gets hold and LIRC can not take control of it. Pressing the remote each time the system boot is annoying, but luckily we do not have to reboot our linux system as frequently as windows :).

---

### Post by bawolvesfan on 2009-06-05
Sorry if this is the wrong place but i havent been able to find my problem anywhere else... i have a fresh install of ubuntu, i ran all the updates, and i installed lirc through the add/remove programs thing. i'm trying to use a pinnacle hd tv pci card's built in ir receiver for boxee. for the initial config i left it at none for both receiver and transmitter. i open the infrared remote control properties window and notice a few things. at the bottom it says 

configuration test
Warning: Remote control daemon not running. cannot test buttons. this could be due to a configuration error. try changing the configuration. 


so i hit the autodetect button... it picks linux input device. i close the window. when i open the window back up its back how it was before and the configuration test still says the daemons not running. any ideas? also if i try to hit the update configuration files button it downloads all the stuff and then says

UPDATING REMOTE CONFIGURATION FILES
rejected send message, 1 matched rules;
type="method_call", sender=":1.49" (uid=1000 pid=3890 comm="/usr/bin/python /usr/bin/gnome-lirc-properties")
...

---

### Post by diamondnular on 2009-06-05
> **bawolvesfan said:**
> Sorry if this is the wrong place but i havent been able to find my problem anywhere else... i have a fresh install of ubuntu, i ran all the updates, and i installed lirc through the add/remove programs thing. i'm trying to use a pinnacle hd tv pci card's built in ir receiver for boxee. for the initial config i left it at none for both receiver and transmitter. i open the infrared remote control properties window and notice a few things. at the bottom it says 

configuration test
Warning: Remote control daemon not running. cannot test buttons. this could be due to a configuration error. try changing the configuration. 


so i hit the autodetect button... it picks linux input device. i close the window. when i open the window back up its back how it was before and the configuration test still says the daemons not running. any ideas? also if i try to hit the update configuration files button it downloads all the stuff and then says

UPDATING REMOTE CONFIGURATION FILES
rejected send message, 1 matched rules;
type="method_call", sender=":1.49" (uid=1000 pid=3890 comm="/usr/bin/python /usr/bin/gnome-lirc-properties")
...

Sorry I really dont understand your whole process. If lirc daemon does not run, you can run it by
```
$sudo /etc/init.d/lircd start
```
Other than that, what else do you want to do?

---

### Post by bawolvesfan on 2009-06-05
I did that and it didnt do anything. it says it may be a configuration error but when i try to change configuration stuff it gives me a rejected send message error.

---

### Post by bawolvesfan on 2009-06-06
so i went and tried that.( i thought i already had) and it says "command not found"

---

### Post by diamondnular on 2009-06-06
> **bawolvesfan said:**
> so i went and tried that.( i thought i already had) and it says "command not found"
My bad, it should read
```
sudo /etc/init.d/lirc restart
```
If you installed LIRC through apt, you should have it running already. If you installed LIRC from source, you will probably have to create init file for LIRC to start it.

Once you have LIRC started, you can try irw to see if LIRC recognize your remote or not. The whole process was described and discussed very details in other posts in this thread.

D.

---

### Post by ZardoZ84 on 2009-06-07
Hi. I'm a other guy wich a lirc problem in (k)ubuntu 9.04..

It's a more stupid problem. I have lirc working out of box which a mce remote, and I made a .lircrc file to launch apps, etc... But I like to get my remote to work like a mouse at my command. I made a valid lircmd.conf file, but now following Lirc docs, I need to modify my xorg.conf file.....

Well, my xorg.conf is like this : 

```

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"True"
EndSection
```

I add this but not works.
 
>  Put this section in your XF86Config-4 file to use the mouse in addition to your normal one.

Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/lircm"
        Option      "Protocol" "IntelliMouse"
        Option      "SendCoreEvents"
        Option      "Buttons" "5"
        Option      "ZAxisMapping" "4 5"
EndSection

And add a line to the ServerLayout section like this:

Section "ServerLayout"
        ...
        InputDevice    "LIRC-Mouse"           <-- add this line
EndSection

---

### Post by evaarties on 2009-06-18
Has someone succesfully managed to get the Dell Travel Remote working: 

[http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&cs=19&dl=false&l=en&s=dhs&docid=2E7A80DF0030F665E040A68F5B284ED5&doclang=en](http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&cs=19&dl=false&l=en&s=dhs&docid=2E7A80DF0030F665E040A68F5B284ED5&doclang=en)

I have one with my Dell Studio 17 (1737) which comes with an IT8512 CIR Receiver.

Any help would be appreciated.

---

### Post by usererror on 2009-06-19
Wow, this thread is insane.

I have a mceusb2 remote that sometimes works great, and then if i reboot, it totally dies, and then will randomly start working again. All of this started when I updated to 9.04.

I'm seriously tempted to reload 8.04, because my video card is apparently not support anymore either in 9.04 as well. I can get it working but if i reboot, it breaks again.

---

### Post by darklord on 2009-06-21
I also had problems with mine remote (for jaunty - ubuntu 9.04), i found a partial fix for gnome-lirc-properties see message 4, this resolve a known bug - hope this helps but i still have to setup gnome-lirc-properties after rebooting.

[http://ubuntuforums.org/showthread.php?p=7492230#post7492230]("http://ubuntuforums.org/showthread.php?p=7492230#post7492230")

:D:D

---

### Post by a6s0lu7 on 2009-06-22
Hello everybody, im trying to setup lirc in mythbuntu 9.04 and im stuck with it.

From reading this thread heres what i got so far:

This is my hardware.conf:

> 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Prolink Pixelview PV-BT878P+ (Rev.4C8E card"
REMOTE_MODULES="false"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="pixelview/lircd.conf.playtv_pro"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""



if i type:
sudo /etc/init.d/lirc start

i get:
* Starting remote control daemon(s) : LIRC                                                                   [OK] 

In the logs:
cat /var/log/daemon.log | grep lirc

i get:
Jun 22 15:48:39 a6s-srv lircd-0.8.4a[5273]: lircd(default) ready

then i start irw

i check logs again and i get:

Jun 22 15:51:00 a6s-srv lircd-0.8.4a[5273]: accepted new client on /dev/lircd
Jun 22 15:51:00 a6s-srv lircd-0.8.4a[5273]: could not get file information for /dev/lirc0
Jun 22 15:51:00 a6s-srv lircd-0.8.4a[5273]: default_init(): No such file or directory 
Jun 22 15:51:00 a6s-srv lircd-0.8.4a[5273]: Failed to initialize hardware


in /dev dir theres isnt a /dev/lirc0 only a /dev/lirc

Ill appreciate every help u can give me as im clueless on how to continue.

Many thanks

---

### Post by fillintheblanks on 2009-06-22
I am not sure if this applies to you. but in mine I had to type **cat /proc/bus/input/devices**

this gave me

> I: Bus=0001 Vendor=107d Product=6606 Version=0001
N: Name="bttv IR (card=34)"
P: Phys=pci-0000:01:06.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:06.0/input/input4
U: Uniq=
H: Handlers=kbd **event4** 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010007 80000190 4801 1e0000 4400 100000 10000ffc

make note of 'event4'

so in my hardware.conf I change > REMOTE_DEVICE="/dev/lirc0"
to REMOTE_DEVICE="/dev/input/event4". maybe you have something similar?

---

### Post by a6s0lu7 on 2009-06-22
Hi, ive done as u sugested, did 

cat /proc/bus/input/devices

got:

> I: Bus=0001 Vendor=109e Product=036e Version=0001
N: Name="bttv IR (card=70)"
P: Phys=pci-0000:01:00.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:01:00.0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=100003
B: KEY=2c0814 100004 0 0 0 4 2008000 2090 2001 1e0000 4400 0 ffc


After i went to /etc/lirc/hardware.conf, and  replaced 
REMOTE_DEVICE="/dev/lirc0"
with
REMOTE_DEVICE="/dev/input/event5"

after restarting lirc daemon i runed irw and in logs was:

> 
Jun 23 03:09:25 a6s-srv lircd-0.8.4a[3730]: accepted new client on /dev/lircd
Jun 23 03:09:25 a6s-srv lircd-0.8.4a[3730]: could not get hardware features
Jun 23 03:09:25 a6s-srv lircd-0.8.4a[3730]: this device driver does not support the new LIRC interface
Jun 23 03:09:25 a6s-srv lircd-0.8.4a[3730]: major number of /dev/input/event5 is 13
Jun 23 03:09:25 a6s-srv lircd-0.8.4a[3730]: LIRC major number is 61
Jun 23 03:09:25 a6s-srv lircd-0.8.4a[3730]: check if /dev/input/event5 is a LIRC device
Jun 23 03:09:25 a6s-srv lircd-0.8.4a[3730]: Failed to initialize hardware


Any more clues??:confused:

---

### Post by nedmar on 2009-07-09
> **lovinglinux said:**
> Sometimes the solution is easier than we think. I almost gave up on lirc, but one day I tried to do it again and found the solution. It wasn't so complicated as many tutorials out there, it was just a wrong value in hardware.conf, that was created by lirc configuration tool.

Hehe.. i remember [[COLOR="Red"]when that happened[/COLOR]]("http://ubuntuforums.org/showthread.php?t=979702") :) i was trying to solve the same problem the people here is still trying. I also gave up trying to figure out on my own how to make it work. However i'm still looking for a solution .. so.. here i am :)

---

### Post by LilYoda on 2009-07-14
Heya

For those that have remotes not fully supported by lirc, you can try following what I did to make my "el cheapo" remote works

mode2 didn't work, so I had to use lircd with debug mode to analyze everything the devinput module was receiving, then rebuild all the files from scratch :mad:

Link here: [http://ubuntuforums.org/showthread.php?t=805876](http://ubuntuforums.org/showthread.php?t=805876)

---

### Post by anonymtrk on 2009-10-08
Hello,

I have installed the lirc packages and under system menu i have got "Infrared Remote Control" now. I  start it, auto-detect the device, it finds. But when i press "Update" button for configuration files, i got the following message. 

[IMG]http://img515.imageshack.us/img515/8321/screenshotxo.png[/IMG]

Or, another solution, can anyone help me to work the infrared device of HP Pavilion dv6 1220st.

p.s: i tried all you said but can not work it.

---

### Post by pezlin on 2009-10-20
Hi!
 
I installed Ubuntu 9.10 Karmic yesterday and can not get the vlsystem mplay blast remote to work as it did in Ubuntu 9.04. I have done the same setup adding /dev/ttyUSB0 to REMOTE_DEVICE in hardware.conf file but still no reaction when using irw and pressing a button on the remote. I have restarted and reinstalled lirc a couple of times but no result. I have understood that lirc comes in version 0.8.6 in Ubunt 9.10 but I don't know if it is problem in this version of Lirc or in Ubuntu 9.10. Does anyone else has the same problem?

---

### Post by lovinglinux on 2009-10-20
> **pezlin said:**
> Hi!
 
I installed Ubuntu 9.10 Karmic yesterday and can not get the vlsystem mplay blast remote to work as it did in Ubuntu 9.04. I have done the same setup adding /dev/ttyUSB0 to REMOTE_DEVICE in hardware.conf file but still no reaction when using irw and pressing a button on the remote. I have restarted and reinstalled lirc a couple of times but no result. I have understood that lirc comes in version 0.8.6 in Ubunt 9.10 but I don't know if it is problem in this version of Lirc or in Ubuntu 9.10. Does anyone else has the same problem?

I have a serial remote, not USB, but this is what I do on a fresh install:

1) When installing Lirc I choose to not configure the remote
2 ) I replace the contents of /etc/lirc from a backup
3)  I replace the contents of /usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv from a backup
4) reboot

It works all the time. Sometimes I have to restart lirc with **sudo /etc/init.d/lirc restart**.

---

### Post by pezlin on 2009-10-20
> **lovinglinux said:**
> I have a serial remote, not USB, but this is what I do on a fresh install:
 
1) When installing Lirc I choose to not configure the remote
2 ) I replace the contents of /etc/lirc from a backup
3) I replace the contents of /usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv from a backup
4) reboot
 
It works all the time. Sometimes I have to restart lirc with **sudo /etc/init.d/lirc restart**.
 
Thank you for your help! I have tried as you suggested but unfortunately without any success.I am a noob in Linux so I don't know why I have REMOTE_DEVICE=/dev/ttyUSB0 just something I read and it has been working until after the update to Karmic. 
 
If I check the daemon.log I can see the following that might be a reason but I don't know if it is and if so how to solve it.
 
Oct 20 15:07:24 htpc modem-manager: (ttyUSB0) closing serial device...
 
Otherwise it looks ok
Oct 20 15:09:00 htpc lircd-0.8.6[1014]: caught signal
Oct 20 15:09:01 htpc lircd-0.8.6[2006]: lircd(mplay) ready, using /var/run/lirc/lircd
Oct 20 15:09:03 htpc lircd-0.8.6[2006]: accepted new client on /var/run/lirc/lircd
 
Do you have any other suggestions?
 
EDIT: I tried to uninstall modemmanager but it didn't help. The message in daemon.log diappeared but no change when using irw. I also noticed in dmesg.log that there was a post stating something about connecting USB to ttyUSB.

---

### Post by skolchin on 2009-10-24
Well, I couldn't make it work under karmic. 

I've got Streamzap remote, mode2 works well, irrecord - too, but 
irexec/irw - not at all.

.lircrc exists (generated by mythbuntu), but even custom config doesn't help:

> skolchin@kol-srv:~$ irexec a.conf &
> [1] 8777
> skolchin@kol-srv:~$ irw
> ^C
> skolchin@kol-srv:~$

where a.conf is:

# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

#begin irexec

begin
    prog = irexec
    button = 1
    config = zenity --info --text "It works"
end

#end irexec
 
Nope, it doesn't work for "1" or any other button.

I can't change REMOTE_DEVICE to ttyUSB0 because I don't have it in /dev. Also, I don't have eventX for the remote so I've to stay with /dev/lirc0

So, I believe I tried anything suggested in this thread and still no luck. Is there anything else I could do?

---

### Post by skolchin on 2009-10-25
Guys, I've made it!
This is what I did:

In another discussion I found that I could run lircd with -n flag so it will remain in foreground and display all logs to console, so I stopped the daemon and run:

sudo lircd --device=/dev/lirc0 -n

Immediatelly after that irexec/irw began to work! But, when I killed lircd and started the service normally, everything stopped working again.

After some analysis I found the reason - it was in **REMOTE_LIRCD_ARGS="''"** line in hardware.conf, which was provided by default. This '' stuff is been added to lircd command line, so lircd consider it as configuration file location and, of course, did not look into normal lircd.conf!

So, I commented out 2 lines in /etc/lirc/hardware.conf:

#REMOTE_LIRCD_CONF="''" 
#REMOTE_LIRCD_ARGS="''"

and the service started working properly.

But it was really hard... Isn't it a bug? May be I shall report it to the bugtracker?

---

### Post by pezlin on 2009-10-25
> **skolchin said:**
> Guys, I've made it!
This is what I did:

In another discussion I found that I could run lircd with -n flag so it will remain in foreground and display all logs to console, so I stopped the daemon and run:

sudo lircd --device=/dev/lirc0 -n

Immediatelly after that irexec/irw began to work! But, when I killed lircd and started the service normally, everything stopped working again.

After some analysis I found the reason - it was in **REMOTE_LIRCD_ARGS="''"** line in hardware.conf, which was provided by default. This '' stuff is been added to lircd command line, so lircd consider it as configuration file location and, of course, did not look into normal lircd.conf!

So, I commented out 2 lines in /etc/lirc/hardware.conf:

#REMOTE_LIRCD_CONF="''" 
#REMOTE_LIRCD_ARGS="''"

and the service started working properly.

But it was really hard... Isn't it a bug? May be I shall report it to the bugtracker?
My hardware.conf file did not have this " so uncomment this line did not do anything.

---

### Post by h3nk3 on 2009-11-02
Any clue anyone???  How to get it work under 9.10 with vl-system-mplay.I´ve got it to work under 9.04 after a few ours but now we are speaking days of no luck!!!!!!!!!!

---

### Post by Sumbaev on 2009-11-04
I have the same problem - after update Jaunty ->Karmic lirc stopped woking.
(I also use Vlsystem Mplay Blast integrated in Zalman HD135 case)

What I managed to do:
1. Erase hardware.conf and create a new one consisting only of of two strings
     REMOTE_DEVICE=/dev/ttyUSB0
     REMOTE_DRIVER=mplay
NOTE: no quotes are needed
2. Substitude lircd.conf with origianal lircd.conf.mplay (i got it from svn version)

3. SWITCH the computer OFF! Reboot won't sort it!
4. Switch it on and check irw.

It worked for me, however if I do a reboot lirc stops working untill the computer is switched off completely. I guess the bug is in how program terminates, but I don't know if it is in kernel or in Lirc

---

### Post by h3nk3 on 2009-11-04
Where did you find the original lircd.conf.mplay. You said from svn.....any links pleasy!!!!

---

### Post by Sumbaev on 2009-11-04
You can find instructions at [www.lirc.org](www.lirc.org) in left menu on main page. 
It is not necessary to use that file. I did so to be sure that codes of buttons are correct.
I thought that the problem was with those codes because lirc and irw started normally, but irw didn't show any results as if I used wrong remote.

---

### Post by Sumbaev on 2009-11-04
Things are even more wierd. Seems it is working/not working not only after off/reboot, but every second time or so.

After several tests I can say it is more connected to the way you shut down or reboot. When I use usual Ububntu way (Panel button (Opens dialog) -> Shutdown (Reboot)-> Confirm (and thats it)) It makes lirc useless next boot.
But when I do SUDO REBOOT (SUDO SHUTDOWN) or if I do it via XBMC on/off dialog it works perfect.

I will try to test it several more times to doublecheck this clue. So far if it works this way I will just change the button on a panel untill they will post a fix for kernel (lirc)

---

### Post by h3nk3 on 2009-11-10
Any progress for you with vlsystem config.

many people in the world waits for a sollution

Best regards / Henrik

---

### Post by niko2 on 2009-11-12
Hello,

I was suffering no IR signal from my mplay blast device
after testing under windows, I realize than device is initialized by software.
Since kernel does not deal with that and lirc is only intended to catch IR signals, I look at LCDproc.
It was working for me after patching it, following this (nearly) very good howto
[http://xbmc.org/forum/showthread.php?p=311796](http://xbmc.org/forum/showthread.php?p=311796)

Then, I came back to LCdproc and readthe patch for mplay (in order to get an idea about how to initialize the IR receiver)

finally, the solution was to set an option in LCDd.conf !!!
this is "keypad" which need to be enabled

so, then, for me, everything is working.

I am running Ubuntu 9.10

---

### Post by Sumbaev on 2009-11-27
It seems one of packets which was updated after the release of 9.10 fixed the problem.
For me it worked after really "cold restart" when I even unplugged the PC to make VFD off.

After that I changed config files as written before and it worked. Adding option KEYPAD works fine as well.

Hope it is finally solved

---

### Post by jmadero on 2009-12-03
Has anyone successfully gotten the IR on the studio 15-17 working? I bought a remote that came with a USB IR, works great but I'd like to be able to just use the internal and not have to have the USB plugged in...

---

### Post by thecapsaicinkid on 2009-12-28
I am also having trouble with my Mplay Blast remote (Zalman HD135 case)

I'm not even sure how I broke it, Lirc/LCDproc were both working fine under Karmic, both older versions built from source.

I decided to upgrade LCDproc to the Karmic package and remove my built one (mythtv needed a newer version) Anyway, install both LCDproc and Lirc from Ubuntu repos and while LCDproc works fine I cannot get anything from the remote.

The IR portion of the VFD doesn't seem to be even working at the lowest level so it's not a lirc issue. The FTDI usb to serial driver loads creating /dev/ttyUSB0 which allows stuff to be sent to the VFD via LCDproc but absolutely nothing from the remote side.

What's really odd is the little red led for the IR is permanently lit from boot, I can't remember if it did this before until the software loaded. It's like the device has been put in an invalid state and won't return to normal even after a full power off, unless of course it is a physical hardware fault.

I've tried cat'ing the /dev/ttyUSB0, nothing. Lirc will load as per normal but obviously receives no commands.

Any ideas?
```

dmesg | grep ftdi
[    7.933309] ftdi_sio 2-9:1.0: FTDI USB Serial Device converter detected
[    7.935089] usbcore: registered new interface driver ftdi_sio
[    7.935092] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver

```Thanks

---

### Post by thecapsaicinkid on 2010-01-06
Well I've solved the issue but I am utterly confused what the problem was.

I booted an XP virtual machine in VirtualBox and enabled the Mplay USB device for the guest OS and installed the windows drivers from the Zalman CD download. Now, the serial driver installed fine but the Zalman software couldn't find the device BUT eventually the IR LED went out (flicking on with each button push as before) and after rebooting the remote functioned as before with LIRC

How can the device get into such a state that isn't reset with a long power off and what put it into this state in the first place??


Thanks

---

### Post by giantpopples on 2010-03-04
Hi !

I'm also trying to get the vlsystem display fully working under Karmic (I'm using XBMC Live, based on karmic).

Following the different guides, i managed to get the remote recognized by lirc (and vfd by lcdproc but that was easier). 
thecapsaicinkid comment helped me a lot, i'm running a dual boot with windows, and at first the ir led was also always on (which is the default state when plugging the display - at least for me).. :confused:

Under windows, the vfd/ir programs initiates the device, and the led stops, the ir signal is then recognized. When the program ends, the led is back on. This is mandatory to use the remote to wake up the pc (cause it is acting as the power button). This was confirmed on this site : [http://zalman.ostergaard.net/lirc.html]("http://zalman.ostergaard.net/lirc.html")

But i can't get it to work under linux... If the led is on on boot, it stays and i can't use my remote, if it's off, i can use my remote but can't wake my pc up :(

The keypad=yesoption in LCDd.conf doesn't seem to change anything, do i have to add some config for the keypad? Or configure LCDProc in a special way to really enable it ?

Thanks for your help !

PS: To go from ir LED ON/OFF, i go under windows, launch the VFD/IR program, the LED stops, then i manually kill the process and reboot, not a very good solution indeed..

i use a VLSys M-play 202Plus R2, which is a m-play blast without fan control

---

### Post by thecapsaicinkid on 2010-03-04
Hiya Giantpopples,


I have both Lirc and LCDproc working with the HD-135 case BUT every once in a while (I think if the machine is powered off without giving the either Lirc or LCDd a chance to shutdown properly) I get into the situation where the light is on permanently and the remote stops functioning.

At this point I have to kill both Lirc and LCDd, boot up my XP vm and run the Zalman 'something centre' program which attempts to detect the display. I usually also for some strange reason have to disconnect/connect the usb zalman display from the virtual machine (by un-re-ticking the device at the top) while it is detecting to actually get it to see the device. This will turn the light off and I can start Lirc up and it works again.

Just to note, my light is OFF from turning the machine on if everything is working correctly, if the light gets stuck on it's on permanently from cold boot even until I do the above in my vm!

I believe the power button works to power on/off the machine even if lirc isn't working properly (the command is still recognised for some reason, read this somewhere) which is what you might be seeing.

---

### Post by giantpopples on 2010-03-04
Thanks for your reply !

It's odd that in your case the light is off when you power the display...

Do you manage to wake up the PC (from standby or shutdown) with the remote ?

For me, if the IR Led is on, i can wake up the PC (it acts just like the power on button on the PC case), if it's off, the LED blink, so it receives the signal but i doesn't do anything on the PC since it is on standby/shutdown... 

I try to enable USB devices as acpi wake up events but it didn't change anything...

Thanks for your help anyway !

---

### Post by thecapsaicinkid on 2010-03-04
There's a thread on these boards where some guy had the same problem as you (I'm not sure if he said the light was lit) His remote wasn't passing anything at all to the serial port (i.e /dev/ttyUSB0) so Lirc obviously didn't work BUT the power button did still function (not sure how or why, it obviously isn't going through lirc)

I don't use the power button so not sure what it actually does, it seems to work outside of the whole /dev/tty -> lirc scenario.


I really don't understand how when it goes 'wrong' my ir light can stay lit even after leaving the machine powered off and unplugged!! It lights as soon as power goes to the machine whereas if it's working properly the light is off from boot and only lights with a keypress.

I'm sure Lirc or LCDproc is putting the display in an invalid state but I don't understand how that can persist with no power. It only started happening when I switched versions of both pieces of software.

---

### Post by giantpopples on 2010-03-04
I came across several information on the mediaportal forum, and on a dedicated topic i read that some data must be sent to the VFD in order to use the ir to act like a poweroff button.

Those datas are in hex format (0xAE 0xAE, 0xA4 0x7E..), but i don't know how to send this to my VFD to test if it could work...

Here is the link : 
[http://forum.team-mediaportal.com/219437-post71.html]("http://forum.team-mediaportal.com/219437-post71.html")

There are many more information on the topic for those who can understand it, unfortunately i don't quite do ;)..

---

### Post by thecapsaicinkid on 2010-05-08
> **giantpopples said:**
> I came across several information on the mediaportal forum, and on a dedicated topic i read that some data must be sent to the VFD in order to use the ir to act like a poweroff button.

Those datas are in hex format (0xAE 0xAE, 0xA4 0x7E..), but i don't know how to send this to my VFD to test if it could work...

Here is the link : 
[http://forum.team-mediaportal.com/219437-post71.html](http://forum.team-mediaportal.com/219437-post71.html)

There are many more information on the topic for those who can understand it, unfortunately i don't quite do ;)..
I've filed a bug.

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/574432](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/574432)

---

