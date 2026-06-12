---
title: "xbmcbuntu No sound over HDMI (outside of xbmc)"
date: 2013-02-08
forum: Multimedia Software
---

### Post by essenceofaaron on 2013-02-08
I am brand new to linux, but XBMCbuntu does what i am looking for in terms of my HTPC... except for one thing.


I cant get sound to work via HDMI in anything except XBMC. 

I can get it working really easily in xbmc just by changing the audio output, but i have no idea how to do that for the rest of the machine

I've looked for guides as to how to fix it, but they all just point to fixing audio inside XBMC or unmuting. which doesnt help me.

since i'm brand new, i really have now idea what the terminal commands are, i've just been following guides i've found online. 

any help would be greatly appreciated

---

### Post by turb0chrg on 2013-04-06
I am having the same issue. XBMC it works fine, XBMCbuntu is not working. alsamixer looks good (not muted, etc). Here's my device

$ lspci | egrep -i audio
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe8f8000 irq 47

Any suggestions?

Joel.



> **essenceofaaron said:**
> I am brand new to linux, but XBMCbuntu does what i am looking for in terms of my HTPC... except for one thing.


I cant get sound to work via HDMI in anything except XBMC. 

I can get it working really easily in xbmc just by changing the audio output, but i have no idea how to do that for the rest of the machine

I've looked for guides as to how to fix it, but they all just point to fixing audio inside XBMC or unmuting. which doesnt help me.

since i'm brand new, i really have now idea what the terminal commands are, i've just been following guides i've found online. 

any help would be greatly appreciated

---

