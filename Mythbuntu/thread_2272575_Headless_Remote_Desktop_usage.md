---
title: "Headless Remote Desktop usage"
date: 2015-04-07
forum: Mythbuntu
---

### Post by bishoptf on 2015-04-07
For the life of me I cannot figure out how to get this working, ive searched and googled but so far unable to find the answer.  I have a headless mythbuntu backend, that i want to remote to from time to time, no big deal I can use x2go since I am running linux to connect but when I do i get the normal xfce session started and not the mythbuntu-session that I see when I am logging on via the console.

I thought it wouldn't matter and for somethings it doesn't but I have noticed that for some reason the sessions are different e.g., when I wanted to go to network manager it wasn't showing me the same information that I saw when logging onto via the console.

So the question is when I connect remote how can I start the desktop session using the mythbuntu-session and not the generic xfce-session.  I've tried pointing to the same session startup script but it doesn't appear to work and starts up the generic xfce session.

Any insight would be appreciated, thanks.

---

### Post by TheFu on 2015-04-08
x2go supports limited sorts of desktops. Don't see myth listed, sorry.
[http://wiki.x2go.org/doku.php/doc:de-compat](http://wiki.x2go.org/doku.php/doc:de-compat)  has a list.  I know that openbox (no DE) works. The issues are spelled out in that link.  If myth needs openGL or any 3d-accel extensions, it may best to move to a SPICE-based remote desktop.

---

### Post by bishoptf on 2015-04-08
> **TheFu said:**
> x2go supports limited sorts of desktops. Don't see myth listed, sorry.
[http://wiki.x2go.org/doku.php/doc:de-compat](http://wiki.x2go.org/doku.php/doc:de-compat)  has a list.  I know that openbox (no DE) works. The issues are spelled out in that link.  If myth needs openGL or any 3d-accel extensions, it may best to move to a SPICE-based remote desktop.

Thanks for the reply, I guess I wasn't clear, mythbuntu just has set up a tailored xfce-session that is called by default when you log on from the console, they have that session and then their is the standard xfce4 session, what I am trying to figure out is how to call the session that I see when I log onto the console.

I can see how it is called but when I call it from the x2go session it does not start up the xfce mythbuntu-session but defaults to the standard session just trying to figure out how to start the xfce mythbuntu-session up via x2go.

---

### Post by TheFu on 2015-04-08
My mistake, I'm sure.  I don't run myth.

I'd create 2 different x2go sessions - one to call the xfce startup and the other for the mthbuntu stuff. You just need to figure out which program + options are being called. That is how I'd test this.  Session-->Session-type-->Custom ...

---

### Post by RideMan on 2015-04-18
Try an experiment: Connect a monitor to the headless machine and reboot, then try VNCing into it. Then do you get the proper desktop session? I suspect you are getting the generic desktop session instead of the mythfrontend session because with no monitor connected, there is no display attached to that system for you to see.

I'm running my MythTV box with a broken monitor hooked to the HDMI port for precisely this reason: with the monitor connected, I can remote into the box and work on the desktop; without the monitor, I can't even open a VNC session, there being no display session to connect to.

--Dave Althoff, Jr.

---

### Post by TheFu on 2015-04-18
@RideMan and others - might be helpful to install and run **xvfb** - to trick the machine that a display device is attached. Don't know if this will work in this situation, but it is commonly used on pure servers to trick them for similar needs.

---

### Post by Lester_Burnham on 2015-04-18
Hi,

You could just setup the VNC server in Mythbuntu Control Centre. Go to Services>VNC & enable it. Give it a password and you should be able to VNC into your current session.
X11vnc should you to do what you need.

Lester

---

### Post by GreatBeach on 2015-04-18
I agree with Lester, VNC works well for remote control.   However, I did not enable VNC from the default session because I do not like leaving my desktop logged in.   Rather I installed 'tightvncserver' and kicked off my desktop remotely from the command prompt.   I did not need to tweak any files either to get the default desktop for my account.

Now I can take advantage of encryption by port forwarding VNC (tcp/5901) over ssh.   This will let me also NAT my connection to the outside if I want to get on, etc...

---

### Post by TheFu on 2015-04-19
If you like VNC, you'll LOVE x2go.

---

