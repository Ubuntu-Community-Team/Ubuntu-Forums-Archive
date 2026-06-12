---
title: "[SOLVED] Elisa mapping of remote control commands"
date: 2008-12-25
forum: Multimedia Software
---

### Post by pfbach on 2008-12-25
Alright,
I installed LIRC and tried to set up the imon IR/LCD that is integrated in the Antec Fusion case. Using the command mode2 -d /dev/lirc0 I did not receive any signals from the Hauppauge remote. Though I got a Samsung MF59-00291C remote to send signals, but the mode2 command only interpreted it with varying HEX codes when I pushed the same button. I then tried to install the Hauppauge card in order to use the IR receiver chipped with that card. The Remote control now works after installing the Hauppauge HVR 4000 card using this approach:
[HVR-4000 HOWTO]("http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-63073")

The problem now is that the signals used via the Hauppague card is handled by the IR_common module. Cited from [ Launchpad LIRC+IR_common]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67399"): "*This makes, by default (live cd included), an echo of numbers keys on my remote control to the active window, and also opens "shutdown menu" when pressing to the shutdown button.*"

The remote works perfectly in gnome, but it does not work the way I want in Elisa. The Up,Down,Left,Right and OK button work, but none of the others.
I end up being stuck in a sub-menu where I don't want to be or watching a movie I am unable to change.
The Backspace function is not working with the remote control, only from the keyboard.

I have not yet found a way to map any keys from the remote to Elisa.

AFAIK, it is not possible to generate own mappings using LIRC, because the IR_common module is being used.

I tried this approach but with no luck:
[MCE Remote control back key problem solved]("http://bentamor.wordpress.com/tag/elisa/")

I feel a bit stuck now, so any help is appreciated.

And by the way, I have to start Elisa using sudo because of the ATI/FGLRX driver...

LIRC version: 0.8.3
Elisa version: 0.5.22-1fluendo1~ppa1~intrepid1ubuntu1

Linux Vision 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

Antec Fusion V2/Black
AMD Phenom(tm) 8450 Triple-Core Processor
Gigabyte GA-MA78GM-S2H Motherboard
Integrated ATI Radeon HD 3200 Graphics
Hauppauge HVR 4000

fglrxinfo:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.8087 Release

---

