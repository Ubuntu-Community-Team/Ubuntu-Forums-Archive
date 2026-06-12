---
title: "Amarok won't play mp3s"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Luft on 2007-05-07
I've followed the post above:  Enabling Multimedia in Feisty (HOW-TO) by Adamant1988  

But when I try to play mp3 files I get a pop up asking me if I want to install mp3 support.  If I click the install mp3 support button Amarok hangs.  Other applications like Rhythmbox do play mp3s.

---

### Post by ratbagradio on 2007-05-08
Amarok is worth persevering with because it's  great player. 

When you load Amarok you will be offered a pop up screen to install files for Mp3 playing. Click on the YES or whatever and wait. It takes a while to kick in.

If that doesn't facilitate Mp3 support, as nothing loads, you may need to add some dependencies. But I forget what they were. 

Try [this thread here]("http://ubuntuforums.org/showthread.php?t=428576&highlight=mp3+amarok") as an introduction.

---

### Post by trippinnik on 2007-05-08
Ugh! I am having this problem too.  I don't understand what happened one day I can play all my music files in Amarok, now it says there is now Mp3 support.  I tried reinstalling, purging, i even purged ubuntu-restricted and xine-extracodecs.  I've also seen that amarok is supposed to be able to use other engines.. but I haven't found a way to set them up.  I'm still not sure why gstreamer is being pushed so much.  It can handle Mp3 playback, but video is choppy compared to xine, and streaming from the internet doesn't work... I guess I am going on a tanget, but I am afraid this is because everything wants to depend on gstreamer...  

I did notive that after the purge Amarok still had all my settings, so I hunted down all the stuff I could find related to amarok and audio in the .kde folder and killed it.  It's still rebuilding my collection. Does anyone know how to use gstreamer as the engine instead of xine?

---

### Post by trippinnik on 2007-05-09
> **ratbagradio said:**
> Amarok is worth persevering with because it's  great player. 

When you load Amarok you will be offered a pop up screen to install files for Mp3 playing. Click on the YES or whatever and wait. It takes a while to kick in.

If that doesn't facilitate Mp3 support, as nothing loads, you may need to add some dependencies. But I forget what they were. 

Try [this thread here]("http://ubuntuforums.org/showthread.php?t=428576&highlight=mp3+amarok") as an introduction.

thanks for the link, but something isn't quite right. it just goes to the main forums page.  Seriously though aren't more people having this problem?  I had mp3 support in amarok until a few days ago.  Right now when I make a new playlist a window pops up with a heading mp3 support, but there is not contents to the window and even leaving it on and in focus for an hour it didn't do anything.  When I try to close it I get a not responding force quite dialogue from Gnome.  It also seems that my Xine libraries are installed and working.  I've been able to play video in Totem xine and stream music from mlb site using the totem plugin for firefox.  

and yes I've tried some of the other music players, banshee, exaile and rythmbox.  None of them has really been as complete as amarok.  Does anyone have an other ideas or know of a way to try another Engine with amarok?  I tried installing Helix and looking for amarok-gstreamer but none of that worked either.

---

### Post by paul_banks on 2007-05-11
I'm having a similar problem... mp3s were working fine in Amarok until I installed today's list of recommended auto-updates, which include:

libhal1 0.5.8.1-4ubuntu12 0.5.9-1ubuntu2~feisty1
libhal-storage1 0.5.8.1-4ubuntu12 0.5.9-1ubuntu2~feisty1
hal 0.5.8.1-4ubuntu12 0.5.9-1ubuntu2~feisty1
hal-device-manager 0.5.8.1-4ubuntu12 0.5.9-1ubuntu2~feisty1

After that, Amarok quit playing mp3s. Now, I get a "no suitable demux plugin" error message. I tried re-installing Amarok, but that didn't work, either. VLC still plays mp3s, though...

---

### Post by stchman on 2007-05-11
> **Luft said:**
> I've followed the post above:  Enabling Multimedia in Feisty (HOW-TO) by Adamant1988  

But when I try to play mp3 files I get a pop up asking me if I want to install mp3 support.  If I click the install mp3 support button Amarok hangs.  Other applications like Rhythmbox do play mp3s.

To play mp's with Amarok, install the package libxine1-ffmpeg (which will install libmad0 as well).  This is for Feisty.

I got that from the [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3).

Also, VLC plays MP3s out of the box since it has its own built in decoder.

---

### Post by paul_banks on 2007-05-11
> **stchman said:**
> To play mp's with Amarok, install the package libxine1-ffmpeg (which will install libmad0 as well).  This is for Feisty.

I got that from the [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3).

Also, VLC plays MP3s out of the box since it has its own built in decoder.

Thanks, but I already have libxine1-ffmpeg installed. I tried re-installing it, but Amarok gives me the same error. Again, everything was fine until I installed those update packages...

---

### Post by paul_banks on 2007-05-11
> **trippinnik said:**
> Ugh! I am having this problem too.  I don't understand what happened one day I can play all my music files in Amarok, now it says there is now Mp3 support.  I tried reinstalling, purging, i even purged ubuntu-restricted and xine-extracodecs.  I've also seen that amarok is supposed to be able to use other engines.. but I haven't found a way to set them up.  I'm still not sure why gstreamer is being pushed so much.  It can handle Mp3 playback, but video is choppy compared to xine, and streaming from the internet doesn't work... I guess I am going on a tanget, but I am afraid this is because everything wants to depend on gstreamer...  

I did notive that after the purge Amarok still had all my settings, so I hunted down all the stuff I could find related to amarok and audio in the .kde folder and killed it.  It's still rebuilding my collection. Does anyone know how to use gstreamer as the engine instead of xine?

I solved my lazy Amarok problem by following the steps in the link below... now it's back in action!

[http://linuxfud.wordpress.com/2006/12/03/amarok-suddenly-stops-playing-mp3s/]("http://linuxfud.wordpress.com/2006/12/03/amarok-suddenly-stops-playing-mp3s/")

---

### Post by trippinnik on 2007-05-13
awesome that worked!

---

### Post by HumbleGod on 2007-05-13
I was having a similar problem, and the link that **paul_banks** provided worked for me as well. Thanks!

---

### Post by Carlos Santiago on 2007-06-01
thanks scthman, that was it!
I was having the same problem, and a simple 
```
sudo apt-get install libxine1-ffmpeg
```
solve my problem. And I didnt have to remove anything.

---

### Post by andyr354 on 2008-03-23
> **Carlos Santiago said:**
> thanks scthman, that was it!
I was having the same problem, and a simple 
```
sudo apt-get install libxine1-ffmpeg
```
solve my problem. And I didnt have to remove anything.

Just wanna bump this up.  I really like Amarok, but was about to dump it on my new setup because I could not get the stupid thing to play anything.

Above command is now written in my little tablet.  Thanks!

Andy

---

