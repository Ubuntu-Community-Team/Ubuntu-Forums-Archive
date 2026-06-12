---
title: "Copying VHS to DVD"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by tinker123 on 2006-12-31
Hi;

I'm running Ubuntu 6.10 (Edgy), with gnome.   I have a TV card in my PC and I have a VCR attached to that via an RFC modulator.   I am able to watch VHS tapes using kdetv and zappingtv.

I would like to copy content off of some old VHS tapes and burn them onto dvds.  In the process I would like to trim some of the content out of the VHS and put the content of more than one VHS tape onto a single dvd.   If I can do that I would also like to make menus ( simple text based choices ).

I have no idea where to start.

What is the easiest software for these tasks?   

I would like to be able to play the resulting DVDs in my computer,  plus on televisions hooked up to DVD players.

Thanks in advance for any info

---

### Post by pseudonym on 2006-12-31
Hi,

If your card uses the bttv driver, one possibility for a recording utility is [xawtv]("http://linux.bytesex.org/xawtv/"). It's not overly fancy, but will allow you to output to both .avi and .mpeg, I think.

A nice little editing suite is [Avidemux]("http://avidemux.sourceforge.net/"), which is easy to use and has plenty of features.

For DVD authoring, I use [DVD Styler]("http://www.dvdstyler.de/"), but other possibilities are DeVeDe, qdvdauthor, and kmediafactory (these last three are in the Ubuntu repositories).

If you want get down and dirty with the command line, mencoder or ffmpeg are good options, but they require you to do a lot of reading first to use them effectively.

FYI, a good place to start an app search is by using the search function in synaptic. For all things video capturing/editing you should also check out the  Linux section of [Doom9.net]("http://forum.doom9.org/forumdisplay.php?f=63") . There are a few good guides and a list of useful apps there which you should find helpful. Also, for things hardware related, [Linux TV]("http://www.linuxtv.org/") is the place to go.

HTH :)

---

### Post by tinker123 on 2006-12-31
I haven't been able to get xawtv to work.

I haven't been able to save the preferences ( or see all of them in the dialog box - scrolls off screen ).    I think it may work if I can do that and set a frequency for my VCR channel ( 3 ).

Any idea how I can do that?

THanks

---

### Post by pseudonym on 2006-12-31
> **tinker123 said:**
> I haven't been able to save the preferences ( or see all of them in the dialog box - scrolls off screen ).
On screens like that you should be able to just arrow down to read the rest of the page. It looks like you can't, but you can :)

---

### Post by tinker123 on 2007-01-01
> **pseudonym said:**
> On screens like that you should be able to just arrow down to read the rest of the page. It looks like you can't, but you can :)

That sounds cool.   I tried using my arrow keys on that dialog box, but it didn't help.

---

### Post by gn2 on 2007-01-01
Eighteen months ago I started trying to do what you are attempting now.

Twelve months ago I gave up and bought an LG stand-alone DVD Recorder.

Now if I want to copy footage from VHS to DVD it's very easy indeed, the DVD Recorder will even edit bits out as well. (and record TV!)

Straightforward and very, very simple. :)

---

### Post by pseudonym on 2007-01-01
> **tinker123 said:**
> That sounds cool.   I tried using my arrow keys on that dialog box, but it didn't help.
In that case you can try doing it from a console outside of X. Just press Ctrl+Alt+F2 to get to one. Log in, and you'll have the full screen available to you (I'm 99.9% sure this is where your problem lies).

Now do what you need to do with xawtv and when finished type 'exit' to log this console off. Then press Ctrl+Alt+F7 to get back to X.

---

### Post by tagra123 on 2007-01-01
I use mythtv for exactly this purpose.

If you dont need all the extra features its fairly easy to get working now. I wont say that installation is completely painless but it makes verry good recordings. After the shows are recorded you can edit / cut extra stuff out and then use nuvexport to make them into mpg file to put on dvd.

If i'm not mistaken you can use mencoder to capture the video and sound without using any extra programs if you didnt want to use mythtv.

I use it for tv recording too now.

Google for mythtv ubuntu

---

### Post by tinker123 on 2007-01-01
Is there any reason why I can't just synaptic to install myth tv for me?

---

### Post by tagra123 on 2007-01-01
> **tinker123 said:**
> Is there any reason why I can't just synaptic to install myth tv for me?

Synaptic might do it all now.

You'll still need to run the backend setup to specify your capture card, etc...  I think but am not sure, that it may even set up mysql now too  Getting mysql took a little time for me using breezy.

---

### Post by tinker123 on 2007-01-01
I will give it a shot.  Mythtv looks friendlier than xawtv

---

### Post by lcohen999 on 2007-05-11
I know this is an old thread, but I am wondering

I am looking to convert about 50 VHS movies that I own to DVD.

My concern is how to strip out the macrovision from these VHS tapes.  Does Ubuntu do that, (I have an ATI All-In-Wonder USB 2.0 card) or what do I need

Thanks!

---

### Post by tagra123 on 2007-05-11
> **lcohen999 said:**
> I know this is an old thread, but I am wondering

I am looking to convert about 50 VHS movies that I own to DVD.

My concern is how to strip out the macrovision from these VHS tapes.  Does Ubuntu do that, (I have an ATI All-In-Wonder USB 2.0 card) or what do I need

Thanks!


I haven't had any issues with the recordings I've made. Video cable from VCR or DVD Player to Capture card. Sound cable to Input Jack on Audio card and no problems on this end. Good quality backup recordings too. I think it gets ignored during the recording. No wavey lines or odd colors on the recording I've made.

If you end up using mythtv you wouldnt need to set up a zap2it account or mess with the channels, etc.  Just get the input from the AV jacks.

---

