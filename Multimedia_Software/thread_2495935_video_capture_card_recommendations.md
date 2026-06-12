---
title: "video capture card recommendations"
date: 2024-03-08
forum: Multimedia Software
---

### Post by revcrussell on 2024-03-08
I need to get a VGA signal (D-sub 15) and put it into a Linux box. I have a PCI slot and PCIe 8x slot available. Since we all know compatibility is a big issue I need to know if they device works before I buy it. I have no problems buying used.

Google searches aren't turning up anything really useful, maybe this: [https://ubuntuforums.org/showthread.php?t=1928003](https://ubuntuforums.org/showthread.php?t=1928003)

Can someone tell me of a working device?

Thanks.

---

### Post by TheFu on 2024-03-08
I've never used any VGA capture cards.  I have used a few Plextor, Haupauge, Magewell, and Chinese devices.  

Plextor recorder took input from the yellow cable or S-Video.  I used this back when we all had VHS and SVHS tapes to digitize.

My first TV tuner was a Haupauge 950Q - that had support for yellow cable or S-Video in addition to the tuner.  It was plug-in-play with V4L and V4L2, so it was easier. 

Later, I wanted to record 1080i stuff and got a Haupauge 1212 recorder. It only worked with MS-Windows. It was great until it overheated for some reason.  Because it was within warranty, Haupauge fixed it for free.  The 2nd 1212 recorder died too.  I'm uncertain why, but it was after the warranty ended, so I got their newer device, a 1515. I seemed to be the same as the 1212.  I was just trialing some alpha Linux code from Haupauge for the 1515 and it died. Because it was after the 1 yr warranty ended, I decided I'd had enough of their equipment.  These Haupauge would capture DTS/DD 5.1 audio too. It was pretty great.  However, none of them captured DD+.

Through some good luck, I found an AGPTek HDMI recorder.  This is a stand-alone HDMI / Component 1080p recorder, just connect some USB storage to it.  However, it only captures 2ch audio.  The quality of the captures isn't professional, but it is good enough for my needs.  2 of those devices have burned out, but they are about 1/3rd the cost of a single Haupauge 1515, so they aren't THAT expensive.  I fear they will stop working soon.

Last month, I picked up a Magewell SDI/HDMI capture PCIe card.  I'm still testing it, but it doesn't like my Ubuntu 20.04 OS. The newest versions of the driver and their capture software are for 22.04.  I'm running the 20.04 version. Their capture software has never worked with any of my inputs, but OSB sees the driver and has support to capture it, but only with a direct input from a camera.  The Magewell doesn't like any of my intermediate HDMI switching equipment, which makes it very difficult to use or recommend.  It claims to capture 2K video and whatever audio is passed through.  I haven't seen that and Magewell support refused to help unless I registered.  If I register, I cannot return the card to the seller.  I'm stuck.

Anyway - that's what I know. Nothing useful for VGA recording, sorry.   That link is about TV capture cards - those are usually TV Tuners like my Haupauge 950Q.  On that front, I can completely recommend Silicon Dust HDHR devices, but whether those are any use is completely dependent on your location in the world, how the broadcast TV signals get to you.

I fear the best answer for you is the run screen capture software on the source system, if you don't have an HDMI output.  If you can mirror the output from the VGA to HDMI or even DisplayPort, there are converters and HDMI splitters that will happily split the output to multiple locations - like the screen and a capture device.  That would be easier than dealing with VGA.

IMHO.

---

