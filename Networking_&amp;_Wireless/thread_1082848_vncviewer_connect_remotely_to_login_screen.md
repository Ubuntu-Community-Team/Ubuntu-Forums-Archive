---
title: "vncviewer connect remotely to login screen"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by Claus7 on 2009-02-28
Hello,

I want to run vncviewer in order to access an ubuntu pc(pc2) from my home pc(pc1).

From pc1 I type vncviewer user_name@ip_of_pc2 and connect normally.

Today, I wanted remotely to restart pc2 from pc1 so I typed:
sudo shutdown -r now

Now after rebooting, If I connect via ssh to pc2, everything is nice and normal. If I try to connect via vncviewer though the following message appears:
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

How can I connect to my login screen, give my user name and password and be able to see the Desktop of pc2 remotely?

Thank you,
Regards!

---

### Post by Claus7 on 2009-02-28
Hello,

it took me an hour or so, yet at least I was able to do it. So here it goes:

First the story:
I had tampered with .Xauthority file, because I have found out that it might be a little bit buggy. In order to restore it back to normal, I had to log out and log in, or to restart my computer.

Because I was not able to do so interactively, I had to restart my computer remotely. So I restarted my computer via command line. 

Unfortunately, while I wanted to be able to connect to my **DESKTOP** remotely, after rebooting, in order to work, I found out that remote Desktop was not an option.

So I posted this thread, trying to find out what to do...

In order for someone to connect remotely to the **LOGIN SCREEN**, someone needs much more effort than just connecting remotely to a Desktop. That is because of security reasons.

For clarity I will use the [COLOR="Red"]pc1[/COLOR] notation, which will refer to my [COLOR="#ff0000"]home pc[/COLOR] (the one I'm standing and want to establish a remote connection to another pc) and [COLOR="Green"]pc2[/COLOR], for the computer which I want to connect and is [COLOR="#008000"]far away[/COLOR].

After the rebooting of pc2, I was able to access it via ssh from pc1. So I connected to pc2 with the following command:
```
ssh -L 5900:localhost:5900 <your-name>@<your-computer>
```
Connecting to pc2 I typed in that pc the command:
```
sudo apt-get install x11vnc
```
and gave my root password of pc2.

That way I was able to install x11vnc to pc2.
Then I typed (still in pc2):
```
sudo x11vnc -safer -localhost -nopw -once -auth /var/lib/gdm/:0.Xauth -display :0
```

A lot of data appeared at the screen and in the end the cursor was blinking in an empty line. The process is ok and someone should not do anything more in that terminal (don't close it). **That way**, I inform pc2, that a remote connection to the login screen of that pc is going to take place remotely.

Then I opened another terminal from pc1 and typed:
ssh -f -L 5900:localhost:5900  <your-name>@<your-computer> x11vnc -safer -localhost -nopw -once -display :0 && sleep 5 && vncviewer localhost:0

and I was able to see the login screen of pc2. I gave in that screen my username and passwd and the connection closed. The login succeeded, because afterwords I opened a new terminal from pc1, typed vncviewer host, and I was able to see the Desktop of pc2.

Helpful links:
[http://ubuntuforums.org/showthread.php?t=719085](http://ubuntuforums.org/showthread.php?t=719085) ->found the link to:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
[http://tombuntu.com/index.php/2007/06/27/remote-access-from-windows-x11vnc/](http://tombuntu.com/index.php/2007/06/27/remote-access-from-windows-x11vnc/)  ->how to install x11nvc

Regards!

---

### Post by krunge on 2009-02-28
> **Claus7 said:**
> 
Then I opened another terminal from pc1 and typed:
ssh -f -L 5900:localhost:5900  <your-name>@<your-computer> x11vnc -safer -localhost -nopw -once -display :0 && sleep 5 && vncviewer localhost:0

N.B.: depending on your vncviewer (you don't say which one you used) you might want to run something like 
```
vncviewer -encodings 'tight zrle copyrect' localhost:0
```
otherwise raw encoding is assumed for localhost and that will be very slow over a network.  I believe the -endocings is needed for the current xtightvncviewer.  For realvnc viewer the newer ones appear to autodetect the network rate and choose the encoding automatically.
> 
and I was able to see the login screen of pc2. I gave in that screen my username and passwd and the connection closed. The login succeeded, because afterwords I opened a new terminal from pc1, typed vncviewer host, and I was able to see the Desktop of pc2.

It may be possible to avoid the 2nd connection by configuring the display manager (gdm in your case) as described here:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

in the section labelled 'Continously'.  You basically did the 'One Time Only' section's method.

---

### Post by Claus7 on 2009-02-28
Hello,

> **krunge said:**
> N.B.: depending on your vncviewer (you don't say which one you used) you might want to run something like ...

Nope! I think that I'm telling which version I use:
VNC viewer version 3.3.7
You can find out by reading my first post. If there is something more about the version of vncviewer that I'm miss, I will be glad to find out how I'll be able to provide such information.

> **krunge said:**
> 
```
vncviewer -encodings 'tight zrle copyrect' localhost:0
```
otherwise raw encoding is assumed for localhost and that will be very slow over a network.  I believe the -endocings is needed for the current xtightvncviewer.  For realvnc viewer the newer ones appear to autodetect the network rate and choose the encoding automatically.
I think that my situation is the "smart" one, so I do not face any problem. I think that this information is valuable for the other versions you mention.

> **krunge said:**
> 
It may be possible to avoid the 2nd connection by configuring the display manager (gdm in your case) as described here:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

in the section labelled 'Continously'.  You basically did the 'One Time Only' section's method.

The fact that I was able to connect, was more that a relief to me. I had to travel back and forth more than one hour in order to login. It took me an hour to find out what I had to do, yet next time will take only a second!
Nice this note though, as I didn't give it so much attention. It was not a problem to open a terminal and type the command in order to connect to my Desktop.

Nice that this thread seem to interest people, even if there are information spread around the net.
Hope that it cleared some things.
Regards!

---

### Post by krunge on 2009-02-28
> **Claus7 said:**
> 
Nope! I think that I'm telling which version I use:
VNC viewer version 3.3.7

Yes, you are right.  Apologies I missed this detail in your first post.

I believe that version was the first one that supported the speed autodetection.

But the current xtightvncviewer still doesn't I believe, so perhaps my -encodings tip will help someone using it in this mode.

---

