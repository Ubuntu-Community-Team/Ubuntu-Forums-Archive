---
title: "Mythbuntu 9.10 x64 HDPVR help"
date: 2010-01-10
forum: Mythbuntu
---

### Post by DarkAmeba on 2010-01-10
Help! I will admit first that I am a noob, so please forgive the inevitable foolish mistakes. That said, I have been banging my head on the wall, and really need some help. I am so close to a running system, but I have hit a wall.

Machine is a frontend/master backend combo: 
Intel Core 2 Duo e8200
Zotac GF9300-G-E (nvidia geforce 9300)
4gb ram
HDPVR
MCE v2 ir blaster / remote
ATT Uverse TV: Motorola VIP1225 STB.

I have two issues:

**First**: upon restart, I have started getting the error "unable to connect to backend..." in mythfrontend after a reboot. If I exit the frontend, then re open it (without even doing anything to mythbackend) the problem seems to be resolved. However, I feel that something is wrong at the core which may be causing me other issues, so I would lke to resolve this.

Based on searches i have so far: edited the mysql database config and commented out the bind localhost line and checked all of my settings: backend is set to 127.0.0.1, passwords and logins are all right and test out fine.

Mythfrontend log right after a restart:

```
Starting mythfrontend.real..
2010-01-10 13:50:34.189 mythfrontend version: branches/release-0-22-fixes [23084] www.mythtv.org
2010-01-10 13:50:34.190 Using runtime prefix = /usr
2010-01-10 13:50:34.190 Using configuration directory = /home/mediacenter/.mythtv
2010-01-10 13:50:35.045 Empty LocalHostName.
2010-01-10 13:50:35.045 Using localhost value of TuckerMediaCenter2
2010-01-10 13:50:35.048 New DB connection, total: 1
2010-01-10 13:50:35.050 Connected to database 'mythconverg' at host: 127.0.0.1
2010-01-10 13:50:35.051 Closing DB connection named 'DBManager0'
2010-01-10 13:50:35.056 ScreenSaverX11Private: Gnome screen saver support enabled
2010-01-10 13:50:35.056 DPMS is active.
2010-01-10 13:50:35.057 Primary screen: 0.
2010-01-10 13:50:35.057 Connected to database 'mythconverg' at host: 127.0.0.1
2010-01-10 13:50:35.058 Using screen 0, 1920x1080 at 0,0
2010-01-10 13:50:35.064 MythUI Image Cache size set to 20971520 bytes
2010-01-10 13:50:35.064 Enabled verbose msgs:  important general
2010-01-10 13:50:35.067 Primary screen: 0.
2010-01-10 13:50:35.067 Using screen 0, 1920x1080 at 0,0
2010-01-10 13:50:35.067 Using theme base resolution of 1280x720
2010-01-10 13:50:35.115 LIRC: Successfully initialized '/dev/lircd' using '/home/mediacenter/.mythtv/lircrc' config
2010-01-10 13:50:35.115 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mediacenter/.mythtv/joystickmenurc
2010-01-10 13:50:35.382 Using the OpenGL painter
2010-01-10 13:50:35.613 Theme error: Unknown widget type
Type: 'align'
Name: ''
Line: 707
2010-01-10 13:50:35.617 Theme error: Unknown widget type
Type: 'align'
Name: ''
Line: 756
2010-01-10 13:50:35.628 Theme error: Unknown widget type
Type: 'align'
Name: ''
Line: 940
```

Backend: (it appears mithfilldatabase ran just right after reboot as well)

```
2010-01-10 13:54:35.810 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-10 13:54:35.848 Using protocol version 50
2010-01-10 13:54:35.890 MainServer::ANN Monitor
2010-01-10 13:54:35.948 adding: TuckerMediaCenter2 as a client (events: 0)
2010-01-10 13:54:35.990 MainServer::ANN Monitor
2010-01-10 13:54:36.048 adding: TuckerMediaCenter2 as a client (events: 1)
2010-01-10 13:54:36.090 Reschedule requested for id -1.
2010-01-10 13:54:36.090 Received a remote 'Clear Cache' request
Segmentation fault
2010-01-10 13:54:36.255 Scheduled 0 items in 0.2 = 0.06 match + 0.10 place
2010-01-10 14:07:05.252 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-01-10 14:17:01.743 MainServer::ANN Monitor
2010-01-10 14:17:01.798 adding: TuckerMediaCenter2 as a client (events: 0)
2010-01-10 14:22:05.322 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-01-10 14:37:05.429 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

**Second**: This one is really killing me. Live TV works for the first channel when it is opened: however, as soon as I change the channel,  get kicked out of live tv with the error: "irrecoverable recorder error." After this occurs, the connection to mythbackend appears to have dropped...  I have played around with the sleeps in my channel change script, but otherwise I'm not really even sure what to try. 

Frontend:
```

010-01-10 14:49:21.948 Connected to database 'mythconverg' at host: 127.0.0.1
2010-01-10 14:49:21.949 TV: UpdateOSDInput done
2010-01-10 14:49:21.949 TV: UpdateLCD done
2010-01-10 14:49:21.949 TV: ITVRestart done
2010-01-10 14:49:21.951 The realtime priority setting is not enabled.
2010-01-10 14:49:21.973 OpenGLVideoSync()
2010-01-10 14:49:22.262 Video timing method: SGI OpenGL
2010-01-10 14:49:22.283 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-10 14:50:38.084 Loading window theme from /usr/share/mythtv/themes/Graphite/schedule-ui.xml
2010-01-10 14:51:28.777 MythSocket(7f7a4dc71010:41): readStringList: Error, timed out after 7000 ms.
2010-01-10 14:51:28.777 RemoteEncoder::SendReceiveStringList(): No response.
2010-01-10 14:51:28.777 NVP(0), Error: Unknown recorder error, exiting decoder
2010-01-10 14:51:28.782 ~OpenGLVideoSync() -- closing opengl vsync
2010-01-10 14:51:28.837 LiveTVChain(live-TuckerMediaCenter2-2010-01-10T14:49:12): SwitchTo() not switching to current
2010-01-10 14:51:28.878 TV: Attempting to change from Watching WatchingLiveTV to None
2010-01-10 14:51:28.912 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-10 14:51:28.913 Using protocol version 50
2010-01-10 14:51:36.021 MythSocket(7f7a4dc70ef0:41): readStringList: Error, timed out after 7000 ms.
2010-01-10 14:51:36.021 RemoteEncoder::SendReceiveStringList(): No response.
2010-01-10 14:51:36.021 TV: Changing from Watching WatchingLiveTV to None
2010-01-10 14:51:36.022 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-10 14:51:43.026 MythSocket(7f7a29a06290:41): readStringList: Error, timed out after 7000 ms.
2010-01-10 14:51:43.026 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.
2010-01-10 14:51:43.026 RemoteEncoder::Setup(): Failed to connect to backend
2010-01-10 14:51:43.026 RemoteEncoder::SendReceiveStringList(): Failed to reconnect with backend.
2010-01-10 14:51:50.026 MythSocket(7f7a4c048540:31): readStringList: Error, timed out after 7000 ms.
2010-01-10 14:51:50.027 Connection to backend server lost
2010-01-10 14:51:50.029 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-10 14:51:57.032 MythSocket(7f7a4ffb8100:31): readStringList: Error, timed out after 7000 ms.
2010-01-10 14:51:57.032 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.
2010-01-10 14:51:57.032 Reconnection to backend server failed
2010-01-10 14:51:57.036 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-10 14:52:04.037 MythSocket(7f7a29daaf00:31): readStringList: Error, timed out after 7000 ms.
2010-01-10 14:52:04.037 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.
2010-01-10 14:52:04.050 ScreenSaverX11Private: DPMS Reactivated 1
2010-01-10 14:52:04.103 TV: Attempting to change from None to None
2010-01-10 14:52:04.103 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-10 14:52:05.540 MythSocket(5982100:31): readStringList: Connection died (select).
2010-01-10 14:52:05.540 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.
2010-01-10 14:52:05.540 RemoteEncoder::Setup(): Failed to connect to backend
2010-01-10 14:52:05.540 RemoteEncoder::SendReceiveStringList(): Failed to reconnect with backend.
2010-01-10 14:52:05.551 Event socket closed. No connection to the backend.
2010-01-10 14:52:05.558 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-10 14:52:05.561 Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

2010-01-10 14:52:17.776 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-10 14:52:17.777 Using protocol version 50
2010-01-10 14:52:23.172 Deleting UPnP client...
Error in my_thread_global_end(): 3 threads didn't exit
```

Backend log shows no errors.

For kicks my channel change script:

```
#!/bin/sh
REMOTE_NAME=Motorola_VIP_1200
irsend SET_TRANSMITTERS 1 #this is the plug on the left when looking at the back of IR reciever, 2 is the other
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME OK 
sleep 0.6
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 0.6 # note, you may have to tweak the interdigit delay up a bit
done
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME OK 
sleep 2.0
exit 0

```

THANK YOU in advance for any input. I am so close I can feel it....

---

### Post by DarkAmeba on 2010-01-11
bump

---

### Post by DarkAmeba on 2010-01-13
Bump :(

---

### Post by oliver.greg@gmail.com on 2010-01-15
This is all on a single computer right?

If so, paste the output of your /etc/hosts file, and the screens for your mythtv-setup and mythfrontend setup as it pertains to the database.  It seems you have something regarding the networking borked.

Make sure the firewall and/or apparmor is off..  I have the same versions of everything currently (mythbuntu amd64 and HDPVR), and I do not see any of those issues.

-Greg

---

### Post by bmikeb on 2010-02-16
I've got the same issue.
mythbuntu 9.10
My setup is an intel adom 330 (x86_64) + Nvidia ION, with 4G ram 750T disk.
The cpu is running hyperthreading. So it looks like 4 CPUs.
everything is running on the same box.

- MythTV will almost never lock on a channel change.
- It will often not lock when i bring it up fresh after a backend restart.
- Once the "irrecoverable recorder error." happens i have to recycle the backend and the frontend to be able to try again.

Because this occasionally works, i was thinking this could be a threading issue.

Any help would be appreciated.

(because someone asked, here is my /etc/hosts).

$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    pvr

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Slacker3k on 2010-02-17
I don't have any great answers, but maybe I can get you looking in the right direction.

I get your first error all the time.  I believe the issue is that that the backend has not fully initialized before the frontend tries to connect.  If you just wait a minute (you don't even have to exit the frontend) then everything should work fine - it will reconnect.

I have two HD-PVRs on a single machine (along with 4 other tuners) and I also receive the read error on occasion when changing channels (but not nearly every time).  My guess is that when changing channels the system just doesn't respond fast enough (maybe even it's a bit-rate change.)  I can always go right back in and then change to the channel.  Since your issue seems to be a bit more severe, I wonder if you have a different (older) firmware on your device.  Perhaps try installing and updating everything on a Windows machine and testing again.

---

### Post by trevmar on 2010-04-09
I have the "irrecoverable recorder error" problem with i386 (32bit). I use 0.22.0+fixes23893. It happens about 50% of channel changes during LiveTV -- it all depends on the content of the channels you are tuning.

I have a Motorola DCX3200 cable box and an HD-PVR (rev E2 sticker). Using analog component and SPDIF audio to the HD-PVR. Channel change is with seperate mceusb IR blaster ($20 from Hong Kong) as the internal HD-PVR blaster tends to lock up the USB. Have all recording profiles set for 13,500bps and 20,200bps as the HD-PVR auto-adjusts its data rate to suit the quality of the source. It throttles itself back to about 3MBps on SD video, even with these fast VBR settings. AC3 audio is awesome. However there is a KILLER PROBLEM. When changing channels your script needs a >3.8 second delay in it, or else the SPDIF audio from the HD-PVR with lock-up and disappear. Added to the delay in the cable box this means that the frontend nearly always times out to an "irrecoverable recorder error" when changing channels while watching live TV. The backend changes, it will record OK (it takes about 10 seconds to sync up) but the frontend times out. I have recompiled the source after setting kShortTimeout in mythsocket.cpp to 13000 from 7000, but this has not fixed the problem. IMO this is a serious problem which will hurt anybody who seriously uses an HD-PVR installation in MythTV. 

    Luckily, I also have a dual-channel HDhomerun, so I am not totally dead in the water, but the wife does tease me every time I try to change the channel in LiveTV :( 
    I would appreciate ideas on what variable I should be extending.. or any patches which need to be applied...

---

### Post by stefanst on 2010-04-28
Same here - wish I had any ideas.

So here's your sympathetic bump.

---

### Post by trevmar on 2010-04-28
Stefan,
You can find the explanation for why the MythTV developers don't care about people like you or me at the Wiki discussion page:

[http://www.mythtv.org/wiki/Talk:Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Talk:Hauppauge_HD-PVR)

I did in fact mount a source tree, and merely asked where to add the appropriate "sleep," yet this is the tirade that somebody, presumably a developer, threw back at us:

[INDENT]Nobody said it was only Motorola boxes. I said it was certain boxes in certain configurations, with certain firmwares. **There *is* a philosophical objection to adding such a timeout. **It's not appropriate to add yet another useless setting when that's not where the issue lies, and should be handled by fixing the driver, the firmware of the box, and in myth, by monitoring channel change scripts as well as with the HD-PVR signal monitor patch. Anyone complaining here should ideally not be doing so until after having applied all the patches mentioned in the wiki page (#6719, #6611). If you care about solving your problems, please make time to recompile from source. Solicitation on performance with the HD-PVR in LiveTV was requested on the lists, with little response. If people truly care to see the issues solved, the least they could do would be test patches to solve it. 
[/INDENT]

---

### Post by randumnumber on 2010-04-28
Bump :/

---

### Post by iamlindoro on 2010-04-28
> **trevmar said:**
> Stefan,
You can find the explanation for why the MythTV developers don't care about people like you or me at the Wiki discussion page:

[http://www.mythtv.org/wiki/Talk:Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Talk:Hauppauge_HD-PVR)

I did in fact mount a source tree, and merely asked where to add the appropriate "sleep," yet this is the tirade that somebody, presumably a developer, threw back at us:

So does that mean you've tested the two patches that were referred to in the "tirade?"  The sleep you want to add is not a usable, committable fix.  The patches are.  It seems to me that the developer in question cares a great deal, otherwise he wouldn't bother to respond to you there, and here.  I should know, I'm him.  If you don't care to test fixes that are actually usable, then from my perspective it's you who cares little about the fix, not I.  

I'll reiterate.  Adding hacks to extend timeouts is not a usable fix.  Modifying the signal and channel change monitors to take one another into account so that the timeout is not an issue is.  Taking my quote (which is the fifth or six in a string) out of context to make an ad hominem attack against me (when the explanation itself is sound) is counterproductive.  If you'd like the issue worked around, do us the courtesy of helping us do it the right way.  Further, how motivated do you imagine we will be when we see stuff like this?  We are hobbyists too, you know.  This is our hobby, and this kind of business does not make it particularly fun, nor does it instill one with any great desire to get right on your problem.

---

### Post by trevmar on 2010-04-28
Well, the question I posted about "sleep" hacks followed your earlier suggestion that I wean my wife off watching LiveTV, which is further still up the wiki thread. That really is not a viable option for me. In retrospect, it was probably offered in jest, and I over-reacted.

Your admonition to apply those specific patches is constructive and useful. I should have seen it earlier, but I have been busy this past few weeks, and only saw your response on the wiki discussion when stefan bumped this thread. 

I have to attend several conferences in Europe until mid-May, so when I get back I will read up how to apply the patches, and let you know the results. Should I do that on this thread, or in the Wiki discussion?

As I said in my posts, it is many, many years since I last coded with C, and the new tool chains are unknown to me. Which, I guess, is why I think in terms of fixing code with 'hacks' rather than 'patches':(

In anticipation that these patches will address the question, I apologize in advance for reacting in anger when I read your response on the wiki.
.

---

### Post by iamlindoro on 2010-04-28
Replying to the mythtv-dev mailing list is the best way to communicate experiences with patches.  There's actually a thread there from this month soliciting responses on those patches.  It's also the best way to get in touch with me/us since I only happened across this post.

Yes, the no-live-tv thing was a joke (though it's still the use case that we most recommend).  Thank you for taking a step back and being understanding in your reply.  I do appreciate it, many people are less kind.

---

### Post by trevmar on 2010-04-28
> **iamlindoro said:**
> Replying to the mythtv-dev mailing list is the best way to communicate experiences with patches

I guess I am also going to need to read up on how to post to that list :(

---

### Post by phroman on 2011-02-27
Well, I realize this is a pretty old post, but I don't know how to apply the patches referred to in this post.  noob.  My Hauppauge HD PVR isn't working anymore and I'M dead in the water.  I was reading about these patches but don't really see how to use them.  Any guidence?  Thanks..!

---

### Post by trevmar on 2011-02-27
My HD PVR is still working same as before. Using Myth v2.2/2.3

Was updating weeklies until a month ago, haven't upgraded since then.

---

