---
title: "Need help with RNG-150 with firewire: great video, no channel changing"
date: 2011-02-22
forum: Mythbuntu
---

### Post by bw_bw on 2011-02-22
SUMMARY: I can't get Firewire channel changing to work on my Cisco RNG-150.  The video works fine.

LONG VERSION:
I've been using MythTV for almost 4 years and I've always solved my issues with Google.  This one, however, has me stumped.

I am trying to get firewire channel changing going on my Cisco-branded RNG-150 STB from Comcast.  I've been through the MythTV Firewire Guide and every other source I can dig up.

System: Mthbuntu 10.10, fully updated.  PCI Firewire card w/ Via 3606 chipset.

The tuner is set up in MythTV according to info from the Firewire Cable Box Compatibility list, and is working for video.  I can watch live TV, i just can't  use Myth to change the channel.  So far I've tried the built-in changer, 6200ch, and MythChanger (w/ -f 6, as talked about here: [http://www.gossamer-threads.com/lists/mythtv/users/442427](http://www.gossamer-threads.com/lists/mythtv/users/442427)).  When I attempt to change the channel, the OSD looks fine: I get a LAM lock and the OSD reports the new channel info, but the channel doesn't actually change.  

plugreport says:

```
$ plugreport
Host Adapter 0
==============

Node 0 GUID 0xa98d040808048da9
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x445829c75e880000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
    channel=1, data_rate=2, overhead_id=0, payload=0
iMPR n_plugs=1, data_rate=2
iPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
    channel=0
```firewire_tester has good things to say (I can run it 100 times and it's all good):

```
$ firewire_tester -n 1 -p -r 2
Action: Test P2P connection 2 times, node 1, channel 1
P2P: Testing...Success, 72 packets received
P2P: Testing...Success, 65 packets received

```I've changed the permissions on /dev/fw0 and /dev/fw1.  There is no /dev/raw1394.  Is this a problem, or is it no longer relevant?

Mythchanger:

```
$mythchanger -f 6 -c 34 -v

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
STB Vendor ID: 0x445829 Model ID: 0x0668, (Using user selected channel changer #6)

1 STB(s) found:
-------------
STB 1: port=1, node=1, changer=6, GUID=0x445829c75e880000
```A little from the backend log.  I scheduled a recording to see if it would change the channel (it didn't).
```
2011-02-22 11:01:11.864 TVRec(1): Changing from None to RecordingOnly
2011-02-22 11:01:11.907 TVRec(1): HW Tuner: 1->1
2011-02-22 11:01:11.999 SetLastChannel(35): cleared: no
2011-02-22 11:01:12.050 LFireDev(445829C75E880000): Buffered packets 2000 (8000 KB)
2011-02-22 11:01:12.055 AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 14 min
2011-02-22 11:01:12.146 Started recording: Pawn Stars "Bumpy Ride": channel 1035 on cardid 1, sourceid 1
2011-02-22 11:01:12.285 MainServer::ANN Monitor
2011-02-22 11:01:12.325 adding: MythBoxHD as a client (events: 2)
**2011-02-22 11:01:17.054 FireSM(445829C75E880000), Warning: Wait for valid PAT timed out**   ***<----- is this something?***
2011-02-22 11:01:17.250 TVRec(1): rec->GetFileName(): '/mythtv/recordings/1035_20110222110100.mpg'
2011-02-22 11:01:17.379 LFireDev(445829C75E880000): Buffered packets 2000 (8000 KB)
2011-02-22 11:11:34.690 ProgramInfo(): Updated pathname '':'' -> '1035_20110222110100.mpg'
2011-02-22 11:11:35.242 MainServer::ANN Playback
```
I'm happy to post more info, but I'm not sure what else is relevant.  It feels like I can get data from the STB, I just can't send commands to it.  I certainly appreciate any help - I've been on this for a few days now, and it's delaying the deployment of an otherwise awesome new MythTV system.


Best,
bw

---

### Post by novellahub on 2011-02-23
Check out this thread:

[http://www.thelinuxlink.net/forum/viewtopic.php?f=18&p=25028](http://www.thelinuxlink.net/forum/viewtopic.php?f=18&p=25028)

---

### Post by bw_bw on 2011-02-24
Unfortunately I am all too familiar with that thread.  The link I posted has a link to that thread, and only seems to add to my confusion: others seem to be using "usr/bin/mythchanger -f 6 -c" with success.  I can't figure out why that's not working for me.

---

### Post by novellahub on 2011-02-25
Could it be a issue of rights to the Firewire interface then?

---

### Post by apathania on 2011-02-28
I have been in the same boat since Oct 2010. I was able to change the channel via firewire using mythchanger until Comcast updated their guide/firmware back then. Afraid, we are SOL. Even went and replaced the cable box. No dice. If you do get it to work, I will be very interested to know your solution.

---

### Post by Nausser on 2011-04-21
I too have the Cisco RNG-150. I have been using this box for well over a year with MythTV. I have an HDPVR connected and use the firewire connection to change the channels. A couple days ago the box was upgraded from the Comcast branding to Xfinity. Now my box stopped working for changing channels. I do not get any errors when myth "changes" the channel. 
I have been using the channel changing scripts according to this thread.
[https://home.timconrad.org/display/taci/Channel+Changing+via+Firewire]("https://home.timconrad.org/display/taci/Channel+Changing+via+Firewire")

When I first followed the above link, it worked right away like a charm. Every step of the way.

Now when I try the part in the beginning:
```
cat /var/log/dmesg | grep 1394
```
I get nothing. The only firewire related entry in my dmesg is the word "firewire" itself. When I run command:
```
cat /var/log/dmesg | grep firewire
```
I get
```
[    1.490136] firewire_ohci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.490142] firewire_ohci 0000:03:00.0: setting latency timer to 64
[    1.585011] firewire_ohci: Added fw-ohci device 0000:03:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x1
[    2.076096] firewire_core: created device fw0: GUID 001e8c0000c2d082, S400
[    2.125571] firewire_core: created device fw1: GUID 0023be9bcf6e0000, S400
[    2.125575] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
```
Also, the part in the instruction where you enter:
```
./mythchanger -f4 -c 33 -v
```
It returns:
```
mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
STB Vendor ID: 0x23be Model ID: 0x0668, (Using user selected channel changer #4)

Skipping empty node 1
1 STB(s) found:
-------------
STB 1: port=0, node=0, changer=4, GUID=0x0023be9bcf6e0000
```

I'm stumped on this one. If this does have to do with the Xfinity upgrade. I assume the demand for a solution to this issue will be solved rather quickly.

If anyone out there needs more information, please do not hesitate to ask.

---

### Post by LowSky on 2011-04-22
Can i ask why you are using f 4?

```
mythchanger -f4 -c 33 -v
```

4 is a Scientific altantic 4250 cable box. have you tried changing its value.

here is exactly what the mythchanger readme says


> 
Developed by: majoridiot ...


... USING mythchanger

=================



The command syntax for mythchanger is:



 $ mythchanger -c <channel> [OPTION]...



Mandatory arguments: channel number



 Options:

    
    -c <channel number> channel to tune
    -f <changer> force channel changer:

        1 = SA3250HD

        2 = SA4200HD (and some 3250s)

        3 = SA4250HDC

        4 = SA4250HDC alternate (and 4240HDCs with 4250 firmware)

        5 = SA8300

        6 = Motorola Fast (DCH and DCT series)

        7 = Motorola alternate
     -g <GUID> GUID of target STB
     -h display this help and exit
     -P power on STB (default: no)
     -R reset firewire bus before doing anything else (default: no)
     -v verbose output
     -V Display version information and exit

OPTION OVERVIEW

===============



-c <channel number>         The channel you want to tune



-f <changer>                If your STB is detected incorrectly or if the channel changer
                            mythchanger selects does not work, you can force the use of another
                            changer with this option.

-g <GUID>                   Changes channel of the STB with the supplied GUID.  This is very
                            useful for backends with multiple firewire tuners.  Otherwise, the 
                            default action is to change the channel on the first STB found on
                            the firewire bus.


-h                          Displays help info and exits


-P                          Power on the STB before channel change- default: no.  Use this option
                            if you or MythTV routinely powers down your STB.  Also useful to recover
                            after firmware update on SA STBs, which power off after update.



-R                          Performs a bus reset BEFORE doing anything else.  Use only if *absolutely*
                            necessary for unstable STBs.
                            
-v                          Verbose output- will display *everything* mythchanger is doing, to help
                            with troubleshooting and debugging.
                            
-V                          Displays version number and exits
              


--end 1.0--

---

### Post by novellahub on 2011-04-24
I just set up a RNG-150 yesterday from Comcast using the following change command:

```

mythchanger -f6 -c 33 -v

```

I am not using a HDPVR and pulling the programming directly into the firewire card.  I can post more detail of the steps I did if needed.  So far no issues with the channel changes.

---

### Post by sisson_d on 2011-05-07
I have a RNG-150 in an area with the Xfinity "Upgrade" (which as far as I can tell just means I have advertising on the bottom of my program guide now). I have tried using all of the different -f options with no success. -f7 is the only one that returned a channel change error message using the -v verbose option. All the others returned no errors, but did not change the channel. Everything else is running great (except some issues with Mythmote).

It sounds like an IR blaster may be the only way to go with the new firmware. I'm just relieved that I just started with this MythTV stuff last week and have never had the firewire channel change capability. That's something I'd hate to lose.

-Doug

---

### Post by novellahub on 2011-05-10
I was hit today by the Xfinity update to the cable box.  No channel changes were made anymore. Channel changes via Firewire don't work any longer using mythchanger.  I had to resort to using a IR Blaster with the MCE remote receiver.  

[http://ubuntuforums.org/showthread.php?t=1581183](http://ubuntuforums.org/showthread.php?t=1581183)

Same remote rules apply to the setup in the link I did for my DTA boxes.  They use the same remote codes.

---

### Post by sisson_d on 2011-05-12
Just a newbie question? What will I need to do to continue using th e firewire stb output while using an external IR blaster. So far, everything I've learned about has to do with firewire channel changing.
I imagine I'll be using some other command that I can enter into the "external channel change command:" entry in the "input connections" section of the backend. What command should I be looking into so I can start learning what I need to know?

Thanks,
Doug

---

### Post by novellahub on 2011-05-12
> **sisson_d said:**
> Just a newbie question? What will I need to do to continue using th e firewire stb output while using an external IR blaster. So far, everything I've learned about has to do with firewire channel changing.
I imagine I'll be using some other command that I can enter into the "external channel change command:" entry in the "input connections" section of the backend. What command should I be looking into so I can start learning what I need to know?

Thanks,
Doug

You will continue using the Firewire stb output to grab the video feed.  The way you change the channel will be different.  I am using the chan_ch_1 script posted in the link I provided in my last post.

---

### Post by sisson_d on 2011-05-12
> You will continue using the Firewire stb output to grab the video feed. The way you change the channel will be different. I am using the chan_ch_1 script posted in the link I provided in my last post.

Thank you for the heads up. I actually just bought a Windows MCE remote IR kit last week and expect it soon. So, your code should help me get up and running in no time. Even though I'm very new to it, I'm starting to really like the open source aspects of Ubuntu. I just wish I had more linux experience so I wouldn't have to do web searches for even the most basic commands.

-Doug

---

### Post by chrismurf2900 on 2011-06-01
Any findings with getting the RNG-150 firewire channel changing to work?

I'm having the exact same issues, and would rather be able to utilize the firewire channel changing ability.  I'm heading down the route of utilizing an external channel changer (IR Transmitter), but wanted to see if you guys have come up with anything.

Also, I'm taking a look at doing some editing with the stb-command application, as well as possibly the firewire.cpp file in MythTV to enable the ability to change channels on the RNG-150 (see my started discussion here: [http://ubuntuforums.org/...1771438]("http://ubuntuforums.org/showthread.php?t=1771438")).  But if anyone can further point me in the right direction to perform the necessary edits, I'll be able to get it done quicker/easier.

Thanks!

---

### Post by harrisg on 2011-06-07
I'm in the same situation. I switched to Comcast a few months ago from DirecTV with MythTV in mind. Now after a couple of months of perfect firewire channel changing with my RNG150, Comcast pushes out an update (presumably the Xfinity update) which breaks channel changing on both of my boxes. No combination of mythchanger works for me anymore. After the update, I have the TV Guide branded program guide and a huge ad at the bottom of the screen.

I would be happy to volunteer my services to test or work on this issue. I am a Mac/iPhone developer, but I don't have any experience with Firewire or anything that low level. I live north of Atlanta, GA.

---

### Post by chrismurf2900 on 2011-06-09
Ya, I've seen a lot of reports from other users having the same issue.

Currently, I'm looking into modding the "stb-command" application to send the proper on/off signals via firewire.
Then I'll be (or concurrently) working on adding the ability to change channels, either via the "stb-command" application or "mythchanger," whichever is easier (I'm thinking mythchanger, but haven't looked too in depth yet).

I'll post an update here when I get something going.  It would be great to have some other testers!

---

### Post by novellahub on 2011-06-10
> **chrismurf2900 said:**
> Ya, I've seen a lot of reports from other users having the same issue.

Currently, I'm looking into modding the "stb-command" application to send the proper on/off signals via firewire.
Then I'll be (or concurrently) working on adding the ability to change channels, either via the "stb-command" application or "mythchanger," whichever is easier (I'm thinking mythchanger, but haven't looked too in depth yet).

I'll post an update here when I get something going.  It would be great to have some other testers!

I would be willing to test. I was previously using the mythchanger script until it stopped working.

---

### Post by chrismurf2900 on 2011-06-12
Not that this is actually that helpful, but I thought I would at least let those interested know.

The "channel up" and "channel down" commands now work in stb-command for an RNG-150 box with Xfinity firmware upgrade.

I'm currently looking into channel changing, but since there is no documentation on the inputs for Comcast's RNG-150 firewire port, I'm basically going through lots of trial and error.

If anyone gets any further findings, please let me know.  Thanks!

---

### Post by wjdukes on 2011-06-20
I am dealing with the same problem and would be happy to help test. I've noticed the same thing about channel up and channel down working through stb-command. 

This is going to be a newbie question, so I apologize, but, in the mean time can anyone point me to a reasonably straightforward guide to setting up an ir blaster for channel changing using reasonably inexpensive usb-based hardware? I don't have a serial port, so I purchased a usb-ir blaster from irblaster.info, but I'm pretty lost in figuring out how to set it up. I'm perfectly willing to put in the time to RTM, if someone will do me the favor of pointing me in the direction of said manual. 

Thanks for any advice on ir blasters, and please let me know if I can help test a firewire option.

---

### Post by Nausser on 2011-07-13
Its been a while since I've checked on this post. I'm very sorry to hear so many people suffering from this Xfinity firmware upgrade.

I'm still manually tuning my STB because after installing and compiling for my HDPVR to work, lirc has been a thing of the past. Even the "irw" program doesn't work. 

As I posted the firewire channel change issue first, you know I've been putting up with this for a while.

I will continue to monitor this thread and hope for a breakthrough!
If anyone can think of something I can try, please don't hesitate to let me know!

---

### Post by Nausser on 2011-07-25
Could anyone give me some direction to figuring/testing this one out on my own? If a new "code" has to be written to communicate via firewire with the Xfinity RNG-150, we should make sure on/off status can also be read. (ex. if the box is off, turn on, then change channel)

In another direction, can someone tell me of a box from Comcast that has the Xfinity upgrade and still works with firewire channel change? The easiest thing to do would be to swap out the box for another brand that already works.

---

### Post by Nausser on 2011-08-06
I became tired of the issue with this box so I brought my RNG-150 to the Comcast store and told them I needed a different brand and they gave me a Scientific Atlanta SA3250HD (I know Scientific Atlanta has a hand in the Cisco box as well).
I plugged up the box and I still have no channel changing capabilities. Mythchanger is seeing my box
```
mythchanger -v -c 427

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
STB Vendor ID: 0x1ac3 Model ID: 0x0be0, Scientific Atlanta Model SA3250HD


Skipping empty node 1
1 STB(s) found:
-------------
STB 1: port=0, node=0, changer=1, GUID=0x001ac3902d820000
```
Since the new box I have is the model that it is, the README included with mythchanger said my box may need to be forced to number 2. So I tried that as well
```
mythchanger -f 2 -v -c 427

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
STB Vendor ID: 0x1ac3 Model ID: 0x0be0, Scientific Atlanta Model SA3250HD

(Using user selected channel changer #2)

Skipping empty node 1
1 STB(s) found:
-------------
STB 1: port=0, node=0, changer=2, GUID=0x001ac3902d820000
```
I'm at a lost. Either I've got something broken or Comcast broke firewire control on all their STBs with the Xfinity "upgrade".
Is there anyone out there that can confirm having the Xfinity branding on their box's user guide (not that any of us use it) and still being able to use mythchanger?

---

### Post by Dan_R on 2011-08-07
My RNG-110 works with the Xfinity updates with mythchanger and 6200ch. It's smaller than the 150 and has no clock like most of the new boxes. I also have an older Motorola DCHxxxx box that works. I'm including a screenshot of my menu through VNC so you believe me :D

RNG-110
mythchanger -v -f 7 -c 201

mythchanger .10f beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
STB Vendor ID: 0x5094 Model ID: 0x10755, (Using user selected channel changer #7)

1 STB(s) found:
-------------
STB 1: port=0, node=1, changer=7, GUID=0x00509400001f2110

---

### Post by chrismurf2900 on 2011-08-07
Just as an update, so everyone knows I'm still looking into this...

I have yet to find a solution on fixing the issue with changing channels.  So far, only know the commands to make a channel go up or down, as well as the ability to check the power status (can't turn on or off yet).

Unfortunately, it seems like (at this point), I'll have to try every iteration and see what happens.

Hopefully I'll have more to report this month.  If anyone else has any updates/fixes, please let me know.

Thanks!

---

### Post by arthurdent22 on 2011-08-13
I just picked up a RNG-150 cable box from Comcast and I find the issue - video works but no channel changing vie firewire.
One suggestion - as a workaround - the cable box has a "Set VCR Recording" option in the program grid. Anybody tried using that to set the channels for recording? It is far from ideal, but you should be able to look at upcoming recordings in mythweb and make sure the cable box has VCR settings for them. At least it b eats having to manually set the box via the remote for each recording.

---

### Post by tim273 on 2012-10-22
Bump...

Any updates on this or is it officially dead?

---

### Post by wildmanne39 on 2012-10-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

