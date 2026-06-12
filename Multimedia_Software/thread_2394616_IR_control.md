---
title: "IR control"
date: 2018-06-19
forum: Multimedia Software
---

### Post by sfranks on 2018-06-19
Please help!

I'm having trouble with setting up my IR remote control.

Background: I'm re-building my client-server Myth setup following a power supply fault in the server that took out most of the hardware. Of course the client wasn't affected, but I thought I'd re-build it at the same time in order to make client and sever Myth versions the same. I'm using Ubuntu 18.04 with all the latest patches.

The client is a Intel NUC (D34010WYK), and this is where my problems lie.

I am aware of the known bug with the NUC IR receiver, and have successfully used the published fix (essentially remove and reload the driver using modprobe). I'm confident that is OK, without the fix the IR driver doesn't load at all. And it is the same as I had to do for the earlier build on the same hardware, which has worked OK for years.

Having read the available material from the Internet, it seems the best approach for the IR receiver is to use ir-keytables to directly map the IR buttons to Myth keystrokes. For example I've mapped the Play button to KEY_P.  Doing this means I shouldn't need LIRC, which is attractive because makes things a bit simpler.

So that is what I set up. Using [FONT=Courier New]sudo ir-keytable -t[/FONT], I see the correct results for every button press. This is nice and reliable.

The *Power *button works, mapped to *KEY_SLEEP*. That button correctly puts the NUC in and out of sleep mode.

Now given that I am mapping all other IR button presses to keyboard keystrokes, I would expect to see them in, say, a text editor. Which I do: but only the four buttons *Up*, *Down*, *Left *and *Right*. Every other button is just lost, never to be seen. But as I say, they all show up perfectly in [FONT=Courier New]sudo ir-keytable -t[/FONT]. *Up*, *Down*, *Left *and *Right *also work at a command prompt.

I can't find any help on diagnosing this: all the material I have found (and its a lot!) says that it should Just Work. But in my case, four buttons work, and the rest don't.

So I tried using LIRC, like I did before this rebuild. But then I get a different problem: the buttons don't register reliably, and if they do, there is a strong chance they repeat forever. I've tried connecting LIRC to ir-keytable (as seems to be recommended); and also disabling the built-in event handler and using LIRC native drvers. Both approaches seem to have the same problem. This is all odd, as I documented the previous build, and I reckon I'm using the same conf files and settings. Oh yes: LIRC never asks which remote control I am using, even if I use [FONT=Courier New]dpkg-reconfigure[/FONT]. I have to copy the right conf table in myself. I'm sure I found an article that says LIRC has a problem with Ubuntu 18, but I now can't find it again. Anyway, I'd prefer the simpler mapping using ir-keytable if only I could get it to work.

I've read so many Internet articles I can feel them dribbling out of my ears. But I've found nothing to help me diagnose or fix the problem; or even anyone else with the same issue. But most articles refer, at the latest, to Ubuntu 17. I wonder if some change in 18 is the cause.

Can anyone offer me any suggestions? My family is getting restless without Myth, and I fear there may be a revolt. And I can't help feeling it shouldn't be so difficult!

Even some general guidance on how the button/key events are supposed to be processed would be appreciated. For example: how are key events routed to the console user's client session (as opposed to, say, a remote connection)? Is there any way to see them other than [FONT=Courier New]ir-keytable -t[/FONT]?

Any and all help would be very much appreciated.

In case it helps, various details:

cat /proc/version:
Linux version 4.15.0-23-generic (buildd@lgw01-amd64-055) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018

dmesg (fragment showing driver loading):
```
...
[    7.414633] nuvoton-cir 00:05: [io  0x0240-0x024f]
[    7.414691] nuvoton-cir 00:05: [irq 3]
[    7.414697] nuvoton-cir 00:05: [io  0x0250-0x025f]
[    7.416230] nuvoton-cir 00:05: activated
[    7.416263] nuvoton-cir 00:05: found NCT6776F or compatible: chip id: 0xc3 0x33
[    7.427521] lirc_dev: IR Remote Control driver registered, major 239
[    7.430456] IR LIRC bridge handler initialized
[    7.464062] Registered IR keymap rc-rc6-mce
[    7.468110] IR RC6 protocol handler initialized
[    7.496132] rc rc0: Nuvoton w836x7hg Infrared Remote Transceiver as /devices/pnp0/00:05/rc/rc0
[    7.496217] input: Nuvoton w836x7hg Infrared Remote Transceiver as /devices/pnp0/00:05/rc/rc0/input12
[    7.497142] lirc lirc0: lirc_dev: driver ir-lirc-codec (nuvoton-cir) registered at minor = 0
[    7.497184] nuvoton-cir 00:05: driver has been successfully loaded
...
```

```
ir-keytable:
Found /sys/class/rc/rc0/ (/dev/input/event11) with:
	Name: Nuvoton w836x7hg Infrared Remote Transceiver
	Driver: nuvoton-cir, table: rc-rc6-mce
	lirc device: /dev/lirc0
	Supported protocols: lirc rc-5 rc-5-sz jvc sony nec sanyo mce_kbd rc-6 sharp xmp
	Enabled protocols: lirc rc-6
	bus: 25, vendor/product: 1050:00c3, version: 0x0033
	Repeat delay = 500 ms, repeat period = 250 ms

ir-keytable -t:
Testing events. Please, press CTRL-C to abort.
4281.432364: event type EV_MSC(0x04): scancode = 0x800f0416		<= Press Play
4281.432364: event type EV_KEY(0x01) key_down: KEY_P(0x0019)
4281.432364: event type EV_SYN(0x00).
4281.692087: event type EV_KEY(0x01) key_up: KEY_P(0x0019)
4281.692087: event type EV_SYN(0x00).
4284.093405: event type EV_MSC(0x04): scancode = 0x800f0422		<= Press OK
4284.093405: event type EV_KEY(0x01) key_down: KEY_SPACE(0x0039)
4284.093405: event type EV_SYN(0x00).
4284.242213: event type EV_MSC(0x04): scancode = 0x800f0422
4284.242213: event type EV_SYN(0x00).
4284.508081: event type EV_KEY(0x01) key_up: KEY_SPACE(0x0039)
4284.508081: event type EV_SYN(0x00).
4286.883651: event type EV_MSC(0x04): scancode = 0x800f041e		<= Press Up
4286.883651: event type EV_KEY(0x01) key_down: KEY_UP(0x0067)
4286.883651: event type EV_SYN(0x00).
4287.033176: event type EV_MSC(0x04): scancode = 0x800f041e
4287.033176: event type EV_SYN(0x00).
4287.292044: event type EV_KEY(0x01) key_up: KEY_UP(0x0067)
4287.292044: event type EV_SYN(0x00).
4288.496596: event type EV_MSC(0x04): scancode = 0x800f041f		<= Press Down
4288.496596: event type EV_KEY(0x01) key_down: KEY_DOWN(0x006c)
4288.496596: event type EV_SYN(0x00).
4288.764081: event type EV_KEY(0x01) key_up: KEY_DOWN(0x006c)
4288.764081: event type EV_SYN(0x00).
4289.819410: event type EV_MSC(0x04): scancode = 0x800f0421		<= Press Right
4289.819410: event type EV_KEY(0x01) key_down: KEY_RIGHT(0x006a)
4289.819410: event type EV_SYN(0x00).
4290.076104: event type EV_KEY(0x01) key_up: KEY_RIGHT(0x006a)
4290.076104: event type EV_SYN(0x00).
4291.132115: event type EV_MSC(0x04): scancode = 0x800f0420		<= Press Left
4291.132115: event type EV_KEY(0x01) key_down: KEY_LEFT(0x0069)
4291.132115: event type EV_SYN(0x00).
4291.388090: event type EV_KEY(0x01) key_up: KEY_LEFT(0x0069)
4291.388090: event type EV_SYN(0x00).
4293.182179: event type EV_MSC(0x04): scancode = 0x800f0423		<= Press Back
4293.182179: event type EV_KEY(0x01) key_down: KEY_ESC(0x0001)
4293.182179: event type EV_SYN(0x00).
4293.330480: event type EV_MSC(0x04): scancode = 0x800f0423
4293.330480: event type EV_SYN(0x00).
4293.596100: event type EV_KEY(0x01) key_up: KEY_ESC(0x0001)
4293.596100: event type EV_SYN(0x00).
^C
```

---

### Post by sfranks on 2018-06-22
Hi all: in case it helps someone else, I found a work-around/fix for this problem.

To load my keystroke mappings, I was using something like:

```
ir-keytable -c -w /home/myuser/mythkeytable

```
after logging in. I did this so I could easily refine the keytable once it was working.

Checking using
```
ir-keytable -t

```showed it worked: it reported the correct keystrokes from every button.

I have now found that putting the keytable in [FONT=Courier New]/etc/rc_keymaps[/FONT] and changing [FONT=Courier New]/etc/rc_maps.cfg[/FONT] to point to my keytable fixes the problem.

Fragment of [FONT=Courier New]/etc/rc_maps.cfg[/FONT]:
```
*       rc-pv951                 pv951
#*      rc-rc6-mce               rc6_mce
*       rc-rc6-mce               mythkeytable
*       rc-real-audio-220-32-keys real_audio_220_32_keys
```

I don't know why: most of the "how-to" guides suggest using [FONT=Courier New]ir-keytable -w[/FONT] in a login script, so I think it must normally work. But using [FONT=Courier New]/etc/rc_maps.cfg[/FONT] looks to be a better approach anyway, so I'm happy with this fix.

I hope this helps someone at some point!

Stephen

---

### Post by geeuz on 2018-07-06
Hi, may I have a question because I didn't find much about my problem Ubuntu 18.04 related.

I have a NUC7i3 and the problem is, my Harmony Remote Commands are executed twice every time. That happens if I only use ir-keytable, if I use lirc it jumps ~5 times.

I already tried hours to configure lirc and ir-keytable, but I have no clue how I will get it working.

If I use "ir-keytable -t" I see the commands two times.

On 16.04 I did "dpkg-reconfigure lirc" and a Setting Menu popped up to configure "Windows Media Center Transceiver", but on Ubuntu 18.04 I don't get a Configuration Menu.

LibreElec works if I deactivate LIRC in services, but I have to use Ubuntu because of other reasons.

Any help is highly appreciated. Thanks in advance.

---

