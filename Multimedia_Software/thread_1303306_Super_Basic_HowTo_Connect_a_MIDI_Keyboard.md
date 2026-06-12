---
title: "Super Basic HowTo Connect a MIDI Keyboard"
date: 2009-10-28
forum: Multimedia Software
---

### Post by ArtInvent on 2009-10-28
The short story on connecting a MIDI keyboard to your Ubuntu computer: Get basically any MIDI keyboard, get a decent USB-MIDI interface like a Roland/Cakewalk UM-1G; connect to keyboard and USB port; turn on the keyboard; REBOOT. I would hazard a guess that most keyboards will be recognized and available as a MIDI device in Ubuntu Jaunty or later. You don't need drivers or discs, the driver if it exists is already in the Linux kernel. You will probably not get any sound connection out of the keyboard, however, until you configure the MIDI connections in your music app or JACK.

If that seems stupidly simple to guys who've been messing around with MIDI for years, well, yes it is. Unfortunately there's very little basic info about the above facts for newbs like I was who are just getting into computer-music connections and MIDI. There's certainly no mention of Linux whatsoever in most keyboard manuals or driver discs or USB MIDI adapter manuals. We are left to wonder if MIDI is solid in Ubuntu or if I buy a keyboard is there a good chance I will muck around for two weeks trying to get it to work, only to find this particular equipment just won't. It would certainly be nice if there were a list of MIDI equipment and interfaces somewhere that are know to work in most cases, but I couldn't find such. At any rate, the answer seems to be that yes indeed, MIDI is pretty solid and easy to implement. If only the information was out there.


Basically I just wanted to be able to teach/learn piano using some kind of computer program, preferably all FOSS. This is super basic, but once you get the equipment connected and making sounds, you can then move on to more advanced music and creation tools like Ardour and Rosegarden etc etc. I found PianoBooster which seems pretty cool as a teaching tool. You follow along with the score to a MIDI piano file and try and play the notes. If you make a mistake, it makes a bad sound and shows you the wrong note you played on the score, and waits for you to hit the right one. Then it keeps going. Simple, but effective way to learn to sight read.

Here is my equipment:
[LIST]
[*]Keyboard: Yamaha PSR-E323. This was $150 new, does a lot, sounds good.
[*]USB MIDI interface: Roland (Cakewalk) UM-1G, $40, I bought because it's suppose to work well with Linux.
[*]Ubuntu 9.04 Jaunty 64 (PulseAudio)
[/LIST]
Related basic music audio software installed:
[LIST]
[*]jackd
[*]qjackctl
[*]timidity
[*]vkeybd
[*]fluid-soundfont-gs
[*]fluid-soundfont-gm
[/LIST]


Then I had to get PianoBooster, which is a small program and not really 'with it' in the up-to-date dept. There is a ppa repo available for Ubuntu, but the latest release supported seems to be Intrepid. I went ahead and set the repo as Intrepid in Synaptic and was able to install and run the program, though there's no shortcut or icon in the main menu. Easy enough to make one.

So I hook up this keyboard to the UM-1G and plug it into the USB port. Messed around for quite a while and couldn't get any response on the computer, it just wasn't being recognized. It did not show in the PianoBooster MIDI config.

The short answer, to repeat, is to plug in the UM-1G, turn on the keyboard, and then reboot. Most USB stuff is plug and play; this thing apparently is not. Doing this, I finally saw the UM-1G show up in the Jack Control | Connect window, though for some reason it's under the ALSA tab and not the MIDI tab.

Note on the UM-1G: There are three lights on the little box. One lights up when connected a USB port. The MIDI IN light comes on when the keyboard is plugged in and turned on. The MIDI OUT light, however, remains off most of the time, which can make you think it's not working right. It only comes on when both the MIDI connection with the computer is made AND a musical key is pressed. It only lights up briefly when a key press has just been made. You can turn the keyboard off and on, and it will still work. But if you reboot the computer, you'll probably need to have it plugged in and the keyboard on during boot. (Though it's possible that just the UM-1G needs to be connected to USB.)

Next I opened PianoBooster and went to Setup | MIDI setup. I set both input and output device to UM-1G:0, and left latency at 0. Setting this output makes the sound come out through the keyboard. This way you don't need Timidity, it seemingly doesn't need to be running. Or, you can patch it to Timidity port 0 to hear it through the computer audio. Doing this however, I had to set the latency to about 250ms to get the audio to sync with the beats of the music notation. With PianoBooster, it so far seems preferable to do the former and have the sound output throught the keyboard speakers.

If you happen to have JACK Control running with the Connect window open to ALSA, you will actually see the connections being made and changing as you work the settings in PianoBooster. Cool. For use in other music/audio programs, you can use JACK to patch connections between MIDI ins and outs. JACK is like a physical patch bay in a recording studio, only a lot more flexible.

So there, for absolute newbs, is a quick little practical intro to getting some basic MIDI working on Linux. Yes, it works and it only gets better from here.

---

### Post by Anonymousable on 2009-10-28
Thanks! I have to have a look at this... I just never knew how to *use* the keyboard once connected.

---

### Post by markbuntu on 2009-10-28
I use patchage for connections. It shows everything in one panel and is point and click to make connections. My Korg nanos show up when I plug them in but need to be connected to something manually, which is what I use patchage for.

---

### Post by YusR on 2009-12-31
> **markbuntu said:**
> I use patchage for connections. It shows everything in one panel and is point and click to make connections. My Korg nanos show up when I plug them in but need to be connected to something manually, which is what I use patchage for.



can you explain this for me ....im trying to get my nano key to work and im having trouble

---

### Post by YusR on 2009-12-31
bump for some help

---

### Post by markbuntu on 2010-01-02
> **YusR said:**
> can you explain this for me ....im trying to get my nano key to work and im having trouble

What is your setup?
What apps are you using?
Can you see the nano in patchage?

---

### Post by gostal on 2011-02-17
I recently bought a Cakewalk UM-1G because I saw that you had it working in Ubuntu. I've been trying to set the thing up in OpenSuse 11.3 but sofar without success. The usb-sytem detects it OK but that's as far as it goes. I cant see it anywhere in the sound system. I would like to know precisely what modules you have running. I dont remember if there's a hardware utility in Ubuntu that gives you this info. If not I'd be happy if you were to post the output of the following command:

"lsmod"

or if that's too long settle for

"lsmod|grep snd" and "lsmod|grep usb"

Your output of 

"cat /proc/asound/cards" and 
"cat /proc/asound/oss/sndstat" 

would also be nice and for that matter relevant sections of /etc/modeprobe.conf.(The paths may look somewhat different on you system)

Thank you beforehand!

---

### Post by gnemo on 2011-05-07
I just spent a few hours trying to get a Yamaha YPT-410 keyboard to talk to Maverick Meerkat with the Trinity (KDE 3.5) desktop. The goal was to be able to type notes on the keyboard directly into MuseScore music notation software. This keyboard has onboard USB MIDI, with a MIDI port on the back for connection to a computer.

I worked at this for a couple of hours last night with no success at all. Artinvent's method (post #1) in this thread didn't work for me. Running "lsusb" showed that the computer never saw the Yamaha keyboard at all - it never appeared in the list of USB devices.

Today I found a page on USB MIDI keyboards on the Arch Linux wiki: 
[https://wiki.archlinux.org/index.php/USB_Midi_Keyboards]("https://wiki.archlinux.org/index.php/USB_Midi_Keyboards")

Following this guide, I was able to get my keyboard working. As far as I can tell, the key sentence in the guide is this apparently inconsequential one: "Now [COLOR="Red"]plug the keyboard in and turn it on[/COLOR]". Note the order of events - plug the keyboard in first, then power it on.

Last night, I had tried turning the keyboard on and then plugging the USB (MIDI) cable into the computer; I also tried leaving the keyboard on and plugged in and rebooting the computer, as per ArtInvent's suggestion in post #1. Neither worked.

Today I tried the sequence in the Arch wicki: Leave keyboard OFF, plug the USB cable into both the keyboard and PC, turn keyboard ON.

That tiny change did the trick. Running lsusb after turning on the keyboard  showed a new entry in the list of usb devices:
```

"Bus 003 Device 012: ID 0499:1037 Yamaha Corp. PSR-E403".

```

With the USB subsystem finally talking to the keyboard, running "aconnect -i" yielded this:
```

client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'YAMAHA DigitalKBD' [type=kernel]
    0 'YAMAHA DigitalKBD MIDI 1'

```

I then ran
```

aseqdump -p 20

```
Which produced a stream of text, of the form "20.0 Clock" and "20.0 Active Sensing". Pressing a key produced "Note on" and "Note off" messages mixed into the stream of "Clock" messages.

Apparently my Yamaha keyboard sends clock information continuously, unlike the example MIDI keyboard in the Arch Linux wiki. This is probably controlled by the onboard MIDI settings on my keyboard, but since everything worked properly I did not try to change it.

At this point I opened up MuseScore, loaded a score I had been working on, clicked on the MIDI icon at the top, tapped the letter "N" on the computer keyboard to go into note entry mode, and pressed a key on the Yamaha keyboard. And joy of joys, the note appeared on the staff in MuseScore.

Mission accomplished! I hope this helps someone else out there.

-Gnemo

---

