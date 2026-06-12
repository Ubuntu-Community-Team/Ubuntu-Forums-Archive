---
title: "Multi-monitor blues"
date: 2011-04-23
forum: Multimedia Software
---

### Post by zaq.hack on 2011-04-23
I love Ubuntu. I have been a fan for years. I use it on all my servers; I even use it for Asterisk (because I think CentOS is clunky). I would rate myself as a senior IT professional.

[COLOR="Red"]**So ... why ... WHY is it so hard to set up multi-monitors?**[/COLOR]

I'm trying 11.04 64-bit beta on a new HP 8540w. It has an nVidia Quadro card for built-in OpenGL support. It supports UEFI and I'm messing with that a bit for lightning-fast boot times.

But, ultimately, I use 4-5 monitors at a time on Windows 7. This machine is fast enough to put all my Win7 stuff in a VirtualBox and save me the 2GB RAM of "overhead" when I don't need it. The problem is that multi-monitor support in Linux simply blows. Let's face it: Windows and Mac can do multi-monitor desktops in a snap.

I'm not afraid of the xorg.conf file. I use VI. But after two hours of trial-and-error to do something that takes SECONDS in any other serious OS, I'm left to wonder: WHY? WTF?

If you think about the xorg.conf file ... and then think about something like DisplayLink. We are lightyears away from being able to pop a USB device into a port, have Ubuntu recognize that, and then provision an "extended desktop" (new screen, whatevah) where you can start using it in just a few seconds ... it's science fiction for Ubuntu. I have two Diamond DisplayLink BVU 195's that are awesome for expanded screen real-estate ... in Windows. With Synergy, I usually end up running 4-5 screens from a single mouse and keyboard. I can run 4 from a single computer running Windows.

I have pixel envy.

[COLOR="SeaGreen"]**Is there a bounty I can offer money to?**[/COLOR] My TIME is worth more than what I want to sacrifice to xorg.conf. I'd put a few hundred bucks personally toward solving this problem. It's way, way past time for Ubuntu (or someone in the Linux world) to put this to bed. If you search through the forums and you see all the UNSOLVED problems for "xinerama" "nvidia" "dual monitor" or "multi-monitor," it adds up to hundreds of hours between the complainers ... and thousands to those who have just given up.

---

### Post by zaq.hack on 2011-04-23
Update: I got Twinview working; up to two monitors. I guess that will have to do, for now. Consolation prize - Synergy and a secondary Win7 box.

Does anyone out there consider themselves an expert at multi-monitor setup in Ubuntu? I'd really like to get more screen real-estate on the primary machine since it will be running most of the virtual machines ...

---

### Post by aphatak on 2011-07-20
I do not, by any stretch of imagination, consider myself an expert on Linux / Xorg.  However, I have been lucky enough to get a 4-monitor setup going under Ubuntu 10.04.  I have recently been banging my head against Ubuntu 11.04, trying to get a single desktop spanning four monitors - all I have so far to show for it is bumps on the head.  It looks like the improved version of Ubuntu does not allow for crazy oddballs who actually work on a desktop setup and not exclusively on a laptop with a tiny little screen!

I haven't given up - not yet.

---

### Post by phantom_ on 2011-07-21
i struggled against my new DisplayLink device all today.

i first got the green screen; then managed to *only* run the DisplayLink driven monitor. my other monitors (notebook LCD and another external LCD) failed.

my GPU is an Nvidia GeForce Go 7300.

there are tens of threads with failures, as far as i see nobody is succeeding in creating a multi-display environment in Linux, regardless of the Ubuntu version.

i checked the device in Windows XP, it is perfect. this is real sad for Linux :(

however, i found an official text giving details about the udlfb driver. 


here it comes;

> 
What is udlfb?
===============

This is a driver for DisplayLink USB 2.0 era graphics chips.

DisplayLink chips provide simple hline/blit operations with some compression, pairing that with a hardware framebuffer (16MB) on the other end of the USB wire.  That hardware framebuffer is able to drive the VGA, DVI, or HDMI monitor with no CPU involvement until a pixel has to change.

The CPU or other local resource does all the rendering; optinally compares the result with a local shadow of the remote hardware framebuffer to identify the minimal set of pixels that have changed; and compresses and sends those pixels line-by-line via USB bulk transfers.

Because of the efficiency of bulk transfers and a protocol on top that does not require any acks - the effect is very low latency that can support surprisingly high resolutions with good performance for non-gaming and non-video applications.

Mode setting, EDID read, etc are other bulk or control transfers. Mode setting is very flexible - able to set nearly arbitrary modes from any timing.

Advantages of USB graphics in general:

 * Ability to add a nearly arbitrary number of displays to any USB 2.0 capable system. On Linux, number of displays is limited by fbdev interface (FB_MAX is currently 32). Of course, all USB devices on the same host controller share the same 480Mbs USB 2.0 interface.

Advantages of supporting DisplayLink chips with kernel framebuffer interface:

 * The actual hardware functionality of DisplayLink chips matches nearly one-to-one with the fbdev interface, making the driver quite small and  tight relative to the functionality it provides. 
 * X servers and other applications can use the standard fbdev interface from user mode to talk to the device, without needing to know anything about USB or DisplayLink's protocol at all. A "displaylink" X driver and a slightly modified "fbdev" X driver are among those that already do.

Disadvantages:

 * Fbdev's mmap interface assumes a real hardware framebuffer is mapped. In the case of USB graphics, it is just an allocated (virtual) buffer.  Writes need to be detected and encoded into USB bulk transfers by the CPU. Accurate damage/changed area notifications work around this problem. In the future, hopefully fbdev will be enhanced with an small standard interface to allow mmap clients to report damage, for the benefit of virtual or remote framebuffers.
 * Fbdev does not arbitrate client ownership of the framebuffer well.
 * Fbcon assumes the first framebuffer it finds should be consumed for console.
 * It's not clear what the future of fbdev is, given the rise of KMS/DRM.

How to use it?
==============
 
Udlfb, when loaded as a module, will match against all USB 2.0 generation DisplayLink chips (Alex and Ollie family). It will then attempt to read the EDID of the monitor, and set the best common mode between the DisplayLink device and the monitor's capabilities.

If the DisplayLink device is successful, it will paint a "green screen" which means that from a hardware and fbdev software perspective, everything is good.

At that point, a /dev/fb? interface will be present for user-mode applications to open and begin writing to the framebuffer of the DisplayLink device using standard fbdev calls.  Note that if mmap() is used, by default the user mode application must send down damage notifcations to trigger repaints of the changed regions.  Alternatively, udlfb can be recompiled with experimental defio support enabled, to support a page-fault based detection mechanism that can work without explicit notifcation.

The most common client of udlfb is xf86-video-displaylink or a modified xf86-video-fbdev X server. These servers have no real DisplayLink specific
code. They write to the standard framebuffer interface and rely on udlfb to do its thing.  The one extra feature they have is the ability to report rectangles from the X DAMAGE protocol extension down to udlfb via udlfb's damage interface (which will hopefully be standardized for all virtual framebuffers that need damage info). These damage notifications allow udlfb to efficiently process the changed pixels.

Module Options
==============

Special configuration for udlfb is usually unnecessary. There are a few
options, however.

From the command line, pass options to modprobe
modprobe udlfb defio=1 console=1

Or for permanent option, create file like /etc/modprobe.d/options with text
options udlfb defio=1 console=1

Accepted options:

fb_defio	Make use of the fb_defio (CONFIG_FB_DEFERRED_IO) kernel
		module to track changed areas of the framebuffer by page faults.
        	Standard fbdev applications that use mmap but that do not
		report damage, may be able to work with this enabled.
		Disabled by default because of overhead and other issues.

console		Allow fbcon to attach to udlfb provided framebuffers. This
		is disabled by default because fbcon will aggressively consume
		the first framebuffer it finds, which isn't usually what the
		user wants in the case of USB displays.

Sysfs Attributes
================

Udlfb creates several files in /sys/class/graphics/fb?
Where ? is the sequential framebuffer id of the particular DisplayLink device

edid	       		If a valid EDID blob is written to this file (typically
			by a udev rule), then udlfb will use this EDID as a
			backup in case reading the actual EDID of the monitor
			attached to the DisplayLink device fails. This is
			especially useful for fixed panels, etc. that cannot
			communicate their capabilities via EDID. Reading
			this file returns the current EDID of the attached
			monitor (or last backup value written). This is
			useful to get the EDID of the attached monitor,
			which can be passed to utilities like parse-edid.

metrics_bytes_rendered	32-bit count of pixel bytes rendered

metrics_bytes_identical 32-bit count of how many of those bytes were found to be
			unchanged, based on a shadow framebuffer check

metrics_bytes_sent	32-bit count of how many bytes were transferred over
			USB to communicate the resulting changed pixels to the
			hardware. Includes compression and protocol overhead

metrics_cpu_kcycles_used 32-bit count of CPU cycles used in processing the
			above pixels (in thousands of cycles).

metrics_reset		Write-only. Any write to this file resets all metrics
			above to zero.  Note that the 32-bit counters above
			roll over very quickly. To get reliable results, design
			performance tests to start and finish in a very short
			period of time (one minute or less is safe).

--
Bernie Thompson <bernie@plugable.com>


web reference of the above text is [here]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/fb/udlfb.txt;h=7fdde2a02a27be74e7e45508e449b5376b28abca;hb=HEAD").

this text explains that a thorough support will be present in very soon kernel releases; however integration with X still has many problems like no GNOME panels, nvidia driver crashing, no right-click context menu, etc.

i hope DisplayLink support progresses more.

by the way, Pluggable has a [support forum]("http://support.plugable.com/plugable"); where we can discuss what is going on with Linux development!

---

### Post by jk121960 on 2011-07-22
I applaud you for stating the obvious, why it it that *nix kicks so much butt and can't seem to get the monitor issue solved, someone (smarter then me) has to step up and finally solve this problem, so thank you for stating with bold clarity the truth. If we are going to talk the talk, we have to walk the walk. 

--jerry

---

### Post by phantom_ on 2011-07-22
[here]("http://support.plugable.com/plugable/topics/usb_2_0_graphics_adapter_ubuntu_10_10") is an explicit thread from Pluggable support forum, starting 5 months ago.

Pluggable developer simply explains why device driver development is so problematic for Xorg. thanks for the honest replies.

it seems that we will not be able to deploy a full more than 2 display setup with any Linux distro.

it seems that Canonical is switching **from Xorg to Wayland as the X server**. and it also seems the switch will be happening in 2-3 releases; here are the news references from [Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=OTQyOA") and [OMG!Ubuntu!]("http://www.omgubuntu.co.uk/2011/02/wayland-enters-ubuntu-11-04-repo/").

i hope DisplayLink becomes PnP with the next X server!

if there is anybody with a solid solution, apart from the above useless news :) i look forward to learning it...

---

