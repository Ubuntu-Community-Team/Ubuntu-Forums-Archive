---
title: "flvstreamer in 11.10"
date: 2012-03-12
forum: Multimedia Software
---

### Post by paulemony on 2012-03-12
Installed:

/usr/bin/get_iplayer
/usr/bin/flvstreamer
/usr/bin/get_flash_video
/usr/bin/rtmpdump

No problem downloading BBC progs from IPlayer but how to do same with 4oD and Demand5? Just need basic terminal commands please!:confused:

---

### Post by ron999 on 2012-03-13
> **paulemony said:**
> ... but how to do same with 4oD and Demand5? Just need basic terminal commands please!
Hi
Some of those programmes can be downloaded using RTMPDump... when you've worked out the commands.;)
Information is in post **#10** here ---> [http://ubuntuforums.org/showthread.php?t=1536508]("http://ubuntuforums.org/showthread.php?t=1536508")

---

### Post by paulemony on 2012-03-13
I saw that and lots of other stuff via Google & decided I wasn't going to live long enough, hence my plea for the basic commands (beginning to think there aren't any).
In brief, if a BBC tv prog can be recorded using **get_iplayer [http://blah.blah.blah/b002a23a.shtml](http://blah.blah.blah/b002a23a.shtml)** what is the equivalent entry using the url of a 4oD or Demand5 prog?

---

### Post by ron999 on 2012-03-13
> **paulemony said:**
> 
In brief, if a BBC tv prog can be recorded using **get_iplayer [http://blah.blah.blah/b002a23a.shtml](http://blah.blah.blah/b002a23a.shtml)** what is the equivalent entry using the url of a 4oD or Demand5 prog?
Hi
There isn't an equivalent entry.
**get_iplayer** is designed to download programmes from _**BBC**_.

---

### Post by paulemony on 2012-03-13
Exactly my point, what is the entry using the *applicable* software (e.g. flvstreamer)? In other words, how do *you* download non-BBC videos? It's very frustrating knowing that you've downloaded software that will do exactly what you want but nobody seems to be able to tell you how to switch it on! For example get Iplayer has an excellent idiot-proof manual [http://linuxcentre.net/getiplayer/documentation](http://linuxcentre.net/getiplayer/documentation) which tells you more than you ever wanted to know about recording BBC progs, but if you want to record anything else...well here I am...

---

### Post by ron999 on 2012-03-13
> **paulemony said:**
> In other words, how do *you* download non-BBC videos?
Me, I use the method shown in post **#10**. :cool:

Each video needs a different set of parameters to use in the RTMPDump command.
(RTMPDump is flstreamer's big brother).

I have to work out the command each time... using the method shown in post **#10**. ;)

There's an example command, if you're interested.
Just copy and paste. :)
It's here ---> [http://pastebin.com/Uht8tB6p]("http://pastebin.com/Uht8tB6p")

---

### Post by paulemony on 2012-03-13
I picked a 4oD prog at random on the website & tried the instructions on the link:
[B]1
Start the server with this command:-
Code:
sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -j REDIRECT && rtmpsrv
2
See the message in console:-
Streaming on rtmp://0.0.0.0:1935

3
Refresh the page and play the video, now wait till the RTMPDump command appears in console.

4
Interrupt the server:- Ctrl-c

5
Stop the server with this command:-
Code:
sudo iptables -t nat -D OUTPUT -p tcp --dport 1935 -j REDIRECT
6
Copy and paste the RTMPDump command to download the video.[/B]

With this result:


[B]paulemony@ubuntu:~$ sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -j REDIRECT && rtmpsrv
[sudo] password for paulemony: 
RTMP Server v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu; license: GPL

Streaming on rtmp://0.0.0.0:1935

rtmpdump -r "rtmpe://ak.securestream.channel4.com:1935/4oD?auth=da_ajamczbLaidKc1cZcUdeaodIcccrbibR-bpx.b1-eS-mxO-pYrfs4q6ngkcqVn9o8n9mdrf&aifp=v002&slist=assets/CH4_08_02_900_51492001001001_001.mp4" -a "4oD?auth=da_ajamczbLaidKc1cZcUdeaodIcccrbibR-bpx.b1-eS-mxO-pYrfs4q6ngkcqVn9o8n9mdrf&aifp=v002&slist=assets/CH4_08_02_900_51492001001001_001.mp4" -f "LNX 11,1,102,63" -W "http://www.channel4.com/static/programmes/asset/flash/swf/4odplayer-11.21.2.swf" -p "http://www.channel4.com/programmes/china-triumph-and-turmoil/4od#3298532" -C O:1 -C O:0 -y "mp4:assets/CH4_08_02_900_51492001001001_001.mp4" -o CH4_08_02_900_51492001001001_001.flv

Closing connection... done!

ERROR: Handshake failed
Closing connection... RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

Connecting ...
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

WARNING: HandShake: Type mismatch: client sent 6, server answered 8
INFO: Connected...
Duplicate request, skipping.
Closing connection... ERROR: RTMP_ReadPacket, failed to read RTMP packet header
done!

^CCaught signal: 2, cleaning up, just a second...
ERROR: Handshake failed
Closing connection... done!

paulemony@ubuntu:~$ sudo iptables -t nat -D OUTPUT -p tcp --dport 1935 -j REDIRECT
[/B]

No idea if that's what's supposed to happen, but if it is what's the RTMPDump command and where is it pasted?

---

### Post by paulemony on 2012-03-13
OK tried that with my 4oD example:

[B]paulemony@ubuntu:~$ rtmpdump -r "rtmpe://ak.securestream.channel4.com:1935/4oD?auth=da_ajamczbLaidKc1cZcUdeaodIcccrbibR-bpx.b1-eS-mxO-pYrfs4q6ngkcqVn9o8n9mdrf&aifp=v002&slist=assets/CH4_08_02_900_51492001001001_001.mp4" -a "4oD?auth=da_ajamczbLaidKc1cZcUdeaodIcccrbibR-bpx.b1-eS-mxO-pYrfs4q6ngkcqVn9o8n9mdrf&aifp=v002&slist=assets/CH4_08_02_900_51492001001001_001.mp4" -f "LNX 11,1,102,63" -W "http://www.channel4.com/static/programmes/asset/flash/swf/4odplayer-11.21.2.swf" -p "http://www.channel4.com/programmes/china-triumph-and-turmoil/4od#3298532" -C O:1 -C O:0 -y "mp4:assets/CH4_08_02_900_51492001001001_001.mp4" -o CH4_08_02_900_51492001001001_001.flv
RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
WARNING: HandShake: Type mismatch: client sent 6, server answered 9
WARNING: HandShake: Server not genuine Adobe!
ERROR: RTMP_Connect1, handshake failed.
[/B]

So we're on the road but what's the problem; what's a handshake & why has it failed?

---

### Post by paulemony on 2012-03-13
P.S. I also tried your example & it worked.

---

### Post by ron999 on 2012-03-13
> **paulemony said:**
> 
So we're on the road but what's the problem; what's a handshake & why has it failed?
Hi
Test your method again with this video here:- [http://video.nytimes.com/video/2012/03/12/opinion/100000001423494/bike-thief.html]("http://video.nytimes.com/video/2012/03/12/opinion/100000001423494/bike-thief.html")


ITV and Channel4 can be tricky :mad:
Maybe you will need to upgrade RTMPDump to v2.[COLOR="Red"]4[/COLOR] for those sites.

---

### Post by paulemony on 2012-03-13
Tried your NYT bike thief video:

[B]Closing connection... done!

RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Duplicate request, skipping.
Closing connection... ERROR: RTMP_ReadPacket, failed to read RTMP packet header
done![/B]

rtmpdump version installed is 2.3-1 from Synaptic, but [http://rtmpdump.mplayerhq.hu/](http://rtmpdump.mplayerhq.hu/) states "The latest release is 2.4 ....RTMPE type 9 handshakes are now supported" so I suppose that's the answer...will report result....

---

### Post by paulemony on 2012-03-14
Removed 2.3 & downloaded 2.4 tar file from [https://launchpad.net/ubuntu/precise/+source/rtmpdump/2.4~20110711.gitc28f1bab-1](https://launchpad.net/ubuntu/precise/+source/rtmpdump/2.4~20110711.gitc28f1bab-1)
Extracted into Downloads & used yr entries in [http://ubuntuforums.org/showthread.php?t=1536508](http://ubuntuforums.org/showthread.php?t=1536508) post6:

$ make SYS=posix
$ sudo make install

When I tried entries from post 10 in [http://ubuntuforums.org/showthread.php?t=1536508](http://ubuntuforums.org/showthread.php?t=1536508) sure enough it showed as 2.4 but still no joy:

[B]rtmpdump -r "rtmpe://ak.securestream.channel4.com:1935/4oD?auth=da_cUbpaJbebEcddOaIcLaUb_dVaYbHbucF-bpyp0Z-eS-jyR-pfoekanWjao4rRqVmaqakVnU&aifp=v002&slist=assets/CH4_08_02_900_53994009001002_001.mp4" -a "4oD?auth=da_cUbpaJbebEcddOaIcLaUb_dVaYbHbucF-bpyp0Z-eS-jyR-pfoekanWjao4rRqVmaqakVnU&aifp=v002&slist=assets/CH4_08_02_900_53994009001002_001.mp4" -f "LNX 11,1,102,63" -W "http://www.channel4.com/static/programmes/asset/flash/swf/4odplayer-11.21.2.swf" -p "http://www.channel4.com/programmes/the-daily-show-with-jon-stewart/4od" -C O:1 -C O:0 -y "mp4:assets/CH4_08_02_900_53994009001002_001.mp4" -o CH4_08_02_900_53994009001002_001.flv

Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

RTMPDump v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

Connecting ...
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

WARNING: HandShake: Type mismatch: client sent 6, server answered 8
INFO: Connected...
Duplicate request, skipping.
Closing connection... ERROR: RTMP_ReadPacket, failed to read RTMP packet header
done!

^CCaught signal: 2, cleaning up, just a second...
ERROR: Handshake failed
Closing connection... done!
[/B]   

Neither of your NYT examples work either, now.

Have I missed something?

---

### Post by ron999 on 2012-03-14
> **paulemony said:**
> used yr entries in [http://ubuntuforums.org/showthread.php?t=1536508](http://ubuntuforums.org/showthread.php?t=1536508) post6:

$ make SYS=posix
$ sudo make install
Hi
That method is too old.
RTMPDump should be compiled from git now.

Copy and paste two commands.

First command:-

```
sudo apt-get install \
build-essential \
git checkinstall
```

Then second command:-

```
cd ~/ && \
git clone git://git.ffmpeg.org/rtmpdump && \
cd rtmpdump && \
version="$(git log -1 --abbrev-commit | grep commit | cut -d' ' -f2)" && \
make VERSION="v2.4\ $version" && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname rtmpdump \
--pkgversion "2.4+git$(date +%Y%m%d)" --backup=no --default && sudo ldconfig
```

When it's finished...
rtmpdump folder in Home - delete it.
rtmpdump deb on Desktop - keep it.

RTMPDump v2.4 will be installed at:-
/usr/local/bin/rtmpdump

```
@ubuntu:~$ rtmpdump -h
RTMPDump v2.4 7340f6d
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
```


> **paulemony said:**
> Have I missed something? usr/bin/rtmpdump and usr/bin/get_flash_player no longer exist.
get_flash_videos was probably uninstalled when you uninstalled RTMPDump v2.3.
You need to re-install it again.

---

### Post by paulemony on 2012-03-14
Did that, guess what:

[B]paulemony@ubuntu:~$ sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -j REDIRECT && rtmpsrv
[sudo] password for paulemony: 
RTMP Server v2.4 7340f6d
(c) 2010 Andrej Stepanchuk, Howard Chu; license: GPL

Streaming on rtmp://0.0.0.0:1935

rtmpdump -r "rtmpe://ll.securestream.channel4.com:1935/a4174/e1" -a "a4174/e1" -f "LNX 11,1,102,63" -W "http://www.channel4.com/static/programmes/asset/flash/swf/4odplayer-11.21.2.swf" -p "http://www.channel4.com/programmes/homeland/4od" -C O:1 -C O:0 -y "mp4:xcuassets/CH4_08_02_900_52804004001002_001.mp4?e=1331770117&h=d3abf60cc59270de97200efad11f3e7d" -o CH4_08_02_900_52804004001002_001.flv

Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

WARNING: Trying different position for client digest!
ERROR: WriteN, RTMP send error 32 (1536 bytes)
ERROR: Handshake failed
Closing connection... done!

RTMPDump v2.4 7340f6d
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
WARNING: HandShake: Type mismatch: client sent 6, server answered 8
INFO: Connected...
Duplicate request, skipping.
Closing connection... done!

ERROR: RTMP_ReadPacket, failed to read RTMP packet header
ERROR: Handshake failed
Closing connection... done!

ERROR: Handshake failed
Closing connection... done!

[/B]

My goodness linux can be hard work! I've spent hours on this (& wouldn't have bothered if I'd known), I think I need a break....

---

### Post by paulemony on 2012-03-14
OK back again, you have to understand that I am computer-literate to the extent that I understand what has to be done but I often have ABSOLUTELY NO IDEA WHATSOEVER how to do it. When you say "That method is too old. RTMPDump should be compiled from git now." what exactly does that apply to, does it mean if rtmpdump has *never* been installed then those 2 commands are all that's needed to install & use it (if only!) or does it mean that that the tar file still has to be downloaded & extracted as before but the old commands;
[B]$ make SYS=posix
$ sudo make install[/B]
are now replaced with the new ones? Or does it mean something else? If so what? All I've come up with so far is:
******  Installation failed. Aborting package creation.**
Seems odd to me that bunch of bright people would go to the trouble of writing a program & then assume that everybody would know how to use it without needing to be told.

---

### Post by ron999 on 2012-03-14
> **paulemony said:**
> Did that
Use command [SIZE="3"][FONT="Courier New"]**rtmpdump -h**[/FONT][/SIZE]

If you see [COLOR="Red"]RTMPDump v2.4 7340f6d[/COLOR] it means you've successfully installed the latest version of RTMPDump that's available.:p

Practice the downloading method at an easy website such as NYT.

Leave Channel4 till you're confident.

---

### Post by paulemony on 2012-03-15
Having thoroughly confused myself I removed 2.4 & reinstalled by right-clicking on rtmpdump folder on desktop & using software centre (despite apocalyptic warnings of what might happen if I did), & reinstalled get_flash_videos from synaptic, so now I have rtmpdump 2.4 and get_flash_videos 1.24. Now if I try to record the NYT bike thief video nothing happens, the command doesn't appear, anything else gives error message "Segmentation fault". A bit of googling suggests this may be related to the fact I have both **/usr/local/lib/librtmp.a** and **/usr/local/lib/librtmp.so** but no definitive fix.

---

