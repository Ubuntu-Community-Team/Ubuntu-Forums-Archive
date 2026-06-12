---
title: "[SOLVED] More Tuners: More HEADACHES"
date: 2008-02-21
forum: Mythbuntu
---

### Post by volkswagner on 2008-02-21
I am still pecking away at my setup:

Master BE/FE:
[LIST=1]
[*]Capture Card 1 is PVR350 iput TV coax Vid. Source CATV
[*]Capture card 2 PVR150 Input TV coax Vid. source CATV, Input 2 s-vid source DigitalCable
[*]Capture Card 4 SA 3250HD cable box via firewire, vid. source DigitalCable
[/LIST]

Slave BE/FE:
[LIST=1]
[*]Capture Card 3 Kworld 110 input 1 coax (QAM) vid. source DTV
[/LIST]

I have verified capture of local and a few cable channels on firewire.  According to Mythtv how to the SA 3250HD is supported and no channel changer is required.  I left that field blank in setup for this video source.  I have three sources set up, DTV for QAM only a few channels, CATV via Schedules Direct for basic cable, and DigitalCable from SD for all channels avail on my SA 3250HD box.

The channel change is not working via firewire.  If I try to record a current show via the guide, selecting a channel from DigitalCable fails.  The card it is trying to tune is card 1(confirmed via backend.log).  This card obviously cant tune in.  If I am in live tv and manually change the card to the firewire box I can view whatever the box is tuned to.  I can also switch to the PVR150 and manually change the input and view the cablebox output.  

So can anyone help diagnose channel changing via firewire?  If and when I can get it to work, will I be able to use it for the PVR150 also?  Big dream I know!

---

### Post by newlinux on 2008-02-22
I have a similar setup, but with a motorola 6200 instead of an SA. You might want to look into seeing if you can even change the channel at all outside of myth with the sa3250ch channel change script, which should be somewhere on your system (try slocate sa3250ch). You will need to use this script as the channel change script for changing channels when you are trying to capture the cable box output from your PVR-150 (you shouldn't have to do this from your firewire capture setup because it should already know to call this script with the proper node number, but it seems this isn't working).


It is strange to me that it is trying to change the channel on the wrong tuner. That sounds like there is something wrong with your sources. Is the channel you are trying to tune to in both your CATV and your DigitalCable sources?

Are you planning on using the same box to capture from firewire as you are using to capture from the PVR-150 analog input?

---

### Post by volkswagner on 2008-02-22
I do have separate video sources.  Some channels are the same, up to channel 62 or so.  I selected a HD channel, 702.  The show info would be the same on SD channel 2.  702 only exists on digitalCable video source.  I do only have one box.  I would like to use it for both inputs.  I would also like to avoid IR blasters.  This is why I have hopes of using firewire to change the channels.  I do realize this has conflict written all over it.  
The reasons for my setup....the firewire will only access limited channels.  FW is my only, current ABC HD input (I don't seem to pick it up with QAM on my Kworld).  I am also using the 150 to pick up cable channels not available without a STB.

---

### Post by newlinux on 2008-02-22
Cool, so long as you realize the potential conflict issues you should be able to do what you want (I have done the same thing in the past for similar reasons - TNTHD only available via firewire, but capturing other channels through my PVR-150 capture and the cable box. Since they are two separate tuners tied to really only one tuner, I had to be careful not to have two shows scheduled to record at the same time on both tuners, and not to use liveTV on either tuner when one is being used for recording. It was a bit tricky sometimes - I had to setup the order of tuners for liveTV to avoid some problems). 

Doesn't sound like you have a problem with your sources. But It is weird that it is trying to change a channel on a tuner that doesn't have that channel...

Have you tried changing the channel command line? the script I referenced is for changing it via firewire... Should be at:

/usr/share/doc/mythtv-backend/contrib/channel_changers/

We can see if firewire channel change via commandline is at least working... You'll need to use it for your PVR-150/cable box setup...


Also, just something to try, have you scanned QAM-64 and QAM-256? Most of my QAM available channels are on QAM-256, but two of the locals are on QAM-64 in my area.

---

### Post by dannyboy79 on 2008-02-22
i can chime in here as I tried to do this as well with my SA3250HD stb and firewire. I could view many stations (locals and whatnot) captured over firewire but for the life of me, the channel changer would not change the channel no matter what! I tried benton roberts ([http://bentonroberts.com/personal/media-server/code](http://bentonroberts.com/personal/media-server/code)) enhanced sa3250hd channel changing scripts to no avail. so i just went the ir-blaster route and don't care that the HD channels I am recording are being downgraded thru the s-video output from the stb into my pvr-350. my ir-blaster is ROCK solid though! it's a serial ir-blaster. I covered the emitter with aluminum foil because ambient lighting can mess with it. I can provide you my channel changing script, lircd or whatever you'd like if you want. 

here's some of the email traffic I generated with many people from the mythtv mailing list.

Can you pretty please take some time to help me troubleshoot this? I can't
> seem to get ANY channel changing to work with my cable box? I live in
> Milwaukee, WI. I have TWC. I am using Ubuntu Feisty with 20.2 version of
> mythtv that was created by Mario and put into the proposed repo for feisty
> and edgy. (mario is the developer of mythbuntu) So, here's some of the info
> that I have posted to others but they haven't helped much. Just not sure why
> the channels just won't change???
>
>
> Host Adapter 0
> ==============
>
> Node 0 GUID 0x00194739706a0000
> ------------------------------
> oMPR n_plugs=1, data_rate=2, bcast_channel=63
> oPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
> channel=0, data_rate=1, overhead_id=0, payload=146
> iMPR n_plugs=0, data_rate=2
>
> Node 1 GUID 0x00506256000010be
> ------------------------------
> libiec61883 error: error reading oMPR
> libiec61883 error: error reading iMPR
>
> here are some "dmesg | grep iee" results after starting up with everything
> hooked up:
>
> ieee1394: unsolicited response packet received - no tlabel match
> [ 5.006696] ieee1394: Speed probe of node 0-00:1023 yields S400
> [ 5.014482] ieee1394: Node added: ID:BUS[0-00:1023] GUID[00194739706a0000]
> [ 5.014904] ieee1394: Host added: ID:BUS[0-01:1023] GUID[00506256000010be]
> [ 16.875675] ieee1394: raw1394: /dev/raw1394 device initialized
>
> sudo firewire_tester -p -n 0 -v 5
> Testing P2P connection, node 0, channel 0
> p2p: success, 369 packets received
> daniel[at]UBUNTU:~/Desktop/libiec61883-1.1.0/examples$ sudo firewire_tester
> -p
> -n 0 -v 5
> Testing P2P connection, node 0, channel 0
> p2p: success, 323 packets received
> daniel[at]UBUNTU:~/Desktop/libiec61883-1.1.0/examples$ sudo firewire_tester
> -p
> -n 0 -v 5
> Testing P2P connection, node 0, channel 0
> p2p: success, 417 packets received
>
> As you can see I believe everything is working correctly. I just can't for
> the life of me get the channel change script to work.
>
> I checked /dev/raw1394
> ls -la /dev/ | grep raw
> crwxrwxrwx 1 root disk 171, 0 2007-09-05 10:22 raw1394
> so I added mythtv to the disk group.
>
> I tested test-mpeg2 again and I got a file with some size to it!!!! This was
> the error despite the file having some size this time:
>
> test.mpg
> libiec61883 warning: Overlayed connection on channel 0.
> You may need to manually set the channel on the receiving node.
> Starting to receive
> done.
>
> So I guess I just need to figure out how to change the channel. So what I
> did was ensure that sa3250ch had my vendor_id etc etc, it didn't. So I added
> it and recompiled sa3250ch.c. THen when I run it when logged in as root,
> this is the output:
> # ./sa3250ch 24 -v
> node 0: vendor_id = 0x00001947 model_id = 0x00000be0
> AV/C Command: 024 = cmd0=0x00487ce7 cmd2=0x04343230 cmd3=0xff000000
> AV/C Command: 024 = cmd0=0x00487c67 cmd2=0x04303234 cmd3=0xff000000
>
> but the channel on the cable box doesn't change, isn't it suppose to?
>
> Can you provide any help please.
>
>
> Daniel

---

### Post by volkswagner on 2008-02-22
Following the readme for SA3250HD channel changer it seems dated.  Does anyone know what to do with the gzip file in /usr/share/doc/mythtv-backend/contrib/channel_changers/

from the readme

sa3250ch is a small program that changes channels on a Scientific Atlanta
2	SA3250HD cable box via a 1394 (aka. Firewire) connection. It is based off
3	of 6200ch by Stacey Son (mythdev@son.org).
4	
> 5	To use this with mythtv do the following:
6	
7	(1) Make sure you have 1394/Firewire drivers installed in your kernel.
8	
9	(2) Install libraw1394, librom1394 and libavc1394.
10	
11	(3) Compile and install "sa3250ch":
12	
13	      # cc -o sa3250ch sa3250ch.c -lrom1394 -lavc1394 -lraw1394
14	      # cp sa3250ch /usr/local/bin
15	
16	(4) Connect a 1394/Firewire cable from your computer to your SA3250HD and test:
17	
18	      # sa3250ch <your_favorite_channel_number>
19	
20	(5) Configure Mythtv to use the channel changer by running the "setup"
21	program and adding to "/usr/local/bin/sa3250ch" to the "External channel
22	change command" field under "Connect source to Input".

I do not see librom1394 in the repository. Do I need it. I am not familiar with compiling.  Any step by step instructions are greatly appreciated.

---

### Post by volkswagner on 2008-02-22
I created the text file and put it in /usr/local/bin.  I have tried various permisions and not able to launch.

```
eric@FamilyRoom:~$ sa3250ch 702
-bash: /usr/local/bin/sa3250ch: Permission denied
```

I have tried

```
sudo chmod 666 /usr/local/bin/sa3250ch
```

Also tried changing groups in thunar.  The settings seem to stick even after a reboot, but I still get permission denied.  Do I need to do the compile?  Do I need to make it executable?  If so, How do I do it?

---

### Post by newlinux on 2008-02-22
Yes, you need to compile it. The compiled file will be executable. I didn't need to install librom1394. This is what I did and it compiled successfully, after copying it to a different directory.

```

sudo apt-get install libraw1394-dev libavc1394-dev
gunzip sa3250ch.c.gz
cc -o sa3250ch sa3250ch.c -lrom1394 -lavc1394 -lraw1394

```

---

### Post by volkswagner on 2008-02-23
I am getting some action thanks to newlinux.

My problem now is when the channel change command does work, it selects the wrong channel.

```
sa3250ch 540
```

yielded me channel 52

```
sa3250 702
```

yielded me channel 560

any thoughts?  Do I need to use a different code?  It seems to me while checking logs that when I requested a recording on channel 7, the backend listed this as 1702 or something.

I just tried to check the logs but no return, it just hangs, I have to hit Ctrl+c.

---

### Post by newlinux on 2008-02-23
Hmm, maybe you should try one of the versions in the link dannyboy gave above. For this version though, try using the -s for single channel mode and the -v option (with and without the single channel option) to see if you get more information:

```

sa3250ch -v -s 702

```

Are you referring to trying to check mythbackend logs and it hangs? That seems weird. How are you checking it? And it seems weird that it is selecting the wrong channel in myth (and the wrong tuner). Still makes me think something else is going on.

---

### Post by volkswagner on 2008-02-23
newlinux thanks.  The following works flawlessly, any channel I throw at it.


```

eric@FamilyRoom:~$ sa3250ch -v -s 702
node 0: vendor_id = 0x00001692 model_id = 0x00000be0
Using single number channel change command method
AV/C Command: cmd0=0x00487ce7 cmd1=0x0402be00 cmd2=0x00000000
```


If I do not use the single switch it goes to the wrong channel.

```
eric@FamilyRoom:~$ sa3250ch -v 702
node 0: vendor_id = 0x00001692 model_id = 0x00000be0
AV/C Command: 702 = cmd0=0x00487ce7 cmd2=0x04323037 cmd3=0xff000000
AV/C Command: 702 = cmd0=0x00487c67 cmd2=0x04373032 cmd3=0xff000000

```

The above actually went to channel 560

I use the following command to access the log file.
I am not sure why it hangs.  I will try a BE restart to see if it fixes the problem.
Restarting BE corrected the problem.  No errors in log either

```
 tail -f /var/log/mythtv/mythbackend.log
```

trying to access the frontend.log hangs, I can however access frontend.log.1

frontend.log does exist in file manager.

---

### Post by newlinux on 2008-02-23
Okay... tail -f is supposed to hang. It reads the file in real time and waits into more is output into the log (the f stands for follow). If you just want to see, say, the last 30 lines of the log you would do:

```

tail -n 30 /var/log/mythtv/mythbackend.log

```

Glad the channel change script works. You can use that with your pvr-150 capture setup as the channel change command. As for your firewire capture, I'm not sure how to apply it to that from myth, but that is probably the problem - the firewire capture isn't using the single channel mode and not changing the channels right...

---

### Post by volkswagner on 2008-02-23
The channel changer with the single argument works every time.  I can not figure out why the capture via firewire is not 100%.  I have run many successive channel changes via the command line.  I then follow up with the firewire_tester set p2p.  Most of the time I get a good connection.  It even seems to pick up channels which I did not think I would get, such as Discovery HD, Noggin, WE, etc.

It seems that when I get "testing failed", it will even fail on the free channels.  I can't seem to reproduce the fail to see when it happens, such as my intervention using the cable remote, or going to a channel which I thought would be 5c protected.  I don't get it.

I see dannyboy's link to the enhanced channel changer looks like it may use the -s argument.  I am not sure though.

I am not able to get the firewire to work after boot though.  I have added users to the disk group which /dev/libraw1394 belongs to root and is in the disk group.  I have to run
```

sudo chmod a+rw /dev/raw1394 /dev/dv1394
plugctl -n 0 "oPCR[0].n_p2p_connections=1"
```

after reboot.

---

### Post by newlinux on 2008-02-23
I had the same problem with ownership, and my firewire capture breaks whenever I go to a 5c station and I would have to reset it with the primer (I use broadcast for mine). I ended up taking all 5c channels out of my firewire lineup. This was unecessary for just using the channel changer with the pvr-150 so I left all channels in that lineup. For the permissions/owner problem:

[https://help.ubuntu.com/community/MythTV_Firewire#head-d68acd8038b522f9ef0096d35a51433e1ff0ab7f](https://help.ubuntu.com/community/MythTV_Firewire#head-d68acd8038b522f9ef0096d35a51433e1ff0ab7f)
 helped me so I don't have to change permissions after every reboot.

---

### Post by volkswagner on 2008-02-24
Wanted to mark this as solved and summarize. Thank you newlinux!

The sa3250ch included with mythbuntu is working great.  When I specified the channel change script for the svid on my pvr150 I listed like this in input setup.

```
sa3250ch -s -v
```

I followed these instructions to get firewire ownership prior to mythbackend starting and added the priming firewire function.

[https://help.ubuntu.com/community/MythTV_Firewire#head-d68acd8038b522f9ef0096d35a51433e1ff0ab7f]("https://help.ubuntu.com/community/MythTV_Firewire#head-d68acd8038b522f9ef0096d35a51433e1ff0ab7f")

I first followed the firewire setup found at mythv main site 

[http://www.mythtv.org/wiki/index.php/FireWire]("http://www.mythtv.org/wiki/index.php/FireWire")

I also created separate video sources for firewire to include only unprotected channels.  I allowed my full lineup for the svid input.  

My video sources look like this
[LIST=1]
[*]CATV=Basic Cable channels avail via coax directly to tuners
[*]DigitalCable=All channels avail from STB svid out to tuner
[*]FireWire=Edited list of DigitalCable to only include unprotected channels
[*]DTV=Only QAM channels avail from Coax direct to Kworld110
[/LIST]

I hope this can help someone else.  My remaining tasks include setting up recording profiles and priority settings to limit conflicts.

---

