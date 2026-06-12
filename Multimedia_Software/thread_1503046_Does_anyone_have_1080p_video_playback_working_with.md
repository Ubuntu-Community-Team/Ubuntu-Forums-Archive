---
title: "Does anyone have 1080p video playback working with nvidia ion and Lucid?"
date: 2010-06-06
forum: Multimedia Software
---

### Post by gizmocan on 2010-06-06
I have a Zotac IONITX-F-E motherboard (Intel Atom Dual Core 1.6 GHz +   Nvidia ION) -based box with Ubuntu 10.04 64-bit installed.

Do you or does someone you know have the same setup as I do? If so, do they have 1080p video playback working? If so, what driver are they using?

I've tried following every guide I could find, but no luck so far. I have libvdpau1 and libvdpau-dev installed. I have the nvidia 195.36.24 driver installed (I used the nvidia installer).

I have mplayer installed (which I compiled from source with  --enable-vdpau). I try to run mplayer with this command:

```
mplayer -vo vdpau -vc ffh264vdpau path/to/myfile.mkv
```

I get  the following message in my terminal:

```
Error opening/initializing the selected video_out (-vo)  device.
```I have libvdpau-dev and libvdpau1 installed.

After Googling this problem, I found a post that suggested the following  steps:

```
sudo add-apt-repository ppa:nvidia-vdpau
sudo apt-get update
sudo apt-get install nvidia-glx-195 nvidia-195-modaliases
```It turns  out that I had already added the nvidia-vdpau repository. However,  despite that, I get:

```
E: Couldn't find package nvidia-glx-195
```

The same problem  exists for the nvidia-195-modaliases package. Do these packages exist? Is there some other way to get them?

Any thoughts are appreciated!

---

### Post by farbird on 2010-06-06
first, use x-updates ppa for 256 version of the nvidia driver for lucid.
2ndly, install the mplayer package from rvm or ripps818 ppa for vdpau support.
last but not least, use smplayer or [xbmc]("http://sglnx.com/2010/05/opensource-complete-home-entertainment-system-xbmc/").

---

### Post by farbird on 2010-06-06
fyi, 1080p on my hp laptop mini311 [ atom280 + ion ] works fine

---

### Post by ShakeyJake on 2010-06-06
Uninstall everything to do with mplayer and any changes to anything else you may have made by following the guides. Then install smplayer from the repos, that and its dependencies should sort you out without any messing around.

---

### Post by gizmocan on 2010-06-06
Thanks for the replies!

In an attempt to follow this advice, I tried:

sudo apt-get purge mplayer
sudo apt-get install smplayer

I then tested mplayer again using the same command as in my first post. I got the same error. My understanding is that if I can't get it to work on the command line, running mplayer through a front end like smplayer or xbmc won't work either.

Next, I did:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A58BCAE3
sudo add-apt-repository ppa:rvm/ppa
sudo apt-get update
sudo apt-get install mplayer

Tested mplayer on the command line again, same problem.

I added the X-updates repository:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update

But I'm not sure how to get the 256 version of the nvidia driver... 
I'm guessing I should start with:

sudo apt-get purge nvidia

but then what?

---

### Post by cbilljones on 2010-06-07
Hi, ive just been working through this myself, did you remove the mplayer you installed form source? this can not be done with apt, you will need to enter the folder you installed from and run "sudo make uninstall" I forgot to uninstall my build i did from source and had the same issue; so remove mplayer with synaptic, then remove the source install, then reinstall with synaptic; hope that sorts it out

for the record it now works great for me: playing 1080p mkv file my quad score sits at 4-20%(1-5% per core) usage, so clearly vdpau is doing a good job of sending it to GPU :)

[edit] im using 195, it works great, no need for 256

also i recommend smplayer from the ppa, makes configuration a breeze

finally, why did you add ppa:ubuntu-x-swat/x-updates?, i would remove that and ppa:rvm/ppa; the mplayer you want is from the ppa:nvidia-vdpau

---

### Post by Jose Catre-Vandis on 2010-06-07
I'm with cbilljones on this.

Clear out all your existing mplayer installation

Add this to your /etc/apt/sources.list

```
#vdpau-ppa
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu lucid main
```

Update
```
sudo apt-get update
```

Install mplayer - should now work fine :)

---

### Post by gizmocan on 2010-06-07
Ok, I'll give that a shot this evening!

When you say you're using 195, are you using the nvidia-current driver in the repo? Did you need to install nvidia-glx-195 and nvidia-195-modaliases separately?

---

### Post by cbilljones on 2010-06-07
> **gizmocan said:**
> Ok, I'll give that a shot this evening!

When you say you're using 195, are you using the nvidia-current driver in the repo? Did you need to install nvidia-glx-195 and nvidia-195-modaliases separately?

well lets double check your PPA's first: goto system>administration>software sources, goto 3rd party software tab; all we want in there is the canonical ppa's and ppa:nvidia-vdpau/ppa; delete all others for now.(should have 3 now). Close software sources telling it to reload

Now, go into synaptic package manager, click reload, search for nvidia; remove whatever your running, also remove mplayer and smplayer if installed. install nvidia-glx-195 and nvidia-195-modaliases. reboot. 

now lets make sure mplayer is completely gone: open terminal, run "mplayer" should say not installed.(if its still there you havnt removed the package you installed from source; if its still there open a terminal, cd to the folder you installed from, run "sudo make uninstall").if so open synaptic package manager, install mplayer and smplayer. open smplayer and goto options; make sure vdpau is set as video output. hopefully i covered everything, good luck.

i am running 195 version from the nvidia vdpau ppa

---

### Post by gizmocan on 2010-06-07
Once again, thanks for taking the time to reply!

Ok. I removed the mplayer I installed from source, as well as the nvidia drivers.

```

cd mplayer-checkout-2010-05-21
sudo make uninstall
sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run --uninstall
sudo apt-get purge nvidia*

```

I opened my software sources, unchecked everything except for the 2 canonical repos and the nvidia vdpau one.

I then modified my sources.list to add the nvidia vdpau repo (which was already there anyway).

I opened synaptic package manager. Hit Reload. Searched for nvidia. There were no packages listed which included the number 195.

I marked nvidia-current, nvidia-current-modaliases, nvidia-glx-185 which all appear to correspond to version 195.36.15 (which is weird, but whatever). I rebooted. 

I open synaptic again and add mplayer and smplayer. I open smplayer and configure it to use vdpau and alsa. I try to open my MKV movie and mplayer crashes.

Here is the mplayer log (which I got from a window in smplayer).

```

 p, li { white-space: pre-wrap; }  ==========================================================================
 Forced video codec: ffh264vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 [VD_FFMPEG] XVMC-accelerated MPEG-2.
 Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
 ==========================================================================
 ID_VIDEO_CODEC=ffh264vdpau
 ==========================================================================
 Trying to force audio codec driver family hwac3...
 Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
 No accelerated IMDCT transform found
 hwac3: switched to AC3, 640000 bps, 48000 Hz
 AUDIO: 48000 Hz, 2 ch, ac3, 640.0 kbit/41.67% (ratio: 80000->192000)
 ID_AUDIO_BITRATE=640000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
 ==========================================================================
 [AO_ALSA] alsa-lib: conf.c:4484:(parse_args) Unknown parameter AES0
 [AO_ALSA] alsa-lib: conf.c:4617:(snd_config_expand) Parse arguments error: No such file or directory
 [AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hw:0,1,AES0=6
 AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
 ID_AUDIO_CODEC=hwac3
 Starting playback...
 [VD_FFMPEG] XVMC-accelerated MPEG-2.
 VDec: vo config request - 1920 x 1080 (preferred colorspace: H.264 VDPAU acceleration)
 VDec: using H.264 VDPAU acceleration as output csp (no 0)
 Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
 ID_VIDEO_ASPECT=1.7778
 VO: [vdpau] 1920x1080 => 1920x1080 H.264 VDPAU acceleration 
 [vdpau] Error when calling vdp_output_surface_create: The system does not have enough resources to complete the requested operation at this time.
 [vdpau] Error when calling vdp_output_surface_create: The system does not have enough resources to complete the requested operation at this time.
 [vdpau] Error when calling vdp_output_surface_create: The system does not have enough resources to complete the requested operation at this time.
 [vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
 [vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
 [vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
 [vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
 [vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
 [vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
 [Mixer] No hardware mixing, inserting volume filter.
 [format] Sample format big-endian AC3 not yet supported 
 [vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
 [vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
 [vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
 
 
 MPlayer interrupted by signal 11 in module: av_sync
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.
  [ This binary of MPlayer in Debian is currently compiled with
    '--enable-debug'; the debugging symbols are in the package
    'mplayer-dbg'.]
 *** glibc detected *** /usr/bin/mplayer: free(): corrupted unsorted chunks: 0x00000000027d7310 ***
 ======= Backtrace: =========
 /lib/libc.so.6(+0x775b6)[0x7ffb1a5d25b6]
 /lib/libc.so.6(cfree+0x73)[0x7ffb1a5d8e53]
 /usr/lib/nvidia-current/libGL.so.1(+0x4bacf)[0x7ffb21428acf]

```

I have 2GB of RAM, which I thought should be enough. No other programs are running.

Any suggestions?

---

### Post by cbilljones on 2010-06-07
Can you try playing the file from terminal with the following command:
mplayer -ao alsa -vo vdpau -vc ffh264vdpau /path/to/file 
post the output from that
also i see an error for ac3, try disabling that option in smplayer: AC3/DTS Passthrough S/PDIF
One other thing; i notice your using alsa, maybe pulse would be better if its installed? I use OSS4 so im not that familiar with pulse

[edit] ok last thing, could you keep system monitor open on resource tab and let us know your CPU usage during playback?

---

### Post by gizmocan on 2010-06-08
Good ideas. I just had a few minutes this morning, but I tried playing the movie with your command. I saw no errors in the terminal, but my whole system became unresponsive so I couldn't scroll back or paste the output here. I could hear the sound playing, but there was no video. There wasn't even a window that got opened up to play the video. 

I'll try again tonight with the system monitor open.

---

### Post by @H.264 on 2010-06-08
Try VLC...

---

### Post by cbilljones on 2010-06-08
I dont think VLC is the answer, clearly something is up with vdpau; thats why you had sound and no vid. Can you check in synaptic and make sure libvdpau is installed? i have libvdpau-dev installed as well, shouldnt be needed but install it anyway, wont hurt anything.

so you understand the command im having you run:
-ao is Audio Out, i suggest pulse if installed, alsa if not 
-vo is Video Out, we need vdpau here 
-vc is Video Codec, we need ffh264vdpau here

---

### Post by gizmocan on 2010-06-08
I confirmed in Synaptic that I have libvdpau1 and libvdpau-dev currently installed.

I tested smplayer and mplayer with the system monitor open. The CPU usage spikes, but doesn't get to 100%. On the other hand, no video appeared, so I don't think that says much...

I'm guessing the problem is still related to my driver version. Is there anything that could be conflicting with my 195.36.15 nvidia driver/glx/modaliases? Like libgl1-mesa or something? Anything else I might be missing?

---

### Post by gizmocan on 2010-06-08
I tried playing a non-HD AVI file in Smplayer, just to see. I get sound and video working fine, but when I hit 'stop', mplayer crashes. 

The error log looks very similar to the problem related to my MKV file:

```
  p, li { white-space: pre-wrap; }  ==========================================================================
 Forced video codec: ffh264vdpau
 Forced video codec: ffmpeg12vdpau
 Forced video codec: ffwmv3vdpau
 Forced video codec: ffvc1vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
 ==========================================================================
 ID_VIDEO_CODEC=ffodivx
 ==========================================================================
 Trying to force audio codec driver family hwac3...
 Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
 AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
 ID_AUDIO_BITRATE=128000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
 ==========================================================================
 AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=mp3
 Starting playback...
 VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
 VDec: using Planar YV12 as output csp (no 0)
 Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
 ID_VIDEO_ASPECT=1.7727
 VO: [vdpau] 624x352 => 624x352 Planar YV12 
 [Mixer] No hardware mixing, inserting volume filter.
 [vdpau] Error when calling vdp_output_surface_create: The system does not have enough resources to complete the requested operation at this time.
 [vdpau] Error when calling vdp_output_surface_destroy: An invalid handle value was provided.
   MPlayer interrupted by signal 11 in module: unknown
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.
  [ This binary of MPlayer in Debian is currently compiled with
    '--enable-debug'; the debugging symbols are in the package
    'mplayer-dbg'.]
 

```

---

### Post by cbilljones on 2010-06-09
Im not sure whats going on there, i think i would probably reinstall and start from scratch:mad:

---

### Post by gizmocan on 2010-06-09
Do you mean re-install Ubuntu from scratch? *gulp*

I have so many things working correctly, I'd hate to lose all that.

Should I try removing (or adding?) all the ATI-related stuff?

Does it make sense that I'm using the 'Transitional package' for nvidia-glx-185 (which Synaptic claims is version 195.36.15)?

---

### Post by cbilljones on 2010-06-09
> **gizmocan said:**
> Do you mean re-install Ubuntu from scratch? *gulp*

I have so many things working correctly, I'd hate to lose all that.

Should I try removing (or adding?) all the ATI-related stuff?

Does it make sense that I'm using the 'Transitional package' for nvidia-glx-185 (which Synaptic claims is version 195.36.15)?

Well, is there any ATI related stuff? Certainly remove that as you have nvidia hardware. Remove all nvidia/vdpau mplayer vdpau h264 ffmpeg stuff. install ubuntu restricted extras if you havnt already. run sudo apt-get auto-remove. install current nvidia driver(should be 195 if nvidia repository is enabled).Reboot. make sure mplayer is not installed by running from terminal. install mplayer/smplayer libvdpau/libvdpau-dev, h264 encoder from synaptic. Try running command from terminal:
mplayer -ao pulse -vo vdpau -vc ffh264vdpau /path/to/file

but really ubuntu is so quick to install, i tend to do that as sometimes its quicker, and then im starting clean. What is working that your worried about losing?

Also transitional packages dont do anything and can safely be removed

---

### Post by gizmocan on 2010-06-09
I tried removing all the pieces, rebooting and reinstalling them with Synaptic as you suggested. Testing in mplayer yields the same results.

I did notice however that I did not have the h264 encoder, nor ffmpeg installed previously. Sadly, adding them made no difference. I also removed all ATI-related packages to no avail.

I also noticed that I still have libdrm-nouveau1 installed, despite having tried to purge my system of nouveau and even blacklisting it. However, removing libdrm-nouveau1 would involve removing a large number of packages including alsa-base, which I don't think would be a good idea... Why is nouveau linked to alsa-base?

I also noticed that while booting, I see an error: nForce2 Error probing smb2. There is a bug filed for this, but it's not clear if it actually affects anything.

Finally, despite still having pulse installed, I only get sound using -ao alsa (no sound for -ao pulse).

I guess my only option is to try reinstalling ubuntu. I'll have to put that off for at least a week, because I don't want to have to setup lighttpd again, now that it's working, until I've finished a website I'm working on.

---

### Post by cbilljones on 2010-06-10
ya something seems broken, i know i had pulse/ffmeg and vdpau working well on that board so it is doable, I think we just need to plan the installation a bit, make sure things get installed when you need them; ill outline my general install routine:
install ubuntu
add nvidia vdpau repository
update and install current nvidia driver(should be 195)
install ubuntu-restricted-extras
install sun-java plugin(you may or may not need this)
install libvdpau, smplayer(should automatically install mplayer with that)
I dont even have ffmpeg installed at the moment so its not required for this. Everything should work at that point. Just to confirm; your are connected to a HD monitor, and your file is 1080P as well right? And your screen resolution is 1920x1080?

---

### Post by gizmocan on 2010-06-10
Yes, my TV is 1080p, the file is 1080p and the same file plays beautifully on the same TV when I use my Win7 laptop. 

Thanks for the install order and all your help!

Can you just confirm that your nvidia driver version is 195.36.15? Do you also install nvidia-current-modaliases? And you don't install nvidia-glx-(anything), h264enc or ffmpeg?

When you say libvdpau, are you referring to libvdpau1 AND libvdpau-dev? 

Do you explicitly remove nouveau or blacklist anything?

---

### Post by cbilljones on 2010-06-10
> **gizmocan said:**
> Yes, my TV is 1080p, the file is 1080p and the same file plays beautifully on the same TV when I use my Win7 laptop. 

Thanks for the install order and all your help!

Can you just confirm that your nvidia driver version is 195.36.15? Do you also install nvidia-current-modaliases? And you don't install nvidia-glx-(anything), h264enc or ffmpeg?

When you say libvdpau, are you referring to libvdpau1 AND libvdpau-dev? 

Do you explicitly remove nouveau or blacklist anything?

Yup, i have 195.36.15, i generally just add the ppa, update and open synaptic, install nvidia-current(which should be 195.36.15). Let it add whatever it wants along with it; i have a few modaliases packages, so synaptic must have added them. h64enc and ffmpeg are used for video conversion/encoding and not required for playback. Adding ubuntu-restricted-extras will add some ffmpeg codecs, but not ffmpeg itself. Now, you can always check in System>Administration>Hardware Drivers, to make sure proper nvidia driver is installed and active. Yes, i mean libvdpau1 AND libvdpau-dev. I dont touch nouveau at all, activated nvidia driver is all you should have to do. Only thing i blacklist is alsa and i remove pulse, but thats only because i prefer oss, ive setup HD boxes with pulse/alsa for friends.

---

