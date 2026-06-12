---
title: "mounting samba shared = permission denied"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by Clive McCarthy on 2010-12-09
I have a shared directory on another machine but I can't get it to mount as a samba share.

The permission denied doesn't say where/which permission is denied. Is it on the remote on on the local machine? The remote has sharing enabled for the shareddocs directory and after I have mkdir'ed the local mount point I open it's permissions too.

The verbose response from mount.cfis looks like this:

[COLOR="Blue"][INDENT]mount.cifs kernel mount options: unc=//192.168.1.102\shareddocs,domain=WORKGROUP,ver=1,rw ,username=clive,,,,,,,,,,,ip=192.168.1.102,pass=** ******
mount error(13): Permission denied
Refer to the mount.cifs( manual page (e.g. man mount.cifs)[/INDENT][/COLOR]

The man page does not have a list of error codes.

I have searched the web for a fix but none of the _many_ suggestions work!

---

### Post by gmargo on 2010-12-10
> //192.168.1.102[COLOR=Red]\[/COLOR]shareddocsPerhaps try a forward slash, not a backslash.

---

### Post by Clive McCarthy on 2010-12-10
The curious thing is that the command HAS a forward slash but cifs converts it to a back-slash!

[COLOR="Blue"]sudo mount.cifs //artshow16/shareddocs $ART_SHOW_DIR --verbose -o domain=WORKGROUP,username=clive,password=*******
[/COLOR]

---

### Post by Clive McCarthy on 2010-12-10
It seems you were on the right track. My command does have a "/" and cifs converts it to a "\" for who knows what reason???

However, if I turn on mapchars then the SAMBA mount.cifs succeeds. This is of course a dreadful hack. The man page for mount.cifs _excludes_ the backslash from being mapped. Not that I had a backslash to start with!

[INDENT][COLOR="SeaGreen"][I]       mapchars
           Translate six of the seven reserved characters (not backslash, but
           including the colon, question mark, pipe, asterik, greater than and
           less than characters) to the remap range (above 0xF000), which also
           allows the CIFS client to recognize files created with such
           characters by Windows´s POSIX emulation. This can also be useful
           when mounting to most versions of Samba (which also forbids
           creating and opening files whose names contain any of these seven
           characters). This has no effect if the server does not support
           Unicode on the wire.
[/I]
[/COLOR][/INDENT]

I have seen at least one BIG rant on the web about cfis and it seems appropriate. Judging from some developer commentary it looks as if they are just hacking around. The developers seem to be in a bind about resolving translations between Windows conventions and Unix conventions.
The verbose mode for mount.cfis produces a truncated output and the error messages are worthless. My guess is that a bunch of script kiddies are writing cfis with very tangled command-line Goto logic!

The man pages also suggest that providing the UNC name will work most of the time. It doesn't.

[INDENT][I][COLOR="SeaGreen"]       ip=arg
           sets the destination IP address. This option is set automatically
           if the server name portion of the requested UNC name can be
           resolved so rarely needs to be specified by the user.
[/COLOR][/I][/INDENT]

I have found it essential to use [COLOR="Blue"]resolveip[/COLOR] to obtain the IP address for the server and then spoon feed mount.cfis with it.

---

### Post by Clive McCarthy on 2010-12-12
Of further note: see how asterisk is spelled in the man page? We are dealing with some rough customers here.

I hit an "unable to allocate memory" message from cifs. The poor thing is out of it's mind...

I have my script working but it's not built on a firm foundation.

---

