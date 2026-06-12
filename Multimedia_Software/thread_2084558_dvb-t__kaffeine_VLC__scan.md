---
title: "dvb-t  kaffeine VLC  scan"
date: 2012-11-15
forum: Multimedia Software
---

### Post by doja on 2012-11-15
Hi all,
I'm new with Ubuntu (12.04) and have a problem to get run dvb-t with kaffeine (1.2.2).

I have a Diggitrade dvb-t stick (ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick) that is working well with MeTV and today I tried also VLC player. There is no substantial problem.

Trying make a scan in Kaffeine results with 'no device found' message.

My additional question:
When I did channel scan for MeTV directly in MeTV the program didn't found all TV-channels by auto scan. But the rest of the channels I could find after using the option 'scan using initial scan file' for my region.

To find TV-channels for VLC I used terminal to create channels.conf

>  w_scan -c DE -X > ~/channels.conf

Unfortunately I couldn't again find all the channels. How to proceed to get them all?

---

### Post by doja on 2012-11-16
I found the devil.

There is some strange behaviour due to MeTV.

I got  MeTV run at first place ( maybe because it was easiest to install )
Then I tried VLC and Kaffeine and they didn't worked. I thought I'm doing something wrong.
For check if  the dvb-t stick is working properly I always tried MeTV at first place and that was wrong.

Because after starting MeTV  other dvb-t applications don't work anymore.

Example:  PC restart and then start of applications in following order

1. Kaffeine - works
2. VLC - works
3. Kaffeine - works
4. MeTV -  works
5. Kaffeine and VLC don't work anymore !!!

I checked it twice.

My second problem remains:
Like by the scan for VLC I couldn't find all channels by the scan with kaffeine.

---

### Post by BicyclerBoy on 2012-11-16
[http://linuxtv.org/wiki/index.php/W_scan](http://linuxtv.org/wiki/index.php/W_scan)

do you have a recent build of w_scan.

DVB-T has mulitple channels on the same frequency called a multiplex.

Do you find the missing channels are on a previous found multiplex ?
Does it appear you find only one channel per muliplex with the initial scan ?

There have been posts on mythtv mailing lists about this behaviour..The "normal" scanning process is to repeat the scan only on existing multiplexes.

Can use the w_scan output to input into dvbscan which outputs channels list
[http://linuxtv.org/wiki/index.php/Dvbscan](http://linuxtv.org/wiki/index.php/Dvbscan)

---

### Post by doja on 2012-11-17
Solved the scan problem for 'w-scan' by letting out the option for  the country '-c DE'

> w_scan -ft -X > ~/channels2.conf

My 'w_scan' like all other applications are fresh, I installed Ubuntu a moth ago.

As far as I could see, there are always several channels from one frequency. 
Missing was the frequency itself. 

The reported bug by MeTV seems affect also 'w-scan' application.
__________________________
Now there remain only the right scan options for Kafeine.

And   I would like to know how to include the channels.conf in VLC  permanently so that I haven't to load it every time I start this  application.

---

### Post by BicyclerBoy on 2012-11-17
w_scan in 12.04 is 1 year old next month...

I don't watch live TV so don't use VLC & its seeking is rubbish c.f. mythtv
I have just typed in multiplex frequencies into VLC etc just to see if it works..

I would guess you add something to .config/VLC or some other obscure file.
Could make a launcher to a to script with cmd line options.

I have a desktop icon & multi-media keyboard key start MythTV frontend on a certain X screen & move the mouse to the screen edge & only if it is not already running etc..

[http://www.linuxtv.org/wiki/index.php/VLC_media_player](http://www.linuxtv.org/wiki/index.php/VLC_media_player)
There is a discussion about channels.conf & a script to convert to xml playlist.
VLC preferences allows a default stream to be set to channels.conf.

---

### Post by doja on 2012-11-17
Now I got also the scan directly with Kaffeine and it is working (now, but after my experience I don't know if it will be the case also tomorrow)

But it was a fight and I can't tell what was wrong or what did I change so that it is running now. I tried to make a scan with 'w-scan' for Kaffeine (they have a different format for the scanfile then VLC and there is a difference to older versions of Kaffeine that are mostly described on the Internet). I tried substituted the origin scanfile  from Kaffeine with the one from 'w-scan' but I didn't get it. After giving up and bringing all the files to the original status Kaffeine was able making the whole scan by itself (finding all channels).  Kaffeine had then all the channels but didn't run. After restart it runs now. Just for fun I tried repeat the scan in Kaffeine again but it was not working anymore or it found again only one frequency.

I'm new with Ubuntu (and Linux generelly) and I'm trying to find the best solutions for me. This is the reason for playing with different applications.  I thought I'm stupid if I'm not able to get run this applications, but sometimes it's not so easy. If there is  some bug you don't know about it's over.

But at the end I get run all the applications: MeTV, VLC, Kaffeine and w-scan.

---

### Post by doja on 2012-11-17
Probably I found the reason for the problem by scan with Kaffeine.

If there is already some channel in the list  and you start the TV-option  in Kaffeine you can't scan properly because the TV is already running. I pressed the button 'stop' to stop receiving TV signal and then started the scan. It was working.

Trying to scan with 'w-scan' if there is already TV application running you get an error message.
If you try to scan by MeTV  the application automatically stop reiciving the TV signal.

Non of this 2  options happen by Kaffeine.

It is also impossible to let run two TV applications parallel because the dvb-t device  can always do only one task.

---

### Post by BicyclerBoy on 2012-11-18
Yes , mythtv is like that as well. The myth backend takes full control of the tuner h/w.
To use dvbscan, w_scan etc you must first stop the backend.

You can use dvbsnoop & some mheg5 dump tools in parallel with other TV applications but you can not change channels.
i.e. I can dump/extract the mheg5 EPG while mythtv is recording etc..
And you can run the interactive mheg5 externally from mythtv while recording..

The tuner can stream more than one program stream (assuming PID filter in tuner).
Some USB stick tuners don't have PID filters & some require USB2.

---

