---
title: "k3b 'device in use' message"
date: 2008-06-24
forum: Multimedia Software
---

### Post by logos34 on 2008-06-24
I keep getting this pop up when trying to burn an audiocd in k3b:

[ATTACH]75229[/ATTACH]

The only apps I have open beside k3b are firefox, nautilus, terminal, gedit, maybe mail and a couple of others (non-multimedia).  I have to hit continue at each step.  I don't want to hit 'quit other apps' because I need them open.  There must be a daemon that's causing this, I think.  But which one?

Never encountered this gutsy

---

### Post by logos34 on 2008-06-29
bump.

Still looking for an answer to what 'gvfsd-cdda' daemon is.  Actually, I hit 'quit other apps' and it appeared to kill just the gvfsd-cdda, not the other apps, and, voila, no more message. So how to disable permanently?  Also, when I look in system monitor, I still see three others: gvfsd, gvfsd-burn, gvfsd-trash. ???

---

### Post by Ilias83 on 2008-07-24
Did you finally found out what this gvfsd-cdda is?
I get the same message when I'm trying to rip my music.
I hit "Quit the other applications" and everything works smoothly.
But I have to hit the same option in every music CD I'm trying to rip.

---

### Post by logos34 on 2008-07-24
Nope, still get the darn message, but at least quit other apps kills it

---

### Post by GSZX1337 on 2008-07-27
Bumpy. Does anyone know what it is. It appears that K3B is the only app that tells me that it is using it. Brasero just hangs. Also, is there a way to have more than one application use the CD Drive (similar to the way you can with the sound card)?

---

### Post by editrix on 2008-07-27
In researching my own cd burning problems, I discovered a post that said that Nautilus locks up whatever it takes to burn a cd, and there's a fix for it. Sorry I can't be more specific, but I've read 1000s of web pages about cd burning recently. :(

---

### Post by mc4man on 2008-07-27
> Did you finally found out what this gvfsd-cdda is
That's the location of audio cds in hardy, and while i don't have k3b I saw similar behavior when working on getting amarok to auto play cds. (another kde app?)
When i first tried a 'normal' method to have amarok autoplay a cd, while it would start up it was unable to access the cd. Even after a little tweaking allowed access the result was a disaster.
The main reason was it was using the location (home/<username>/.gvfs/.. ) as the device. (and then unfortunately having it's default device changed to that). I'm thinking that maybe some kde apps are having a little  difficulty with the new way audio cds are 'treated' in hardy.

The way I found to have Amarok work properly as the default (autoplay) player I don't think would translate well to k3b, but possibly this is an 'explanation'

---

### Post by logos34 on 2008-08-04
whatever that 'gvfs-cdda' is ('gnome virtual file system daemon'??), it's gone away, perhaps fixed by a recent update.

> **mc4man said:**
> That's the location of audio cds in hardy, and while i don't have k3b I saw similar behavior when working on getting amarok to auto play cds. (another kde app?)
When i first tried a 'normal' method to have amarok autoplay a cd, while it would start up it was unable to access the cd. Even after a little tweaking allowed access the result was a disaster.
The main reason was it was using the location (home/<username>/.gvfs/.. ) as the device. (and then unfortunately having it's default device changed to that). I'm thinking that maybe some kde apps are having a little  difficulty with the new way audio cds are 'treated' in hardy.

The way I found to have Amarok work properly as the default (autoplay) player I don't think would translate well to k3b, but possibly this is an 'explanation'

I am having a similar problem getting amarok to look up the cdda info for cds...Usually the drive makes a lot of sound and fury before abandoning the attempt and printing 'track#' for each...It plays the cd but that's it.  Maybe we've talked about this, not sure.

I've checked the amarok settings and even the config file in the kde folder.  But even if I can get it to fetch track titles like it should (and BTW it does the album covers fine), the spin up noise is really annoying (again, no settings in the config file seem to fix it)

---

### Post by Kevrox on 2008-12-05
same problem here but I an using intrepid gnome kernel 27.10
SO the hardy fix did not transfer to intrepid??? 
If I tell k3b to kill the application (gvfsd-cdda) it tries and then says error encoding track and spits the cd out... 
will keep trawling...unless someone has a workaround

---

### Post by commonplace on 2009-01-21
> **Kevrox said:**
> same problem here but I an using intrepid gnome kernel 27.10
SO the hardy fix did not transfer to intrepid??? 
If I tell k3b to kill the application (gvfsd-cdda) it tries and then says error encoding track and spits the cd out... 
will keep trawling...unless someone has a workaround


Same problem here. Trying to use K3b to rip an audio CD, and keep getting this message. Killing gvfsd-cdda doesn't work. Anyone?

/Kevin

---

### Post by Frogbarf on 2009-03-12
I rebooted and when I fired up K3B, I was able to kill gvfsd-cdda and proceed.

Gvfsd-cdda is the "Gnome virtual file system" (demon?), something new in Hardy and as others have observed it interferes with other processes wanting to use the CD drive.

The thing that's very very odd is that within the last week I was able to copy an Audio CD using K3B without the slightest hiccup, but updating the system last night (after ~3 months of no updates) seems to have changed that.

I have a funny idea that the bright spark who thought of GVFS didn't think it through quite all the way!

Has this been reported as a bug on Launchpad??

---

### Post by SvenS. on 2009-07-11
Has anybody solved this problem? I'm still trying to copy a mixed CD (Audio+Video) with only one cd/dvd drive. I don't know how to manage with k3b because the drive is already in use by gvfsd-cdda. I konw I can turn that off by typing:
gvfs-mount -u cdda://sr0/
but that unmount command is gone as soon as the cd-drive opend and closed again. and after that k3b tells me it can not fixate the disk.

Any help???

---

### Post by chitowner2 on 2010-08-22
Same scenario here too; k3b getting "gvfsd-cdda" error. 

Maybe this is due to an auto-run setting in gnome? 
Or whatever causes the popup that displays options?

CT
:-/

---

### Post by Paddy Landau on 2011-06-25
Bump.

I still get this error with K3B. Fortunately, it's no problem to kill the process, but I'd love to know what it's about and how to stop it.

---

### Post by Mike_tn on 2012-03-26
And 10 months later....
I used to run Maverick, now I'm running Debian Squeeze and I get the K3B "CD/DVD in use by gvfsd-cdda" note too. I can kill it. Makes you wonder what else is messed up by this though.

---

### Post by ianmillington on 2012-05-03
I have a similar issue but I'm using KDE 

I get a pop-up showing this when I invoke K3b from the right click menu

"K3b is currently busy and cannot start any other operation"

It does a 5 second countdown and goes away. It does not appear if I launch KDE through its own icon

---

### Post by GlasGhost on 2012-08-17
Same problem here in Natty Narwhal . . .

BUMP

---

