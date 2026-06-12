---
title: "DLNA Support from a myth Back End Server"
date: 2009-04-30
forum: Mythbuntu
---

### Post by lantern on 2009-04-30
Hi all,

I problably have the wrong end of the stick with DLNA but i havwe a query.

I have just purchased a new LCD tv (Sony Bravia) which is DLNA compliant.

I have tried to connect it to the MYTH server but it cannot find.

Is there something that i must do in order for a DLNA compliant unit to be able to see folders (photos mainly).

Permissions are set as anyone can read the file...CHMOD directorys?

Any pointers would be great.

Roger

---

### Post by utar on 2009-05-01
I don't think Myth has DLNA built it.  However I expect you will be able to install a DNLA server program and point it at the Myth media directories.

Not something I've had experience off, but perhaps someone else on the forum can help.

[Edit: as a matter of interest is this the TV which Myth is connected to, or elsewhere in your house?]


Utar

---

### Post by joshoekstra on 2009-05-02
I got a 40W5500 and here it tells me that it can't use mythtv, it does see it though. I tried using ushare and a couple of other free programms, but they get the same result. I'm not enclined to install twonky if another free programm could do it, but sofar no luck for me :(

---

### Post by lantern on 2009-05-03
Thanks for the replies, i have a 40W4500. and after a bit of playing it can see the server but not the files.

Utar; The tv is connected to the backend by (hdmi) and via the LAN.

 Not a major issue as myth does everything anyhow. i would be nice to be able to use the functions of the tv and let the pc do more intensive stuff (transcoding etc...)

Frustrating!!!

BTW anyone know of some sony hacks ;)

---

### Post by rojjjjjjj on 2009-06-14
I have the same setup and am now using minidlna. I am not sure why the inbuilt pnp server in mythtv does not work but minidlna was very easy to configure (once compiled). It would be great to see it available as an ubuntu package or even incorporated into the mythtv code for a future release.

---

### Post by joshoekstra on 2009-06-14
Ah, you got it to work? What was the problem in the end?

---

### Post by zekopeko on 2009-06-14
> **rojjjjjjj said:**
> I have the same setup and am now using minidlna. I am not sure why the inbuilt pnp server in mythtv does not work but minidlna was very easy to configure (once compiled). It would be great to see it available as an ubuntu package or even incorporated into the mythtv code for a future release.

go to launchpad.net and report a bug with need-packaging tag.
provide link to the page and source code. and any release (if it was made).

---

