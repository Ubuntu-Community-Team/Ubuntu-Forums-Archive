---
title: "What kind of MIDI cable should I buy?"
date: 2006-05-07
forum: Multimedia &amp; Video
---

### Post by slugkilla on 2006-05-07
I see a few low priced MIDI in&out to joystick port cables. Would this work well on Ubuntu? Would it be better if I got a MIDI in-out to USB cable? Thanks for any help,
-slugkilla

---

### Post by dolson on 2006-05-07
It depends on what you're plugging it into. I have a cheap one that was given to me several years ago, and it works great, but the thing is that my soundcard (Audigy2 ZS) supports the onboard MIDI port well.

If you're looking to get MIDI-to-MIDI cables and use eBay, I order Pulsar cables myself. They're cheap and work great. IIRC, the seller is pulsartech, but I could be remembering wrong, because it's been a couple years.. They may sell what you're looking for as well.

---

### Post by slugkilla on 2006-05-12
I ended up buying the Joystick port cable with the in and out plugs on the other end. I hooked it up to my keyboard (very old Yamaha PSR-195) and don't know what to do now. I think it is configured wrong in Qjackctl or something because non of the programs I have used respond to pressing the keys on the keyboard. Also the keyboard does not show any sign of *knowing* that it is connected to anything. This is my first time doing anything like this so could anyone tell me how I could find out if this keyboard is going to work on ubuntu?

---

### Post by dolson on 2006-05-12
What sound card do you have? If it has a supported MIDI port on it, then you go into QjackCtl and start JACK. Click on the Connections button. On the Connections window, go to the MIDI tab. On the left side, you will see your MIDI port listed there, as a readable client/output port. Launch your JACK-supported soft-synth, such as ZynAddSubFX. It will show up in the list on the right side. Now click on each one, then click the Connect button to virtually patch your keyboard into ZynAddSubFX. You may have to switch over to the Audio tab and click on ZynAddSubFX on the left pane, and then click on alsa_pcm on the right and connect them, to virtually patch the outputs of Zyn to the inputs of your soundcard.

---

### Post by slugkilla on 2006-05-12
I have a built in sound card. It's fairly recent hardware and it has a midi port so that should be fine(I hope). I did what you said and I have things set up with the guides on  Ubuntu studio, but the keyboard still does not make the soft-synth work. I think it could be how the sound card it setup in Qjackctl.
On my setup:
Input device: (default)
Output device: (default)
Input channels: 0
Output channels:0

Is that right?

BTW: On the MIDI tab there are both '62:Midi Through' with port-0 under it and '72:MPU-401 UART MIDI' I connected both to zyn.

Thanks so much for the help.:)

Edit: I found Nvidia nforce2 listed under the in/output device sections. I guess thats my sound card?
     I also found this in the message area of qjackctl
          unix_connect: can't connect to server (unix:/home/slugkilla/.kde/socket-ubuntu/myinternetinfo)

---

### Post by slugkilla on 2006-05-12
I have a built in sound card. It's fairly recent hardware and it has a midi port so that should be fine(I hope). I did what you said and I have things set up with the guides on  Ubuntu studio, but the keyboard still does not make the soft-synth work. I think it could be how the sound card it setup in Qjackctl.
On my setup:
Input device: (default)
Output device: (default)
Input channels: 0
Output channels:0

Is that right?

BTW: On the MIDI tab there are both '62:Midi Through' with port-0 under it and '72:MPU-401 UART MIDI' I connected both to zyn.

Thanks so much for the help.:) 

also found this is the message section
unix_connect: can't connect to server (unix:/home/slugkilla/.kde/socket-ubuntu/myinternetinfo)

---

### Post by dolson on 2006-05-13
Can you take a screenshot of your JACK connections?

Can you try this and confirm it works at least? [http://ubuntustudio.com/wiki/index.php/QjackCtl_Connections](http://ubuntustudio.com/wiki/index.php/QjackCtl_Connections)

---

### Post by slugkilla on 2006-05-13
Ok I took 3 pics of it and I can take more if you need me to.

Connections audio tab:
[http://img111.imageshack.us/my.php?image=audiotab0ez.png](http://img111.imageshack.us/my.php?image=audiotab0ez.png)

Connections MIDI tab:
[http://img102.imageshack.us/my.php?image=miditab6zd.png](http://img102.imageshack.us/my.php?image=miditab6zd.png)

And my setup:
[http://img107.imageshack.us/my.php?image=setup7cz.png](http://img107.imageshack.us/my.php?image=setup7cz.png)

Thanks for helping me with this.

---

### Post by dolson on 2006-05-13
On the MIDI tab, your soundcard MIDI port is most likely "MPU-401 UART MIDI." I don't see "NVIDIA" mentioned anywhere?

And I don't know why you have so many ALSA Input Ports... I think my card lists only two..

Two things: When you click a key in VKeybd, does that meter bar at the bottom of Zyn move? It should.

And if so, can you try connecting the output of Zyn into all of the ALSA input ports to figure out which ones go to your speakers?

---

### Post by slugkilla on 2006-05-13
The first 2 input ports are my speakers. The other ones don't do anything. The bar does move and I can hear the sounds. Both the midi output ports are connected to zyn. When I strike a key on the MIDI keyboard I works like it normally does. I'm looking at the manual again for any hint on what to do. Thanks for helping.

---

### Post by dolson on 2006-05-13
If the Vkeybd works, then if you connect the MPU-401 to Zyn, it should work as well, so long as you plugged the MIDI OUT of your keyboard to the MIDI IN of the MIDI cable. Try swapping which plug of the cable plugs into the MIDI OUT of your board.

---

### Post by slugkilla on 2006-05-13
so. Does this mean it's just not going to work? ](*,)

---

### Post by dolson on 2006-05-13
I don't know, I don't have the same sound card as you do. Maybe someone with the same device can help?

In the meantime, paste the output of these:

cat /proc/asound/seq/clients
cat /proc/asound/seq/drivers
cat /proc/asound/devices
cat /proc/asound/modules
cat /proc/asound/card0/midi*

And how come your NVIDIA stuff doesn't show in your screenshots? You said it was listed there.

---

### Post by slugkilla on 2006-05-13
cat /proc/asound/seq/clients:

Client info
  cur  clients : 7
  peak clients : 7
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 63:0, 128:0
Client  62 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  63 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
  Output pool :
    Pool size          : 1024
    Cells in use       : 0
    Peak cells in use  : 0
    Alloc success      : 0
    Alloc failures     : 0
Client  72 : "MPU-401 UART MIDI" [Kernel]
  Port   0 : "MPU-401 UART MIDI" (RWeX)
    Connecting To: 130:0
Client 128 : "Client-128" [User]
  Port   0 : "qjackctl" (-W--)
    Connected From: 0:1
  Input pool :
    Pool size          : 200
    Cells in use       : 0
    Peak cells in use  : 1
    Alloc success      : 7
    Alloc failures     : 0
Client 129 : "Virtual Keyboard" [User]
  Port   0 : "Virtual Keyboard" (R-e-)
    Connecting To: 130:0
  Output pool :
    Pool size          : 500
    Cells in use       : 0
    Peak cells in use  : 0
    Alloc success      : 0
    Alloc failures     : 0
Client 130 : "ZynAddSubFX" [User]
  Port   0 : "ZynAddSubFX" (-We-)
    Connected From: 129:0, 72:0
  Input pool :
    Pool size          : 200
    Cells in use       : 0
    Peak cells in use  : 1
    Alloc success      : 42
    Alloc failures     : 0

cat /proc/asound/seq/drivers:

snd-seq-midi,loaded,1
snd-seq-oss,loaded,0

cat /proc/asound/devices:

 18: [0- 2]: digital audio playback
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
  1:       : sequencer
 33:       : timer
 40: [1- 0]: raw midi
 32: [1- 0]: ctl

cat /proc/asound/modules:

0 snd_intel8x0
1 snd_mpu401

cat /proc/asound/card0/midi*:

cat: /proc/asound/card0/midi*: No such file or directory


-----------------
BTW: I did have the plugs reversed

---

### Post by slugkilla on 2006-05-14
this does not look good:( 

cat /proc/asound/card1/midi*:

MPU-401 UART MIDI

Output 0
  Tx bytes     : 0
Input 0
  Rx bytes     : 0

Edit: wait I forgot to start jack and make connections

 cat /proc/asound/card1/midi*:
MPU-401 UART MIDI

Output 0
  Tx bytes     : 0
Input 0
  Rx bytes     : 0
  Buffer size  : 4096
  Avail        : 0
  Overruns     : 0

---

### Post by slugkilla on 2006-05-25
Still no luck. Would it help if I got a new sound card (right now I have a built-in one)? What Is a greatly supported card I could get? Thanks for any help.

---

### Post by dolson on 2006-05-26
Try an SB Live! 5.1 or an Audigy2 or something. But I can't guarantee they will be great cards, it's just what I use, and they work fine.

---

### Post by slugkilla on 2006-05-26
Got a SABRENT SBT-SP6C 5.1 Channels PCI Interface Sound Card from newegg. I'll tell ya bout it when it gets here.

---

### Post by dolson on 2006-05-26
Well, it is not on the list of *sound cards that work in Linux*, I don't expect it to work. But the site is out of date... Perhaps if you confirm it works, you could write to them and ask them to add it?

[http://alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://alsa-project.org/alsa-doc/index.php?vendor=All#matrix)

---

### Post by slugkilla on 2006-05-26
2 reveiws reported it to work so I thought I would test it out. If it works I'll be sure to vist that site.

---

### Post by dolson on 2006-05-27
That's good news then. I wonder why ALSA's site is not being updated with this info? Hmm.

Did the reviews state that the MIDI port worked?

---

### Post by slugkilla on 2006-05-27
No it did not. But the features said this: 
High Performance Dual Game Port
MPU401 compatible MIDI interface & GM 

The chipset,CMI8738, is supported by alsa-project. I'll just have to wait for it to get here so I can test it out.

---

### Post by slugkilla on 2006-06-01
The card came today, gonna put it in this weekend and set things up. I'll get back to ya.

---

### Post by slugkilla on 2006-06-02
before I test the MIDI port, I'll try and get it setup right. My old Nvidia nforce2 the new cmi 8738 and some odd realteak thing are present in the alsa mixer. There is a number of ports on my new card. I tried them all And got to speaker to crackle when i first put it in. I just can't get music the play!! That would be ok if the midi port worked but i have not tested it yet. What do I need to do in order to get sounds coming from my new card? thanks

---

### Post by slugkilla on 2006-06-02
I have the card working. It's cool. I Started jack but when I conect the the MIDI UART to zyn, the link in not made and the message window says 
> 19:26:09.214 Patchbay deactivated.
19:26:09.305 Statistics reset.
19:26:09.474 Startup script...
19:26:09.474 artsshell -q terminate
19:26:09.521 MIDI connection graph change.
19:26:10.179 Startup script terminated with exit status=256.
19:26:10.180 JACK is starting...
19:26:10.180 /usr/bin/jackd -R -dalsa -dhw:0 -r48000 -p128 -n2 -S -H -M
19:26:10.194 JACK was started with PID=5658 (0x161a).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|hwmon|hwmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 128 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
19:26:10.447 MIDI connection change.
19:26:10.460 MIDI connection graph change.
19:26:12.464 Server configuration saved to "/home/josh/.jackdrc".
19:26:12.465 Statistics reset.
19:26:12.670 Client activated.
19:26:12.671 Audio connection change.
19:26:12.685 Audio connection graph change.
19:26:12.686 XRUN callback (1).
19:26:14.684 XRUN callback (376 skipped).
jackd watchdog: timeout - killing jackd
zombified - calling shutdown handler
19:26:15.437 Shutdown notification.
19:26:15.438 Client deactivated.
19:26:15.440 JACK was stopped successfully.
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
19:26:18.110 MIDI connection graph change.
19:26:18.133 MIDI connection graph change.
19:26:18.333 MIDI connection change.
19:26:31.178 MIDI connection graph change.
19:26:31.214 MIDI connection change.
19:26:46.928 MIDI connection change.

---

### Post by slugkilla on 2006-06-03
The title of this tread no longer applys. I'm moving to a new thread.

---

