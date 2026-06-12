---
title: "Need Names of Media Apps for Ubuntu"
date: 2007-06-21
forum: Multimedia Production
---

### Post by GMU_DodgyHodgy on 2007-06-21
I want to take my photos and run them in a movie format with music.  I used to do this with Windows Movie Maker but want to do the same in Ubuntu. I would like the output to be in some video media format similar to quicktime or .wmv that could then also be burned to a CD.  

Any examples of software I can try for linux?

---

### Post by renzokuken on 2007-06-21
kino is the closest to WMM, its in the repos.

---

### Post by GMU_DodgyHodgy on 2007-06-21
> **renzokuken said:**
> kino is the closest to WMM, its in the repos.

Thank you for the reference.  Kino looks good for movies - however, I also wanted to use it for photo book compilations with audio - can Kino support that as well.  The HOWTOs on the website seem to focus on video.

I also found Open Movie Maker that looks good as well.  

I will report on anything else I find.

---

### Post by jubjubrsx on 2007-06-22
you might check out in automatix2 they have a package called    iLinux kind of the equivelant of iLife for macOSx

---

### Post by ridgeland on 2007-06-23
I also want to create a DVD for TV that is a slideshow with music I selected.
I search and test from time to time but have not succeeded in finding a simple process.

Here are some packages to explore.  They capture your PC screen etc:
Istanbul 
gtk-recordMyDesktop
xvidcap

xvidcap is nice for making a training video with the microphone and screen, recording mouse movements and screens opening.  Like the other two you could play a slideshow in another program and record the screen as it goes by making a movie.  Open air recording from speakers to microphone is not appealing.

qdvdauthor and dvd-slideshow talk of doing what I want but I have not gotten them to work.

I think Kino should be able to edit the movie to replace the sound track with a sound file.  I haven't see it yet.

Post back if you find the solution.  Let us know.

---

### Post by eggdeng on 2007-06-23
> I want to take my photos and run them in a movie format with music. Avidemux, it's in the repositories.

---

### Post by ridgeland on 2007-06-24
Personal breakthrough:
I made a slide show with sound.
Not so far as getting it to a DVD for the TV's DVD player but I got closer.
I used qdvdauthor to create a slide show (slideshow.vob) --- very awkward.
Then I used Avidemux to add a sound track (mp3) to the slideshow --- very easy
Avidemux saved it as avi format (slideshow.avi).  This plays fine with mplayer and totem.

I copied it over for WinXP but it only plays the sound track, no video.
I had a similar problem playing xvidcap videos in Windows.  With xvidcap I found an option that saved it in a format Windows liked.  I haven't found that in Avidemux yet.

---

### Post by ridgeland on 2007-06-24
:) Success, I just watched my slideshow with music on my TV :)
I used
qdvdauthor
Avidemux
DeVeDe

With qdvdauthor I created a slideshow (59 photos from our wedding in 1986)  Then with Avidemux I added an mp3 (some Brahms).  Then with DeVeDe I created a Video DVD iso (NTSC).  Then with Nautilus I just said burn to CD (DVD actually).   Popped the DVD in the TV's DVD player and watched my 8 minute slide show with music.

If anyone wants the detail of all the steps it took, just ask.  When I fight an issue I tend to create an instruction sheet for myself to use a year from now when I've forgotten it all.

If anyone can explain the process another way please post the tools and steps.

---

### Post by Dragonbite on 2007-06-25
> **ridgeland said:**
> :) Success, I just watched my slideshow with music on my TV :)
I used
qdvdauthor
Avidemux
DeVeDe

With qdvdauthor I created a slideshow (59 photos from our wedding in 1986)  Then with Avidemux I added an mp3 (some Brahms).  Then with DeVeDe I created a Video DVD iso (NTSC).  Then with Nautilus I just said burn to CD (DVD actually).   Popped the DVD in the TV's DVD player and watched my 8 minute slide show with music.

If anyone wants the detail of all the steps it took, just ask.  When I fight an issue I tend to create an instruction sheet for myself to use a year from now when I've forgotten it all.

If anyone can explain the process another way please post the tools and steps.Awesome!  Yeah. I love hearing how other people get things working so I'd love to get a copy of your documentation!

I've been thinking that I need to get some family video and pics on DVD to send to my brothers so they can see their nieces and nephew more than just around Christmas time! :)

Two other video projects that are promising but fairly early in their development stage are [[COLOR="Blue"]Diva[/COLOR]]("http://www.diva-project.org/") and [[COLOR="Blue"]Kdenlive[/COLOR]]("http://kdenlive.org/").

Just noticed for Kdenlive..>     * Supported input formats
      **png, jpeg, gif** (non animated), svg, **mp3**, vorbis, wav, flash, mpeg, avi, dv, wmv, ... You can even insert another Kdenlive project in the timeline!
    * Firewire capture
      A dv firewire capture monitor has also been added.
    * Supported export formats
      dv, avi, mpeg, flash, wav, vorbis, mp3, quicktime, realvideo, png Export is now non blocking, you can continue working while exporting
    *[B] DVD wizard
      A basic DVD wizard allows you to burn your movie to a dvd, with a simple title[/B]
    * Project management
      Your project clips can now be arranged in folders.
    * Timeline
      Many new keyboard shortcuts have been added for easier navigation. You can copy and paste clips. Magnetic guides have been added, as well as virtual clips that allow you to create "clones" of a zone. You can insert commented markers in clips, there is a new autoscroll while playing feature, and many more.
    * Video effects
      Brightness, Charcoal, Gamma, Greyscale, Invert, Mirror, Obscure, Sepia, Speed, Stroboscope, Freeze
    * Audio effects
      Mute, Volume, Declipper, Vinyl, Limiter, Equalizer, Phaser, Pitch Scaler, Pitch Shifter, Rate Scaler, Reverb, Room Reverb
    * Transitions
      Crossfade, Push, Picture in Picture, Luma Wipe.
    * Languages
      Thanks to our translation team, Kdenlive is available in english, french, german and spanish


---

### Post by ridgeland on 2007-06-25
I created my notes file in OpenOffice then saved a copy as html and put it on a web-page:
[http://www.davidandjoyce.net/help_pages/dvd_making_videos.html](http://www.davidandjoyce.net/help_pages/dvd_making_videos.html)

Comments and feedback are welcome.
A better approach and instructions would be very welcome.

Below william_nbg told us of mandvd.  This worked so much better that I changed my approach.  I update the above web page on August 19, 2007.  Now there is a link to the *.vob to see the slideshow in Firefox and also a link to an *.iso that you can download, burn to a DVD and test in your TV's DVD player.

---

### Post by Dragonbite on 2007-06-25
This should be submitted to the Ubuntu Studio project so that not only can they see what people want, but HOW and WHY these programs can be used!

I'm going to read this more carefully when I'm home (and probably fool around with formatting, but I'm just weird that way.. I'll send anything I come up with).

---

### Post by GMU_DodgyHodgy on 2007-06-26
Wow! !  I had to go on a business trip for a couple of days - now i have to catch up with all the responses.
these look good and I will give it a shot!

Thanks all!

---

### Post by GMU_DodgyHodgy on 2007-07-01
First I have to sat I love all the help I have received on these boards.

I had some success myself.  I actually was able to use KDenLive to start adding my photos, mpeg video, and music to make a DvD.  All in one step.  

I tried Avidemux - however, I could not import an mp3 or any other audio file.  I did some research and found this to be the case. 

KDenLive is the one application I have found to be closest to Windows Movie Maker - but with more functionality. 

It is easy to import all the elements for your movie into a palette, add them to your timeline and then create your movie. 

It works like a charm.  I just wish it wasn't KDE based.  But oh well. 

Cheers!

---

### Post by Dragonbite on 2007-07-02
> **GMU_DodgyHodgy said:**
> First I have to sat I love all the help I have received on these boards.

I had some success myself.  I actually was able to use KDenLive to start adding my photos, mpeg video, and music to make a DvD.  All in one step.  

I tried Avidemux - however, I could not import an mp3 or any other audio file.  I did some research and found this to be the case. 

KDenLive is the one application I have found to be closest to Windows Movie Maker - but with more functionality. 

It is easy to import all the elements for your movie into a palette, add them to your timeline and then create your movie. 

It works like a charm.  I just wish it wasn't KDE based.  But oh well. 

Cheers!I don't see it in the repository, so you have to install it manually or it is part of a meta-package?

That's the first "review" (opinion) on kdenlive I've read.  Now I'm more tempted to give it a try.

The only "darn it" is that it is KDE-based.  Although I forgot, there is one for Gnome called [[COLOR="Blue"]PiTiVi[/COLOR]]("http://www.pitivi.org/wiki/Main_Page"). It is currently at version 0.10.3.

---

### Post by GMU_DodgyHodgy on 2007-07-02
> **Dragonbite said:**
> I don't see it in the repository, so you have to install it manually or it is part of a meta-package?

That's the first "review" (opinion) on kdenlive I've read.  Now I'm more tempted to give it a try.

The only "darn it" is that it is KDE-based.  Although I forgot, there is one for Gnome called [[COLOR="Blue"]PiTiVi[/COLOR]]("http://www.pitivi.org/wiki/Main_Page"). It is currently at version 0.10.3.

Dragonbite - Its easy to install they have a debian package the self installed on my box. 

It is pretty intuitive.  

I tried PiTiVi and putting thingstogether was easy there to. However you cannot save your work to a file.  

I first put my photos together in an MPeg movie using DigiKam (another KDE app) and then imported this into KDenlive where I added some additional fotos with titles  and comments etc.  Then I added music and compiled a .VOB drive.  

I was then able to import photos individually and start a movie from there eliminating the need for DigiKam.  

I like how KDenLive works and it can do it all in one session.   It is worth a try.

---

### Post by ridgeland on 2007-07-02
GMU_DodgyHodgy,
Glad it worked for you.
I cannot find a way to get the download.   I chased after:
[http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing](http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing) (from kdenlive.org)
but got nowhere.
I tried three approaches.
[http://ubuntuforums.org/showthread.php?t=322916](http://ubuntuforums.org/showthread.php?t=322916)
offered two approaches both lead to errors.
I tried adding the deb for sid from wikibooks then kdenlive shows up but when it tries to install it talks of missing dependencies for libmlt or something.  J'ai meme essaye le francaise...  rien.

I even searched in Fedora7 and StudioUbuntu -- no kdenlive.

So where and how did you get a working copy?  Links please.  
"they have a debian package"  who day?
Thanks.

---

### Post by GMU_DodgyHodgy on 2007-07-02
> **ridgeland said:**
> GMU_DodgyHodgy,
Glad it worked for you.
I cannot find a way to get the download.   I chased after:
[http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing](http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing) (from kdenlive.org)
but got nowhere.
I tried three approaches.
[http://ubuntuforums.org/showthread.php?t=322916](http://ubuntuforums.org/showthread.php?t=322916)
offered two approaches both lead to errors.
I tried adding the deb for sid from wikibooks then kdenlive shows up but when it tries to install it talks of missing dependencies for libmlt or something.  J'ai meme essaye le francaise...  rien.

I even searched in Fedora7 and StudioUbuntu -- no kdenlive.

So where and how did you get a working copy?  Links please.  
"they have a debian package"  who day?
Thanks.

Ridgeland - Try the link beliow:

[http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing#Ubuntu](http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing#Ubuntu)

There is a link for an Ubuntu on the page:

Ubuntu

An installation guide (in French) exists on ubuntu-fr documentation site. Ubuntu Edgy Eft 6.10 users may download deb files with gpg signatures (key available from Kdenlive web site)** compressed into one zip file** at [1] or [2]. An APT repository containing svn builds of kdenlive is available at Treviño's Repository

[edit] 

Hope this helps - kDenlive works great and does alot of the things I was looking to do with my photos and home movies in one package.

---

### Post by ridgeland on 2007-07-03
GMU_DodgyHodgy,
Thanks for the detail.
Unfortunately that is one of the efforts I had already made and got errors.
That means I have to solve the errors I'm getting.  I had hoped for an easy install.
I'll post back results.

Comment about Avidemux not loading mp3s.  I found that it would not load my mp3's with album art in the Tags.  I opened the mp3 with Audacity, saved it again as an mp3 with no tag info and then Avidemux could accept it.  This may or may not have been the problem you encountered.

---

### Post by GMU_DodgyHodgy on 2007-07-03
> **ridgeland said:**
> GMU_DodgyHodgy,
Thanks for the detail.
Unfortunately that is one of the efforts I had already made and got errors.
That means I have to solve the errors I'm getting.  I had hoped for an easy install.
I'll post back results.

Comment about Avidemux not loading mp3s.  I found that it would not load my mp3's with album art in the Tags.  I opened the mp3 with Audacity, saved it again as an mp3 with no tag info and then Avidemux could accept it.  This may or may not have been the problem you encountered.


Ridgeland - My apologies, I did not know you had already tried that root.  Please post your errors - because the package auto-installed for me.  I did not need to get my hands dirty.  I will try your path to load the MP3 without the album art.  Sounds like it might work.

---

### Post by ridgeland on 2007-07-03
What a can of worms.... dependency hell.
But I finally got it loaded.  I used a variation on the ubuntu-fr instructions.
Verify in synaptics:
Liste des libraires requises
      SDL : libsdl-image1.2
      libsamplerate : libsamplerate0
      ogg : libogg0
      vorbis : libvorbis0a
      libdv : libdv4
      libjack : libjack0.100.0-0
      sox : sox
      libxml2 : libxml2
      ladspa: ladspa-sdk
      avformat: libavformat0d
      (optionnel : libquicktime et theora : libquicktime0 libtheora0)
I had them all even the optionnel ones.
Download a zip file:
Téléchargement kdenlive_mlt_ubuntu.zip
I downloaded to '/Data/Software/Sound and Video/Kdenlive' (common ground for other OSs)
But copied the zip over to /opt/Kdenlive to install it (local OS only)
The next steps on ubuntu-fr did not work for me.  Lots of mess.
What did work is going to Nautilus to /opt/Kdenlive and double clicking on the zip to unzip it. Delete the *.sig files (why I don't know but ubuntu-fr did).  Then one by one double click on the deb and install them.  I did the sequence of mlt_cvs, then mlt++, then kdenlive_mlt_ubuntu.  I think sequence will matter.  Each install was happy.  Now Kdenlive is on the menu and loads.
I had no trouble creating a slideshow but have not yet found how to add a sound clip.
I get one clip for the audio which plays sound.  One clip for the slide show (needs tweaked) but I don't see how to combine the two.
Any pointers?

---

### Post by ridgeland on 2007-07-03
I found the manual via Jason Wood's homepage:
[http://www.uchian.pwp.blueyonder.co.uk/kdenlive/documentation/handbook/en/index.html](http://www.uchian.pwp.blueyonder.co.uk/kdenlive/documentation/handbook/en/index.html)

OK - the steps were to make the slideshow, open the audio file, drag each down to a time-line 0, 1 then export the group.  Then in Nautilus open the exported file and it plays - slideshow with mp3 in my case.

---

### Post by william_nbg on 2007-07-11
I think the best and easiest app for slide shows with music and effects is:

mandvd

you'll find a deb at the "getdeb" site.

---

### Post by ridgeland on 2007-07-13
Thanks william_nbg.
mandvd was very easy to download from [www.getdeb.net](www.getdeb.net) and install.
Very easy to pick a folder of slides and an mp3.  Easy transisition selection.
This is the easiest I've tried.
I didn't test to a TV DVD player yet.   DeVeDe was easy so I'm not concerned.

---

### Post by Ubuntiac on 2007-07-14
> **william_nbg said:**
> I think the best and easiest app for slide shows with music and effects is:

mandvd

you'll find a deb at the "getdeb" site.

I'd also recommend ManSlide (by the same person). It needs to be installed from source unfortunately, but is extremely sexy and made purely for creating slideshows. Take a look at the photos / download it here:

[http://kde-apps.org/content/show.php/Manslide?content=52227](http://kde-apps.org/content/show.php/Manslide?content=52227)

(parle vous francais?) ;-)

---

### Post by tinkietruck on 2007-08-18
> **ridgeland said:**
> :) Success, I just watched my slideshow with music on my TV :)
I used
qdvdauthor
Avidemux
DeVeDe

With qdvdauthor I created a slideshow (59 photos from our wedding in 1986)  Then with Avidemux I added an mp3 (some Brahms).  Then with DeVeDe I created a Video DVD iso (NTSC).  Then with Nautilus I just said burn to CD (DVD actually).   Popped the DVD in the TV's DVD player and watched my 8 minute slide show with music.

If anyone wants the detail of all the steps it took, just ask.  When I fight an issue I tend to create an instruction sheet for myself to use a year from now when I've forgotten it all.

If anyone can explain the process another way please post the tools and steps.


Do you have a DVD  burner or just a cd burner? What kind of discs did you use?  I have some DVD-R discs.  I do have access to a DVD burner if necessary to create dvd's to play in any dvd player.  I want all of my family members to be able to watch the dvd if I send it to them for Christmas of all my pictures.  

It is great that you gave detailed instructions on how to use these programs to create a dvd movie.  

Thanks,
Brandy

---

### Post by dad311 on 2007-08-18
I also created a slide show using the following programs.

kdenlive 0.5  -  I like the slideshow feature in kdenlive, but there is an audio bug in version 0.5.  So I created a slideshow with no audio.

cinerlerra - Imported my side show.  Added the audio, with special effects (fade in/out, etc) to match the slides.  Rendered the movie to a dvd format.

qdvdauthor  - used to author the DVD.  Created menus, backgrounds, etc.

Brasero - used to burn the DVD.

glabels - used to create a label for the DVD.

---

### Post by ridgeland on 2007-08-18
I have a combo DVD and CD burner that came with this Dell.
I had to go look.  I used a DVD-RW.  TV-DVDs can be very picky.  Read your manual and see which DVD and/or CD types are acceptable.  Earlier, back when I used Windows, I burned a DVD that played fine on my TV-DVD player but was refused by my friend's TV-DVD player.  Newer TV-DVD players may work with CD-R or CD-RW, again you need to start by reading the specs of your player.  I've found that simple folders of jpegs play in most any TV-DVD player, but thats without the sound track.

---

