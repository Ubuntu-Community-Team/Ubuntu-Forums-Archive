---
title: "error opening jump program file"
date: 2009-11-01
forum: Mythbuntu
---

### Post by B34N on 2009-11-01
I finally got Mythbuntu up and running and after tweaking some settings, I'm now getting the message "error opening jump program file" whenever I try to watch TV.  I'm guessing that it has something to do with the fact that one of the settings I changed was to change the channel when I hit the up/down arrows but I believe that I put everything back to the way it was and yet the error still remains.  Any thoughts?

Thank you

Edit: I didn't actually solve it, I just did a fresh reinstall.  I saw this error posted in a few other posts and no one received a fix.

---

### Post by B34N on 2009-11-15
It's happening again.  This time I didn't make any changes.   I have one frontend/backend and two frontends.  It happens on all three so I'm guessing it's a backend problem.  Any thoughts?

---

### Post by Nisitiiapi on 2009-11-16
I have this exact same problem.  Everything seemed fine for a few days and now this error.  A clean install did not fix it (even repartitioned and reformatted).  Interestingly, recording is not a problem.  I can record a show and watch it without a problem.  I can even watch it while it's recording.  So, it is purely a problem with Live TV and it doesn't matter if I try to tune a channel manually or from the Program Guide. I haven't been able to find any solution, but occasionally, if I try Watch TV, I'll get it to work (not even 10% of the time, though, unfortunately).

I'm not sure whether it's a frontend or backend problem.  The error shows in the frontend logs, but if you are having the issue on all frontends, it would seem like a backend issue.

Here are excerpts from mythbackend and mythfrontend logs.  I see in the frontend logs, "NVP::OpenFile(): Error, couldn't read file: /mythtv/livetv/1002_20091116042653.mpg
NVP(0), Error: JumpToProgram failed.
NVP(0), Error: Unknown recorder error, exiting decoder"
I'm thinking this is the jump error.
```

==> /var/log/mythtv/mythbackend.log <==
2009-11-16 04:26:59.710 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-16 04:26:59.712 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 04:26:59.715 Using protocol version 50
2009-11-16 04:26:59.782 Spawning LiveTV Recorder -- begin
2009-11-16 04:27:00.078 Spawning LiveTV Recorder -- end
2009-11-16 04:27:00.091 We have a playbackURL(/mythtv/livetv/1002_20091116042659.mpg) & cardtype(DUMMY)
2009-11-16 04:27:00.095 We have a RingBuffer
2009-11-16 04:27:00.146 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-11-16 04:27:00.148 playCtx, Error: Attempting to setup a player, but it already exists.
2009-11-16 04:27:00.148 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2009-11-16 04:27:00.148 TV Error: LiveTV not successfully started

==> /var/log/mythtv/mythfrontend.log <==
2009-11-16 04:26:52.846 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2009-11-16 04:26:52.846 TV: Changing from None to Watching WatchingLiveTV
2009-11-16 04:26:52.846 TV: State is LiveTV & mctx == ctx
2009-11-16 04:26:52.849 Realtime priority would require SUID as root.
2009-11-16 04:26:52.851 TV: UpdateOSDInput done
2009-11-16 04:26:52.851 TV: UpdateLCD done
2009-11-16 04:26:52.851 TV: ITVRestart done
2009-11-16 04:26:52.852 Video timing method: USleep with busy wait
2009-11-16 04:26:52.873 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-16 04:26:52.926 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/schedule-ui.xml
2009-11-16 04:26:54.820 RingBuf(/mythtv/livetv/1002_20091116042653.mpg): Waited 1.0 seconds for data to become available...
2009-11-16 04:26:54.820 Checking to see if there's a new livetv program to switch to..
2009-11-16 04:26:55.823 RingBuf(/mythtv/livetv/1002_20091116042653.mpg): Waited 2.0 seconds for data to become available...
2009-11-16 04:26:55.823 Checking to see if there's a new livetv program to switch to..
2009-11-16 04:26:57.830 RingBuf(/mythtv/livetv/1002_20091116042653.mpg): Waited 4.0 seconds for data to become available...
2009-11-16 04:26:57.831 Checking to see if there's a new livetv program to switch to..
2009-11-16 04:26:58.742 RingBuf(/mythtv/livetv/1002_20091116042653.mpg) Warning: Peek() requested 2048 bytes, but only returning 376
2009-11-16 04:26:58.742 NVP::OpenFile(): Error, couldn't read file: /mythtv/livetv/1002_20091116042653.mpg
2009-11-16 04:26:58.742 NVP(0), Error: JumpToProgram failed.
2009-11-16 04:26:58.748 NVP(0), Error: Unknown recorder error, exiting decoder
2009-11-16 04:26:58.973 TV: Attempting to change from Watching WatchingLiveTV to None
2009-11-16 04:26:59.642 TV: Changing from Watching WatchingLiveTV to None
2009-11-16 04:26:59.663 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-16 04:26:59.671 TV: Attempting to change from None to None
2009-11-16 04:26:59.710 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-16 04:26:59.712 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 04:26:59.715 Using protocol version 50
2009-11-16 04:26:59.782 Spawning LiveTV Recorder -- begin
2009-11-16 04:27:00.078 Spawning LiveTV Recorder -- end
2009-11-16 04:27:00.091 We have a playbackURL(/mythtv/livetv/1002_20091116042659.mpg) & cardtype(DUMMY)
2009-11-16 04:27:00.095 We have a RingBuffer
2009-11-16 04:27:00.146 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-11-16 04:27:00.148 playCtx, Error: Attempting to setup a player, but it already exists.
2009-11-16 04:27:00.148 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2009-11-16 04:27:00.148 TV Error: LiveTV not successfully started
```Any solutions would definitely be welcome.

---

### Post by Neon Dusk on 2009-11-16
I was getting this error on my frontend (the combined backend/frontend didn't have the problem). Setting the option on the frontend to always stream from the backend fixed the problem for me.

---

### Post by sturle on 2009-11-16
> **Neon Dusk said:**
> I was getting this error on my frontend (the combined backend/frontend didn't have the problem). Setting the option on the frontend to always stream from the backend fixed the problem for me.
I tried your workaround, but get the same error.  I think the cause may be different.  My log says:
```

2009-11-16 19:54:19.242 Tuning to 'MPEG Program 1' pnum: 0x1 without CRC check on PMT
2009-11-16 19:54:19.246 mpegts_read_header: could not find any PMT's
2009-11-16 19:54:19.246 AFD Error: avformat err(-1) on av_open_input_file call.
2009-11-16 19:54:19.246 Couldn't open decoder for: myth://w.x.y.z:6543/1311_20091116195411.mpg
2009-11-16 19:54:19.247 NVP(0), Error: JumpToProgram failed.
2009-11-16 19:54:19.509 TV: Attempting to change from Watching WatchingLiveTV to None
2009-11-16 19:54:19.746 NVP(0), Error: Unknown recorder error, exiting decoder

```The frontend runs karmic, the backend jaunty.  I can run mythfrontend and watch TV on the backend with no problems at all.

Norwegian DVB-T uses a rather new format, H.264/AVC.  Only VLC and the MythTV frontend will play it correctly due to special features used in the interlaced H.264/AAC stream and the LATM HE-AAC sound format.  Perhaps some important component has been removed or changed in karmic?  I have installed all codecs from medibuntu.

---

### Post by 0nelove on 2009-11-16
I've experienced this problem as well under a fresh install of 9.10.  Tried total reinstall & had same result reported above.  My machine is a frontend/backend combined.  I'm a log newbie, but using mythbuntu for the last year, so I can get whatever log is asked for.  (full path please!)

I will subscribe to this thread.  Thanks for any input.  This has me stuck.

---

### Post by sturle on 2009-11-17
> The frontend runs karmic, the backend jaunty.  I can run mythfrontend and watch TV on the backend with no problems at all.
I found a solution: apt-get install mythbuntu-repos, and answer yes to nightly builds and new packages.  I chose 0.22 and hope for some stability.  My frontend works now.

---

### Post by dlouwers on 2009-11-21
Hi,

I am having the same issue on Karmic 9.10 combined front and backend. I tried to do an:

```
sudo apt-get install mythbuntu-repos
```

as has been advised by previous poster but this particular package doesn seem to exist. Could you please advise me on how to resolve this issue?

Best,

Dirk Louwers

---

### Post by Neon Dusk on 2009-11-21
You can download and install the mythbuntu-repos package from [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by epi 1:10,000 on 2009-12-12
I have the same problem on 9.04 w/ Avenard .22 on a HVR1250 tunner.

---

### Post by B34N on 2009-12-12
I intermittently have the same problem.  I am running a Mythbuntu 9.10 backend/front end and I have multiple frontends running on Ubuntu 9.10.  I notice I get this problem more when it's trying to tune in a channel that does not have a signal.

What does the error actually mean?

---

### Post by cmadooly on 2009-12-26
same issue here. Although it will happen to me even if the channel has a signal. It tends to happen when I change channels too quickly.

---

### Post by sampe on 2009-12-29
Same problem for me, changing channels works fine though. 

I get the "Error opening jump program file" when I try to use the TV-Guide.

Any updates regarding this is more than welcome!

---

### Post by JRoque250 on 2009-12-29
Hi. I'm going to be very vague with this one and not very helpful but: I ran the backend setup and went through the capture cards screen, etc. After exiting the backend setup screens, I launched the frontend and lo and behold the problem is now gone. I hadn't ran setup since I last upgraded to the latest .22 build a couple of days ago.

I was getting an error in the log saying that it was trying to open a channel 1001 which I don't have in my lineup. Might have been coincidence but I can now start the frontend, change channels, etc and haven't seen the "jump program" error again. Fingers crossed.

JR

---

### Post by 0nelove on 2009-12-29
> **JRoque250 said:**
> Hi. I'm going to be very vague with this one and not very helpful but: I ran the backend setup and went through the capture cards screen, etc. After exiting the backend setup screens, I launched the frontend and lo and behold the problem is now gone. I hadn't ran setup since I last upgraded to the latest .22 build a couple of days ago.

I was getting an error in the log saying that it was trying to open a channel 1001 which I don't have in my lineup. Might have been coincidence but I can now start the frontend, change channels, etc and haven't seen the "jump program" error again. Fingers crossed.

JR

it's helpful to me: sounds like the newer builds of .22 might be clearing this up.  (are other things breaking to make up for the live TV function addition? - haha)  Thanks JR

---

### Post by VMZ on 2010-01-03
Try setting the live TV starting channel to a TV-channel (eg. no data channel) in backend setup -> input connections.

My empirical studies suggest, that if mythtv tunes to a software update channel, the mysterious jump program file fails to open.

I was on the verge of a nervous breakdown, because I got the error just after I finally got my multi--tuner and multi-LNB setup working :mad:

After tedious forking, I deleted all the OEM software channels, changed the starting channels to a station I knew to be working, and lo-and-behold, it worked!


That's why I think the best way to start building up DVB channel-lists, is to first scan 1 transponder with some FTA-channels, and when you have it, you can use that for a starting channel.


/VM


edit: Version at the moment is 0.22 (22594) running on Mythbuntu/Karmic.

edit2: Version is now 23046 and it seems that earlier comments are correct (about channels without signal causing problems). I noticed that when I scanned DVB-S channels with one LNB (which is improperly aligned and signal is very low), I got the "jump" again... After deleting those channels everything works ok. But one could say that newer versions _do not_ address the situation.

---

### Post by killabee44 on 2010-02-20
I am also having this problem. The channels without signals are definitely causing this. If anyone knows a fix, please fill us in. Thanks.

---

### Post by B34N on 2010-02-20
> **killabee44 said:**
> I am also having this problem. The channels without signals are definitely causing this. If anyone knows a fix, please fill us in. Thanks.

I continue to have this problem on multiple front-ends.  It is more prevalent on channels without a signal but it is certainly not exclusive to those channels.  I'm under the assumption that the problem is happening on the back-end but I cannot confirm that.  I plan on upgrading my back-end soon and I wonder if part of the problem is due to lack of power from my old P4 back-end.

---

### Post by VMZ on 2010-02-20
Just go to channel editor and delete those channels without signal. After that, set the starting channel for each input to existing/working channel.

---

### Post by killabee44 on 2010-02-21
> **VMZ said:**
> Just go to channel editor and delete those channels without signal. After that, set the starting channel for each input to existing/working channel.

Yeah, I need to do that. This is a fresh install that I am trying to get finished. I guess it is only happening on Mythbuntu 9.10 64? That is what I am running. 

I see it when I am changing channels and land on a channel with no signal.  

Going to Backend *setup>Input connections * and then putting in a channel with a signal as a starting channel fixes it as you guys suggested.  It's just a nagging issue.

---

### Post by VMZ on 2010-02-21
Well, not sure this being a 9.10/64-specific issue, at least I had this problem with mythbuntu 9.04/32 and it still exists when I scan new DVB-S transponders.

It really is a nagging issue :)

---

### Post by dwhecht on 2010-02-21
I also experience this issue.  When I get the error my frontend crashes and then when I reopen the front end, the starting channel when I open LiveTV will be the same one if failed on.  I have to go back to the backend and change the starting channel to a known good signal channel.  This type of a failure should not change the default starting channel and it should not cause MythFrontEnd to fail.

I'm running MythBuntu 9.10 64bit with a Hauppage 2250 tuner card.

---

### Post by colinnwn on 2010-03-05
This is happening to me also. I was going through all the digital channels to map them to an actual station (all but the 4 big network channels were mapped incorrectly.) When I got to channel 23, it never tuned in and I got this EOJPF buffer.

My primary tuner PVR-150 is still working fine. Originally my secondary HVR-1250 was set to start on 13_1. But if I switch to the HVR-1250 now, it tries to start on 23, the channel it failed on. After about 10 seconds I get the EOJPF buffer again. 

Went into the BE, and this error somehow switched the HVR-1250 starting channel in the BE from 13_1 to 23. I reset it to 13_1 and the HVR-1250 works, but only a little bit. 

It takes 20 or more seconds to lock a known good channel. Almost all of them the signal strength flips between 68%, 69%, 70% and 20%, and the dB will flip between 2.4 and 2.0. After a while it settles down and locks the channel. Any other channel on that multiplex will tune immediately, but if I switch off that multiplex, the tuner takes a long time to lock again.

This is a real buzz kill.

---

### Post by dibuntux on 2010-03-07
Ehi, I started this 2 threads before, but this just got more popular somehow... well never mind, just use this one. This is my original one:

 Error opening jump program file buffer
With Mythbuntu 9.10 AMD64, I'm always getting this
"Error opening jump program file buffer" when starting Live TV. It was not so with 9.04 (MythTV 0.21, I know...)...

My first tuner is a DVB-S Skystar2, connected to 2 LNB, I've been using for years with Myth. The error comes out only when the last watched channel is on Astra sat, like CNN or BBC. Myth says "partial lock", if I'm fast enough, I just switch to the next channel ON THE SAME MULTIPLEX, and it will lock normally. If I change multiplex, or satellite (other input), at random I've to repeat this procedure. If I do not, Myth exit LiveTV with the dreaded "Error opening jump program file buffer".
This does not happen with DVB-T on my Nova T-500.

I know many people are experiencing this problem, and all of them did not have it on 9.04. I'm using the update PPA, but until now nothing changed.

Any Ideas? Just wait for 10.04 and myth 0.23? TIA

Mythbuntu 9.10 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by VMZ on 2010-03-07
dibuntux, I'm quite sure your problem spawns from either mis-aligned LNB for Astra (just a little bit off) or you have a bad cable/connector somewhere. Especially if you have long cabling, it's easy to get very strange problems just by mixing several types of coax.

Check with stand-alone stb the channels you experience problems with. Error level is very useful for troubleshooting (which AFAIK is unavailable in mythtv).

BTW, I have the same situation with my terrestrial tuners, they never get me to this dreaded error, only sat does this (because of dead channels).

---

### Post by dibuntux on 2010-03-07
VMZ, thanks for the reply. The cable & connector & system are the same as in 9.04... that worked without problems of this sort. 
Also, after the initial problem, when you get to lock on the channel it is perfect. I've issues on some channels on DVB-T related to signal strength, but those are different. 
This is one is systematic and look like a sw problem.

---

### Post by ikke2808 on 2010-08-30
The solution is simple... Change the starting channel to one that has data coming in.

This solved it for me.

---

### Post by Tonyr63 on 2010-09-01
> **ikke2808 said:**
> The solution is simple... Change the starting channel to one that has data coming in.

This solved it for me.

What do you mean by this response?  Where do you change the starting channel and how does that make any difference?

If I set the starting channel in the backend to be channel 3 and I start the front end Live Tv it will start at channel 3.  If I switch to channel 5 and close and go back to the backend it has now got starting channel set to channel 5. So what does this have to do with the error widely reported?

I have 2 machines running just front end and they used to connect to the backend and run live TV however they suddenly started to produce this error for no reason I can understand.  The backend end computer will run front end Live Tv with no problem but the other client machines that used to work do not any longer.

So many have reported this error but no one has provided a solution or any meaningful troubleshooting steps to resolve.

What is causing this problem and how do we resolve.

Where bare the MythTv experts as it seems impossible to get any response to MythTv issues just so many other people vainly reporting the same problems.

How does this move forward if there is no support?

I cannot see how changing the starting channel can make any difference.

 Please elaborate on your solution.

---

### Post by alimac01 on 2010-09-03
Hi guys,
 
I too have this problem which will not go away no matter what I do. It seems that it works ok on non encryted channels because I can switch between BBC1, BBC2, etc and the picture will be fine all night but if I switch between a few encrypted channels then the problem appears and eventually I will get the "video frame buffering failed too many times" error as well.
 
I am just about to throw this thing out of the window so any feedback would be very gratefully.
 
Alimac01

---

### Post by Tonyr63 on 2010-09-06
Hi

I had a working system and following an installation of Shepard both of my other front end client machines that used to connect to the back end MYTHTV server without a problem now give this "Jump Error" every time.  I cannot get them to  connect to watch live at all and I cannot get any assistance on any forum.  Mythtv is dead in the water from any client machine however if I log on directly to the back end system it can run live TV with no problem.

How do I troubleshoot this problem?

If this was a Windows system a simple clean reinstall would fix but with MYTHTV these is non support forum that responds.  I now understand the significance of the MYTH.

---

### Post by Tonyr63 on 2010-09-15
Hi
 
The jist of the speculation about the source of the error [FONT=Calibri]"Error opening jump program file" is if you attempt to connect to your backend system from a client machine and it was last set to a channel with either a poor or no signal.[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]I can absolutely confirm that this is not the case.[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]If i go to my backend system and run the frontent live TV direct I can view all 23 FTA channels.  If I go to the channel with the strongest signal and exist live TV locking in that channel and go to either of the other networked clent machines runing the same version of MythTv and Ubuntu I get the [FONT=Calibri]"Error opening jump program file" every time.  This has nothing to do with connecting to a channel with a weak signal in my case and I previously have both client working perfectly with the same software release.[/FONT][/FONT]
[FONT=Calibri][FONT=Calibri][/FONT][/FONT] 
[FONT=Calibri][FONT=Calibri]I canot believe such a catastrophic error can have no resolution and the overall solution can be so bug ridden.  I have been troubleshooting for 3 weeks with no idea of how to resolve.[/FONT][/FONT]
[FONT=Calibri][FONT=Calibri][/FONT][/FONT] 
[FONT=Calibri][FONT=Calibri]I am running MythTv 0.23 so it was not fixed from version 0.22.[/FONT][/FONT]
[FONT=Calibri][FONT=Calibri][/FONT][/FONT] 
[FONT=Calibri][FONT=Calibri][/FONT][/FONT]

---

### Post by lank23 on 2010-11-30
Been running Mythbuntu 10.04 with mythtv 0.24, and I too get a this error but it only occurs when I try to tune to a channel using firewire output from my QIP 7100 from Verizon.  So times I get the channel, other times I get the error.  I never get this error using my PVR150 for any channel.

Looking harder at the mythfrontend.log running this command

```
tail -f /var/log/mythfrontend.log | grep Error
```

I always see this line

```
2010-11-30 21:03:56.218 playCtx, Error: Attempting to setup a player, but it already exists.
```

and from my /var/log/mythtv/mythbackend.log just a few seconds before the same time as the frontend log I get a bunch of this lines.
```
LFireDev(002180FFFE4BAB21), Warning: No Input in XXXX msec...
```

then it fails to get a signal and I get the onscreen error prompt "error opening jump program file".

So it is basically due that we can not get a lock on the signal, I figure my issue is due to the encryption on some of the channels not allowing me to get a lock via the firewire.

---

