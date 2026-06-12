---
title: "Unable to Start Jack Session"
date: 2016-06-13
forum: Multimedia Software
---

### Post by thomas113 on 2016-06-13
Hi so I'm having an issue with starting a Jack session, or just in general getting any midi program to function properly anyways (which goes back to jack) 

So anyways, the problem I have is any time I try to start a Jack session I get an error message, which I'll post on the lines bellow. I should say I've tried all the major fixes I could find online and still have come up with the same exact result. The error is as follows:

 [COLOR=#999999]23:45:07.239 Statistics reset.[/COLOR]
 [COLOR=#cccc99]23:45:07.269 ALSA connection change.[/COLOR]
 [COLOR=#999999]23:45:07.475 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 [COLOR=#66cc99]23:45:08.761 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]23:45:11.317 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 Sun Jun 12 23:45:11 2016: Starting jack server...
 Sun Jun 12 23:45:11 2016: JACK server starting in realtime mode with priority 10
 Sun Jun 12 23:45:11 2016: self-connect-mode is "Don't restrict self connect requests"
 Sun Jun 12 23:45:11 2016: Acquired audio card Audio0
 Sun Jun 12 23:45:11 2016: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Sun Jun 12 23:45:11 2016: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Sun Jun 12 23:45:11 2016: ERROR: Cannot initialize driver
 Sun Jun 12 23:45:11 2016: ERROR: JackServer::Open failed with -1
 Sun Jun 12 23:45:11 2016: ERROR: Failed to open server
 Sun Jun 12 23:45:12 2016: Saving settings to "/home/ubuntu-studio/.config/jack/conf.xml" ...
 [COLOR=#ff0000]23:45:16.798 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock

 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock

 [COLOR=#ff0000]23:46:27.513 D-BUS: JACK server could not be started. Sorry
[/COLOR]
So from this point on I have no idea at this point how to proceed, I'm really hoping that someone has a bit of insight or a little more experience with this than me. Thanks ahead of time for any help you guys.

---

### Post by kazakore on 2016-06-13
'm assuming those lines comes from qjackctl, they look like it... 

Maybe you have something already using ALSA and do it's tied up and Jack can't connect. Most likely this will be PulseAudio on a moden distro. I was surprised that Ubuntu Studio still does not ship with scriptn the qjackctl options for when starting and stopping the Jack server. I have mine edited to look like this. I think I had similar issues when I first installed 16.04 and this is what fixed it for me (but my memory is less than perfect.)

Scripts in Options tab of Setup:
On Startup = pulseaudio -k; killall pulseaudio
After Startup = pulseaudio DnF /etc/pulse/default.pa
On Shutdown = pulseaudio -k
After Shutdown = killall jackd; pulsesession

This appears to ensure that PA released ALSA for Jack to take command and then relaunches it with the Jack/PA Sinks so you get PA through Jack on startup and reverts to normal PA operation on Jack shutdown.


Actually looking at my last line has reminded me of an issue I had. Very often Jack isn't/wasn't closing cleanly for me. Has it run at all? If it did and then you stopped it and it wont start. If you run a "ps -A | grep jack" command you will see jackdbus still running. "killall jackd" or "killall jackdbus" didn't work and I had to use a "kill -9 *PID*" to terminate it and get Jack to start again. Not run into this for a while now and can't remember what I was messing with to trigger it before so hopefully not related...

---

### Post by thomas113 on 2016-06-14
Thanks for the suggestion. I had suspected that pulseaudio had been an issue, I had problems with it before on later mint distros (thats actually how I came to find ubuntu studio)

Anyways, I ran the scripts you suggested. Unfortunately I'm still looking at the more or less the same errors here. This is what I came up with:

>  Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 [COLOR=#999999]00:54:05.283 Startup script...[/COLOR]
 [COLOR=#990099]00:54:05.285 -k; killall pulseaudio[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 sh: 0: Illegal option -k
 [COLOR=#999999]00:54:05.694 Startup script terminated with exit status=512.[/COLOR]
 [COLOR=#ff0000]00:54:05.942 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Tue Jun 14 00:54:05 2016: Starting jack server...
 Tue Jun 14 00:54:05 2016: JACK server starting in realtime mode with priority 10
 Tue Jun 14 00:54:05 2016: self-connect-mode is "Don't restrict self connect requests"
 Tue Jun 14 00:54:05 2016: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Tue Jun 14 00:54:05 2016: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Tue Jun 14 00:54:05 2016: ERROR: Audio device hw:0 cannot be acquired...
 Tue Jun 14 00:54:05 2016: ERROR: Cannot initialize driver
 Tue Jun 14 00:54:05 2016: ERROR: JackServer::Open failed with -1
 Tue Jun 14 00:54:05 2016: ERROR: Failed to open server
 Tue Jun 14 00:54:07 2016: Saving settings to "/home/ubuntu-studio/.config/jack/conf.xml" ...
 [COLOR=#ff0000]00:58:30.315 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]



As you can see its most of the same stuff, with the execution of the extra scripts in that. So I went ahead and ran another check or two to see what was going on in the background, As I expected pulse was runnnig, and so was a process "jackdbus" I hadn't expected that as jack hasn't been run yet on this computer. 

> ubuntu-studio@ubuntu-studio:~$ killall pulseaudio
ubuntu-studio@ubuntu-studio:~$ ps -A | grep jack
20718 ?        00:00:10 qjackctl
20724 ?        00:00:01 jackdbus
ubuntu-studio@ubuntu-studio:~$ ps -A | grep pulseaudio
20792 ?        00:00:00 pulseaudio
ubuntu-studio@ubuntu-studio:~$ killall pulseaudio
ubuntu-studio@ubuntu-studio:~$ ps -A | grep pulseaudio



---

### Post by parkerfeagins on 2016-06-15
> **thomas113 said:**
> Thanks for the suggestion. I had suspected that pulseaudio had been an issue, I had problems with it before on later mint distros (thats actually how I came to find ubuntu studio)

Anyways, I ran the scripts you suggested. Unfortunately I'm still looking at the more or less the same errors here. This is what I came up with:



As you can see its most of the same stuff, with the execution of the extra scripts in that. So I went ahead and ran another check or two to see what was going on in the background, As I expected pulse was runnnig, and so was a process "jackdbus" I hadn't expected that as jack hasn't been run yet on this computer.

I have been having the exact same error output on my launch attemos. Except pulseaudio isn't involved.

---

### Post by kazakore on 2016-06-15
> **thomas113 said:**
> 
As you can see its most of the same stuff, with the execution of the extra scripts in that. So I went ahead and ran another check or two to see what was going on in the background, As I expected pulse was runnnig, and so was a process "jackdbus" I hadn't expected that as jack hasn't been run yet on this computer.

Seems weird you are getting jackdbus showing up when it has never been started before. As I think I mentioned I had this issue where jackdbus was something still in the background and had to be killed before I could start jack. To do this **killall jackdbus** does not work. You have to run

ps -A | grep jack
 1431 ?        00:00:35 qjackctl
7475 ?        00:00:01 jackdbus
kill -9 7475

(PID number example, will be different every time.)

 The do a ps -A | grep jack again to check it has gone. You should then be able to start the Jack server.

I think I only had issues getting back to crash and stopping it with devices connected before inserting the scripts.

Personally I have everything PA related remove from Settings > Session And Startup and have added a line to start qjackctl on boot and have Jack autoconnect on qjackctl startup.


But I also have the KXStudio repositories and I'm pretty sure that my version of either Jack or QJackCTL changed with that, as before Update/Upgrade after adding them I was missing the option to start qjackctl in the background, whereas after upgrading it returned (like I am used to.) Maybe this has improved some of the other stability issues as well, I don't know...

---

### Post by thomas113 on 2016-06-17
Ok so I went ahead and went with that, I killed the jackdbus that was running in the background. I still wasn't able to open the jack server, Qjackctl got a little bit farther into the process than it has any other time so, thanks for the help. So here's what I got this time:

>  Thu Jun 16 15:02:30 2016: ------------------
 Thu Jun 16 15:02:30 2016: Controller activated. Version 1.9.11 (unknown) built on Wed Oct 28 19:44:17 2015
 Thu Jun 16 15:02:30 2016: Loading settings from "/home/ubuntu-studio/.config/jack/conf.xml" using expat_2.1.0 ...
 Thu Jun 16 15:02:30 2016: setting parameter 'engine':'driver':'(null)' to value "alsa"
 Thu Jun 16 15:02:30 2016: setting parameter 'engine':'realtime':'(null)' to value "true"
 Thu Jun 16 15:02:30 2016: setting parameter 'engine':'verbose':'(null)' to value "false"
 Thu Jun 16 15:02:30 2016: setting parameter 'engine':'client-timeout':'(null)' to value "500"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'device' to value "hw:0"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'capture' to value "hw:0"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'playback' to value "hw:0"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'rate' to value "44100"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'period' to value "1024"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'nperiods' to value "2"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'hwmon' to value "false"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'hwmeter' to value "false"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'duplex' to value "true"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'softmode' to value "false"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'monitor' to value "false"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'dither' to value "n"
 Thu Jun 16 15:02:30 2016: setting parameter 'drivers':'alsa':'shorts' to value "false"
 Thu Jun 16 15:02:30 2016: Listening for D-Bus messages
 Thu Jun 16 15:02:30 2016: Starting jack server...
 Thu Jun 16 15:02:30 2016: JACK server starting in realtime mode with priority 10
 Thu Jun 16 15:02:30 2016: self-connect-mode is "Don't restrict self connect requests"
 Thu Jun 16 15:02:31 2016: Acquired audio card Audio0
 Thu Jun 16 15:02:31 2016: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit

 Thu Jun 16 15:02:31 2016: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Thu Jun 16 15:02:31 2016: ERROR: Cannot initialize driver
 Thu Jun 16 15:02:31 2016: ERROR: JackServer::Open failed with -1
 Thu Jun 16 15:02:31 2016: ERROR: Failed to open server
 Thu Jun 16 15:02:32 2016: Saving settings to "/home/ubuntu-studio/.config/jack/conf.xml" ...
 [COLOR=#ff0000]15:02:39.469 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info[/COLOR]



So now when I'm looking at this, its starting to seem to me that my problem lies with alsa, like its starting right here 
> Thu Jun 16 15:02:31 2016: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit

 Thu Jun 16 15:02:31 2016: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Thu Jun 16 15:02:31 2016: ERROR: Cannot initialize driver
 Thu Jun 16 15:02:31 2016: ERROR: JackServer::Open failed with -1
 Thu Jun 16 15:02:31 2016: ERROR: Failed to open server
 Thu Jun 16 15:02:32 2016: Saving settings to "/home/ubuntu-studio/.config/jack/conf.xml" ...



Could this be a permissions issue with alsa or something like that?

---

### Post by kazakore on 2016-06-22
I've had similar looking messages fairy recently, think Jack as started refusing to start again and then I look a minute or two later and it is actually running correctly despite the message. I haven't looked so carefully to say it definitely looks the same as yours (except just a single red line saying Jack connection failed) and I'm not sure if it tries itself again automatically or if the message is in error. Again only after forcing close (think after I close it with a jack program connected) and again I have a fair few bits from outside the official repository.

Sorry but my rather low level general knowledge on this is about exhausted. The LAU mailing list is generally a far better place than these forums to get answers to problems on this kind of stuff. [http://lists.linuxaudio.org/listinfo/linux-audio-user](http://lists.linuxaudio.org/listinfo/linux-audio-user)

---

### Post by kazakore on 2016-06-22
Or you're not making the same, very simple mistake as Parker are you? 

[http://ubuntuforums.org/showthread.php?t=2327684](http://ubuntuforums.org/showthread.php?t=2327684)

---

