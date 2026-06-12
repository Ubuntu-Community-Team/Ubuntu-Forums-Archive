---
title: "No Sound in Fiesty Fawn Gateway Laptop"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by johntkucz on 2007-06-20
Hello, I recently installed Fiesty Fawn v7.04 on a gateway laptop and have never experienced sound:

lspci -v returns this:

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0100000-d01fffff
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at d0504000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at d0505000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at d0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at d0507000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 18
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0100000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Capabilities: <access denied>

08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at b000 [size=256]
        Memory at d0200000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>


Then I followed the alsa installer instructions for ATI,but when I hit the 

./configure --with-cards=hda-intel --with-sequencer=yes;make;make install

command, it returned a Permission denied ( error 1)

after a lot of processes:
install: cannot remove `/usr/include/sound/uda1341.h': Permission denied
install: cannot remove `/usr/include/sound/util_mem.h': Permission denied
install: cannot remove `/usr/include/sound/version.h': Permission denied
install: cannot remove `/usr/include/sound/vx_core.h': Permission denied
install: cannot remove `/usr/include/sound/wavefront.h': Permission denied
install: cannot remove `/usr/include/sound/wavefront_fx.h': Permission denied
install: cannot remove `/usr/include/sound/ymfpci.h': Permission denied
make: *** [install-headers] Error 1

Help! THanks

---

### Post by Ziox on 2007-06-21
I believe that even the most current version of also doesn't support SB450 (most likely a Sigmatel Card).  My friend has the exact problem.  The strange thing is that I've heard that if you have a USB speaker, then you can hear sound from that speaker....

---

### Post by Soybean on 2007-06-22
My wife has a Gateway laptop with an ATI SB400 that wasn't working in Feisty... it might be a similar problem. I tried a lot of different things, but as far as I can tell, the solution was to mute the "External Amplifier" (all the way to the right) in alsamixer.

Seems worth a shot, at least.

---

### Post by Ylang on 2007-06-28
I have been having the same exact problem. I also have a gateway laptop, and my sound has never worked, I did buy a usb sound card, but I cannot say that it helped in the slightest.

---

### Post by eternalsword on 2007-06-28
> **johntkucz said:**
> 
./configure --with-cards=hda-intel --with-sequencer=yes;make;make install


this should be:
./configure --with-cards=hda-intel --with-sequencer=yes;make;sudo make install

it will prompt you for your password when it's ready to install

---

### Post by Ylang on 2007-06-29
Wait. Soybean. How do you mute the external amplifier? Is it just in the volume controls? I can't find it. Sorry, I am really new to Ubuntu
.

---

### Post by eternalsword on 2007-06-30
> **Ylang said:**
> Wait. Soybean. How do you mute the external amplifier? Is it just in the volume controls? I can't find it. Sorry, I am really new to Ubuntu
.

open up alsamixer in the terminal and look for "External Amplifier"  if you see it, press the right arrow until it is the item selected (the item selected has red text and arrows and it's label will appear at the Items up top).  If the bar has an MM, it is muted otherwise press the m key to mute it.  While you're in alsamixer, you can make sure other things are not muted or turned down.  To control volume within alsamixer for the currently selected item, use the up and down arrow keys.  To exit alsamixer, hit the Esc key.

---

### Post by russellnation on 2007-07-01
yes, like the others my gateway laptop (almost 3 years old m450 or something like that with intel integrated 82801... ) no audio -> i muted the external amplifier and now jammin out to some floyd dark side of the moon.
much thanks

---

### Post by russellnation on 2007-07-01
open terminal
- type in (without the quotes) "alsamixer"
push the right arrow key untill you see external amplifier highlighted them push the letter M key on your keyboard
- hit esc 
- put on some sweet musics and enjoy

---

### Post by PolycarbGuru on 2007-07-01
> **russellnation said:**
> open terminal
- type in (without the quotes) "alsamixer"
push the right arrow key untill you see external amplifier highlighted them push the letter M key on your keyboard
- hit esc 
- put on some sweet musics and enjoy

That only works if you have an "external amplifier".

---

### Post by johntkucz on 2007-07-30
okay, some major new good news in this thread. Still, sound is not operating in Fiesty Fawn on the gateway mx3701 (i'll never get a gateway again, so undurable and mucho problemas, unlike harder shell laptops (dell/thinkpads/macs) -- anyways.  I finally got sound working on the windows xp boot.  YES! So psyched I finally got the dual-OS system boot, first time, down! Very psyched (A long-term goal is to add in mac os -- triple-OS boot, but let's not get too far ahead!)
Anyways, strangely, even with hte original boot disk that came with the computer, I still had to download an ATI audio driver.....hhmmm. The windows xp sound works, but only with that driver. My question is, can I get the ubuntu fiesty fawn OS to do some crazy Wine conversion stuff with that windows xp driver? The driver I need for xp sound to work is:

D00664-001-001.exe

Found here

[http://support.gateway.com/support/drivers/getFile.asp?id=20815&dscr=SigmaTel%20Audio%20Driver%20version:%205.10.5082.0&uid=167131185](http://support.gateway.com/support/drivers/getFile.asp?id=20815&dscr=SigmaTel%20Audio%20Driver%20version:%205.10.5082.0&uid=167131185)

Anyone know how to wing that?

Obviously, I've done a LOT of work with this same sound problem on threads
12644 -- [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg375452.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg375452.html)

and 

8321

I finally, atleast have sound in xp, to watch a movie, I had to "time it with sound from an external phone" with the soundless movie! (very difficult synching!)

Thanks

---

### Post by johntkucz on 2007-08-01
> **Ziox said:**
> I believe that even the most current version of also doesn't support SB450 (most likely a Sigmatel Card).  My friend has the exact problem.  The strange thing is that I've heard that if you have a USB speaker, then you can hear sound from that speaker....

intersting....No sound (even with headphones) here.  do get sound in windows xp.  some other fishy stuff.  in prvious installations, I couldn't even get the volume onscreen indicator to display, now it updates with increments and decrements graphics (works when xp sound works).

---

### Post by johntkucz on 2007-08-01
> **russellnation said:**
> open terminal
- type in (without the quotes) "alsamixer"
push the right arrow key untill you see external amplifier highlighted them push the letter M key on your keyboard
- hit esc 
- put on some sweet musics and enjoy


right...well, obviously it's not that simple for my system.  although I think i've already tried this I remember one special command that showed all the alsamixer channels (some are hidden).  what is that?

---

### Post by anewguy on 2007-08-07
I have another version of a Gateway laptop, and sound never worked for it "out of the box".  However, it was no big problem for me, so in the face of redundancy, I'll tell you what I had to do to get sound working on mine:

- double-click on the volume control in the top bar to open up the volume control

- if it does not already say "(ALSA MIXER)", then go to file and Change Device to the ALSA MIXER for you sound (mine gives me choices about such things as the modem sound at the same time).

- click "Edit" and "Preferences"

- scroll down to "External Amplifier" and be sure it is checked - if not, check it, then close the
"Preferences" window so you are back to the main volume control menu

- click the "Switches" tab, find "External Amplifier" in it and UNCHECK it here (I know it seems counter-intuitive)

- now check your sound

This may be redundant to you, it may be too basic to you in that you may have already gone beyond this stage, but it is what worked for my Gateway laptop.:)

---

### Post by johntkucz on 2007-08-08
> **anewguy said:**
> I have another version of a Gateway laptop, and sound never worked for it "out of the box".  However, it was no big problem for me, so in the face of redundancy, I'll tell you what I had to do to get sound working on mine:

- double-click on the volume control in the top bar to open up the volume control

- if it does not already say "(ALSA MIXER)", then go to file and Change Device to the ALSA MIXER for you sound (mine gives me choices about such things as the modem sound at the same time).

- click "Edit" and "Preferences"

- scroll down to "External Amplifier" and be sure it is checked - if not, check it, then close the
"Preferences" window so you are back to the main volume control menu

- click the "Switches" tab, find "External Amplifier" in it and UNCHECK it here (I know it seems counter-intuitive)

- now check your sound

This may be redundant to you, it may be too basic to you in that you may have already gone beyond this stage, but it is what worked for my Gateway laptop.:)


Hey anewguy,
Sincerely appreciate sharing your personal fix-it.  I've tweaked with those checkboxes and panels, so not sure if this will work, but let's hope occam's razor (simplest answer is the best) prevails in this case!  Given all my previous efforts of complex and simple strategies, not sure if it will, but regardles....Thanks A TON for taking the time to post your fix it!  I've booted (dual in xp, now) but if I can get sound to work, it will be all ubuntu from now on, baybaby!

---

### Post by fooman on 2007-08-10
i have a gateway mx6453 and for 6 months i went without hearing a peep outa this thing. :(

a few months ago i happened upon this thread:

[http://ubuntuforums.org/showthread.php?t=276343&highlight=gateway](http://ubuntuforums.org/showthread.php?t=276343&highlight=gateway)

the "fix" provided by Donn on the 2nd page of that thread worked beautifully for me.  i followed his instructions and almost fell out of my seat when i rebooted to the wonderful sounds of ubuntu's opening jingle.   =D>

sound now works perfectly!  ...hope it helps.  :)

---

### Post by johntkucz on 2007-08-17
> **fooman said:**
> i have a gateway mx6453 and for 6 months i went without hearing a peep outa this thing. :(

a few months ago i happened upon this thread:

[http://ubuntuforums.org/showthread.php?t=276343&highlight=gateway](http://ubuntuforums.org/showthread.php?t=276343&highlight=gateway)

the "fix" provided by Donn on the 2nd page of that thread worked beautifully for me.  i followed his instructions and almost fell out of my seat when i rebooted to the wonderful sounds of ubuntu's opening jingle.   =D>

sound now works perfectly!  ...hope it helps.  :)

Can't say if you fix will work, but I tweaked the sound control panel so the source is STAC92xx (Not Connected) for output and I get a BEEP -- it's a default, low-scale default system beep!  However, aplay, alsamixer, and the right-hand click sound menu don't load, also, the other device options in sound menu are gone! ??:confused::)

---

### Post by johntkucz on 2007-08-17
My info:
Codec: SigmaTel STAC9200

Default system beek Works. Only with
these parameteres

The panel sound control is "xed" out.  WheneveR i try to do a "Test" from the sound control panel, it crashes.  No devices show up under sound contro lpanel.

Panel Sound says "No Volume control Gstreamer plugins found"

alsamixer, aplay do not work

Sound control panel
playback: STAC92xx Analog (not connected)
playback music:STAC92xx (Not Connectioned)
audio confere playback: Autodetect
audi Capture: ALSA
Device: No options
No options

---

### Post by netron on 2007-08-22
> **fooman said:**
> i have a gateway mx6453 and for 6 months i went without hearing a peep outa this thing. :(

a few months ago i happened upon this thread:

[http://ubuntuforums.org/showthread.php?t=276343&highlight=gateway](http://ubuntuforums.org/showthread.php?t=276343&highlight=gateway)

the "fix" provided by Donn on the 2nd page of that thread worked beautifully for me.  i followed his instructions and almost fell out of my seat when i rebooted to the wonderful sounds of ubuntu's opening jingle.   =D>

sound now works perfectly!  ...hope it helps.  :)

did that fix by Donn - no luck.  still no sound.

fresh feisty install.

---

