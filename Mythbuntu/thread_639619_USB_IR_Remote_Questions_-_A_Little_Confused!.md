---
title: "USB IR Remote Questions - A Little Confused?!?"
date: 2007-12-13
forum: Mythbuntu
---

### Post by riverty on 2007-12-13
**My setup includes:**

[LIST]
[*]Mythbuntu 7.10 - fresh install off CD ISO
[*]ATI HDTV Wonder (PCI) - connected to terrestrial HD antenna
[*]Hauppauge PVR-150 (PCI) - connected directly to Time-Warner Cable
[*]NVidia 7950 GT (PCIx) - connected to 32" 720p HDTV via VGA cable
[*]Sapphire Theatrix IR Remote Control with USB IR Receiver
[/LIST]

Mythbuntu seems to work fine though I have not tested everything yet. I have successfully got both tuners to work, in both SD and HD. I have the guide downloading and database filled. I have watched TV and paused live TV fine. All seems good with the install. I should mention that I am currently dual-booting this system with Windows MCE 2005 (which I'm trying to replace with Mythbuntu) so I have a basis for ruling out faulty hardware and comparing settings and such. The machine is solid.

**My issue:**

First, I'm confused. Lirc *seems* to be what I want to work with, yet everything I have read so far, talks about homebrew or serial IR receivers only. There doesn't seem to be a working inode for /dev/lirc - /dev/lircd for it. Lircd **is** running on the machine however.

Second. The remote works *OK* in Windows MCE. I can run most basic commands from this remote for day-to-day operations fine. In Mythbuntu, only a few buttons on the remote actually work. Up, down, left, right, enter works. The number keypad works in kedit. That's about it.

If I get some buttons to work, then I know that the remote control works, and I know that the IR receiver is working, and I know that Mythbuntu *"sees"* the stuff, how do I **program it** to get the other buttons to work? What file(s) so I work with? What programs are responsible for a USB connected IR receiver?

I did some digging and found out that the remote was manufactured from a company called Jess. I found 1 thread on how someone, a while ago, hacked the source code to Lirc(d) and recompiled to get it to work. This would be beyond what I would want to try to do.

One more thing. I *do* have access to a remote from a Hauppauge WinTV-HVR 1600 setup. I **do not** have the card, only the remote. The IR receiver for this setup plugs into the card itself. It does not come with a USB IR receiver. Could / should I use this remote with my current USB IR receiver? The reason I ask this is because the support (config files and such) for this remote seems much better than the "off-brand" remote I have. Would it even work without the IR receiver that comes with the 1600 setup?

Someone please, set me straight, and thanks!

---

### Post by tohc1 on 2008-01-01
The first thing you need to do is find the device assigned to your ir reciever and confiure LIRC to use this. 

Run the following

```
dmesg |grep input 
```

This should list the input devices and which device they are assigned to. You should be able to spot your ir reciever by the description. If this doesn't work try

```
dmesg
```

but you'll have a lot of messages to wade through.

Once you know what input it is you need to edit /etc/lirc/hardware.conf 

```
sudo nano /etc/lirc/hardware.conf 
```

and change the following lines: 

	DEVICE="/dev/input/eventX" 
	DRIVER="dev/input" 
	MODULES="lirc_dev"

where X is the input number you found earlier. 
Restart lirc.
```
sudo /etc/init.d/lirc restart
```

then you can test using irw
```
irw
```

Press buttons on the remote and it should tell you the button name as defined in /etc/lircd.conf (you'll need to get this from the web, from mythbuntu, or make your own)

---

