---
title: "Another Realtek/Nvidia problem from a noob"
date: 2009-05-21
forum: Multimedia Software
---

### Post by mirnander on 2009-05-21
My first question for the community.

I hope this is the right section to post this thread....

I am completely new to ubuntu and I've had some problems with my realtek driver and invidia sound card. At first after install, the sound was fine. (I think... System sounds were working. I didn't test playback though.) At any rate, after I installed an update at ubuntu's suggestion, my sound disappeared. :sad:  

I found a little help by googling and found that typing "alsamixer" in the terminal would bring up some hidden options. By tweaking some of those controls, I got sound but with some serious buffering issues.

My sound pops and clicks as if the cpu is overloaded, but my cpu is never over %50 when this happens. I'm also getting problems with getting the proper playback speed when first playing an audio file.

Here's what I've got: 

Card: HDA NVidia                                                             &#9474;
Chip: Realtek ALC880    
Ubuntu jaunty 9.04 - updated last night
ext4 file system (that's what I chose on install... a mistake perhaps?)

Please lemme know if more info is in order.

I'm getting sound working under the "advanced linux sound architecture" and the "HDA analogue Nvidia ALC880 Analogue," setting in the sound dialogue under system preferences, but still.... buffering issues abound. 

(At least I think this is a buffering issue. I am a noob to ubuntu after all. I have, however, been home recording for a few years now, and the sounds I am hearing under normal playing conditions sound a lot like what I would hear when I overloaded my cpu when recording music under windows.)

I read something about this possibly being an issue with a kernel update, but I've got nothing to roll back to on boot up, so dunno...

I really want to get ubuntu fully working for me. Not only am I sick of windows, but I also want to spread the word about open source.... gotta get it working first though so I can show it off and help out my friends who are thinking about making the switch themselves...

Thanks in advance :)

---

### Post by mirnander on 2009-05-22
Well... after school and some studying today I went back to hunting for a solution to these audio issues and guess what? I found it!! Woot!

So if you are having problems with audio skipping, clipping, popping, buffering, music playing at random speeds, etc., on you install of ubuntu jaunty 9.04, then follow this post to the letter: [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

(I hope I added enough terms in there to help you find this post with google a little quicker than I was able to.) 

There was only a couple issues I had after following the author's instructions. I had to disable the gnome volume controls for pulse audio (which is something I had enabled before reading markbuntu's tut.) 

I also was hearing a lot of hiss and air, sort of like tape noise, after following the instructions. I think this is probably because I had been fiddling with the PCM levels by running 'alsamixer' from the terminal. It took me a second to remember that I had done changed that in my first attempts to get the sound going in the first place.

So... if youv'e got no sound I think you first need to make sure that you have PCM up to a decent level (mine needed to be turned up all the way.) If you've got random play back speeds and pops and clicks, then you need to read this: [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

Don't be scared.... there are no command lines to deal with. You're just going to use a built in utility that comes with ubuntu to download and install some missing utilities, and then you will need open up your sound controls to let ubuntu know what's changed and how to behave. It's not difficult, just time consuming.

---

