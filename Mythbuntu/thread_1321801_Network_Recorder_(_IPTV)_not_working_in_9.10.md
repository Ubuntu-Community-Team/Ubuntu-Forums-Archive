---
title: "Network Recorder ( IPTV) not working in 9.10"
date: 2009-11-10
forum: Mythbuntu
---

### Post by OffAxis on 2009-11-10
I have a 9.04 mythbuntu install that I recently upgraded to 9.10.
It records IPTV on the network card. 
At least it used to; since the upgrade the only thing it'll do is pop up an error message
```
"Error: MythTV is using all inputs, but there are no active recordings?"
```

I've already deleted the original network setup and input a new one from scratch, and still nothing.
I've also tried restarting the backend after booting; same problem (so I don't think it's a start-up sequencing / availability thing)

Any ideas?

---

### Post by OffAxis on 2009-11-24
Since my initial upgrade (which rendered my network recorder inoperable) I've done two things:
a clean install of 9.10 (doesn't work)
installed the nightly builds package on the upgrade (also doesn't work)

@TheCook> **TheCook said:**
> BUT now I cannot scan for channels with the Network Recorder
 While it's true that the 'Scan for channels' doesn't work right, the problem seems to be deeper than that; on an upgraded install there should be no need to scan for channels.

(In 9.04 I had to go to the Channel Editor and use the Scan For Channels button there. You might try that in 9.10 and see if it works- I haven't tried that on my clean install yet.)

---

### Post by TheCook on 2009-11-24
Agree with the need not to scan for channels if you just upgrade.  BUT one of the fixes suggested was to remove the tuner, reboot and reinstall.  I did that and couldn't fully re-install.  I'll try scanning from the channel editor tonight and see if that works.

Thanks for the suggestion, I didn't think of scanning from there.

Regards,

The Cook

---

### Post by TheCook on 2009-11-25
Hello all again,

I tried to scan from the channel editor and had the same result as before.  The Scan Type is M3U Import, I hit the Next button and the scan just sits there with a status of Tuning and scan at 0% until I hit enter again to finish.

Is there a way to add m3u channels manually?

Just for giggles I tried creating a slave backend with a network recorder/m3u tuner using Mythdora build 0.21 then upgrade to 0.22.  It has the same troubles.  Can't scan for channels.

Also noticed that on mythweb, neither Network Recorder is reported.  When I first upgraded the Network Recorder was marked as asleep now, with no channels against it, it is just not showing up at all neither is the slave backend Network Recorder.

---

### Post by nickrout on 2009-11-25
> **TheCook said:**
> Hello all again,

I tried to scan from the channel editor and had the same result as before.  The Scan Type is M3U Import, I hit the Next button and the scan just sits there with a status of Tuning and scan at 0% until I hit enter again to finish.

Is there a way to add m3u channels manually?

Just for giggles I tried creating a slave backend with a network recorder/m3u tuner using Mythdora build 0.21 then upgrade to 0.22.  It has the same troubles.  Can't scan for channels.

Also noticed that on mythweb, neither Network Recorder is reported.  When I first upgraded the Network Recorder was marked as asleep now, with no channels against it, it is just not showing up at all neither is the slave backend Network Recorder.

My understanding of the network recorder is that you don't need to scan for channels at all. You enter the url of the m3u file and the backend downloads that and takes the channel info from it.

But I may be wrong.

---

### Post by TheCook on 2009-11-25
You are right.  The way you get the system to download the channels is to either 'scan for channels' or 'fetch channels from listing source'.  I have been unable to get either to work.  Maybe the system expects something different from the listings source now.  Here is a chunk of my listings source (IPs changed).  If anyone can point out any problems let me know.

#EXTINF:0,512 - Committees
#EXTVLCOPT:udp-caching=300
udp://@192.168.0.43:1234
#EXTINF:0,604 - DW
#EXTVLCOPT:udp-caching=300
udp://@192.168.0.16:1234

---

### Post by OffAxis on 2009-11-26
Looks like there's a 'Scan for channels' bug report here:

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/452779](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/452779)

---

### Post by TheCook on 2009-11-26
I am the same as Mark at #18.  I'll kep an eye on this.

Don't know how to manually add UDP multicast streams as channels.  It asks for a frequency and all I have is an IP Address and a port.

Thanks for the heads up.

---

### Post by nickrout on 2009-11-26
> **TheCook said:**
> You are right.  The way you get the system to download the channels is to either 'scan for channels' or 'fetch channels from listing source'.  I have been unable to get either to work.  Maybe the system expects something different from the listings source now.  Here is a chunk of my listings source (IPs changed).  If anyone can point out any problems let me know.

#EXTINF:0,512 - Committees
#EXTVLCOPT:udp-caching=300
udp://@192.168.0.43:1234
#EXTINF:0,604 - DW
#EXTVLCOPT:udp-caching=300
udp://@192.168.0.16:1234

According to this [http://www.gossamer-threads.com/lists/mythtv/users/287181#287181](http://www.gossamer-threads.com/lists/mythtv/users/287181#287181) you should not have the @ sign in your channel definition.

You should read that whole thread carefully.

---

### Post by TheCook on 2009-11-27
I even tried their "known good" version.  Mine worked before the upgrade to 9.10 even with the @ in there.

Does it help if I say I am using the 64-bit version?  I found this in the log.  Don't know if it helps.  It looks like there are no channels (now theres your problem;))

2009-11-27 17:57:55.792 MythBackend: Starting up as the master server.
2009-11-27 17:57:55.805 New DB connection, total: 2
2009-11-27 17:57:55.811 Connected to database 'mythconverg' at host: localhost
2009-11-27 17:57:55.822 New DB connection, total: 3
2009-11-27 17:57:55.834 Connected to database 'mythconverg' at host: localhost
2009-11-27 17:57:55.882 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: '/home/chris/iptv.m3u'
2009-11-27 17:57:55.893 IPTVChanFetch, Error: Invalid channel list header ()
2009-11-27 17:57:55.901 IPTVChan(1): Loaded 0 channels from /home/chris/iptv.m3u

---

### Post by nickrout on 2009-11-27
please show us the iptv.m3u file

---

### Post by OffAxis on 2009-11-30
```
#EXTM3U
#EXTINF:0,1 - First Channel
udp://111.1.1.1:1002
#EXTINF:0,2 - Second Channel
udp://222.2.2.2:2001
#EXTINF:0,3 - Third Channel
...
```

Here's a piece of mine...

Having the @ sign in there never worked for me, but the above did (and does in 9.04 and everything prior). I know I can also have an xmltv id in there for each channel, but that seems unnecessary in the U.S. while I use Schedules Direct.

---

### Post by TheCook on 2009-11-30
OK Let me start from the begining.  I am a bit frustrated at the moment because my entire network has colapsed from the firewall back.  I have no backend at the moment and the front end is going through yet another rebuild (the last one lasted a week). Anyway...
I upgraded from a working 9.04 to 9.10 (so the .m3u file I had was working in 9.04 even with the @.  I seem to remember putting them back in a few versions ago (a few years back) for some reason but can't find anything in my notes). 
The result of the upgrade was that the 'Network Recorder' had a status of asleep when I looked it up on mythweb.  Other threads suggested that I remove it and reinstall it.  When I did (without deleting the .m3u file) I was not able to scan channels.  It was suggested that I take the @ bits out so Idid.  I even copied the 'known good' version from gossamer threads and was still unable to scan channels.  I am happy to try other 'known good' m3u files once I get a working backend again.  It may take me some time.  There is something wrong with one of the network connections on the BE and I am having troubles finding something to manage the connection with... it may even be a US network card :mad: but that is another issue.

Thanks for the suggestions.  I'll come back with a status as soon as I get the other bits fixed.):P  Just need to get the three year old to stop demanding playschool all the time and the four month old to sleep long enough to get some sleep/time on the network.

I put in a part of my existing m3u file a few steps back.  For waht its worth you can consider it as:

#EXT3U
#EXTINF:0,512 - Committees
#EXTVLCOPT:udp-caching=300
udp://@192.168.0.43:1234
#EXTINF:0,604 - DW
#EXTVLCOPT:udp-caching=300
udp://@192.168.0.16:1234

I can't get into the backend and copy it easily at the moment.  Few too many aligators in the swamp.

---

### Post by TheCook on 2009-12-01
OK,

I have a network that is mostly working and I am using the other network connection on my back end.

I have an m3u file that contains:

#EXTM3U
#EXTINF:0,1 - First Channel
udp://239.193.0.91:8208
#EXTINF:0,2 - Second Channel
udp://239.193.0.2:8208

I have asked to scan channels and I get nothing.

I am now at WAF - infinity and it will take a miracle to keep this going in any form.  Is it worth building from scratch?  Why not I'm in the doghouse already8-[

---

### Post by nickrout on 2009-12-01
if you have network problems you need to fix those first obviously.

are those 239. addresses multicast? Do you have a multicast route?

additionally I believe that the EXTVLCOPT is not relevant to mythtv, maybe the backend is barfing on that. Try removing it.

---

### Post by OffAxis on 2009-12-01
> Is it worth building from scratch?
As in... compiling myth from scratch?

I don't think it is; the bug seems to have happened in the latest release, and would need to be fixed in the source code. The two things you could try are 
1. Enable the daily auto-builds. It's not fixed yet, but when it is that's the first place it should show up. There's a .deb on mythbuntu.org here:
[http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

If that doesn't work (or if you want to raise the WAF quicker)

2. Re-install 9.04 (like I had to:)) It's no longer available on the mythbuntu site but you can find it on the torrents or I can post it for download if you don't have a copy.

you could also try manually editing the tables in mysql, but I'm not sure how those play out with a network recorder. When I get a chance I'll do a dump from my 9.04 tables and compare that to the 9.10 setup.

---

### Post by TheCook on 2009-12-02
I have fixed the network problems.  I moved the NIC and replaced the network cable. Fixed.

I have checked the route

[FONT="Courier"]$ route
Kernel IP routing table
Destination  Gateway         Genmask      Flags Metric Ref    Use Iface
192.168.100.0   *            255.255.255.0   U     1      0        0 eth0
192.168.0.0     *            255.255.255.0   U     1      0        0 eth1
239.193.0.0     192.168.0.1  255.255.0.0     UG    0      0        0 eth1
link-local      *            255.255.0.0     U     1000   0        0 eth0
default         TheFirewall  0.0.0.0         UG    0      0        0 eth0
[/FONT]
It is routing the multicast through the correct NIC.  That would be why I can see the streams using VLC (Just thought I'd check it again)

The current m3u file is now just one channel:

#EXTM3U
#EXTINF:0,1 - First Channel
udp://239.193.0.2:8208 

Can't cut it down much more than that.

I'm starting to grasp at straws but does it matter what you use to create the file.  This last one was made using nano.  I know that using notepad in windows doesn't work (or atleast it didn't in the past).  Is there another editor that is known to work?

Regards,

The Cook

---

### Post by TheCook on 2009-12-02
Just thought I'd let you know that I tried running the short m3u file in iptv and it didn't work.

I put the original one with the @ and other bits and it works fine.

I'm a bit worried that I have some strange things going into my file while I edit it.

---

### Post by TheCook on 2009-12-02
just had a look at the file with vi and there was a ^M at the end of each line.  I deleted them and tried that in VLC... Didn't work.  I had to put the @ symbol back in.

I tried it in 'scan channels' with both the @ in and the @ out.  Both don't work.

---

### Post by OffAxis on 2009-12-02
vlc and mplayer can pick up my streams, too. It's just myth that's missing them.

> I know that using notepad in windows doesn't work (or atleast it didn't in the past).

The default encoding is different in notepad (ansi versus unc or some such thing). If I remember correctly notepad can EDIT unix text files and maintain the correct encoding, but when creating from scratch its default is to use its own default encoding scheme (which is not 100% compatible). You can over-ride that in the bottom of the 'Save As...' dialog box.

If you're on windows you should try notepad++.
[http://notepad-plus.sourceforge.net/uk/site.htm](http://notepad-plus.sourceforge.net/uk/site.htm)

On Linux systems I think they all default to the same encoding; kate, gedit, etc.

---

### Post by OffAxis on 2009-12-02
> It is routing the multicast through the correct NIC. 

Just out of curiousity, how did you go about setting up your route table?

Did you do it with route commands? 
Did you edit the /etc/dhclient.conf?
Does it maintain over a reboot?

I've never managed to get my multi-card setup quite right; if you could enlighten me as to how you did it, I would be grateful.

---

### Post by TheCook on 2009-12-02
Re routing, I use route commands in /etc/rc.local.  The only reason I need route commands is because the system insists on making the wrong card default e-v-e-r-y t-i-m-e (it has done so on a few computers and on a few different versions).  As I would like the fast NIC to service the front end(s) and the slow ethernet port to service the streams I am stuck with needing to change the default.  So all I do is delete the old default and add a new default.

The two commands are:
route del default gw 192.168.0.1 dev eth1
route add default gw 192.168.100.100 dev eth0

OffAxis, I would love to see what the channels should look like in mysql.  Maybe I can put them in manually... need to study up some more on mysql.

Does the channel scan need to have the streams available to do the scan or does it just translate the m3u straight into the correct mysql table?  What program does the scan? maybe I can do a crash course and scan the program for errors.:D

---

### Post by OffAxis on 2009-12-02
I haven't dumped the tables out of 9.10 yet, but in 9.04 it looks like there's 4 tables of interest;

**callsignnetworkmap** (it's only got two fields, callsign and network. I had zero records in this) I have no idea what it does.
**capturecard** - describes the setup of the capture card (in our case ties the .m3u to the NIC)
**cardinput** - looks like it ties the capture card to the source id (and starting channel)
**channel** - channel table, which ties a channel number to a source id

I've attached my first 10 channels from the 'channels' table. I dumped it with phpmyadmin as an update query (to the channels table)

---

### Post by TheCook on 2009-12-03
This one says there has been a fix to the scan issue.

[http://ubuntuforums.org/showthread.php?t=1325556](http://ubuntuforums.org/showthread.php?t=1325556)

I'll give it ago tonight and respond

---

### Post by TheCook on 2009-12-04
No Luck.

I'll just sit and wait I think.  Hopefully the DVB-T dongle can record enough playschool to keep little miss off my back.

---

### Post by OffAxis on 2009-12-07
No luck on my end either.

I've upgraded another system to 9.10, this time setting the 'mythbuntu-repos' package to use the .23 sources.

Still nothing.

---

### Post by OffAxis on 2009-12-07
found a bug ticket:

[http://svn.mythtv.org/trac/ticket/7722#comment:1](http://svn.mythtv.org/trac/ticket/7722#comment:1)

---

### Post by thestevee on 2009-12-08
hey,

i have more or less the same problem after upgrading to 9.10 and trying to scan for .m3u channels. it worked flawlessly in 9.04.

---

### Post by TheCook on 2009-12-09
Yep,

If you can get the scan to work in 9.10 let me know.  At least it is on the list to be fixed.

---

### Post by TheCook on 2010-01-19
Just thought I'd ask again.

Has anyone managed to get .m3u channel sacanning to work on 9.10

---

### Post by nickrout on 2010-01-19
I suggest you search the mythtv-users mailing list archives at [http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/) or join that mailing list and ask there. You are FAR more likely to find someone who knows the answer there than you are here.

---

### Post by thestevee on 2010-05-16
> **TheCook said:**
> Just thought I'd ask again.

Has anyone managed to get .m3u channel sacanning to work on 9.10

I thought i'd ask again: anybody having success with an m3u channel scan for mythtv of 10.04 lucid?

---

### Post by ian dobson on 2010-05-16
Hi,

I think I have the m3u scanner working on both 9.10 and 10.04, or atleast I managed to record F1 today from my freebox ethernet recorder.

Since I got the freebox up and running (I used the channel scanner to read in most of the channels the first time) I just manually edit the channels table as everytime I run myth-setup I need to reboot the backend before it'll find the tuners again.

Regards
Ian Dobson

---

### Post by thestevee on 2010-05-17
aha, good to hear.
can you provide a part of your m3u file... just to try it on my machine?
thanks!

---

### Post by ian dobson on 2010-05-17
Hi,

Note I'm using vlc to stream the video from my IP receiver to the backend and convert it to a udp stream that mythtv can use.

I have a script that does the channel changing, but you just need to get the last line setup correctly.

I had a problem on my backend that apache didn't start early enough/before the backend, so I added a loop that checked if port 80 is open and if not it waits abit longer.

Note the first line of the file must be #EXTM3U

```

#EXTM3U
#EXTINF:0,90000 - XXXX
#EXTMYTHTV:xmltvid=YYYY
udp://127.0.0.1:9001

```

Regards
Ian Dobson

---

### Post by thestevee on 2010-05-19
Thank you Ian for the help!
Now it works for me, although I don't exactly understand why. I put the the .m3u file in /var/www ([http://www.mythtv.org/wiki/Dreambox-NetworkRecorder](http://www.mythtv.org/wiki/Dreambox-NetworkRecorder)), which gave me a nice URL to paste into the Backend's channel scanner. It used to recognize file paths in earlier versions, however. 

What confused me all along was the error message of invalid channel header... which made no sense. But I think that this is the common return for file not found.

And I used to see the imported channels during a channel scan for my .m3u playlist. Today I saw nothing and it looked like it failed, but the channels were in the channel editor.
Cool, that it works now.

---

