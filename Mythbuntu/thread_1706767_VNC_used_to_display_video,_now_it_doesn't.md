---
title: "VNC used to display video, now it doesn't"
date: 2011-03-14
forum: Mythbuntu
---

### Post by bcg30506 on 2011-03-14
I have x11vnc starting at boot on my combined mythtv box so I can access it occasionally from a machine that cannot run mythfrontend to do certain housekeeping tasks.  This includes editing a recording then starting a transcode with cuts.

The client is a Mac running JollysFastVNC.  It all worked fine, including video streaming across VNC, though very slowly, but enough to press 'e' to add cut points then exit to the menu.  Now all I get is the menus and a black screen when playing a recording.  The client has not been upgraded but the mythbuntu box did via an apt-get upgrade.  I do not know what all was updated but something broke the ability I had to view video over VNC.

Any tips on what I can look at to find the issue and hopefully then to revert it back?  I'm running 10.04 with all updates applied.

---

### Post by dibuntux on 2011-03-14
It does not work if you use VDPAU on the remote PC. Either use a profile with no VDPAU or use mythtv client.

;)

---

### Post by nhtrader on 2011-03-14
> **bcg30506 said:**
>  Now all I get is the menus and a black screen when playing a recording.

Would you please describe in more detail what happens on the client? 

But if you make a successful connection and nothing appears, it sounds like the vnc config file needs to be edited. A command is missing to start the virtual desktop. And of course the config filename and location depend upon which vnc server you are using.

what's the command you use to start your vnc server? x11vnc, vnc4server or ...

---

### Post by bcg30506 on 2011-03-14
I know it is not supposed to work with VDPAU, but up until the update this weekend, it did.  I cannot tell you how, only that it has for the last 1-2 years since I've been running with VDPAU.

As for details, again, until updating the mythbuntu box with all the apt-get updates this weekend, everything worked.  Now, however, VNC works for all the menus and image gallery, but when I play a video or recording, the client window goes black.  This is what most sites document as "normal" and I wouldn't have thought anything of it, except it did work for me.

The client is JollyFastVNC on OS/X.  The server is started with:

x11vnc -rfbauth ~/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -bg -xkb

---

### Post by bcg30506 on 2011-03-15
I did for the sake of completeness try changing the playback profile from VDPAU to Slim and yes, video then played over VNC.  So it does appear that something changed in the last update that took away the ability for VDPAU profile to display video over a VNC connection, because it did a week ago.

---

### Post by krunge on 2011-03-16
> The server is started with:

x11vnc -rfbauth ~/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc xxxxxxxxxx -bg -xkb
Just a guess, but maybe the x11vnc option "-noxdamage" makes a difference?  The X11 DAMAGE extension is often broken by drivers and/or Xorg.

BTW: The -notruecolor option only applies to low color 8bpp (256 colors) displays which I doubt yours is...  I suggest you remove it from your cmdline, and I also suggest you edit your post in this thread and delete it from there (you'd be amazed how many people blindly cut-n-paste commands, post them back, etc. until the posted suggestions are full of noise.)

---

### Post by bcg30506 on 2011-03-17
Tried the -noxdamage option and it made no difference. Thanks for the tip though.

I also removed the -notruecolor option and could not tell a difference either so I removed it from my posted command earlier in this thread.

---

### Post by bcg30506 on 2011-03-17
Maybe someone can help me with the x11vnc settings changes mentioned above.  I manually killed the running process and manually ran from the command line to try these out.  However, I do not know where to change them so it uses the new parameters when it starts at boot.

I did not add it to my startup myself and the parameters I originally posted must be defaults x11vnc package uses when installing.  So I have no idea how to find the file they are set in to change the parameters used when booting.

[EDIT]
Never mind. I'm an idiot. A bit more searching and I found this:
[Thread post that answers question]("http://ubuntuforums.org/showpost.php?p=6808952&postcount=8")
The answer is:
> /usr/share/mythbuntu/session.sh

---

