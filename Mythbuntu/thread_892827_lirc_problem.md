---
title: "lirc problem"
date: 2008-08-17
forum: Mythbuntu
---

### Post by stevanbt on 2008-08-17
Hi all,
I'm installing Mythbuntu 8.04.1 and am experiencing a problem with my remote control.  Box spec;-
Antec Fusion black v2 
Hauppauge Nova t 500 freeview card
2 gig memory
Abit an-m2hd motherboard
AMD x2 5000+ cpu

I have installed lirc, to check everything's working I've started lirc with (already created a link to the event in /dev/input using udev)```
sudo /usr/sbin/lircd -H dev/input -d /dev/input/irremote -n
```
all ok, in another term I've entered 
```
irw
```
When I press buttons on the remote I get output in the irw term
```
long number 00 OK NOVA-T500
```

So all seems ok so far, but when I start mythfrontend, select watch tv and press the ok button nothing happens.  However, the right arrow will activate watch tv.  I've checked lirc is working with 
```
ps -ef | grep lirc
```

I've setup a very similar system in the past and the remote works, I just can't figure out what I've done wrong.  Any help or suggestions welcome.

Thanks in advance, Steve.

---

### Post by Flecko on 2008-08-17
Let me ask some questions...

Did you select your IR receiver and remote control when you were installing Mythbuntu?

If you didn't do the above, can you goto Mythbuntu control center and select the Nova-t 500 and see if it helps?

You shouldn't have to manually install lirc after your system is set up. It works almost automatically if you have a standard IR receiver and remote.

Let me know.

---

### Post by stevanbt on 2008-08-17
Hi,
I don't remember selecting the remote during install, but I've just gone into Mythbuntu Control Centre and selected Nova T 500 and rebooted (just in case).  Things appear to be the same.

Thanks, Steve.

---

### Post by stevanbt on 2008-08-19
Hi,
I decided to re-install and selected the Nova T 500 remote when prompted.  I've started a terminal session and typed ```
irw
```, the buttons appear to be working ok:-
```
0000000000010160 00 OK NOVA-T500
0000000000010069 00 ArrowLeft NOVA-T500
000000000001006a 00 ArrowRight NOVA-T500
000000000001016b 00 PrevCh NOVA-T500

```

However, mythfrontend only responds to left, right, up, down etc.  It does not respond to OK and Back/Exit.

Any suggestions?

Thanks, Steve.

---

### Post by Neon Dusk on 2008-08-20
You could have a look at your ~/.lirc/mythtv file.

You should have a section for the ok button like :-
```

begin
    remote = NOVA-T500
    prog = mythtv
    button = OK
    config = Return
end

```

---

