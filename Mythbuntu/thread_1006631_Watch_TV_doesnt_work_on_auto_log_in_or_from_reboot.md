---
title: "Watch TV doesnt work on auto log in or from reboot"
date: 2008-12-09
forum: Mythbuntu
---

### Post by xyzacct on 2008-12-09
The frontend comes up fine but when I click on watch tv nothing happens. I have to exit, run the back end configurator, exit out of that, have the mythfilldatabase run, restart the frontend and then it works. What's going on?

---

### Post by xyzacct on 2008-12-09
Ok, so it doesn't start either from auto login or regular log in. I tried running mythfilldatabase and it still doesn't work. I tried running /etc/init.d/mythtv-backend start then open the frontend and select watch tv, still doesn't work. I have to start the backend configuration, close it, open the frontend and then it'll work. What am I missing here?

---

### Post by EasyRiderOnTheStorm on 2008-12-10
You might want to check your logs for clues. Try 

/var/log/mythtv/mythfrontend.log
/var/log/mythtv/mythbackend.log

When you say nothing happens when you click on LiveTV, is it nothing-nothing, or does it just go to a black screen? The latter happens a lot if your tuner has difficulties locking on the channel, mythfrontend just times out.

---

### Post by volkswagner on 2008-12-10
What type of tuner is it?

Is this a master backend with a frontend or a slave?

After a fresh reboot, while in the frontend check the status of your tuner.  Go to >Information Center>Machine Status> and scroll to tuner status.

Sometimes the easiest fix is to go into the backend setup, delete the tuner and add it back.

I this problem on a slave machine.  Setting a static IP address cured the problem for me.

---

### Post by xyzacct on 2008-12-10
It's a backend/frontend machine. The tuner is the HDHomerun. I don't know how to read those stinkin logs. :D I'll do a reboot and post the info before I start dinkin' around though.

Oh, when I say nothing happens I mean, I click on "watch tv" and the screen flicks but doesn't actually go to the watch tv portion, it just stays at the initial menu. Make sense?

Here's the frontend log
```
Starting mythfrontend.real..
2008-12-10 17:31:20.819 New DB connection, total: 2
2008-12-10 17:31:20.819 Connected to database 'mythconverg' at host: localhost
2008-12-10 17:31:20.820 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-12-10 17:31:20.820 Enabled verbose msgs:  important general
2008-12-10 17:31:22.724 No theme dir: /home/myth/.mythtv/themes/Iulius
2008-12-10 17:31:22.724 Primary screen 0.
2008-12-10 17:31:22.725 Using screen 0, 1280x1024 at 0,0
2008-12-10 17:31:22.725 No theme dir: /home/myth/.mythtv/themes/Iulius
2008-12-10 17:31:22.725 Switching to square mode (Iulius)
2008-12-10 17:31:22.862 Using the OpenGL painter
2008-12-10 17:31:22.863 JoystickMenuClient Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-12-10 17:31:22.863 lirc_init failed for mythtv, see preceding messages
2008-12-10 17:31:23.947 Loading from: /usr/share/mythtv/themes/Iulius/base.xml
2008-12-10 17:31:23.979 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-12-10 17:31:24.019 Registering Internal as a media playback plugin.
2008-12-10 17:31:24.354 Failed to run 'cdrecord --scanbus'
2008-12-10 17:31:24.359 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-12-10 17:31:24.362 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-12-10 17:31:24.400 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-12-10 17:31:24.440 No theme dir: /home/myth/.mythtv/themes/Iulius
2008-12-10 17:31:24.487 Using NV NPOT texture extension
2008-12-10 17:33:54.319 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-12-10 17:33:54.339 Using protocol version 40
2008-12-10 17:33:56.110 Deleting UPnP client...
```

backend
```
2008-12-10 17:31:10.882 Using runtime prefix = /usr
2008-12-10 17:31:11.010 Empty LocalHostName.
2008-12-10 17:31:11.029 Using localhost value of myth
2008-12-10 17:31:11.147 New DB connection, total: 1
2008-12-10 17:31:11.218 Connected to database 'mythconverg' at host: localhost
2008-12-10 17:31:11.238 Closing DB connection named 'DBManager0'
2008-12-10 17:31:11.245 Connected to database 'mythconverg' at host: localhost
2008-12-10 17:31:11.327 New DB connection, total: 2
2008-12-10 17:31:11.333 Connected to database 'mythconverg' at host: localhost
2008-12-10 17:31:11.371 Current Schema Version: 1214
Starting up as the master server.
2008-12-10 17:31:11.462 HDHRChan(1015029f/0), Error: Unable to send discovery request
			eno: Network is unreachable (101)
2008-12-10 17:31:11.472 HDHRChan(1015029f/1), Error: Unable to send discovery request
			eno: Network is unreachable (101)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-12-10 17:31:11.520 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-12-10 17:31:11.545 Main::Registering HttpStatus Extension
2008-12-10 17:31:11.553 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-12-10 17:31:11.782 Enabled verbose msgs:  important general
2008-12-10 17:31:11.829 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-10 17:32:31.512 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-10 17:33:54.339 MainServer::HandleAnnounce Monitor
2008-12-10 17:33:54.342 adding: myth as a client (events: 0)
2008-12-10 17:33:54.344 MainServer::HandleAnnounce Monitor
2008-12-10 17:33:54.346 adding: myth as a client (events: 1)
```
So, yeah, it looks like the tuner is unavailable.

---

### Post by xyzacct on 2008-12-10
Which when I do volkswagoner's suggestion, they show unavailable. Hmmm.

---

### Post by xyzacct on 2008-12-10
Which when I do volkswagoner's suggestion, they show unavailable. Hmmm. I wonder what would cause that. All I do is kick off the back end configurator and exit out of it. That makes the tuners available?

---

### Post by EasyRiderOnTheStorm on 2008-12-11
volkswagner seems to have nailed it. It's not your tuner that isn't available, it's your PC's own network adapter. It hasn't connected to your LAN yet when mythbackend tries to jump on the tuner - by the time you restart mythbackend, your PC is connected already so it works. 

So just to be clear, what did you try? What you should do is configure your PC to have a fixed IP address, so it doesn't need to negotiate a dynamic one via DHCP when it starts up. Do not forget to exclude that particular IP from your router's DHCP pool, so it doesn't get assigned to something else as well. Is that what you tried...?

---

### Post by xyzacct on 2008-12-11
I haven't tried anything yet, I was waiting on some other suggestions as I didn't want to go the static IP route...I just switched my lan over to dhcp a little bit ago. I will give that a shot though and report back.

---

### Post by EasyRiderOnTheStorm on 2008-12-11
> **xyzacct said:**
> I haven't tried anything yet, I was waiting on some other suggestions as I didn't want to go the static IP route...I just switched my lan over to dhcp a little bit ago.

Well, there's always more than one way to skin a cat...

- You can keep DHCP (for all the other devices on your LAN) by using excluding that particular static IP that your mythbox uses from the DHCP pool; everything else can keep using DHCP.

- This hack is just a means to an end, namely to get your mythbox's network adapter up and running **before** mythbackend tries to access the tuner. Any other means of delaying mythbackend should do just as fine.

- This is sort of hilarious, but the HDHomerun manufacturer's forum discusses this exact problem, with some possible (DIY) solutions. See [[here]("http://www.silicondust.com/forum/viewtopic.php?t=5825")].

---

### Post by xyzacct on 2008-12-11
> **EasyRiderOnTheStorm said:**
> Well, there's always more than one way to skin a cat...

- You can keep DHCP (for all the other devices on your LAN) by using excluding that particular static IP that your mythbox uses from the DHCP pool; everything else can keep using DHCP.

- This hack is just a means to an end, namely to get your mythbox's network adapter up and running **before** mythbackend tries to access the tuner. Any other means of delaying mythbackend should do just as fine.

- This is sort of hilarious, but the HDHomerun manufacturer's forum discusses this exact problem, with some possible (DIY) solutions. See [[here]("http://www.silicondust.com/forum/viewtopic.php?t=5825")].
Cool, thanks for the link. I should have looked around first (shame on me) but this was my first foray into all things Ubuntu+Myth (I'm an Archlinux user :D) so I felt like I was starting from scratch. I'll peruse that link and see what I can come up with. If it's simply a matter of the backend starting before the network is active, isn't there something you can put in...init.d (in Arch it's in the rc.conf file) that forces one daemon to wait on another? That seems like it'd be the easiest fix.

---

### Post by erotomanic on 2008-12-12
I had the same problem.  Switched the network settings from roaming to DHCP and I believe that did the trick, although I'm not 100% sure yet.

---

