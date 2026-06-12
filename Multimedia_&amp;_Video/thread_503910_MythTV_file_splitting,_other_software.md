---
title: "MythTV file splitting, other software?"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by najames on 2007-07-18
I have a AMD x2  MythTV PC with a Hauppauge PVR-150 tuner installed.  I am a seasoned Ubuntu user.  Everything seems to be working fine.  Recording from schedulings works ok.   I have recordings on my 8300HD STB that I want to transfer to a PC because the box is full plus my wife wants to keep some.  I have connected my STB to output recordings from the STB into the PVR-150, XFS file system is beinig used on the PC for recordings.

There does not seem to be a menu button to record live TV, so I am hitting the R key to start.    I found that this method does not work well because it starts recording as soon as I watch the recording, therefore when I was rewinding/setting it up, it was all being recorded.  I figured out how to start the recording clean by deleting all of the temp recording files, start the live TV, and record.  However, when recordings get to about 1.1GB it starts recording to a second file. 

Is there a better way to record "live TV"?   Anyone else have this problem with files splitting?

My wife is IMPATIENT with my MythTV play, so I plan on blowing away the machine tonight and putting Win2000 back on it and use Hauppauge's simple "front end" for now until I get all the recordings off the STB.  Maybe another software like Sage would work better, suggestions??  

I need a simple setup that I can confiure quickly/easily, but  more importantly it has to be easy for the wife to use.  I have too much home remodeling to do, so I have limited time to spend on this.

---

### Post by najames on 2007-07-18
Taps please.  Goodbye Ubuntu MythTV.

Hello WinBlows with 10,000 popup balloons.  Bill Gates get your hands off my shoulders and quit poking me in the butt with that thing.  I am just doing a temp install, and NO I am not buying Vi$ta.

---

### Post by newlinux on 2007-07-18
You can record from a hardware mpeg encoder with the following command

```

cat /dev/video0 > file.mpg

```

replace video0 with the appropriate video device.

Hit CTRL-C when you are done recording.

Make sure nothing else is using the device.

---

### Post by newlinux on 2007-07-18
Also, you can combine  mpeg2 files using mpgtx or even cat.

---

### Post by najames on 2007-07-19
Thanks for the replys.

I have been beating on MythTV for about a month off and on now, no more time to waste.  I will try Sage or BeyondTV maybe this weekend.  I don't mind paying a few bucks if it works ok.  Sage does have Linux stuff too, but I suspect I am stuck with 2000 or XP for this.

This thing has to work well  as a media center, using a remote hopefully.   Command line stuff ain't gonna cut it for my non-linux wife and  I surely don't want to do it either.  I do enough command line Solaris stuff at work.

I **_HATE_** using XP, but it is easy to play the video on the STB, hit the record butrton in Hauppage software, and it all goes into one mpg file.  In reinstalled XP last night, installed Hauppauge drivers and software and recored 4 x 30minute shows off the SA 8300HD.  I might give the firewire a try tonight, not sure.  It would be nice to just copy over the files and work on the PC.

---

### Post by newlinux on 2007-07-19
you could setup remote buttons to execute those commands.

---

### Post by newlinux on 2007-07-19
also if you setup the guide and channel change script, you could record signal from the set top box just like you do other channels from the tuner. I do this via firewire.

---

