---
title: "M-audio Ozone in Ubuntu?"
date: 2006-03-22
forum: Multimedia &amp; Video
---

### Post by ombudsmedia on 2006-03-22
Hi,

Does anyone here use m-audio ozone with Ubuntu? 
I have installed alsa-base
I have downloaded the firmware madfuload 1.2
and I also run the codes:

./configure
make
make install

I got no error message but the usb audio device doesn't show up in jack or multimedia selector...

thanks for any help!

---

### Post by Harry_Sack on 2006-03-26
I also have this one. I don't think I've ever had it working in ubuntu, but it works in demudi. Have no idea what the problem might be though.

---

### Post by Harry_Sack on 2006-03-28
This is strange. I'm now running the Breezy Live CD, and Ozone just popped in, ready for use. I've been struggling to make it work in dapper. It seems to me, that, for some reason unknown to me, it gets detected after it has run with another OS on the same machine.
And I think your method is correct. That's what I've done as well. Just "sudo make install", but I guess you've done that.

---

### Post by ombudsmedia on 2006-03-29
Hi Harry,

My first test was in a Breezy installation I had on my notebook.
The first time I plugged Ozone into USB jack it was recognized and also appears at multimedia selector. But it last 10 minutes and then never show up again : (

Researching yet...  Ubuntu is my first choice, but I can't stay without soundboard
 I'm considering to use dual boot Demudi/Ubuntu...

---

### Post by EPOX123 on 2006-04-11
hehehe must be a bug, try and disconnect your usb and reconnect it with ubuntu loaded and loggedin. Might work, screen saver might mess it up not sure.

---

### Post by maku-d on 2006-07-21
I have an m-audio ozone too and also can't get it working in dapper.  Anyone have any idea why this would be? Something to do with snd-usb-? not being loaded into the kernel.  I've installed the madfuload drivers also, still no luck. 

ombudsmedia did you have any luck with demudi?  I'm seriously considering the switch- as above just cause I really wanna get sound recording up in linux.  The drivers exist, shouldn't it be simple to get this thing working under ubuntu?

If anyone has any ideas send em my way...I'd be totally thankful to be able to stick with dapper.

[SIZE="5"]----------
EDIT - Problem Solved 28/11/2007
----------[/SIZE]
To save everyone time...I've solved this problem...it took almost two years, but I've just uploaded step by step instructions...find them on [SIZE="3"][page 5]("http://ubuntuforums.org/showthread.php?p=3854071#post3854071")[/SIZE] of this thread...here's the link to the post- [SIZE="4"][http://ubuntuforums.org/showpost.php?p=3854071&postcount=49]("http://ubuntuforums.org/showpost.php?p=3854071&postcount=49")[/SIZE]

---

### Post by maku-d on 2006-07-24
ALRIGHT!!!!  I got it working!  And get this ... didn't even need the driver. Here's how it happened:
I had dapper installed on both my P4 2.8 and powerbook G4 667mhz.  Anyway I was a little unhappy with dapper performance on the G4 so I thought- why not do the update to the edgy prerelease repositories? ...alot of people have been talking about it lately.  So I did- 'sudo apt-get install dist-upgrade' and like four days later(I'm using a 56k modem to connect to the net) it finished.  Did the reset last night and what do you know- nothing.  Couldn't detect my hardware, and like seven other less significant fails- eek! Edgy's clearly not ready for me yet. Anyway so I had to format and I thought what better time than to try breezy with my ozone.  So I dug out my old powerpc breezy install disk and vwala!! about an hour later I had the Ozone automatically detected and working fine- HUZZAH!  As we speak I'm downloading the ubuntu studio apps for breezy.

Now this brings me to something...which probably won't get replied to but I'll write it anyway.  Why is it automatically supported in breezy, and dapper can't find it?  And why on the powerpc and not on the pentium 4?  If anybody knows I would love to find out.  I was thinking maybe I could do a dist-upgrade to dapper and see if it keeps working, but then I thought screw that...I'll just wait for edgy, hell, maybe I won't even do that upgrade. It still seems a bit ridiculous that distros could go backwards.  I guess ubuntu is still young.

Oh well, I'm happy for now...hope this last entry gave hope to any Ozone owners out there.

---

### Post by dolson on 2006-07-25
Can you boot up your system, then plug it in, and run dmesg right after, and paste the last few lines here?

Then also try this on the system it does not work on, so we can compare.

Output of lsmod would be helpful from both systems too.

---

### Post by license on 2006-09-17
I also have an Ozone. I used to use Ubuntu before getting my Ozone and I really liked it. I'm thinking about giving it another try but it will be more or less pointless if my Ozone doesn't work with it. Has anyone had luck with it in Dapper yet?

---

### Post by maku-d on 2006-09-18
Hey all, been away for a while- just checking around for distros that might work with my ozone- brough me back here and saw the new post.  Here's my new findings

  Ozone doesn't work with linux- I think.

I haven't really found anywhere where anyone has actually gotten it working.

Haven't gotten it working at all in dapper. I had it detecting on my powerbook g4 with breezy(ie. I had the option 'Ozone' where you set the sound, where on any other linux distro it isn't even present) but once it was selected, I couldn't actually get playback with it :(

I tried demudi (the newer version 1.3.x as opposed to 1.2.1 which I might try soon- if I can be bothered) and had no success getting it to detect.

So yeah...basically I've come to the conclusion I'm not gonna get it working under linux.  I'm a little pissy at m-audio for not releasing a driver, but what can you do.  Another sad fact is that audio is the last thing in my multimedia toolkit preventing me from switching solely to linux.

If anyone has the smarts to get the ozone up and running in linux- particularly ubuntu (my distro of choice), I (along with many others I'm sure) will love you!

Hope this helps all...

---

### Post by sirbrown on 2006-11-22
I recently read this thread while trying to troubleshoot my Ozone, which had been working in Dapper with the firmware loader available at [http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/).  It stopped working after upgrading to Edgy; uninstalling Edgy and reinstalling Dapper got it working again with playback and midi input and everything.  So I think the last post's suggestion that the Ozone doesn't work in Linux at all might be a little hasty--you just might not want to upgrade to Edgy yet.

Just a note for others like me who search the forum posts whenever they're trying to figure stuff like this out.

---

### Post by ombudsmedia on 2006-11-24
Hi,

I have my ozone working very well on debian with a preempt kernel as described in ubuntustudio. MIDI and audio.

In debian it was recognized easily. Just have to load firmware. 
But it just work well with the preempt kernel.

---

### Post by mrthingy on 2006-12-14
Sorry for bumping this thread, but I wondered if anyone had got their m-Audio Ozone working yet?

---

### Post by mrthingy on 2006-12-15
dmesg (when pluggin the Ozone in): 

```
[17179662.320000] usb 4-4.2: new full speed USB device using ehci_hcd and address 6
[17179662.420000] usb 4-4.2: configuration #1 chosen from 1 choice

```

snd-usb-audio appears to be loaded fine as a module according to "lsmod". 

It even finds my Evolution MIDI keyboard. But the Ozone seems to be invisible. 

```
nick@nick-desktop:~$ cat /proc/asound/cards 
 0 [keyboard       ]: USB-Audio - MK-361 USB MIDI keyboard
                      Evolution Electronics Ltd. MK-361 USB MIDI keyboard at usb-0000:00:13.3-4.3, fu

```

lsusb:

```
nick@nick-desktop:~$ lsusb
Bus 004 Device 006: ID 0763:2808 Midiman 
Bus 004 Device 005: ID 0a4d:00a0 Evolution Electronics, Ltd 
Bus 004 Device 003: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1241:1122 Belkin 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by person x on 2007-02-20
I recently had trouble with the Ozone as well. The madfuload doesn't seem to work automatically. 

If you've installed madfuload you can manually load the firmware, however.

You'll need to lsusb and find what but and device Midiman is attached to. In your case bus 004, device 006.

Then you can invoke madfuload to load the firmware:

 sudo madfuload --device=/proc/bus/usb/(bus)/(device) --firmware=/usr/local/share/usb/maudio/ma008100.bin --waitbyte3

so in your case that would be

 sudo madfuload --device=/proc/bus/usb/004/006 --firmware=/usr/local/share/usb/maudio/ma008100.bin --waitbyte3

but you'll have to check each time before you load because it's apt to change.

It'll give you an error about resetting but it still seems to work fine. You can go to System>Preferences>Sound  and head to the sounds tab to switch the default device to Ozone. Good Luck!

---

### Post by person x on 2007-02-20
On top of that you'll need to do a good old fashioned ```
sudo modprobe snd-seq-midi
``` to get the keys working.

---

### Post by mrthingy on 2007-03-12
> I recently had trouble with the Ozone as well. The madfuload doesn't seem to work automatically.

If you've installed madfuload you can manually load the firmware, however.

You'll need to lsusb and find what but and device Midiman is attached to. In your case bus 004, device 006.

Then you can invoke madfuload to load the firmware:

sudo madfuload --device=/proc/bus/usb/(bus)/(device) --firmware=/usr/local/share/usb/maudio/ma008100.bin --waitbyte3

so in your case that would be

sudo madfuload --device=/proc/bus/usb/004/006 --firmware=/usr/local/share/usb/maudio/ma008100.bin --waitbyte3

but you'll have to check each time before you load because it's apt to change.

It'll give you an error about resetting but it still seems to work fine. You can go to System>Preferences>Sound and head to the sounds tab to switch the default device to Ozone. Good Luck!

Thanks for the detailed help! However, I'm still having problems. It works until shortly after the "madfuload" bit.

1. I do a "lsusb" to find where the Ozone is.
2. I then use madfuload with the correct device (e.g., /proc/bus/usb/004/006)
3. My soundcard makes a *POP* which seems to indicate it's initialising, also, a pop-up appears at the bottom right of the desktop showing a new Ozone is available.
4. However, it isn't selectable as a device in the sound setup. The sound server gives errors and even thought JACK can see the Ozone, it won't initialise it and crashes.

**If I do a "lsusb" again, the Ozone has moved along to the next USB bus! (e.g., 004/007). **

I can keep trying to use madfuload, but it will just shift the USB device to the next available slot. :confused:

---

### Post by doktorn on 2007-04-18
I've also been trying to make Ozone work in Ubuntu. I've got the Edgy and tomorrow will be trying Feisty.

I have loaded madfuload drivers and done a sudo /etc/init.d/udev restart and yes, the Ozone is popping up and it is avaliable in Sound and avaliable for default soundcard. However, when I try to test the output for Ozone I get the error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.

Also nothing shows in JACK. Maybe a modprobe for seq might solve that issue... Still I am unable to play any sound with Ozone.

Anyone got a clue or belive this might be solved for Feisty?

---

### Post by doktorn on 2007-04-18
Wohoo! I got the sound working for about 10 seconds.

Did an installation of OSS as M-audio wants it to be.
Then tried loading the driver.

Tada! For just a short time however... JACK is not responding at all again.

---

### Post by maku-d on 2007-06-10
Hi, just tried the above and when I attempt to run madfuload I get this error

$ sudo madfuload --device=/proc/bus/usb/001/010 --firmware=/usr/local/share/usb/maudio/ma008100.bin --waitbyte3

control transfer failed: (32) Broken pipe
control transfer failed: (32) Broken pipe
control transfer failed: (32) Broken pipe
downloading block 0 failed


Any thoughts?

---

### Post by doktorn on 2007-06-13
Don't know... Apparently this thread is quite dead. I've been trying to understand what happens. What I hear from other places is that it seems to be getting worse by each update of Ubuntu. Worked in Dapper, almost worked in Edgy, and just not working in Feisty. I'm using Ubuntustudio now because I belived it were better for handling usb audio. This does not seem to be the case however. I have no idea what your errormessage means. Maybe something wrong with usb?

I got my Ozone to work yesterday, but when I tried to run Ardour together with it my system hanged and were unable to respond to anything. I got this in Feisty and Edgy too. Does any other studio distro work better? I'm getting tired of trying... How about all you other? Do you think it's possible to request a driver from M-audio? seems like madfuload just doesn't do the job. The Ozone doesn't stay on it's bus/device for long.

And does anyone know why it only works in 1 of 15 cases?

---

### Post by maku-d on 2007-06-14
Yeah, really not sure. It's frustrating. Back on my old powerbook I had it detecting and thought working but it never actually worked with input or output...just detected the card. Was the same as you with trying ubuntu studio, thought it might be built in with better usb hardware detection, but was wrong. I've downloaded but have yet to try 64studio. I've got a 64bit processor so I could give it a go. I'm also curious about testing knoppix with it also to see if it auto detects. 

To be honest I'm just not sure it's possible to get m-audio usb soundcards working in linux. I've seen a few tutes and posts around the place, and obviously we followed the steps people have been laying out, but I can never find a concrete example of someone saying 'it works' then when asked how actually offers further response.

If anyone can boast success with snd-usb-audio compiling into the kernel and then supporting any m-audio card I'd love to get some advice so I can test with the ozone. I'm tempted to try any distro where I can find someone willing to help me through getting it working if that'll be possible- it's the one thing holding me back from getting into linux audio production. Madfuload lists it as working- but I'm thinking that could just be cause it's in the same product catagory as other m-audio cards that have actually been physically tested.

We'll see I guess ;D

---

### Post by maku-d on 2007-06-15
Damn! That was easier than I thought! I just booted knoppix 5.1.1 off an old linux format cover disc and it automatically detected and used the ozone!!!! :D I just downloaded a couple of mp3's off the net to test it and it's playing them beautifully.  Then opened audacity and what do you know...it recorded the input from my mic!!!

So I figure there's two ways to go from here. Sit back, smile, thank the god's (knoppix is debian based) and install all the audio apps I want to use- as well as a real time kernel....OR....pray that a linux expert will grace this topic and help me figure out why it works seamlessly in knoppix and not remotely after a stack of pissing around in ubuntu. 

I tell you what, if nothing else I have a lot of newfound respect for knoppix. Really never thought more than it was a distro for repairing other installs- with this hardware detection I'm thinking someone who wants to actually get stuff made, rather than mess around fixing stuff all day should actually consider using it as a desktop os...I am ;D

Anyway, I'll frequent here a bit, but for now I'm thinking knoppix all the way. Might try some other live distro's and see if any others can recognise the ozone. Everyone out there with frown's about their ozone's can breathe a sigh of relief...our sweet soundcards work in linux ;)

---

### Post by maku-d on 2007-06-16
Okay, got the ozone working in ubuntu studio this morning. Will post instructions soon.

---

### Post by paulg on 2007-06-21
Just noticed this thread. I have a MobilePre which also relies on the madfulload program. There's a bug in the installation that creates udev rules for an older version of udev that's not compatible with the Feisty/Ubuntu Studio udev. The process should be the same for the Ozone. See my howto [here](http://ubuntuforums.org/showthread.php?t=466667&highlight=Ozone).

---

### Post by doktorn on 2007-06-21
Great maku-d! Yeah I've heard about knoppix and Studio64.. Problem is that I'm new to Linux and just don't want to try many more distros.. It's hard as it is learning this one.. =) I'd really like to see that instructions of yours... Meanwhile I'll have a look at what paulg writes about. Seems like it might be the problem.

---

### Post by doktorn on 2007-06-21
Hey Buddies! That solved the problems! Thanks paulg! Awesome! Got sound! And the driver loads perfectly when starting my Ozone. This is the trick for Ozone: 

sudo gedit /etc/udev/rules.d/42-madfuload.rules

ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2808", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin -D $env{DEVNAME}"

(From paulg's howto)

Thanks for finding this info! Now it's just switching standard soundcard and add to modprobe... Because madfuload installation doesn't do the trick itself, does it? (Couldn't start jack-server, 
"cannot create /dev/shm/jack-1000 directory (Permission denied)
cannot create server sockets
cannot create engine"). Maybe solveable... Will think of this for all the rest of us noobies.

Thanks again paulg!

---

### Post by doktorn on 2007-06-21
Yes! I just had to restart the computer and voila! Worked!... And for everyone who didn't know this about jack and journaling filesystems (ext3 etc...) Mark Realtime with priority 0 to remove all glitches and get a wonderful sound. Thats all folks! =) Don't make same mistakes as I did. Thanks for everything guys! Now I'm out to spread the word. (A friend has been interested in Ubuntu but fears the problem with his Ozone as well...) Feels good I can make others happy.

---

### Post by paulg on 2007-06-21
> Now it's just switching standard soundcard and add to modprobe... Because madfuload installation doesn't do the trick itself, does it?

Not sure what you mean? What module are you needing to load? Again, I don't have this specific card so I may be missing a step required to get the Ozone working but will help you if I can.

To switch soundcards, I have found the most reliable way to be with the 'asoundconf' command in bash. In a terminal type asoundconf and it will display the help screen with all of the options for the command. These are most likely the only ones you will need:
[LIST]
[*]list cards available on your system```
asoundconf list
``` 
[*]set the card the system will use by default```
asoundconf set-default-card <card name>
```
[/LIST]

How are you starting JACK? With qjackctl? Are you selecting the correct interface (probably HW:1 but there should be a list from a pull-down menu)?

~pAul.

Edit: Just saw you got it working, great!

---

### Post by maku-d on 2007-06-25
---------------------------------------------------------------------------------------------
-----GET M-AUDIO OZONE WORKING TO PLAY SOUND IN AND OUT-----
---------------------------------------------------------------------------------------------
1. Install ubuntu studio with ozone turned on
2. # cd /etc
3. # sudo grep -R "snd-usb-audio index" *

     my output was-> modprobe.d/alsa-base:options snd-usb-audio index=-2

4. # cd modprobe.d
5. # sudo gedit alsa-base
6. find the line with snd-usb-audio and change the index=-2 to index=0
7. save and exit gedit
8. # sudo rmmod snd-usb-audio
9. # sudo modprobe snd-usb-audio
10. listen to music in your favourite player or record in your fav recorder ;D


Note: For testing your alsa configuration- check the scripts here: 
         [http://bulletproof.servebeer.com/alsa/index.php?task=scripts](http://bulletproof.servebeer.com/alsa/index.php?task=scripts)

Shouts to wishie @ #alsa@FreeNode for the help.

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
As a final note- I haven't got the midi controller working yet. I'll try the madfuload
instructions again and see if I can get that side of the ozone working. For now
I'm happy to know that right after an ubuntu install I can get sound in and out with
these simple steps. Hope it helps anyone with an ozone to get recording and playback
functionality.

---

### Post by maku-d on 2007-06-25
Sorry, output above probably should've been code to avoid the auto smiley :p

>> my output was-> 

```
modprobe.d/alsa-base:options snd-usb-audio index=-2
```

---

### Post by paulg on 2007-07-09
> **maku-d said:**
> ---------------------------------------------------------------------------------------------
As a final note- I haven't got the midi controller working yet. I'll try the madfuload
instructions again and see if I can get that side of the ozone working. For now
I'm happy to know that right after an ubuntu install I can get sound in and out with
these simple steps. Hope it helps anyone with an ozone to get recording and playback
functionality.

maku-d or doktorn, could you guys confirm if midi works or not? Did you need madfuload to make it work? Any additional steps required?

---

### Post by Aurora on 2007-07-19
> **maku-d said:**
> ---------------------------------------------------------------------------------------------
-----GET M-AUDIO OZONE WORKING TO PLAY SOUND IN AND OUT-----
---------------------------------------------------------------------------------------------
1. Install ubuntu studio with ozone turned on...


Hi,

You can't get it working in an existing install?  You have to install fresh with the device hooked up?

What about madfuload; do you have to install this as well?  I downloaded it, but I can't find where the file went. After downloading a window opens that lists madfuload-1.2 and there's a window within it that says: location: /  If I cd / and type ls it's not there, same if I navigate with Thunar.  I don't know how to install it if I can't find its directory.

I have Pro Tools on a Mac I could use, but I don't want to keep paying more and more for every little thing, and be bound by all the licenses.  I would love to use my Ubuntu Studio system instead.  Help, please, I'm totally lost :confused:

--Paul in Seattle

---

### Post by mrthingy on 2007-07-20
Many thanks to everyone that's persevered trying to fix this problem. I now have my Ozone working in Ubuntu, which is just fantastic!

Aurora: I don't think so, I'm sure you can correct the Ozone at any point. Madfuload needs to be installed, and you need to compile it first. Just download it somewhere as a file on it's own and then with the console i.e., 

# tar xvfz <madfuload archive file>
# cd <madfuload directory>
# make
# sudo make install

Then just follow the instructions about fixing the udev rules.

---

### Post by Aurora on 2007-07-20
> **mrthingy said:**
> 
Aurora: I don't think so, I'm sure you can correct the Ozone at any point. Madfuload needs to be installed, and you need to compile it first. Just download it somewhere as a file on it's own and then with the console i.e., 

# tar xvfz <madfuload archive file>
# cd <madfuload directory>
# make
# sudo make install

Then just follow the instructions about fixing the udev rules.

Thanks, mrthingy...but it didn't work as expected.  Here's my terminal output.  My comments in [square brackets].

pad@Studio909:~$ cd madfuload-1.2
[There was no .tgz file after the download; apparantly it was extracted automatically?]
pad@Studio909:~/madfuload-1.2$ make
make: *** No targets specified and no makefile found.  Stop.
pad@Studio909:~/madfuload-1.2$ man make
[Tried RTFM,,,way over my head]
Reformatting make(1), please wait...
pad@Studio909:~/madfuload-1.2$ ./
bash: ./: is a directory
[Don't know what I'm doing....]
pad@Studio909:~/madfuload-1.2$ cd /home/pad
pad@Studio909:~$ make madfuload-1.2
make: Nothing to be done for `madfuload-1.2'.
pad@Studio909:~$ cd madfuload-1.2
pad@Studio909:~/madfuload-1.2$ make
make: *** No targets specified and no makefile found.  Stop.
pad@Studio909:~/madfuload-1.2$ 

pad@Studio909:~/madfuload-1.2$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
pad@Studio909:~/madfuload-1.2$ 

Where do I go from here?

---

### Post by paulg on 2007-07-23
Aurora, try installing the package build-essential (sudo aptitude install build-essential).

Then run sequentially:
```
~/madfuload1.2/$ make
~/madfuload1.2/$ ./configure
~/madfuload1.2/$ sudo make install
```

Plug in your device and type: ```
asoundconf list
```
You should see the Ozone listed now if the install worked but if you have a more recent version of Ubuntu (I think 6.10 and up) you will need to update your udev rules for the Ozone firmware to be loaded. I have a post [here]("http://ubuntuforums.org/showthread.php?t=466667&highlight=Ozone") that covers a udev fix for a number of M-Audio USB devices, including the Ozone.

---

### Post by Aurora on 2007-07-24
> **paulg said:**
> Aurora, try installing the package build-essential (sudo aptitude install build-essential).

Then run sequentially:
```
~/madfuload1.2/$ make
~/madfuload1.2/$ ./configure
~/madfuload1.2/$ sudo make install
```


```
pad@Studio909:~$ sudo aptitude install build-essential
**********everything installs**************
Setting up build-essential (11.3) ...
pad@Studio909:~$ cd madfuload-1.2
pad@Studio909:~/madfuload-1.2$ make
make: *** No targets specified and no makefile found.  Stop.
pad@Studio909:~/madfuload-1.2$
```

:confused:I don't get it.  I'm going to try Googling the exact phrase "No targets specified and no makefile found". I'll tell you if it helps; in the meantime, see if you can come up with anything.

[EDIT] OK, have to run ./configure first, then make.  I am struggling with the udev rules now...

---

### Post by Aurora on 2007-07-24
Next chapter in the saga:

Terminal:
pad@Studio909:~$ sudo /etc/init.d/udev restart
Password:
 * Loading additional hardware drivers...                                [ OK ] 
pad@Studio909:~$ asoundconf list
Names of available sound cards:
IXP
Academic
pad@Studio909:~$

I am using the Ozone Academic version, so that's probably it.  Now I try to start JACK, and it doesn't start--it did before I installed madfuload.  The message log window says:

cannot create /dev/shm/jack-1000 directory (Permission denied)
cannot create server sockets
cannot create engine
19:31:53.121 JACK was stopped successfully.
19:31:53.122 Post-shutdown script...
19:31:53.123 killall jackd
jackd: no process killed
19:31:53.351 Post-shutdown script terminated with exit status=256.
19:31:55.185 Could not connect to JACK server as client. Please check the messages window for more info.

Permission denied?  Do I have to run JACK as root or something?  It never did that before.  It recognizes Ozone Academic in the setup window, but not in the connect window.  Also it doesn't list ALSA pcm like it did before.

<sigh> I guess I'm limited to proprietary software for awhile yet.

---

### Post by paulg on 2007-07-24
Are you selecting the 'academic' card?```
asoundconf set-default-card Academic
```

You should not be running JACK as root.

---

### Post by Aurora on 2007-07-25
> **paulg said:**
> Are you selecting the 'academic' card?```
asoundconf set-default-card Academic
```


OK, JACK starts now.  In the connections window, the only client is ALSA_PCM.  If I start Rosegarden and play a MIDI file,  the audio is routed to the ALSA_PCM client, and nothing comes out the phones output of the Ozone. There is no audio out of the internal sound card, either.  I opened up XMMS and played an MP3....ah, sound from the the Ozone, though XMMS doesn't appear in the connections window.

So I guess ALSA_PCM means whatever the default sound card is?  I'm pretty sure I had Rosegarden playing through the internal sound card via JACK before; now I don't have any sound from it.

If I don't want to use the Ozone every time I turn on the computer, do I have to manually reset the default sound card with jasoundconf?  And what's up with Rosegarden?

---

### Post by paulg on 2007-07-25
> **Aurora said:**
> 
If I don't want to use the Ozone every time I turn on the computer, do I have to manually reset the default sound card with jasoundconf?  And what's up with Rosegarden?

If you start the computer with the Ozone unplugged I think the other card will be selected... You may need to experiment with that as I am not certain. 

Try using the program patchage for a good visual representation of your available connections. qjackctl has the same features but I prefer the way patchage is laid out. I have never used Rosegarden so I cannot comment on that. You need to have the card set to duplex and have the rosegarden outputs mapped to the alsa_pcm outputs. You may need to do some routing within rosegarden. Channel 1 is usually 'left' and channel 2 is usually 'right'.

---

### Post by Aurora on 2007-07-26
> **paulg said:**
> <snip> You need to have the card set to duplex and have the rosegarden outputs mapped to the alsa_pcm outputs. You may need to do some routing within rosegarden. Channel 1 is usually 'left' and channel 2 is usually 'right'.

I was able to use Rosegarden with JACK and synth plugins with the crappy built-in sound, but not with the Ozone.  All the routing is done, but there is still no sound.  The Rosegarden outs are connected to 'playpack' in alsa_pcm, the Rosegarden record inputs are routed to 'capture' in the alsa_pcm; and the MIDI outs in Rosegarden are feeding MIDI in ports 0-3 in TiMIDIty.  TiMIDIty does not show up as a readable client in the audio tab in Jack Control.  I do not see any way to route internally in Rosegarden.  I also cannot get sound out of Wired, Muse, or XMMS.  In the case of XMMS, I can play and hear MIDI files using TiMIDIty without JACK.

---

### Post by luissp on 2007-07-28
Paulg,
I have the same problem. Ozone works (with some problems) but no sound with rosegarden. It sounds in the speakers of my laptop. Windog is a **** and my laptop works very well in ubuntu for most of the tasks, but I think that making music is so difficult for me...:( sad, sad, sad

---

### Post by paulg on 2007-08-01
Sorry I can't be of more help. I am unfamiliar with Rosegarden.

---

### Post by maku-d on 2007-10-02
Hey all, haven't been back to check here for a while. Was just reading an article at [prorec.com]("http://prorec.com/articles/tabid/109/entryid/270/default.aspx") and saw aurora's comment at the bottom and thought I'd come check back to see if anything new had come up on the thread. Since my earlier posts I've been doing audio recording and film syncing with ardour, but still never worried about midi. I'll give it a shot over the next couple of days and see if I can get it up and running with rosegarden. I'd love use the ozone as a controller (used to use it in cubase, but haven't done any film scoring in a while so haven't really needed it) for my next scoring project to test linux midi, so yeah, leave it with me and I'll report back on my findings.

---

### Post by Aurora on 2007-11-16
> **maku-d said:**
> Hey all, haven't been back to check here for a while. Was just reading an article at [prorec.com]("http://prorec.com/articles/tabid/109/entryid/270/default.aspx") and saw aurora's comment at the bottom and thought I'd come check back to see if anything new had come up on the thread. Since my earlier posts I've been doing audio recording and film syncing with ardour, but still never worried about midi. I'll give it a shot over the next couple of days and see if I can get it up and running with rosegarden.

Hello Maku-d,
Since the last time, I've managed to get sound playing in and out, but it plays through the built-in motherboard sound with Rosegarden, even though the Ozone is set as the default soundcard, and JACK is set up to use the Ozone exclusively.  I actually had it playing through the Ozone in Feisty, but JACK stubbornly uses built-in sound with Gutsy, no matter what I do in the settings dialog.  Non-JACK sound apps play through the Ozone in Gutsy,  If I boot Studio to Go! demo live CD, sound plays back through the right speakers, so it seems to be an Ubuntu issue.  I think it also worked with the Musix live CD, but I can't recall for sure.

I have also joined two mail lists, Ubuntu-Studio-Users and Linux-Audio-Users, but no one one these lists has been able to help.  I have also enlisted the help of one of the Sweetwater Sound personnel who has recorded a couple CD;s with LInux, but no answers.

Still no luck with MIDI. The ozone has never been recognised as a client.

I think it's time to look beyond Ubuntu Studio, there just seem to be so many problems, and other distros seem to work better.

I think it's also time to shop for new hardware, even though my income has dropped through the floor.  Other keyboards seem to work out of the box, including some M-Audio products.  This is one of those times I wish I had programming skills, so I could just write the drivers or whatever I need, and then contribute it to the community.

Peace,

Paul

---

### Post by maku-d on 2007-11-19
Hey man, glad to hear your results. I've just finished work 
last week on a massive movie project, so I've got a bit of 
time to play. I've think you've probably done a lot more 
testing than me. I haven't even got an ubuntu install at the 
moment. My housemate's running ubuntu gutsy on his 
acer laptop and my girlfriend's running kubuntu gutsy on 
her computer. I'll give it a go on those. I'm planning to start 
a new project where I entirely create a feature length movie 
using open source linux software. Probably sounds like a 
bit of a joke, but over the last few years I've used a heap 
of different multimedia programs and have always wished 
I could see a concrete example of something done with 
linux and open source. So yeah... I'll see how I go. Still 
winding down from the movie I've just finished. Am thinking 
about going Fedora (eek! Can I say that here?) with planet 
ccrma or maybe 64studio, but yeah will see how I go. I 
might end up having to invest in some new hardware also. 
It's a shame cause my ozone's got me through a lot of 
projects over the years. Haven't even thought about 
researching that though...would definitely ditch m-audio 
though. Have always promised to come back with results 
and hardly ever do. Hopefully I'll get around to it in the next 
couple of days and at least confirm that I can't get midi 
working so we can all give up and move on (I'm sure 
most people have already...I've always hoped it'd get 
solved). 

Cheers dudes.

---

### Post by maku-d on 2007-11-25
IT WORKS!!!!

Let me say it again...

IT WORKS!!!!

After years and years of messing with the Ozone, I've 
finally got it working with linux. Audio recording, midi 
controller, as well as the pitch wheel and function controls. 
It works! I'm so excited! I literally just tested Jack with 
zynaddsubfx and the second I got the keyboard working 
I came here to post. 

It's a crazy story. Like I wrote previously I've got a bit of
spare time since finishing my last project. Haven't had an 
Ubuntu install for a while- have tried a couple of gutsy's
(Ubuntu and Kubuntu both in beta and release) on my
housemates computers. But yeah...hadn't had my own
install. So I freed up a harddrive and went to install it last
night. Had a bunch of issues with gutsy. Mainly grub related...
installed it a couple of times and it was annoying me so 
I installed fedora 8 which I also had some issues with,
and then 64studio which I couldn't get to boot.

It was a long night and I think I settled with Fedora in the
end, but opened it when I woke up this morning and had a 
network issue (was gonna go planet ccrma...am probably 
coming off a bit impatient...but I guess I am... I wanted to test
the ozone), so I'd decided to go with kubuntu this morning (I
love kde so yeah...I wasn't too sad about not having ubuntu for
testing),I booted the live cd, but for some reason couldn't bring 
myself to install. Anyway I did a hard reset and switched out the
disc for the 64studio 2 i386 live disc, which I'm glad I did!

First thing I did when it booted was load default jack at defaults
and quickly open Ardour to test if the soundcard worked out of 
the box. I had a mic plugged into the xlr port and it recorded and
played back no worries. I quit ardour, went back to jack, stopped it, 
and decided it was time to test midi once and for all.

I opened a terminal and checked if any midi devices had been
detected/setup. 

```
$ ls /dev/*mid*
```

I had two midi devices listed- /dev/dmmidi and /dev/midi. Next
I tested to see if they were actually functional. 

```
$ cat /dev/midi
```

I pressed the buttons and controls and could clearly see the 
ozone was connected and being detected. I pressed-

```
ctrl-c
```

-to quit cat. So I knew the ozone was connected. Next I went
back to jack. I set it up for low latency but first clicking setup.

Inside setup I changed the server path to jackd. I left the realtime
box ticked and changed to Frames/Period to 128 for low latency
as well as the port maximum to 128. This brought my latency down
to 5.8ms. Next I clicked the > next to Input device and selected the
Ozone. I clicked the > next to Output device and selected the ozone 
again. It was device hw:0. 

So I hit okay, then started jack. I opened zynaddsubfx and then in Jack
clicked the CONNECT button. I switched to the MIDI tab, selected
Ozone on the left, selected Zynaddsubfx on the right, clicked 
connect, and guess what? ... when I pressed the keys they played
sound!!!!! When I moved the pitch wheel the pitch shifted. When I 
turned the 1 control knob, the volume when up and down.

Guys... it works!!! Our Ozone's are finally fully working with linux.

Anyway...as soon as it worked I came here and posted. Now I'm 
off to do some scoring. The sad thing is I'm currently still running 
the live disc. No working install yet, so in reality I'm probably gonna
have to get something installed and working. 

Totally report back if you can get similar results. We've all been working
at this for years and I'd love to see that everyone finally has a fully
funcitonal audio setup with linux with just their computer and m-audio
ozone. I'm back being happy again. Hope you guys will be too ;D

Mark.

---

### Post by maku-d on 2007-11-28
Okay...I decided to see if I could get this working 
in Ubuntu...and I did. It's heaps more convoluted 
than 64studio was, but it works so here's the steps. 

I did this straight off from a clean install, so 
anyone with ubuntu/kubuntu at any stage should 
be able to get their ozone working by following 
each step here. Here's the steps to get the ozone 
up and running-

01. Turn on and plug in your Ozone.

02. ```
$ cd /etc
```
03. ```
$ sudo grep -R "snd-usb-audio index" *
```
[INDENT]NOTE: my output was-> modprobe.d/alsa-base-options snd-usb-audio index=-2[/INDENT]

04. ```
$ cd modprobe.d
```
05. ```
$ sudo nano alsa-base
```
06. Find the line with snd-usb-audio and change the
[INDENT]index=-2 (or whatever yours was above) to index=0
[/INDENT]

07. Ctrl-O (as in the letter o) to save changes

08. Ctrl-X to quit nano

09. ```
$ sudo rmmod snd-usb-audio
```
[INDENT]NOTE: This might do nothing if it's not loaded[/INDENT]

10. ```
$ sudo modprobe snd-usb-audio
```

11. Download the madfuload for the Ozone from
[INDENT][http://usb-midi-fw.sourceforge.net/]("http://usb-midi-fw.sourceforge.net/")[/INDENT]
[INDENT]NOTE: I got version 1.2[/INDENT]

12. Navigate to the directory you downloaded madfuload to.

13. ```
$ sudo tar xvfz <madfuload archive file>
```
14. ```
$ cd <madfuload directory>
```
15. ```
$ sudo apt-get install build-essential
```
16. ```
$ make
```
17. ```
$ ./configure
```
18. ```
$ sudo make install
```
19. ```
$ sudo nano /etc/udev/rules.d/42-madfuload.rules
```

20. Comment out all lines (add a # to the front of them)

21. Add the line-
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2808", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin -D $env{DEVNAME}"
```
[INDENT]-to the end of the file.[/INDENT]

22. Ctrl-O (the letter o) to save the changes.

23. Ctrl-X to exit nano.

24. ```
$ sudo /etc/init.d/udev restart
```
25. ```
$ asoundconf list
```

26. Ozone should be in the list of available soundcards.

27. ```
$ asoundconf set-default-card Ozone
```

28. In Kubuntu I now went to sound prefs and 
[INDENT]chose the ozone as my midi interface.[/INDENT]

29. Test the playback through the Ozone.

30. ```
$ sudo apt-get install qjackctl
```
31. ```
$ sudo apt-get install zynaddsubfx
```
32. ```
$ sudo apt-get install linux-rt
```

33. Reboot
34. Open Jack Control (qjackctl)
35. Click setup
36. Change Server Path to jackd
37. Change Frames/Period to 128
38. Change Port Maximum to 128
39. Click the > next to 'input device' and choose hw:0 Ozone
40. Click the > next to 'output device' and choose hw:0 Ozone
41. Click OK to exit Setup.
42. Click the Start button in Jack
43. Open ZynAddSubFX select beginner (unless you know you want advanced)
44. Click Connect in Jack.
45. Click the midi tab.
46. Select the Ozone on the left, and ZynAddSubFX on the right, then click connect.
47. Close the Connect window
48. Play the keys on the Ozone keyboard and hopefully you should get sound
(If you don't, check that your speakers are on ;D  )
49. Use the connect method to route programs to the ozone as you need them.
50. Enjoy your working Ozone in Ubuntu!!!!


Hope this helps! Love to hear everyone's feedback. Hope everyone can get 
their Ozone's working and start doing some serious scoring. Well...I'm off 
to finally do some of my own scoring. Good luck all :D

Mark.

---

### Post by Aurora on 2007-12-09
Hello,

[edit] As of 12/11/07, I can start JACK using /usr/bin/jackd as the server file path, and using the default for both input and output.  But there is no sound from Rosegarden.

I did all of the above.  I had Kubuntu, madfuload 1.2, and the Ubuntu Studio meta package (with JACK and all the other sound apps) already installed, so I was able to skip those installation steps.  I note that the Sourceforge page where you download madfuload says that the particular version of the Ozone that I have, does not require the firmware, so maybe that's messing it up.  Also the line in /etc/udev/rules.d/42-madfuload.rules you posted was just slightly different from the one I already had; maybe I will try going back to the original.

The upshot is, the Ozone does not appear as an option in the KDE sound system MIDI dialog, and  JACK no longer starts.  So my system is more broken than before.  Luckily I still have Musix and 64 Studio installed on other partitions :)  I'm not going to touch those until I know what's breaking Ubuntu Studio.

In K-menu>System Settings>Sound System, I click the Hardware tab, and under 'Select Your MIDI Device, here are the options listed in the drop-down menu:
Midi Through Midi Through Port-0 - ALSA Device
TiMidity TiMidity Port 0 - ALSA Device
TiMidity TiMidity Port 1 - ALSA Device
TiMidity TiMidity Port 2 - ALSA Device
TiMidity TiMidity Port 3 - ALSA Device
Client-129 qjacktl -  ALSA Device

I tried selecting qjacktl and hitting 'apply'. The sound system fails to restart.

When I try to start JACK, I get different messages, depending on the server path.  With jackd:
12:33:31.594 Patchbay deactivated.
12:33:31.623 Statistics reset.
JACK tmpdir identified as [/dev/shm]
12:33:31.653 MIDI connection graph change.
12:33:31.839 MIDI connection change.
12:33:46.061 Startup script...
12:33:46.061 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
sound server terminated
12:33:46.291 Startup script terminated successfully.
12:33:46.291 JACK is starting...
12:33:46.291 jackd -v -R -P1 -dalsa -r44100 -p512 -n8 -D -Chw:1 -Phw:1
12:33:46.299 JACK was started with PID=7509 (0x1d55).
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
cannot create /dev/shm/jack-1000 directory (Permission denied)
cannot create server sockets
cannot create engine
cleaning up shared memory
cleaning up files
unregistering server `default'
12:33:46.312 JACK was stopped successfully.
12:33:46.313 Post-shutdown script...
12:33:46.313 killall jackd
jackd: no process killed
12:33:46.520 Post-shutdown script terminated with exit status=256.
12:33:48.355 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

With jackd-realtime:
12:38:23.362 Startup script...
12:38:23.362 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
12:38:23.590 Startup script terminated with exit status=256.
12:38:23.590 JACK is starting...
12:38:23.590 jackd-realtime -v -R -P1 -dalsa -r44100 -p512 -n8 -D -Chw:1 -Phw:1
12:38:23.592 Could not start JACK. Sorry.
12:40:46.381 JACK was stopped successfully.
12:40:46.382 Post-shutdown script...
12:40:46.383 killall jackd
jackd: no process killed
12:40:46.605 Post-shutdown script terminated with exit status=256.

Starting with /usr/bin/jackd is the same as jackd.

With jackstart:
12:45:45.653 Startup script...
12:45:45.653 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
12:45:45.879 Startup script terminated with exit status=256.
12:45:45.879 JACK is starting...
12:45:45.879 jackstart -v -R -P1 -dalsa -r44100 -p512 -n8 -D -Chw:1 -Phw:1
12:45:45.882 Could not start JACK. Sorry.
12:45:49.591 JACK was stopped successfully.
12:45:49.591 Post-shutdown script...
12:45:49.591 killall jackd
jackd: no process killed
12:45:49.811 Post-shutdown script terminated with exit status=256.

I hope some of that output is useful; I don't understand any of it.  Can you figure out whaat's going wrong?

Thanks,

Paul

---

### Post by Aurora on 2007-12-09
> **Aurora said:**
> 

 I'm not going to touch [64 Studio and Musix] until I know what's breaking Ubuntu Studio.


OK, I lied.  In 64 Studio,

pad@64studio:~$ ls /dev/*mid*
ls: /dev/*mid*: No such file or directory

pad@64studio:~$ asoundconf list
Names of available sound cards:
pad@64studio:~$


I booted with the keyboard plugged in and turned on.  Do I have to do something else to have this device detected?

FWIW,  I can control Xpand! instruments in Pro Tools, and Garage Band instruments, with this keyboard, so I know it works.

I'm truely puzzled.

--Paul

---

### Post by maku-d on 2007-12-20
It's surprising me that the ozone isn't being detected. Even without madfuload, when running lsusb you should be able to see your ozone. 

I also had mine working in 64studio without madfuload, before getting it up in ubuntu, so either way we should be able to get it going. Do you have an ubuntu installation anymore? Even if you don't we might be able to figure it out with your 64studio 2.0 live i386 disc (the one I used for testing).

---

### Post by Aurora on 2007-12-29
> **maku-d said:**
> It's surprising me that the ozone isn't being detected... Do you have an ubuntu installation anymore? Even if you don't we might be able to figure it out with your 64studio 2.0 live i386 disc (the one I used for testing).

Hi,

I do in fact have Ubuntu Studio Gutsy installed, as well as 64 Studio and Musix.  Tell me if this terminal output from Ubuntu Studio is helpful:

pad@Studio909:~$ sudo modprobe usb-audio
FATAL: Module usb_audio not found.
pad@Studio909:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0763:2019 Midiman 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04fc:0c15 Sunplus Technology Co., Ltd 

Am I missing usb-audio? Is that a kernel module, or what?  How would I get that installed?

It looks like the MIDI interface on the keyboard is being detected; Midiman is an M-Audio product.

I have subscribed to this thread so I won't miss posts again #-o

Enjoy your summer down there,

Paul in cold, drizzly Seattle

[Edit: I burned a copy of 64 Studio Live, 64 bit, since I'm using AMD 64.  The keyboard again does not show up in JACK, but I can play some soft synths through the Ozone using the QWERTY keyboard or the virtual keyboard]

---

### Post by Aurora on 2008-01-02
pad@Studio909:~$ lsmod | grep usb
usblp                  15616  0
snd_usb_audio          81408  0
snd_pcm                80644  4 snd_atiixp,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            18176  1 snd_usb_audio
snd_hwdep              10500  1 snd_usb_audio
snd_rawmidi            25728  2 snd_usb_lib,snd_seq_midi
snd                    55172  13 snd_atiixp,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usb_storage            73536  2
libusual               18704  1 usb_storage
ide_core              118980  3 ide_cd,usb_storage,atiixp
usbcore               139912  8 usblp,snd_usb_audio,snd_usb_lib,usb_storage,libusual,ohci_hcd,ehci_hcd
scsi_mod              148844  5 sbp2,sg,sd_mod,usb_storage,libata

Does this look right?

---

### Post by texas8112 on 2008-01-06
i am running a M-Audio Ozone with no problems what so ever. i am a complete noob. all i did was select it in the player. if anyone wants me to post some of my 'settings/configuration' or whatever let me know.

---

### Post by Aurora on 2008-01-07
> **texas8112 said:**
> i am running a M-Audio Ozone with no problems what so ever. i am a complete noob. all i did was select it in the player. if anyone wants me to post some of my 'settings/configuration' or whatever let me know.

OK, some questions:

When you say "running" the device, does that include monitoring audio, controlling soft synths and writing MIDI data in Rosegarden?  I would like to use the keyboard for composing in Rosegarden via JACK.. Today I regained the ability to hear media players and Ardour through the thing, but Rosegarden is still silent.

If you have JACK Control and Rosegarden insalled, try starting JACK Control, clicking the setup button, and seeing if the Ozone shows up in the Input and Output pulldown menu. Then, fire up Rosegarden, click on the File menu, and open one of the demo songs. Hit play; do you hear anything?

In JACK Control, does the keyboard show up in the MIDI tab when you click the "Connections" button?

---

### Post by ff-xubuntop on 2008-01-11
hi everyone,

first id like to thank all of you in this thread who did a lot of research to find out how to get ozone working. great work!

i have my ozone working now (on xubuntu 7.10), but i have a few things to add to the step-by-step instructions..

first of all, my ozone does not have the same product id as maku-d uses in his guide. mine is 2008 and not 2808. you can check the actual number by typing lsusb. im a complete newbie, but i suppose the udev rule should match this.

secondly, @aurora: midiman is just the former name of m-audio, that maybe they still use in the hardware. i dont think it means the midi part of ozone is recognized and not the audio. (and btw usb-audio should be snd-usb-audio)

lastly, it didnt work until i rebooted. doing udev restart wasn't enough.

hope it helps --and thanks again!

---

### Post by Aurora on 2008-01-12
I am glad to have Texas8112and ff-xubuntop on board. ff-xubuntop, do you have MIDI working with yours, or just audio?  I have partial audio (everything except Rosegarden), no MIDI.  I did have audio working with Rosegarden at one point, but lost it after applying the instructions in post #49. I have never had the MIDI recognized by any distro with this device.

I have long since changed udev rules to match my product number, 2019, and rebooted many times. snd-usb-audio is there, as you can see by  post #54.

--PD

---

### Post by Aurora on 2008-02-24
To anyone still following this thread:

I found out that a patch was added to the Linux kernel for this specific version of the Ozone in September.  Tim Gardner and Ben Collins on the Ubuntu kernel team have assured me that the patch will be part of the Hardy kernel.  I have tried patching my kernel myself, but the new patched kernel won't boot.  I'll just wait for Hardy to be released, rather than waste more and more hours on this.  For the intrepid and impatient, I think there's a way to get to the patch from here:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=2ea547dcdd4216370f00dd65a18ee5a0271646a0](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=2ea547dcdd4216370f00dd65a18ee5a0271646a0)

Happy music making,

Paul DeShaw

---

### Post by maku-d on 2008-02-24
Hey Aurora, this is great news for you. I've seen a couple of your posts around the place and saw that your Ozone wasn't the stock one, but rather some sort of academic version? It's a shame how much trouble you've had with it. It took me so long to get mine up and running and I was so happy once I had it working. I was experimenting with a Fedora 8 install the other day to try out CCRMA and my Ozone detected completely by default. MIDI support out of the box as well as Audio. When I then installed the CCRMA kernel it still worked perfectly. So it definitely wouldn't surprise me if that call about the patch for your variation of the Ozone actually does end up in the kernel (Might maybe have something to do with pulse audio also? Not that I'm really that technical, but the Fedora thing made me reflect on how many hours I'd spent in the past trying to get the Ozone up and running, to have it now working perfectly out of the box). 

Either way, I'm really looking forward to Hardy. Seeing as it's a long term release, I think it's going to make a great base for the Ubuntu Studio tools. I'm still working on that movie project and when scoring time comes around I'll definitely still be using my Ozone with only open source tools. 

Good luck man, it's nice to see how much persistence you've had with getting your Ozone up and running. I feel a little bad I've had mine working so long now and couldn't help get yours going, but now I don't have to stress that I didn't know the solution for you. Cheers- :guitar:

---

### Post by Nobre on 2008-04-21
Hi... Im trying to get my Ozone working... 
I do every line of code mentioned here... but no sucess...
In my lsusb, the ozone was recognized... but with asoundconf list, only my onboard card are there.

WHAT SHOULD I DO?

Im using Hardy Heron, with all latest updates, and ubuntu-studio packages... including linux RT kernel used by default.

Im really need some help to forget all comercial apps for producing music and use 100% GNU/Linux and free softwares as my studio and tools.

Thanks a lot...
Sorry about my english...

---

### Post by Aurora on 2008-04-22
> **Nobre said:**
> Hi... Im trying to get my Ozone working... 
I do every line of code mentioned here... but no sucess...
In my lsusb, the ozone was recognized... but with asoundconf list, only my onboard card are there.

WHAT SHOULD I DO?

Im using Hardy Heron, with all latest updates, and ubuntu-studio packages... including linux RT kernel used by default.

Im really need some help to forget all commercial apps for producing music and use 100% GNU/Linux and free softwares as my studio and tools.

Thanks a lot...
Sorry about my english...

It was my understanding that these problems would be fixed with the release of Hardy Heron. I can only suggest joining the Ubuntu Studio User's List and asking there:

[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-Studio-users](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-Studio-users)

It may also be helpful to file a bug report.  I don't know how to do that.

Your English is better than my Portuguese will ever be...you might also try working with the Musix distribution-- [http://www.musix.org.ar/](http://www.musix.org.ar/)  Quoting Wikipedia:

"Because Musix is developed by a team from Argentina, Spain and Brazil, the main language used in development discussion and documentation is Spanish. Musix has its own community of users in Spanish, Portuguese and in English."

I find the language difference difficult, but you might be more at home in that community.  I do have problems with my Ozone in Musix, though.

If you install Musix, and keep Ubuntu Studio in another partition, you will have to do some tricks to get Ubuntu to boot.

---

### Post by maku-d on 2008-04-22
Hi all, just thought I'd come on and say I'm planning to download Hardy when it gets released in a couple of days. Will install the drivers again and check if there're any quirks. Either way I'll repost the steps I use to successfully configure it. 

Back soon :guitar:

---

### Post by maku-d on 2008-04-22
Nobre, did you install the madwifi driver successfully?

---

### Post by Nobre on 2008-04-22
> **Aurora said:**
> It was my understanding that these problems would be fixed with the release of Hardy Heron. I can only suggest joining the Ubuntu Studio User's List and asking there:

[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-Studio-users](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-Studio-users)

It may also be helpful to file a bug report.  I don't know how to do that.

Your English is better than my Portuguese will ever be...you might also try working with the Musix distribution-- [http://www.musix.org.ar/](http://www.musix.org.ar/)  Quoting Wikipedia:

"Because Musix is developed by a team from Argentina, Spain and Brazil, the main language used in development discussion and documentation is Spanish. Musix has its own community of users in Spanish, Portuguese and in English."

I find the language difference difficult, but you might be more at home in that community.  I do have problems with my Ozone in Musix, though.

If you install Musix, and keep Ubuntu Studio in another partition, you will have to do some tricks to get Ubuntu to boot.

Thanks dude!
I got the Ozone working with Ubuntu Studio 8.04 (beta) but without the 
2.6.24-16-rt kernel (preempt)... I change back to the 2.6.24-16-generic and its works perfectly! :guitar:
Now I will try to correct this things in realtime kernel, because the low-latency kernel is so better to work with audio, I think...:confused:

I think thats anything about snd-usb-audio does not load with madfuload driver (ozone driver) with this kernel... but I have a low knoledge to track kernel isssues/errors...



See you!

---

### Post by Nobre on 2008-04-22
> **maku-d said:**
> Nobre, did you install the madwifi driver successfully?

I use atheros drive for my wifi card.

---

### Post by Nobre on 2008-04-22
Theres something strange here!  :confused:

Now... Its not working again... still using 2.6.24-16-generic instead of 2.6.24-16-rt...  DOES NOT WORK ANYMORE! :mad::mad:

The most strange thing is about lsusb.
I restart few times and the used bus changes... and the vendorID and productID changes...

> 
anobre@mariri:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 005: ID 0763:2008 Midiman** 
Bus 001 Device 001: ID 0000:0000  

SOMETIMES 0763:2008 AND OTHERS 0763:2808...  
I think that is way the driver cant load, with parammmeters passed by /etc/udev/rules.d/42-madfuload.rules :-k
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2808", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin -D $env{DEVNAME}"
```

If I try to use madfuload manualy... and change this values to the actual, I got this:

> control transfer failed: (32) Broken pipe
control transfer failed: (32) Broken pipe
control transfer failed: (32) Broken pipe
downloading block 0 failed


Whata hell!](*,)
I dont know what to do anymore!   May I put this Ozone into the trash?

----
EDITED: 
Since I wrote this post...
I got the Ozone working back... just rebooting the Ubuntu with de Ozone turned on.
Dammmn it!  I really can't know what is wrong with de firmware loader and the Ubuntu.
Now I will try to use RealTime Kernel again, to check if theres some relation with it.
May be something wrong, with madfuloader and udev...

---

### Post by Aurora on 2008-04-22
Yes, always boot the Ozone first, then the computer.

FWIW, I posted a link to this thread on the Ubuntu Studio User's list.  Some of the devs might be interested, and maybe some of these fixes could be integrated into a future release.

---

### Post by Nobre on 2008-04-22
> **Aurora said:**
> Yes, always boot the Ozone first, then the computer.

FWIW, I posted a link to this thread on the Ubuntu Studio User's list.  Some of the devs might be interested, and maybe some of these fixes could be integrated into a future release.


I always boot the Ozone first... but I just can get it working when I boot Ozone, boot ubuntu and reboot ubuntu... and if the idvendor and idproduct is changed in lsusb, theres no sucess... 

Too buggy!

---

### Post by Nobre on 2008-04-23
AGAIN.. MY ENGLISH IS SO POOR... SO SORRY!

I really am convinced about this problem with idvendor and idproduct at powering Ozone and the UDEV.

When the OS identifies as **ID 0763:2808 Midiman**, I can't get Ozone working. 
But if the OS get **ID 0763:2008 Midiman**... great... it works! so, the madfuload driver could be running only if this ID's is correct!

I found how to do Ozone get the working ID. It was by attempt and error.](*,)
Power on Ozone, boot Ubuntu, check USB bus with lsusb, type this code:
```
sudo madfuload -D /proc/bus/usb/00X/00X -f /usr/local/share/usb/maudio/ma008100.bin --nowait -v
```
where **X** are the numbers listed by lsusb command.
I dont know why, but this code changes the ID from **ID 0763:2808 Midiman** to **ID 0763:2008 Midiman**.
But it still doesnt working until reboot and keeping Ozone powered on. A udev restart doesnt solve the problem.

Im trying to discover what should we do to get this results automatically in **/etc/udev/rules.d/42-madfuload.rules** at startup.:-k

Im not a developer, or GNU/Linux geek... Could anybody suggests me a code for this things?

Thanks a lot... 
I hope this tip helps somebody also.

---

### Post by Aurora on 2008-04-25
In light of what Nobre has been going through, I cancelled my upgrade to Hardy before it finished downloading (even though the download ran overnight...Ubuntu's servers are slow right after a new release).  I am thinking of doing a clean install onto another partition so I don't break anything in my current installation, which at least has audio working.

--Paul

---

### Post by HaightsW on 2008-04-25
> **Nobre said:**
> AGAIN.. MY ENGLISH IS SO POOR... SO SORRY!

I really am convinced about this problem with idvendor and idproduct at powering Ozone and the UDEV.

When the OS identifies as **ID 0763:2808 Midiman**, I can't get Ozone working. 
But if the OS get **ID 0763:2008 Midiman**... great... it works! so, the madfuload driver could be running only if this ID's is correct!

I found how to do Ozone get the working ID. It was by attempt and error.](*,)
Power on Ozone, boot Ubuntu, check USB bus with lsusb, type this code:
```
sudo madfuload -D /proc/bus/usb/00X/00X -f /usr/local/share/usb/maudio/ma008100.bin --nowait -v
```
where **X** are the numbers listed by lsusb command.
I dont know why, but this code changes the ID from **ID 0763:2808 Midiman** to **ID 0763:2008 Midiman**.
But it still doesnt working until reboot and keeping Ozone powered on. A udev restart doesnt solve the problem.

Im trying to discover what should we do to get this results automatically in **/etc/udev/rules.d/42-madfuload.rules** at startup.:-k

Im not a developer, or GNU/Linux geek... Could anybody suggests me a code for this things?

Thanks a lot... 
I hope this tip helps somebody also.


Sobre,
I can confirm my computer (also UbuntuStudio, Hardy rt kernel) behaved exactly as you described since I upgraded yesterday. I could actually get Ozone loading automatically by changing the udev rule a tiny little bit (removing "_device" from the SUBSYSTEM identifier):

Replace:
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2808", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin -D $env{DEVNAME}"
```

With: 
```
ACTION=="add", SUBSYSTEM=="usb", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2808",  RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin -D $env{DEVNAME}"
```

And yes indeed, lsusb sees 0763:2008 and udev is set to 0763:2808, go figure! :confused: I hope this bit of black magic works for you as well.
Good luck!

---

### Post by Nobre on 2008-04-25
> **HaightsW said:**
> Sobre,
I can confirm my computer (also UbuntuStudio, Hardy rt kernel) behaved exactly as you described since I upgraded yesterday. I could actually get Ozone loading automatically by changing the udev rule a tiny little bit (removing "_device" from the SUBSYSTEM identifier):

Replace:
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2808", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin -D $env{DEVNAME}"
```

With: 
```
ACTION=="add", SUBSYSTEM=="usb", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2808",  RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin -D $env{DEVNAME}"
```

And yes indeed, lsusb sees 0763:2008 and udev is set to 0763:2808, go figure! :confused: I hope this bit of black magic works for you as well.
Good luck!

**HaightsW**,
1- Do you need to boot the Ubuntu with Ozone powered on?
2- What about power of Ozone and power on again, without a Ubuntu shutdown?

Thanks, 

Nobre.
[email]nobre.it@gmail.com[/email]

---

### Post by Aurora on 2008-04-25
> **HaightsW said:**
> ... I could actually get Ozone loading automatically by changing the udev rule a tiny little bit (removing "_device" from the SUBSYSTEM identifier):

Replace:
```
ACTION=="add", SUBSYSTEM=="usb_device"...
```

With: 
```
ACTION=="add", SUBSYSTEM=="usb"...
```


Odd indeed.  I still run Gutsy, and the udev rule says "usb_device". Everything works except MIDI.  I'm going to wait a bit before installing Hardy, at least on my main computer. This is scaring me.

---

### Post by HaightsW on 2008-04-26
Hi Nobre,
Upon reboot, Ozone is seen as 0763:2008 regardles of being ON at bootime or fired up afterwards; everything works peachy either way. If I then power cycle Ozone, it changes to 0763:2808 and no longer works. That's strange, but tolerable for my use.

---

### Post by Chang An on 2008-05-04
I had my ozone working fine in Gutsy.  When I tried to install the madfuload 1-2 driver in a fresh install of Hardy I get this error message after running ./configure

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

add if I try to go on an run make it says there is not a make file.  Any ideas.

Here is the config.log too.  I can't make since of it.

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by madfuload configure 1.2, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = jondoe-laptop
uname -m = x86_64
uname -r = 2.6.24-16-rt
uname -s = Linux
uname -v = #1 SMP PREEMPT RT Thu Apr 10 14:04:43 UTC 2008

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1316: checking for a BSD-compatible install
configure:1371: result: /usr/bin/install -c
configure:1382: checking whether build environment is sane
configure:1425: result: yes
configure:1482: checking for gawk
configure:1511: result: no
configure:1482: checking for mawk
configure:1498: found /usr/bin/mawk
configure:1508: result: mawk
configure:1518: checking whether make sets $(MAKE)
configure:1538: result: yes
configure:1750: checking for gcc
configure:1766: found /usr/bin/gcc
configure:1776: result: gcc
configure:2020: checking for C compiler version
configure:2023: gcc --version </dev/null >&5
gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2026: $? = 0
configure:2028: gcc -v </dev/null >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
configure:2031: $? = 0
configure:2033: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2036: $? = 1
configure:2059: checking for C compiler default output file name
configure:2062: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2065: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "madfuload"
| #define PACKAGE_TARNAME "madfuload"
| #define PACKAGE_VERSION "1.2"
| #define PACKAGE_STRING "madfuload 1.2"
| #define PACKAGE_BUGREPORT "usb-midi-fw-user@lists.sourceforge.net"
| #define PACKAGE "madfuload"
| #define VERSION "1.2"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2104: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/alex/madfuload-1.2/missing --run aclocal-1.8'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/alex/madfuload-1.2/missing --run tar'
AUTOCONF='${SHELL} /home/alex/madfuload-1.2/missing --run autoconf'
AUTOHEADER='${SHELL} /home/alex/madfuload-1.2/missing --run autoheader'
AUTOMAKE='${SHELL} /home/alex/madfuload-1.2/missing --run automake-1.8'
AWK='mawk'
CC='gcc'
CCDEPMODE=''
CFLAGS=''
CPPFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EXEEXT=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/alex/madfuload-1.2/missing --run makeinfo'
OBJEXT=''
PACKAGE='madfuload'
PACKAGE_BUGREPORT='usb-midi-fw-user@lists.sourceforge.net'
PACKAGE_NAME='madfuload'
PACKAGE_STRING='madfuload 1.2'
PACKAGE_TARNAME='madfuload'
PACKAGE_VERSION='1.2'
PATH_SEPARATOR=':'
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
UDEV_RULES_DIR=''
VERSION='1.2'
ac_ct_CC='gcc'
ac_ct_STRIP=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__include=''
am__leading_dot='.'
am__quote=''
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${prefix}/share'
exec_prefix='NONE'
host_alias=''
includedir='${prefix}/include'
infodir='${prefix}/info'
install_sh='/home/alex/madfuload-1.2/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
mkdir_p='mkdir -p -- .'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE "madfuload"
#define PACKAGE_BUGREPORT "usb-midi-fw-user@lists.sourceforge.net"
#define PACKAGE_NAME "madfuload"
#define PACKAGE_STRING "madfuload 1.2"
#define PACKAGE_TARNAME "madfuload"
#define PACKAGE_VERSION "1.2"
#define VERSION "1.2"

configure: exit 77
I'm sorry for how log that was. Any help would be great:)

---

### Post by Nobre on 2008-05-07
Chang An,

You need to install build-essential package

```
sudo apt-get install build-essential
```

Cya!

---

### Post by Chang An on 2008-05-12
> **Nobre said:**
> Chang An,

You need to install build-essential package

```
sudo apt-get install build-essential
```

Cya!

Thanks.  
I think the build-essential package should be installed by default.  After I installed the madfuload driver and I cut and pasted the ozone setting (which is what I had to go to get it working in Gutsy)  I went to jack and I could not find the the ozone.  Does anybody have the ozone working in Hardy?  If so, I would greatly appreciate and explanation of what you did to get there.

---

### Post by Nobre on 2008-05-12
Chang An,

After a fresh install in my new notebook, I compile madfuloader into Hardy Heron and my Ozone now works as never before!  Awsome!:guitar:
I just power on Ozone and...  powwww!  Its working!
I dont need to boot Hardy with Ozone already powered... Now I can plug and play at any time I want.

I hope the things work with you too.

Cya!

---

### Post by luissp on 2008-05-22
After a fresh install a do not have my ozone working but...
INCREDIBLE!!! I have it working now for some days. The system recognizes it as never before. Really plug and play (and no need to pray). I'll try to explain the proccess, but I'm quite newbie (though I was fighting with my ozone since edgy).

I made a fresh install of UbuntuStudio and madfuload in my old notebook. Bad choice. Problems with wireless, with my external HD... and of course with the ozone ](*,)](*,)so I decided to begin and install Ubuntu Hardy and after that the UbuntuStudio Packages (omitting desktop and menus 'cause I don't feel confortable with them).

After installing madfuload I got no sound from the ozone ](*,)](*,). It was in lsusb but not recognized by alsa . Lookin in the 'forii' for similar problems with USB interfaces I found this I don't remember where (sure you can find it, but I'll reproduce it):
```

Setup VirtualBox USB Support:
USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:
sudo gedit /etc/init.d/mountdevsubfs.sh
You'll see a block of code that looks like this:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
Now uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Ok now logoff, then log back in so the vbox driver see's you are logged in to the vboxusers group.

If the above doesnt work try rebooting.......
```

It follows with more instructions, but for me it's all. I don't remember if I need to reboot, and may be I had to make "ozone" the default card, but when you make:
```
>asoundconf list
```
and you get:
```
Names of available sound cards:
SI7012
Ozone

```
:shock::shock::shock:

The sun rises again for my ozone :lolflag:

---

### Post by Aurora on 2008-05-24
Congratulations on your success, but there are some things I don't understand. The code you quoted was for configuring VirtualBox, but you didn't mention anything about installing it. Did you install Ubuntu in VirtualBox or directly on your hardware?  

And, how exactly do you install the Ubuntu Studio packages without the desktop and menus?

-Paul

--Paul

---

### Post by luissp on 2008-05-25
Paul,

Sorry if I mislead you with the reference to VirtualBox. My setup is nothig to do with VirtualBox. I only got the idea from other forum.

As I tried to describe in my post:
 1. I installed Ubuntu Hardy.
 2. then added the UbuntuStudio Packages via Synaptic (leaving out packages like ubuntustudio-desktop, ubuntustudio-look... and so)
 3. and then installed madfuload.
 4. After that I midified the /etc/init.d/mountdevsubfs.sh as I explained in the post.

I hope it helps,
Luis

Here you are the ubuntustudio packages i've installed:
ubuntustudio-graphics
ubuntustudio-audio-plugins
ubuntustudio-video
ubuntustudio-menu
ubuntustudio-audio
ubuntustudio-controls

---

### Post by Aurora on 2008-05-25
> **luissp said:**
> Paul,

Sorry if I mislead you with the reference to VirtualBox. My setup is nothig to do with VirtualBox...
Here you are the ubuntustudio packages i've installed:
ubuntustudio-graphics
ubuntustudio-audio-plugins
ubuntustudio-video
ubuntustudio-menu
ubuntustudio-audio
ubuntustudio-controls

Thanks, that is quite helpful. Somehow I had the impression you couldn't use USB with VirtualBox, but now I see it's possible. I might just try installing in VirtualBox to see how things work, before deciding between an upgrade or a clean install.

---

### Post by luissp on 2008-05-25
Aurora,

I'm afraid my English is not as clear as I think :-k. I do not use VirtualBox. Before you do anything complicated I recommend you to edit the file /etc/init.d/mountdevsubfs.sh in the way of my first post. It's easy and I think it would work (and you can turn around easy too).

The error about using VirtualBox is because I cut & paste the code of my post from a VirtualBox forum.

---

### Post by Aurora on 2008-05-29
> **luissp said:**
> Aurora,

I'm afraid my English is not as clear as I think :-k. I do not use VirtualBox....

I understand that you do not use VirtualBox.  I thank you for giving me the idea to use VirtualBox, even though you do not use it yourself. With VirtualBox, I can try out Hardy without changing anything in my Gutsy install.  That way, there is no risk of breaking anything.  Many people have had problems with recent Ubuntu upgrades breaking things.  Earlier upgrades were easy and painless, but the last two releases have been troublesome.

So, even though you were not suggesting I use VirtualBox, I might try it anyway, to keep my system safe while I try out the newest Ubuntu version.

--Paul

---

### Post by Aurora on 2008-06-04
Greetings,

On June 4th,2008 at approximately 19:50 Pacific time, I heard sounds while pressing a key with the Ozone plugged into a Linux machine for the first time.

I also recorded some voice into Audacity using a mic plugged into it.  It was very noisy, but it did work; played back and recorded through the device.
 
I have not tried Hardy on my desktop yet, but I installed it on my Intel Mac laptop, and discovered the keyboard is detected out of the box, without installing madfuload. 

I have yet to try Rosegarden, which has its own issues: getting sound out of it is a major pain.  But at least I know that ALSA, JACK, and ZynAddSubFX will work with this device.:D

Thanks for all the help an support on this forum. This community rocks.

--Paul

---

### Post by fred@forte-systems.com on 2008-06-22
Greetings, 

Thnaks for all the great help here, I've also gotten my ozone working (mostly, see below) using the info here.

I did have to do the /dev to /proc change and make edits to the 42-mafuload.rules file, etc.

I'm wondering if alsamixer works wth the ozone.  I can't seem to get it to respond. Let me know if I should repost this in  a new thread.

I get the following whenever I try to run it:

fredimac@musicmaker:~$ alsamixer -D hw:0
No mixer elems found

Results of cat /proc/asound/pcm

00-00: USB Audio : USB Audio : playback 1 : capture 1
01-04: Intel ICH - IEC958 : Intel ICH5 - IEC958 : playback 1
01-03: Intel ICH - ADC2 : Intel ICH5 - ADC2 : capture 1
01-02: Intel ICH - MIC2 ADC : Intel ICH5 - MIC2 ADC : capture 1
01-01: Intel ICH - MIC ADC : Intel ICH5 - MIC ADC : capture 1
01-00: Intel ICH : Intel ICH5 : playback 1 : capture 1


alsamixer works with the Intel using the command alsamixer -D hw:1

Really what I'm looking for is a way to control volume and EQ for all apps when not running jack.  Currently only the volume control in individual applications work.


Thanks in advance,
Fred

---

