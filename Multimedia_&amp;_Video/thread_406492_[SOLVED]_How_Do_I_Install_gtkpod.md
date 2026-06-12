---
title: "[SOLVED] How Do I Install gtkpod?"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by jeremyj on 2007-04-11
Hey, all, this is another newbie question.  I apologize.

I'm looking for an easy way to transfer all of my music from my iPod Video to my Ubuntu laptop.  I've heard gtkpod is an easy way of doing this, and I've downloaded the tar.gz file to my desktop, but have no clue what to do next.  (I don't know how to install a program at all on a Linux system.)  Do I need to download any extra gtkpod files as well?

Also, I don't think I'll be using Ubuntu for my iPod in the future, so will this mess up my iPod at all?  I just need a quick and easy way to transfer my music over to my laptop and preserve the track names, track numbers, album names, artists, genres, and possibly album art.  Please help.  Thanks in advance.


Jeremy

---

### Post by heimo on 2007-04-11
Enable Universe packages and use synaptic to install gtkpod:
[https://wiki.ubuntu.com/MOTU/Packages?action=show](https://wiki.ubuntu.com/MOTU/Packages?action=show)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

I have no idea if gtkpod will mess up your iPod. I haven't used gtkpod or iPod.

---

### Post by pingpongboss on 2007-04-11
i'm pretty sure Amarok can transfer songs from your ipod into your computer, keeping all the tags intact. At least the version in feisty can (1.4.5).

---

### Post by kvonb on 2007-04-11
I couldn't get gtkpod to actually write to the iPod (I have a nano), so it seems a bit useless to me.

I use Amarok. it does the lot, reads and writes easily.

One side note, if an MP3 refuses to play on the iPod, open it with Audacity and export it as an MP3 (you will have to have libmp3lame installed to do that, look in synaptic).

I found that the iPod doesn't like anything higher than 128kbps audio, but it could be something else entirely, but re-saving it as MP3 seems to fix it.

Rgds, Kev :)

PS.. Oh and don't forget to right click on the iPod icon and select "eject" before unplugging it!!!

PPS.. You can set Amarok as the default application to launch when you plug the iPod in by going to the menu: System->Preferences->Removable Drives and Media, selecting the "Multimedia" tab and type in amarok where it says rythmbox.

---

### Post by jeremyj on 2007-04-11
> **heimo said:**
> Enable Universe packages and use synaptic to install gtkpod:
[https://wiki.ubuntu.com/MOTU/Packages?action=show](https://wiki.ubuntu.com/MOTU/Packages?action=show)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

I have no idea if gtkpod will mess up your iPod. I haven't used gtkpod or iPod.

Thanks!  That worked perfectly!  gtkpod is installed now.  The only problem I've having is transferring my music from the iPod to my laptop.

> **pingpongboss said:**
> i'm pretty sure Amarok can transfer songs from your ipod into your computer, keeping all the tags intact. At least the version in feisty can (1.4.5).

I think I'll look into Amarok too since gtkpod seems to be a little picky about transferring the songs to my laptop.  Thanks!

> **kvonb said:**
> I couldn't get gtkpod to actually write to the iPod (I have a nano), so it seems a bit useless to me.

I use Amarok. it does the lot, reads and writes easily.

One side note, if an MP3 refuses to play on the iPod, open it with Audacity and export it as an MP3 (you will have to have libmp3lame installed to do that, look in synaptic).

I found that the iPod doesn't like anything higher than 128kbps audio, but it could be something else entirely, but re-saving it as MP3 seems to fix it.

Rgds, Kev :)

Oh and don't forget to right click on the iPod icon and select "eject" before unplugging it!!!

Sorry.  I'm not trying to write to my iPod, just copy from it.  I'll keep that in mind about the problems with writing and MP3's not playing though.  And, yeah, clicking "Eject" might be a good idea.  I almost made that mistake!  Haha!  Thanks again!


Does anyone know why gtkpod won't copy from my iPod?  I keep getting an error message that says something like, "Failed to write.  Did not match pattern."  (A quick paraphrase.)  I've read that some parts of gtkpod need additional packages to support different music file extensions.  Is that true and could that be the problem?  Or do I need to change the template to something other than the default writing template?  Thanks in advance again!

---

### Post by kellsens on 2007-04-11
Hi Jeremyj,
 
    Take a look at Yamipod ([http://www.yamipod.com]("http://www.yamipod.com")). I have an Ipod Video too, and I use this program to 'manage' it.

Kellsens

---

### Post by stchman on 2007-05-08
> **jeremyj said:**
> Thanks!  That worked perfectly!  gtkpod is installed now.  The only problem I've having is transferring my music from the iPod to my laptop.



I think I'll look into Amarok too since gtkpod seems to be a little picky about transferring the songs to my laptop.  Thanks!



Sorry.  I'm not trying to write to my iPod, just copy from it.  I'll keep that in mind about the problems with writing and MP3's not playing though.  And, yeah, clicking "Eject" might be a good idea.  I almost made that mistake!  Haha!  Thanks again!


Does anyone know why gtkpod won't copy from my iPod?  I keep getting an error message that says something like, "Failed to write.  Did not match pattern."  (A quick paraphrase.)  I've read that some parts of gtkpod need additional packages to support different music file extensions.  Is that true and could that be the problem?  Or do I need to change the template to something other than the default writing template?  Thanks in advance again!

I thought that when an ipod has the DRM music(M4P I think) files it won't let you copy the files from teh ipod to the computer.

---

### Post by dangerousnerd on 2007-05-08
I have never had good luck using gtkpod.  I tried it with every version since Breazy (I think) and it never worked.  I use Banshee.  You can install it through Synaptic. :)

---

### Post by jeremyj on 2007-05-08
> **stchman said:**
> I thought that when an ipod has the DRM music(M4P I think) files it won't let you copy the files from teh ipod to the computer.

Yeah, that's true.  I found that out with Amarok.  I never used gtkpod because I found Amarok to be easier.  You're right about the DRM protected files, but I'm not worried about copying those to my laptop because 99% of my music is from CD's that I've bought in stores and that's what I really wanted to copy over instead of having to painstakingly re-import all of my music to my other computer.

---

