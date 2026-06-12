---
title: "Screen resolution changes constantly (EDID/KVM switch issue, seems to be the problem)"
date: 2013-09-23
forum: Multimedia Software
---

### Post by jgratero on 2013-09-23
I have an issue that has been going on for quite a while: It has to do with the resolution of my screen, that changes (on and off) every other boot. I use a D-Link KVM switch (DKVM-4K), and my monitor is a Samsung SyncMaster 943SNX Plus. I have two PC's connected, using that same monitor (hence the KVM switch requirement) 

The problem started a few months ago: Suddenly, the resolution defaulted to 1024x768. If I were to check the "monitor settings" section, there was no possibility to change it (on those moments, the max. resolution recognized by the system was that one). Grub resolution changed as well, showing bigger fonts and display. I was puzzled.

A few days later, it changed back, but with an issue: Resolution changed between login screen, and desktop startup. At the login screen it showed the correct one, 1360x768, but once in the desktop, it showed the 1024x768 (???). I those occasions, I was able to change it back using the "monitor settings section":

[IMG]http://i39.tinypic.com/10yf02v.png[/IMG]

Every once in a while, after Grub, it showed this:

[IMG]http://i42.tinypic.com/2088ho9.jpg[/IMG]

I checked further on the EDID issue with the **dmesg | grep drm**, and I found this:

> johnny@johnny-FQ652AA-ABA-CQ2009F-NA910:~$ dmesg | grep drm
[   15.184259] [drm] Initialized drm 1.1.0 20060810
[   15.845191] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.845201] [drm] Driver supports precise vblank timestamp query.
[   15.904301] [drm] initialized overlay support
[   16.127411] fbcon: inteldrmfb (fb0) is primary device
[   16.226627] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   16.335080] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   23.700322] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 204
[   23.836045] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 171
[   23.972038] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 132
[   53.248075] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 214
[   54.352093] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 193
[   55.044036] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 224
[   55.180072] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 146
[  120.264046] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 28
[  125.608059] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
johnny@johnny-FQ652AA-ABA-CQ2009F-NA910:~$

So, what exactly is this? Why is the resolution changing on and off?

Any ideas?

---

