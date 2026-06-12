---
title: "FGLRX 8.10 + Hardy Heron 64bit = strange"
date: 2008-12-04
forum: Multimedia Software
---

### Post by CHaoSlayeR on 2008-12-04
Hi there,

I know there are a lot posts in this forum and other about problems regarding to the ATI/AMD fglrx driver. I'm currently searching for a solution for about 3 days now with only half success. So I'm asking for help here.

The problem I had is after applying an update (don't know what it was - is there a log of updates anywhere?) the apt supplied fglrx driver 8.5 stopped working in a way that I had the slow scrolling and slow window redraw bug again. In addition to that the xv module was working but did it's job on the CPU rather than the GPU so I checked dmesg and the Xorg.0.log to find out that DRI was missing and the software OpenGL driver was used. I then experimented a lot with my previously working xorg.conf without any success.

Then I thought I give the latest driver directly from ATI (8.11) a try and that was even worse. That driver just did't work with my xorg.conf resulting always in the "low graphics mode". So I removed all driver stuff again and installed the 8.10 driver using the instructions at [Ubuntu Hardy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") with the success that it was giving me my old resolution back. After some tweaking I also managed to get DRI/OpenGL working again.

But the strange issue with slow scrolling/window management and software processed xv remained. That was the first day with this issue. The last 2 days I experimented a lot with my xorg.conf to first get the slow scrolling issue fixed. I managed to do that by activating Composite and applying translucency/shadow effects to the windows in KDE 3.5 (strange huh?). I completely removed compiz and xserver-xgl stuff and it worked like a charm. As long as those effects are activated the performance is very good. When I deactivate the effects in "window behavior" the slowdown can be seen immediately.

So I left the composite extension enabled. The next task was a bit harder: getting the xv working again. The issue was that whenever I wanted to open a video file using the xv option the X server hardlocked with a blank screen. From a remote console I saw that it jumped to 100% CPU usage (using both of the AMD X64 cores). The last thing I could see was the first frame of the video before both of my CRTs went black. The only thing I could do after that was to hard reset the machine. After a lot of research in this forum and in other places on the web I managed to get it working as expected by not using xv. I currently configured the standard video out option for mplayer to "gl:yuv=3". With that the CPU usage is very low as expected (even a Matroska in HD resolution) and scaling is working correctly (scaling totally failed when I used the X11 option, plus the CPU usage was very high even at PAL resolution).

Now all things are working somehow but I don't think it is the way it is supposed to work! I saw a lot of users with similar hardware configurations as mine being able to get hardware accelerated video using xv without a crash and without the flickering issue.

Summary:
- smooth scrolling/window resize/movement only with composite + effects
- efficient accelerated video playback/scaling only with -vo "gl:yuv=3"

Hardware:
- 2x 19" CRT (2x 1280x1024 @ 85Hz)
- AMD/ATI Radeon HD 2400 PRO (RV610) (PEG)
- AMD Athlon 64 X2 4400+ @ 2.3 GHz
- 2GB RAM
- ASRock ALive NF6P-VSTA Mainboard (nVidia nForce 2 MCP61)
- LG GSA-H55N DVD/-RW writer (SATA)
- Samsung SH-S182M DVD/-RW writer (PATA)
- 1x Hitachi HDS72161 250GB HDD (SATA)
- 2x Hitachi HDT72505 500GB HDD (SATA)

Software:
- Ubuntu Gutsy Gibbon upgraded to Hardy Heron
- kdm
- kde 3.5
- xfce
- FGLRX 8.10 (configured for BigDesktop)

Thanks in advance for any hints/help!

C]-[aoZ

---

