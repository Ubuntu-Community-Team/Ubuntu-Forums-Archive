---
title: "Turning on Video Remotely"
date: 2011-08-24
forum: Multimedia Software
---

### Post by johnlee on 2011-08-24
Hey, not sure if this is a trivial question or not.

I want to VNC into a computer which is turned on, but has the laptop lid closed so the screen is off- I can ssh into it, so I know it is on.

Anyone have a clue how to fire up the video through terminal?

---

### Post by MG&amp;TL on 2011-08-24
If you make the laptop 'do' a command via SSH, does it wake the screen up? (i.e. run something that doesn't do anything, but makes a process)

Edit, oops, missed the VNC bit, so I don't actually know what I'm talking about. But if I'm on the right track, tell me.

---

### Post by SeijiSensei on 2011-08-25
Rather than using VNC you can just use ssh natively to run commands at the prompt.  If you need GUI applications, try connecting with "ssh -X hostname".  Then you can run graphical applications on the remote and have them display on the local desktop as if they were running locally.  Here's a quick test:

```

[user@local]$ ssh -X remote
[user@remote]$ xterm

```

You should now see a little "xterm" terminal window appear on your local machine.  If you replace "xterm" with other commands like "firefox", they'll behave the same way.

If you get a "permission denied" error, run the command "xhost +" before using ssh to connect to the remote.  I don't believe it's required when tunnelling X over SSH, but just in case, that's the solution.

---

