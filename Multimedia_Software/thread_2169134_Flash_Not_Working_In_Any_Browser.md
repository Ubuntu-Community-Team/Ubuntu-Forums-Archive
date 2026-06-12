---
title: "Flash Not Working In Any Browser"
date: 2013-08-20
forum: Multimedia Software
---

### Post by ktz84 on 2013-08-20
I can't get youtube videos to play in any browser. I have installed xubuntu restricted extras and I have installed Chromium and Chrome in addition to the preinstalled firefox.

I've tried the gnash swf viewer plugin for firefox and that gave me a black screen but no video which a slight step up from either it saying that my adobe couldn't load or needed to be upgraded.

I've tried everything I can find such as renaming the libflashplayer.so so that Chrome would use it's version but that made no difference. I've removed the adobe player and replaced with gnash viewer that did as described above.

Now I haven't a clue where to go from here? Help please.

I'm using xUbuntu 12.04 x86 and is a new install on an AMD Athlon XP 1800+ cpu with 1GB ram and ATI Radeon graphics card so old computer.

---

### Post by ktz84 on 2013-08-21
I'm reinstalling to see if I have any better luck this time. Fingers crossed.

---

### Post by ktz84 on 2013-08-21
Ok reinstalled again. This time all I have done is update and upgrade all packages. Then I installed xubuntu-restricted-extras. I then loaded firefox up and went to youtube where I get continual crash reports about the plugin-container. I installed Chromium hoping I'd have better luck there but I'm getting reports on it to say that chromium-browser has crashed however the browser itself doesn't crash. The report always happens after I reload youtube so it's clearly flash that this crash report is about also.

I thought 12.04 was supposed to be the stable version. The enterprise class version!

---

### Post by slw210 on 2013-08-21
Flash works fine for me on 12.04 Ubuntu, not running Xubuntu 12.04 anymore, but pretty sure it worked there as well.

Could you provide more info on your crashes? Screenshots, etc.

---

### Post by ktz84 on 2013-08-21
Neither now triggers a crash report as in an notice in the top panel however chromium puts a jigsaw puzzle piece where the video should be and a message to "Could not load Shockwave Flash"

Here's a screenshot of this:
[IMG]https://dl.dropboxusercontent.com/u/3136192/chromium%20flash%20error.png[/IMG]


Firefox on the otherhand draws the area where the video should be playing and its totally black then it changes to white and then finally switches back to black again where it just sits. As it's just a black box where the video should be I haven't screenshot that.

If you need more info please let me know.

---

### Post by ktz84 on 2013-08-21
Here is a screenshot of the Software Centre which shows that xubuntu-restricted-extras and flash are installed

[IMG]https://dl.dropboxusercontent.com/u/3136192/flash%20install.png[/IMG]

---

### Post by slw210 on 2013-08-21
Almost sounds like it is being blocked by an add-on of some sort.

No Ubuntu here at work, I can check tonight when I get home, though.

---

### Post by ktz84 on 2013-08-21
Thanks slw210 for trying to help. This is my sister's computer and she's been without it for 3 days now so I've had take the decision to put Windows XP back on it. She was a little apprehensive about moving to Linux though I had shown her how easy it was as I run it myself on a vm so she was willing to give it a go. I need to get it back to her so I couldn't send it back without flash considering the internet is about the only thing she uses it for.

On the positive side I like it so I may well switch my ubuntu 13.04 to xubuntu 13.04.

---

### Post by Cheesemill on 2013-08-21
It could have been an issue with your processor.

Recent versions of Flash have a requirement for certain instruction sets which older processors don't have, if this is the case then there is nothing you could have done about it except trying to install an old, unsupported version of Flash.

---

### Post by ktz84 on 2013-08-21
Works in XP Cheesemill so unless Adobe had different requirements for the cpu for linux and windows then surely it wouldn't work in XP either.

---

### Post by SweetAurora on 2013-08-21
Yes, Adobe does have different requirements for Linux. Your CPU has to have SSE2 instructions to run Flash v11.2. You will need to install Flash v11.0 or v10.0 if it only hase SSE1.

---

### Post by Cheesemill on 2013-08-21
They do have different requirements.

The Linux version requires a CPU with the SSE2 instruction set (which the Athlon XP doesn't have), the Windows version doesn't have this requirement.

---

### Post by RadicaX on 2013-08-21
Adobe does not update for Linux except in google chrome. I am running Xubuntu 12.04 and it runs fine on all the browsers I use. (firefox, google chromium, and google chrome.) Sadly, they probably do have a different hardware requirement. Windows XP still gets more drivers quite often than Linux. Your specs are about the same, except I use Intel for my processor. (Dual core.) and my graphics card is also intel. So it really probably is the Processor. You could try it on a Linux that has Flash already install and set and see if it works. (Linux Mint/ puppy linux. Your sister probably would not enjoy puppy though. Howbeit, it is just to check.) When I installed flash on my machine, I used flash aid. After that I just used Google Chrome which I had to download from their site.

And within the time of typing this Cheemill answered that question. So sorry, looks like you will need a different processor if you want flash. or hope shumway will support what your sister needs on such an old processor.

---

### Post by ktz84 on 2013-08-21
Ahh well that will the reason then. Glad someone was able to get to the bottom of it for me. It' such a shame because the system was quite usable even as old as it is however it's a good bit slower in xp and the updates are taking forever.

---

### Post by RadicaX on 2013-08-21
Yeah it is a shame. It would still be a great machine minus the flash. But that would mean it was better for work or things like that. Sadly, till HTML5 is the standard, and people make the switch completely off it, and flash is not as big a deal.. It causes problems.

---

### Post by lunoob-blunoob on 2013-09-14
I have the same symptoms. Running google-chrome from a terminal and trying to watch a youtube video, this is the treminal output:

Xlib:  extension "GLX" missing on display ":0".
[10887:10887:0914/090918:ERROR:gl_surface_glx.cc(327)] glxQueryVersion failed
[10887:10887:0914/090918:ERROR:gl_surface_x11.cc(58)] GLSurfaceGLX::InitializeOneOff failed.
[36:36:0914/090956:ERROR:webplugin_delegate_proxy.cc(390)] PluginMsg_Init returned false
[36:36:0914/090956:ERROR:webplugin_impl.cc(258)] Couldn't initialize plug-in
[36:36:0914/091020:ERROR:webplugin_delegate_proxy.cc(390)] PluginMsg_Init returned false
[36:36:0914/091020:ERROR:webplugin_impl.cc(258)] Couldn't initialize plug-in

And then:
@ubu10:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 6
model        : 6
model name    : AMD Athlon(tm) XP 1800+
stepping    : 2
cpu MHz        : 1529.247
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
bogomips    : 3058.49
clflush size    : 32
cache_alignment    : 32
address sizes    : 34 bits physical, 32 bits virtual
power management: ts


Rats! I guess it's the processor.

---

