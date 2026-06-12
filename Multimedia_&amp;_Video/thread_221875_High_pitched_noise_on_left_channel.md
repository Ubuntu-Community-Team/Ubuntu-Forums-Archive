---
title: "High pitched noise on left channel"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by Aninhumer on 2006-07-24
Whenever an application uses sound, it plays fine on the right channel, but the left channel just emits an unbearable high pitched whine.

The sound settings indicate that I am using a "VIA HDA VT82xx" sound card, and lspci lists it as:
0000:04:01.0 0403: VIA Technologies, Inc. VIA High Definition Audio Controller

I wouldn't mind in the short term if there was a way to turn off the left channel (other than actually cutting off the left speaker)

---

### Post by Aninhumer on 2006-07-25
Please can someone help?

[/Shameless Bump]

---

### Post by Aninhumer on 2006-07-26
:(

---

### Post by Aninhumer on 2006-07-26
I now have a horrible feeling that my sound card may actually be broken, is there any way to test if the noise is being produced by the driver or by a broken sound card?

---

### Post by TwoWordz on 2006-10-14
I have the same audio chipset and I also have noise on the left channel.

Did you figure out how to solve the problem?

tW

---

### Post by TwoWordz on 2006-10-15
I am pretty sure it is a bug. I filled a bug report [#66252]("https://launchpad.net/distros/ubuntu/+bug/66252").

I'll tell you if I find anything.

TW

---

### Post by Vismund Cygnus on 2006-10-28
I have the same problem, but what's really annoying is that the problem started suddenly yesterday. I've Windows XP too in my computer and it hasn't the problem. Any ideas?

PD: Excuse my English, please :D

---

### Post by Vismund Cygnus on 2006-10-28
OK, there's the solution I've found:

set "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base"

Here's the reference: [Audio Left Channel Problem]("http://forums.nvidia.com/lofiversion/index.php?t18109.html")

---

### Post by charonn0 on 2007-03-08
Just thought I'd post to say that the above solution worked perfectly on my Asus P5L-MX running Ubuntu 6.10

---

### Post by c1tlr340 on 2007-11-04
This solution also worked for me. Ubuntu 7.10, Toshiba Equium L40-10X. This was driving me nuts.:):)

---

### Post by MaGuSware™ on 2007-11-23
I wish i could say the same, im running 7.10 on the same laptop, it dosnt work for me though 
:( is it possible i did something wrong :S

i type the command in terminal and nothing happens :S jsut creats a new line :S

help anyone?

---

### Post by MaGuSware™ on 2007-11-23
Ok, i fixed it now! i had to login as root and physically add the line to the file :( took a bit of messign though as im nub but its fixed!!! w000t!

---

### Post by ekstee on 2007-12-13
yes. this is great. my sound is working great now.

to edit in ubuntu 7.10, open applications > accessories> terminal 

then type the following:  legend: // comment
//in order to switch to root, type
sudo -s -H
//then you navigate to the specific folder using the root read and write command:
sudo nano /etc/modprobe.d/alsa-base
//through the terminal, add at the bottom:
options snd-hda-intel position_fix=1 model=3stack
//then hit ctr+o to save

then restart ubuntu and it's good to go.

---

### Post by phannigan on 2008-04-07
> **Vismund Cygnus said:**
> OK, there's the solution I've found:

set "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base"

Here's the reference: [Audio Left Channel Problem]("http://forums.nvidia.com/lofiversion/index.php?t18109.html")

I am having this problem as well. Can you tell me how to enter the command from "terminal"?
Thanks
Paul

---

### Post by quackquack on 2008-06-12
click Applications, then under Accessories, Click Terminal

in the Terminal window, type :

sudo gedit /etc/modprobe.d/alsa-base

then type your password when asked. A text editor will open with the alsa-base file open. 

simply add this line:

options snd-hda-intel position_fix=1 model=3stack

to the bottom of the file and press save. When its saved, restart your computer and sound should work :)

this worked for me too, btw :D

---

