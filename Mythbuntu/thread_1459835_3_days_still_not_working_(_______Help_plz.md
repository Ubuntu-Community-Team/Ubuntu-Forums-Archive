---
title: "3 days still not working :(      : Help plz"
date: 2010-04-22
forum: Mythbuntu
---

### Post by hibridB on 2010-04-22
Hello  

the past 3 days Ive been trying to get mythbuntu all set up and working. Ive had no luck what so ever. Which is why im posting on here.

what Im trying to achieve is to watch TV using s-video from my Sky box and analog TV for an aerial.

 My TV tuner is a FlyTV Platinum33/35. Mythbuntu dose pick it up. so thats fine. 

But when i try to scan for channels it ether crash's myth backend or i get "scanning newzealand 1 no lock". it just sits there and dose nothing .

note i don't have any EPG's available in new zealand that are up to date.  

thanks in advance

---

### Post by jbman on 2010-04-22
What version are you trying to install?

---

### Post by hibridB on 2010-04-22
mythbuntu 9.10

---

### Post by Rasa1111 on 2010-04-22
hi hibrid...

 i dont know much about mythbunutu...

only that, I tried to get it going for a neighbor....
only to have the same( or almost the same) problem. 

 All she wanted to do was use it to watch her movies from her laptop to her TV~
and to have a library for the all..

eventually I installed Moovida~  and she is now watching all the stuff from her HD, on her TV with an S video cable...  and it even separates all of them into sections, music/movies/docus/pics/etc/etc. 

it is actully quite niice! 
so niice i installed it on my box, Just havent used it yet at home.

---

### Post by hibridB on 2010-04-22
do you know if i can use TV tuner in Moovida


but i still really want to get mythbuntu going.

thanks for your quick reply's

---

### Post by Lepy on 2010-04-22
Can't find a link to the FlyTV. Regardless, if you hook the tuner up to your aerial, you should be able to scan and pick up available channels and hopefully EPG, if you have set your location-specific settings correctly.

Recording a STB over a tuner's s-video requires a little more effort. This probably isn't the only or easiest way to do it...but... 

1.) You will not be able to scan channels over an s-video connection, it only sends an image. You will have to gather guide-data from a listing service and fill it with mythfilldatabase command. 

2.)Running mythtv-setup, you will have to link the s-video capture portion of your card (option 2) with the video source containing your guide data (option3). This should not be a problem since you have said your tuner is recognized.

3.) Link the card and the data source using option 4. You will  want your tuner card to watch channel 3, and you will need to setup a channel changing script/ir blaster for your sky box.

With this setup, in the event of a recording, the script and blaster will send a channel change command to your Sky STB, the STB will tune to the appropriate channel while outputting to channel 3, and your s-video input will start recording the show(though it is actually tuned and recording channel 3). Mythtv will handle the naming and tagging of the video so it shows up as relevant to your guide information in the database.

The actual setup will be more involved, but I hope this gives you a good starting point.

I highly suggest reading all of the docs: 
[http://www.mythtv.org/docs/](http://www.mythtv.org/docs/)

and browsing the wiki:
[http://www.mythtv.org/wiki](http://www.mythtv.org/wiki)

---

### Post by hibridB on 2010-04-22
i cant seem to find guide data for new zealand. i can only find one form 2007 and thats it. Do i really need one of these to get s-video working ?

---

### Post by Lepy on 2010-04-22
Without guide data you would have to manually schedule recordings and your database would contain only the recording times, no program names or descriptions. Your mythbox would act mainly like a high tech vcr, not the dvr it was meant to be. 

2007? You might be referring to this:
[http://forums.gbpvr.com/showthread.php?30586-Alternative-New-Zealand-XMLTV-listing-source](http://forums.gbpvr.com/showthread.php?30586-Alternative-New-Zealand-XMLTV-listing-source)

I have no experience with NZ listings, but you might want to read this thread as it very recent/active: 
[http://www.geekzone.co.nz/forums.asp?forumid=84&topicid=58727](http://www.geekzone.co.nz/forums.asp?forumid=84&topicid=58727)

Any xmltv data can be used with mythfilldatabase, I believe.

---

### Post by hibridB on 2010-04-22
> Link the card and the data source using option 4. You will want your tuner card to watch channel 3, and you will need to setup a channel changing script/ir blaster for your sky box.

With this setup, in the event of a recording, the script and blaster will send a channel change command to your Sky STB, the STB will tune to the appropriate channel while outputting to channel 3, and your s-video input will start recording the show(though it is actually tuned and recording channel 3). Mythtv will handle the naming and tagging of the video so it shows up as relevant to your guide information in the databas

so i need a ir blaster to do this im guessing. and with out i cant use s-video ?

---

### Post by Lepy on 2010-04-22
> **hibridB said:**
> so i need a ir blaster to do this im guessing. and with out i cant use s-video ?

As far as I know, unless you want to manually change the channel with your skybox remote before every recording (and I'm 99.5% confident that you want to do that :biggrin:)...yes.

If you were to hook your coax straight into the back of your tuner card, the card itself would take care of changing channels before a recording. This will be true of hooking your aerial up too.

The blaster (and the script you will setup) will mimic your STB's remote button presses to change channels as a recording starts. Since your s-video connection is just picking up an analog video signal, it has no tuning capabilities.

You could build a blaster yourself, but I think the easiest approach would be to buy a usb MCE remote that comes with an ir blaster, something akin to this: [http://en.community.dell.com/cfs-filesystemfile.ashx/__key/CommunityServer.Wikis.Components.Files/laptop/Dell-MCE-Remote_2C00_-IR-Blaster-_2600_-IR-Receiver-with-Dell-Studio-MCE.jpg](http://en.community.dell.com/cfs-filesystemfile.ashx/__key/CommunityServer.Wikis.Components.Files/laptop/Dell-MCE-Remote_2C00_-IR-Blaster-_2600_-IR-Receiver-with-Dell-Studio-MCE.jpg)

Either approach will be reliant on having 1.) guide data or 2.) manual recording schedules so that the tuner/blaster knows when to change channels and start recording.

---

### Post by hibridB on 2010-04-22
hmm ok well im getting lost here sorry :(

the reason im trying to get mythbuntu is so i can use my set-top box's s-video output. because windows media center will not let me use it unless i have the ir blaster / mce remote. I cant use the virtual ir blaster because im running win 7 64bit. 

All that i want out of mythbuntu is the ability to watch TV and record every now and then. 

I would like to use my set-top box remote to change the channels.

so far i have set up the video sources manually. That working great.

ive linked my card s-video to the video source.

ive assigned channel numbers to the channels.

i go to the frontend watch tv just says plz wait and it returns back to the menu. 

Thanks for the help

---

### Post by Lepy on 2010-04-22
So, media center won't let you use your s-video input unless it detects an MCE remote with an ir blaster? Does it grey out the option or something to prevent confusion?

I misunderstood you intentions. I guess you don't care to utilize all of mythbuntu's functionality?

No matter which way you slice it, I would consider purchasing a usb receiver + blaster combo. If not, every time you want to watch tv, you will need to use a keyboard to start live tv and then use your STB remote to tune channels and switch back to the keyboard to start recording any program you may want to keep. Your STB remote probably can act as a universal remote, so you can turn 3 control devices into one.

Mythbuntu livetv also isn't 100% real time. It writes to the HDD then plays the video.You will experience 3-5 seconds of video lag when using your STB (change channels, open config menus). Its not that bad, but if you STB is slow to tune/react, it might get frustrating.

But...whatever works for you mate. Let's try to get you watching some quality programming the mythtv way! :popcorn: 
It sounds like you setup your tuner, guide data (even selecting no grabber will work), and then linked the two together. Not sure what is happening otherwise. 

Can you please run this command from a terminal (mythfrontend -v important > ~/frontend.log), try to start watching livetv, then paste back with the log information?

---

### Post by hibridB on 2010-04-22
hello heres the log you asked for. It 61846 lines. 

start :
```
2010-04-23 10:21:51.345 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-04-23 10:21:51.397 Using runtime prefix = /usr
2010-04-23 10:21:51.398 Using configuration directory = /home/brendan/.mythtv
2010-04-23 10:21:52.257 Empty LocalHostName.
2010-04-23 10:21:52.292 New DB connection, total: 1
2010-04-23 10:21:52.303 Closing DB connection named 'DBManager0'
2010-04-23 10:21:52.386 Enabled verbose msgs: important
2010-04-23 10:21:52.426 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-04-23 10:21:53.490 New DB connection, total: 2
2010-04-23 10:21:56.376 Found mainmenu.xml for theme 'MythCenter'
2010-04-23 10:21:57.148 Using protocol version 50
2010-04-23 10:22:01.016 Using protocol version 50
2010-04-23 10:22:01.151 Spawning LiveTV Recorder -- begin
2010-04-23 10:22:01.510 Spawning LiveTV Recorder -- end
2010-04-23 10:22:01.535 We have a playbackURL(/var/lib/mythtv/livetv/3000_20100423102201.mpg) & cardtype(MPEG)
2010-04-23 10:22:08.036 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/livetv/3000_20100423102201.mpg'.
2010-04-23 10:22:08.039 We have a RingBuffer
2010-04-23 10:22:08.091 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2010-04-23 10:22:08.155 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-04-23 10:22:08.155 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-04-23 10:22:08.155 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-04-23 10:22:08.155 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-04-23 10:22:08.155 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-04-23 10:22:08.155 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-04-23 10:22:08.155 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-04-23 10:22:08.156 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Error: Invalid file descriptor in 'safe_read()'
```

the same thing keeps on repeating

heres the last few lines of the log
```
2010-04-23 10:22:24.167 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Error: Waited 16 seconds for data, aborting.
2010-04-23 10:22:24.167 RingBuf(/var/lib/mythtv/livetv/3000_20100423102201.mpg) Warning: Peek() requested 2048 bytes, but only returning 0
2010-04-23 10:22:24.167 NVP::OpenFile(): Error, couldn't read file: /var/lib/mythtv/livetv/3000_20100423102201.mpg
2010-04-23 10:22:24.167 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2010-04-23 10:22:24.167 TV Error: LiveTV not successfully started
```

---

### Post by Lepy on 2010-04-22
My first thought is a permission issue. Try running the command:
```
sudo chmod 777 /var/lib/mythtv/livetv/
```
and see if this allows you to watch tv. Watch the log again to see if this changes any of the messages, if it doesn't work. 

Make sure you have set storage directories correctly in mythtv-setup (chmoding all those dirs to be safe).

What filesystem type is /var/lib/mythtv/livetv? Would you have specified it as ntfs per chance?

---

### Post by hibridB on 2010-04-22
ok i ran sudo chmod 777  on all the dirs

that didnt work. and the log is stll the same

and the file system is on a ext3 i think. diffenetly not ntfs 

:confused:

---

### Post by Lepy on 2010-04-23
I would have your livetv storage directory open while trying to watch livetv and alt+tab to make sure the file is being created and see if it grows in size at all. 

If you have mounted the recording dirs from a separate partition/s check /etc/fstab and make sure you have the setting correct, especially rw access.

You might want to check this thread, specifically this post as the problems seem kinda similar:
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8420689&postcount=21](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8420689&postcount=21)

---

### Post by hibridB on 2010-04-23
hmm ok well ive followed that post. still doing the same thing. 

it dose make the .mpg file. but it stays at 0 bytes

---

### Post by matt06 on 2010-04-23
I googled "**Error: Invalid file descriptor in 'safe_read()'**" and it seems like it could be filesystem or drive error..are you still getting those in your log?  How is your drive physically hooked up?  Also, how you did you initially create your partition and filesystem?  Just throwing some guesses out there.

I'd post the contents of /etc/fstab and maybe even output of 'fdisk -l'.

---

### Post by hibridB on 2010-04-23
well im going to do a re install  with a fresh hdd see what happens :D

---

### Post by nickrout on 2010-04-23
1. I suggest you join the mythtvnz mailing list:

[http://lists.ourshack.com/mailman/listinfo/mythtvnz](http://lists.ourshack.com/mailman/listinfo/mythtvnz)
Archives [http://www.gossamer-threads.com/lists/mythtv/mythtvnz/](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/)

2. I recommend tv_grab_nz-py for EPG. Google it and you will find it.

---

### Post by hibridB on 2010-04-25
so after spending many hours trying to get mythbuntu working. Ive still had no luck at all. It is still not working. 

so im giving up 

thanks guys for your help

---

### Post by nickrout on 2010-04-26
well you must be doing something wrong because it works for the rest of us. I also invited you to the best NZ resource for mythtv, and I got no acknowledgement or thanks. I pointed out the best source for NZ EPG and got similar thanks.

Some people you just can't help.

---

### Post by matt06 on 2010-04-26
A post consisting of "not working" and a detailed response or explanation of what is failing are two very different things.  One might be able to get Myth working for you, the other will likely not.

---

### Post by Lepy on 2010-04-26
If you still haven't completely given up, please post the requested information: the contents of /etc/fstab and the output of the command "sudo fdisk -l"

Also, have you enabled auto-builds? Enabling fixes might help: [http://www.mythbuntu.org/files/mythbuntu-repos.deb](http://www.mythbuntu.org/files/mythbuntu-repos.deb)

---

### Post by nickrout on 2010-04-27
Also I am not entirely sure that the FlyTV Platinum33/35 is supported in linux, I know the OP said ubuntu had "picked it up" but does it really work? Can other software, eg tvtime use it?

---

### Post by mtader on 2010-06-05
I had Mythbuntu running for quite a long time and made some changes to add ZoneMinder to the same box.  I am running a master backend with multiple front ends, all version 0.22.  Ubuntu 9.10.  I am able to see and play my recorded programs just fine. When I try to watch LiveTV or record something, I get the following in the mythfrontend.log:

2010-06-05 14:07:17.436 RingBuf(/mythmedia/recordings/1022_20100605140654.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-06-05 14:07:17.436 RingBuf(/mythmedia/recordings/1022_20100605140654.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-06-05 14:07:17.436 RingBuf(/mythmedia/recordings/1022_20100605140654.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-06-05 14:07:17.436 RingBuf(/mythmedia/recordings/1022_20100605140654.mpg) Error: Waited 16 seconds for data, aborting.
2010-06-05 14:07:17.436 RingBuf(/mythmedia/recordings/1022_20100605140654.mpg) Warning: Peek() requested 2048 bytes, but only returning 0
2010-06-05 14:07:17.436 NVP::OpenFile(): Error, couldn't read file: /mythmedia/recordings/1022_20100605140654.mpg
2010-06-05 14:07:17.436 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2010-06-05 14:07:17.436 TV Error: LiveTV not successfully started
2010-06-05 14:07:17.436 RingBuf(/mythmedia/recordings/1022_20100605140654.mpg) Error: Invalid file descriptor in 'safe_read()'


I am using Hauppauge cards, 350 and 150.  I used the frontend right on the server and got the same errors.  The permissions have not changed from when it was working, to the best of my knowledge.  The only other thing I can think of that changed was that the cards moved to /dev/video20 and /dev/video29 since I put in the CCTV capture card in there.  I am not sure if that is an issue or not, or if there is even a way to control that.  I am a real newbie (getting better), so any details and explanations would help me troubleshoot better.  THANKS!!

---

### Post by nickrout on 2010-06-05
changing device files certainly is an issue. you need to fix that!

---

### Post by mtader on 2010-06-05
Is the device changes causing the issue?  Either way, is there a way to set the device numbers and have them stay?  I have never had them move around, but with this new CCTV capture card, they seem to move.

---

### Post by nickrout on 2010-06-06
yes it will cause an issue. the backend identifies capture card the device node that it was when it was set up.

search these forums and you will find a solution, good terms would be "udev device"

---

### Post by mtader on 2010-06-06
OK thanks, I will look around and see what I can do with UDEV.  I hope I can get the assignements solid, so I do not have to reconfig Myth each time.  I never had this issue before while running Myth, and I had 3 cards running before.  grrr.  If I can assign device numbers by input, that may also help me get my 2250 card running as well.  For some reason, Myth would not pick that one up.

Any thoughts as to the issue/errors above?  The device numbers stay the same once it is running (unless something is happening in the background) and I still get the error above.  So I am wondering if that issue is different???  maybe??

---

