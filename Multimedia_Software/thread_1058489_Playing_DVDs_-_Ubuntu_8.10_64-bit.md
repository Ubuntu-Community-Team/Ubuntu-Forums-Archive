---
title: "Playing DVDs - Ubuntu 8.10 64-bit"
date: 2009-02-02
forum: Multimedia Software
---

### Post by rockinstlouis on 2009-02-02
Greetings.. I'm currently using libdvdcss2 to play DVD movies with Totem.. but it seems like it's not the best quality.. occasionally i see image distortion and horizontal lines when fast moving images go past the screen..

Is there anything better out there?

---

### Post by Crafty Kisses on 2009-02-02
Have you installed this package?
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by rockinstlouis on 2009-02-04
I have.. and it does work...  I guess I was hoping for video codecs that do a much better job.. 

Recently I did confirm that it's not an issue relating to Totem.. MPlayer does the same thing.. even tried using the different codecs in it's options.. didn't help..

I think I SOL on this..  looks like it's back to my TV

Unless there is a commercial product out there.. I wouldn't mind purchasing one.. just as long as it's not dreadfully expensive..

---

### Post by mc4man on 2009-02-04
The horizontal lines are interlacing artifacts, enable deinterlacing in your player, (mplayer has much better ones than totem

You may want to add the smplayer ppa to your sources and install a recent, updated mplayer and a front end for it, smplayer, there should be about 6 choices for deinterlacing (and a much better player overall

[https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa)

Edit; plus smplayer is activly supported by the developer in this forum, any problems just start a thread - smplayer .... and you'll get a response

---

### Post by rockinstlouis on 2009-02-06
I will give that a shot.. Recently I found out that all fast moving objects are doing that.. I tested that when I found out my screensavers are doing that..

I think I need to investigate options on my video driver..

---

### Post by gandaran on 2009-02-06
> **rockinstlouis said:**
> I have.. and it does work...  I guess I was hoping for video codecs that do a much better job.. 

Recently I did confirm that it's not an issue relating to Totem.. MPlayer does the same thing.. even tried using the different codecs in it's options.. didn't help..

I think I SOL on this..  looks like it's back to my TV

Unless there is a commercial product out there.. I wouldn't mind purchasing one.. just as long as it's not dreadfully expensive..
try changing the video output/driver to x11 or xv in mplayer>preferences>video tab, for totem type **gstreamer-properties** in terminal

---

### Post by simonfogliato on 2009-03-16
I also have this exact same issue! I have tried to play DVD's using VNC, MPlayer, etc in combination with using info from medibuntu... They all have the same issue when the DVD has some fast movement during play. I get these strange horizontal lines during the movie. They are very close together but to a movie buff it is extremely annoying! I have spent much time but I still cant fix this.

My only idea is to just buy PowerDVD for Linux.

Please any info would help!

---

### Post by Neo_The_User on 2009-03-16
[http://ubuntuforums.org/showthread.php?p=6884756#post6884756](http://ubuntuforums.org/showthread.php?p=6884756#post6884756)

^My post.

You might have to change "AGPSize" "8" to "4" if your GPU is a 4X AGP GPU.

Also...

[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

and

[https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats](https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats)

If you need further enhancement, let me know and I will give you some more xorg.conf suggestions for tweaking.

---

### Post by simonfogliato on 2009-03-17
Yeah I am still a little stuck. I have followed the Medibuntu instructions to the letter by adding the repository + key and installed libdvdcss2. I mean I can play DVD's just fine...

I have tried this on 3 PC's one is running my nvidia 8600GTSoc that is a PC-Express card. So your AGP comment isn't relevant.

---

### Post by mc4man on 2009-03-17
I did notice on 8.10 a slight quality issue somewhat similar do what you see as compared to 8.04 when playing dvd's. (all progressive, so not related to interlaced content

In 8.10 I was using the 177 nvidia driver, as soon as I started using 180.29 the 'issues' disappeared.

---

### Post by simonfogliato on 2009-03-18
My issue has been SOLVED! I did exactly what you guys said and just used the latest nvidia driver and bingo it was crystal clear! This was one of those things where I overcomplicated things.

libdvdcss2 + latest nvidia driver = perfect dvd play

Thank you very much for all your help.

---

### Post by kumoshk on 2009-03-30
> **simonfogliato said:**
> My only idea is to just buy PowerDVD for Linux.

Please any info would help!

I know your problem is solved, but if you're concerned about the DMCA (Digital Millennium Copyright Act) and you live in the United States, the following should still be useful for you as far as encrypted DVDs are concerned:

I bought PowerDVD before I was using a 64-bit OS. I tried the Intrepid version and it worked, most of the time. It didn't handle skips very well (the program sometimes freezes when the skips are bad). I might recommend waiting until the Fluendo DVD player comes out (hopefully it'll be out around April&#8212;that's what they're thinking, I think)&#8212;it will work in 64 bit, and it's less expensive (plus it likely won't have the issue with skips).

Anyway, I couldn't get PowerDVD to work on my 64-bit OS&#8212;so, guess what I did? I put Ubuntu 32 bit on a USB drive and I just use that to watch my movies. It works fine and I still have my 64 bit OS (except for while I'm watching movies). I'm using the Intrepid install on the Jaunty beta, though&#8212;I think it works better there, actually&#8212;probably due to the newer driver). You don't have to do anything special to set up a USB install with Jaunty. Just make a root partition on it (don't import any users and such) and click advanced to set the boot loader to be on the USB drive (not the partition). That's it. Oh, and make sure you have the nvidia driver (and a card that works with it)&#8212;the Fluendo player won't require proprietary drivers, just so you know.

The video in PowerDVD for Linux works well enough. The audio works reasonably well, although it sounds better when louder sounds are present than when things are quiet on my laptop.

---

### Post by simonfogliato on 2009-04-14
Eureka!!! I have finally solved my stupid line problem and learned a few things about DVDs... Ubuntu/Video Drivers/libdvdcss2 were all working just fine, the only issue was **interlacing**.

I could type an essay on the topic now but to better explain interlacing please read:
       - [http://tldp.org/HOWTO/DVD-Playback-HOWTO/usage.html](http://tldp.org/HOWTO/DVD-Playback-HOWTO/usage.html)

The solution is **deinterlacing**, it is the process of converting source material that contains alternating half-pictures to a computer screen that displays a full picture at a time. Aka fixing interlaced DVD video. The following link explains everything you need to know on how to fix the problem and apply your custom deinterlacing technique.
       - [http://tldp.org/HOWTO/DVD-Playback-HOWTO/usage.html](http://tldp.org/HOWTO/DVD-Playback-HOWTO/usage.html)

Most all players support deinterlacing to correct your interlaced video. For example open up a DVD using VLC media player and select - "Video > Deinterlace > Linear". Bingo problem solved...

---

