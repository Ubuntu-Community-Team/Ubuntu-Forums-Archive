---
title: "Pulseaudio and Jackd working fine."
date: 2008-07-30
forum: Multimedia Software
---

### Post by neltnerb on 2008-07-30
I seem to no longer be able to post on the forums in the original thread, and I don't have the patience to figure out why, so I'll post the solution as a new thread.

I was correct that the order of loading is screwing it up. Pulseaudio is loading before jackd, so it doesn't become aware of the device. The following steps worked very easily for me to make it work (5 minutes to set up), but I don't know how to automate it to happen on startup because I don't understand the ubuntu conventions for startup scripts.

First, install pulseaudio-module-jack from debian sid.

[http://packages.debian.org/sid/i386/pulseaudio-module-jack/download](http://packages.debian.org/sid/i386/pulseaudio-module-jack/download)

This should install without complaint, and I would assume that one could compile an ubuntu version of the plugin with jack support with some minimal effort (but why bother).

Next, edit your /etc/pulse/default.pa to tell it to load the jack modules.

-----------------snip----------------
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=inpu
t
#load-module module-null-sink
#load-module module-pipe-sink
load-module module-jack-sink
load-module module-jack-source
---------------snip--------------------

Now pulse will automatically connect to jack sinks if they exist when it's started.

I found that doing /etc/init.d/pulseaudio restart, or even stop followed by start failed to actually restart the server. I had to kill it manually with 

kill pulseaudio

I was able to do this as a user account without sudo, so that makes me think that pulseaudio is started on login, not as a root process. I will be looking into how exactly pulseaudio is started so that I can start jack first, but I don't know how to do this yet. Naturally, jackd cannot be started as a root service and be connected to by a user, so both drivers have to be started in userspace.

Next, start the jack server with whatever settings you use.

jackd -d freebob (with your driver and settings instead)

Finally, restart pulseaudio as a daemon with

pulseaudio -D

Don't use -n because you're using the default settings.

Now jack_out should show up both in System->Sounds as well as the pulse audio manager (aptitude install paman), allowing you to switch to it. Well, at least it does for me.

Cheers,
Brian

---

### Post by neltnerb on 2008-07-30
Alright, I figured out how to make it start up automatically. Boy is it a stupid mess though.

Apparently, GNOME automatically starts pulseaudio because you enable ESD Mixing in the Sound Control Panel (???). It does this because /usr/bin/esd is actually a symlink to /usr/bin/esdcompat, which is a script the pulseaudio people put out that behaves like esd's startup script, but starts pulseaudio instead.

So, I got things to start in the correct order by telling it to *NOT* enable system sound mixing (ESD) in System->Preferences->Sound. You can also do this in gconf-editor at desktop->gnome->sound (I think, I didn't spend a lot of time figuring out how gconf works).

Then, it was a matter of adding jackd to the startup programs. I did this by going to System->Preferences->Sessions (apparently there isn't a human readable "script" file anymore... why you wouldn't have the Session information change a linear script file is beyond me, but whatever). I created one startup program that ran '/usr/bin/jackd -d freebob'

Next, I needed to create a delayed turn-on version of pulseaudio. I did this by simply creating /usr/local/bin/delayed-pulseaudio which contained

----------------
#!/bin/sh

sleep 10
pulseaudio -D
----------------

and running chmod +x /usr/local/bin/delayed-pulseaudio. This caused a 10 second delay from the start of running the script to pulseaudio actually being run (long enough for jackd to start).

I created another new entry in the Session startup list for that new script to get it to automatically load. Without including it, pulseaudio no longer started (having turned off ESD, it wasn't loaded).

This thus far seems to correctly automatically run jackd in local userspace, and then subsequently run pulseaudio. Possibly another option would be to change pulseaudio to be a script to first run a delay and then run the real pulseaudio program, but then you wouldn't be able to run it instantly from the command line. I think the way I outline above is probably the cleanest (and should probably be how pulseaudio is started anyway... why is it started through a trick esd script???).

If anyone has any better ideas, please, feel free to help iterate towards a nice howto =) I, unfortunately, have done enough fiddling now that I can't be sure that this will work on other people's computers... but if it doesn't work on yours let me know so I can see what might be different?

---

### Post by markbuntu on 2008-07-31
Boy, that answers some questions I was having. 

btw, Pulseaudio is started at boot, you can see it in Boot Up Manager (bum) and turn it off there and Pulse Audio Session Manager was in System/Preferences/Sessions and turned it off there too and it was still running. I also found that ALSA was turned off in System/Services by default and turned that on 

I thought hal might have something to do with that but I never got around to investigating that avenue. Now you tell me that using esd starts Pulseaudio.

It seems that the PA devs were determined to have Pulse running no matter what people did to get rid of it. It is a wonder that three or four instances of pa were not running by default.

Anyway, I got all my sound working together with the exception of jack and thanks to you, I can probably get that working now too.

You may be able to get jack to be the default by editing etc/libao.conf to read:
```

default_driver=jackd

```

I think that helped to get PA to use ALSA sinks and sources in my setup but of course I used:
```

default_driver=alsa

```

I am guessing here. I have not tried this yet but it may be part of the solution you are looking for.

---

### Post by neltnerb on 2008-07-31
Neat, thanks for the further information. Especially the pointer to BUM; is it deriving it's information from the rc. files, or is there yet another place for startup scripts? I was under the impression that editing /etc/default/pulseaudio to say 

PULSEAUDIO_SYSTEM_START=0

would cause it to not start a system wide instance. I think this is the default in Hardy, I assume that is what you are running?

One huge issue is that (as the ubuntu developer gurus point out as the reason it's not included) jackd is somewhat unstable (sometimes I need to do things like unplug and plug back in my firewire sound card, or it will collapse due to xruns, etc). If the system is unable to start jackd, hardcoding it to load jack in that module file seems to cause pulseaudio to *also* not be able to load.

I should check and see if the lines to load the jack-sink and jack-source modules are really necessary. I think that if in /etc/default/pulseaudio you have the line

DISALLOW_MODULE_LOADING=0

instead of 1 (which is not default, I believe) it may automatically detect the option to connect to jack as an output. If this is the case, all one may have to do is install the plugin from debian sid, tell it not to start the system server, not disallow module loading, not start ESD, and set it up to delay starting the userspace pulseaudio.

My machine is now sufficiently hacked (in the good way) that I don't want to go and try to unfix my working sound... but if anyone tries to follow this brief outline for how to set it up, try doing the bare minimum suggested in this post to see if it will automatically load jack output through HAL. If it will, then it may be reasonable to actually produce a debian universe package that modifies those settings to make it work uniformly for those that want to install the unstable jack system.

---

### Post by markbuntu on 2008-07-31
Well yes, I am running Hardy and I also do not want to mess up my now working sound. I had a lot of problems with jack when I had Ubuntu Studio installed a few months ago and my interest have changed so I have not much need to use it anymore but I am getting ready to give Studio another shot. I have downloaded the 8.04.1 Ubuntu Studio dvd iso and will probably install it sometime in the next few weeks when I get another drive to put it on.

As far as I know, Hardy loads PA by default but yes,

PULSEAUDIO_SYSTEM_START=0

is the default. I wonder why it is found in BUM? Just in case?

I think

DISALLOW_MODULE_LOADING=0

would prevent any user from having PA at all.

I was able to get all my PA and ALSA and OSS sound apps working together but it was bugging me that I could not get any jackd apps to play with them. I wrote this little guide for how I did it. A few people have used it and some have had success.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I will put a link to this thread for jack enthusiasts who look at mine.

Anyway, I will be installing Studio again soon and it will be nice to see if I can get everything to go like OSS-ALSA-PA-JACK-sound card since what I have now goes something like OSS-ALSA-PA-ALSA-sound card. Hopefully, I will be able to add a jack section to my little guide soon.

And yes, jack is still buggy and a little unstable with the new usb stuff but the devs are working hard on that.

---

### Post by markbuntu on 2008-08-04
OK, I got UbuntuStudio installed. I did a new install of 8.04.1 i386 and then installed Ubuntu Studio on top of it with Synaptic. I have a few minor issues, like timdity failing to load and the rt kernel giving me a grub error 15 so it needs some work...
And a new SIIG SoundWave 7.1 PCI card, works OOB!!

I got all my sound working very easily ( I have a lot of experience with that, lol).

And I have some progress to report on the jack side of things. First of all, jack works with this card, xruns eliminated, card midi in use and working with Hydrogen. Have not had much time to try it with other apps yet but this is very good so far for a $40 card.

And the big news, jack can use the SIIG card and pulseaudio can use the on board and they will both run AT THE SAME TIME!!! Even if I have pulseaudio configured to use the SIIG card and run jack, as soon as I close jackcontrol, the pulseaudio sound comes back.

I did nothing special to get this to happen, followed my own guide and configured jack:
Driver: alsa 
Interface: hw:1 ( C-Media CIM8768, the SIIG card)
Input Device: (default)
Output Device: (default)

 Still fooling around with 
Frames/Period
Periods/Buffer
but have latency down to 8.71 msec which is OK for what I am currently doing which does not include live recording. I know I can get it way down when I get the rt kernel working.

Studio is a much more pleasant experience this time around.... Uh Oh, updates. We will see what they bring, good news I hope.

---

### Post by leepesjee on 2008-08-06
With the help of your hints above (and others in the original thread) I managed to route the firefox/flash audio through pulseaudio to jack (Hardy with a multi-channel M-Audio lt1010 card), so now I've got all my audio apps nicely playing in jack:) A few comments:
- I needed to add a 'channels=2' option to the 'load-module module-jack-sink' command and likewise with the source-command, otherwise the modules wouldn't initialize.
- The start-up or not at boot-time of the pulseaudio daemon and how it's organised is complete obscure to me. Where Markbuntu has difficulty to not let it start, I don't manage start it at all (at boot-time), whatever I try. I gave up trying to understand. I'am new to Ubuntu and I agree that the start-up routines are a mess (uncomprehensible for an Ubuntu-newbee at least). I had a like experience trying to use dhcpcd instead of dhclient. However, I can start the pulseaudio daemon in Gnome Sessions (not if I enable ESD in System -> Sounds ???) so that's what I do.
- In Gnome Sessions there was an item "PulseAudio Session Management" which uses the command pactl to dynamically load a module in pulseaudio. I don't know what that module does (I diasabled it), but this command is of good use. I've put it in jackcontrol to load the jack-sink module after startup of jack ('pactl load-module module-jack-sink channels=2'). This way the module is always loaded after jack starts. So, if you make sure that the pulseaudio daemon runs, you are in order. In fact, the be sure for the daemon to start - also if jack is not up - I commented the jack lines in the pulseaudio configuration file. Advantange of this setup: after the occasional crash of the jack server, you can just restart it and the pulseaudio sink (and/or source if you want) is there also.
- About the stability of jack. I had problems with it too, when I used an external audio device with firewire. I've a pci card now and jack is very stable. I wonder if jack's really the problem, or if it's the firewire interface.
Greetings, Leo.

---

### Post by markbuntu on 2008-08-07
I remember reading somewhere that pactl can be used to dynamically load modules into the pa daemon. I never thought of it for this and neither did about a zillion other people, duh. 

Anyway, You are a hero today!!

I am doing a major rewrite of my guide and will be including a section on jack in it. I am changing the title to:
Mutiple Sound Solution v0.3 (ALSA, PulseAudio,jack)

I will give a hint to your fix with attribution if you have no objections and will be keeping a link to this thread open.

I am planning on changing the guide tomorrow, it seems an auspicious date, 08/08/08.

I do believe you have found the solution to this issue but I have a few questions.

If jack crashes, does this cause a problem for pulse?

Should these modules be removed with pactl when jack closes?

I agree about the firewire thing. freebob seems to still be a work in progress.

---

### Post by neltnerb on 2008-08-07
On my setup, if jack crashes, I also have to restart pulseaudio. Perhaps with the dynamic module loading it can reload the jack output module instead of restarting? I'm afraid that while leepesjee's comments sounds great, they're over my head.

freebob is actually being obsoleted. it's being replaced with ffado

[http://www.ffado.org/](http://www.ffado.org/)

but this hasn't made it into the ubuntu version of jack yet.

My experience with ffado was that it was slightly more likely to work at all, but also slightly less stable than freebob. However, freebob is no longer being developed, so we will all need to switch sooner or later =)

---

### Post by markbuntu on 2008-08-07
Have you tried pactl yet?
It seems that all you have to do is edit the jack launcher and put the pactl load-module module-jack-sink command with the options in front of the jackd command.


[http://linux.die.net/man/1/pactl](http://linux.die.net/man/1/pactl)


[http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules)

I really would like us to get this figured out. I will give it a whirl this weekend.

---

### Post by leepesjee on 2008-08-08
*If jack crashes, does this cause a problem for pulse?*
*Should these modules be removed with pactl when jack closes?*

Well, I don't know what it does on a crash, as I don't have them (lol), but if I stop Jack decently, I see in Pulseaudio Manager that the jack-sink module is removed, whitout any other disturbances (that answers the second question too, I think).

*On my setup, if jack crashes, I also have to restart pulseaudio.*

I think the reason why you need to restart Pulse, is that the jack-sink module is removed on a jack crash. So you can either restart Pulse, or only reload the jack-modules with pactl. I think you should try it.

*... and put the pactl load-module module-jack-sink command with the options in front of the jackd command*

Actually, I think it should be done the other way round, because the module won't load if jack is not up (well, it doesn't on my system). I start jack with the qjackctl program, and put the pactl command under Setup -> Options -> 'Execute script after start-up'.

---

### Post by markbuntu on 2008-08-08
Well, that actually makes more sense. I will give it a try sometime this weekend on my UbuntuStudio install. That is where I use jack.

---

### Post by markbuntu on 2008-08-08
Well OK, that works.

I just wrote a little script and put it in the box in jack control/Setup/Options/Execute script after Startup. The script in my ~/scripts/jack_startup file:

```

#load pulseaudio jack modules
#!/bin/sh

pactl load-module module-jack-sink
pactl load-module module-jack-source

```

I just made a new file in my /home/markstudio/scripts directory called jack_startup and made it executable and put those lines in it. 

This is good, the last piece to the puzzle I have been putting together. Now I have jack sinks and sources in the Pulse Audio Volume Control and in the Volume Control on the panel. And I have Pulse audio JACK Sink and Pulse Audio JACK Source in my jack Audio connections bay all connected up to system playback and source automatically.

A thousand thanks to you guys. :guitar::lolflag::guitar:

---

### Post by markbuntu on 2008-08-09
I have just tested this in both my UbuntuStudio8.04.1 i386 install and the regular Hardy i386 install and it works in both. I can now record streaming radio and anything else playing in any pulse/alsa/oss application in ardour by fooling around in the connections bay.

I have updated my guide and included this fix in it. Now we truly have a Multiple Sound Solution that really works everywhere for everything.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

netlerb, I do believe you can mark this thread as solved.

---

### Post by motin on 2008-08-10
> **markbuntu said:**
> I have just tested this in both my UbuntuStudio8.04.1 i386 install and the regular Hardy i386 install and it works in both. I can now record streaming radio and anything else playing in any pulse/alsa/oss application in ardour by fooling around in the connections bay.

I have updated my guide and included this fix in it. Now we truly have a Multiple Sound Solution that really works everywhere for everything.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

netlerb, I do believe you can mark this thread as solved.

Exactly - I was going to say the same: No special startup sequence is needed, just have the pulseaudio sink+source loaded dynamically upon startup. Thanks markbuntu for presenting pactl to us! :)

---

### Post by markbuntu on 2008-08-10
no, no, it was leepesjee who fgured that out, thank him instead.

Also, I have finsished testing with my Hardy amd64 install and it works fine there to and in the UbuntuStudio64 which I upgraded my amd64 to after testing. I have put a few new notes in my guide about some minor issues with that which are easily fixed that I did not see in the i386 testing. If you are running Hardy UbuntuStudio64 or are plannning to, you should check them out.

---

### Post by markbuntu on 2008-08-10
I have attached some screenshots for the non-believers. I got all the xruns playing a 24k stream. They stopped when I switched to a 96k stream. 

My desktop is 3850x1200 across a 24 and 19 inch monitor. I really could use another 24 inch monitor for this

---

### Post by motin on 2008-08-11
> **markbuntu said:**
> no, no, it was leepesjee who fgured that out, thank him instead.

Ah, I was too quick! Thank you leepesjee! Thank you both :)

---

### Post by minghio on 2008-11-09
```

#load pulseaudio jack modules
#!/bin/sh
pactl load-module module-jack-sink
pactl load-module module-jack-source
```

If I execute this script I receive the message:
Connection failure: Connection refused

What's wrong?
I'm on intrepid and the Jack server is running smoothly.

---

### Post by neltnerb on 2008-11-09
I get that error if pulseaudio is not running when I try to load the modules.

Try doing 'pulseaudio -D' before you load the modules. If that doesn't work, perhaps pulseaudio is frozen -- in which case you could try 'killall pulseaudio' first.

---

### Post by lilorox on 2008-11-12
This thread fits exactly my needs so thank you guys :)

But (there is always a "but"!) if I'm not mistaken all I should do to get jackd and pulseaudio working is load the sink and source modules into pulseaudio, right?

Because doing this manually after my session is started loads the modules all right, starts jackd (I can see a new sink (jack_out) and two new sources (jack_in and jack_out.monitor) in the pulseaudio manager after loading the modules), but seems to prevent pulseaudio to do its job :(

If I run mplayer with -ao jack, it works, but with -ao pulse or -ao alsa, it doesn't!

Did I miss something? Is there anything I need to do besides loading the modules?

BTW, I'm running intrepid (and just switched to Ubuntu after 3 years with Gentoo, but that's a detail ;))

Any help would greatly appreciated !

---

### Post by variona on 2008-11-19
Is the "pactl load-module" a feature available from Hardy upwards?
Further down the output for "pactl -h"
This would explain the error I'm getting "No valid command specified."

user@terminal:~$ pactl -h
pactl [options] stat
pactl [options] list
pactl [options] exit
pactl [options] upload-sample FILENAME [NAME]
pactl [options] play-sample NAME [SINK]
pactl [options] move-sink-input ID SINK
pactl [options] move-source-output ID SOURCE
pactl [options] remove-sample NAME

  -h, --help                            Show this help
      --version                         Show version

  -s, --server=SERVER                   The name of the server to connect to
  -n, --client-name=NAME                How to call this client on the server

---

