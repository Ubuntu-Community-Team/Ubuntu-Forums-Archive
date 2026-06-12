---
title: "New mythbuntu 10.10 client install hangs on stop video"
date: 2011-07-02
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2011-07-02
This is a new Mythbuntu 10.10 64bit install on a custom system running Windows 7 Home Premium, a Windows HTPC. Because Mythtv Windows cannot display recordings from 0.24 fixes back-end without stuttering, I added a Mythbuntu 10.10 64bit front end. After fixing all the little connection, mysql, video driver glitches, and changing the computer name for the Mythbuntu boot &#8943; I can now watch recording on the remote client.

Except when I stop the recording, mythtv hangs with frozen frame short segment of audio repeating.  I either have to hard boot or pop open a console and kill mythfrontend using HTOP.

Kinda stumped on this one:confused:

Any ideas on what to try?

---

### Post by ian dobson on 2011-07-03
Hi,

What graphic card/driver are you using?

Regards
Ian DObson

---

### Post by keepitsimpleengr on 2011-07-03
Hi Ian...

So to pass the time, I decided to reinstall Mythbuntu 10.10, and got two successive install failures.  (The original did install, so this is unexpected, although during the latter installs I got a Ubiquity crash.)  These were installed from the mythbuntu-10.10-desktop-amd64 CD.  

So then I installed from ubuntu-10.10-desktop-amd64 CD, updated, installed Mythtv fixes/0.24.1 from the Ubuntu repositories.  Now I'm getting really squirrelly behavior.  My frustration level is approaching MS Vista levels.

> **ian dobson said:**
> Hi,

What graphic card/driver are you using?

Regards
Ian DObson
In answer to your question, the mobo is a Foxconn A88GMV AM3 AMD 880G HDMI Micro ATX AMD with on-board ATI Radeon HD 4250.  It was originally in my first Mythbuntu build ([http://ubuntuforums.org/showthread.php?t=1587584]("http://ubuntuforums.org/showthread.php?t=1587584")) along with an EVGA GeForce GT 240 Superclocked 512MB 128-bit GDDR5 Express, and this build was successful.  The A88GMV was surplussed in an upgrade, and became available for this second HTPC, in the bedroom with Win7 WMC.

The original HTPC was a 10.04 install immediately upgraded to 10.10 because of a compile problem with drivers for the Hauppauge WinTV-HVR-2250 tuner card, and because of an evil quirk with the EVGA GeForce GT 240 when installing 10.10. I'm pondering the possibility that 10.10 is jinxed. 

[INDENT]My original HTPC with the nVidia 240 hasn't been a trip down the primrose path, getting the HDMI audio to work has been a pain in the neck.  Just last week it inexplicably quit working, and it took quite a bit of finagling to fix it.  Some upgrade surreptitiously reset the ALSA mixer S/PDIF output to one that didn't work. 

This HTPC works beautifully and is a joy in my life.  :guitar:[/INDENT]

So now I'm mulling getting a ZOTAC GeForce 8400 GS 512MB because it's cheap, it's nVidia and it's half height, and it might solve some of my headaches.

My 64 bit workstation (on which I have a Mythtv client) has a nVida 260 GTX.  No problems with the sound but then no HDMI either.  It started out as dual SLI 8800GTXs, which died and were replaced under warranty with two 260's&#8943;one of which was DOA and replaced&#8943;and subsequently one of the 260's has died.  I suspect PNY sent me re-furbished 260s.  All this is to say I tend to nVidia but I am definitely not a fanboy.

My 32bit workstation runs a Radeon HD 4650, and has been trouble free but then I really don't ask too much of it.  

The current plan is to give it a day or two rest, then decide what to do next.

Any thoughts or suggestions would be welcomed :D

---

### Post by keepitsimpleengr on 2011-07-10
The ZOTAC GeForce 8400 GS 512MB arrived, was installed and worked great on the Win7 WMC & Netflix streaming via IE/Silverlight.

Getting it to work on the Mythtv (24.1) has been a little troublesome.  Thanks to tjones00 [http://ubuntuforums.org/showthread.php?t=1668737]("http://ubuntuforums.org/showthread.php?t=1668737") I got the nVidia HDMI working.

Now the problem is audio drop-outs during Mythtv liveTV or recording play back.  The dropputs are very long - not like stuttering.

My effective bandwith on this wireless link is 20+Mb/sec three times more than the 7Mb/s Mythtv uses..

Any thots?

---

### Post by ian dobson on 2011-07-10
Hi,

The problem with wireless is the latency (when other users are using the wireless connection the bandwith drops to almost 0 and the delay goes through the roof).

What messages to you see in your log files (/var/log/mythfrontend.log)

Regards
Ian Dobson

---

### Post by nickrout on 2011-07-13
> **keepitsimpleengr said:**
> The ZOTAC GeForce 8400 GS 512MB arrived, was installed and worked great on the Win7 WMC & Netflix streaming via IE/Silverlight.

Getting it to work on the Mythtv (24.1) has been a little troublesome.  Thanks to tjones00 [http://ubuntuforums.org/showthread.php?t=1668737]("http://ubuntuforums.org/showthread.php?t=1668737") I got the nVidia HDMI working.

Now the problem is audio drop-outs during Mythtv liveTV or recording play back.  The dropputs are very long - not like stuttering.

My effective bandwith on this wireless link is 20+Mb/sec three times more than the 7Mb/s Mythtv uses..

Any thots?

Until you do anything else on the network, or someone starts the microwave, or your neighbours are on the same channel, plus the latency that Ian referred to. There is not a lot of future in using wireless for mythtv. Even powerline is better, but a real cat5/6 cable is what you really want.

---

### Post by keepitsimpleengr on 2011-07-13
> **ian dobson said:**
> What messages to you see in your log files (/var/log/mythfrontend.log)

Yikes, Ian…

I had this nice long post as an answer, and it went to write-only memory.

So I'll try again (and save a copy)

The good news there are no wifi nets in the neighborhood and the only user here is me, so there'll be little problems with that.

The bad news is that there are two access points here, DD-WRT/WRT54GLs and I use Rosewill RNX-G300EX PCI for the htpcs.

```
htpc/server&#8943;*wifi*&#8943;AP&#8213;*lan*&#8213;AP&#8943;*wifi*&#8943;htp/client
                      &#9500;WrkSta/client
                      &#9584;Untangle Firewall&#9472;Cablemodem=cloud
```

I have changed locations of the APs to my best estimate of good RF, and I have set AP parameters to optimize streaming video and running on channels 1 and 6.  The result is SNRs around 80-75, down from 20-30.

The results where improvement but still occasional skips.  Swapping AP hardware produced the same result.

The 1st AP has worked well (htpc/server&#8943;*wifi*&#8943;AP&#8213;*lan*&#8213;WrkSta/client), even before Ituned and arranged the APs.  I do pretty much everything on the htpc from my workstation including VNC.

So I tried htpc/server&#8213;*lan*&#8213;AP&#8943;*wifi*&#8943;htpc/client and still got the same results.

Using the wifi for remote administration of the htpc/client has also been a little shaky…

At this point I suspect a marginal RNX-G300EX so I'm getting a TP-Link TL-WN722N Wireless USB Adapter to test.

nickrout-I'm still optimistic that wifi can work since it has worked well with the htpc/server htpc/server&#8943;*wifi*&#8943;AP&#8213;*lan*&#8213;WrkSta/client.  Others might heed his advice because I'm in a more or less ideal wifi environment, a quiet, older suburban neighborhood with big lots and single story homes-and low geek density

Now from the log (…55 is htpc/server)

```
2011-07-11 09:19:40.700 Player(0): Waited 100ms for video buffers AAAAAAALAAAAAfAAA
2011-07-11 09:19:40.709 Player(0): Waited 100ms for video buffers AAAAAAALAAAAAfAAA
2011-07-11 09:19:40.811 Player(0): Waited 100ms for video buffers AAAAAAALAAAAAfAAA
2011-07-11 09:19:40.813 RingBuf(myth://192.168.0.55:6543/1131_20110711091911.mpg): Waited 0.2 seconds for data 
			to become available... 0 < 32768
2011-07-11 09:19:40.820 Player(0): Waited 100ms for video buffers AAAAAAALAAAAAfAAA
2011-07-11 09:19:40.829 Player(0): Waited 100ms for video buffers AAAAAAALAAAAAfAAA
```

There were hundreds of "Player(0): Waited…" and the occasional "RingBuf(myth://192.168.…): Waited…"

From before tuning and placement

```
2011-07-10 15:26:49.636 Player(1): Waited 100ms for video buffers AAAAAAAffLAAAAAAA
2011-07-10 15:26:49.644 Player(1): Waited 100ms for video buffers AAAAAAAffLAAAAAAA
2011-07-10 15:26:49.646 Player(1): Waited 100ms for video buffers AAAAAAAffLAAAAAAA
2011-07-10 15:26:49.651 Player(1): Waited 100ms for video buffers AAAAAAAffLAAAAAAA
2011-07-10 15:26:49.654 Player(1): Waited 100ms for video buffers AAAAAAAffLAAAAAAA
2011-07-10 15:26:49.688 RingBuf(myth://192.168.0.55:6543/1061_20110709230000.mpg): Waited 15.5 seconds for data 
			to become available... 0 < 32768
2011-07-10 15:26:49.757 Player(1): Waited 100ms for video buffers AAAAAAAffLAAAAAAA
2011-07-10 15:26:49.764 Player(1): Waited 100ms for video buffers AAAAAAAffLAAAAAAA
2011-07-10 15:26:49.771 Player(1): Waited 100ms for video buffers AAAAAAAffLAAAAAAA
2011-07-10 15:26:49.774 Player(1): Waited 100ms for video buffers AAAAAAAffLAAAAAAA
```

This compared to the log from the htpc/server

```
2011-07-10 23:17:16.435 Player(a): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2011-07-10 23:17:16.440 Player(a): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2011-07-10 23:17:16.442 Player(a): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2011-07-10 23:17:16.545 Player(a): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2011-07-10 23:17:16.553 Player(a): Waited 100ms for video buffers AAAAAALAAAAAAAAAAAAAAAAAAAAAAAA
2011-07-10 23:17:16.555 Player(a): Waited 100ms for video buffers AAAAAALAAAAAAAAAAAAAAAAAAAAAAAA
2011-07-10 23:17:16.561 Player(a): Waited 100ms for video buffers AAAAAALAAAAAAAAAAAAAAAAAAAAAAAA
2011-07-10 23:17:16.563 Player(a): Waited 100ms for video buffers AAAAAALAAAAAAAAAAAAAAAAAALAAAAA
2011-07-10 23:17:16.568 Player(a): Waited 100ms for video buffers AAAAALuAAAAAAAAAAAAAAAAAALAAAAA
2011-07-10 23:17:16.571 Player(a): Waited 100ms for video buffers AAAAAUuALAAAAAAAAAAAAAAAALAAAAA
```

Thanks for the help, I'll post the results...

---

### Post by David Grigor on 2011-07-15
If you haven't done so already. Move it temporarily where you can hardwire it up to troubleshoot. Once you get it where there is no audio skipping etc. then you know it's your wireless connection.   

I tried it as well and ended up wiring every bedroom.

---

### Post by ian dobson on 2011-07-15
Hi,

Maybe try installing iperf on the frontend and backend and run it for a while, watching the transfer rates. Your problem looks like dropouts in the wireless signal.

with iperf, this is what I see over my gigabit lan:
```
 
iperf -c 192.168.0.3 -i 1

------------------------------------------------------------
Client connecting to 192.168.0.3, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.1 port 45127 connected with 192.168.0.3 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec  80.4 MBytes   674 Mbits/sec
[  3]  1.0- 2.0 sec  81.1 MBytes   681 Mbits/sec
[  3]  2.0- 3.0 sec  81.0 MBytes   679 Mbits/sec
[  3]  3.0- 4.0 sec  81.1 MBytes   681 Mbits/sec
[  3]  4.0- 5.0 sec  80.9 MBytes   678 Mbits/sec
[  3]  5.0- 6.0 sec  81.4 MBytes   683 Mbits/sec
[  3]  6.0- 7.0 sec  80.1 MBytes   672 Mbits/sec
[  3]  7.0- 8.0 sec  81.1 MBytes   681 Mbits/sec
[  3]  8.0- 9.0 sec  81.1 MBytes   681 Mbits/sec
[  3]  9.0-10.0 sec  81.2 MBytes   682 Mbits/sec
[  3]  0.0-10.0 sec   810 MBytes   679 Mbits/sec
```Regards
Ian Dobson

---

### Post by keepitsimpleengr on 2011-09-11
OK-solved.  Now I can watch the Mythbuntu client without drops & skips.

_Rehash_&#8943;

Mythbuntu client-server (in den) <&#8943;> wireless link 1 <&#8943;office LAN&#8943;> wireless link 2 <&#8943;> Mythbuntu\Win7 client (in bedroom).  [INDENT]The office LAN is fixed IP behind an Untangle firewall router.  There is another client on mythbuntu 10.10 computer in the office (which has always worked well).
[/INDENT]
Problem&#8213;Mythbuntu\Win7 client hangs with frozen frames, short segment of audio repeating.

Hardware&#8213;Rosewill RNX-G300EX IEEE 802.11b/g PCI Wireless Cards on client & client-server
[INDENT]&#8213;2 Linksys WRT54GL wireless broadband routers on LAN for link1 and link 2[/INDENT]

WRT54GL Firmware&#8213;DD-WRT v24-sp2(07/22/09) voip set up to act as an access point.

_Note_&#8943; many people advised this was an unworkable scheme, and in probably most cases it will be.

_Solution_&#8943; Set up DD-WRT with the following Wireless settings…

[INDENT]Basic Channel: Different fixed channels at least 4 difference, I use 6 & 11

Basic Sensitivity Range (ACK timing): 50

MAC filter use filter: Enable, Selected Permit only clients listed to access…
[INDENT]Requires adding MAC addresses in "Edit MAC Filter List"  This causes the 54GL's to ignore any but the listed MAC address, down side, no "guest" capability.[/INDENT]

Advanced Basic rate: All

Advanced CTS Protection Mode: Off

Advanced Frame Burst: Enable

Advanced Max associate clients: 4 for client link 2, 1 for clent-server link 1

Advanced AP isolation: Enable

Advanced Preamble: Short

Advanced Afterburner: On

Advanced Wireless GUI access: Off

Advanced WMM support: Off

Other settings: default for supplied firmware.
[/INDENT]
_Why I suspect this worked_&#8943; 
The 54GL Access Points's with the firmware's setting are set to handle a multiple client, wide area situation.  With these mods I reconfigured them for a small area, few client situation, disabling Advanced WMM probably the most important.  In addition, the client mythtv when used all other users of its access point are turned off except for a Skype phone. Also, the client-server is set up to allow other connections though it's LAN connection, and these are used to connect the TV and disc players, not used when client is being used.

---

