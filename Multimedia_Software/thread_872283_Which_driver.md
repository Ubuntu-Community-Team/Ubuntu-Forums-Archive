---
title: "Which driver"
date: 2008-07-27
forum: Multimedia Software
---

### Post by FLCL on 2008-07-27
How do i figure out the specific sound driver i need for my card?
I have this information 
"*-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0"

Is that second line it? or what? Please help.

---

### Post by Vakman on 2008-07-27
Do you currently not have any sound? If not, find out if sound works in root. If it does then in the terminal:
```
adduser <username> audio
```
Put your user name in for the username. Don't do this if the sound does not work in root.

---

### Post by FLCL on 2008-07-27
I have no sound at all. Even got an icon of the speaker with an x. these are some erros i recieve:

[IMG]http://imagedash.com/images/jdv1217187097x.png[/IMG]

[IMG]http://imagedash.com/images/arx1217140254z.png[/IMG]

This is the icon shown:
[IMG]http://imagedash.com/images/opt1217140116i.png[/IMG]

---

### Post by Vakman on 2008-07-27
Okay. Have you tried logging in as root just to see if you have sound there?

---

### Post by FLCL on 2008-07-27
Yeah, no audio under root either.

It is the correct driver the via82xx, and i have located it on my system, but i still got nothing. 
I've been trying to compile using the alsa project way, and i get to this line:

"sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<via82xx> --with-oss=yes"
but it tells me this:

"bash: via82xx: No such file or directory" 

Help

---

### Post by FLCL on 2008-07-27
bump

---

### Post by cariboo on 2008-07-27
You should check to see if the module is installed, To do this in a terminal type:

```
lsmod | grep snd_via82xx
```

If you get a result back that includes your sound driver then the module is installed. If you get no result but the command line tyoe:

```
sudo modprobe snd_via82xx
```

This will install the module and you should have sound

---

### Post by FLCL on 2008-07-28
Ugh..thanks but it didnt work. Failed to install this is the result i got:

"FATAL: Module snd_via82xx not found.
FATAL: Error running install command for snd_via82xx"

Anyone know whats going on?
My mother board is an Asus A7V400-MX
the information print out i recieve in terminal for my sound card is:

"*-multimedia UNCLAIMED
description: Multimedia audio controller
product: VT8233/A/8235/8237 AC97 Audio Controller
vendor: VIA Technologies, Inc.
physical id: 11.5
bus info: pci@0000:00:11.5
version: 50
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0" 

The fact that that showed up means that it detects my card doesnt it? Ugh..im never going to install virtual box again..Please tell me if you need anymore information. I was certain that thats the driver i needed but i could be wrong.
Does anyone know which driver i need? or a way of finding out? PLEASE help!

---

### Post by FLCL on 2008-07-28
bump

---

### Post by cariboo on 2008-07-28
Sorry but it seems I had a typo that should have been:

```
sudo modprobe snd-via82xx
```

Hope this solves your problem:

If the module is installed already you may want to try:

```
asoundconf list
```

to see if your sound card is listed. If it is then:

```
asoundconf set-default-card <yoursound>
```

where <yoursound> is the sound card liste in the middle directive.

Jim

---

### Post by FLCL on 2008-07-28
The first one returns the same error.
> FATAL: Module snd_via82xx not found.
FATAL: Error running install command for snd_via82xx


The second one doesnt list anything unless i use sudo with it, and then i get the following:
> Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Why is this?

---

### Post by FLCL on 2008-07-28
Bump... :/

---

