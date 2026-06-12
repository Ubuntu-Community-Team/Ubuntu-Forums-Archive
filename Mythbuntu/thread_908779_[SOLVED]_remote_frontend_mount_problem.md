---
title: "[SOLVED] remote frontend mount problem"
date: 2008-09-02
forum: Mythbuntu
---

### Post by mark467 on 2008-09-02
My backend is running great for a while now. I am now trying to add a remote frontend. I have it mostly configured but cant see the actual data files. i tried to mount the network share but get access denied

i added this to fstab

192.168.1.25://var/lib/mythtv   /var/lib/mythtv defaults,user,soft,nointr 00

is there a how to on setting up a remote frontend for mbuntu 8.04
that has a step by step. I thought it would be a pretty straighyt forward thing but apparently not. I am not that well versed in linux yet

---

### Post by murchball on 2008-09-02
You shouldn't need to mount the backend like that. I believe the video and whatnot are transferred via the myth protocol (or something like that). At any rate, when you first run mythfrontend on the remote machine, it should prompt you for the connection info. I believe that the current version has auto discovery too. If this isn't happening, it's probably an issue with the backend.

---

### Post by mark467 on 2008-09-03
That is what I found here in the forums. 
Something changed since I posted also. After doing all my updates and sitting all night now I can watch my recorded tv, but music and videos still dont work. Music shows my songs but gives DecoderMad: Failed to open input error 5
Videos shows my dvds (without cover art) and gives error failed to open "name.iso" in /var/lib/mythtv/videos

also i noticed the folder recordings is gone from /var/lib/mythtv on the frontend but recordings seem to work fine now

---

### Post by murchball on 2008-09-03
I didn't realize that you were trying to view dvds, you're correct that you need to mount the remote share for that.

---

### Post by SiHa on 2008-09-03
It's not obvious, but the Frontend looks in it's local filesystem for Mythvideo etc, so you need to map these onto the backend directories.

There's an excellent guide to mouting nfs shares here:

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

and here:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I can't remember where I got this last bit, but my frontend /etc/fstab entries are (from memory):

192.backend.ip.address:/var/lib/mythtv/videos /var/lib/mythtv/videos nfs rsize=8192,wsize=8192,timeo=14,intr
192.backend.ip.address:/var/lib/mythtv/pictures /var/lib/mythtv/pictures nfs rsize=8192,wsize=8192,timeo=14,intr

I think the syntax is correct, but try ```
$sudo mount -a
``` before rebooting to check all is well.

The destination folders you are mapping to must already exist, but don't neccesarily need to be the same as on the backend.

Once these are mounted, Mythvideo should be able to see stuff.

Edit: I forgot, without these mounted, Mythfronted will still appear to see directories full of stuff, because it just downloads the list stored in the MySQL database. You can enable browse mode in Mythvideo, which does actively browse the directories - it's somewhere in the setups.

Edit 2:
> also i noticed the folder recordings is gone from /var/lib/mythtv on the frontend but recordings seem to work fine now That's correct. Don't ask me why - something to do with the evolution of Myth, but the way it plays recordings and videos is completely different. Recordings are streamed from the backend, Videos play from the local filesystem.

---

### Post by mark467 on 2008-09-03
ok i get 
mount: unkown filesystem type "intr."
when i do sudo mount -a after adding your lines to fstab
i am using mythbuntu 8.04 if that makes a difference (on both pcs)

if i remove everything after the local folder i get same error but with '' for file system
ie. 192.168.1.25:/var/lib/mythtv/pictures /var/lib/mythtv/pictures
instead of
192.168.1.25:/var/lib/mythtv/pictures /var/lib/mythtv/pictures rsize=8192,wsize=8192,timeo=14,intr.

I assume this is all the same for the music folder as well

---

### Post by SiHa on 2008-09-04
Ah bugger it. Sorry, I was typing from memory, and forgot the important part - the filesystem!
It's an nfs share, so you need that in there.
Also I put a '.' at the end of the line out of habit.

Try ```
192.168.1.25:/var/lib/mythtv/pictures /var/lib/mythtv/pictures nfs rsize=8192,wsize=8192,timeo=14,intr
```

Instead - I'll edit the first post to make it clearer to anyone else that stumbles across this thread.

And, yes just susbstitute video with 'pictures' or 'music'

Cheers,

Simon

---

### Post by mark467 on 2008-09-04
Great that was it. Thanks so much. music and pics are great, dvds are choppy. i guess myth uses different compression or something for tv recordings. it is over 54g wireless music and recordings play fine. would it play smooth over 100mb hard wire you think.

---

### Post by SiHa on 2008-09-04
Post Removed.

---

### Post by newlinux on 2008-09-04
Unless your wireless connection is really bad, you should be able to stream DVD over wireless G. regular dvds should top out around 7-8Mbps, which even a weak wireless G connection should do. I can easily stream standard definition over wireless G, and when conditions are right (little interference) I can even stream HD mpeg-2 (up to around 20Mbps). My Wireless G connections around my house typically run 15-20Mbps. So it's not a given wireless G won't work for dvds, in most cases it should.

If you can stream the SD mpeg-2 TV recordings you should probably be able to stream the dvds. Maybe your nfs connection is really slow. You might want to run some tests to see what your true wireless network speed is. Are these dvd isos your are streaming? Are you using the internal player or some external player for dvds?

---

### Post by SiHa on 2008-09-05
> **newlinux said:**
> Unless your wireless connection is really bad, you should be able to stream DVD over wireless G. 

I stand corrected:oops:

---

### Post by mark467 on 2008-09-05
> **newlinux said:**
> 

If you can stream the SD mpeg-2 TV recordings you should probably be able to stream the dvds. Maybe your nfs connection is really slow. You might want to run some tests to see what your true wireless network speed is. Are these dvd isos your are streaming? Are you using the internal player or some external player for dvds?

the are dvd iso's and i am using the builtin player to watch them. what kind of tests can i run to check speed

---

### Post by newlinux on 2008-09-05
First a couple of questions. 
1. What types of recordings are you viewing through livetv that work right (analog NTSC, digital QAM,  SDTV, etc.)? 
2. When playing dvds, have you looked at your frontend logs while playing a dvd to see if there is any error information?
3. Have you tried playing back an iso over the nfs share with VLC or Xine or mplayer and see how it plays? 

There are a couple of ways to test network speed.  One way, install iperf on both machines where you want to test your network speed. On the machine the file is coming from, do:

```

iperf -s

```

On the machine you normall view the file on do:
```

iperf -c <IP_ADDRESS_OF_SOURCE_MACHINE>

```
insert the ipaddress of the machine your ran iperf -s on and remove the brackets.

This will give you an idea of what your network speed is. You might want to run it a few times to see if it is consistent. Now this gives you network speed. if this looks fast enough for watching dvds (anything over 10Mbps should do great) then there is probably something else wrong with your setup. You can test file transfers speeds with rsync over your nfs link and see how fast that is. You may need to adjust some NFS parameters, or use SAMBA/CIFS instead.

You can also test your realtime speed by using iptraf (needs to be run with sudo and is available in the repos). Open up a terminal on your remote frontend and run iptraf and look at the  interface statistics (or something like that). Then try watching something live on myth and then take a look at the monitor to see what the network transfer rates are. Do the same with watching a dvd, and watching a dvd with an external player. This will give you an idea of the throughput that is required of these streams...

---

### Post by mark467 on 2008-09-05
Ok tested the speed and it was consistently 24.2 to 24.7 mbit 

the recorded tv is analog NTSC  recorded at 2200 bitrate
plays the same over vlc
and which log and where is it located to check for errrors

---

### Post by newlinux on 2008-09-05
242Mbps over wireless G????? You sure you don't mean 24.2Mbps? Wireless G is supposedly only capable of 54Mbps.

What plays the same over vlc? your recordings or dvd isos? You mean you still get choppy playback with vlc when playing it from command line with VLC?

Your frontend and backend logs are in /var/log/mythtv/
If you run mythfrontend from the menu you can do:

tail -f /var/log/mythtv/mythfrontend.log

to see what your frontend is doing while you are watching a dvd. You have to hit ctrl C to get out of that.

---

### Post by mark467 on 2008-09-06
Ii says  24.2 to 24.7 above. Yes the dvd's play the same over vlc and xine. I will try a dvd and check logs later

---

### Post by newlinux on 2008-09-06
My apologies. Must have been something weird with my fonts and display. Couldn't see the decimals at my work computer. If VLC and xine have the same problem. it's probably an installation issue or an network transfer issue. Your network connection is definitely fast enough. Have you tried playing a dvd locally (copying one of the isos over the NFS link - which at the same time you can check the transfer rate over your NFS link - and then playing it locally). If it has the same problem in VLC when played locally then it is probably a general system install issue. If it plays fine is it probably an NFS issue (and you'll have a good idea of how fast files are moving over your NFS share).

---

### Post by mark467 on 2008-09-15
Ok it must be something with my video card or setup. Copied a 7.5 gb iso over and it still plays choppy. it copied in 15 min (i ran a hard line) VLC plays it even worse than the myth player. the front end is a p3 800 with 512 mb ram and a cheap nvidia chipset agp w/ 128mb could the system be the problem?

I reinstalled the prop.  media stuff and now the all play but they all stutter. Even the recorded tv is stutering

---

