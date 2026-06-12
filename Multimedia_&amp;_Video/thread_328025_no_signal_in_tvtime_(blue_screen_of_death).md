---
title: "no signal in tvtime (blue screen of death?)"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by teepark on 2006-12-30
I have an nVidia video card with binary drivers, an ATI TVWonder Pro tuner card, and ubuntu edgy x86. When I run the command 'tvtime', I get a blue screen, with 'no signal' in top center, 'No video source' in top right, and 'Permission denied', (new line) 'Cannot open capture device /dev/video0' in the bottom left. When running 'tvtime' from the terminal I get this:
```
$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/travis/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: Permission denied
```

The owner and group of ~/.tvtime and it's contents are my username. What else could be causing this?

When I run 'sudo tvtime' I still have a blue screen with 'no signal' across the top, but no 'Permission denied, Cannot open capture device /dev/video0' message any more.

So it appears that there's two problems - the user isn't allowed to use /dev/video0, and even if he could, tvtime isn't reading a valid signal from it.

As far as I can tell, there is only one relevant line in my dmesg:
```
[17179584.784000] Linux video capture interface: v1.00
```

I have seen that other people will have ...v2.00 in that line, and a series of lines with 'bttv' immediately following that line. Am I missing a needed driver?

Here's the section in 'lspci -v':
```
05:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 03)
	Subsystem: ATI Technologies Inc ATI TV Wonder Pro
	Flags: bus master, medium devsel, latency 32, IRQ 66
	Memory at d3000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
```

I really appreciate any help that anybody might be able to give me.

---

### Post by pseudonym on 2006-12-30
What's the output of lsmod?...

---

### Post by teepark on 2006-12-30
```
$lsmod
...
video                  17540  0 
...
video_buf              27652  2 cx8800,cx88xx
...
videodev               10752  2 cx8800,cx88xx
...
```

---

### Post by teepark on 2006-12-30
New update: after rebooting (maybe it was the reboot, maybe something else), 'sudo tvtime' now plays TV! But I still get the same blue screen and error messages when executing as user.

Also, even when I do get video by running as root, I have no sound. I turned everything on and up in alsamixer, but get no sound. I suspect this is a sound card (audigy 4 pro) related problem however, because I can hear it by plugging the cord from my tv tuner directly into my speakers, just not when plugged into the sound card inputs.

---

### Post by crispy_420 on 2006-12-30
Did you turn on your audio-in in alsa mixer?

As far as running it in sudo, just change the launcher.

I be wrong but there is little chance of harm running tvtime as root.

---

### Post by quirks on 2007-04-29
I have recently had the same problem and the solution to it is quite obvious:
TVtime says you don't have the permission to access /dev/video0. If you check the file ownership and permissions, it gives you

```
# ls -l video*
lrwxrwxrwx 1 root root      6 2007-04-27 18:50 video -> video0
crw-rw---- 1 root video 81, 0 2007-04-27 18:50 video0
```

That is, only users belonging to the video group may access it; all others are not allowed to even read from it. So make sure, you are member of the video group by running this command:

```
usermod -a -G video <your username>
```

Logout of your session and login again to make the changes take effect and have fun watching TV without sudoing. :)

In my opinion there should be a seperate group within the users and groups administration applet for this.

quirks

P.S. Sorry for reviving such an old thread, but if somebody else has the same problem, he will find the solution here.

---

