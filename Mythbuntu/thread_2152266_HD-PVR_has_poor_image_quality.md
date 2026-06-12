---
title: "HD-PVR has poor image quality"
date: 2013-06-07
forum: Mythbuntu
---

### Post by waynelivingstone on 2013-06-07
I have a HD-PVR Rev F2 that I've tried to set up a few times with limited success. 
I decided to try again now that I'm trying Mythbuntu 12.04 and I have had better progress that I've had before, which is good. 

I'm using component cables from my cable box (Foxtel in Australia) to the HD-PVR and I'm getting a very soft image. It is equivalent to the image quality I get from my Wintv PVR2 and nowhere near the quality I see on the TV with the image passing through the HD-PVR or direct to the TV. Unless I am mistaken I should be seeing a much higher quality image. 

Is there something I need to do to improve my image quality?

Wayne

---

### Post by uteck on 2013-06-07
This wiki page; [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR) has some good info that might help you.
Look at secion 9. Bitrate and Picture Controls and see if changing the defaults helps.

---

### Post by waynelivingstone on 2013-06-09
I've tried changing the bitrate for the HD-PVR in the Mythbackend Recording Profiles but I havent noticed any change at all. 

So I went to the wiki and tried to follow the instructions but I'm stuck. I tried the first thing there to see what would happen and I got this:

# v4l2-ctl --device=/dev/video0 --set-ctrl=video_bitrate=13500000 
The program 'v4l2-ctl' is currently not installed.  You can install it by typing:
apt-get install v4l-utils

So then I did what it said: 

# apt-get install v4l-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 v4l-utils : Depends: libv4l-0 (= 0.8.6-1ubuntu1) but 0.8.6-1ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.

So now I have no idea what to do next. I'm not very confident with the command line so I need basic instructions. 

Wayne

---

### Post by waynelivingstone on 2013-06-17
Does anyone have any ideas how I can move forward from here?

---

### Post by uteck on 2013-06-17
Have you tried upgrading your system to fix the held packages:
apt-get update
apt-get dist-upgrade
review what is going to be installed or removed, and press y.

---

### Post by waynelivingstone on 2013-06-18
Thanks, that got things working again. 

I've tried the commands and scripts on [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR) but I'm not seeing any change in picture quality for better or worse when I change the bitrate. 
I've done some testing in VLC and the picture quality is better, but still not quite what I see on the TV. Changing the bitrate made no change in VLC either. 

When I hook the HDPVR up to windows I get near perfect picture quality when comparing to the TV display. In Windows I can see that the input resolution is 720x576 (576i), and it's using a bitrate of 5.0MB

My other issue is that no matter what I playback through it comes up as 4:3 when the source is 16:9. 

Any ideas why I'm not seeing any improvement?

---

### Post by newlinux on 2013-06-18
What firmware version are you using on your HD-PVR? Have you changed to recording profile for the HD-PVR in mythtv

---

### Post by waynelivingstone on 2013-06-18
My HD-PVR is using firmware 1.7.30059.1

I have found and tried changing the bitrates in the HD-PVR recording profiles in backend setup. Do I need to tell it to use one of those profiles somewhere?

---

### Post by newlinux on 2013-06-18
I don't believe so. What kernel version are you running? According to the HD-PVR mythtv wiki - [http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Firmware_Version_Stability](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Firmware_Version_Stability) - firmware versions later than 1.6.29207 will have color and saturation issues when run with a kernel earlier than 3.2.34, which may be what you are experiencing. You can try one of the fixes listed in the wiki for this issue (downgrade firmware version, upgrade kernel, run a script adjusting the parameters before every recording). I had this problem and ended up downgrading the firmware version.

---

### Post by waynelivingstone on 2013-06-18
My Kernel is 3.5.0-34

I dont believe my issue is anything to do with colour saturation. My image quality in mythtv has a soft fuzziness to it rather than the crisp image I see on the TV or in Windows.

---

### Post by newlinux on 2013-06-18
Okay. It's hard to know exactly what's different without seeing what you are seeing. Are you running a custom kernel (I thought you were on Ubuntu 12.04)? It might be helpful to make a short recording of the same program in Linux and in Windows and then examine the characteristics of the file so we can see what exactly is recording differently (bit rate, resolution, etc.).

---

### Post by waynelivingstone on 2013-06-18
I am using Mythbuntu 12.04 with the standard kernel. (I wouldn't know how to customise the kernel)

I have made two 30 second recordings as requested. When I play them both back in VLC side by side it's much harder to see the difference, but you can see it a bit on the screen menus.

[https://www.dropbox.com/sh/iwh86wrj4w3ahzo/TSjmdAgXaa](https://www.dropbox.com/sh/iwh86wrj4w3ahzo/TSjmdAgXaa)

---

### Post by newlinux on 2013-06-19
Hmmm, I guess mythbuntu uses a new kernel than ubuntu, or perhaps there has been a significant update to the kernel that I haven't installed (I rarely install updates on solidly working system)? I'm running Ubuntu 12.04.2 on most of my machines the kernel version is 3.2.0-39. I'm not at my home to view those files right now, but I'll try and take a look at them in the next day or so and see if I can be of any help...

---

### Post by newlinux on 2013-06-19
Okay, because I like to tinker more than I like my job right now, I downloaded these at work and looked at them. They do look very similar, but I can tell what you are talking about, the Linux one does appear a little "softier" or not quite as sharp. Now comparing it to TV, that's passthrough with no processing, so I would expect that to look better. I suspect the TV looks better than the windows or Linux recordings. I looked at the file attributes and for video they look about the same (very similar bitrate, same resolution, etc). Audio is encoded differently, but not an issue for you. Interestingly when I play the videos back they show up as the same window size when using VLC, but not when using Windows Media Player. The linux recording by default starts off smaller, even though files show as having the same resolution. Not sure what that's about, but I don't use Windows Media Player often enough to know if that means anything...

The only thing I can think of right now is that Windows and Linux are using different picture settings (contrast, sharpness, saturation, etc.) when encoding. You might want to check what the settings are for those in Windows (I assume somewhere in the windows software you can see and change these settings) and compare them to what they are in Linux ```
v4l2-ctl --list-ctrls
```.

---

### Post by waynelivingstone on 2013-06-20
v4l2-ctl --list-ctrls
                     brightness (int)    : min=0 max=255 step=1 default=128 value=128 flags=slider
                       contrast (int)    : min=0 max=255 step=1 default=64 value=64 flags=slider
                     saturation (int)    : min=0 max=255 step=1 default=64 value=64 flags=slider
                            hue (int)    : min=0 max=30 step=1 default=15 value=15 flags=slider
                      sharpness (int)    : min=0 max=255 step=1 default=128 value=128 flags=slider
                 audio_encoding (menu)   : min=3 max=4 default=3 value=3 flags=update
                 video_encoding (menu)   : min=2 max=2 default=2 value=2
             video_bitrate_mode (menu)   : min=0 max=1 default=1 value=1 flags=update
                  video_bitrate (int)    : min=1000000 max=13500000 step=100000 default=6500000 value=6500000
             video_peak_bitrate (int)    : min=1100000 max=20200000 step=100000 default=9000000 value=9000000 flags=inactive


All the picture settings are the same in Windows except Hue which is 0, but I doubt that difference is causing my issue.

---

### Post by newlinux on 2013-06-20
Well, I'm mostly out of ideas... The only other thing I can think of is to play with the controls in Linux (specifically sharpness and maybe contrast) to see if you can generate a better video. The wiki indicates the settings have to be set before each recording... After you adjust settings you may want to verify via the command above that the settings have changed right before the recording starts.

---

### Post by nickrout on 2013-06-23
What are you trying to record here? Most people buy an HD-PVR to record HD. You seem to be recording at SD resolution, although you don't say whether the source is HD or SD. 

Encoding an analogue signal is inherently lossy and the picture won't be as good as, for example, recording a digital stream directly. 

Also what are you using to record in windows?

---

### Post by BicyclerBoy on 2013-07-02
The image of OSD gui shows the difference very well.
The actual program source material is far too blurred/soft to be useful for easy comparison.
That program is edited/mastered blurred/soft.

IMO The OSD image shows the linux recording to be far worse than windows.
The linux recording looks to have one one field repeated twice for each frame. i.e. half vertical resolution.
Mediainfo shows both are interlaced video.
HD-PVR does not transcode, only encodes in the same video mode as input.

Playing the linux sample recording with field order swapped did not look any worse or better but then the OSD gui image is static position so this should be anticipated.

The HD-PVR recordings (that I have) at SD480i60 & HD720p60 look good. The HD720p60 recordings are very good.
It is possible the 50Hz support in the HD-PVR driver never had any testing.

There was a collection of HD-PVR patches to the kernel in last couple months, including mention of 576i50 & other video modes.

Can you provide a sample of high quality program with movement ? MotoGP or tennis?

---

### Post by waynelivingstone on 2013-08-18
Ok it's been a while but I'm finally getting back onto this. 

I have been playing with the bitrates and sharpness at the command line and realised that the bitrates I set were being overridden by the ones set in the backend recording profiles. So I went there and started experimenting with different values and saw some minor improvement in the picture quality. 

I also thought I saw some improvement by increasing the sharpness, but that gets reset to the default value after reboot. 
Then for some reason I decided to set the sharpness to 0 and to my surprise the picture is near perfect. The picture looks good and all the channel overlays are crisp without the previous fuzziness. 

My problem now is I dont know how tto set the sharpness to 0 so that it sticks after a reboot. 
I see the wiki has a startup script to set the various values, but it doesnt say what to do with it or how to execute it. 

Can anyone tell me how to set the sharpness value permanently?

---

### Post by nickrout on 2013-08-18
startup scripts can usefully be placed in /etc/rc.local - which is run as root on bootup.

---

### Post by waynelivingstone on 2013-08-21
I set up the startup script from the wiki and put a line at the end of /etc/rc.local pointing to it. 
When I ran the script it didn't work as desired. I think it might be a bit out of date. 

So since the sharpness was the only thing I wanted to change I just put 
v4l2-ctl --device=/dev/video0 --set-ctrl=sharpness=0
at the end of /etc/rc.local and it had the desired effect. 

Now I've tried changing the brightness in the same way but the value never changes. I've tried adding it as:
v4l2-ctl --device=/dev/video0 --set-ctrl=brightness=80
v4l2-ctl --device=/dev/video0 --set-ctrl=sharpness=0
or
v4l2-ctl --device=/dev/video0 --set-ctrl=sharpness=0 --set-ctrl=brightness=80
but it doesn't work. 

I've noticed that at boot the values are:

                     brightness (int)    : min=0 max=255 step=1 default=128 value=128 flags=slider
                       contrast (int)    : min=0 max=255 step=1 default=64 value=64 flags=slider
                     saturation (int)    : min=0 max=255 step=1 default=64 value=64 flags=slider
                            hue (int)    : min=0 max=30 step=1 default=15 value=14 flags=slider
                      sharpness (int)    : min=0 max=255 step=1 default=128 value=0 flags=slider
                 audio_encoding (menu)   : min=3 max=4 default=3 value=3 flags=update
                 video_encoding (menu)   : min=2 max=2 default=2 value=2
             video_bitrate_mode (menu)   : min=0 max=1 default=1 value=1 flags=update
                  video_bitrate (int)    : min=1000000 max=13500000 step=100000 default=6500000 value=6500000
             video_peak_bitrate (int)    : min=1100000 max=20200000 step=100000 default=9000000 value=9000000 flags=inactive

but when I activate the tuner by going into Watch TV it is this:

                     brightness (int)    : min=0 max=255 step=1 default=128 value=128 flags=slider
                       contrast (int)    : min=0 max=255 step=1 default=64 value=64 flags=slider
                     saturation (int)    : min=0 max=255 step=1 default=64 value=64 flags=slider
                            hue (int)    : min=0 max=30 step=1 default=15 value=14 flags=slider
                      sharpness (int)    : min=0 max=255 step=1 default=128 value=0 flags=slider
                 audio_encoding (menu)   : min=3 max=4 default=3 value=4 flags=update
                 video_encoding (menu)   : min=2 max=2 default=2 value=2
             video_bitrate_mode (menu)   : min=0 max=1 default=1 value=0 flags=update
                  video_bitrate (int)    : min=1000000 max=13500000 step=100000 default=6500000 value=6000000
             video_peak_bitrate (int)    : min=1100000 max=20200000 step=100000 default=9000000 value=8100000

video_bitrate and video _peak_bitrate and audio_encoding changes but that is set by me in the backend recording profiles. I would say that they all start at their default values except that hue isnt default at boot or after the tuner is activated. Could some or all of the values be set somewhere that isn't allowing me to override them?

---

### Post by nickrout on 2013-08-21
I'd take this to the mythtv-users mailing list if I were you. It's gone past what I know.

Although... when you say "the end of rc.local" you do mean BEFORE the exit 0 statement don't you?

---

### Post by waynelivingstone on 2013-08-21
Oops, my rc.local didn't even have an exit 0 statement. 
It doesn't seem to have made any difference though.

---

### Post by waynelivingstone on 2013-08-23
I found the following post that gave me the solution to changing the brightness and other values. Pretty simple really. 
[http://www.mythtv.org/pipermail/mythtv-users/2011-August/320135.html](http://www.mythtv.org/pipermail/mythtv-users/2011-August/320135.html)

---

### Post by Pierre_duParte on 2013-08-23
> **waynelivingstone said:**
> I have a HD-PVR Rev F2 that I've tried to set up a few times with limited success. 

Is there something I need to do to improve my image quality?


Hi Wayne,
I'm in AU as well, and I am totally frustrated by the crappy images that mythtv & linux throw up. It'd be nice if someone could explain why a $40 dbtv set top box does a better job than a HTPC containing a quadcore CPU/APU/GFX + megagiga thingies of memory storage et al. 

But every now and then in our seemingless hopeless  googling and wading and trawlng through obfuscated dribble there is a ray of hope. I came across this:
[http://rudd-o.com/linux-and-free-software/picture-perfect-mythtv-how-to-improve-video-quality](http://rudd-o.com/linux-and-free-software/picture-perfect-mythtv-how-to-improve-video-quality)

I cleaned house and followed the advice. The item on gamma adjustment was particularly useful. The images I'm getting now (AMD A8 based system) are a dramatic improvement, albeit that they remain poor in comparison to running the same hardware over Windows or my $40 AKAI set-top box. But it's a start....

---

### Post by dakota34 on 2013-08-25
this isn'ta solution to the hd-pvr issues, but as far as poor image on your hefty AMD quadcore, if you're not using an NVIDIA card and taking advantage of VDPAU then you are not getting anywhere near the best display/playback available in Linux. It's not a lot of fun to buy a separate card for an already expensive CPU/Motherboard combo, but AMD/ATI graphics pale in comparison to what you'll see with VDPAU. Night and day.

---

