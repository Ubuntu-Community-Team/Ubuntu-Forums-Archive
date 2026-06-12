---
title: "Playing a midi keyboard"
date: 2008-11-04
forum: Multimedia Software
---

### Post by poldie on 2008-11-04
All I want to do is play a midi keyboard and hear piano-like sounds!  I have a midi keyboard, and I have an Edirol um 1ex usb to midi convertor.  I've had this working on Windows, and it appears that although there are no linux drivers for it, it can work without them.   

Before trying to get that working, though, I thought it would make sense to work from the other end, so to speak. I need something to make sounds with, so I've looked at qsynth (v0.3.3), and loaded soundfonts into it. I've installed rosegarden(v1.7.0), created some 'music' and have tried to send the midi messages to qsynth. I can see the light flashing on qsynth, so I believe I'm sending midi events to the right place, and sometimes I can hear sounds, although not always. And when I can, it's just random corrupt sounding noise - as if I'm playing non-audio data. I don't think the soundfont I've load is compressed.  If I try and load some other soundfonts in, qsynth hangs.  

Does anyone know what I'm talking about, and how to get around it?  I don't mind not using qsynth, and perhaps I don't need to use rosegarden once I've got the system working.  I'll use anything. I'm not interested in recording or anything, nor working with audio (so I don't think I need the 'Jack' app/driver).

Cheers.

edit: I'm using ubuntu 8.10 64 bit. I'm using alsa, I think!

---

### Post by Don Dakin on 2008-12-18
Hello there,

I am also having some problems getting midi to work with a keyboard plugged into the usb port of the computer.

First of all I have Ubuntu 8.10 amd64 installed on a toshiba laptop.

I was able to get a s/w synth working using jack (the midi device pops up in the alsa tab of the connection manager) to connect to a monophonic synth ( I forgot the name) So I know that the midi data from the keyboard is being read this way. when I plug in the keyboard I can see midi thing popping up in the /proc file tree and aconnect is showing midi devices.

Problem I am seeing is that /dev/midi1 does not seem to be sending data.

cat /dev/midi1 shows nothing (when tapping on the keyboard) this leading me to believe there is some driver/kernel issue.
I looks to me like the midi data stream is not routed to anywere in the /dev filesystem.

Can anyone out there shed some light ?

The program I am interested in using is an organ emulator called beatrix. This program requires the /dev/midi device to provide the input data stream from the keyboard.

I have dug around in /dev/snd and found other midi devices but none of them provide a data stream (using cat /dev/snd/whatever it was) 

I have not tried different kernels (yet)

Thanks in advance for any help you can provide

Regards

Don Dakin

BTW

Everything else worked really well and this ubuntu distro was the only one I could get to install on this laptop. Overall I'm really impressed and happy with it.

---

### Post by markbuntu on 2008-12-18
Have you tried patchage?
It shows all the possible connections you can make with midi and audio when you are using jack. You can use it to make and break the connections just by clicking on the boxes.

---

### Post by Don Dakin on 2008-12-20
Hi,

The program beatrix [http://people.dsv.su.se/~fk/beatrix_home.html](http://people.dsv.su.se/~fk/beatrix_home.html)

runs in a shell, very minimal but the sound samples on the web page sound good so I wanted to give it a try.

It really wants input on /dev/midi 

I think I need something in the /dev tree receiving midi from the keyboard for the program to read.

This program is not "jack" compatible as fas as I can tell.

Thanks

Don......

---

