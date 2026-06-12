---
title: "Logitech USB Headset no mic / sound too quiet"
date: 2008-09-23
forum: Multimedia Software
---

### Post by marcster1973 on 2008-09-23
hello ubuntu-community :-)

I'd like to use my USB Headset with Skype but but the Sound is way too quiet. The Mic doesnt work at all. 

The Card is recognized by Kubuntu and I see it in KMix. 
```

marcster@DPC:/$ lsusb
....
Bus 001 Device 003: ID 046d:0a01 Logitech, Inc. Logitech USB Headset
----

marcster@DPC:/$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf8ff0000 irq 19
 1 [CX8811         ]: CX88x - Conexant CX8811
                      Conexant CX8811 at 0xf9000000
 2 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:02.0-3, full speed
```

Nothing is muted in alsamixer and Volume Controls are > 80 % in alsamixer and and Kmix. Kmix-Capture is also set at 100 %. But when i set Skype to use Logitech USB Headset Mic / Speakers all i get is the above.

Any help is greatly appreciated. 

Kind regards.

Marcster

---

### Post by marcster1973 on 2008-09-25
Just to keep the Thread alive.

Please any help?

TIA

---

### Post by gunthergloop on 2008-09-25
Have you selected the right device in the Alsa mixer?

ie. in AM, select File -> Change Device, then from there select the device you are using for your mic and adjust that volume.

Hope that helps (?)

---

### Post by marcster1973 on 2008-09-25
Hm I already did alsamixer -c 2 and set mic and speaker on the headset to 100 % ... same problem...

any other ideas?

---

### Post by gunthergloop on 2008-09-25
I'm a newbie to be honest. I get lost without my hand held in terminal, etc.
but I was having the same/ similar problem. I thought I upped the volume in the mic, but it turned out to be the mic port in the main soundcard I was upping. 

I know you're likely waay past what I'm talking about, but for the record, here's what I did...

Rightclick on volume, -> Open Volume Control 
Then from there -> File -> Change Device
I selected the device and changed settings there.



Other than that -I'll shut up now.
I hope someone else has some sensible things to say on it though.  ;)

---

### Post by markbuntu on 2008-09-25
OK, you can try my guide. It starts with the very basic basics and goes on and on and gets more and more and more involved until at the end, if you read all the links, you are a Ubuntu sound expert. But you do not have to go that far.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by erikthedrink on 2009-09-08
You can try this.  Might workIn Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 2[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:(
Note, if you unplug your usb headset, your laptop speakers will take over.  In order to re-establish contact with the usb headset, you will need to (plug it back in) restart the system.

---

### Post by rockdj on 2009-11-05
Maybe check out my other post here: [http://swiss.ubuntuforums.org/showpost.php?p=8252657&postcount=2](http://swiss.ubuntuforums.org/showpost.php?p=8252657&postcount=2)

Might solve your problem as my issue was definitely related to my USB headset and not having the right (or the best) Profile assigned to it.

---

