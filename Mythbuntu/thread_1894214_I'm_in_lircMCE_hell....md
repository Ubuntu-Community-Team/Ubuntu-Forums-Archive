---
title: "I'm in lirc/MCE hell..."
date: 2011-12-12
forum: Mythbuntu
---

### Post by RideMan on 2011-12-12
The story so far...
I bought a cheap remote that kind of half worked as  keyboard, also featured switchable button modes and in general had a lot of usability issues.
Finally, I got a SIIG Vista MCE remote which is much more usable. Or at least would  be if I could make it work. I was able to get a few basic functions to work. I figured that was a good start.

1) I added a udev rule to force the IR receiver to always map to /dev/input/irremote. 
Result: Works!

2) Using irw, determined that I was getting keystrokes instead of remote events. Did lots of reading and ultimately added a rule to /usr/share/X11/xorg.conf.d/11-evdev-quirks.conf so that the remote receiver would not be seen as a keyboard. 
Result: Well, the remote isn't showing up as a keyboard anymore...

But it isn't working, either.

First, to double check mythfrontend...
Many forum posts suggested changing the IR port from /dev/lircd to /var/run/lirc/lircd. Worthless advice...on my system, /dev/lircd is a link to /var/run/lirc/lircd. And mythfrontend seems to be happy either way...

LIRC: Successfully initialized '/var/run/lirc/lircd' using 'home/tv/.mythtv/lircrc' config

A look at ~/.mythtv/lircrc shows the expected key bindings. For example, KEY_DOWN is mapped to Down.

Over in /etc/lirc/hardware.conf things seem to be configured correctly as well...

REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/input/irremote"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
START_LIRCD="true"
LOAD_MODULES="false"
LIRCMD_CONF=""

(irrelevant cruft omitted)

Now, everything seems to be happy. But MythTV does not respond at all to IR events. Meanwhile, if I run irw, I can see IR events being generated when I hit remote buttons. Some of the codes returned are not the ones I want, but they are codes that MythTV should be able to interpret (KEY_DOWN for example).

So I have two, related problems.

First, how come MythTV doesn't seem to be getting my IR commands?

Second, there are buttons on my remote that return no codes in irw, but that are specifically enumerated in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb. How do I know that file is even being referenced? Or do I need to move it? I also ran irrecord and created a new remote codes file for my remote, and added that to the end of lircd.conf.mceusb. I noticed that the codes I got from irrecord were very different from the existing codes in that file. Annoyingly, some (but not all) of the keys that did not return events in irw also did not generate new codes in irrecord. 

I've been fooling with this thing all evening and have to go to work in the morning. I figured it was time to stop hunting through discussion threads from 2008 and start another one myself.

So can anybody help? 

Thanks!

--Dave Althoff, Jr.

---

### Post by nickrout on 2011-12-12
does your frontend log show anything helpful?

---

### Post by RideMan on 2011-12-12
Ah, the problem of posting from my iPad...presumably you missed that line:

```
LIRC: Successfully initialized '/var/run/lirc/lircd' using 'home/tv/.mythtv/lircrc' config
```

Let me look again just to be sure...looking only at the last boot yesterday, after I stopped fiddling with it...here are some excerpts from the frontend log starting with the last startup.  Note that this is incomplete; I'm trying to leave out the irrelevant cruft.  I could include that, but I think it's easier on anybody trying to assist if I can limit the log to the relevant bits.  Let me know if I am wrong about that.  

```

# Including front-end stuff so you know about my configuration...

Starting mythfrontend.real..
2011-12-12 00:32:43.678 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
2011-12-12 00:32:43.678 Using runtime prefix = /usr
2011-12-12 00:32:43.678 Using configuration directory = /home/tv/.mythtv
2011-12-12 00:32:43.678 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-12-12 00:32:44.622 Empty LocalHostName.
2011-12-12 00:32:44.622 Using localhost value of Farnsworth

# ...seemed like an appropriate hostname to me 
# (see http://en.wikipedia.org/wiki/Philo_Farnsworth)

2011-12-12 00:32:44.622 Testing network connectivity to '192.168.2.21'
2011-12-12 00:32:44.733 New DB connection, total: 1
2011-12-12 00:32:44.796 Connected to database 'mythconverg' at host: 192.168.2.21
2011-12-12 00:32:44.798 Closing DB connection named 'DBManager0'
2011-12-12 00:32:44.860 Connected to database 'mythconverg' at host: 192.168.2.21

# Combined frontend/backend system, and that part is working nicely.

2011-12-12 00:32:45.024 ScreenSaverX11Private: XScreenSaver support enabled
2011-12-12 00:32:45.024 DPMS is disabled.

# DPMS is a pain in the neck so it is shut off.  XScreenSaver support enabled, but
# the screen saver is shut off in X settings.

2011-12-12 00:32:45.044 Enabled verbose msgs:  important general

# What follows is the only mention of LIRC in the frontend log:

2011-12-12 00:32:45.076 LIRC: Successfully initialized '/var/run/lirc/lircd' using '/home/tv/.mythtv/lircrc' config
2011-12-12 00:32:45.076 JoystickMenuThread: Joystick disabled - Failed to read /home/tv/.mythtv/joystickmenurc

# Deleted stuff about the NVIDIA and OpenGL support
# Deleted stuff about the DB connection, which is fine
# Deleted warnings about theme files that I'm not using anyway
# Deleted stuff about frontend modules and plugins, and localizations for same
# Deleted stuff about remote control connections and menu themes
# Deleted stuff about what went on while I was watching a TV show later
# No mentions of anything IR, LIRC or control related.

```

Helpful?  

--Dave Althoff, Jr.

---

### Post by RideMan on 2011-12-13
Okay, now it is getting weirder.  I'm thinking I know exactly what is going on, but I don't know how to fix it...

I've edited my /usr/share/lirc/remotes/mceusb/lirc.conf.mceusb file so that it ONLY contains the key codes for my Vista MCE remote.  Those codes are in the wrong format for the current version of MythTV, but for the moment that's fine.  I rebooted the system, then I ran irw only to find that...the "new" commands are being generated.

Okay.  Where the heck are those codes coming from?  Obviously the system is not using the remote configuration in /usr/share/lirc/remotes/mceusb/lirc.conf.mceusb.  So what remote configuration IS it using?  And how do I change it?  I'm becoming more and more certain that the problem is that lirc isn't using the configuration I want it to use; heck, for all I know I might not even be using the right instance of lirc!  

So how do I figure out what is really going on here?  The logs aren't very enlightening; where do I go next?

(I went through something similar in getting mysql running on my OS-X machine).

---

### Post by RideMan on 2011-12-14
One more update before I go to bed...

I've figured out how to get MythTV to accept the commands that are coming through, the ones I see in irw.  

In the ~/.lirc/mythtv file, each command included "remote = myremote".  But the remote commands were getting passed as something else, so mythtv was ignoring them, assuming the commands were from the wrong remote.  That makes sense.

What doesn't make sense:  What's matching to the codes on my remote?  I still have keys that aren't returning any commands even though they're making the light blink on my receiver.  Still open to ideas...!

--Dave Althoff, Jr.

---

### Post by musikmann on 2011-12-27
What you need is here:  [http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)  Go to the section describing the "**~/.mythtv/lircrc**" file.  From what I have read, lirc is a 'bridge' between mythtv and the remote.  I guess some day when a developer has ample time on his/her hands, they wont require it, but for now, that page gives a bunch of random extremely useful info about setting up a MCE remote. I have a working MCE under Fedora and MythTV.  Hope this helps and isn't too late and you've already slit your wrists.  This is one of those doesn't 'just works' things in Linux.'  The fix isn't really that complicated, though.


EDIT: you will need to replace the output of 'irw' with what you see for the "BUTTON=" section.  If you haven't edited mythtv key stroke settings, you should be good to go.

---

### Post by s_g_robertson on 2011-12-29
irw will show you the button the lirc is detecting and the remote it think is is coming from.
```
000000037ff07be7 01 Pause mceusb
```
In this case "pause" is the button and  "mceusb" is the remote
so in the lircrc file (~/.lirc/mythtv) it references the remote ,the program, the button and then "key"(config) that you want that to represent.

```
begin
    remote = mceusb
    prog = mythtv
    button = Pause
    config = P
    repeat = 1
    delay = 3
end

```
So in this case when the "mceusb"(remote) Pause(button) is pressed Mythtv(prog) gets a "P"(config)

Also useful in debugging these problems is ircat "prog"
eg
```
ircat mythtv
```
this will print out the config value in response to a button press.

So in a sense irw can show you the input to the lircrc configuration and ircat shows the output

Stephen


> **RideMan said:**
> One more update before I go to bed...

I've figured out how to get MythTV to accept the commands that are coming through, the ones I see in irw.  

In the ~/.lirc/mythtv file, each command included "remote = myremote".  But the remote commands were getting passed as something else, so mythtv was ignoring them, assuming the commands were from the wrong remote.  That makes sense.

What doesn't make sense:  What's matching to the codes on my remote?  I still have keys that aren't returning any commands even though they're making the light blink on my receiver.  Still open to ideas...!

--Dave Althoff, Jr.

---

### Post by RideMan on 2011-12-30
Hmmmmmm...

irw is telling me that key presses are coming from /dev/input/event2 which happens to be the real source symlinked to /dev/input/irremote in udev.  Irritatingly enough, there are key presses on the remote that generate no response at all, even though they are meticulously programmed into the lircrc file. Most irritating is that one of the offending keys is the OK button, making it impossible to, say, dismiss a dialog box or select a program in the program guide.

ircat is showing that the buttons that generate no key code in irw also deliver no response code to mythtv. That is not at all surprising. So where are my button pushes going? I have a remote with 44 buttons on it and only 21 are even generating codes at all.  Even more frustrating, the button names coming out of lirc do NOT match the names in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb even though I have explicitly pointed to that file in REMOTE_LIRCD_CONF= in hardware.conf.  I'm getting button names that don't seem to be referenced *anywhere* (KEY_CDSTOP, KEY_NEXTSONG, KEY_PREVIOUSSONG, to name three). Seeing those weird button names in irw allowed me to edit my .lircrc to make those buttons work, but wherever this configuration file is lurking, it is lacking some key codes. Where the heck are these button translations coming from?

--Dave Althoff, Jr.

---

