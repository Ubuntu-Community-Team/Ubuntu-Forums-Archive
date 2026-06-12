---
title: "Record piano music using Ubuntu"
date: 2011-02-09
forum: Multimedia Software
---

### Post by 8jwong14 on 2011-02-09
Hi everyone.  I am interested in recording piano music using Ubuntu.  I don't want to use a mic.  I want to be able to connect my piano to my PC and record music.  

My digital piano is a Yamaha YPG-635 (Great digital piano by the way)  The digital piano has a 1/4 inch headphone port, and a USB port.  I am currently running Ubuntu 10.04.  I'll upgrade to 11.04 eventually.

I'd appreciate any assistance.

---

### Post by tommcd on 2011-02-09
Is the digital piano detected by Ubuntu?
When you plug in the piano via the usb port, try running **lsusb** in the terminal. It should list all usb devices connected to the computer, including the piano.
To record music you could use **audacity**. It is in the Ubuntu repos. [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
Here are some great video tutorials on digital music making in linux: [http://filmsbykris.com/](http://filmsbykris.com/)
See the videos under "*Music Editing/Creation*".
You may also be interested in ubuntu Studio: [http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by IceRoadTrucker on 2011-02-09
Ok, if I were you, I'd be doing the following:

1. Being happy that I discovered Linux and have a keyboard
2. Trying it out ASAP using a simple 1/8" cord going to your computer's *stereo line in*, just for instant gratification
2. Downloading something like Puredyne or Ubuntu Studio and installing it on another partition
3. Trying "JACK Control" within Puredyne or Ubuntu Studio (read: toying with it until you finally find right settings several months later) to see if it is recognized as a readable MIDI-client 
4. Using it to control Fluid Synth/Qsynth in realtime
5. Downloading new .sf2 Soundfonts all the time to use in Fluid/Qsynth
6. Recording both in Rosegarden (MIDI) and in Ardour (Audio) through Jack Audio.

Or rather, if you lent me your keyboard right now, that's what I'd be doing with it...I already have a virtual keyboard, to do this with, "VMPK."

---

### Post by 8jwong14 on 2011-02-10
Now I jsut need to find the audio in cable and an adapter for 1/4 inch to 1/8 inch.  I'm also going to try finding the usb cable I had.

---

### Post by 8jwong14 on 2011-02-10
> **tommcd said:**
> Is the digital piano detected by Ubuntu?
When you plug in the piano via the usb port, try running **lsusb** in the terminal. It should list all usb devices connected to the computer, including the piano.
To record music you could use **audacity**. It is in the Ubuntu repos. [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
Here are some great video tutorials on digital music making in linux: [http://filmsbykris.com/](http://filmsbykris.com/)
See the videos under "*Music Editing/Creation*".
You may also be interested in ubuntu Studio: [http://ubuntustudio.org/](http://ubuntustudio.org/)
Would you mind jsut telling me how to record using audacity and a usb connection?

---

### Post by 8jwong14 on 2011-02-10
> **IceRoadTrucker said:**
> Ok, if I were you, I'd be doing the following:

1. Being happy that I discovered Linux and have a keyboard
2. Trying it out ASAP using a simple 1/8" cord going to your computer's *stereo line in*, just for instant gratification
2. Downloading something like Puredyne or Ubuntu Studio and installing it on another partition
3. Trying "JACK Control" within Puredyne or Ubuntu Studio (read: toying with it until you finally find right settings several months later) to see if it is recognized as a readable MIDI-client 
4. Using it to control Fluid Synth/Qsynth in realtime
5. Downloading new .sf2 Soundfonts all the time to use in Fluid/Qsynth
6. Recording both in Rosegarden (MIDI) and in Ardour (Audio) through Jack Audio.

Or rather, if you lent me your keyboard right now, that's what I'd be doing with it...I already have a virtual keyboard, to do this with, "VMPK."
I don't want to record using midi and I want to do it within Ubuntu 10.04.

---

### Post by tommcd on 2011-02-10
> **8jwong14 said:**
> Would you mind jsut telling me how to record using audacity and a usb connection?
Sorry, but I have no direct experience with Audacity. It should work for what you want to do though from what I have read about it.
Ubuntu Studio is probably what you want though if you plan to make music with linux / Ubuntu.

---

### Post by 8jwong14 on 2011-02-13
> **tommcd said:**
> Sorry, but I have no direct experience with Audacity. It should work for what you want to do though from what I have read about it.
Ubuntu Studio is probably what you want though if you plan to make music with linux / Ubuntu.
I'll install it on my laptop then so I can move it to the piano.  Thanksf or your help.

---

