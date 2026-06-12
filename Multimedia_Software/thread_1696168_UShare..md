---
title: "UShare."
date: 2011-02-27
forum: Multimedia Software
---

### Post by bestusername on 2011-02-27
Is there anyone else out there who uses UShare? I'm trying to set it up so I can stream videos from Ubuntu to my Xbox 360.

I got it set up however it spews out this:

```
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.2.3:49224
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/james/videos
scandir: No such file or directory
Found 1 files and subdirectories.

```

As you can see it's saying no such file or directory but at the same time telling me it did find the one file in the directory. Anyone have any idea how to fix this or any other software will allow me to achieve streaming to 360? Because this software seems extremely buggy.

---

### Post by bestusername on 2011-02-27
Bump

---

### Post by dhughes on 2011-03-06
The files you have in that directory may not be of teh type ushare or the Xbox can use, perhaps? Maybe? I don't know.

 Ushare is like voodoo, sometimes I can get it to work and other times I can't but I follow teh same steps and set it up the same way. Right now I can't get it working.

 I have the ushare.conf use eth0 and use port 49200 the port is set up in the port forwarding of my router with my computer's IP.

 So conf port 49200, router forwarded 49200.

 Start ushare with *ushare -x* I see my computer's IP scroll by and ushare using 4920**1**.

 I stop ushare and restart it and it shows 49202, stop and start it again and it goes to 49203 and so on it keeps incrementing the port number by one digit each time it is started even though the configuration file is set to 49200.

 It's pretty simple, if I find out how to do it each time I'll write it down and let you know but for now, I don't get it.

**edit:** Ohh I see now, it helps to read the man page I guess :P I just read it again, more throughly and saw [I]"...  -port (-p) PORT
Set Network port to listen on. Default is random above 49152 ...".[/I] so that's why it was incrementing I guess. Now that I set the port to 49152 which apparently you have to use otherwise the port number jumps all over the place, what a weird feature!

**edit #2** It's still incrementing even less than, at or above 49152. This may take some more investigating :(

**edit #3** I guess there's something going on with a library file, libupnp, Ushare uses and it breaks the application, according to [http://ubuntuforums.org/showthread.php?t=903204&highlight=ushare&page=2](http://ubuntuforums.org/showthread.php?t=903204&highlight=ushare&page=2)

**edit #4** I went to [crackednoodle.com]("http://crackednoodle.com/2010/05/ushare-no-longer-supported/") and found a good bit of info that got Ushare working, just don't use DLNA, in the config file for Ushare at the very end where it has *USHARE_ENABLE_DLNA=* just put no so it's USHARE_ENABLE_DLNA=no and for me anyway it now works. Thanks Cracked Noodle!

 Oh and bestusername make sure you don't have any spaces in the path name, on my journey around the Web today I've read that a common problem with your path to your media, and by that I mean path errors such as a space in there somewhere usually at the start or the end like here --> /home/user/pathtomedia or /home/user/pathtomedia <-- or there

---

