---
title: "MP3 and CDs"
date: 2008-06-02
forum: Multimedia Software
---

### Post by chejose on 2008-06-02
I have a list of MP3 files that I would like to make a CD of...music.

It must be simple to do since I could not find anyone in the forum that asked how to do it. 

If I try K3b, it does not accept the MP3 format for music CDs, and if I make a data CD there is no way to make it play beyond one piece at a time.

There must be a good explanation as to how to do it somewhere, but need help in finding it. The "comprehensive" list above was not much help.

I am running Ubuntu 8.10, Gnome. Have some experience with Linux, but not in this area.

Thanks for any help.

José

---

### Post by ron999 on 2008-06-02
Hi
K3b will do the job. But you have to enable mp3 support first.
There's a link here that might help you:-[http://linuxappfinder.com/blog/howto_enable_mp3_support_for_k3b]("http://linuxappfinder.com/blog/howto_enable_mp3_support_for_k3b")

---

### Post by chejose on 2008-06-02
I followed up the link you sent, and did as suggested. The solution was to add a package called libk3b2-mp3. Apt-get said that it was no longer available, and suggested a substitute. So I installed that, but no results.

What leaves me wondering is that when K3b says a file cannot be dropped onto a music CD, in the "explanation" it says that it is in the .m3u format! In all directories these particular files are listed as mp3 (and I downloaded mp3). Why K3b would list it as different, is another mystery for me.

So... will have to keep this going and try again.

Thanks, ron999

---

### Post by Pieter Kunnen on 2008-06-02
> **chejose said:**
> I have a list of MP3 files that I would like to make a CD of...music.

It must be simple to do since I could not find anyone in the forum that asked how to do it. 

If I try K3b, it does not accept the MP3 format for music CDs, and if I make a data CD there is no way to make it play beyond one piece at a time.

There must be a good explanation as to how to do it somewhere, but need help in finding it. The "comprehensive" list above was not much help.

I am running Ubuntu 8.10, Gnome. Have some experience with Linux, but not in this area.

Thanks for any help.

José

José

I have in stalled Nero Linux Version 3. This makes the creation of MP3 and creation of CDA (normal CD format) files very simple.

It's not for free due to the Frauenfelder MP3 converters. 

Pieter

---

### Post by chejose on 2008-06-02
Pieter

Thanks for the suggestion, though I hope I can do the job in the "normal" Ubuntu/linux system..

After all, it shouldn't THAT hard!

José

---

### Post by gandaran on 2008-06-02
how about brasero. have you tried it?

---

### Post by chejose on 2008-06-02
Yes, but when I pass a group of files to the right side ( I suppose that is to burn them. They all show up, then one by one disappear. And the indicator below continues with 0 kb.

José

---

### Post by gandaran on 2008-06-02
> **chejose said:**
> Yes, but when I pass a group of files to the right side ( I suppose that is to burn them. They all show up, then one by one disappear. And the indicator below continues with 0 kb.

José
 
just tried out brasero burning a cd and it works fine!
have you installed all the gstreamer plugins in synaptic?

---

### Post by chejose on 2008-06-03
Back to the problem on a new day.

I checked the gstreamer plugins and there are some installed. But the Synaptic package manager has a couple of dozen at least, and I don't have much confidence in installing them all... afraid that I might break something. :(

But there was one that was specific for MP3 and I installed that one, but still no results.

Would there be some specific ones that should be installed to make this work?

José

---

### Post by chejose on 2008-06-03
To make things worse, When I started my PC today I found that I cannot play mp3 files that are downloaded. The Firefox plugin will play streaming mp3 though.

So things seem to get worse instead of better.

Hopefully someone out there...

Jos´e

---

### Post by Dave67 on 2008-06-03
If you install lame this should fix things. MP3 is an non free codec so it will never be installed on default. Any Linux distribution I ever used I had to install lame, what you installed already is fine. do a search on your package manager and install it. I will watch your post since I have not used Ubuntu in sometime. k3b will use the lame I have it installed on my distribution other wise i would not be able to play mp3 music.

I noticed that some are getting M3u I believe this is the play list format for k3b but since k3b does not know what MP3 is until you install lame than it will default to a known file type. 

:)

---

### Post by chejose on 2008-06-03
I finally got back my PC, and will have to leave again for later.

But I installed lame, with no difference. When I try to load a mp3 file into K3b I get a message "Problem encountered..." and the details say not compatible format.

So back to it later...

José

---

### Post by gandaran on 2008-06-04
> **chejose said:**
> Back to the problem on a new day.

I checked the gstreamer plugins and there are some installed. But the Synaptic package manager has a couple of dozen at least, and I don't have much confidence in installing them all... afraid that I might break something. :(

But there was one that was specific for MP3 and I installed that one, but still no results.

Would there be some specific ones that should be installed to make this work?

José

José
    here's a list of gstreamer plugins you must have installed, these are fundamental, especially the multiverse ones.

gstreamer0-10-alsa
gstreamer0-10-ffmpeg
gstreamer0-10-plugins-bad
gstreamer0-10-plugins-bad-multiverse
gstreamer0-10-plugins-base
gstreamer0-10-plugins-good
gstreamer0-10-plugins-ugly 
gstreamer0-10-plugins-ugly-multiverse

and I also recommend installing others, won't break anything.

---

### Post by chejose on 2008-06-04
Thanks again for getting back to me... and good morning!

All the plugins you recommend were already installed except for the two miltiverse ones which I then installed.

I already have lame installed.

But K3b still refuses the files and I have not been able to play the ones I downloaded. I could before, but I apparently messed up something and none of the applications I now have will play them.

And again, thanks for your patience.

José

---

### Post by soxs on 2008-06-04
try:
```
sudo apt-get install vlc vlc-plugin-alsa vlc-plugin-pulse vlc-plugin-sdl vlc-plugin-esd
```
now try to play any of your mp3 files with vlc (which should do fine playing mp3s anytime)
tell us about the error-msgs you get.
May it be possible, your .mp3 files being corrupted?

The final approach would be to try to convert the mp3 files via oggconvert (```
sudo apt-get install oggconvert
```) in .ogg files and check wether they work, so we can rule out it being malfunctioning burning utlities or the lack of codecs.

---

### Post by chejose on 2008-06-04
I have been learning Linux for a good year now, but this is the first time I have found such a ilogical problem.

The MP3 files must be OK since a few days ago I could play them with no problem.

I installed the plugins as you suggested, but if I select play a file in VLC it appears for a moment in the list to play, then is gone.

K3b still says that the files are not compatible.

If no other solution comes up, I will try your conversion suggestion... no time right now.  :)


thanks for taking it up.

José

---

### Post by soxs on 2008-06-04
Did you look what sound environemt ubuntu uses (don't leave it with autodetect) and make sure vlc has the same audio autput.
Did you try any other files to play? Some vids and/or other sound files? (try it all with vlc)

---

### Post by chejose on 2008-06-04
OK... I think I have finally found the problem, though not the answer.

Music CDs play normally, and I found a MP3 file that someone had sent me and it played with no problem.

But examining things closer, it turns out that the "MP3" files I downloaded say MP3 in the file lists, but they are actually .M3U files.

So the problem is in the format of the files instead of Ubuntu. So the problem has shifted to a different level.

Any suggestions this time?

And thanks,

José

---

### Post by chejose on 2008-06-04
An extra note.

I just tried out K3b with that one "real" mp3 that I found, and it accepted it no problem.

So in reality, this is a new question:

How to use M3U files... play and record to CD.

Thanks for those who have helped me clear things up.

José

---

### Post by chejose on 2008-06-04
So I looked up M3U in Google and found out that they are not music files, but simply links to play the music listed. So it is impossible to record them to a CD, as far as I can see.

All that fuss about nothing! I am very disillusioned with the site I downloaded the files from... even paid for them!

But that is the way one learns... at times the hard way.

So again, thanks to you who tried to help a helpless problem.

José

---

### Post by soxs on 2008-06-04
lol, i overread that part and thought you meant mp3s.
m3u files are (more or less) simple playlists

---

