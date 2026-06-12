---
title: "ubuntu 9.04 and hdmi"
date: 2009-05-17
forum: Multimedia Software
---

### Post by alch on 2009-05-17
I recently installed ubuntu on my new dell vostro 220s. It has an ATI video card with HDMI out. I have it connected to my tv with HDMI. There is no monitor connected.

I am having some issues with VLC media player on this setup. I have both the sound and video going through the HDMI connection. In VLC i have the video going through the default output, and audio going through ALSA then specifically the hdmi output. I have the closed source ati drivers installed.

Whenever I try to full screen a show the screen goes blank and my tv says no input on hdmi. Where could i start in troubleshooting this, is there a way to get video back to where it was after it goes blank? force close vlc maybe without being able to see it?

Any help is appreciated. Thanks.

---

### Post by thesheff17 on 2009-06-07
This happened to me when I added a second monitor and shut down the machine.  I would see the ubuntu menu booting but then nothing.  To resolve this I unplugged the monitor cable that was showing the bios and ubuntu splash screen.  Once I did this the computer defaulted to the other port on the video card and booted fine.  Does your video card have dual ports?

I'm not sure what the reason for this is but I hope there is a fix eventually.

---

### Post by alch on 2009-06-26
I eventually got it to work. Not sure what it is but I restarted a few times. It seems to work better if I have the option on the tv set to the computer input while I boot the machine. Slightly finicy imo. Now I have a different problem. No sound over a non HDMI source.

I have to say that audio is  probably the most frustrating thing to play with in ubuntu. Right now I can get sound through HDMI if i play with the settings in VLC and set it to alsa HDMI output. Then in the volume controll setup i change it to alsa hdmi and check a box that says IEC958. Not sure what that means but it works.

Now however I can't get sound to play over the non hdmi output.
I have a motherboard sound card in this thing and have the mini jack running into my stereo. I can't get any audio through this. In sound settings I try to test sound, when i have my intel alc662 audio selected and hit test sound and I get this error.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Thanks in advance.

---

### Post by alch on 2009-06-26
Well I found a crappy work around. I am pretty sure I must have broken the default sound setup at some point while trying to get it to play through HDMI.

Now I am playing the sound through HDMI then using my TV's output port to run into an input on my stereo. Not the greatest fix but works for now.

Is there any way to just reset all of the audio back to default? Maybe reinstall all the packages and drivers. I am not 100% against just reformatting but i figure I can learn more by fixing instead of wiping.

---

### Post by tixetsal on 2009-06-26
> **alch said:**
> I eventually got it to work. Not sure what it is but I restarted a few times. It seems to work better if I have the option on the tv set to the computer input while I boot the machine. Slightly finicy imo. Now I have a different problem. No sound over a non HDMI source.

I have to say that audio is  probably the most frustrating thing to play with in ubuntu. Right now I can get sound through HDMI if i play with the settings in VLC and set it to alsa HDMI output. Then in the volume controll setup i change it to alsa hdmi and check a box that says IEC958. Not sure what that means but it works.

Now however I can't get sound to play over the non hdmi output.
I have a motherboard sound card in this thing and have the mini jack running into my stereo. I can't get any audio through this. In sound settings I try to test sound, when i have my intel alc662 audio selected and hit test sound and I get this error.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Thanks in advance.

Same problem here.  9.04 amd64 on geforce 8200 chipset.  Audio via mobo outputs was fine until I started using HDMI.  Then, audio would ONLY work via HDMI.  Tried many solutions.  No luck.  Reinstalled out of frustration.  Audio worked fine until updates.  tried toggling HDMI AUDIO in BIOS, but no luck.  Going to attempt ANOTHER reinstall with some tweaked BIOS options.  
Maybe we need to file a bug report.

---

### Post by tixetsal on 2009-06-27
I discovered that by booting 2.6.28-11-generic, instead of 2.6.28-13, my audio was restored, as long as I booted that kernel. I have another box with Asus P5N7A-VM MOBO, and this bug did not effect that machine. My AMD geforce 8200 will not play nice with 28-13 though. My sound card shows up in lspci, but aplay -l tells that I have no sound card.

---

### Post by alch on 2009-06-27
Thats possibly it. I do keep doing those updates whenever they pop up. I will try to boot into an older kernel before formatting. I followed a guide to reinstall my ALSA drivers. And by the way sound seems to work best in VLC where I can set the output to HDMI through ALSA it doesnt work in a lot of other applications, ie firefox.

---

### Post by DrDunkMcNally on 2009-10-30
Hi there,
 
I'm having a problem similar to yours:
 
I'm running Ubuntu 9.04 on my HP Pavilion dv6675US which has hdmi out nvidia graphics card (unsure which one and don't have it in front of me to check).
 
I'm running an HDMI cable from my laptop to my hd tv, and I get nothing in response from the tv. The laptop detects that there is another monitor present, but it seems that's as far as it goes, my tv does not display anything, ever. (let me clarify, it does work for other HDMI inputs, and has worked until now with vista from my laptop)
 
I'm hoping this is similar enough to your original issue that there is something I can use. However, being new to Ubuntu (and any type of Linux in general) most of this conversation went over my head.
 
Could you please break it down for me so I might hope to understand?
 
Thanks,
Dunk

---

### Post by TimTang on 2009-11-17
I'm having the same problem with HDMI after upgrading from 8.10. I simply get nothing. It could be working for all I know, but all I see is the blank blue screen of my flat screen TV, which usually indicates "no signal".

Even with 8.10 I had to drag out my old monitor to troubleshoot video problems but I've since got rid of it so now I just don't use ubuntu any more which is a shame 'cause I like it.

HDMI will be an ubuntu killer if they don't focus heavily on it because, like myself, most people are moving their computers into the living room. IF a "live CD" won't even work, ubuntu will be a hard sell.

---

### Post by markbuntu on 2009-11-17
You can set pulseaudio to make a virtual output device that will output simultaneously to all your sound devices. If you have Pulseaudio Preferences installed there is a simultaneous output tab. just open that and click the box. You will have to move your applications to the new virtual device the next time you run them. 

Of course, your applications will need to going through pulseaudio for this to work. If you are using jaunty or earlier you will need have to jump through some hoops to get your hdmi working with pulseaudio. There is a good guide for that here.

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

If you are using karmic then the hdmi outputs are already available in the gnome volume control but you will need pulseaudio preferences to make the virtual simultaneous output available.

---

