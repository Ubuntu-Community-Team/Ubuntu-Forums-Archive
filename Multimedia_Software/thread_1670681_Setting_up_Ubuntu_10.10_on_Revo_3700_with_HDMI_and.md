---
title: "Setting up Ubuntu 10.10 on Revo 3700 with HDMI and XBMC"
date: 2011-01-19
forum: Multimedia Software
---

### Post by ernz on 2011-01-19
**_[COLOR="Red"]IMPORTANT UPDATE: READ FIRST[/COLOR]_**
[COLOR="Red"]
As of 12.04 LTS, all of these issues are addressed and everything works perfectly. If you still experience intermittent WiFi drops, try updating your routers firmware - that fixed it for me.

------------[/COLOR]

It took me much longer than it should have to set up my new media box over HDMI. I've collected some good instructions from several other posts and forums in a single how-to to help any other newbies.

My media box is a Acer Revo 3700 with Nvidia ION chipset. There appears to be problems with primarily with audio over HDMI and system halting issues. HD video's also don't work by default in Youtube and BBC IPlayer. Fixes below.

Note: CTRL+SHIFT+c or v will copy and paste in terminal

[SIZE="4"]1) Installing Ubuntu[/SIZE]
I used 10.10 (Maverick). Installed from LiveCD. Wireless and ethernet worked out of the box for me.

[SIZE="4"]2) Install Restricted Drivers[/SIZE]
System > Administration > Additional Drivers
Activate the driver for NVidia and restart your machine. If the system hangs (halting issue) then press and hold the power button on the Revo for around 6 seconds to restart.

[SIZE="4"]3) Fix Restarting Issue[/SIZE] [COLOR="Red"][Don't do this if you use the Revo's wireless - It causes intermittent wifi drops][/COLOR]
[s]There appears to be some sort of issue with the wireless driver causing a system crash on halt. To fix you need to blacklist an item in the modprobe.
Open Applications > Accessories > Terminal and type:[/s]
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
[s]Enter your password and in this new file, type:[/s]
```
blacklist rt2800pci
```
[s]Save the file and restart (Pressing and holding Revo power if necessary). Your Revo should now restart without incident in future.[/s]

[SOURCE]("http://www.ebuyer.com/product/236579")

[SIZE="4"]4) Audio over HDMI[/SIZE]
It seems as though the audio drivers aren't quite mature enough yet to work flawlessly out of the box on this model which is a real ball-ache. We need to do a bit of tinkering to make them work...

First, in the terminal type:
```
sudo gedit ~/.asoundrc
```
Enter your password and in this file paste the following:
```
pcm.dmixer {
type dmix
ipc_key 2048
slave {
pcm "hw:1,7" # Always use pure hw. dmix will reformat/resample audio.
period_size 512 # If you get stuttering/or non-working audio, fiddle around with these
buffer_size 4096
rate 48000 # HDMI, I'll assume 48kHz
format S16_LE # Should be default for pretty much any soundcard.
}
bindings {
0 0
1 1
}
}

pcm.!default {
type plug
slave.pcm dmixer
} 
```
Save and close. 
[SOURCE]("http://ubuntuforums.org/showthread.php?t=1625530&highlight=revo+3700&page=2") (thanks asdf29)

Now, again in the terminal enter:
```
alsamixer
```
You will see this:
[IMG]http://i.imgur.com/RKTYZ.png[/IMG]

Press F6 to select device. Use arrow keys and enter to select 1. HDA Nvidia:
[IMG]http://i.imgur.com/Zwh1H.png[/IMG]

You can now see SPDIF outputs. Just set them all to enabled (00) from muted (mm) by using the arrow keys to select and the 'm' key to change:
[IMG]http://i.imgur.com/NDnWU.png[/IMG]

Now restart and check that your audio is working. If you still aren't hearing anything, ensure the audio is turned up on the HDMI device, the HDMI cable is plugged in fully and that you are actually playing a sound. Double-check that those PFDIF channels are unmuted in alsamixer! Headphone jack will work to test if something is actually playing. The audio controls (up, down, mute) don't yet work using this method, but I have been getting by using the XBMC volume control and TV volume. Additionally, check that your ALSA version is at least 1.0.23. If it's not follow the tutorial [here]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules") to upgrade.

[SIZE="4"]4) Install XBMC[/SIZE]

Currently, boxee, vlc, totem and flash plugin don't appear to offer hardware acceleration for the ION chipset, but fortunately the Dharma release of XBMC does. This is REALLY good news if you're wanting to play those x264 1080p MKVs!

Run the following from terminal to install XBMC Dharma.

```
sudo add-apt-repository ppa:lars-opdenkamp/xbmc-pvr
sudo apt-get update
sudo apt-get install xbmc libva1
```

[SOURCE]("http://www.loggn.de/ubuntu-xbmc-10-0-dharma-pvr-repository/")

If you find that lines or "flicker" appear across the screen whilst playing video in XBMC then you may be able to fix this by disabling compiz. 

Do do this, go to System > Preferences > Appearance > Visual Effects > None
OR
For temporary deactivation of compiz run (ALT + F2):
```
metacity --replace
```

[SIZE="4"]5) BBC IPlayer[/SIZE]

You can add the BBC IPlayer plugin for this version of XBMC. It will allow you to watch IPlayer right inside XBMC at all sorts of definitions. To do this, download the plugin from [here]("http://code.google.com/p/xbmc-iplayerv2/"). Extract the folder, rename the extracted folder from "IPlayer" to "plugin.video.iplayer". Copy this folder to /home/<yourusername>/.xbmc/addons/ 
If you can't see the ".xbmc" folder then press CTRL + H to show hidden directories. (Folders prefixed with . are hidden in Ubuntu).
Restart XBMC and you'll find the player under Videos > Video Add-ons > IPlayer (Right clicking any of the menu items will add this to the favourites menu which allow you to go straight to this menu from Favourites on the home page of XBMC. 

Note that if sound is REALLY quiet, bring the sound up on the Ubuntu desktop AND XBMC. Just hit backslash to minimize XBMC.

[SOURCE]("http://code.google.com/p/xbmc-iplayerv2/")

[SIZE="4"]6) Youtube HD Videos[/SIZE]

There's a version of Adobe Flash Player out there, version 10.2. It (kind of) supports hardware acceleration with the ION 2. Using this method I have managed to get 720p videos to play in full screen without any problems. 1080p playback is still a bit flaky. Install 10.2 by running:

```

wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p2_32bit_linux_111710.tar.gz
tar zxvf flashplayer10_2_p2_32bit_linux_111710.tar.gz
sudo cp libflashplayer.so /usr/lib/flashplugin-installer/

```

Restart Firefox and check out a 720p or 1080p video on Youtube.

[SOURCE]("http://www.multimediaboom.com/install-adobe-flash-player-10-2-beta-in-ubuntu-windows/") 

**Important:**
[s]Running an automated update appears to break the system and prevents it from rebooting. It seems to just hang on reboot with a flashing cursor. I suspect a broken update so I'm holding off updates for a while until this device is a bit better supported. I disabled the automatic update in System > Startup Applications (probably a bad idea from a security POV).[/s] Feedback or improvements on methods used above would be appreciated.

**UPDATE 2011-01-21**
I ran an update and it all worked without incident this time. Doesn't break on start up any more.
**UPDATE 2011-01-22**
Added instructions for BBC IPlayer and HD Youtube support.
**UPDATE 2011-01-24**
Removed the restart fix as it causes an intermittent wifi fault.

---

### Post by pablo0151 on 2011-01-19
Hi

Just wanted to say a huge thanks for your info this topic, it's been bugging me for some time now and it's amazing to finally get some sound on the go.

Thank you again, the level of help and expertise on this forum is immense.

Cheers

Paul

---

### Post by ernz on 2011-01-21
You're welcome. Let me know if you find any more fixes or issues and I can add them to the main post.

---

### Post by scp93ch on 2011-02-01
That's a really useful set of instructions.
I have the same computer and also want to use XBMC, iPlayer and YouTube.  

My remaining problem though is the sound - I can't seem to get it to work through HDMI.  I have followed your instructions exactly (though I have no understanding of what it all actually means) but wonder if the reason it is not working is because I have other settings wrongly configured.

I'd be really grateful if you could add to your instructions what settings you have in the desktop System/Preferences/Sound settings GUI and in the XBMC sound configuration.

Thanks.

---

### Post by buster2209 on 2011-02-10
Did you use 32 or 64 bit ubuntu?

**[COLOR="Red"]EDIT:[/COLOR]** Never mind. I just read that the wireless in 64 bit Meerkat doesn't work and there is no fix..

[http://ubuntuforums.org/showpost.php?p=10153050&postcount=3](http://ubuntuforums.org/showpost.php?p=10153050&postcount=3)

---

### Post by _karel_ on 2011-03-02
Wireless works perfect for me in Maverick Meerkat 64 bit

---

### Post by ernz on 2011-03-27
> **scp93ch said:**
> That's a really useful set of instructions.
I have the same computer and also want to use XBMC, iPlayer and YouTube.  

My remaining problem though is the sound - I can't seem to get it to work through HDMI.  I have followed your instructions exactly (though I have no understanding of what it all actually means) but wonder if the reason it is not working is because I have other settings wrongly configured.

I'd be really grateful if you could add to your instructions what settings you have in the desktop System/Preferences/Sound settings GUI and in the XBMC sound configuration.

Thanks.

Does sound work outside of XBMC? Have you definitely enabled all nvidia devices in the sound config as shown?

---

### Post by jmkemp on 2011-03-27
Thanks for the clear instructions. 

I've been following various instructions for days trying to get the sound to work on the HDMI on my Acer R3700 (which doesn't run XBMC). These instructions got me sound through the aplay command line, but still not working in various applications. 

In the end a very simple thing helped. In System > Preferences > Sound there is a checkbox at the bottom of the 'Sound Effects' tab that says 'enable window and button sounds'. Once I'd ticked it all the sounds worked in applications. Certainly worth adding in as a last thing to check.

---

### Post by slacker69 on 2011-04-07
ernz can I just say a huge thanks!  The HDMI audio portion of this was driving me nuts but now its finally fixed!!  yay!! 

For the person it didnt work for use terminal, in your home dir do a "ls -a" ensure .asoundrc exists and check it isnt empty, you can do "more .asoundrc" and this should display the contents.  I actually made a mistake the first time myself and accidentially typed "/~.asoundrc" which give me a file called "~.asoundrc" rather than ".asoundrc".

Anyway awesome post and thanks again ernz!!!

---

### Post by jlivin25 on 2011-06-27
Hi Enrz & All
 
I'm just logging in here as it looks like this is the best place to be for help on this one, i've got a revo3700 and i've installed Ubuntu 10.10 and thought i was likely to get issues but as i'm a complete NOOB i thought i'd just give it a go and learn as I go.
 
I had been running XBMC on Windows 7 which was stable but was very frustrating to get 'everything to work' i've only had Ubuntu for two days and its already much much faster and more responsive in both running XBMC but also in startup, sleep and shut down.
 
I've used load of different web pages for help and workarounds and have started using 'terminal' to carry out certain install etc but locations of things and how to open are still very unfamiliar.
 
nVidia drivers have been installed successfully but the issue i'm still having that i cant resolve myself at the moment from this and other pages is the issue with sound over HDMI.
 
I followed Ernz's (thanks so much for this much appreciated from a NOOB) instructions and they worked as detailed without fault apart from not allowing sound over HDMI and i don't know how to fix this, oviously a media server without sound isn't much good :(
 
apart from the instuctions at the top of this thread are there any other settings i need to alter to get the sound over the HDMI, in 'sound outputs' within Ubuntu? or from settings->system in XBMC as the options have confused me a little and some help would be much appreciated.:confused:
 
I am happy to post any details from my system (if you can hint how lol), again please excuse the NOOBness :P
 
as stated i'm running:
 
Acer Aspire Revo3700
Ubuntu 10.10 64-bit
Installed proprietory Nvidia Graphics Drivers
Installed all availiable system updates (update manager)
Installed / edited workaround to prevent shutdown issues
Installed / edited Ernz's sound over HDMI fix
(only thing different was that 'blacklist' file exists already with code in it so i copied in the code from Ernz at the end of the file, not outside and brackets that i could see)
 
Update:
in fit of experimentation i also tried messing about with the code below to try differnt pcm devices that were listed under 'alsamixer' when pressing F2, from
 
pcm "hw:1,7" # Always use pure hw. dmix will reformat/resample audio. # original
 
to one each of the followign at a time
 
pcm "hw:1,3" # Always use pure hw. dmix will reformat/resample audio. # a HDMI device listed under F2->PCM
pcm "hw:1,8" # Always use pure hw. dmix will reformat/resample audio. # a HDMI device listed under F2->PCM
pcm "hw:1,7" # Always use pure hw. dmix will reformat/resample audio. # a HDMI device listed under F2->PCM

Thanks
 
James (trying but failing to help himself)

---

### Post by mistergoomba on 2011-11-07
I have the latest version of Ubuntu (11.10) installed and am still having problems with sound. I know it can't be the HDMI connection because I'm getting video. Are there any known issues with this method and Oneiric?

---

### Post by wildmanne39 on 2011-11-07
Hi, if you are using a nvidia card you can have a look at this link it may help.
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)

Please let us know if it does or not work because it is still a work in progress.
Thank you

---

### Post by mistergoomba on 2011-11-09
So, the first things I noticed was that a lot of the output in the test scenarios seemed correct. I followed some of the steps anyway and still no luck. Something went wonky, though:

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

However, I only have this file:
/proc/asound/NVidia/eld#1.0

Which your guide indicates is for device 7

---

### Post by wildmanne39 on 2011-11-09
Hi, thank you for posting back you show you solved your issue, will you please post here how you solved it.

---

### Post by mistergoomba on 2011-11-09
I'm sorry, I wasn't able to get it to work. I'm afraid I may have made it worse

---

### Post by BicyclerBoy on 2011-11-09
If you use modprobe option probe_mask for snd-hda-intel...this results in a remapping of the alsa logical device names (aplay -l) & the /proc filesystem filenames.

For example if you have hw:1,[3, 7, 8, 9] & used a probe_mask = 0x08 then alsa aplay -l will report
hw:1,3 but this is linked to /proc/asound/card1/eld#3.0
```
http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html

```
Using probe_mask values makes debugging HDMI audio more tricky & it is unnecessary.

One entry in /etc/pulse/default.pa allows system wide shared audio over an unenumerated HDMI subdevice (excluding digital pass-thru').

The latest alsa/pulse-audio (11.10) works out-of-the-box with no probe_mask values.
Pulse (pavucontrol) lists/enumerates all HDMI subdevices..
e.g. for GT240 it lists (4) subdevices/codecs.
     for GT520 it lists (2) subdevices/codecs

The problem with using probe_masks is that it is not hot-swap configurable, if you plug into another HDMI port you have to rebuild /reboot.

To ease debugging your Revo 3700, I would remove any snd-hda-intel probe_masks.
aplay -l
dmesg | grep HDMI

You have to use nVidia proprietary driver to use HDMI audio.
The older HDMI & ION have no/limited ELD reporting. So you have to find the audio capabilities with speaker-test..
The MCP67 chipset seems to have a channel order bug.

speaker-test -c 2 -r 44100 -D hw:0,3

---

### Post by wildmanne39 on 2011-11-09
Hi, I am going to ask the person that wrote the guide to see if he can help when he has a minute.
Thank you

---

### Post by mistergoomba on 2011-11-10
I ran speaker-test -c 2 -r 44100 -D hw:0,3 and got nothing, but when I did speaker-test -c 2 -r 44100 -D hw:1,7 I started getting hissing. This is good, right?!

---

### Post by mistergoomba on 2011-11-10
SUCCESS! I removed the probe_mask and everything works!

---

### Post by BicyclerBoy on 2011-11-11
Can you you post
aplay -l

What HDMI (sub)devices do you see listed in 
pavucontrol

With ION & MCP67,7A chipsets you have to find out the audio capabilities by trial & error..The eld files do not reflect reality..(what does?).

---

### Post by forbzie22 on 2012-01-12
Hi,

Im still having no luck with getting sound via HDMI on my revo r3700.

I have tried everything in this thread, including setting the .asoundrc and un-muting all channels. Have set gnome sound config to HDMI output. I have installed XBMC and set all audio outputs to HDMI too.

I have the same alsa version mentioned in this thread too.

Is there anything else to check ?

Running Ubuntu 10.10 64 bit.

Thanks

---

### Post by jlivin25 on 2012-01-12
hello mate
 
I had this same problem, easy fix is to install ubuntu 11.10.
 
which solves most problems and resulted in stable run oc XBMC.
 
Hope that helps, otherwise i can try to remember what else I tried.
 
Jim

---

### Post by BicyclerBoy on 2012-01-12
Exactly what have you modified ?

You are using nVidia proprietary driver ?
You need alsa (user space) 1.0.24..

XBMC Live users (10.04) used/required iQuik ppa.
Ubuntu 10.10 is likely badly supported because it is not a LTS release & it is couple of releases old.
This previously recommended ppa **does not** have any 10.10 alsa packages..
$ sudo add-apt-repository ppa:ricotz/unstable

It could be best to (do as previously suggested) upgrade to 11.04/11.10.

Remove any probe_masks for module snd_hda_intel in /etc/modprobe.d/*.conf &
$ [sudo] update-initramfs -u
& reboot/restart

---

### Post by forbzie22 on 2012-01-13
ok, I'll try upgrading to 11.10 tonight when back from work.
Am using the nvidia driver that ubuntu automatically picks up.

Will let you know how i get on.

It's strange though, i can use the command aplay /usr/share/sounds/Front_Right.wav and I here a sound.

I have seen lots of comments about setting the default.pa in /etc/pulse as this controls alsa. 

Anyway, before confusing things furhter.....will try the upgrade as it will be the easier more efficient option.

---

### Post by forbzie22 on 2012-01-13
Installed 11.10 and sound works ok now.

Needed to disable the Intel IEC958
Enables HDMI 5.1 Nr2 Audio via sound config

Now i have the problem where my resolution will only goto 1280, ubuntu 10.10 was able to display at 1920 so this is weird.

Any ideas ?

Almost there :)

---

