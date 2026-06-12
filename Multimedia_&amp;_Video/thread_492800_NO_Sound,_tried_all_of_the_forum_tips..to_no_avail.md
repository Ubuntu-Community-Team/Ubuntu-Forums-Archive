---
title: "NO Sound, tried all of the forum tips..to no avail"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by Kubotaz4 on 2007-07-05
Ive tried all of the self help tips and cant figure out how to get my sound to work.

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.14rc4.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc4.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc4.tar.bz2

the "sudo cp ~/downloads/asla* . brings up a prompt that says
    jay@jay-desktop:~$ cd usr/src/alsa
    bash: cd: usr/src/alsa: No such file or directory
    jay@jay-desktop:~$ cd /usr/src/alsa
    jay@jay-desktop:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
    Password:
    cp: cannot stat `/home/jay/downloads/alsa*': No such file or directory

I have the driver, lib, and util saved on the desktop

Then I went and found instructions to do this, so maybe this will help someone decide what i need and could help me out.  

jay@jay-desktop:~$ cat /proc/asound/card0/codec\#*
Codec: SigmaTel STAC9221 A1
Address: 0
Vendor Id: 0x83847680
Subsystem Id: 0x102801a7
Revision Id: 0x103201
Default PCM: rates 0x7e0, bits 0x0e, types 0x1
Default Amp-In caps: ofs=0x00, nsteps=0x0e, stepsize=0x05, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Power: 0x0
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x06 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x17
Node 0x07 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x18
Node 0x08 [Audio Output] wcaps 0x40211: Stereo Digital
  PCM: rates 0x7e0, bits 0x0e, types 0x5
Node 0x09 [Audio Input] wcaps 0x140311: Stereo Digital
  PCM: rates 0x160, bits 0x0e, types 0x5
  Connection: 1
     0x11
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP
  Pin Default 0x02214030: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0x80: HP
  Connection: 1
     0x02
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT
  Pin Default 0x01a19021: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x24: IN
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT
  Pin Default 0x01111012: [Jack] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x60: IN OUT
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP
  Pin Default 0x01114010: [Jack] Speaker at Ext Rear
    Conn = 1/8, Color = Green
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x0824: IN
  Pin Default 0x02a19020: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x20: IN
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0837: IN OUT
  Pin Default 0x01117011: [Jack] Speaker at Ext Rear
    Conn = 1/8, Color = Yellow
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x05
Node 0x10 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 3
     0x08* 0x17 0x19
Node 0x11 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN
  Pin Default 0x400000f1: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Power: 0x0
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x0e* 0x15 0x0f 0x0b 0x0c 0x0d 0x0a
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x0e 0x15* 0x0f 0x0b 0x0c 0x0d 0x0a
Node 0x14 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
  Amp-Out vals:  [0x00]
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x01813122: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
  Pin-ctls: 0x20: IN
Node 0x16 [Volume Knob Widget] wcaps 0x600000: Mono
Node 0x17 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x12
Node 0x18 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x13
Node 0x19 [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
Node 0x1a [Audio Output] wcaps 0x30201: Stereo Digital
Node 0x1b [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x400000f2: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x1a


Thanks for all of your help.

---

### Post by mig5 on 2007-07-05
Have you definately looked here? [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
That fixed my sound problems

---

### Post by sosy on 2007-07-05
> sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.14rc4.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc4.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc4.tar.bz2

the "sudo cp ~/downloads/asla* . brings up a prompt that says
**jay@jay-desktop:~$ cd usr/src/alsa**
bash: cd: usr/src/alsa: No such file or directory
jay@jay-desktop:~$ cd /usr/src/alsa
jay@jay-desktop:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
Password:
cp: cannot stat `/home/jay/downloads/alsa*': No such file or directory

i'm new to linux but AFAIK, ~ points to ur home directory. according to the bold line, bash is on ur home directory and tries to change directory to usr/src/alsa in ur home directory. but 'usr/src/alsa' is in '/'.  :idea: maybe that's the problem?

---

### Post by Kubotaz4 on 2007-07-05
Thanks for looking, but that bold was acutally a typo on my part...there wasnt a "/" in front of the usr.  the next line will clarify.  
Please keep looking and help out this guy who would like to listen to my awesome system.  Thanks!!!

---

### Post by Gremlinzzz on 2007-07-05
Did look at the controls right click sound icon choose preferences make sure pcm is highlighted and choose device track control i;m using alsa mixer but you should try all of em.then right click icon again choose open volume control then click edit tab/ preferences and check the boxs to see  some more controls to see if any are muted.

---

### Post by GFC2 on 2007-07-06
/home/jay/downloads/alsa*': No such file or directory

If the downloads are on your desktop, that's not the correct directory.  The information in the guide is not correct.   Click Places>Filesystem to open a file system browser and browse your way to the desktop.  Set the file system browser to give the filepath in the address bar text, not icons.  The address bar will  show the correct filepath.

I've read elsewhere that if you simply  enter /(directory name) the forward slash will bring up the correct filepath to the directory.  Never tried it myself.  

If you're editing commands, I've found it useful to copy all the commands to a notepad, copy/paste/edit in the notepad, then paste to the terminal.  That way if you goof you have a backup at your fingertips.

I'm stuck just a little bit ahead of you.  

cd alsa-driver-1.0.14.tar.bz2 yields:

bash: cd: alsa-driver-1.0.14.tar.bz2: Not a directory

If you find a solution to that one, please post it.

---

### Post by paulg on 2007-07-06
> **GFC2 said:**
> I've read elsewhere that if you simply  enter /(directory name) the forward slash will bring up the correct filepath to the directory.  Never tried it myself.

It's the auto completion feature in bash. As you type hit tab and it will auto complete the directory/file name. If it does not work it is not enabled. Open the file in your home directory with your favourite editor called .bashrc and uncomment (delete the '#' signs) the bit at the bottom about auto completion.

> **GFC2 said:**
> cd alsa-driver-1.0.14.tar.bz2 yields:
bash: cd: alsa-driver-1.0.14.tar.bz2: **Not a directory**

You should listen to your bash, that is not a directory ;)

It's a BZip2 file. It's been a while since I have had to handle a bz2 tar-ball so I had to go looking for an answer I found it [here]("http://ubuntuforums.org/showthread.php?t=485898&highlight=bzip2").

dreadlord_chris' post (3rd one down) has a great explanation. Based on his help/explanation in the link above here's what you need to know:

```
tar xfvj alsa-driver-1.0.14.tar.bz2
```

tells tar to extract alcsound.tar.bz2 with the options xfvj - which break down too:
**x** = Extract
**f** = file mode (use the file listed on the command line)
**v** = verbose (print a bunch of stuff to the screen)
**j** = the file is comressed, pipe thru bzip2 first

Happy compiling!

---

### Post by GFC2 on 2007-07-06
Thanks, paulg, I look forward to trying it.

---

