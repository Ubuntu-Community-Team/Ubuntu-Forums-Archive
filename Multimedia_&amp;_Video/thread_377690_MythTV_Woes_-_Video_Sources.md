---
title: "MythTV Woes - Video Sources"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by Muffy on 2007-03-06
I'm having some troubles with my Video Sources in the mythtv-steup installation process.

When trying to setup the tv_grab_au grabber and click OK, I get a message stating: 
> MythTV was unable to retrieve channel information for your provider. Please check the terminal window for more information 

From the terminal window I found this:
> 
2007-03-07 03:19:08.232 Please wait while MythTV retrieves the list of available channels
Can't locate Compress/Zlib.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/tv_grab_au line 137.
BEGIN failed--compilation aborted at /usr/bin/tv_grab_au line 137.
2007-03-07 03:19:08.272 tv_grab_au --config-file '/root/.mythtv/tvgrabber.xmltv' --configure
2007-03-07 03:19:08.272 exited with status 512


Does anybody know a solution?

---

### Post by Prefader on 2007-03-06
Make sure the right perl modules are installed - in this case, try :
```
sudo apt-get install libcompress-zlib-perl
```
and see if that fixes your problem.

---

### Post by superm1 on 2007-03-06
This particular grabber needs a perl library not installed by default:

```
sudo apt-get install libcompress-zlib-perl
```

Should do it.

---

### Post by Muffy on 2007-03-06
OK That didn't fix the problem. However, I have noticed something that I didn't notice before in the terminal output when running mythtv-setup. Here's the complete output:

> [B]X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed[/B]
2007-03-07 10:19:56.673 Using runtime prefix = /usr
2007-03-07 10:19:56.709 DPMS is active.
2007-03-07 10:19:56.746 New DB connection, total: 1
2007-03-07 10:19:56.761 Connected to database 'mythconverg' at host: localhost
2007-03-07 10:19:56.763 Total desktop dim: 1280x1024, with 1 screen[s].
2007-03-07 10:19:56.765 Using screen 0, 1280x1024 at 0,0
2007-03-07 10:19:56.884 Current Schema Version: 1160
2007-03-07 10:19:56.894 Total desktop dim: 1280x1024, with 1 screen[s].
2007-03-07 10:19:56.897 Using screen 0, 1280x1024 at 0,0
2007-03-07 10:19:56.899 Switching to square mode (G.A.N.T.)
2007-03-07 10:19:57.369 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-03-07 10:19:57.682 Joystick disabled.
2007-03-07 10:19:58.038 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-03-07 10:19:58.207 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-03-07 10:20:14.343 New DB connection, total: 2
2007-03-07 10:20:14.343 Connected to database 'mythconverg' at host: localhost
2007-03-07 10:20:14.344 DiSEqCDevTree, Warning: No device tree for cardid 1
2007-03-07 10:20:14.357 New DB connection, total: 3
2007-03-07 10:20:14.358 Connected to database 'mythconverg' at host: localhost
2007-03-07 10:21:05.343 Please wait while MythTV retrieves the list of available channels
Can't locate Date/Parse.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/tv_grab_au line 139.
BEGIN failed--compilation aborted at /usr/bin/tv_grab_au line 139.
2007-03-07 10:21:05.519 tv_grab_au --config-file '/root/.mythtv/tvgrabberau.xmltv' --configure
2007-03-07 10:21:05.519 exited with status 512




---

### Post by superm1 on 2007-03-06
> **Muffy said:**
> OK That didn't fix the problem. However, I have noticed something that I didn't notice before in the terminal output when running mythtv-setup. Here's the complete output:
Well this got you closer, you still appear to be missing another perl module though:

```
sudo apt-get install libtimedate-perl
```

---

### Post by Muffy on 2007-03-06
```
sudo apt-get install libtimedate-perl
```

After running this I get a slight change in my errors (bolded):

> X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-03-07 11:43:50.505 Using runtime prefix = /usr
2007-03-07 11:43:50.544 Gnome-Screensaver support enabled
2007-03-07 11:43:50.544 DPMS is active.
2007-03-07 11:43:50.672 New DB connection, total: 1
2007-03-07 11:43:50.716 Connected to database 'mythconverg' at host: localhost
2007-03-07 11:43:50.736 Total desktop dim: 1280x1024, with 1 screen[s].
2007-03-07 11:43:50.759 Using screen 0, 1280x1024 at 0,0
2007-03-07 11:43:50.891 Current Schema Version: 1160
2007-03-07 11:43:50.902 Total desktop dim: 1280x1024, with 1 screen[s].
2007-03-07 11:43:50.904 Using screen 0, 1280x1024 at 0,0
2007-03-07 11:43:50.912 Switching to square mode (G.A.N.T.)
2007-03-07 11:43:51.354 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-03-07 11:43:51.821 Joystick disabled.
2007-03-07 11:43:52.195 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-03-07 11:43:52.359 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-03-07 11:44:13.673 New DB connection, total: 2
2007-03-07 11:44:13.673 Connected to database 'mythconverg' at host: localhost
2007-03-07 11:44:25.171 Please wait while MythTV retrieves the list of available channels
Can't locate Date/Manip.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/tv_grab_au** line 140.**
BEGIN failed--compilation aborted at /usr/bin/tv_grab_au **line 140.**
2007-03-07 11:44:25.557 tv_grab_au --config-file '/home/mlee/.mythtv/tvgrabberau.xmltv' --configure
2007-03-07 11:44:25.557 exited with status 512


Also, the error "Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed" has disappeared (one small victory :)).

---

### Post by superm1 on 2007-03-06
> **Muffy said:**
> ```
sudo apt-get install libtimedate-perl
```After running this I get a slight change in my errors (bolded):



Also, the error "Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed" has disappeared (one small victory :)).
Your definitely getting closer....

i'm surprised that there are this many deps for this grabber, anyhow:

```
sudo apt-get install libdate-manip-perl
```

That session management error isn't a big deal.

---

### Post by superm1 on 2007-03-06
I'm finding these deps by looking what package that missing file is in.  Once they are all resolved, i'll make a wiki entry about this.

---

### Post by Muffy on 2007-03-06
```
sudo apt-get install libdate-manip-perl
```

OK Just tried that, still no luck; I'm getting the same error messages. 

I'm concerned about the "Failed to open device" errors; could this mean that I haven't installed my tv card properly?

---

### Post by superm1 on 2007-03-06
> **Muffy said:**
> ```
sudo apt-get install libdate-manip-perl
```OK Just tried that, still no luck; I'm getting the same error messages. 

I'm concerned about the "Failed to open device" errors; could this mean that I haven't installed my tv card properly?

Your still getting: "Can't locate Date/Manip.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/tv_grab_au[B] line 140."
[/B]
That was the relevant error.

---

### Post by Erlander on 2007-03-06
I don't think tv_grab_au exists.  Its my understanding that EPG for Australia don't exist as out TV channels won't publish them to stop people recording and cutting out the ads.

Here is what I did.

Rob

---

### Post by Muffy on 2007-03-06
OK I see, my mistake. You're right, that has changed. Here's the output:

```
2007-03-07 12:40:09.906 Please wait while MythTV retrieves the list of available channels
Can't locate DateTime/TimeZone.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/tv_grab_au line 141.
BEGIN failed--compilation aborted at /usr/bin/tv_grab_au line 141.
2007-03-07 12:40:10.978 tv_grab_au --config-file '/home/mlee/.mythtv/tvgrabberau.xmltv' --configure
2007-03-07 12:40:10.979 exited with status 512

```

---

### Post by Muffy on 2007-03-07
OK, I'm starting to figure this out (i think). 

So if I'm getting this error:

```
Can't locate DateTime/TimeZone.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/tv_grab_au line 141.
BEGIN failed--compilation aborted at /usr/bin/tv_grab_au line 141.
```

I should try this:

```
sudo apt-get install libdatetime-timezone-perl
```

I'm gonna give that a go and see if I've learned something.

---

### Post by Muffy on 2007-03-07
Aha! Progress! Although I still haven't got MythTV running yet, I've fixed that one problem and (more importantly) learned how.  Sadly, I've got another error message to fix. 

```
Can't locate DateTime/Format/DateManip.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/tv_grab_au line 142.
```

I'm not sure what I need to download for this one; I can't work it out. Can anyone help?

---

### Post by superm1 on 2007-03-07
> **Muffy said:**
> Aha! Progress! Although I still haven't got MythTV running yet, I've fixed that one problem and (more importantly) learned how.  Sadly, I've got another error message to fix. 

```
Can't locate DateTime/Format/DateManip.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/tv_grab_au line 142.
```I'm not sure what I need to download for this one; I can't work it out. Can anyone help?
I'm not sure this is for sure it, but hopefully.  If not, you will have to get that from CPAN (and someone really *should* make a package for it)
**```
sudo apt-get install  libhtml-calendarmonth-perl
```**

---

### Post by buddyholy on 2007-03-10
I think you have the dodgy version. 

I had the same problems as you, I managed to fix that  problem you had but it just lead to more code errors. 

Try the tv_grab_au from 

[http://www.onlinetractorparts.com.au/rohbags/xmltvau/](http://www.onlinetractorparts.com.au/rohbags/xmltvau/)

extract it into /usr/share/xmltv/tv_grab_au

then copy the tv_grab_au into /usr/bin

and see how it goes

---

