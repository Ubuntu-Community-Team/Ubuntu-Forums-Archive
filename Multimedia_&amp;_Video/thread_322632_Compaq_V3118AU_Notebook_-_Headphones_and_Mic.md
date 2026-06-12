---
title: "Compaq V3118AU Notebook - Headphones and Mic"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by ozPATT on 2006-12-20
Hi people, 

I have just read through [this]("http://ubuntuforums.org/showthread.php?t=206606&highlight=microphone+headphone") post, regarding microphone issues, and tried the suggestions, but I still have no joy. 

I am using a compaq v3118AU notbook, and it has jacks for headphones and mic on the front. When i plug headphones in, it makes no difference. The sound still comes out from the main speakers. 

When i plug a mic in, nothing records. I have built in mics in the laptop, and they dont record either. 

When i double click on the speaker to go to th sound settings, I only have 2 sliders, for volume (master and pcm) and one under capture which shows a microphone which I have made sure isnt muted. 

Could someone please explain how I can get this to work?

Many Thanks

Patrick

---

### Post by ozPATT on 2006-12-21
anyone.... anyone...

---

### Post by aaron552 on 2007-01-01
I have the same: Presario 3118AU without working mics or headphone socket. ](*,) 

It seems noone knows anything about this.

---

### Post by ozPATT on 2007-01-11
well i am now on the IRC channels trying to find out if anyone can help.. you are right though, noone seems to know about it :(

woohoo, well, I think I am one step closer to the solution. :) Before going on the chat, my gnome-volume-control only had 2 tabs, playback and capture. Playback had master and pcm, capture had capture. 

I was told to run the following:

```
cat /proc/asound/card0/codec#0
```

Then find the first line, the Codec: bit. Mine said Generic 14f1 ID 5045 

So then I was told to edit the following:

```
sudo gedit /etc/modprobe.d/alsa-base
```

And make sure the last line was as follows: 

```
options snd-hda-intel model=14f1
```

So I did that then rebooted. Now, I have an extra tab in alsamixer, called switches, which gives me two options: Front Mic and Microphone.

It still doesnt work, but this is progress I feel. :) If there is anyone who can add to this progress, I would love to hear it, as I am unable to use skype which I need for work until I can fix it... 

Many thanks

Patrick

---

### Post by pixeldotz on 2007-02-26
did you get the issuse sorted out?

i ask only because i just recently bought a compaq c500 and i am having the same issuse with ubuntu.6.10.

---

### Post by jrz on 2007-04-02
I'll just add that we've been working on a compaq v3000 notebook with the same problem and are unable to find any help in solving it, FAQ's, forums, google search, IRC, etc. In our case we're running Ubuntu 6.06. Although Linux has numerous points of assistance, it appears that finding positive results is extremely difficult, and is disheartening when you begin to get responses like 'you should reinstall the OS and see if that helps." This is the primary reason for abandoning Windows, trying to get an OS that will perform all necessary functions without periodic re-installations. If anyone has actually made progress in getting the microphone to work on a Compaq, nvidia, system please point us to where you found genuine assistance. Thanks.

---

### Post by ffarah on 2007-09-26
problem with mic and headphones is alsa-driver.

u've to download latest version and compile it for yourselves.

im not an admin, but i did it.  MIC stil can't get to work, :(


download link  (choose the latest date of driver)

[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/)

PD: i wont give up,  my mics will work sometime!!!!

---

### Post by ffarah on 2007-09-26
sorry, then do this (just in case u dont know what compiling is)

one at a time

```
./configure
sudo make
sudo make install
```

be patient, takes a lil time...

---

### Post by jrz on 2007-09-27
Are some still having this problem? We finally got ours to work after trying more than 6 different drivers. I believe there are 2 things necessary, finding a compatible driver, and the latest ndiswrapper. Recently we found that after applying a kernel update we had to reinstall the driver, but once you learn the steps to get it to work it is less difficult to do it a second or third time.

---

