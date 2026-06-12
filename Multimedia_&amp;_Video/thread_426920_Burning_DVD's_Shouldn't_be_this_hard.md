---
title: "Burning DVD's Shouldn't be this hard??"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by Scruffynerf on 2007-04-28
Situation:

I do a reasonable amount of video coding, and am a ubuntu/linux newbie. Currently my home rig is a dual boot with XP Home. (Ubuntu Ultimate 1.3 (Edgy +, with multimedia codecs etc installed.)) 

I have a series of avi's which I really need to turn into a basic dvd (vob).  Ideally, I'd like a program to convert the avi's to the vob, and to burn the dvd through a gui without much fuss. I use an old xbox to test - as if a dvd will play on the xbox, it'll play on anything.

On windows, DVDSanta was/is really good for this.

On linux, I can't seem to find anything that works.

Here's my list of what I've tried.

Avidemux - Appers to copy DVD's well, but not go from files on HDD to DVD. Also confusing for options.
Brasero - Burns data to DVD's fine, but that's it.
GnomeBaker - Appears to burn data to DVD's fine, but that's it.
DeVeDe - Converts wonderfully. Can't burn anything to save it's life. The .iso feature seems borked.
ManDVD - Unexpectedly crashes during burn.
QDVDAuthor - Repo version borked. Corrupt init file.

I can't be the only one doing this - what do people use to convert avi's to vob's for ordinary dvd players??

cheers

Scruffy

---

### Post by taurus on 2007-04-28
Here is what I would do.

Use devede to convert .avi to .iso.  Then, use k3b to burn the .iso as an image file to a DVD.  Then, insert the DVD into a standalone player and watch it on a big screen tv.

---

### Post by Scruffynerf on 2007-04-29
I have tried that, no cigar. The dvd player won't recognise it.

I've tried twice with the DeVeDe iso option, burning the iso through both k3d and braseo = no each time
I've tried just creating the disk structure  (audio_ts/video_ts) through DeVeDe and burning it via k3d = nope.

Any other suggestions?

---

### Post by Zeedok on 2007-04-29
I've also been interested in this.

On Win XP I've been using DVD flick which is a great, easy to use, open source project that works really well . . .

BUT is currently only available for Windows.

No-one has ported this to Linux as far as I know. I have not had a chance to try getting it going with wine, but that may be an option. Otherwise, I guess I'm stuck booting into WinXP every time I want to convert an avi!

Here's the link anyway: [http://www.dvdflick.net/]("http://www.dvdflick.net/")

---

### Post by Erlander on 2007-04-29
Try the search button on this forum, on General Help and on Absolute Beginner Talk.

I just searched using "DVD burn encode" on this forum and got some promising leads.

Not being critical, just trying to help.

Rob

---

### Post by Kingsley on 2007-04-30
> **Zeedok said:**
> I've also been interested in this.

On Win XP I've been using DVD flick which is a great, easy to use, open source project that works really well . . .

BUT is currently only available for Windows.

No-one has ported this to Linux as far as I know. I have not had a chance to try getting it going with wine, but that may be an option. Otherwise, I guess I'm stuck booting into WinXP every time I want to convert an avi!

Here's the link anyway: [http://www.dvdflick.net/](http://www.dvdflick.net/)
Would it work with Crossover Office or Wine?

---

### Post by cleverselfreferentialname on 2007-05-01
DVD Flick can't be ported. It's written in Visual Basic 6. I doubt it would work in wine, but give it a shot.

EDIT: Oh, a lot of people like tovid. I'm trying it now. Just make sure the place it's using as it's tmp directory has a ton of space.

---

### Post by berdoo on 2007-05-07
If devede isn't making a proper .iso image for some reason, just select "Create Disc Structure" under "Actions". Use "New Video DVD Project" in K3b to burn the disc. I've also written a couple of tutorials using [Avidemux and DVDStyler]("http://chronologicaldissonance.blogspot.com/2006/11/free-movies.html"), and [devede]("http://chronologicaldissonance.blogspot.com/2007/01/making-dvds-with-devede.html").

---

### Post by IanW on 2007-05-07
Have you tried Tovid? It's on [http://www.getdeb.net]("http://www.getdeb.net")

---

### Post by kelvin spratt on 2007-05-07
i use devede all the time never had a problem i use the latest version [http://www.getdeb.net/](http://www.getdeb.net/) i save as a ISO
then right click on it to bring up flag entry near the bottom WRITE TO DISK left click wait for disc to burn
watch dvd success in every burn this may look sarcastic but it is not. That really is all i do send me a message if you need more help i don't personally like kb3 i've had mixed results Brasero is also good for ISO writing also ISO pruduce less errors when burning as it copies the disc structure as it was written i hope this gives you hope

---

### Post by RudolfMDLT on 2007-05-07
@scruffy: okay - this might be silly but did you burn the ISO on a data disc or did you tell K3B to burn the image? Put the disc in a PC - is there a Video_ts folder or an ISO image?

---

### Post by jstarr on 2007-09-15
Hi there,

I would suggest reading the Gentoo HOWTOs for dvd authoring using the command line that are available [here]("http://gentoo-wiki.com/HOWTO_Create_a_DVD").

While I love GUIs, I think it is helpful to at least have a partial understanding of the command line tools, because they are often easier to use for certain tasks.

For example, if you want to create a DVD filesystem from a mpeg file without any DVD menus, you can use the following commands.

```
$ dvdauthor -o dvd/ -t movie.mpg
$ dvdauthor -o dvd/ -T
```

Now you have a DVD filesystem that you can burn to a DVD!

I will grant that other tasks for DVD authoring using the command line are more complicated than this; however, once you have a good understanding of the tools, they offer better, more reliable and customizable results.

I just thought I would offer my two cents. Good luck! ;)

---

### Post by wickstopher on 2007-09-15
This might seem a bit ridiculous, but sometimes we overlook the funniest/simplest things. In DeVeDe, the default format is set to PAL.  If you are using an NTSC DVD player, you will have to set that manually when you add a file to the project.

---

### Post by robertmf on 2007-09-19
> **IanW said:**
> Have you tried Tovid? It's on [http://www.getdeb.net]("http://www.getdeb.net")

Using Feisty.

TOVID  works for dvd/vcd encoding and authoring.   TOVID is a collection of terminal based programs. dvdauthor, makexml, makedvd/vcd ...
[COLOR="Red"][B]
MAKEXML has "-noask" as an option.  This is a bug.  [/B][/COLOR]

What you have to do is do the TOVID [LAYOUT] and [ENCODE].  At the bottom of the [ENCODE] page is a button to [SAVE AS SCRIPT]

Do this.  

Edit the .sh to remove the MAKEXML -noask  and "from gui"

Then run the script.

**Note** -- VCD does not **do** menus and chapters, so edit out -menu if authoring VCD.  Perhaps best to create one .sh template for dvd and one for vcd.

---

