---
title: "HDMI Audio and Flash"
date: 2009-06-27
forum: Multimedia Software
---

### Post by Plaguester on 2009-06-27
I installed 9.04 a few weeks ago. One of the first things I did was to install flash player. At the time my computer was connected to some PC speakers and both video and audio worked fine in flash. Now I have the PC set up in a theater system and it is connected with an HDMI cable for both video and audio.

To get the HDMI audio to work, I went to Preferences > Sound and switched each playback value to "HDA Nvidia NVIDIA HDMI". I also opened gstreamer-properties from a terminal and changed the plugin to "ALSA" and the device to "NVIDIA HDMI". I now get sound out of all my programs except for flash player. Is there any way to get flash to use the proper sound device?

I'm not sure if any console outputs would be useful, just let me know and I will post them.

---

### Post by Plaguester on 2009-06-30
Anyone?

---

### Post by sherbey on 2009-07-18
Flash doesn't work for me over HDMI either, even though everything else seems to. Are there any fixes for this?

---

### Post by igorzwx on 2009-07-18
have you tried OSS4?

---

### Post by Plaguester on 2009-07-18
I managed to find the fix a couple of days ago.

Edit or create .asoundrc.

```
sudo gedit ~/.asoundrc
```

Add the line

```
defaults.pcm.device 3
```

Reboot.

---

### Post by johan_tre on 2009-07-18
[Plaguester]("http://ubuntuforums.org/member.php?u=479896"), 
I thank you so much for your first post! SO many thanks for the magic line :).
The magic you gave was the command "gstreamer-properties"

This made the whole thing working for me. Nothing else seemed to help:
no alsamixer, no sound settings, no nothing...   

I cannot understand that in no other guide or howto's this seems to be not mentionned.

From now on, I can start searching in a direction: it is proven that my hardware is supported. 

What I'm wondering now, is what gstreamer does more than the others?
And why so many smart guys did not notice?!

I'm using Jaunty, with a P5N7A mobo. 
Graphic card: nvidia GeForce9300 / nForce730i.
Sound is on board and is a HDA NVidia chipset,  or Realtek ALC1200, or an Intel ...   wth, 
I've read so many things about this board, I don't even know what chipset it actually IS.
To confuse the Russians I guess...   

Fact is, I can stop wondering if my hardware is Linux supported, which is in most cases more depending in luck.

Thanks again :)

---

### Post by markbuntu on 2009-07-18
fyi 
HDMI audio is part of the graphics processor so it is separate from the on-board sound device and dependent on the gpu driver to work properly. Your on-board ALC 1200 is fully supported by the ALSA snd-hda-intel driver since version 1.0.18. 

The HDMI is dependent on the nvidia gpu driver which comes from nvidia and is proprietary. There are a few chipsets which the nvidia driver does not support HDMI audio but I do not think that yours is one of them.

There is also a problem with flash in that it is not totally ALSA compliant so it cannot be easily switched to other than the default device and so must be fooled into which device it uses by changing the default in your ~/.asoundrc file. It is not necessary to be root (sudo) to edit this file since it is in your /home/user directory.

There are plenty of guides and how-tos around and you can use the forum search function to find them. For hardware specific problems you should use hardware specific search terms.

---

### Post by manolo on 2009-07-19
.

---

### Post by manolo on 2009-07-19
> **johan_tre said:**
> 
I'm using Jaunty, with a P5N7A mobo.
Graphic card: nvidia GeForce9300 / nForce730i.
Sound is on board and is a HDA NVidia chipset, or Realtek ALC1200, or an Intel


I need to buy a new computer for a Home-theatre. Would you please, johan_tre, confirm that your set up now works all right?
Do you get sound, via HDMI connector, in all channels (7 + bass)?
How about video? Monitor brand? Good quality? Which resolution?

Could you please list your set up?

Many thanks,
Manolo.

---

### Post by johan_tre on 2009-07-19
@manolo
Flatscreen: Plasma Panasonic xxxxV10.  (a recent model)
Keyboard-mouse:  Di Novo Mini
Case: Antec Fusion Black with remote.
Mobo: P5N7A with 64-bit Intel Dual Core Proc, 4Gb DDR, 320Gb Sata disk.
Media soft: Xbmc

What follows are my experiences and questions till now:

**Mobo:** (what intrests you the most I guess)
This mobo hardware seems to work fine on Linux...   bus as usual, the hardware is ok linux support however...

[LIST]
[*] Normal sound from the onboard soundcard jacks:  OK
[*]Sound over HDMI:  OK.  Actually, out-of-the-box on Jaunty.  But you needed to know the extra info regarding "gstreamer-properties"
Setup:  HDMI directly into the Panasonic.  (sorry, no surround test)  I would need an hdmi AV receiver for that. I think this must be working though.
More info: Google on Alsa + P5N7A.  It easily starts to get complicated, you really need to know what you're looking for.

I didn't manage to have the sounds of the buttons of the ubuntu os working, but I guess something else similar to  "gstreamer-properties" exists to enable it.

Still haven't found it though :(  Any help would be welcome.
It'll be searching again, like mostly it happens in Linux :)
Any help is welcome here.
[*]Graphics: OK, out-of-the-box on LCD monitors using DVI cable.... 
And now comes a big BUT:
The biggest problem is coming from the Nvidia drivers.
(not linux's fault, I know, but here we are stuck with it)
An annoying overscan problem persists!
(overscan =  the image projected on your Plasma TV screen for 1900*1028 is to big; it's like the signal is ment for a physical bigger screen)
I could fix this by means of the nvidia-settings, lowering the resolution + un-ticking "GPU scaling"
Again a BUT...
**1)** When I reboot, the resolution is reset to the native resolution of my screen (1900*1024')
When I open nvidia-settings again, it jumps back to the smaller resolution.
Any help in this one is welcome!!   Please help. At least I need the nvidia-settings to be reboot-persistent!
**2)** With the smaller resolution, left and right a black zone exists...  no way to fix this with the Plasma TV settings, neither the nvidia-settings.
[/LIST]
 I cannot understand how Nvidia leaves so many linux users using a TV (and hardware vendors) in the cold?  
At least they should provide a solution?!  What is their excuse for crying out loud?
Setups with an extra PCIe card with S-video connection are also overscanned, even worse!  (but that is another, but similar story)

**Keyboard-mouse:**  Logitech Di Novo Mini works out-of-the-box on Jaunty, despite messages in many fora. 
Some media keys I need to manage, (like switch off etc) but I think that is feasable.
I wanted this set from the beginning, but fora kept me away from buying it due to lack of linux support. 

**Case:** Antec fusion black with remote.
I managed to make it working with Lirc and XBMC. Long story, anyone interested in the right links etc, let me know. 

**Flatscreen:** wonderful, really :)

I'm not using this hardware very long, but found few hangup's already since I use the internal GPU. 
Difficult to say where the problem is coming from...   I'll find out later on.

Hope this was helpful :)

---

### Post by 4dplane on 2009-07-19
After spending a day on this topic I found that this works inside of ~/.asoundrc

```
pcm.dmixer {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "hw:0,3"
rate 48000
channels 2
period_time 0
period_size 1024
buffer_time 0
buffer_size 4096
}
}

pcm.!default {
type plug
slave.pcm "dmixer"
}
```

I have two audio cards so pcm "hw:0,3" is not my HDMI so I had to change it to pcm "hw:1,3" and it works!

Also, all I have to do is change pcm "hw:1,3" back to pcm "hw:0,0" and all audio goes out the 1/8 inch jack instead.

this info was found @
[http://forum.boxee.tv/archive/index.php/t-8147.html](http://forum.boxee.tv/archive/index.php/t-8147.html)

---

### Post by manolo on 2009-07-20
> **johan_tre said:**
> @manolo
Hope this was helpful :)

Thank you very much Johan. Your information is very helpful! :D

Sorry I can not help you with the problems :(
Only a few comments:

OverScan: Are not the settings stored in /etc/X11/xorg.conf? In your first post you said you were using HDMI for both audio and video, but in the last one you mention using DVI for LCD monitors. Do you have the overscan problem with both connections?

Gnome sound (Is this what you mean by 'ubuntu buttons'?): Usually it goes through esd (Enlightened Sound Daemon).

Thank you again and good luck!

---

### Post by johan_tre on 2009-07-20
The Nvidia's overscan problem is only found on HDMI and S-video. 
Nvidia goes even further by ignoring the xorg.conf.  So many options are not possible like 
"Mode" for instance. 
With this option it would be possible to find a workaround for the overscanning. 

The sound I meant was the sound of clicking buttons etc.  I'll google my way with "esd", thanks for that.

---

### Post by cajimene on 2009-08-07
> **Plaguester said:**
> I managed to find the fix a couple of days ago.

Edit or create .asoundrc.

```
sudo gedit ~/.asoundrc
```Add the line

```
defaults.pcm.device 3
```Reboot.

Hello, 

First at all, I'm sorry for my bad english.

I have a problem with this solution, if I put this option on my .asoundrc, flash works fine, even gnome sounds effects (like push buttons ..), but xbmc doesn't work. If I don't put this option on my .asoundrc, xbmc works fine but others options don't work.

How can I select what device I have to use for 'each application'?

Maybe, it's easier to put the option that you explain before and later, fix xbmc. I have followed an "howto" [http://www.xbmc.org/forum/showthread.php?t=53812](http://www.xbmc.org/forum/showthread.php?t=53812) to install xbmc and I don't know how to setup this for another option.

Thanks in advance,

Carlos

---

### Post by cajimene on 2009-08-07
Hello,

Ten minutes later from my last post, I have fixed my own question. In sound options of xbmc, in output option I have changed 'hdmi' for 'default' and it works fine (I have had good luck)

Thanks 

Carlos.

---

### Post by SJCBColby on 2009-10-18
Great Post Plaguester!

I added the file you suggested and I now get sound via HDMI from my Nvidia 9300 to my Samsung 550 HD TV.  

Before that I added the alsamixergui and then checked off all the IEC958 tick boxes. - had sound at that point but not for everything - and no sound with flash - now it all seems to work ( tested on hulu) 

SJC

---

### Post by skdevnath on 2009-10-25
> **4dplane said:**
> After spending a day on this topic I found that this works inside of ~/.asoundrc

```
pcm.dmixer {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "hw:0,3"
rate 48000
channels 2
period_time 0
period_size 1024
buffer_time 0
buffer_size 4096
}
}

pcm.!default {
type plug
slave.pcm "dmixer"
}
```I have two audio cards so pcm "hw:0,3" is not my HDMI so I had to change it to pcm "hw:1,3" and it works!

Also, all I have to do is change pcm "hw:1,3" back to pcm "hw:0,0" and all audio goes out the 1/8 inch jack instead.

this info was found @
[http://forum.boxee.tv/archive/index.php/t-8147.html](http://forum.boxee.tv/archive/index.php/t-8147.html)


This worked for me thanks a lot.:guitar:

---

### Post by skn332 on 2010-03-06
i know this is an old thread but i have the same issue just with karmic.  .asoundrc doesnt exist and i was wondering if there is a fix for 9.10?

---

### Post by Plaguester on 2010-03-07
9.10 shouldn't need the hacky fix. Just go to System > Preferences > Sound, goto the hardware tab, and choose HDMI out for the hardware profile.

---

### Post by pbradley on 2010-03-14
This worked great to get Flash running over HDMI for me.  My system has onboard analog audio with an add-in ATI video with HDMI out.  Before this fix, I could switch sound back and forth through the System -> Preferences -> Sound menu but could not get Flash audio through the HDMI.  The one downside to this fix is that it forces all audio over HDMI.  I can't, even manually using the menu above, get the sound to switch back to the analog without renaming the .asoundrc file and rebooting.  Is there any way to not 'hardset' the audio device in .asoundrc and have it look at the Sound menu settings.  I'd like it best if the system could send sound over both devices but I'd settle for not having to reboot.  Thanks and great work-around.

---

### Post by Plaguester on 2010-03-14
Mine switches back and forth flawlessly, but I'm only using one device. Does the sound switch properly from that menu for programs other than flash?

---

### Post by Diego318 on 2010-07-27
> **Plaguester said:**
> I managed to find the fix a couple of days ago.

Edit or create .asoundrc.

```
sudo gedit ~/.asoundrc
```Add the line

```
defaults.pcm.device 3
```Reboot.


This doesnt work for me, after the reboot it just notifies me that ATI HDMI sound driver has been disable.  I get the same notification when i use numbers 1-3.  Could it be that my hdmi sound is a different number?  Again, this is only for getting flash to work with sound, all other sounds work fine.

Thanks for everybody's help so far.  And thanks in advance for any future help.

---

### Post by Plaguester on 2010-07-27
If you're using 9.10 or later, you shouldn't need that hack. Just go to System > Preferences > Sound, Hardware tab. Pick your input and then the hardware profile for Digital HDMI out. However, I have nVidia hardware and not ATI...

---

### Post by mmkevins on 2012-03-08
Years later, I'm having this problem (but with multiple sound cards).  I successfully got everything else working (vlc, etc.) but flash wouldn't play.  I tried many, then came across this:

> **Plaguester said:**
> I managed to find the fix a couple of days ago.

Edit or create .asoundrc.

```
sudo gedit ~/.asoundrc
```

Add the line

```
defaults.pcm.device 3
```

Reboot.

This solution worked for me.  BTW, I'm using 10.04 64-bit with 3 sound cards: intel, sound-blaster, and hdmi on radeon 6450.

Thanks Plaguester, and thanks internet for allowing complete strangers to have conversations spanning years and continents to solve linux audio problems (among other things).

---

