---
title: "Limit access to x11vnc server"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by Bill Tetzeli on 2013-07-02
Hey all,

I have x11vnc configured to start on boot and am trying to figure out how to minimize the chances of someone hacking into it.  AFAIK the only barrier to access is the password.  What I'd like to do is either limit the number of password attempts, then either shut down the server or reject the attacker permanently, or better yet only allow one host to connect.  Here's my x11vnc.config file if anyone's interested:

start on login-session-start
script
/usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -norepeat -noxdamage -rfbauth ~/.vnc/passwd -shared -forever -bg -rfbport 5900 -o /var/log/x11vnc.log
end script

I also tried using the "-allow" option but all that got me was the server closing on me.  I'm pretty sure I set the values correctly.  Any idea how I can work this out?  I really miss Team Viewer's "whitelist", so much simpler.  Unfortunately, not an option before login.

In the meantime I've changed my 8 character password to a 30 character password.  Still, if I can tighten the security up further it can't hurt.  And I do tunnel through SSH via Remmina, though that only affects my session and not someone else trying to set up a separate connection.

---

### Post by steeldriver on 2013-07-02
Since you're tunneling over SSH anyway, invoke it with *-localhost* and/or firewall port 5900

---

### Post by Bill Tetzeli on 2013-07-02
> **steeldriver said:**
> Since you're tunneling over SSH anyway, invoke it with *-localhost* and/or firewall port 5900
All right, so how would I do that in Remmina?  When I say "tunneling via SSH", I mean I'm just clicking the appropriate boxes under the SSH tab of my VNC connection profile; I'm not doing it via terminal commands.  I assume that if I invoked -localhost in the startup script that I could then create an SSH connection using Remmina, then in the terminal screen that pops up - do what?  I'm afraid I'm rather hapless when it comes to doing VNC via command line.

---

### Post by steeldriver on 2013-07-02
I don't think you need to do anything different from what you're already doing at the client (Remmina) end of things - it's just that adding the '-localhost' switch to the x11vnc server command tells it not to accept connections except on the localhost ('lo') interface (which is where the tunnel you set up from Remmina will appear to come from). So any attempts to connect to the x11vnc server on the server's external port 5900 will be rejected (in fact, external probes won't even see that anything is listening on 5900). You can set up your firewall to drop incoming 5900 on the server as well if you want 'belt and braces' security.

At that point, your VNC is as secure as your SSH is I think - you can install fail2ban to limit brute force attacks on *that* if you want to

DISCLAIMER: I am *not* a security expert, just what I've learned from reading around and trying things

---

### Post by Bill Tetzeli on 2013-07-02
Okay, I know I'm being thick as ten posts here, but so far no joy.  I've added "-localhost" to the startup script, so now I have

[COLOR=#000000]start on login-session-start[/COLOR]
[COLOR=#000000]script[/COLOR]
[COLOR=#000000]/usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -localhost -noxfixes -norepeat -noxdamage -rfbauth ~/.vnc/passwd -shared -forever -bg -rfbport 5900 -o /var/log/x11vnc.log[/COLOR]
[COLOR=#000000]end script

and then use the same VNC connection I've got set up in Remmina (it's set up as a VNC connection with SSH tunnel enabled, not as a strict SSH connection).  When I attempt the connection, I get the SSH private key password prompt, but when the password clears and Remmina tries to make the VNC connection through the SSH tunnel nothing happens.  If I click the Cancel button I get a message saying "VNC server closed connection".  This, btw, is happening within my home network - leaving aside the fact that I'll need to be able to connect to the computer when I'm outside my home network as well.

So I guess I'm stuck.  If this means I have to create a strict SSH connection instead, that's no problem, but once I make it and am at the command prompt I have no idea what to do next.  Is there some other part of the startup script that needs changing?  Do I need to change my firewall settings?  What am I missing here?[/COLOR]

---

### Post by steeldriver on 2013-07-02
OK my apologies - I just tried it with as near identical a setup as I can manage here (added '-localhost' to the x11vnc command line on my Mythbuntu box and then tried to connect via Remmina) and you're right, it does not seem to work

It's funny because I have an almost identical setup to connect to my work except using tightvncserver - that works fine - also I checked that the 'x11vnc -localhost' connects fine if I create the tunnel manually and then point Remmina at localhost:5900

I will investigate and post back - sorry for the incorrect information

---

### Post by steeldriver on 2013-07-02
OK so it looks like it *does* work if I check Remmina's "Tunnel via loopback address" (as well as "Enable SSH Tunnel") - makes sense, I don't know why that does not appear to be necessary for my remote tightvncserver

[ATTACH=CONFIG]244336[/ATTACH]

For the record, here is my full x11vnc command line - everything except for '-localhost -o "$HOME/.vnc/x11vnc.log"' is the default invocation from Mythbuntu's session.sh script

```
x11vnc -localhost -o "$HOME/.vnc/x11vnc.log" -rfbauth $PASSWORD -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb
```

You should see that x11vnc is only listening on localhost:

```
$ sudo netstat -nlpt | grep x11vnc
[sudo] password for harvtv: 
tcp        0      0 **127.0.0.1**:5900          0.0.0.0:*               LISTEN      3949/x11vnc     
tcp6       0      0 **::1**:5900                :::*                    LISTEN      3949/x11vnc     

```

---

### Post by Bill Tetzeli on 2013-07-02
Six words:

I want to have your baby.

It worked like a charm!  Without SSH tunneling, my VNC server doesn't want to know from nuthin'.  Thanks for the extra peace of mind and your hard efforts. :-)

---

