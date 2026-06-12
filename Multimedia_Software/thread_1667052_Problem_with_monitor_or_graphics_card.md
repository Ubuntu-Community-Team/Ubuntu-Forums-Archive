---
title: "Problem with monitor or graphics card"
date: 2011-01-14
forum: Multimedia Software
---

### Post by gramsyn on 2011-01-14
Hello everyone.

I have connected a PC running Ubuntu 10.10 to an LG TV through HDMI. I get an image, but the borders are out of the screen. At the screen options, the monitor isn't listed correctly. Ubuntu recognise the monitor as Goldstar Company Ltd. 52" or Denon 52" whereas it is LG 47". (Note that Denon is the AV receiver which intervenes to PC and TV). I suppose it produces an image for 52", and for this reason I cannot see the borders. 

Is it a problem of the graphics card driver or of the monitor driver?

My card is add-on to i3 Intel processor. The graphics controller is identified as graphics controller "Intel Core Processor Integrated Graphics Controller". 

LG doesn't provide a driver for Linux. Is there any other site where I can find the proper driver? 

Or is there anything else I can do to fix this? It is vital for me, as I cannot work at all with this setup.

Thanks in advance

---

### Post by BicyclerBoy on 2011-01-14
You need to setup the TV to use just-scan/direct pixel mapping/no-overscan.

On some TVs this requires you set the input to type PC input.
On some TVs you need to select professional mode (Pany V20) to do much adjustment.
Hdmi connection is required.

LG is Goldstar.
i3 CPU has a crappy integrated GPU.
The video adapter EDID probe detects the AVR/HT amp as well as the display.

The video adapter is also an audio device.

You may get better performance with the *buntu supplied intel driver for i3.
But intel GPU video performance (decode MPEG2 MPEG4) is not very good.
The default i3 GPU performance with *buntu10.04 was terrible.

For good video you are best to disable the i3 GPU & buy a nvidia GT220/240/430.

---

### Post by BicyclerBoy on 2011-01-14
You need to setup the TV to use just-scan/direct pixel mapping/no-overscan.

On some TVs this requires you set the input to type PC input.
On some TVs you need to select professional mode (Pany V20) to do much adjustment.
Hdmi connection is required.

LG is Goldstar.
i3 CPU has a crappy integrated GPU.
The video adapter EDID probe detects the AVR/HT amp as well as the display.

The video adapter is also an audio device.

You may get better performance with the *buntu supplied intel driver for i3.
But intel GPU video performance (decode MPEG2 MPEG4) is not very good.
The default i3 GPU performance with *buntu10.04 was terrible.

For good video you are best to disable the i3 GPU & buy a nvidia GT220/240/430.

---

### Post by gramsyn on 2011-01-15
I decided to buy a graphics card (Gigabyte GTS450). After some adjustments, it finally worked.

However, I can have no sound from HDMI. (Graphics and video work fine). From the sound options, I choose as harware the already listed HDA NVidia with profile Digital Stereo HDMI Output. But no sound...

What should I do?

---

### Post by BicyclerBoy on 2011-01-15
First let's make sure the video driver is right..
That 2d 3d & vdpau work okay..

from terminal
glxgears
vdpauinfo

What nvidia driver version are you running ?
I think you need 260...

---

### Post by gramsyn on 2011-01-15
Thanks for the immediate reply.

I am using the Nvidia version 260.19.06

From the glxgears, i get 16500 - 16900 FPS

However, I get error when I type vdpauinfo

---

### Post by gramsyn on 2011-01-15
I mean that it returns "command not found"

---

### Post by BicyclerBoy on 2011-01-15
Sorry vdpauinfo comes from ppa..

[http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu)

You need to add this in synaptic then reload & search for it & install.

It will also ensure you install libvdpau.

---

### Post by gramsyn on 2011-01-15
I am sorry for the silly questions. I try to insert the address you typed in synaptic. I open the repositories / other software / add. 
I type it at the APT: but the add button remains faded (I cannot click it). Is there any alternative way. Or maybe, I am in the wrong place to type the address...

---

### Post by gramsyn on 2011-01-15
However I have found from the pre-set repositories a "vdpau-va-driver".

Maybe I should install this?

---

### Post by BicyclerBoy on 2011-01-15
No ...I think that is a VAAPI wrapper for vdpau functions..

browser to the posted link & there will be instruction to add repository & to get the public key.

---

### Post by gramsyn on 2011-01-15
Sorry. I don't get it. I don't know where to look and what for. I can see no instructions for the repositories at that page. Is this important?

---

### Post by BicyclerBoy on 2011-01-15
Sorry

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

try that.

It is important to check each step is working.
Vdpau is necessary if you want decent video playback.

When you have issues with the media players you will at least know the video performance is not the case.

If this is not important then the i3 CPU/GPU was fine..

---

### Post by gramsyn on 2011-01-16
I am desperately stuck!!! I tried to enter the address to synaptic, it seemed to recognise it, but returned an error saying that cannot connect to the repository. I closed it and opened again. It returns the same error and closes instantly. It doesn't let me in, so I cannot delete the wrong repository. No synaptic program works.

I tried to post another thread for this (so I will not bother you with everything, but no one answered. Can you please tell me what I should do to fix Synaptic and then see what we can do to properly install the card.

Many thanks

---

### Post by BicyclerBoy on 2011-01-16
Synaptic package manager is stupid & ridiculous..

If you get a bad entry in the /etc/apt/sources.lis[FONT=Verdana]t it stops working

need to edit
[/FONT]gksudo gedit /etc/apt/sources.list

And remove the line that looks like what you typed in.. 
Then synaptic should recover.

---

### Post by gramsyn on 2011-01-16
You ROCK!!!

Now synaptic is fixed. However I am stupid enough (as it appears) for not being able to setup the repository for vdpau. I know that I am getting a menace, but I would really appreciate if you could help me with the card installation step-by-step.

To tell the truth I bought an NVIDIA brand-new card, because everyone suggested it as more compatible to Ubuntu and now, I cannot have video and sound from HDMI. For me it sounds terrible!

---

### Post by BicyclerBoy on 2011-01-16
Even long time Linux users can not get HDMI audio working without a struggle.

All the underlying support is not complete/not up to date.

I would just park the HDMI audio, it will work out of the box in 6-12 months.
The sound out of a TV is very poor.
S/PDIF matrix multichannel & 2ch PCM is generally fine.
Almost no audio material for HD audio.

So I don't hink HDMI audio is worth the trouble..
You need a new very good HT amp AVR & good loudspeaker system..this equates to about 0.1% of HTPC users.

---

### Post by gramsyn on 2011-01-16
This is the case: I have a home cinema (Denon amp and 5.1 speakers). I should send video and audio to the amp and the connect the amp to TV. However, I tried not to stick at this. I sent video to TV, which is Ok and tried to get sound from the integrated sound card through optical cable to the amp. The result is to get just stereo sound, not DTS or DD. I suppose maybe there are some adjustments of the sound card or try to solve the HDMI sound problem.

In the meanwhile, I finally succeeded to follow the instructions of your link and I think I installed the repository properly. The instructions now say: "Now you're ready to start installing software from the PPA! "

What should I install from the repository? I hope we are close to finish the second step...

---

### Post by BicyclerBoy on 2011-01-16
To get S/PDIF to the amp you need to select the digital pass thru' or alsa:IEC958 device.

No internal volume control & no mixer.
Pulse audio does not work with pass thru (AFAIK).

Your player software may be downmixing to 2ch PCM.
You are not selecting the AC3 audio track..

What player s/w do you use ?

Make sure the gnome-alsa-mixer alsa-mixer does not have the IEC958 muted.

Install
vdpauinfo

This will pull in libvdpau..

run vdpauinfo from terminal...
post the results.

---

### Post by gramsyn on 2011-01-18
I don't know why,but I can't install vdpau. However, I solved the problem with sound through VLC adjustments. Now I have video from HDMI and 5.1 Audio from optical. For me it seems ok,but if installing vdpau will vastly improve my system, maybe I try again.

Now I said that I solved the initial problem with the monitor (image bigger than the monitor). I used overscan compensation from NVidia Xsensor Settings. But I have to do it each time I turn on the PC. Can I save this settings?

---

### Post by BicyclerBoy on 2011-01-18
The default setting of most TVs is over-scan on.
For best PQ you should read the TV handbook & find the just-scan/direct pixel mapping/no over-scan setting.

You do not want to use the under/over scan settings in the video card.
Using native resolution scaling in GPU is sensible.
It is recommended to use YUV  colour-space setting (not RGB).

Some TVs require the user to select a setup/profile that is not the default preprogrammed.
Sometimes this is called professional mode.

VLC from repositories does not support vdpau.
If you use VLC at least enable de-interlacing filter yadifx2 & lancros or bi-cubic scaling.


IMO The default playback in most media players is not very good.

Vdpau is strongly recommended if you use with MythTV or XBMC or mplayer.

---

