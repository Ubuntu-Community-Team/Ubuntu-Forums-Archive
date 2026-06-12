---
title: "Access login screen remotely"
date: 2010-07-17
forum: Mythbuntu
---

### Post by lnoland on 2010-07-17
My system:
Mythbuntu 9.10
mythtv-common:
  Installed: 0.22.0+fixes23893-0ubuntu0+mythbuntu3
  Candidate: 0.22.0+fixes23893-0ubuntu0+mythbuntu3
  Version table:
 *** 0.22.0+fixes23893-0ubuntu0+mythbuntu3 0
        500 [http://us.autobuilds.mythbuntu.org](http://us.autobuilds.mythbuntu.org) karmic/main Packages
        100 /var/lib/dpkg/status
     0.22.0+fixes22594-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages

This box is a combination frontend/secondary backend system which is part of my home theater system so I do not normally have a keyboard/mouse attached to it (or at least they are not conveniently accessible).  I use automatic login and control mythtv from my laptop over the network using VNC.  The problem is, if my system reboots, such as following a power outage, it generally does not automatically login -- it brings up the login screen.  Since VNC only works once there is an XServer session, I generally have to go to the machine, plug in a keyboard and login, which gets annoying (there is no place to set the keyboard so I have to hold it as I type in my password, I frequently make mistakes typing that way, etc.).  I can't figure out why the automatic login fails following the reboot (though I have found that if I login remotely via ssh and issue the reboot command, about one time in six it will auto-login, but that's a pain as well).

I was thinking that surely there is some way for me to connect to the login screen via ssh so that I can enter the password from my laptop, but so far I haven't found any way to do so.  Via X11 forwarding I can start an XServer remotely tied to the display on my laptop but that is no help.  I have heard that I can use X11 forwarding to connect to the main XServer (screen :0) once it is running (though so far I haven't found instructions on how to do that) but, though I don't know how that login screen is generated, I'm guessing it is not via the XServer since, if it was already started, I would think that I could access it via VNC.

So, does anyone know how I could remotely access the login screen so I could enter my password without having to use a directly attached keyboard?

Thanks for any assistance you can offer.

 - Les

---

### Post by pu15e on 2010-07-18
Certainly :-)

Just SSH to the machine using:

```

ssh -t -L 5900:localhost:5900 myth@jenner 'x11vnc -localhost -xkb -display :0'

```

...(where jenner is the name of one of our frontends and myth is the user on that machine - replace as appropriate).

Leave that terminal window running. Then, just VNC to localhost.

Cheers,
 Mattt.

---

### Post by lnoland on 2010-07-19
> **pu15e said:**
> Certainly :-)

Just SSH to the machine using:

```

ssh -t -L 5900:localhost:5900 myth@jenner 'x11vnc -localhost -xkb -display :0'

```

...(where jenner is the name of one of our frontends and myth is the user on that machine - replace as appropriate).

Leave that terminal window running. Then, just VNC to localhost.

Cheers,
 Mattt.

Thanks for the info.  So, if I am reading this right, you are suggesting that my inability to access the login screen via VNC isn't because the XServer isn't running but rather because the VNC server (x11vnc) isn't running.  Is that correct?

What happens if I disconnect my ssh session -- does x11vnc continue to run so that the next time I connect with the vnc client it will just connect without having to do all of the setup?

Thanks again.  I don't know when I will be able to try out your suggestion -- I can't really reproduce the problem at will (though I suppose if I just pull the power on the machine, there's a pretty good chance of it happening).

-- Les

---

### Post by pu15e on 2010-07-19
Correct - the X server *is* running if the machine is throwing a G/KDM login screen. It's the VNC service that isn't running, as you say.

The SSH command I showed you will only run VNC in it's own session, so it'll wink out of existence the moment you close the SSH session - disconnecting you immediately in the process if you're VNC'ed to the host at the time.

Of course, the real solution you're looking for is to simply have the VNC service start with X before anyone's logged in (and I'm not sure offa the top of my head how one'd go about that, but it certainly wouldn't be difficult). What I like about the SSH way, though, is that it's not dependant on whether the remote host has a running VNC service or not - only that x11vnc (in this instance) is installed.

Cheers,
 Mattt.

---

