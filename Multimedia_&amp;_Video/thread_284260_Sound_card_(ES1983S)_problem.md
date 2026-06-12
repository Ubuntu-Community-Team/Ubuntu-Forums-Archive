---
title: "Sound card (ES1983S) problem"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by spamzilla on 2006-10-25
So my ESS Technology ES1983S Maestro-3i PCI sound card is not working. I saw somewhere that this card does not have a supported driver...although the site did say not all drivers are listed or somethinmg similar. 

**What I have tried**

- [Comprehensive Sound Problem Solutions Guide v0.5c](http://ubuntuforums.org/showpost.php?p=1264969&postcount=76) - didn't get my sound working

- [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) - didn't work

- Used Automitix to install all codec's/drivers etc and still no luck. 

What I want to know is, am I fighting a lost battle trying to get my sound working, or is there something I can do?

Cheers :)

---

### Post by spamzilla on 2006-10-25
It would seem that my laptop sound card isn't configured

```
matt@matt-laptop:~$ **aplay -l**
aplay: device_list:221: no soundcards found...
```

but it knows that I have a sound card

```
matt@matt-laptop:~$ **lspci -v**
0000:00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
        Subsystem: Dell Latitude C600
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at d800 [size=256]
        Memory at f3ffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>
```

Can someone help me solve me annoying problem please? :)

---

### Post by Kateikyoushi on 2006-10-25
This is the module you have to load, then check with aplay whether it works or not.
```
modprobe snd-card-maestro3
```

---

### Post by spamzilla on 2006-10-25
I pasted that into terminal, and got the following

```

matt@matt-laptop:~$ **modprobe snd-card-maestro3**
FATAL: Module snd_card_maestro3 not found.

```

When I click on the speaker icon, I get the following message

```
No volume control GStreamer plugins and/or devices found.
```

I have installed all GStreamer plugins, so I guess I need to make my laptop "find" my sound card.

---

### Post by christhemonkey on 2006-10-25
What kernel are you running?


(to find out do this: )
```
uname -r 
```

---

### Post by spamzilla on 2006-10-25
Ubuntu Dapper Drake 2.6.15-27-386

---

### Post by christhemonkey on 2006-10-25
I think that should be:
```
sudo modprobe snd-maestro3 
```

---

### Post by spamzilla on 2006-10-25
Ok that worked. THis is the aplay output

```
matt@matt-laptop:~$ **aplay**
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
aplay: main:544: audio open error: No such device

```

---

### Post by spamzilla on 2006-10-25
Can anyone tell my why the aplay command gave me some errors, please. I want me sound back :'(

Cheers

---

### Post by spamzilla on 2006-10-26
Anyone :(

---

### Post by christhemonkey on 2006-10-26
The reason aplay gives you errors is because you have an invalid .asound file (it will be .asoundsomething) in your home directory.

Can you rename this file to something else, like .notanasoundwhatever and then try aplay

And also can you post the file that you rename as well please?

---

### Post by spamzilla on 2006-10-26
just to clarify, I fixed the problem. What i did was typed...

```
 gksudo gedit  /etc/modules.conf
```

...into terminal. I had no text in this file, so I entered this into the file and saved it.

```

alias 3c574_cs
alias usb-controller usb-uhci
alias eth0 3c574_cs
options 3c574_cs irq=11
alias sound-slot-0 maestro3
post-install sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -L >/dev/null 2>&1 || :
pre-remove sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -S >/dev/null 2>&1 || : 

```

My sound now works fine :D

---

### Post by Anjue on 2007-07-10
> **spamzilla said:**
> just to clarify, I fixed the problem. What i did was typed...

```
 gksudo gedit  /etc/modules.conf
```

...into terminal. I had no text in this file, so I entered this into the file and saved it.

```

alias 3c574_cs
alias usb-controller usb-uhci
alias eth0 3c574_cs
options 3c574_cs irq=11
alias sound-slot-0 maestro3
post-install sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -L >/dev/null 2>&1 || :
pre-remove sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -S >/dev/null 2>&1 || : 

```

My sound now works fine :D

how about the built in intel sound card?

---

