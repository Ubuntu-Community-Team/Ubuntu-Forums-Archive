---
title: "Streaming Buffering Difficulties"
date: 2010-07-20
forum: Mythbuntu
---

### Post by tmcgary on 2010-07-20
I am making some headway into a problem detailed in this thread: [http://ubuntuforums.org/showthread.php?t=1521188](http://ubuntuforums.org/showthread.php?t=1521188)

I have been able to get the video to <sort of> stream via VLC using the method provided by jlagrone in that thread. As the issue I am now having isn't directly related to the purpose of the other thread I decided to start a new thread.

However, VLC buffers, plays for a few seconds, then buffers again, lather rinse repeat. I am unable to get a very useful stream established. This has happened both over wireless G and with my client (a windows laptop) via Cat 5 at 100 Mbps.

I would love some help with ideas on how to troubleshoot this. I am unsure if its a hardware shortcoming or a software configuration issue.

My hardware:

FE/BE unit:
10.04 Lucid 2.6.32-22-generic
Dell Optiplex GX270
2.4 Ghz P4 Celeron CPU
2 Gb RAM
Nvidia 8400GS
2 x Western Digital 1 TB Black Caviar HDD SATA (houses media files)
1 x Western Digital 40 Gb HDD PATA (houses OS)

Client Laptop (Windows):
Windows XP Pro SP3
Dell Inspiron B120
1.40 Ghz Celeron CPU
1.24 GB RAM
Mobile Intel 915GM/GMS, 910GML Express Chipset

Router:
Linksys WRT54G
BE/FE wired in
Client usually is using WiFi. Could be wired.

Is this inability to keep a steady stream a shortcoming of the processor of the BE's CPU? Any direction on things to troubleshoot or debug logs to view would be appreciated. I am just unsure how to proceed. Thanks in advance!

Tom

---

### Post by tmcgary on 2010-07-23
Tried using the Top command from the client computer via putty. During playback the server's CPU Util jumps to .90 and the CPU% for mythweb.pl stays below 20%. I don't see anything in Top that would indicate a shortcoming in the BE's CPU or memory.

Other information that may be helpful:

The files are .m4v, each approximately 1 gig. Is this just too large for streaming over the internet?

---

### Post by jlagrone on 2010-07-26
If you're on your network, I can't really think of anything that would be causing a buffering issue.  You might check to see if there are any buffer or prebuffer settings in the player you are using and maybe tell it to buffer more or increase the memory available for buffering.

If you are going over the internet outside your network, you might check your upload speeds at home.  Mine typically stays around 512k for the first few minutes and then drops off to something lower.  If you can't upload it fast enough, it would continually have to stop and buffer.

As for size, I have streamed 2-3 Gb files over wireless, but have never tried over the internet.  As your ultimate goal is to stream to a phone, you might want to look scaling and encoding files to the native resolution or something close to it.  This should make for a smaller file so there may be less buffering.  Also I believe most modern phones have hardware decoding for mpeg2 and h.264 and maybe other formats.  Choosing a format the phone can decode with hardware will reduce battery usage.

---

### Post by tmcgary on 2010-07-26
So far I've been trying to just stream within my network. Furthermore, Speedtest.net states my upload is .96 Mbps. I'll try messing around with buffer/pre-buffer settings in VLC to see if I can get better results. Any other players for Windows that might be good?

---

### Post by tmcgary on 2010-07-27
After some experimenting in VLC I think I tracked the problem down to the video and audio being asynchronous. This leads to errors occuring in the VLC message log:

[http://pastebin.com/uXaF112X](http://pastebin.com/uXaF112X)

More reading of other error logs show "PTS out of range". When I looked this up I read many threads about sync issues. Basically, the video is lagging behind the audio (or the other way around as well).

When the file is played locally on the server no such issue exists. It is only over the network.

So: is the synchrony issue in the file itself or does it stem from a network setting?

I am going to try to re-encode some video with different settings and see if I can make any improvements. It is also worth noting that this phenomenon occurred with HDTV recordings make on the BE but not with SDTV recordings. The latter streamed fine. Thanks in advance!

---

### Post by ozybushwalker on 2010-07-27
Have you looked into CPU utilisation on your client (laptop)?

The client CPU is almost certainly fast enough to decode audio in real time but possibly isn't fast enough to decode HD video in real time. 

It might be useful to compare CPU utilisation on the client when streaming SDTV and HDTV.

---

### Post by tmcgary on 2010-08-23
Sorry for the lengthy hiatus in replying to this thread. I was off the grid for 2 weeks. 

@ozybushwalker: the client CPU util is only 15-20% during playback attempts. 

@jlagrone, et al: so far I have only attempted the streaming on the intranet.

**NEW DEVELOPMENT/DISCOVERY:** I went back to see if I can playback DVR'ed recordings, since that template formed the basis of the video (i.e. harddrive-saved, transcoded dvd's) streaming. I am able to stream SDTV recordings to VLC without any problem. However, when I try to playback HDTV content with VLC I get the following errors:

[http://pastebin.com/1Sp2tKqd](http://pastebin.com/1Sp2tKqd)

this is somewhat reminiscent of my previous pastebin posting.

These recordings were transcoded with MythTV using the auto/default transcoding (that code for I don't know what codec/file type these ended up, though they have mpg extensions). Furthermore, both the SD- and HDTV recordings play without error on the local FE/BE machine in which they are stored. 

[B]So, my questions:
[/B]Is this a VLC issue? If so, is there an alternative player for _*windows*_ I could try? Or is this a MythWeb issue? I searched the forum for a similar issue and found nothing of use; most issue similar were for local playback and they suggested buffering the sound card etc. I dont suppose that would help at all in my case. 

Lastly, could this be a recording issue.? I use the somewhat maligned Hauppauge HVR-1600 to record clear-QAM. Could the sync issues stem from poorly recording/weak signal strength recorded material? My (newbie) opinion is that it could not be, as they play on the local be/fe without any sync issues and the SDTV plays perfectly streaming over the intranet. 

Thanks for any help!

---

### Post by tmcgary on 2010-08-23
One more piece of info that may be helpful:

Viewing the HDTV content over the intranet worked before, in 9.04, using the same client and server. Is anyone of aware any changes in mythweb/mythtv in 10.04 that may precipitate the sync issues? Any changes in VLC in that same timeframe? Thanks again!

---

### Post by ian dobson on 2010-08-23
Hi,

Can you try ftping from the server to your client to see what bandwidth your really getting.

The errors your seeing usualy mean a corrupt media file/stream.

Regards
Ian Dobson

---

### Post by tmcgary on 2010-08-23
Ian,

thanks for giving me some direction. Once I am able to FTP in, how do I observe my bandwidth?

Do you suspect the files are corrupted or the stream? The files would surprise me as they play locally on the FE/BE, but my knowledge is quite limited. Thanks again!

Tom

---

### Post by ozybushwalker on 2010-08-23
ftp clients usually report the bandwidth at completion of the transfer. For example:

ftp> get 2010-03-15-cat-wd0e.gz
local: 2010-03-15-cat-wd0e.gz remote: 2010-03-15-cat-wd0e.gz
200 PORT command successful
150 Opening BINARY mode data connection for 2010-03-15-cat-wd0e.gz (2409995765 bytes)
226 Transfer complete
2409995765 bytes received in 21654.62 secs (108.7 kB/s)


You may be getting errors on the network. If you are streaming over TCP the error should cause the receiver to discard the packet (in hardware or software). After sending a block of data, TCP expects to receive an acknowledgement. If the acknowledgement doesn't arrive "soon enough" TCP will retransmit. If the receiver has "enough" buffering it won't notice the occasional data loss. Transferring a large file can give an idea of the network performance over a significant enough time period. In the above ftp, the server and client were largely idle over the transfer. This suggests that would be a struggle to stream video across this network segment at 1Mbps (108kB/s is quite a bit less than 1Mbps). The ftp test doesn't really help if your network has occasional spikes in utilisation or error rates.

---

### Post by tmcgary on 2010-08-23
This is embarrassing but...

I haven't used FTP in a long time, but figured it would be like riding a bike. I installed FileZilla Server on the Windows Laptop (lets not call this client anymore:D) and FileZilla Client on the FE/BE. I figured fire the server app up and login, no prob. 

Well I kept getting time outs. Each computer can ping each other just fine. The windows laptop can get onto mythweb fine. Even using the FTP from the linux terminal gets me a time out. I went into windows firewall and enabled FTP server-still nothing but time outs.

Finally, last ditch I turned the annoying winblows firewall off and the FTP works without problem. Transfers rates for a ~35 MB file were 2450 Kb/s-2700 Kb/s. I will try larger (1 GB+) file tomorrow morning and report back. I tried to stream HDTV from mythweb with the firewall off and it gave the same VLC errors as in my pastebin.

Any additional thoughts?

<edit>Upon further review, I needed to enable wireless network ports in windows firewall which allowed it to run successfully while on. Additionally I was able to get FTP from the linux terminal to work (once I figured out the syntax etc for everything) and got this read out:

ftp> get MVI_0961.MOV
local: MVI_0961.MOV remote: MVI_0961.MOV
200 Port command successful
150 Opening data channel for file transfer.
WARNING! 143444 bare linefeeds received in ASCII mode
File may not have transferred correctly.
226 Transfer OK
33555728 bytes received in 14.91 secs (2198.5 kB/s)

not sure what that error message means...

---

### Post by tmcgary on 2010-08-24
FTP specs for a 2 GB file:

ftp> get Big_File.ISO
local: Big_File.ISO remote: Big_File.ISO
200 Port command successful
150 Opening data channel for file transfer.
WARNING! 10294279 bare linefeeds received in ASCII mode
File may not have transferred correctly.
226 Transfer OK
2145630208 bytes received in 881.67 secs (2376.6 kB/s)

I tried to play this file back in both xbmc and in VLC and both failed. The message log for VLC is here:

[http://pastebin.com/Q2J23dky](http://pastebin.com/Q2J23dky)

It should  be noted that this file is normally stored on the FE/BE and was then transferred via USB thumb drive to my windows laptop for the FTP test. I verified that Big_File.ISO played on the FE/BE before transfer and on the Laptop after the USB thumb drive transfer.

So clearly something is getting messed up during the FTP transfer. But why would this not affect music playback and SDTV playback via mythweb over the same network infrastructure?? Any thoughts on culprits? Is a 6 year old router likely or is something else at play?

---

### Post by ian dobson on 2010-08-24
Hi,

When you transfer a binary file per FTP you need to tell FTP (or atleast your client) that it's a binary file (8bit and not 7bit).

If you transfer a binary file in 7bit mode the 8th bit will be reset damaging the file.

Regards
Ian Dobson

---

### Post by tmcgary on 2010-08-24
Thanks ian! I figured it was that. I never tinkered much with those types of settings. Will redo and see what happens. Thanks again

---

### Post by tmcgary on 2010-08-24
Update: using binary fixed the playback. The transfer rate was also the  same at ~2.4 MB/s. Should this be sufficient to stream HDTV on my  intranet?

@ozybushwalker: Is there a way to observe where network/TCP errors may be occuring? 

Whats my next move?

---

### Post by tmcgary on 2010-08-25
New development:

My FE/BE also dual-boots into windows XP. On a hunch, I booted into XP downloaded and installed DvdFab 8 and transcoded an .iso already present into a .avi. 17 hours later I booted back to mythbuntu and then streamed the file to my windows laptop client. It streamed to VLC without any sync issues whatsoever.

I was using handbrake for linux to x264. Are there known issues with that program or setting? I will try to re-encode a couple other movies to make sure this wasnt an abberation. I will be out of town for a few days beginning tomorrow but will try to check back for responses. 

ozybush, ian and jlagrone: thanks for your help thru all this stuff!!

---

### Post by ian dobson on 2010-08-25
Hi,

I've used handbrake afew times to transcode and never had any real compatibility problems with it (I don't transcode any more, it's easier to just add more harddisks :D ).

What transcode options did you use? And what version of handbrake?

Regards
Ian Dobson

---

### Post by tmcgary on 2010-08-26
I was used Handbrake SVN 3428 because of issues with 10.04. I hadnt checked in a while if there was a "stable" (not sure what the proper term I'm looking for here is) release that fixed the problems with 10.04 since I downloaded the SVN in June or so. I was using the the 'normal' settings on Handbrake for x264. 

To clarify the successful .avi was using h264. 

The thing that leaves me confused is: why does streaming of HDTV recordings still not work??

---

### Post by ian dobson on 2010-08-26
Hi,

All I can think of is that HD h264 recordings have a higher bitrate than "normal" SD mpeg2 recordings (10Gb/Hour for HD against 2.5Gb hour for SD).

Other than this I don't know.

Regards
Ian Dobson

---

