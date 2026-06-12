---
title: "Hauppauge HVR-2250 analog support issues with MythTV"
date: 2010-09-03
forum: Mythbuntu
---

### Post by jjwest85 on 2010-09-03
Hi,

I wanted to start an new thread for the discussion of analog support for the Hauppauge 2250 card started at this thread: [http://ubuntuforums.org/showthread.php?t=942403&page=29](http://ubuntuforums.org/showthread.php?t=942403&page=29).  This part of the drive has just now come out in a first draft from Steven Toth's website and KernelLabs.com.

Original post from Steven Toth:
[http://www.kernellabs.com/blog/?p=1443](http://www.kernellabs.com/blog/?p=1443)
> 
SAA7164 Analog support complete?

First draft is available from [http://kernellabs.com/hg/~stoth/saa7164-v4l]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l")
 Firmware is available from [http://www.steventoth.net/linux/hvr2...mwares/4019072]("http://www.steventoth.net/linux/hvr22xx/firmwares/4019072")
 Comments welcome.                      Here is my current dmesg out put for "saa":

```
dmesg | grep saa
[   12.907123] saa7164 driver loaded
[   12.907171] saa7164 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.907449] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   12.907454] saa7164[0]/0: found at 0000:08:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfb800000
[   12.907460] saa7164 0000:08:00.0: setting latency timer to 64
[   12.907463] IRQ 17/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.100326] saa7164_downloadfirmware() no first image
[   13.100566] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   13.100569] saa7164 0000:08:00.0: firmware: requesting NXP7164-2010-03-10.1.fw
[   13.322496] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   13.322498] saa7164_downloadfirmware() firmware loaded.
[   13.322507] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   13.322512] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   13.322513] saa7164_downloadfirmware() BSLSize = 0x0
[   13.322514] saa7164_downloadfirmware() Reserved = 0x0
[   13.322516] saa7164_downloadfirmware() Version = 0x1661c00
[   20.545780] saa7164_downloadimage() Image downloaded, booting...
[   20.655477] saa7164_downloadimage() Image booted successfully.
[   22.991705] saa7164_downloadimage() Image downloaded, booting...
[   24.419422] saa7164_downloadimage() Image booted successfully.
[   24.461423] saa7164[0]: Hauppauge eeprom: model=88061
[   25.163796] DVB: registering new adapter (saa7164)
[   28.452027] DVB: registering new adapter (saa7164)
[   28.452234] saa7164[0]: registered device video0 [mpeg]
[   28.683982] saa7164[0]: registered device video1 [mpeg]
[   28.896806] saa7164[0]: registered device vbi0 [vbi]
[   28.896830] saa7164[0]: registered device vbi1 [vbi]
[   38.946804] saa7164[0]-FWMSG: 0-00:01:15.866;thread 0xd1833363;dbgtmmhSysPwstMan;switching off analog reception...
[  239.069138] saa7164[0]-FWMSG: 0-00:04:36.433;thread 0xd181f363;mhStreamHdl;Received SET_CUR DMA State to ACQUIRE
[  239.071927] saa7164[0]-FWMSG: .450;thread 0xd181f363;mhStreamHdl;Received SET_CUR DMA State to PAUSE
[  239.246082] kernel BUG at /home/jeremy/Downloads/saa7164-v4l-0feb7df206fa/v4l/saa7164-buffer.c:274!

```Notice the 4th from the bottom entry talking about "switching off analog reception...".  

[markuswells]("http://ubuntuforums.org/member.php?u=307842") was the first to see this line. 

I tried doing a channel scan in MythTV, but it froze around channel 38 for an ATSC scan from 2 to 83 for OTA channels.  It could be there are not anymore analog channels in my area.  I have a feeling that this message is more than just if I have channels or not though.

---

### Post by jjwest85 on 2010-09-03
Hi,

I also wanted to post the procedure I used to install the firmware and driver for the analog support.  This is based off of [LowSky's guide]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212") with a few modifications.  I do not know if this works, it could be the problem for all I know.

1. Open Terminal
```
cd Downloads/
```2.  Obtain the needed files:
```
wget http://kernellabs.com/hg/~stoth/saa7164-v4l/archive/tip.tar.gz
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
```3.  Move firmware to correct location:
```
sudo cp *fw /lib/firmware
```4.  Now to install the driver:
```
tar vfxz tip.tar.gz
cd saa7164-v4l-<specific current thread>
make CONFIG_DVB_FIREDTV:=n
sudo make install
```<specific current thread> = insert specific current thread from tip.tar.gz download.

5.  Reboot.

OR 

From LowSky:
```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware

hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot 
```6.  check dmesg in a terminal with:
```
dmesg | grep saa
```

---

### Post by markuswells on 2010-09-06
After the new firmware updates on Sept 5, 2010 (and following the steps here) I am still getting the same "switching off analog reception..." message.

Looking at mythbackend.log shows "Error: Ran out of free AUDIO buffers ..."

Anyone have any ideas if its a mythtv setting, I still think its firmware, but I want to be sure its not some settings I am not doing right.

---

### Post by justNiz on 2010-09-10
> **markuswells said:**
> After the new firmware updates on Sept 5, 2010 (and following the steps here) I am still getting the same "switching off analog reception..." message.

Looking at mythbackend.log shows "Error: Ran out of free AUDIO buffers ..."

Anyone have any ideas if its a mythtv setting, I still think its firmware, but I want to be sure its not some settings I am not doing right.

I am at work right now so I can't fire up mythfrontend to check but I think that on the Utilities->Setup->General->Audio page it has a place where you can set the size of audio buffer by checking "aggressive buffering" or something similar. Have you already tried checking/unchecking that?

I believe there's also an Extra Audio Buffering checkbox at Setup->TV Settings->Playback.

---

### Post by jac1d on 2010-09-16
> **markuswells said:**
> After the new firmware updates on Sept 5, 2010 (and following the steps here) I am still getting the same "switching off analog reception..." message.



Mark - 

What firmware are you referring to?  I can't find any firmware on Steven or the Hauppauge site from September 5th of this year.  The firmware Steven listed to try with his analog driver build was from March IIRC.

-Jeff

---

### Post by RadicalGeek on 2010-09-20
I tried the driver for the analog channels but when I scanned for channels all I get is timed out, no signal.

---

### Post by myrlin16 on 2010-09-21
> **RadicalGeek said:**
> I tried the driver for the analog channels but when I scanned for channels all I get is timed out, no signal.

Ditto, I'm having the same problem.  I can use the following to test that the hvr-2250 analog inputs are working:

   v4l2-ctl -d /dev/video1 --set-freq=55.250
   mplayer /dev/video1

That will play video from my hvr2250, but only if I have stopped mythtvbackend from running.  As soon as I restart mythtvbackend this test fails giving me a blue screen and a nice fuzz sound.

When I go into mythtv-setup and attempt to add the new devices I cannot seem to get them to work.  I have removed all other devices and tried multiple configurations.  No matter what I do when I select the tuner under "input connections" and scan for channels it quickly runs through all the channels saying "timed out, no signal".

Somebody please help.  I've been trying to get this to work for a week now and the WAF (Wife Acceptance Factor) is going down for my mythbox!

I can post config files, logs, etc.  Just let me know what will help.

---

### Post by myrlin16 on 2010-09-21
Just FYI, I have a pvr-150 and an hvr-2250 in the same box.  The pvr-150 works great.  I have thought about removing the pvr-150 to see if my problems are an interaction between the cards. 

RadicalGeek, do you have any other cards in your setup?

---

### Post by RadicalGeek on 2010-09-25
No I just have the hvr-2250 only.

---

### Post by RadicalGeek on 2010-09-25
I got it to see the analog part but it still doesn't read any channels in the analog.  Also how do you get rid of the first channel as, "Add New Channel."

---

### Post by jjwest85 on 2010-09-26
Hi,
I wanted to give an update.  I am still getting the dmesg error saying that it is turning off analog support on this card.  Besides that though, in mythtv, I am having MythTV automatically find an "Analog V4L capture card", which is new since I have updated to the newest release of the analog driver.  I have updated my walkthrough above, so that it works for whatever thread/update they are on for the driver.

I was also able to do a scan with the new card type of "analog" and input of "tuner", but it didn't find anything.  Partly because I don't think their are any analog channels where I live anymore.

Summary of MythTV setup:
Card type: Analog V4L capture card (defaulted to this after I did another driver install).
Input type: tuner
Video source name: Analog0
Input connections Display Name: Antenna2 (my digital names are Antenna0 and Antenna1, which still work)

I used the rest of the default settings in Myth-backend under headings for the Capture cards, Video sources, and Input connections.

Let me know if anyone has any luck now with the latest driver build or at least also is given the default card type of analog now.

---

### Post by RadicalGeek on 2010-09-26
Ok gang a quick update.  I got the hvr-2250 card installed on the backend: 2 V4L, 2 MJPG, and 2 DBV.  When going in to the frontend to watch TV it says all the tuners are busy.  Check the system info and all 6 tuners have a yellow dot next to them.  Setup the IP for the backend 2 by the IP address for the box, but still get the same error.

---

### Post by jjwest85 on 2010-09-26
@RadicalGeek
Are you able to get channels to populate in the scan on the backend for the 2 V4L card types?  Also, what is the MJPG card type?

---

### Post by RadicalGeek on 2010-09-26
@JJ

When you you go into the back end to setup the hvr2250 card it comes up also under mjpeg.

---

### Post by mythnutz on 2010-09-27
I am a total noob, but thru your notes I was able to get the analog ports working. I think. 
 
However, all I see is a blue screen using mplayer or VLC. Any ideas how to tell mplayer or vlc, use svideo or composite?
 
Thanks.

---

### Post by mythnutz on 2010-09-27
made progress. I used the v4l2-ctl --list-inputs to get a list of all the inputs and then used  v4l2-ctl --set-input to change the card input to composite. Happy to report that composite works and I can see video. However, changing the card input to Svideo did not work (no video at all).
 
I think knowing how to use v4l2-ctl is good to troubleshoot your configuration. Mythtv does nt make it easy to test the setup. 
 
Any advice on the Svideo part of the HVR-2250 would be appreciated.

---

### Post by aflores3 on 2010-09-27
> **jjwest85 said:**
> Hi,
I wanted to give an update.  I am still getting the dmesg error saying that it is turning off analog support on this card.  Besides that though, in mythtv, I am having MythTV automatically find an "Analog V4L capture card", which is new since I have updated to the newest release of the analog driver.  I have updated my walkthrough above, so that it works for whatever thread/update they are on for the driver.

I was also able to do a scan with the new card type of "analog" and input of "tuner", but it didn't find anything.  Partly because I don't think their are any analog channels where I live anymore.

I'm having the exact same results. followed post 2 of this thread. dmesg says its turning off analog. MythTV finds Analog V4L capture card, scanning finds no channels. 

My PVR-150 still finds analog channels in my area.

---

### Post by tdyboc on 2010-09-27
Any updates on this adapter?  Still getting switching off analog reception.

---

### Post by mythnutz on 2010-09-27
> **tdyboc said:**
> Any updates on this adapter? Still getting switching off analog reception.
 
 
FYI:
 
From the driver developer "I have never noticed any issues related to or around this message."
 
[http://www.kernellabs.com/blog/?p=1443#comment-1824](http://www.kernellabs.com/blog/?p=1443#comment-1824)

---

### Post by tdyboc on 2010-09-27
I downloaded the latest (I think) but I still see that message.  I am still figuring out all this so maybe it will work or I have something not configured properly.

---

### Post by markuswells on 2010-09-27
So, I have spent several days in "full on attack mode" trying to get this cards analog side to work in mythtv.

I have re-installed the OS from scratch several times trying small variations on each install, following these steps exactly
[http://ubuntuforums.org/showpost.php?p=9803479&postcount=2](http://ubuntuforums.org/showpost.php?p=9803479&postcount=2)

Scanning for channels works fine for digital, but no luck with the analog. I 'fetched' the channels from SchedulesDirect and that has always worked well me.

I still see the "turned off" message
```

dmesg | grep saa
[   54.722802] saa7164[0]-FWMSG: 0-00:01:17.233;thread 0xd1833363;dbgtmmhSysPwstMan;switching off analog reception...

```
but the following test works, so I am ignoring it for now.

Just like others on this topic, I am able to 'test' the analog half of this card by doing the following (I hated installing v4ls-ctl but its very helpful in debugging this)
```

sudo /etc/init.d/mythtv-backend stop
v4l2-ctl -d /dev/video1 --set-freq=55.250
mplayer /dev/video1

```
I tried to find other frequencies, but it was not worth it, this freq works fine.

So the card seems to be installed correctly.

I think we need someone who has this card working in mythtv to help figure out what the configuration settings should be. For example looking at my mythbackend.log shows "Error: Ran out of free AUDIO buffers ..." but I have tried some of the suggestions above and still have the same issue.

For those of you who do not know, if you are watching cable TV, then you are likely watching analog (unless you are paying extra for the digital).

---

### Post by mythnutz on 2010-09-27
> **markuswells said:**
> So, I have spent several days in "full on attack mode" trying to get this cards analog side to work in mythtv.
 
I have re-installed the OS from scratch several times trying small variations on each install, following these steps exactly
[http://ubuntuforums.org/showpost.php?p=9803479&postcount=2](http://ubuntuforums.org/showpost.php?p=9803479&postcount=2)
 
Scanning for channels works fine for digital, but no luck with the analog. I 'fetched' the channels from SchedulesDirect and that has always worked well me.
 
I still see the "turned off" message
```

dmesg | grep saa
[   54.722802] saa7164[0]-FWMSG: 0-00:01:17.233;thread 0xd1833363;dbgtmmhSysPwstMan;switching off analog reception...

```
but the following test works, so I am ignoring it for now.
 
Just like others on this topic, I am able to 'test' the analog half of this card by doing the following (I hated installing v4ls-ctl but its very helpful in debugging this)
```

sudo /etc/init.d/mythtv-backend stop
v4l2-ctl -d /dev/video1 --set-freq=55.250
mplayer /dev/video1

```
I tried to find other frequencies, but it was not worth it, this freq works fine.
 
So the card seems to be installed correctly.
 
I think we need someone who has this card working in mythtv to help figure out what the configuration settings should be. For example looking at my mythbackend.log shows "Error: Ran out of free AUDIO buffers ..." but I have tried some of the suggestions above and still have the same issue.
 
For those of you who do not know, if you are watching cable TV, then you are likely watching analog (unless you are paying extra for the digital).
 
For what is worth, according to the developer, that switching analog off error means nothing.

---

### Post by markuswells on 2010-09-27
I just installed the latest update and yes the "turned off" message is gone, it was a firmware log and the firmware is controlled by hauppauge, so for now its simply turned off.

So for now I can only assume its because of the "free AUDIO buffers.

Looking at my mythbackend.log shows "Error: Ran out of free AUDIO buffers ..."

Anyone else seeing that?

---

### Post by myrlin16 on 2010-09-29
> **RadicalGeek said:**
> Ok gang a quick update.  I got the hvr-2250 card installed on the backend: 2 V4L, 2 MJPG, and 2 DBV.  When going in to the frontend to watch TV it says all the tuners are busy.  Check the system info and all 6 tuners have a yellow dot next to them.  Setup the IP for the backend 2 by the IP address for the box, but still get the same error.

I have digital working and was having this problem.  Every time I would reboot the tuners would say they are busy.  Adding a delay to the mythbackend init script fixed the problem.  The problem has something to do with the backend coming up before mysql, at least that is what I gathered from others while trolling forums.

This is what I have in /etc/init/mythtv-backend.conf 

```

# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (      local-filesystems 
          and   net-device-up IFACE=lo) 
#          and   mysql-started           )
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        sleep 20
        /usr/bin/mythbackend $ARGS
end script

```

I added the "sleep 20".  You might also note I added "mysql-started" to the start on items... I ended up commenting that out because it required editing the mysql init script and stops working every time mysql is updated.  20 Seconds works for me, but you may want to go a little longer as I still sometimes get the "tuner busy" note.

On another note, this also goes away when I stop and restart the backend.

---

### Post by myrlin16 on 2010-09-29
> **markuswells said:**
> 

```

sudo /etc/init.d/mythtv-backend stop
v4l2-ctl -d /dev/video1 --set-freq=55.250
mplayer /dev/video1

```
I tried to find other frequencies, but it was not worth it, this freq works fine.

I found more frequencies here:
[http://en.wikipedia.org/wiki/North_American_cable_television_frequencies]("http://en.wikipedia.org/wiki/North_American_cable_television_frequencies")

There is a big table in the middle of the article that has the frequencies in the second column.  For example, lowband channel 2 "55.25" corresponds to "--set-freq=55.250".  I have tried a couple of other channels, but not many of them.

My hvr2250 analog tuners seem to be working fine, they just aren't working with myth.  I see there is a new release of the driver, I will try it out and report back if I learn anything.

---

### Post by mythnutz on 2010-09-29
All my analog ports are working. Composite and Svideo. Digital TV antenna works too.

---

### Post by myrlin16 on 2010-09-30
> **mythnutz said:**
> All my analog ports are working. Composite and Svideo. Digital TV antenna works too.

mythnutz, thanks.  I think several of us have the card analog and digital working... the question is do they work with myth?  If so, how do you have them set up?  What options did you choose in mythtv-setup?

On another note, I tried the latest driver from kernellabs.  I once again was able to tune channels using v4l2-ctl and watch using mplayer, but I was unable to get myth to work with the hvr2250 analog.  I tried every combination of settings I thought were reasonable in mythtv-setup but was never able to scan and pick up a single channel.

---

### Post by justNiz on 2010-09-30
I installed everything but couldn't get mythtv to scan analog channels either. 

For other reasons I'm planning on reformatting/reinstalling my mythbox from CD when Ubuntu 10.10 comes out. Does anyone know if 10.10 will already contain the latest saa7164 analog driver and firmware?

Also, does anyone know if saa7164 FM radio support got implemented? (Steven Toth said it depended on saa7164 analog being implemented).

---

### Post by markuswells on 2010-09-30
> **RadicalGeek said:**
> Ok gang a quick update.  I got the hvr-2250 card installed on the backend: 2 V4L, 2 MJPG, and 2 DBV.  When going in to the frontend to watch TV it says all the tuners are busy.  Check the system info and all 6 tuners have a yellow dot next to them.  Setup the IP for the backend 2 by the IP address for the box, but still get the same error.

Can you expand on this, you have 2V4L, 2MJPG and 2 DVB. Why the 2MJPG and how do you put that to use?

---

### Post by LowSky on 2010-10-06
The download and install instructions for analog support should look like this

```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware

hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```

---

### Post by aflores3 on 2010-10-08
> **myrlin16 said:**
> mythnutz, thanks.  I think several of us have the card analog and digital working... the question is do they work with myth?  If so, how do you have them set up?  What options did you choose in mythtv-setup?

I'm one of the several that have it working, just not within myth. 

Its so close I can taste it! Thanks to all for putting in the time to make it work.

---

### Post by navodeo on 2010-10-12
> **LowSky said:**
> The download and install instructions for analog support should look like this

```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware

hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```

Lowsky thanks for this concise instruction set.  I've been struggling & waiting for analog support for many months.  This is my first Myth box and I must say it's been frustrating to say the least!  I have searched all over trying to piece this all together.  I've got the above fw installed and dmesg shows it loaded with no errors.

Now this is where I'm stuck now and I can't find help anywhere so far.  MythTV setup - I think I've got everything right down to the Input Connections area but when I get to the "connect source to input" and scan for channels I'm lost!  The "frequency table" and "modulation" tabs have me stumped - I'm a newbie ok.  I've tried many if not all of the combinations and can't find a channel.  

BTW - I have Cableone and am just trying to access the analog channels for the time being.

Any help would be greatly appreciated.  

Thanks.

---

### Post by mythnutz on 2010-10-15
> **aflores3 said:**
> I'm one of the several that have it working, just not within myth. 
 
Its so close I can taste it! Thanks to all for putting in the time to make it work.
 
I can't get it to work with Myth. It works with VLC and V4L + Mplayer. I have not had time to mess with it in weeks. The WAF is in the toilet.

---

### Post by mythnutz on 2010-10-18
Ok, looks like I am onto something. If I set the input to my Svideo (input 2) connector on the card using v4lin and fire up mplayer, I see video. If I go to the myth front end and try to watch live TV, I get a blue screen (sentence enhancers here). I go back to mplayer and more blue screen like in myth. If I check the input setting using v4lin --get-input, I see that the input was changed to input 5. Changing the input back to 2 I see video again on mplayer.... so, how the heck do I make myth use only input 2 as default? (the frigging card has 2 of each).

---

### Post by myrlin16 on 2010-10-19
Mythnutz, your last comment prompted me to search for any information on changing default input for the card.  Unfortunately I didn't find anything useful, but I did find this comment from the developer (Steven Toth) that could be related:

> 
Vinnie, Myth works OK for me providing that I restrict analog to specific tuners and digital to another. I have an open bug where, if you attempt to use a single tuner (half of the board) for both analog and digital, the mythtv switch from analog to digital works fine, the switch back from digital to analog results in blue video.
Other than this I have no known myth issues.

Found in comments from [July 31st]("http://www.kernellabs.com/blog/?p=1443") post on kernel labs blog.

I doubt it will make a difference, but it might be worth trying to set things up without digital just to see if myth is somehow switching to digital on us before we select analog. Steven apparently set his up with one input as analog only and the other as digital, I wish he had given more detail on exactly how.  I will try it myself the next time I get a chance... I can't right now as my wife is watching tv.  

My WAF is plummeting as well, I hope we can figure this out soon.

---

### Post by mythnutz on 2010-10-19
Yup, I did not find anything remotely useful on how to set defaults. All I found was some convoluted rules about Groups and other stuff. 
 
When I add the card to myth it discovers all the inputs. When I create settings for one input, it applies them to both. I might just nuke the install and start over.

---

### Post by myrlin16 on 2010-10-19
> **mythnutz said:**
> I might just nuke the install and start over.

Let us know if that works.  I've been hesitant to do the same because I have almost 700G of stuff that I don't want to have to move around and backup.  I'll do anything to make it work though!

---

### Post by dnobes on 2010-10-20
I have done a fresh install, and tested with only using the analogue tuners, and this does not fix the problem either...  I have done it for BOTH 0.23 AND 0.23.1...  I am running this on Ubuntu 10.04LTS and I am at a loss...

Digital works just fine following this, but no luck with the analogue:
hg clone [http://kernellabs.com/hg/~stoth/saa7164-v4l](http://kernellabs.com/hg/~stoth/saa7164-v4l)
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install

Then I tried this and had no luck ([Hauppauge_WinTV-HVR-2200]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200")):
```
make menuconfig
perl -p -i -e 's/FIREDTV=m/FIREDTV=n/' v4l/.config
edit as needed but should have all enabled that is needed
make
make install
reboot
```


But it did not work out for me either:
```
dnoble3@servermc:~/Hauppauge/saa7164-v4l$ make menuconfig
make -C /home/dnoble3/Hauppauge/saa7164-v4l/v4l menuconfig
make[1]: Entering directory `/home/dnoble3/Hauppauge/saa7164-v4l/v4l'
make -C /lib/modules/2.6.32-25-generic/build -f /home/dnoble3/Hauppauge/saa7164-v4l/v4l/Makefile.kernel config-targets=1 mixed-targets=0 dot-config=0 SRCDIR=/lib/modules/2.6.32-25-generic/build v4l-mconf
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:398: fatal error: opening dependency file scripts/basic/.fixdep.d: Permission denied
compilation terminated.
make[3]: *** [scripts/basic/fixdep] Error 1
make[2]: *** [scripts_basic] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make[1]: *** [/lib/modules/2.6.32-25-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/home/dnoble3/Hauppauge/saa7164-v4l/v4l'
make: *** [menuconfig] Error 2
dnoble3@servermc:~/Hauppauge/saa7164-v4l$ sudo make menuconfig
[sudo] password for dnoble3: 
make -C /home/dnoble3/Hauppauge/saa7164-v4l/v4l menuconfig
make[1]: Entering directory `/home/dnoble3/Hauppauge/saa7164-v4l/v4l'
make -C /lib/modules/2.6.32-25-generic/build -f /home/dnoble3/Hauppauge/saa7164-v4l/v4l/Makefile.kernel config-targets=1 mixed-targets=0 dot-config=0 SRCDIR=/lib/modules/2.6.32-25-generic/build v4l-mconf
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
make -f /lib/modules/2.6.32-25-generic/build/scripts/Makefile.build obj=scripts/kconfig hostprogs-y=mconf scripts/kconfig/mconf
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[3]: *** [scripts/kconfig/dochecklxdialog] Error 1
make[2]: *** [v4l-mconf] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make[1]: *** [/lib/modules/2.6.32-25-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/home/dnoble3/Hauppauge/saa7164-v4l/v4l'
make: *** [menuconfig] Error 2
```

I am not particularly sure which ncurses library they want...

I have been waiting 4 years for to get this working, but I am just not having any luck...

---

### Post by dnobes on 2010-10-20
OK, GOT IT WORKING!!!

To setup an analogue tuner all you need to do is in the MythTV backend setup of the Capture Card. When setting the card type as “IVTV MPEG-2 Encoder” the PVR-2250 card does not show-up/auto-fill. So just manually set the "Video Device" to "/dev/video1".  This is assuming you setup the digital card already, otherwise you can set it to "/dev/video0", BUT if you do, then make sure that if you setup a digital tuner it does not use the first tuner..

I setup my digital tuner first:
/dev/dvb/adapter0/frontend0

Then I setup my analogue tuner:
/dev/video1

Now they work like a charm!

Here is hoping all of you can reproduce!!!
*Credit goes to Robert Pollack on Steven Toth's page:
[http://www.kernellabs.com/blog/?p=1443](http://www.kernellabs.com/blog/?p=1443)

---

### Post by LowSky on 2010-10-21
Cool that it works but you basically lose use of half the card.

I guess for now it's a simple compromise.

Hopefully the driver gets better over time so we can have full capability.

---

### Post by angel12 on 2010-10-21
So i have just installed 10.10 to give this a shot, and i am stuck on building the modules. Here is my output:

```
make -C /home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l 
make[1]: Entering directory `/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/firmware'
make[2]: Leaving directory `/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-22-generic/build
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/au0828-video.o
/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/au0828-video.c: In function 'au0828_uninit_isoc':
/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/au0828-video.c:185: error: implicit declaration of function 'usb_buffer_free'
/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/au0828-video.c: In function 'au0828_init_isoc':
/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/au0828-video.c:255: error: implicit declaration of function 'usb_buffer_alloc'
/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/au0828-video.c:256: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l/au0828-video.o] Error 1
make[2]: *** [_module_/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/angel12/Downloads/saa7164-v4l-8da3bd06a289/v4l'
make: *** [all] Error 2
```


Any ideas?

---

### Post by LowSky on 2010-10-21
> **angel12 said:**
> So i have just installed 10.10 to give this a shot, and i am stuck on building the modules. Here is my output...

...Any ideas?


try it my way it will work

```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware

hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```

---

### Post by angel12 on 2010-10-21
> **LowSky said:**
> try it my way it will work

```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware

hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```

same thing happens. it shouldnt matter that im on 64bit right?

Edit: looks like its because i am on a 2.6.35 kernel:  [http://www.spinics.net/lists/linux-media/msg22089.html](http://www.spinics.net/lists/linux-media/msg22089.html)

---

### Post by dnobes on 2010-10-21
This is a known problem with the 2.6.35 kernel...  There will have to be a patch for the driver in order to work with this kernel...  Report it to the developer Steven Toth...  But you should be able to fix it pretty easily...  the usb_buffer_free and usb_buffer_alloc methods were renamed...

---

### Post by angel12 on 2010-10-21
> **dnobes said:**
> This is a known problem with the 2.6.35 kernel...  There will have to be a patch for the driver in order to work with this kernel...  Report it to the developer Steven Toth...  But you should be able to fix it pretty easily...  the usb_buffer_free and usb_buffer_alloc methods were renamed...

Im somewhat a noob when it comes to this, what exactly should i have to do to fix it?

---

### Post by dnobes on 2010-10-21
Two ways to fix it...

1)Find a header file that is inccluded in all the files that use either "usb_buffer_alloc" or "usb_buffer_free" and add:
#define usb_alloc_coherent(a, b, c, d) usb_buffer_alloc(a, b, c, d)
#define usb_free_coherent(a, b, c, d) usb_buffer_free(a, b, c, d)

2)Go to each file that uses them and add it at the top of each one...
Just look for them using "grep -r <looking for here> *" from the root directory.

---

### Post by jdk82 on 2010-10-23
Hi all,

Just wanted to report that I followed LowSky's guide from post #42 and I now have analogue working on both of the 2250's inputs! It's not perfect, the audio is very loud and I see a flash of blue when changing channels / inputs, but it is definitely better than nothing! One more note for anyone still having trouble, I had to delete all of my existing tuners from the backend and then add the 2250's tuner BEFORE adding my other card in order to get both of the 2250's tuners working. I'm going to look for ways to normalize the audio volume, but if anyone has any suggestions please chime in.

Edit: 

Okay, I spoke a little to soon. Live tv works okay but recordings are messed up. A 1/2 hour recording shows up as 8 minutes or so in length. The entire program is there but the total time is very wrong, and trying to skip forward by 30 seconds results in actually skipping forward several minutes. My dmesg is full of this:

```
[87529.087639] No pack at 0x0
[87529.087642] No pack at 0x800
[87529.087644] No pack at 0x1000
[87529.087647] No pack at 0x1800
[87529.087649] No pack at 0x2000
[87529.087652] No pack at 0x2800
[87529.087655] No pack at 0x3000
[87529.087657] No pack at 0x3800
[87529.087660] No pack at 0x4000
[87529.087662] No pack at 0x4800
[87529.087665] No pack at 0x5000
[87529.087667] No pack at 0x5800
[87529.087670] No pack at 0x6000
[87529.087672] No pack at 0x6800
[87529.087675] No pack at 0x7000
[87529.087677] No pack at 0x7800
```

This repeats consistently as long as either 2250 tuner is active. If I pause a currently recording program and watch the total time, it increments by 1 second every 3 or 4 instead of every second.I have also posted my issue here:

[http://www.kernellabs.com/blog/?p=1449&cpage=1#comment-1874](http://www.kernellabs.com/blog/?p=1449&cpage=1#comment-1874)

I will post to this thread if I figure anything out.

---

### Post by RadicalGeek on 2010-10-24
I followed LowSky's instructions but it doesn't see the driver at the backend.
Did a dmesg and got the following output.

[    9.908435] saa7164 driver loaded
[    9.908475] saa7164 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.909233] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[    9.909238] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfe400000
[    9.909243] saa7164 0000:02:00.0: setting latency timer to 64
[   10.076724] saa7164_downloadfirmware() no first image
[   10.076762] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   10.103198] saa7164_downloadfirmware() Upload failed. (file not found?)

Looks like the firmware didn't load right.

How can I correct this?

Radical Geek

---

### Post by jdk82 on 2010-10-24
Hi RadicalGeek,

It's looking for the wrong firmware, which would indicate that the driver did not build / install properly. Try following LowSky's instructions again and pay carefull attention to the output following the command

```
make CONFIG_DVB_FIREDTV:=n
```

If it works properly you'll see a lot modules being built. It took about 10 minutes on my machine. It may be a good idea to capture the output of that command so you can post it here if it still doesn't work.

---

### Post by LowSky on 2010-10-24
saa7164-1.0.3.fw is for using the digital tuner, not analog, and even so it isn't install correctly.

---

### Post by myrlin16 on 2010-10-24
> **dnobes said:**
> 
To setup an analogue tuner all you need to do is in the MythTV backend setup of the Capture Card. When setting the card type as “IVTV MPEG-2 Encoder” the PVR-2250 card does not show-up/auto-fill. So just manually set the "Video Device" to "/dev/video1".  This is assuming you setup the digital card already, otherwise you can set it to "/dev/video0", BUT if you do, then make sure that if you setup a digital tuner it does not use the first tuner..

Thanks DNOBES!!  I finally got around to trying this out and I now have analog working on my HVR2250 with myth.  I set mine up just using the analog inputs without any digital... that works better with my setup since I only get a few digital channels anyways.

Still one small problem though:

[QUOTE=jdk82]Live tv works okay but recordings are messed up. A 1/2 hour recording shows up as 8 minutes or so in length. The entire program is there but the total time is very wrong, and trying to skip forward by 30 seconds results in actually skipping forward several minutes.[/QUOTE]

I'm having this exact same problem.  For every 3-4 seconds of actual video, myth reports 1 second of video.  This could make things interesting when I try to transcode the video.  I'll report back here if I can figure this out.

Thanks again dnobes!!

---

### Post by jdk82 on 2010-10-24
Hi myrlin16,

Can you check dmesg and verify that you have messages similar to mine:

```
[105500.087041] No pack at 0x0
[105500.087043] No pack at 0x800
[105500.087045] No pack at 0x1000
[105500.087047] No pack at 0x1800
[105500.087049] No pack at 0x2000
[105500.087051] No pack at 0x2800
[105500.087053] No pack at 0x3000
[105500.087054] No pack at 0x3800
[105500.087056] No pack at 0x4000
[105500.087058] No pack at 0x4800
[105500.087060] No pack at 0x5000
[105500.087062] No pack at 0x5800
[105500.087064] No pack at 0x6000
[105500.087066] No pack at 0x6800
[105500.087068] No pack at 0x7000
[105500.087070] No pack at 0x7800
```

---

### Post by myrlin16 on 2010-10-24
jdk82,

> **jdk82 said:**
> Hi myrlin16,

Can you check dmesg and verify that you have messages similar to mine:


Exactly the same.

I found a reference to these messages in a comment here: 
   [http://www.kernellabs.com/blog/?p=1443](http://www.kernellabs.com/blog/?p=1443)

"Jeff" asks a question on september 9th and Steven's answer is the following:

> Known issue with the encoder, which is why the checks were added initially.

Try TS instead of PS, you may be happier.

I have no idea what he means by "TS instead of PS" as these acronyms weren't mentioned in the original comment.  I've been trying to figure it out as it may help our problem.

Let me know if you find anything, I can't work on it anymore tonight unfortunately.

---

### Post by jdk82 on 2010-10-24
myrlin16,

PS / TS are recording format? options that you can change in the recording profiles menu. I haven't had a chance to try changing them today as the tuner has been busy and, judging from comments I've read, it isn't likely to make a difference. If you get any results please post back, I'll do the same.

---

### Post by myrlin16 on 2010-10-24
> **jdk82 said:**
> 
PS / TS are recording format? options that you can change in the recording profiles menu. I haven't had a chance to try changing them today as the tuner has been busy and, judging from comments I've read, it isn't likely to make a difference. If you get any results please post back, I'll do the same.

Well, I convinced the wife to let me play around a little more tonight while she watches a different TV. :-)  So, here is what I tried...

I went into the following menu:
   Utilities Setup->Setup->TV Settings->Recording Profiles

I had the following profiles:
   MPEG-2 Encoders (PVR-x50, PVR-500)
   Transcode

I selected the "MPEG-2" option and was presented with several sub-profiles.  I selected each and changed the stream type from "MPEG-2 PS" to "MPEG-2 TS".  

Long story short this was a non-starter for me.  When I go back to "Watch TV" I get a black screen with the word "Please Wait...." and after a short while it goes back to the main menu.  I tried several different options in the profiles: created new profile, created new sub profile, tried editing only "Live TV", etc.  All results where the same.

I have a PVR-150 in the same box that also uses the IVTV card options.  Maybe this is giving me problems? When I create a new profile it seems the profile is active for all IVTV type of cards there doesn't seem to be a way to setup options for the HVR2250 and have different options for the PVR150 since they are both IVTV card types.  In any event I don't think the PVR150 is my problem since I was attempting to watch tv using the HVR2250 analog input.  Does anybody else have better luck changing the stream type to "TS"?

Sorry, that's all a bit confusing, but then so are the recording profiles.

---

### Post by myrlin16 on 2010-10-26
Okay, so I have made some progress.  I was unable to change the stream type to TS over PS, but after a little searching I found this comment on another forum:

> 
>I am given the choice between MPEG2-PS or MPEG2-TS 
>(along with some others I clearly don't want) in 
>"Recording Profiles". 
> 
>Which should I choose and why? 
> 
 
Neither. Choose DVD Special II. That's the stream type used by Windows MCE and is therefore getting the most testing. 


With this in mind I went into the recording profiles and changed the stream type from PS to "DVD-Special 2".  It works... sort of.  I no longer get the "No pack at 0x???" errors.  However I do still have issues with the recording length.  For every 3-4 seconds of recorded video I only get 1 second reported by myth.

In addition to the time issues I also cannot fast forward Live TV when watching these inputs.  Fast forward and Rewind are also very much broke when watching something recorded with the time shrink issue.

For now I have my system setup to always prefer my pvr150 and default to that when watching liveTV.  This will work for now with an annoyance periodically when it either records something with the HVR2250 with a time shrink or we're forced to watch the HVR2250 for LiveTV and can't fast forward properly.

Hopefully this will help somebody figure out the time issues.  I'll report back if I see the "No pack at 0x???" messages again... for now they appear to be gone! :-)

---

### Post by myrlin16 on 2010-10-27
Well... 22hrs later and the "No pack at 0x???" is back.  Looks like switching to DVD-Special 2 did nothing for me. :-(  Sorry for sending anybody down that path.  

I'll see if I can get TS working this weekend.

---

### Post by NightStorm on 2010-10-29
> **dnobes said:**
> Two ways to fix it...

1)Find a header file that is inccluded in all the files that use either "usb_buffer_alloc" or "usb_buffer_free" and add:
#define usb_alloc_coherent(a, b, c, d) usb_buffer_alloc(a, b, c, d)
#define usb_free_coherent(a, b, c, d) usb_buffer_free(a, b, c, d)

2)Go to each file that uses them and add it at the top of each one...
Just look for them using "grep -r <looking for here> *" from the root directory.

I think that it probably has more problems than just that.  I used a quickie (and dirty) command line script to fix-up the files, ala :
mkdir -p ~/tmp;for f in $(egrep -l 'usb_buffer_alloc|usb_buffer_free' $(find . -name '*.c'));do sed 's/usb_buffer_alloc/usb_alloc_coherent/g' < $f > ~/tmp/x.txt;sed 's/usb_buffer_free/usb_free_coherent/g' < ~/tmp/x.txt > $f;echo $f done;done

That gets it a bit further along, but it still errors out:

make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/moi/Downloads/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/moi/Downloads/saa7164-v4l/v4l/dvb_net.o
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c:1190: warning: 'struct dev_mc_list' declared inside parameter list
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c:1190: warning: its scope is only this definition or declaration, which is probably not what you want
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c: In function 'dvb_set_mc_filter':
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c:1197: error: dereferencing pointer to incomplete type
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c: In function 'wq_set_multicast_list':
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c:1247: error: 'struct net_device' has no member named 'mc_list'
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c:1249: error: dereferencing pointer to incomplete type
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c:1249: warning: left-hand operand of comma expression has no effect
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c:1249: warning: value computed is not used
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c:1250: warning: passing argument 2 of 'dvb_set_mc_filter' from incompatible pointer type
/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.c:1190: note: expected 'struct dev_mc_list *' but argument is of type 'struct dev_mc_list *'
make[3]: *** [/home/moi/Downloads/saa7164-v4l/v4l/dvb_net.o] Error 1
make[2]: *** [_module_/home/moi/Downloads/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/moi/Downloads/saa7164-v4l/v4l'

---

### Post by RadicalGeek on 2010-11-14
I have 10.10 and have problems installing the analog drivers.  When I run, make CONFIG_DVB_FIREDTV:=n, I get the following output.

make -C /home/bill/saa7164-v4l/v4l 
make[1]: Entering directory `/home/bill/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/bill/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/bill/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/bill/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/bill/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-22-generic-pae/build
make -C /lib/modules/2.6.35-22-generic-pae/build SUBDIRS=/home/bill/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
  CC [M]  /home/bill/saa7164-v4l/v4l/au0828-video.o
/home/bill/saa7164-v4l/v4l/au0828-video.c: In function 'au0828_uninit_isoc':
/home/bill/saa7164-v4l/v4l/au0828-video.c:185: error: implicit declaration of function 'usb_buffer_free'
/home/bill/saa7164-v4l/v4l/au0828-video.c: In function 'au0828_init_isoc':
/home/bill/saa7164-v4l/v4l/au0828-video.c:255: error: implicit declaration of function 'usb_buffer_alloc'
/home/bill/saa7164-v4l/v4l/au0828-video.c:256: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/bill/saa7164-v4l/v4l/au0828-video.o] Error 1
make[2]: *** [_module_/home/bill/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/bill/saa7164-v4l/v4l'
make: *** [all] Error 2

What needs to be corrected?

---

### Post by jdk82 on 2010-11-14
Hi RadicalGeek,

You need to re-read page 5 of this thread, angel12 posted the exact same problem. It is because of the kernel version you're running. A fix was proposed by dnobes, but angel12 never posted success/failure. Maybe you could try it and let us know the results?

EDIT: Never mind, the post directly above yours is about your issue and basically says that it didn't completely fix the issue.

---

### Post by myrlin16 on 2010-11-17
I finally had a chance to update to myth 0.24.  I left my distro at mythbuntu 10.04 because of issues others on this list have had with compiling the hvr2250 driver with the latest kernel.

The net upshot is that the time sync problems seem to be resolved.  With the HVR-2250 analog inputs I am now able to record and have the recorded file list the correct time.  Fast forward and rewind is working without jumping around erratically.

I still have the 'No Pack at 0x????' errors in "/var/log/syslog".  These are annoying, but they don't appear to be causing a problem at the moment.

Note: I still have my stream type set to DVD Special II.  If you update to 0.24 and don't have the same results with the time stretch you might try changing the stream type in your recording profiles.

Note2: I did not recompile the driver, all I did was install the mythbuntu-repos package from [here]("http://mythbuntu.org/auto-builds") and select 0.24 as my version.  I then ran update-manager and ran the updates.

I'll report back if I have any issues.  If this continues to work I may venture into testing whether or not 0.24 fixes the issue with switching between analog and digital.

---

### Post by jdk82 on 2010-11-18
Hi all,

I've stumbled across a fix that does not involve updating mythtv. If you run mythcommflag and tell it to rebuild the time index it will fix the recordings! Here is a step by step guide:

1) Run mythtv-setup
2) Under the "General" menu, goto the "Job Queue (Job Commands)" page
3) Under a user job, enter a User Job Description
4) For the same User Job, enter the following command
```
mythcommflag --rebuild --file %FILE%
```
5) Exit mythtv-setup
6) Either make this script run for every recording, (I haven't found a way to make it run only for recordings from the 2250) or manually run it after the recording is finished.

This will rebuild the time index stored in mythbackend's database and fix both the recording length problem and the ff/rw issues.

Hope this helps someone.

---

### Post by dnobes on 2010-11-23
Has anyone found any info on compiling with the new kernel?  My previously proposed fix only worked for the first few of what I imagine to be a long list of incompatibilities...

---

### Post by slideman on 2010-11-23
Hi all,

I have just gotten started on using my 2250.  I have been using it to capture digital up to now, but I would like to connect the svideo output of my set top box to the card so I can capture some of the non-clear-QAM stuff decoded by the box.

My take on what I have read here is that this is possible, and to get there quickest, I should wget the Steven Toth software and follow the instructions for it.  If I update to the most recent version of mythtv or use the mythcommflag trick, I should not see timing issues.  

I further assume that I can do BOTH analog (specifically svid) capture as well as digital in the same box.  I just put the firmware for the analog and the video together in the correct location and it works.

Do I have this right?

Is there anything else I ought to know?  

(Also, I should confess that I am using mythdora because I am more familiar with fedora from work, so if there is anything special about the mythbuntu version that makes the use of svideo possible, please let me know.)

Thanks!

---

### Post by slideman on 2010-11-30
dnobes,

As far as compiling with the new kernel, I have been thinking about doing that myself.
I have not had time to do it yet, (will probably  have to wait until after Christmas) but my approach would be to get the current version of v4l from the git repository, and then merge changes between that and the code you have.

I think you can get the new v4l stuff by following the instructions at [http://linuxtv.org/repo/](http://linuxtv.org/repo/)

Looking at the code, it seems to have usb_free_coherent calls, as well as usb_free_urb calls.

The best way to do the merge would be to do a 3-way diff between the code that Steven Toth based his code on, his modified code, and the current v4l code.  

Does anyone know what version of the code Steven Toth based his code on?

---

### Post by dreww_1972 on 2010-12-10
Important comment in Steve Toth's development blog:
"Steven,
 Got things working with analog in Mythtv (Mythdora). Used Erol instructions above from Aug 6 post.
 The only thing that was a little screwy was in the MythTV backend  setup of the Capture Card. When setting the card type as &#8220;IVTV MPEG-2  Encoder&#8221; the PVR-2250 card did not show up when I scrolled through the  Video Devices. However, if I manually set the Video Device to  /dev/video# the card showed up and everything went fine."
--Credit to Robert Pollack I am simply re-posting it for folks here. Took me 1/2 day to get my card up and running to satisfaction. YIKES

So, to be clear, you can get the NTSC ("analog") tuner to function with mythtv by initializing the tuner as an "IVTV MPEG-2 Encoder" defined for /dev/video0 and /dev/video1. Then go on to define the video source (basic cable), inputs, scan, fetch, mythfilldatabase, etc.

I have deleted all the Digital ATSC tuners (QAM and ATSC) for now. I'll enable them in a bit.

I am using the latest driver from [http://kernellabs.com/hg/~stoth/saa7164-v4l]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l") (CRC value [8da3bd06a289]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l/rev/8da3bd06a289")).

Latest firmwares
[http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/)
[http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/](http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/)

And compiled the driver without firedtv as indicated previously when making this module.

Hope this helps.

---

### Post by navodeo on 2010-12-15
Could someone please give me some idea what is wrong with my installation.  I've reinstalled Mythbuntu 10.04 64 bit, didn't upgrade to MythTV 0.24.  I let the system download the multitude of updates then used the instructions below exactly.  Did not receive any error msgs and dmesg shows the firmware loads. 

I have tried setting up the card as V4L MPEG & IVTV as described and it appears to be setting up.  I go through the follow-on sections until I get to channel scan where I get ZERO anything!  I know I have a signal but the channel strength shows 0 if that actually means anything.  Have used the try-all options everywhere and still no channels.

Could it be the card is bad?  I tried to use the v4l-ctl & mplayer mentioned elsewhere but just get a blue screen and static.  I am new to this so maybe it is a something really stupid but I just can't get anywhere.

Please any suggestions!! I have read everything I can find and just can't get it to work.  Help!!!!


> **LowSky said:**
> try it my way it will work

```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware

hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```

---

### Post by dnobes on 2010-12-16
It's a result of the kernel updates...  I can't remember which revision of the kernel it stopped working with, but I am pretty confident that is it...  I am going to look further into the problem in the next couple weeks, but for now it is just a likely theory...

---

### Post by RadicalGeek on 2010-12-19
I've setup the card in the back end but I still can't watch TV.  I go to Watch TV and then it just says Please Wait... then goes back to the front end.  Is there some setting that needs to be changed for it to work?

Radical Geek

---

### Post by navodeo on 2011-01-05
> **dnobes said:**
> It's a result of the kernel updates... I can't remember which revision of the kernel it stopped working with, but I am pretty confident that is it... I am going to look further into the problem in the next couple weeks, but for now it is just a likely theory...
 
Was this in response to my plea? If so do you have any suggestions or need other info from me?
 
Thanks.

---

### Post by newbuntu81 on 2011-02-06
> **RadicalGeek said:**
> I've setup the card in the back end but I still can't watch TV.  I go to Watch TV and then it just says Please Wait... then goes back to the front end.  Is there some setting that needs to be changed for it to work?

Radical Geek


Hi All,

I'm new to Ubuntu, using Mythbuntu 10.10 with Mythtv 0.24.

I am trying to set up my Haupaugge PVR-2250's dual ports to analog.  I got it working in ATSC (over the air mode) but cannot seem to get it working in Analog mode.  Can someone point me to a specific post?  I know that new drivers have been posted on steventoth.net and I am using the latest.


dmesg | grep saa
[   22.840810] saa7164 driver loaded
[   22.840889] saa7164 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.843643] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   22.843660] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xdf400000
[   22.843671] saa7164 0000:03:00.0: setting latency timer to 64
[   23.040535] saa7164_downloadfirmware() no first image
[   23.040593] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   23.128567] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   23.128573] saa7164_downloadfirmware() firmware loaded.
[   23.128595] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   23.128604] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   23.128608] saa7164_downloadfirmware() BSLSize = 0x0
[   23.128612] saa7164_downloadfirmware() Reserved = 0x0
[   23.128616] saa7164_downloadfirmware() Version = 0x51cc1
[   29.992041] saa7164_downloadimage() Image downloaded, booting...
[   30.097647] saa7164_downloadimage() Image booted successfully.
[   32.244774] saa7164_downloadimage() Image downloaded, booting...
[   33.908020] saa7164_downloadimage() Image booted successfully.
[   33.944709] saa7164[0]: Hauppauge eeprom: model=88061
[   34.532840] DVB: registering new adapter (saa7164)
[   37.620453] DVB: registering new adapter (saa7164)

Can anyone help me out?  

By the way, has anyone figured out a workaround for the "Please wait..." which takes you back to the frontend?

Thanks,
New Ubuntu 81 (Newbuntu81)

---

### Post by newbuntu81 on 2011-02-07
> **newbuntu81 said:**
> Hi All,

I'm new to Ubuntu, using Mythbuntu 10.10 with Mythtv 0.24.

I am trying to set up my Haupaugge PVR-2250's dual ports to analog.  I got it working in ATSC (over the air mode) but cannot seem to get it working in Analog mode.  Can someone point me to a specific post?  I know that new drivers have been posted on steventoth.net and I am using the latest.


dmesg | grep saa
[   22.840810] saa7164 driver loaded
[   22.840889] saa7164 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.843643] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   22.843660] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xdf400000
[   22.843671] saa7164 0000:03:00.0: setting latency timer to 64
[   23.040535] saa7164_downloadfirmware() no first image
[   23.040593] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   23.128567] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   23.128573] saa7164_downloadfirmware() firmware loaded.
[   23.128595] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   23.128604] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   23.128608] saa7164_downloadfirmware() BSLSize = 0x0
[   23.128612] saa7164_downloadfirmware() Reserved = 0x0
[   23.128616] saa7164_downloadfirmware() Version = 0x51cc1
[   29.992041] saa7164_downloadimage() Image downloaded, booting...
[   30.097647] saa7164_downloadimage() Image booted successfully.
[   32.244774] saa7164_downloadimage() Image downloaded, booting...
[   33.908020] saa7164_downloadimage() Image booted successfully.
[   33.944709] saa7164[0]: Hauppauge eeprom: model=88061
[   34.532840] DVB: registering new adapter (saa7164)
[   37.620453] DVB: registering new adapter (saa7164)

Can anyone help me out?  

By the way, has anyone figured out a workaround for the "Please wait..." which takes you back to the frontend?

Thanks,
New Ubuntu 81 (Newbuntu81)

--------------------------------------------------------------------------------------------------

Ok I figured out how to get rid of the "Please wait..." and it taking you back to the frontend.

Apparently Mythbuntu 10.10 ships with MythTV 0.24 (26437), Kernel 2.6.35, LibAPI 0.23.1.xxxx, and Branches 0.23 fixes.

I was told in an IRC chat that I needed to update the LibAPI to 0.24 and did so and it fixed that problem.

_**Instructions:**_

Allowing Updates: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

or command line:
sudo dpkg-reconfigure mythbuntu-repos
choose  PPA

Then go run Update Manager again and install updates.

_**Mythbuntu 10.10 as Installed:**_
MythTV Version   : 26437
MythTV Branch    :  branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.7.0

_**Mythbuntu 10.10 after Updates**_:
MythTV Version   : v0.24-151-g1a69c92
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0


_**My Issues**_
Now I just have to figure out how to get my 2250 tuners working in analog mode with the other firmware.  I keep erroring out on installation.

**I'm following these instructions per a previous poster**:
wget [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware

hg clone [http://kernellabs.com/hg/~stoth/saa7164-v4l]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l")
cd saa7164-v4l
sudo make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot

**Log:**
2011-02-07 19:18:50 (81.2 KB/s) - `NXP7164-2010-03-10.1.fw.2' saved [4019072/4019072]

michael@michael-OptiPlex-GX280:~$ sudo cp NXP7164-2010-03-10.1.fw /lib/firmware
michael@michael-OptiPlex-GX280:~$ sudo hg clone [http://kernellabs.com/hg/~stoth/saa7164-v4l]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l")
destination directory: saa7164-v4l
abort: destination 'saa7164-v4l' is not empty
michael@michael-OptiPlex-GX280:~$ cd saa7164-v4l
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-video.o
/home/michael/saa7164-v4l/v4l/au0828-video.c: In function 'au0828_uninit_isoc':
/home/michael/saa7164-v4l/v4l/au0828-video.c:185: error: implicit declaration of function 'usb_buffer_free'
/home/michael/saa7164-v4l/v4l/au0828-video.c: In function 'au0828_init_isoc':
/home/michael/saa7164-v4l/v4l/au0828-video.c:255: error: implicit declaration of function 'usb_buffer_alloc'
/home/michael/saa7164-v4l/v4l/au0828-video.c:256: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/michael/saa7164-v4l/v4l/au0828-video.o] Error 1
make[2]: *** [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2

[B]
My issues seem to be with:
[/B]1. /home/michael/saa7164-v4l/v4l/au0828-video.c:185: error: implicit declaration of function 'usb_buffer_free'

2. /home/michael/saa7164-v4l/v4l/au0828-video.c:255: error: implicit declaration of function 'usb_buffer_alloc'

I will do some research on those and see what I come up with.  Any tips would be greatly appreciated.

Thanks.

---

### Post by newbuntu81 on 2011-02-08
> **newbuntu81 said:**
> --------------------------------------------------------------------------------------------------

Ok I figured out how to get rid of the "Please wait..." and it taking you back to the frontend.

Apparently Mythbuntu 10.10 ships with MythTV 0.24 (26437), Kernel 2.6.35, LibAPI 0.23.1.xxxx, and Branches 0.23 fixes.

I was told in an IRC chat that I needed to update the LibAPI to 0.24 and did so and it fixed that problem.

_**Instructions:**_

Allowing Updates: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

or command line:
sudo dpkg-reconfigure mythbuntu-repos
choose  PPA

Then go run Update Manager again and install updates.

_**Mythbuntu 10.10 as Installed:**_
MythTV Version   : 26437
MythTV Branch    :  branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.7.0

_**Mythbuntu 10.10 after Updates**_:
MythTV Version   : v0.24-151-g1a69c92
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0


_**My Issues**_
Now I just have to figure out how to get my 2250 tuners working in analog mode with the other firmware.  I keep erroring out on installation.

**I'm following these instructions per a previous poster**:
wget [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware

hg clone [http://kernellabs.com/hg/~stoth/saa7164-v4l]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l")
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot

**Log:**
2011-02-07 19:18:50 (81.2 KB/s) - `NXP7164-2010-03-10.1.fw.2' saved [4019072/4019072]

michael@michael-OptiPlex-GX280:~$ sudo cp NXP7164-2010-03-10.1.fw /lib/firmware
michael@michael-OptiPlex-GX280:~$ sudo hg clone [http://kernellabs.com/hg/~stoth/saa7164-v4l]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l")
destination directory: saa7164-v4l
abort: destination 'saa7164-v4l' is not empty
michael@michael-OptiPlex-GX280:~$ cd saa7164-v4l
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-video.o
/home/michael/saa7164-v4l/v4l/au0828-video.c: In function 'au0828_uninit_isoc':
/home/michael/saa7164-v4l/v4l/au0828-video.c:185: error: implicit declaration of function 'usb_buffer_free'
/home/michael/saa7164-v4l/v4l/au0828-video.c: In function 'au0828_init_isoc':
/home/michael/saa7164-v4l/v4l/au0828-video.c:255: error: implicit declaration of function 'usb_buffer_alloc'
/home/michael/saa7164-v4l/v4l/au0828-video.c:256: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/michael/saa7164-v4l/v4l/au0828-video.o] Error 1
make[2]: *** [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2

[B]
My issues seem to be with:
[/B]1. /home/michael/saa7164-v4l/v4l/au0828-video.c:185: error: implicit declaration of function 'usb_buffer_free'

2. /home/michael/saa7164-v4l/v4l/au0828-video.c:255: error: implicit declaration of function 'usb_buffer_alloc'

I will do some research on those and see what I come up with.  Any tips would be greatly appreciated.

Thanks.

--------------------------------------------------------------

_**My Progress:**_
First I installed a GUI based search tool called Catfish.
sudo apt-get install catfish

After installing catfish, I added the two below lines to the compat.h file found at /saa7164-v4l/v4l at the very top:

cd /saa7164-v4l/v4l
sudo gedit compat.h
#define usb_alloc_coherent(a, b, c, d) usb_buffer_alloc(a, b, c, d)
#define usb_free_coherent(a, b, c, d) usb_buffer_free(a, b, c, d)

Then jump up a level.
cd /home/michael/saa7164-v4l

And continue instructions to compile and install
sudo make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot


_**Here are my latest warning messages.**_

**Compiled**
michael@michael-OptiPlex-GX280:~/saa7164-v4l/v4l$ cd /home/michael/saa7164-v4l
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/tuner-xc2028.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tuner-simple.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tuner-types.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt20xx.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda8290.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tea5767.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tea5761.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda9887.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda827x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au8522_dig.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au8522_decoder.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-pci.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-usb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-fe-tuner.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-sram.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-eeprom.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-misc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-hw-filter.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-dma.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bttv-driver.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bttv-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bttv-if.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bttv-risc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bttv-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bttv-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bttv-gpio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bttv-input.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bttv-audio-hook.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cpia2_v4l.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cpia2_usb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cpia2_core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-alsa-main.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-alsa-pcm.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-driver.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-firmware.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-gpio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-queue.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-streams.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-fileops.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-ioctl.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-controls.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-mailbox.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-audio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-irq.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-av-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-av-audio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-av-firmware.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-av-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-scb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-io.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-audio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-core.o
/home/michael/saa7164-v4l/v4l/cx231xx-core.c: In function 'cx231xx_uninit_isoc':
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:702: error: implicit declaration of function 'usb_buffer_free'
/home/michael/saa7164-v4l/v4l/cx231xx-core.c: In function 'cx231xx_init_isoc':
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:793: error: implicit declaration of function 'usb_buffer_alloc'
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:794: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/michael/saa7164-v4l/v4l/cx231xx-core.o] Error 1
make[2]: *** [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2


**Installed**
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make install
make -C /home/michael/saa7164-v4l/v4l install
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.35-25-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.35-25-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.35-25-generic/kernel/drivers/media/common:

-e 
Removing obsolete files from /lib/modules/2.6.35-25-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.35-25-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.35-25-generic 
make -C firmware install
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'

---

### Post by newbuntu81 on 2011-02-08
[QUOTE=newbuntu81;10438525]--------------------------------------------------------------

_**My Progress:**_
I added the two below lines to the compat.h file found at /saa7164-v4l/v4l at the very top:

cd /saa7164-v4l/v4l
sudo gedit compat.h
#define usb_alloc_coherent(a, b, c, d) usb_buffer_alloc(a, b, c, d)
#define usb_free_coherent(a, b, c, d) usb_buffer_free(a, b, c, d)

Then edited these files, and replaced all instances of "usb_buffer_alloc" to "usb_alloc_coherent" and  all instances of "usb_buffer_free" to "usb_free_coherent".
Sudo gedit cx231xx-core.c
Sudo gedit au0828-video.c

Then jumped up a level.
cd /home/michael/saa7164-v4l

And continued instructions to compile and install
sudo make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot


_**Here are my latest warning messages.**_

**Compiled**: As you can see, a bunch of new driver/firmware files were created--that's some progress.

michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is  /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-core.o
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:34: warning: "usb_alloc_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:8: note: this is the location of the previous definition
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:35: warning: "usb_free_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:9: note: this is the location of the previous definition
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:34: warning: "usb_alloc_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:8: note: this is the location of the previous definition
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:35: warning: "usb_free_coherent"  redefined
/home/michael/saa7164-v4l/v4l/compat.h:9: note: this is the location of the previous definition
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-avcore.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-417.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-ioctl.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-ir.o
  CC [M]   /home/michael/saa7164-v4l/v4l/cx23885-input.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23888-ir.o
  CC [M]  /home/michael/saa7164-v4l/v4l/netup-init.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cimax2.o
  CC [M]  /home/michael/saa7164-v4l/v4l/netup-eeprom.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-f300.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx25840-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx25840-audio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx25840-firmware.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx25840-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-mpeg.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-cards.o
  CC [M]   /home/michael/saa7164-v4l/v4l/cx88-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-tvaudio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-dsp.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-input.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvbdev.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dmxdev.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_demux.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_filter.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_ca_en50221.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_frontend.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_net.o
/home/michael/saa7164-v4l/v4l/dvb_net.c:1190: warning: 'struct dev_mc_list' declared inside parameter list
/home/michael/saa7164-v4l/v4l/dvb_net.c:1190: warning: its scope is only this definition or  declaration, which is probably not what you want
/home/michael/saa7164-v4l/v4l/dvb_net.c: In function 'dvb_set_mc_filter':
/home/michael/saa7164-v4l/v4l/dvb_net.c:1197: error: dereferencing pointer to incomplete type
/home/michael/saa7164-v4l/v4l/dvb_net.c: In function 'wq_set_multicast_list':
/home/michael/saa7164-v4l/v4l/dvb_net.c:1247: error: 'struct net_device' has no member named 'mc_list'
/home/michael/saa7164-v4l/v4l/dvb_net.c:1249: error: dereferencing pointer to incomplete type
/home/michael/saa7164-v4l/v4l/dvb_net.c:1249: warning: left-hand operand of comma expression has no effect
/home/michael/saa7164-v4l/v4l/dvb_net.c:1249: warning: value computed is not used
/home/michael/saa7164-v4l/v4l/dvb_net.c:1250: warning: passing argument 2 of 'dvb_set_mc_filter' from incompatible pointer type
/home/michael/saa7164-v4l/v4l/dvb_net.c:1190: note: expected 'struct dev_mc_list *' but argument is of type 'struct dev_mc_list  *'
make[3]: *** [/home/michael/saa7164-v4l/v4l/dvb_net.o] Error 1
make[2]: *** [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2


_**Take #2 Process:**_
So then I decided to edit the dvb_net.c file as I did with the two files mentioned above.  I edited the below mentioned file, and replaced all instances of "usb_buffer_alloc" to "usb_alloc_coherent" and  all instances of "usb_buffer_free" to "usb_free_coherent".
 
Sudo gedit dvb_net.c

**_Log:_**
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory  `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_net.o
/home/michael/saa7164-v4l/v4l/dvb_net.c:1190: warning: 'struct dev_mc_list' declared inside parameter list
/home/michael/saa7164-v4l/v4l/dvb_net.c:1190:  warning: its scope is only this definition or declaration, which is  probably not what you want
/home/michael/saa7164-v4l/v4l/dvb_net.c: In function 'dvb_set_mc_filter':
/home/michael/saa7164-v4l/v4l/dvb_net.c:1197: error: dereferencing pointer to incomplete type
/home/michael/saa7164-v4l/v4l/dvb_net.c: In function 'wq_set_multicast_list':
/home/michael/saa7164-v4l/v4l/dvb_net.c:1247: error: 'struct net_device' has no member named 'mc_list'
/home/michael/saa7164-v4l/v4l/dvb_net.c:1249: error: dereferencing pointer to incomplete type
/home/michael/saa7164-v4l/v4l/dvb_net.c:1249: warning: left-hand operand of comma expression has no  effect
/home/michael/saa7164-v4l/v4l/dvb_net.c:1249: warning: value computed is not used
/home/michael/saa7164-v4l/v4l/dvb_net.c:1250: warning: passing argument 2 of 'dvb_set_mc_filter' from incompatible pointer type
/home/michael/saa7164-v4l/v4l/dvb_net.c:1190:  note: expected 'struct dev_mc_list *' but argument is of type 'struct  dev_mc_list *'
make[3]: *** [/home/michael/saa7164-v4l/v4l/dvb_net.o] Error 1
make[2]: *** [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2

---

### Post by newbuntu81 on 2011-02-08
[QUOTE=newbuntu81;10440736][QUOTE=newbuntu81;10438525]--------------------------------------------------------------

_**My Progress:**_
I was given an article from a friend, which has you install v4l-conf and the linux-source-2.6.35 dvb-core files.
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=10398468&postcount=358](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=10398468&postcount=358)

**Article Instructions which I have partially rewritten with great help from the above post.**
1. sudo apt-get install v4l-conf
2. For all files with implicit declaration of function 'usb_buffer_free', add the following to the top after the #includes.

#define usb_buffer_alloc(a, b, c, d) usb_alloc_coherent(a, b, c, d)
#define usb_buffer_free(a, b, c, d) usb_free_coherent(a, b, c, d)

3. Repeat step 2 until you no longer encounter the 'usb_buffer_free' errors.

4. You should now encounter the 'struct net_device' errors. Download the full linux-source-2.6.35, decompress it, and copy the following to the v4l directory.

sudo apt-get install linux-source-2.6.35 (Or use the Package Manager)

5. Now the hard part. You need to open the linux-source-2.6.35.tar.bz2 found at
 "/usr/src/linux-source-2.6.35/", THEN extract all *.h and *.c files from the linux-source-2.6.35.tar.bz2 files from the "/usr/src/linux-source-2.6.35/drivers/media/dvb/dvb-core/" folder TO your v4l folder (i.e. "/home/michael/saa7164-v4l/v4l"). 

Because I'm new at this, I ended opening the tar.bz2 file with Archive Manager (GUI), extracting those 19 files to a new folder on my desktop, then using the command line to sudo cp them to the correct folder.

sudo cp -r ~/Desktop/dvb-core/* /home/michael/saa7164-v4l/v4l/

I've heard you can also use a **man tar** command but I got what I needed anyway.


6. You may encounter more 'usb_buffer_free' errors, if so, repeat step 2 again until it goes away.

Then I changed directories and began compiling again.
cd /home/michael/saa7164-v4l

And continued instructions to compile and install
sudo make CONFIG_DVB_FIREDTV:=n


_**Here are my latest warning messages.**_

**Compiled**: As you can see, a bunch of new driver/firmware files were created--that's some progress.

michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
[sudo] password for michael: 
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/tuner-xc2028.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tuner-simple.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt20xx.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda8290.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tea5767.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tea5761.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda9887.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda827x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au0828-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au8522_dig.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au8522_decoder.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-pci.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-usb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-fe-tuner.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-sram.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-eeprom.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-misc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-hw-filter.o
  CC [M]  /home/michael/saa7164-v4l/v4l/flexcop-dma.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-alsa-main.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-alsa-pcm.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-driver.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-firmware.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-gpio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-queue.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-streams.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-fileops.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-ioctl.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-controls.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-mailbox.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-audio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-irq.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-av-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-av-audio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-av-firmware.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-av-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-scb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx18-io.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-audio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-core.o
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:34: warning: "usb_alloc_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:8: note: this is the location of the previous definition
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:35: warning: "usb_free_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:9: note: this is the location of the previous definition
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:34: warning: "usb_alloc_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:8: note: this is the location of the previous definition
/home/michael/saa7164-v4l/v4l/cx231xx-core.c:35: warning: "usb_free_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:9: note: this is the location of the previous definition
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-avcore.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-417.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-ioctl.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-ir.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-input.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23888-ir.o
  CC [M]  /home/michael/saa7164-v4l/v4l/netup-init.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cimax2.o
  CC [M]  /home/michael/saa7164-v4l/v4l/netup-eeprom.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx23885-f300.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-mpeg.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-tvaudio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-dsp.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-input.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvbdev.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dmxdev.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_demux.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_filter.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_ca_en50221.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_frontend.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_net.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_ringbuffer.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_math.o
  CC [M]  /home/michael/saa7164-v4l/v4l/av7110_hw.o
  CC [M]  /home/michael/saa7164-v4l/v4l/av7110_v4l.o
  CC [M]  /home/michael/saa7164-v4l/v4l/av7110_av.o
/home/michael/saa7164-v4l/v4l/av7110_av.c:1520: warning: initialization from incompatible pointer type
/home/michael/saa7164-v4l/v4l/av7110_av.c:1532: warning: initialization from incompatible pointer type
/home/michael/saa7164-v4l/v4l/av7110_av.c:1538: warning: initialization from incompatible pointer type
/home/michael/saa7164-v4l/v4l/av7110_av.c:1549: warning: initialization from incompatible pointer type
  CC [M]  /home/michael/saa7164-v4l/v4l/av7110_ca.o
/home/michael/saa7164-v4l/v4l/av7110_ca.c:353: warning: initialization from incompatible pointer type
/home/michael/saa7164-v4l/v4l/av7110_ca.c:364: warning: initialization from incompatible pointer type
  CC [M]  /home/michael/saa7164-v4l/v4l/av7110.o
/home/michael/saa7164-v4l/v4l/av7110.c:733: warning: initialization from incompatible pointer type
/home/michael/saa7164-v4l/v4l/av7110.c:743: warning: initialization from incompatible pointer type
  CC [M]  /home/michael/saa7164-v4l/v4l/av7110_ipack.o
  CC [M]  /home/michael/saa7164-v4l/v4l/av7110_ir.o
  CC [M]  /home/michael/saa7164-v4l/v4l/a800.o
  CC [M]  /home/michael/saa7164-v4l/v4l/af9005-remote.o
  CC [M]  /home/michael/saa7164-v4l/v4l/af9005.o
  CC [M]  /home/michael/saa7164-v4l/v4l/af9005-fe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/af9015.o
  CC [M]  /home/michael/saa7164-v4l/v4l/anysee.o
  CC [M]  /home/michael/saa7164-v4l/v4l/au6610.o
  CC [M]  /home/michael/saa7164-v4l/v4l/az6027.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ce6230.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cinergyT2-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cinergyT2-fe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cxusb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dib0700_core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dib0700_devices.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dibusb-common.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dibusb-mb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dibusb-mc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/digitv.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dtt200u.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dtt200u-fe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dtv5100.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dw2102.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ec168.o
  CC [M]  /home/michael/saa7164-v4l/v4l/friio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/friio-fe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/gl861.o
  CC [M]  /home/michael/saa7164-v4l/v4l/gp8psk.o
  CC [M]  /home/michael/saa7164-v4l/v4l/gp8psk-fe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/m920x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/nova-t-usb2.o
  CC [M]  /home/michael/saa7164-v4l/v4l/opera1.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ttusb2.o
  CC [M]  /home/michael/saa7164-v4l/v4l/umt-010.o
  CC [M]  /home/michael/saa7164-v4l/v4l/vp702x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/vp702x-fe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/vp7045.o
  CC [M]  /home/michael/saa7164-v4l/v4l/vp7045-fe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-firmware.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-init.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-urb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-remote.o
/home/michael/saa7164-v4l/v4l/dvb-usb-remote.c: In function 'dvb_usb_remote_init':
/home/michael/saa7164-v4l/v4l/dvb-usb-remote.c:195: warning: assignment from incompatible pointer type
/home/michael/saa7164-v4l/v4l/dvb-usb-remote.c:196: warning: assignment from incompatible pointer type
  CC [M]  /home/michael/saa7164-v4l/v4l/usb-urb.o
/home/michael/saa7164-v4l/v4l/usb-urb.c: In function 'usb_free_stream_buffers':
/home/michael/saa7164-v4l/v4l/usb-urb.c:103: error: implicit declaration of function 'usb_buffer_free'
/home/michael/saa7164-v4l/v4l/usb-urb.c: In function 'usb_allocate_stream_buffers':
/home/michael/saa7164-v4l/v4l/usb-urb.c:123: error: implicit declaration of function 'usb_buffer_alloc'
/home/michael/saa7164-v4l/v4l/usb-urb.c:124: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/michael/saa7164-v4l/v4l/usb-urb.o] Error 1
make[2]: *** [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2

---

### Post by newbuntu81 on 2011-02-08
[QUOTE=newbuntu81;10441098][QUOTE=newbuntu81;10440736][QUOTE=newbuntu81;10438525]--------------------------------------------------------------

**_Process:_**
I edited these files, and replaced all instances of  "usb_buffer_alloc" to "usb_alloc_coherent" and  all instances of  "usb_buffer_free" to "usb_free_coherent".

cd /saa7164-v4l/v4l
sudo gedit cx231xx-core.h
sudo gedit usb-urb.c
sudo gedit em28xx-core.c
sudo gedit benq.c
sudo gedit gspca.c
sudo gedit hdpvr-video.c
sudo gedit pd-video.c


Then jumped up a level.
cd /home/michael/saa7164-v4l

And continued instructions to compile and install
sudo make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot

**__**[U][B]
Here are my latest warning messages.[/B][/U]

**__**michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]   /home/michael/saa7164-v4l/v4l/pd-video.o
/home/michael/saa7164-v4l/v4l/pd-video.c:15: warning: "usb_alloc_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:8: note: this is the location of the previous definition
/home/michael/saa7164-v4l/v4l/pd-video.c:16: warning: "usb_free_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:9: note: this is the location of the previous definition
  CC [M]  /home/michael/saa7164-v4l/v4l/pd-alsa.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pd-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pd-radio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pd-main.o
/home/michael/saa7164-v4l/v4l/pd-main.c: In function 'poseidon_probe':
/home/michael/saa7164-v4l/v4l/pd-main.c:457: error: 'struct usb_device' has no member named 'autosuspend_disabled'
make[3]: *** [/home/michael/saa7164-v4l/v4l/pd-main.o] Error 1
make[2]: ***  [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2

---

### Post by newbuntu81 on 2011-02-08
[QUOTE=newbuntu81;10441346][QUOTE=newbuntu81;10441098][QUOTE=newbuntu81;10440736][QUOTE=newbuntu81;10438525]--------------------------------------------------------------

**_Process:_**
Next, I edited another file and replaced some text thanks to my friend's quick researching help.

cd /saa7164-v4l/v4l
sudo gedit pd-main.c

I searched for "pd->udev->autosuspend_disabled = 0;" at line 457 and deleted it, then replaced it with:
[SIZE=2][SIZE=2][COLOR=#000000][FONT=Arial][SIZE=2]
usb_enable_autosuspend(pd->udev); 

[/SIZE][/FONT][/COLOR][/SIZE][/SIZE]Then recompile
cd /home/michael/saa7164-v4l

And continued instructions to compile and install
sudo make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot

[U][B]
Here are my latest warning messages.[/B][/U]

michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/pd-main.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-i2c-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-audio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-encoder.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-video-v4l.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-eeprom.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-main.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-hdw.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-v4l2.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-ctrl.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-std.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-devattr.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-context.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-io.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-ioread.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-cx2584x-v4l.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-wm8775.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-cs53l32a.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-sysfs.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pvrusb2-debugifc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pwc-if.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pwc-misc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pwc-ctrl.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pwc-v4l.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pwc-uncompress.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pwc-dec1.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pwc-dec23.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pwc-kiara.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pwc-timon.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-si470x-usb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-si470x-common.o
  CC [M]  /home/michael/saa7164-v4l/v4l/s921_module.o
  CC [M]  /home/michael/saa7164-v4l/v4l/s921_core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-ts.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-tvaudio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-input.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7146_i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7146_core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7146_fops.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7146_video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7146_hlp.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7146_vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-fw.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-bus.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-cmd.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-api.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-buffer.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-encoder.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7164-vbi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/smscoreapi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sms-cards.o
  CC [M]  /home/michael/saa7164-v4l/v4l/smsendian.o
  CC [M]  /home/michael/saa7164-v4l/v4l/smsir.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_hv7131d.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_hv7131r.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_mi0343.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_mi0360.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_mt9v111.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_ov7630.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_ov7660.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_pas106b.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_pas202bcb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_tas5110c1b.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_tas5110d.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sn9c102_tas5130d1b.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bt87x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tea575x-tuner.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stb0899_drv.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stb0899_algo.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stk-webcam.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stk-sensor.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stv0900_core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stv0900_sw.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda18271-maps.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda18271-common.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda18271-fe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tuner-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/usbvision-core.o
/home/michael/saa7164-v4l/v4l/usbvision-core.c: In function 'usbvision_init_isoc':
/home/michael/saa7164-v4l/v4l/usbvision-core.c:2517: error: implicit declaration of function 'usb_buffer_alloc'
/home/michael/saa7164-v4l/v4l/usbvision-core.c:2520: warning: assignment makes pointer from integer without a cast
/home/michael/saa7164-v4l/v4l/usbvision-core.c: In function 'usbvision_stop_isoc':
/home/michael/saa7164-v4l/v4l/usbvision-core.c:2576: error: implicit declaration of function 'usb_buffer_free'
make[3]: *** [/home/michael/saa7164-v4l/v4l/usbvision-core.o] Error 1
make[2]: *** [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2

---

### Post by newbuntu81 on 2011-02-08
[QUOTE=newbuntu81;10441391][QUOTE=newbuntu81;10441346][QUOTE=newbuntu81;10441098][QUOTE=newbuntu81;10440736][QUOTE=newbuntu81;10438525]--------------------------------------------------------------

Hmmm, now I'm stumped.  It seems to want a semi colon but it has one.  I hate playing coding "Wheres Waldo".

**_Process:_**
I edited these files, and replaced all instances of  "usb_buffer_alloc"  to "usb_alloc_coherent" and  all instances of  "usb_buffer_free" to  "usb_free_coherent".

cd /saa7164-v4l/v4l
sudo gedit usbvision-core.c

Then recompile
cd /home/michael/saa7164-v4l

And continued instructions to compile and install
sudo make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot

[U][B]
Here are my latest warning messages.[/B][/U]
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/usbvision-core.o
/home/michael/saa7164-v4l/v4l/usbvision-core.c:48: warning: "usb_alloc_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:8: note: this is the location of the previous definition
/home/michael/saa7164-v4l/v4l/usbvision-core.c:49: warning: "usb_free_coherent" redefined
/home/michael/saa7164-v4l/v4l/compat.h:9: note: this is the location of the previous definition
/home/michael/saa7164-v4l/v4l/usbvision-core.c: In function 'usbvision_init_isoc':
/home/michael/saa7164-v4l/v4l/usbvision-core.c:2523: error: expected expression before ';' token
/home/michael/saa7164-v4l/v4l/usbvision-core.c: In function 'usbvision_stop_isoc':
/home/michael/saa7164-v4l/v4l/usbvision-core.c:2570: warning: unused variable 'sb_size'
make[3]: *** [/home/michael/saa7164-v4l/v4l/usbvision-core.o] Error 1
make[2]: *** [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2


_**Code:**_
So line 2523 in usbvision-core.c appears in bold, the lines before and after appear as:

usbvision->sbuf[bufIdx].urb = urb;
        usbvision->sbuf[bufIdx].data =
            usb_alloc_coherent(usbvision->dev,
                     sb_size,
                     GFP_KERNEL,
**                     &urb->transfer_dma);**
        urb->dev = dev;
        urb->context = usbvision;


_**The Fix:**_
Be sure to add this line at the top of the usbvision-core.c file.

#define usb_buffer_alloc(a, b, c, d) usb_alloc_coherent(a, b, c, d)
#define usb_buffer_free(a, b, c, d) usb_free_coherent(a, b, c, d)

---

### Post by newbuntu81 on 2011-02-09
[QUOTE=newbuntu81;10441487][QUOTE=newbuntu81;10441391][QUOTE=newbuntu81;10441346][QUOTE=newbuntu81;10441098][QUOTE=newbuntu81;10440736][QUOTE=newbuntu81;10438525]--------------------------------------------------------------

Ok, and this one "scored big"...look at all the .o's created in the output.  Getting closer!

**_Process:_**
I edited these files, and replaced all instances of  "usb_buffer_alloc"  to "usb_alloc_coherent" and  all instances of  "usb_buffer_free" to  "usb_free_coherent".

cd /saa7164-v4l/v4l
sudo gedit uvc_video.c

Then recompile
cd /home/michael/saa7164-v4l

And continued instructions to compile and install
sudo make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot

[U][B]
Here are my latest warning messages.[/B][/U]
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/uvc_video.o
  CC [M]  /home/michael/saa7164-v4l/v4l/uvc_ctrl.o
  CC [M]  /home/michael/saa7164-v4l/v4l/uvc_status.o
  CC [M]  /home/michael/saa7164-v4l/v4l/uvc_isight.o
  CC [M]  /home/michael/saa7164-v4l/v4l/v4l2-dev.o
  CC [M]  /home/michael/saa7164-v4l/v4l/v4l2-ioctl.o
  CC [M]  /home/michael/saa7164-v4l/v4l/v4l2-device.o
  CC [M]  /home/michael/saa7164-v4l/v4l/v4l2-fh.o
  CC [M]  /home/michael/saa7164-v4l/v4l/v4l2-event.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zc0301_core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zc0301_pb0330.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zc0301_pas202bcb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zoran_procfs.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zoran_device.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zoran_driver.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zoran_card.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda18271.o
  CC [M]  /home/michael/saa7164-v4l/v4l/xc5000.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt2060.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt2266.o
  CC [M]  /home/michael/saa7164-v4l/v4l/qt1010.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt2131.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mxl5005s.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mxl5007t.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mc44s803.o
  CC [M]  /home/michael/saa7164-v4l/v4l/max2165.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7146.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7146_vv.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-adstech-dvb-t-pci.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-apac-viewcomp.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-asus-pc39.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-ati-tv-wonder-hd-600.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-a16d.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-cardbus.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-dvbt.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-m135a.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-m733a-rm-k6.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-avertv-303.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-behold.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-behold-columbus.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-budget-ci-old.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-cinergy-1400.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-cinergy.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-dm1105-nec.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-dntv-live-dvb-t.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-dntv-live-dvbt-pro.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-empty.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-em-terratec.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-encore-enltv2.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-encore-enltv.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-encore-enltv-fm53.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-evga-indtube.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-eztv.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-flydvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-flyvideo.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-fusionhdtv-mce.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-gadmei-rm008z.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-genius-tvgo-a11mce.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-gotview7135.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-hauppauge-new.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-imon-mce.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-imon-pad.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-iodata-bctv7e.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-kaiomy.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-kworld-315u.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-kworld-plus-tv-analog.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-manli.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-msi-tvanywhere.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-msi-tvanywhere-plus.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-nebula.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-nec-terratec-cinergy-xs.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-norwood.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-npgtech.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-pctv-sedna.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-pinnacle-color.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-pinnacle-grey.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-pinnacle-pctv-hd.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-pixelview.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-pixelview-mk12.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-pixelview-new.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-powercolor-real-angel.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-proteus-2309.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-purpletv.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-pv951.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-rc5-hauppauge-new.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-rc5-tv.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-real-audio-220-32-keys.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-tbs-nec.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-terratec-cinergy-xs.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-tevii-nec.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-tt-1500.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-videomate-s350.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-videomate-tv-pvr.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-winfast.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rc-winfast-usbii-deluxe.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-core.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-common.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ir-nec-decoder.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ir-rc5-decoder.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ir-rc6-decoder.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ir-jvc-decoder.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ir-sony-decoder.o
  CC [M]  /home/michael/saa7164-v4l/v4l/imon.o
  LD [M]  /home/michael/saa7164-v4l/v4l/videodev.o
  CC [M]  /home/michael/saa7164-v4l/v4l/v4l2-int-device.o
  CC [M]  /home/michael/saa7164-v4l/v4l/v4l2-common.o
  CC [M]  /home/michael/saa7164-v4l/v4l/v4l1-compat.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tuner.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tvaudio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda7432.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda9875.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa6588.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa5246a.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa5249.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda9840.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tea6415c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tea6420.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7110.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7115.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa717x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7127.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7185.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7191.o
  CC [M]  /home/michael/saa7164-v4l/v4l/adv7170.o
  CC [M]  /home/michael/saa7164-v4l/v4l/adv7175.o
  CC [M]  /home/michael/saa7164-v4l/v4l/adv7180.o
  CC [M]  /home/michael/saa7164-v4l/v4l/adv7343.o
  CC [M]  /home/michael/saa7164-v4l/v4l/vpx3220.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bt819.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bt856.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bt866.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ks0127.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ths7303.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tvp5150.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tvp514x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tvp7002.o
  LD [M]  /home/michael/saa7164-v4l/v4l/msp3400.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cs5345.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cs53l32a.o
  CC [M]  /home/michael/saa7164-v4l/v4l/m52790.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tlv320aic23b.o
  CC [M]  /home/michael/saa7164-v4l/v4l/wm8775.o
  CC [M]  /home/michael/saa7164-v4l/v4l/wm8739.o
  CC [M]  /home/michael/saa7164-v4l/v4l/vp27smpx.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx25840.o
  CC [M]  /home/michael/saa7164-v4l/v4l/upd64031a.o
  CC [M]  /home/michael/saa7164-v4l/v4l/upd64083.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ov7670.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tcm825x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tveeprom.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt9v011.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt9m001.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt9m111.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt9t031.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt9t112.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt9v022.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ov772x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ov9640.o
  CC [M]  /home/michael/saa7164-v4l/v4l/rj54n1cb0c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tw9910.o
  LD [M]  /home/michael/saa7164-v4l/v4l/bttv.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zr36067.o
  CC [M]  /home/michael/saa7164-v4l/v4l/videocodec.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zr36050.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zr36016.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zr36060.o
  CC [M]  /home/michael/saa7164-v4l/v4l/c-qcam.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bw-qcam.o
  CC [M]  /home/michael/saa7164-v4l/v4l/w9966.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pms.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stradis.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cpia.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cpia_pp.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cpia_usb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/meye.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa6752hs.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7134.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-empress.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-alsa.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7134-dvb.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx88xx.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx8800.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx8802.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-alsa.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-blackbird.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx88-vp3054-i2c.o
  LD [M]  /home/michael/saa7164-v4l/v4l/em28xx.o
  LD [M]  /home/michael/saa7164-v4l/v4l/em28xx-alsa.o
  CC [M]  /home/michael/saa7164-v4l/v4l/em28xx-dvb.o
  LD [M]  /home/michael/saa7164-v4l/v4l/poseidon.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx231xx.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx231xx-alsa.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx231xx-dvb.o
  LD [M]  /home/michael/saa7164-v4l/v4l/usbvision.o
  LD [M]  /home/michael/saa7164-v4l/v4l/pvrusb2.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ovcamchip.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cpia2.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mxb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/hexium_orion.o
  CC [M]  /home/michael/saa7164-v4l/v4l/hexium_gemini.o
  CC [M]  /home/michael/saa7164-v4l/v4l/videobuf-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/videobuf-dma-sg.o
  CC [M]  /home/michael/saa7164-v4l/v4l/videobuf-dma-contig.o
  CC [M]  /home/michael/saa7164-v4l/v4l/videobuf-vmalloc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/videobuf-dvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/btcx-risc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/v4l2-mem2mem.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx2341x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cafe_ccic.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dabusb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ov511.o
  CC [M]  /home/michael/saa7164-v4l/v4l/se401.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stv680.o
  CC [M]  /home/michael/saa7164-v4l/v4l/w9968cf.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zr364xx.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stkwebcam.o
  LD [M]  /home/michael/saa7164-v4l/v4l/sn9c102.o
  LD [M]  /home/michael/saa7164-v4l/v4l/et61x251.o
  LD [M]  /home/michael/saa7164-v4l/v4l/pwc.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zc0301.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_main.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_benq.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_conex.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_cpia1.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_etoms.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_finepix.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_jeilinj.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_mars.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_mr97310a.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_ov519.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_ov534.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_ov534_9.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_pac207.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_pac7302.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_pac7311.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sn9c2028.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sn9c20x.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sonixb.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sonixj.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca500.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca501.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca505.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca506.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca508.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca561.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sq905.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sq905c.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sunplus.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_stk014.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_stv0680.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_t613.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_tv8532.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_vc032x.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_zc3xx.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_m5602.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_stv06xx.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_gl860.o
  LD [M]  /home/michael/saa7164-v4l/v4l/hdpvr.o
  CC [M]  /home/michael/saa7164-v4l/v4l/usbvideo.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ibmcam.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ultracam.o
  CC [M]  /home/michael/saa7164-v4l/v4l/konicawc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/vicam.o
  CC [M]  /home/michael/saa7164-v4l/v4l/quickcam_messenger.o
  CC [M]  /home/michael/saa7164-v4l/v4l/s2255drv.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ivtv.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ivtvfb.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx18.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx18-alsa.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mem2mem_testdev.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx23885.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ak881x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/soc_camera.o
  CC [M]  /home/michael/saa7164-v4l/v4l/soc_mediabus.o
  CC [M]  /home/michael/saa7164-v4l/v4l/soc_camera_platform.o
  LD [M]  /home/michael/saa7164-v4l/v4l/au0828.o
  LD [M]  /home/michael/saa7164-v4l/v4l/uvcvideo.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7164.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ir-kbd-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-aztech.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-rtrack2.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-sf16fmi.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-sf16fmr2.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-cadet.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-typhoon.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-terratec.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-maxiradio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-aimslab.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-zoltrix.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-gemtek.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-gemtek-pci.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-trust.o
  CC [M]  /home/michael/saa7164-v4l/v4l/si4713-i2c.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-si4713.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-maestro.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-miropcm20.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dsbr100.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-usb-si470x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-mr800.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-tea5764.o
  CC [M]  /home/michael/saa7164-v4l/v4l/saa7706h.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tef6862.o
  CC [M]  /home/michael/saa7164-v4l/v4l/radio-timb.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb-pll.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stv0299.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stb0899.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stb6100.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sp8870.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx22700.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx24110.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda8083.o
  CC [M]  /home/michael/saa7164-v4l/v4l/l64781.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dib3000mb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dib3000mc.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dibx000_common.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dib7000m.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dib7000p.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dib8000.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt312.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ves1820.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ves1x93.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda1004x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/sp887x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/nxt6000.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mt352.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zl10036.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zl10039.o
  CC [M]  /home/michael/saa7164-v4l/v4l/zl10353.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx22702.o
  CC [M]  /home/michael/saa7164-v4l/v4l/drx397xD.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda10021.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda10023.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stv0297.o
  CC [M]  /home/michael/saa7164-v4l/v4l/nxt200x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/or51211.o
  CC [M]  /home/michael/saa7164-v4l/v4l/or51132.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bcm3510.o
  CC [M]  /home/michael/saa7164-v4l/v4l/s5h1420.o
  CC [M]  /home/michael/saa7164-v4l/v4l/lgdt330x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/lgdt3304.o
  CC [M]  /home/michael/saa7164-v4l/v4l/lgdt3305.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx24123.o
  CC [M]  /home/michael/saa7164-v4l/v4l/lnbp21.o
  CC [M]  /home/michael/saa7164-v4l/v4l/isl6405.o
  CC [M]  /home/michael/saa7164-v4l/v4l/isl6421.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda10086.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda826x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda8261.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dib0070.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dib0090.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tua6100.o
  CC [M]  /home/michael/saa7164-v4l/v4l/s5h1409.o
  CC [M]  /home/michael/saa7164-v4l/v4l/itd1000.o
  LD [M]  /home/michael/saa7164-v4l/v4l/au8522.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda10048.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx24113.o
  CC [M]  /home/michael/saa7164-v4l/v4l/s5h1411.o
  CC [M]  /home/michael/saa7164-v4l/v4l/lgs8gl5.o
  CC [M]  /home/michael/saa7164-v4l/v4l/tda665x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/lgs8gxx.o
  CC [M]  /home/michael/saa7164-v4l/v4l/atbm8830.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb_dummy_fe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/af9013.o
  CC [M]  /home/michael/saa7164-v4l/v4l/cx24116.o
  CC [M]  /home/michael/saa7164-v4l/v4l/si21xx.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stv0288.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stb6000.o
  LD [M]  /home/michael/saa7164-v4l/v4l/s921.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stv6110.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stv0900.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stv090x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/stv6110x.o
  CC [M]  /home/michael/saa7164-v4l/v4l/isl6423.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ec100.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ds3000.o
  CC [M]  /home/michael/saa7164-v4l/v4l/mb86a16.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ttpci-eeprom.o
  CC [M]  /home/michael/saa7164-v4l/v4l/budget-core.o
  CC [M]  /home/michael/saa7164-v4l/v4l/budget.o
  CC [M]  /home/michael/saa7164-v4l/v4l/budget-av.o
  CC [M]  /home/michael/saa7164-v4l/v4l/budget-ci.o
  CC [M]  /home/michael/saa7164-v4l/v4l/budget-patch.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-ttpci.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ttusb_dec.o
/home/michael/saa7164-v4l/v4l/ttusb_dec.c: In function 'ttusb_dec_init_usb':
/home/michael/saa7164-v4l/v4l/ttusb_dec.c:1269: error: implicit declaration of function 'usb_buffer_alloc'
/home/michael/saa7164-v4l/v4l/ttusb_dec.c:1270: warning: assignment makes pointer from integer without a cast
/home/michael/saa7164-v4l/v4l/ttusb_dec.c: In function 'ttusb_dec_exit_rc':
/home/michael/saa7164-v4l/v4l/ttusb_dec.c:1562: error: implicit declaration of function 'usb_buffer_free'
make[3]: *** [/home/michael/saa7164-v4l/v4l/ttusb_dec.o] Error 1
make[2]: *** [_module_/home/michael/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
make: *** [all] Error 2

---

### Post by newbuntu81 on 2011-02-09
[QUOTE=newbuntu81;10441589][QUOTE=newbuntu81;10441487][QUOTE=newbuntu81;10441391][QUOTE=newbuntu81;10441346][QUOTE=newbuntu81;10441098][QUOTE=newbuntu81;10440736][QUOTE=newbuntu81;10438525]--------------------------------------------------------------

Ok, and this one "scored even bigger"...look at all the .o's created in the output.  Getting closer!

**_Process:_**
I edited these files, and replaced all instances of  "usb_buffer_alloc"  to "usb_alloc_coherent" and  all instances of  "usb_buffer_free" to  "usb_free_coherent".

cd /saa7164-v4l/v4l
sudo gedit ttusb_dec.c

Then recompile
cd /home/michael/saa7164-v4l

And continued instructions to compile and install
sudo make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot

[U][B]
Here are my latest warning messages.[/B][/U]
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make CONFIG_DVB_FIREDTV:=n
make -C /home/michael/saa7164-v4l/v4l 
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/michael/saa7164-v4l/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/michael/saa7164-v4l/v4l/ttusb_dec.o
  CC [M]  /home/michael/saa7164-v4l/v4l/ttusbdecfe.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb-ttusb-budget.o
  LD [M]  /home/michael/saa7164-v4l/v4l/b2c2-flexcop.o
  LD [M]  /home/michael/saa7164-v4l/v4l/b2c2-flexcop-pci.o
  LD [M]  /home/michael/saa7164-v4l/v4l/b2c2-flexcop-usb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/bt878.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dvb-bt8xx.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dst.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dst_ca.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-vp7045.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-vp702x.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-gp8psk.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dtt200u.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dibusb-common.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-a800.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dibusb-mb.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dibusb-mc.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-nova-t-usb2.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-umt-010.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-m920x.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-gl861.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-au6610.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-digitv.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-cxusb.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-ttusb2.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dib0700.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-opera.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-af9005.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-af9005-remote.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-anysee.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dw2102.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dtv5100.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-af9015.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-cinergyT2.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-ce6230.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-friio.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-ec168.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-az6027.o
  CC [M]  /home/michael/saa7164-v4l/v4l/pluto2.o
  LD [M]  /home/michael/saa7164-v4l/v4l/smsmdtv.o
  CC [M]  /home/michael/saa7164-v4l/v4l/smsdvb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/smsusb.o
  CC [M]  /home/michael/saa7164-v4l/v4l/smssdio.o
  CC [M]  /home/michael/saa7164-v4l/v4l/dm1105.o
  LD [M]  /home/michael/saa7164-v4l/v4l/earth-pt1.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mantis_core.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mantis.o
  LD [M]  /home/michael/saa7164-v4l/v4l/hopper.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ngene.o
  LD [M]  /home/michael/saa7164-v4l/v4l/snd-bt87x.o
  LD [M]  /home/michael/saa7164-v4l/v4l/snd-tea575x-tuner.o
  Building modules, stage 2.
  MODPOST 432 modules
WARNING: "usb_buffer_alloc" [/home/michael/saa7164-v4l/v4l/gspca_main.ko] undefined!
WARNING: "usb_buffer_free" [/home/michael/saa7164-v4l/v4l/gspca_main.ko] undefined!
WARNING: "usb_buffer_alloc" [/home/michael/saa7164-v4l/v4l/au0828.ko] undefined!
WARNING: "usb_buffer_free" [/home/michael/saa7164-v4l/v4l/au0828.ko] undefined!
  CC      /home/michael/saa7164-v4l/v4l/adv7170.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/adv7170.ko
  CC      /home/michael/saa7164-v4l/v4l/adv7175.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/adv7175.ko
  CC      /home/michael/saa7164-v4l/v4l/adv7180.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/adv7180.ko
  CC      /home/michael/saa7164-v4l/v4l/adv7343.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/adv7343.ko
  CC      /home/michael/saa7164-v4l/v4l/af9013.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/af9013.ko
  CC      /home/michael/saa7164-v4l/v4l/ak881x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ak881x.ko
  CC      /home/michael/saa7164-v4l/v4l/atbm8830.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/atbm8830.ko
  CC      /home/michael/saa7164-v4l/v4l/au0828.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/au0828.ko
  CC      /home/michael/saa7164-v4l/v4l/au8522.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/au8522.ko
  CC      /home/michael/saa7164-v4l/v4l/b2c2-flexcop-pci.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/b2c2-flexcop-pci.ko
  CC      /home/michael/saa7164-v4l/v4l/b2c2-flexcop-usb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/b2c2-flexcop-usb.ko
  CC      /home/michael/saa7164-v4l/v4l/b2c2-flexcop.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/b2c2-flexcop.ko
  CC      /home/michael/saa7164-v4l/v4l/bcm3510.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/bcm3510.ko
  CC      /home/michael/saa7164-v4l/v4l/bt819.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/bt819.ko
  CC      /home/michael/saa7164-v4l/v4l/bt856.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/bt856.ko
  CC      /home/michael/saa7164-v4l/v4l/bt866.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/bt866.ko
  CC      /home/michael/saa7164-v4l/v4l/bt878.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/bt878.ko
  CC      /home/michael/saa7164-v4l/v4l/btcx-risc.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/btcx-risc.ko
  CC      /home/michael/saa7164-v4l/v4l/bttv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/bttv.ko
  CC      /home/michael/saa7164-v4l/v4l/budget-av.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/budget-av.ko
  CC      /home/michael/saa7164-v4l/v4l/budget-ci.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/budget-ci.ko
  CC      /home/michael/saa7164-v4l/v4l/budget-core.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/budget-core.ko
  CC      /home/michael/saa7164-v4l/v4l/budget-patch.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/budget-patch.ko
  CC      /home/michael/saa7164-v4l/v4l/budget.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/budget.ko
  CC      /home/michael/saa7164-v4l/v4l/bw-qcam.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/bw-qcam.ko
  CC      /home/michael/saa7164-v4l/v4l/c-qcam.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/c-qcam.ko
  CC      /home/michael/saa7164-v4l/v4l/cafe_ccic.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cafe_ccic.ko
  CC      /home/michael/saa7164-v4l/v4l/cpia.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cpia.ko
  CC      /home/michael/saa7164-v4l/v4l/cpia2.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cpia2.ko
  CC      /home/michael/saa7164-v4l/v4l/cpia_pp.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cpia_pp.ko
  CC      /home/michael/saa7164-v4l/v4l/cpia_usb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cpia_usb.ko
  CC      /home/michael/saa7164-v4l/v4l/cs5345.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cs5345.ko
  CC      /home/michael/saa7164-v4l/v4l/cs53l32a.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cs53l32a.ko
  CC      /home/michael/saa7164-v4l/v4l/cx18-alsa.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx18-alsa.ko
  CC      /home/michael/saa7164-v4l/v4l/cx18.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx18.ko
  CC      /home/michael/saa7164-v4l/v4l/cx22700.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx22700.ko
  CC      /home/michael/saa7164-v4l/v4l/cx22702.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx22702.ko
  CC      /home/michael/saa7164-v4l/v4l/cx231xx-alsa.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx231xx-alsa.ko
  CC      /home/michael/saa7164-v4l/v4l/cx231xx-dvb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx231xx-dvb.ko
  CC      /home/michael/saa7164-v4l/v4l/cx231xx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx231xx.ko
  CC      /home/michael/saa7164-v4l/v4l/cx2341x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx2341x.ko
  CC      /home/michael/saa7164-v4l/v4l/cx23885.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx23885.ko
  CC      /home/michael/saa7164-v4l/v4l/cx24110.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx24110.ko
  CC      /home/michael/saa7164-v4l/v4l/cx24113.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx24113.ko
  CC      /home/michael/saa7164-v4l/v4l/cx24116.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx24116.ko
  CC      /home/michael/saa7164-v4l/v4l/cx24123.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx24123.ko
  CC      /home/michael/saa7164-v4l/v4l/cx25840.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx25840.ko
  CC      /home/michael/saa7164-v4l/v4l/cx88-alsa.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx88-alsa.ko
  CC      /home/michael/saa7164-v4l/v4l/cx88-blackbird.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx88-blackbird.ko
  CC      /home/michael/saa7164-v4l/v4l/cx88-dvb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx88-dvb.ko
  CC      /home/michael/saa7164-v4l/v4l/cx88-vp3054-i2c.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx88-vp3054-i2c.ko
  CC      /home/michael/saa7164-v4l/v4l/cx8800.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx8800.ko
  CC      /home/michael/saa7164-v4l/v4l/cx8802.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx8802.ko
  CC      /home/michael/saa7164-v4l/v4l/cx88xx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/cx88xx.ko
  CC      /home/michael/saa7164-v4l/v4l/dabusb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dabusb.ko
  CC      /home/michael/saa7164-v4l/v4l/dib0070.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dib0070.ko
  CC      /home/michael/saa7164-v4l/v4l/dib0090.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dib0090.ko
  CC      /home/michael/saa7164-v4l/v4l/dib3000mb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dib3000mb.ko
  CC      /home/michael/saa7164-v4l/v4l/dib3000mc.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dib3000mc.ko
  CC      /home/michael/saa7164-v4l/v4l/dib7000m.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dib7000m.ko
  CC      /home/michael/saa7164-v4l/v4l/dib7000p.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dib7000p.ko
  CC      /home/michael/saa7164-v4l/v4l/dib8000.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dib8000.ko
  CC      /home/michael/saa7164-v4l/v4l/dibx000_common.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dibx000_common.ko
  CC      /home/michael/saa7164-v4l/v4l/dm1105.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dm1105.ko
  CC      /home/michael/saa7164-v4l/v4l/drx397xD.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/drx397xD.ko
  CC      /home/michael/saa7164-v4l/v4l/ds3000.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ds3000.ko
  CC      /home/michael/saa7164-v4l/v4l/dsbr100.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dsbr100.ko
  CC      /home/michael/saa7164-v4l/v4l/dst.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dst.ko
  CC      /home/michael/saa7164-v4l/v4l/dst_ca.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dst_ca.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-bt8xx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-bt8xx.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-core.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-core.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-pll.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-pll.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-ttpci.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-ttpci.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-ttusb-budget.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-ttusb-budget.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-a800.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-a800.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-af9005-remote.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-af9005-remote.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-af9005.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-af9005.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-af9015.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-af9015.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-anysee.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-anysee.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-au6610.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-au6610.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-az6027.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-az6027.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-ce6230.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-ce6230.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-cinergyT2.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-cinergyT2.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-cxusb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-cxusb.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-dib0700.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dib0700.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-dibusb-common.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dibusb-common.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-dibusb-mb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dibusb-mb.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-dibusb-mc.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dibusb-mc.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-digitv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-digitv.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-dtt200u.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dtt200u.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-dtv5100.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dtv5100.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-dw2102.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-dw2102.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-ec168.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-ec168.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-friio.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-friio.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-gl861.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-gl861.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-gp8psk.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-gp8psk.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-m920x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-m920x.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-nova-t-usb2.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-nova-t-usb2.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-opera.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-opera.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-ttusb2.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-ttusb2.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-umt-010.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-umt-010.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-vp702x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-vp702x.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb-vp7045.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb-vp7045.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb-usb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb-usb.ko
  CC      /home/michael/saa7164-v4l/v4l/dvb_dummy_fe.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/dvb_dummy_fe.ko
  CC      /home/michael/saa7164-v4l/v4l/earth-pt1.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/earth-pt1.ko
  CC      /home/michael/saa7164-v4l/v4l/ec100.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ec100.ko
  CC      /home/michael/saa7164-v4l/v4l/em28xx-alsa.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/em28xx-alsa.ko
  CC      /home/michael/saa7164-v4l/v4l/em28xx-dvb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/em28xx-dvb.ko
  CC      /home/michael/saa7164-v4l/v4l/em28xx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/em28xx.ko
  CC      /home/michael/saa7164-v4l/v4l/et61x251.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/et61x251.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_benq.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_benq.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_conex.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_conex.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_cpia1.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_cpia1.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_etoms.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_etoms.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_finepix.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_finepix.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_gl860.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_gl860.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_jeilinj.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_jeilinj.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_m5602.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_m5602.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_main.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_main.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_mars.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_mars.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_mr97310a.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_mr97310a.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_ov519.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_ov519.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_ov534.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_ov534.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_ov534_9.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_ov534_9.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_pac207.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_pac207.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_pac7302.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_pac7302.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_pac7311.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_pac7311.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_sn9c2028.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sn9c2028.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_sn9c20x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sn9c20x.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_sonixb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sonixb.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_sonixj.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sonixj.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_spca500.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca500.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_spca501.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca501.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_spca505.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca505.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_spca506.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca506.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_spca508.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca508.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_spca561.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_spca561.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_sq905.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sq905.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_sq905c.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sq905c.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_stk014.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_stk014.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_stv0680.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_stv0680.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_stv06xx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_stv06xx.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_sunplus.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_sunplus.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_t613.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_t613.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_tv8532.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_tv8532.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_vc032x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_vc032x.ko
  CC      /home/michael/saa7164-v4l/v4l/gspca_zc3xx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/gspca_zc3xx.ko
  CC      /home/michael/saa7164-v4l/v4l/hdpvr.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/hdpvr.ko
  CC      /home/michael/saa7164-v4l/v4l/hexium_gemini.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/hexium_gemini.ko
  CC      /home/michael/saa7164-v4l/v4l/hexium_orion.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/hexium_orion.ko
  CC      /home/michael/saa7164-v4l/v4l/hopper.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/hopper.ko
  CC      /home/michael/saa7164-v4l/v4l/ibmcam.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ibmcam.ko
  CC      /home/michael/saa7164-v4l/v4l/imon.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/imon.ko
  CC      /home/michael/saa7164-v4l/v4l/ir-common.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-common.ko
  CC      /home/michael/saa7164-v4l/v4l/ir-core.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-core.ko
  CC      /home/michael/saa7164-v4l/v4l/ir-jvc-decoder.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-jvc-decoder.ko
  CC      /home/michael/saa7164-v4l/v4l/ir-kbd-i2c.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-kbd-i2c.ko
  CC      /home/michael/saa7164-v4l/v4l/ir-nec-decoder.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-nec-decoder.ko
  CC      /home/michael/saa7164-v4l/v4l/ir-rc5-decoder.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-rc5-decoder.ko
  CC      /home/michael/saa7164-v4l/v4l/ir-rc6-decoder.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-rc6-decoder.ko
  CC      /home/michael/saa7164-v4l/v4l/ir-sony-decoder.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ir-sony-decoder.ko
  CC      /home/michael/saa7164-v4l/v4l/isl6405.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/isl6405.ko
  CC      /home/michael/saa7164-v4l/v4l/isl6421.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/isl6421.ko
  CC      /home/michael/saa7164-v4l/v4l/isl6423.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/isl6423.ko
  CC      /home/michael/saa7164-v4l/v4l/itd1000.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/itd1000.ko
  CC      /home/michael/saa7164-v4l/v4l/ivtv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ivtv.ko
  CC      /home/michael/saa7164-v4l/v4l/ivtvfb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ivtvfb.ko
  CC      /home/michael/saa7164-v4l/v4l/konicawc.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/konicawc.ko
  CC      /home/michael/saa7164-v4l/v4l/ks0127.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ks0127.ko
  CC      /home/michael/saa7164-v4l/v4l/l64781.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/l64781.ko
  CC      /home/michael/saa7164-v4l/v4l/lgdt3304.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/lgdt3304.ko
  CC      /home/michael/saa7164-v4l/v4l/lgdt3305.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/lgdt3305.ko
  CC      /home/michael/saa7164-v4l/v4l/lgdt330x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/lgdt330x.ko
  CC      /home/michael/saa7164-v4l/v4l/lgs8gl5.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/lgs8gl5.ko
  CC      /home/michael/saa7164-v4l/v4l/lgs8gxx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/lgs8gxx.ko
  CC      /home/michael/saa7164-v4l/v4l/lnbp21.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/lnbp21.ko
  CC      /home/michael/saa7164-v4l/v4l/m52790.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/m52790.ko
  CC      /home/michael/saa7164-v4l/v4l/mantis.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mantis.ko
  CC      /home/michael/saa7164-v4l/v4l/mantis_core.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mantis_core.ko
  CC      /home/michael/saa7164-v4l/v4l/max2165.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/max2165.ko
  CC      /home/michael/saa7164-v4l/v4l/mb86a16.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mb86a16.ko
  CC      /home/michael/saa7164-v4l/v4l/mc44s803.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mc44s803.ko
  CC      /home/michael/saa7164-v4l/v4l/mem2mem_testdev.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mem2mem_testdev.ko
  CC      /home/michael/saa7164-v4l/v4l/meye.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/meye.ko
  CC      /home/michael/saa7164-v4l/v4l/msp3400.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/msp3400.ko
  CC      /home/michael/saa7164-v4l/v4l/mt2060.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt2060.ko
  CC      /home/michael/saa7164-v4l/v4l/mt20xx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt20xx.ko
  CC      /home/michael/saa7164-v4l/v4l/mt2131.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt2131.ko
  CC      /home/michael/saa7164-v4l/v4l/mt2266.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt2266.ko
  CC      /home/michael/saa7164-v4l/v4l/mt312.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt312.ko
  CC      /home/michael/saa7164-v4l/v4l/mt352.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt352.ko
  CC      /home/michael/saa7164-v4l/v4l/mt9m001.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt9m001.ko
  CC      /home/michael/saa7164-v4l/v4l/mt9m111.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt9m111.ko
  CC      /home/michael/saa7164-v4l/v4l/mt9t031.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt9t031.ko
  CC      /home/michael/saa7164-v4l/v4l/mt9t112.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt9t112.ko
  CC      /home/michael/saa7164-v4l/v4l/mt9v011.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt9v011.ko
  CC      /home/michael/saa7164-v4l/v4l/mt9v022.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mt9v022.ko
  CC      /home/michael/saa7164-v4l/v4l/mxb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mxb.ko
  CC      /home/michael/saa7164-v4l/v4l/mxl5005s.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mxl5005s.ko
  CC      /home/michael/saa7164-v4l/v4l/mxl5007t.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/mxl5007t.ko
  CC      /home/michael/saa7164-v4l/v4l/ngene.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ngene.ko
  CC      /home/michael/saa7164-v4l/v4l/nxt200x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/nxt200x.ko
  CC      /home/michael/saa7164-v4l/v4l/nxt6000.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/nxt6000.ko
  CC      /home/michael/saa7164-v4l/v4l/or51132.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/or51132.ko
  CC      /home/michael/saa7164-v4l/v4l/or51211.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/or51211.ko
  CC      /home/michael/saa7164-v4l/v4l/ov511.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ov511.ko
  CC      /home/michael/saa7164-v4l/v4l/ov7670.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ov7670.ko
  CC      /home/michael/saa7164-v4l/v4l/ov772x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ov772x.ko
  CC      /home/michael/saa7164-v4l/v4l/ov9640.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ov9640.ko
  CC      /home/michael/saa7164-v4l/v4l/ovcamchip.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ovcamchip.ko
  CC      /home/michael/saa7164-v4l/v4l/pluto2.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/pluto2.ko
  CC      /home/michael/saa7164-v4l/v4l/pms.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/pms.ko
  CC      /home/michael/saa7164-v4l/v4l/poseidon.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/poseidon.ko
  CC      /home/michael/saa7164-v4l/v4l/pvrusb2.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/pvrusb2.ko
  CC      /home/michael/saa7164-v4l/v4l/pwc.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/pwc.ko
  CC      /home/michael/saa7164-v4l/v4l/qt1010.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/qt1010.ko
  CC      /home/michael/saa7164-v4l/v4l/quickcam_messenger.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/quickcam_messenger.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-aimslab.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-aimslab.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-aztech.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-aztech.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-cadet.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-cadet.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-gemtek-pci.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-gemtek-pci.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-gemtek.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-gemtek.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-maestro.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-maestro.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-maxiradio.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-maxiradio.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-miropcm20.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-miropcm20.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-mr800.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-mr800.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-rtrack2.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-rtrack2.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-sf16fmi.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-sf16fmi.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-sf16fmr2.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-sf16fmr2.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-si4713.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-si4713.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-tea5764.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-tea5764.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-terratec.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-terratec.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-timb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-timb.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-trust.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-trust.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-typhoon.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-typhoon.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-usb-si470x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-usb-si470x.ko
  CC      /home/michael/saa7164-v4l/v4l/radio-zoltrix.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/radio-zoltrix.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-adstech-dvb-t-pci.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-adstech-dvb-t-pci.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-apac-viewcomp.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-apac-viewcomp.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-asus-pc39.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-asus-pc39.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-ati-tv-wonder-hd-600.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-ati-tv-wonder-hd-600.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-avermedia-a16d.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-a16d.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-avermedia-cardbus.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-cardbus.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-avermedia-dvbt.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-dvbt.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-avermedia-m135a.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-m135a.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-avermedia-m733a-rm-k6.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia-m733a-rm-k6.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-avermedia.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-avermedia.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-avertv-303.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-avertv-303.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-behold-columbus.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-behold-columbus.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-behold.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-behold.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-budget-ci-old.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-budget-ci-old.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-cinergy-1400.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-cinergy-1400.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-cinergy.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-cinergy.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-dm1105-nec.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-dm1105-nec.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-dntv-live-dvb-t.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-dntv-live-dvb-t.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-dntv-live-dvbt-pro.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-dntv-live-dvbt-pro.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-em-terratec.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-em-terratec.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-empty.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-empty.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-encore-enltv-fm53.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-encore-enltv-fm53.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-encore-enltv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-encore-enltv.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-encore-enltv2.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-encore-enltv2.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-evga-indtube.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-evga-indtube.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-eztv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-eztv.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-flydvb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-flydvb.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-flyvideo.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-flyvideo.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-fusionhdtv-mce.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-fusionhdtv-mce.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-gadmei-rm008z.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-gadmei-rm008z.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-genius-tvgo-a11mce.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-genius-tvgo-a11mce.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-gotview7135.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-gotview7135.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-hauppauge-new.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-hauppauge-new.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-imon-mce.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-imon-mce.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-imon-pad.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-imon-pad.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-iodata-bctv7e.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-iodata-bctv7e.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-kaiomy.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-kaiomy.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-kworld-315u.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-kworld-315u.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-kworld-plus-tv-analog.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-kworld-plus-tv-analog.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-manli.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-manli.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-msi-tvanywhere-plus.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-msi-tvanywhere-plus.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-msi-tvanywhere.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-msi-tvanywhere.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-nebula.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-nebula.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-nec-terratec-cinergy-xs.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-nec-terratec-cinergy-xs.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-norwood.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-norwood.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-npgtech.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-npgtech.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-pctv-sedna.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-pctv-sedna.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-pinnacle-color.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-pinnacle-color.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-pinnacle-grey.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-pinnacle-grey.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-pinnacle-pctv-hd.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-pinnacle-pctv-hd.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-pixelview-mk12.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-pixelview-mk12.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-pixelview-new.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-pixelview-new.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-pixelview.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-pixelview.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-powercolor-real-angel.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-powercolor-real-angel.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-proteus-2309.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-proteus-2309.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-purpletv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-purpletv.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-pv951.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-pv951.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-rc5-hauppauge-new.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-rc5-hauppauge-new.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-rc5-tv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-rc5-tv.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-real-audio-220-32-keys.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-real-audio-220-32-keys.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-tbs-nec.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-tbs-nec.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-terratec-cinergy-xs.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-terratec-cinergy-xs.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-tevii-nec.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-tevii-nec.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-tt-1500.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-tt-1500.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-videomate-s350.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-videomate-s350.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-videomate-tv-pvr.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-videomate-tv-pvr.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-winfast-usbii-deluxe.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-winfast-usbii-deluxe.ko
  CC      /home/michael/saa7164-v4l/v4l/rc-winfast.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rc-winfast.ko
  CC      /home/michael/saa7164-v4l/v4l/rj54n1cb0c.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/rj54n1cb0c.ko
  CC      /home/michael/saa7164-v4l/v4l/s2255drv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/s2255drv.ko
  CC      /home/michael/saa7164-v4l/v4l/s5h1409.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/s5h1409.ko
  CC      /home/michael/saa7164-v4l/v4l/s5h1411.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/s5h1411.ko
  CC      /home/michael/saa7164-v4l/v4l/s5h1420.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/s5h1420.ko
  CC      /home/michael/saa7164-v4l/v4l/s921.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/s921.ko
  CC      /home/michael/saa7164-v4l/v4l/saa5246a.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa5246a.ko
  CC      /home/michael/saa7164-v4l/v4l/saa5249.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa5249.ko
  CC      /home/michael/saa7164-v4l/v4l/saa6588.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa6588.ko
  CC      /home/michael/saa7164-v4l/v4l/saa6752hs.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa6752hs.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7110.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7110.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7115.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7115.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7127.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7127.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7134-alsa.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7134-alsa.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7134-dvb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7134-dvb.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7134-empress.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7134-empress.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7134.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7134.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7146.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7146.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7146_vv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7146_vv.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7164.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7164.ko
  CC      /home/michael/saa7164-v4l/v4l/saa717x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa717x.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7185.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7185.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7191.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7191.ko
  CC      /home/michael/saa7164-v4l/v4l/saa7706h.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/saa7706h.ko
  CC      /home/michael/saa7164-v4l/v4l/se401.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/se401.ko
  CC      /home/michael/saa7164-v4l/v4l/si21xx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/si21xx.ko
  CC      /home/michael/saa7164-v4l/v4l/si4713-i2c.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/si4713-i2c.ko
  CC      /home/michael/saa7164-v4l/v4l/smsdvb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/smsdvb.ko
  CC      /home/michael/saa7164-v4l/v4l/smsmdtv.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/smsmdtv.ko
  CC      /home/michael/saa7164-v4l/v4l/smssdio.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/smssdio.ko
  CC      /home/michael/saa7164-v4l/v4l/smsusb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/smsusb.ko
  CC      /home/michael/saa7164-v4l/v4l/sn9c102.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/sn9c102.ko
  CC      /home/michael/saa7164-v4l/v4l/snd-bt87x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/snd-bt87x.ko
  CC      /home/michael/saa7164-v4l/v4l/snd-tea575x-tuner.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/snd-tea575x-tuner.ko
  CC      /home/michael/saa7164-v4l/v4l/soc_camera.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/soc_camera.ko
  CC      /home/michael/saa7164-v4l/v4l/soc_camera_platform.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/soc_camera_platform.ko
  CC      /home/michael/saa7164-v4l/v4l/soc_mediabus.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/soc_mediabus.ko
  CC      /home/michael/saa7164-v4l/v4l/sp8870.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/sp8870.ko
  CC      /home/michael/saa7164-v4l/v4l/sp887x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/sp887x.ko
  CC      /home/michael/saa7164-v4l/v4l/stb0899.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stb0899.ko
  CC      /home/michael/saa7164-v4l/v4l/stb6000.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stb6000.ko
  CC      /home/michael/saa7164-v4l/v4l/stb6100.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stb6100.ko
  CC      /home/michael/saa7164-v4l/v4l/stkwebcam.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stkwebcam.ko
  CC      /home/michael/saa7164-v4l/v4l/stradis.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stradis.ko
  CC      /home/michael/saa7164-v4l/v4l/stv0288.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stv0288.ko
  CC      /home/michael/saa7164-v4l/v4l/stv0297.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stv0297.ko
  CC      /home/michael/saa7164-v4l/v4l/stv0299.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stv0299.ko
  CC      /home/michael/saa7164-v4l/v4l/stv0900.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stv0900.ko
  CC      /home/michael/saa7164-v4l/v4l/stv090x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stv090x.ko
  CC      /home/michael/saa7164-v4l/v4l/stv6110.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stv6110.ko
  CC      /home/michael/saa7164-v4l/v4l/stv6110x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stv6110x.ko
  CC      /home/michael/saa7164-v4l/v4l/stv680.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/stv680.ko
  CC      /home/michael/saa7164-v4l/v4l/tcm825x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tcm825x.ko
  CC      /home/michael/saa7164-v4l/v4l/tda10021.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda10021.ko
  CC      /home/michael/saa7164-v4l/v4l/tda10023.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda10023.ko
  CC      /home/michael/saa7164-v4l/v4l/tda10048.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda10048.ko
  CC      /home/michael/saa7164-v4l/v4l/tda1004x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda1004x.ko
  CC      /home/michael/saa7164-v4l/v4l/tda10086.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda10086.ko
  CC      /home/michael/saa7164-v4l/v4l/tda18271.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda18271.ko
  CC      /home/michael/saa7164-v4l/v4l/tda665x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda665x.ko
  CC      /home/michael/saa7164-v4l/v4l/tda7432.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda7432.ko
  CC      /home/michael/saa7164-v4l/v4l/tda8083.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda8083.ko
  CC      /home/michael/saa7164-v4l/v4l/tda8261.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda8261.ko
  CC      /home/michael/saa7164-v4l/v4l/tda826x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda826x.ko
  CC      /home/michael/saa7164-v4l/v4l/tda827x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda827x.ko
  CC      /home/michael/saa7164-v4l/v4l/tda8290.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda8290.ko
  CC      /home/michael/saa7164-v4l/v4l/tda9840.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda9840.ko
  CC      /home/michael/saa7164-v4l/v4l/tda9875.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda9875.ko
  CC      /home/michael/saa7164-v4l/v4l/tda9887.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tda9887.ko
  CC      /home/michael/saa7164-v4l/v4l/tea5761.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tea5761.ko
  CC      /home/michael/saa7164-v4l/v4l/tea5767.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tea5767.ko
  CC      /home/michael/saa7164-v4l/v4l/tea6415c.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tea6415c.ko
  CC      /home/michael/saa7164-v4l/v4l/tea6420.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tea6420.ko
  CC      /home/michael/saa7164-v4l/v4l/tef6862.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tef6862.ko
  CC      /home/michael/saa7164-v4l/v4l/ths7303.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ths7303.ko
  CC      /home/michael/saa7164-v4l/v4l/tlv320aic23b.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tlv320aic23b.ko
  CC      /home/michael/saa7164-v4l/v4l/ttpci-eeprom.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ttpci-eeprom.ko
  CC      /home/michael/saa7164-v4l/v4l/ttusb_dec.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ttusb_dec.ko
  CC      /home/michael/saa7164-v4l/v4l/ttusbdecfe.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ttusbdecfe.ko
  CC      /home/michael/saa7164-v4l/v4l/tua6100.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tua6100.ko
  CC      /home/michael/saa7164-v4l/v4l/tuner-simple.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tuner-simple.ko
  CC      /home/michael/saa7164-v4l/v4l/tuner-types.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tuner-types.ko
  CC      /home/michael/saa7164-v4l/v4l/tuner-xc2028.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tuner-xc2028.ko
  CC      /home/michael/saa7164-v4l/v4l/tuner.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tuner.ko
  CC      /home/michael/saa7164-v4l/v4l/tvaudio.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tvaudio.ko
  CC      /home/michael/saa7164-v4l/v4l/tveeprom.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tveeprom.ko
  CC      /home/michael/saa7164-v4l/v4l/tvp514x.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tvp514x.ko
  CC      /home/michael/saa7164-v4l/v4l/tvp5150.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tvp5150.ko
  CC      /home/michael/saa7164-v4l/v4l/tvp7002.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tvp7002.ko
  CC      /home/michael/saa7164-v4l/v4l/tw9910.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/tw9910.ko
  CC      /home/michael/saa7164-v4l/v4l/ultracam.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ultracam.ko
  CC      /home/michael/saa7164-v4l/v4l/upd64031a.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/upd64031a.ko
  CC      /home/michael/saa7164-v4l/v4l/upd64083.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/upd64083.ko
  CC      /home/michael/saa7164-v4l/v4l/usbvideo.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/usbvideo.ko
  CC      /home/michael/saa7164-v4l/v4l/usbvision.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/usbvision.ko
  CC      /home/michael/saa7164-v4l/v4l/uvcvideo.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/uvcvideo.ko
  CC      /home/michael/saa7164-v4l/v4l/v4l1-compat.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/v4l1-compat.ko
  CC      /home/michael/saa7164-v4l/v4l/v4l2-common.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/v4l2-common.ko
  CC      /home/michael/saa7164-v4l/v4l/v4l2-int-device.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/v4l2-int-device.ko
  CC      /home/michael/saa7164-v4l/v4l/v4l2-mem2mem.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/v4l2-mem2mem.ko
  CC      /home/michael/saa7164-v4l/v4l/ves1820.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ves1820.ko
  CC      /home/michael/saa7164-v4l/v4l/ves1x93.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/ves1x93.ko
  CC      /home/michael/saa7164-v4l/v4l/vicam.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/vicam.ko
  CC      /home/michael/saa7164-v4l/v4l/videobuf-core.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/videobuf-core.ko
  CC      /home/michael/saa7164-v4l/v4l/videobuf-dma-contig.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/videobuf-dma-contig.ko
  CC      /home/michael/saa7164-v4l/v4l/videobuf-dma-sg.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/videobuf-dma-sg.ko
  CC      /home/michael/saa7164-v4l/v4l/videobuf-dvb.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/videobuf-dvb.ko
  CC      /home/michael/saa7164-v4l/v4l/videobuf-vmalloc.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/videobuf-vmalloc.ko
  CC      /home/michael/saa7164-v4l/v4l/videocodec.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/videocodec.ko
  CC      /home/michael/saa7164-v4l/v4l/videodev.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/videodev.ko
  CC      /home/michael/saa7164-v4l/v4l/vp27smpx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/vp27smpx.ko
  CC      /home/michael/saa7164-v4l/v4l/vpx3220.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/vpx3220.ko
  CC      /home/michael/saa7164-v4l/v4l/w9966.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/w9966.ko
  CC      /home/michael/saa7164-v4l/v4l/w9968cf.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/w9968cf.ko
  CC      /home/michael/saa7164-v4l/v4l/wm8739.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/wm8739.ko
  CC      /home/michael/saa7164-v4l/v4l/wm8775.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/wm8775.ko
  CC      /home/michael/saa7164-v4l/v4l/xc5000.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/xc5000.ko
  CC      /home/michael/saa7164-v4l/v4l/zc0301.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zc0301.ko
  CC      /home/michael/saa7164-v4l/v4l/zl10036.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zl10036.ko
  CC      /home/michael/saa7164-v4l/v4l/zl10039.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zl10039.ko
  CC      /home/michael/saa7164-v4l/v4l/zl10353.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zl10353.ko
  CC      /home/michael/saa7164-v4l/v4l/zr36016.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zr36016.ko
  CC      /home/michael/saa7164-v4l/v4l/zr36050.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zr36050.ko
  CC      /home/michael/saa7164-v4l/v4l/zr36060.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zr36060.ko
  CC      /home/michael/saa7164-v4l/v4l/zr36067.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zr36067.ko
  CC      /home/michael/saa7164-v4l/v4l/zr364xx.mod.o
  LD [M]  /home/michael/saa7164-v4l/v4l/zr364xx.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
./scripts/rmmod.pl check
found 432 modules
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ 

_**Wow, never got this far before.  I guess I do this now**_
sudo make install

michael@michael-OptiPlex-GX280:~/saa7164-v4l$ sudo make install
make -C /home/michael/saa7164-v4l/v4l install
make[1]: Entering directory `/home/michael/saa7164-v4l/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.35-25-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.35-25-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.35-25-generic/kernel/drivers/media/common:

-e 
Removing obsolete files from /lib/modules/2.6.35-25-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.35-25-generic/kernel/drivers/media/:
    video/gspca/m5602/: gspca_m5602.ko 
    dvb/dvb-usb/: dvb-usb-dtv5100.ko dvb-usb-opera.ko dvb-usb-cxusb.ko 
        dvb-usb-vp7045.ko dvb-usb-af9005-remote.ko dvb-usb-ttusb2.ko 
        dvb-usb-af9015.ko dvb-usb-dib0700.ko dvb-usb-az6027.ko 
        dvb-usb-a800.ko dvb-usb-gp8psk.ko dvb-usb-dibusb-common.ko 
        dvb-usb-au6610.ko dvb-usb-digitv.ko dvb-usb.ko 
        dvb-usb-dibusb-mc.ko dvb-usb-af9005.ko dvb-usb-nova-t-usb2.ko 
        dvb-usb-friio.ko dvb-usb-ce6230.ko dvb-usb-dtt200u.ko 
        dvb-usb-cinergyT2.ko dvb-usb-vp702x.ko dvb-usb-umt-010.ko 
        dvb-usb-anysee.ko dvb-usb-dibusb-mb.ko dvb-usb-dw2102.ko 
        dvb-usb-gl861.ko dvb-usb-ec168.ko dvb-usb-m920x.ko 
    video/saa7164/: saa7164.ko 
    video/zoran/: videocodec.ko zr36050.ko zr36016.ko 
        zr36060.ko zr36067.ko 
    video/cx18/: cx18.ko cx18-alsa.ko 
    video/cpia2/: cpia2.ko 
    IR/keymaps/: rc-tevii-nec.ko rc-adstech-dvb-t-pci.ko rc-hauppauge-new.ko 
        rc-pctv-sedna.ko rc-proteus-2309.ko rc-msi-tvanywhere.ko 
        rc-avermedia-dvbt.ko rc-pixelview.ko rc-dm1105-nec.ko 
        rc-encore-enltv-fm53.ko rc-imon-mce.ko rc-evga-indtube.ko 
        rc-em-terratec.ko rc-gadmei-rm008z.ko rc-avermedia-m733a-rm-k6.ko 
        rc-dntv-live-dvb-t.ko rc-kworld-plus-tv-analog.ko rc-behold.ko 
        rc-norwood.ko rc-rc5-tv.ko rc-pinnacle-color.ko 
        rc-cinergy-1400.ko rc-avertv-303.ko rc-cinergy.ko 
        rc-manli.ko rc-eztv.ko rc-kworld-315u.ko 
        rc-avermedia-a16d.ko rc-tt-1500.ko rc-videomate-tv-pvr.ko 
        rc-apac-viewcomp.ko rc-terratec-cinergy-xs.ko rc-nebula.ko 
        rc-msi-tvanywhere-plus.ko rc-npgtech.ko rc-ati-tv-wonder-hd-600.ko 
        rc-pinnacle-pctv-hd.ko rc-iodata-bctv7e.ko rc-budget-ci-old.ko 
        rc-avermedia.ko rc-imon-pad.ko rc-nec-terratec-cinergy-xs.ko 
        rc-winfast-usbii-deluxe.ko rc-flydvb.ko rc-videomate-s350.ko 
        rc-pv951.ko rc-pixelview-mk12.ko rc-winfast.ko 
        rc-encore-enltv2.ko rc-pixelview-new.ko rc-purpletv.ko 
        rc-fusionhdtv-mce.ko rc-empty.ko rc-gotview7135.ko 
        rc-kaiomy.ko rc-pinnacle-grey.ko rc-powercolor-real-angel.ko 
        rc-avermedia-m135a.ko rc-rc5-hauppauge-new.ko rc-flyvideo.ko 
        rc-encore-enltv.ko rc-behold-columbus.ko rc-tbs-nec.ko 
        rc-avermedia-cardbus.ko rc-genius-tvgo-a11mce.ko rc-real-audio-220-32-keys.ko 
        rc-dntv-live-dvbt-pro.ko rc-asus-pc39.ko 
    dvb/b2c2/: b2c2-flexcop-pci.ko b2c2-flexcop.ko b2c2-flexcop-usb.ko 
    video/ivtv/: ivtvfb.ko ivtv.ko 
    dvb/mantis/: mantis_core.ko mantis.ko hopper.ko 
    video/hdpvr/: hdpvr.ko 
    common/tuners/: tuner-xc2028.ko mt2060.ko tda9887.ko 
        mt2131.ko mc44s803.ko qt1010.ko 
        max2165.ko mt20xx.ko tda827x.ko 
        tda18271.ko xc5000.ko mxl5007t.ko 
        tea5761.ko tuner-types.ko tda8290.ko 
        tuner-simple.ko mt2266.ko tea5767.ko 
        mxl5005s.ko 
    video/sn9c102/: sn9c102.ko 
    dvb/dvb-core/: dvb-core.ko 
    video/: videobuf-dma-contig.ko vpx3220.ko videobuf-dma-sg.ko 
        pms.ko bt856.ko v4l2-mem2mem.ko 
        upd64083.ko stradis.ko videobuf-core.ko 
        ths7303.ko tda9840.ko saa7191.ko 
        cx2341x.ko wm8775.ko meye.ko 
        adv7180.ko w9968cf.ko rj54n1cb0c.ko 
        saa7185.ko tuner.ko mt9t031.ko 
        zr364xx.ko ks0127.ko stv680.ko 
        videobuf-dvb.ko tvaudio.ko tea6420.ko 
        bt866.ko cafe_ccic.ko mt9v011.ko 
        saa5246a.ko msp3400.ko tvp514x.ko 
        mem2mem_testdev.ko tcm825x.ko soc_camera.ko 
        wm8739.ko stkwebcam.ko saa5249.ko 
        cpia_pp.ko soc_mediabus.ko tda7432.ko 
        w9966.ko ir-kbd-i2c.ko mt9m001.ko 
        upd64031a.ko ov511.ko tea6415c.ko 
        dabusb.ko bt819.ko cpia_usb.ko 
        videodev.ko mxb.ko tda9875.ko 
        adv7175.ko soc_camera_platform.ko adv7343.ko 
        cs53l32a.ko s2255drv.ko btcx-risc.ko 
        se401.ko saa7110.ko saa7115.ko 
        saa6588.ko ak881x.ko tvp7002.ko 
        v4l2-common.ko hexium_gemini.ko hexium_orion.ko 
        tw9910.ko tvp5150.ko mt9m111.ko 
        vp27smpx.ko adv7170.ko ov772x.ko 
        ov7670.ko saa7127.ko m52790.ko 
        ov9640.ko mt9v022.ko v4l1-compat.ko 
        videobuf-vmalloc.ko v4l2-int-device.ko c-qcam.ko 
        tveeprom.ko cs5345.ko saa717x.ko 
        cpia.ko tlv320aic23b.ko bw-qcam.ko 
        mt9t112.ko 
    video/cx23885/: cx23885.ko 
    dvb/bt8xx/: dst_ca.ko dvb-bt8xx.ko bt878.ko 
        dst.ko 
    dvb/siano/: smssdio.ko smsdvb.ko smsusb.ko 
        smsmdtv.ko 
    video/cx25840/: cx25840.ko 
    dvb/ttusb-dec/: ttusbdecfe.ko ttusb_dec.ko 
    dvb/ngene/: ngene.ko 
    dvb/dm1105/: dm1105.ko 
    video/cx231xx/: cx231xx.ko cx231xx-dvb.ko cx231xx-alsa.ko 
    video/saa7134/: saa6752hs.ko saa7134-empress.ko saa7134-alsa.ko 
        saa7134-dvb.ko saa7134.ko 
    dvb/ttpci/: dvb-ttpci.ko budget-patch.ko ttpci-eeprom.ko 
        budget-av.ko budget.ko budget-core.ko 
        budget-ci.ko 
    video/et61x251/: et61x251.ko 
    video/gspca/gl860/: gspca_gl860.ko 
    IR/: ir-rc6-decoder.ko ir-sony-decoder.ko ir-jvc-decoder.ko 
        ir-core.ko ir-common.ko ir-nec-decoder.ko 
        ir-rc5-decoder.ko imon.ko 
    radio/si470x/: radio-usb-si470x.ko 
    dvb/frontends/: nxt6000.ko dib7000m.ko dib0090.ko 
        drx397xD.ko s5h1411.ko tda665x.ko 
        dib8000.ko nxt200x.ko s921.ko 
        s5h1409.ko atbm8830.ko dib3000mb.ko 
        ec100.ko lgs8gl5.ko dib3000mc.ko 
        stv0900.ko sp8870.ko tda8083.ko 
        stv0297.ko tda10086.ko zl10353.ko 
        mb86a16.ko lgs8gxx.ko stv0299.ko 
        dvb-pll.ko cx22702.ko lgdt3304.ko 
        tda8261.ko tua6100.ko bcm3510.ko 
        stb0899.ko or51211.ko cx24113.ko 
        tda826x.ko af9013.ko au8522.ko 
        si21xx.ko s5h1420.ko stv090x.ko 
        stv0288.ko mt352.ko zl10039.ko 
        isl6405.ko sp887x.ko dibx000_common.ko 
        isl6421.ko mt312.ko or51132.ko 
        tda1004x.ko stv6110.ko itd1000.ko 
        stv6110x.ko zl10036.ko lgdt3305.ko 
        dib7000p.ko l64781.ko ves1x93.ko 
        stb6100.ko ves1820.ko dib0070.ko 
        cx22700.ko cx24110.ko dvb_dummy_fe.ko 
        lgdt330x.ko cx24123.ko lnbp21.ko 
        stb6000.ko isl6423.ko tda10023.ko 
        cx24116.ko tda10021.ko tda10048.ko 
        ds3000.ko 
    video/bt8xx/: bttv.ko 
    video/cx88/: cx8802.ko cx8800.ko cx88-blackbird.ko 
        cx88-alsa.ko cx88xx.ko cx88-vp3054-i2c.ko 
        cx88-dvb.ko 
    video/gspca/: gspca_stk014.ko gspca_spca501.ko gspca_spca500.ko 
        gspca_mars.ko gspca_stv0680.ko gspca_sunplus.ko 
        gspca_vc032x.ko gspca_benq.ko gspca_spca505.ko 
        gspca_sn9c20x.ko gspca_zc3xx.ko gspca_sq905c.ko 
        gspca_sonixb.ko gspca_etoms.ko gspca_pac7302.ko 
        gspca_pac207.ko gspca_ov534_9.ko gspca_spca508.ko 
        gspca_sq905.ko gspca_sn9c2028.ko gspca_t613.ko 
        gspca_spca561.ko gspca_ov534.ko gspca_tv8532.ko 
        gspca_jeilinj.ko gspca_spca506.ko gspca_sonixj.ko 
        gspca_main.ko gspca_cpia1.ko gspca_conex.ko 
        gspca_mr97310a.ko gspca_pac7311.ko gspca_ov519.ko 
        gspca_finepix.ko 
    dvb/pluto2/: pluto2.ko 
    video/usbvideo/: ibmcam.ko usbvideo.ko vicam.ko 
        ultracam.ko konicawc.ko quickcam_messenger.ko 
    video/usbvision/: usbvision.ko 
    common/: saa7146_vv.ko saa7146.ko 
    video/gspca/stv06xx/: gspca_stv06xx.ko 
    video/em28xx/: em28xx-dvb.ko em28xx-alsa.ko em28xx.ko 
    radio/: dsbr100.ko radio-maestro.ko si4713-i2c.ko 
        radio-zoltrix.ko radio-miropcm20.ko radio-terratec.ko 
        tef6862.ko radio-aimslab.ko radio-maxiradio.ko 
        radio-gemtek.ko radio-trust.ko radio-sf16fmr2.ko 
        saa7706h.ko radio-tea5764.ko radio-si4713.ko 
        radio-typhoon.ko radio-cadet.ko radio-aztech.ko 
        radio-sf16fmi.ko radio-rtrack2.ko radio-gemtek-pci.ko 
        radio-timb.ko radio-mr800.ko 
    video/pvrusb2/: pvrusb2.ko 
    dvb/pt1/: earth-pt1.ko 
    video/tlg2300/: poseidon.ko 
    video/uvc/: uvcvideo.ko 
    dvb/ttusb-budget/: dvb-ttusb-budget.ko 
    video/pwc/: pwc.ko 
    video/ovcamchip/: ovcamchip.ko 
    video/zc0301/: zc0301.ko 
    video/au0828/: au0828.ko 
/sbin/depmod -a 2.6.35-25-generic 
make -C firmware install
make[2]: Entering directory `/home/michael/saa7164-v4l/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/michael/saa7164-v4l/v4l/firmware'
make[1]: Leaving directory `/home/michael/saa7164-v4l/v4l'
michael@michael-OptiPlex-GX280:~/saa7164-v4l$ 


_**And finally,**_
sudo reboot

_**Just came back up from reboot and am Editing this post**_
I'm using the new firmware!!!!!  Take note of the "NXP7164-2010-03-10.1.fw"--which is the analog driver for my HVR 2250 card!  

michael@michael-OptiPlex-GX280:~$ dmesg | grep saa7164
[   20.533478] saa7164 driver loaded
[   20.533579] saa7164 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.544530] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   20.544545] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xdf400000
[   20.544558] saa7164 0000:03:00.0: setting latency timer to 64
[   20.704108] saa7164_downloadfirmware() no first image
[   20.704168] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   20.951188] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   20.951194] saa7164_downloadfirmware() firmware loaded.
[   20.951216] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   20.951224] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   20.951228] saa7164_downloadfirmware() BSLSize = 0x0
[   20.951232] saa7164_downloadfirmware() Reserved = 0x0
[   20.951235] saa7164_downloadfirmware() Version = 0x1661c00
[   27.824534] saa7164_downloadimage() Image downloaded, booting...
[   27.928567] saa7164_downloadimage() Image booted successfully.
[   30.188039] saa7164_downloadimage() Image downloaded, booting...
[   31.984551] saa7164_downloadimage() Image booted successfully.
[   32.021179] saa7164[0]: Hauppauge eeprom: model=88061
[   32.775612] DVB: registering new adapter (saa7164)
[   36.171733] DVB: registering new adapter (saa7164)
[   36.173112] saa7164[0]: registered device video0 [mpeg]
[   36.424363] saa7164[0]: registered device video1 [mpeg]
[   36.656352] saa7164[0]: registered device vbi0 [vbi]
[   36.656425] saa7164[0]: registered device vbi1 [vbi]
michael@michael-OptiPlex-GX280:~$

---

### Post by newbuntu81 on 2011-02-09
[QUOTE=newbuntu81;10441602][QUOTE=newbuntu81;10441589][QUOTE=newbuntu81;10441487][QUOTE=newbuntu81;10441391][QUOTE=newbuntu81;10441346][QUOTE=newbuntu81;10441098][QUOTE=newbuntu81;10440736][QUOTE=newbuntu81;10438525]--------------------------------------------------------------

Ok, so the card is installed, using the correct firmware.  When I go into the MythTV backend I can set it up using IVTV and it actually shows the card type now, which is a nice surprise.  Don't forget to set the type to "tuner".

I scanned for channels and it listed some but did not populate a channel name (i.e. NBC).

Currently, I do not have any picture except a blue screen.  I have seen that others were having this issue through November 2010--I have not seen any updates since that.

Others seemed to mention that the AV (Composite) jacks work just fine, so if worst comes to worst I could use that...but I really was hoping to take advantage of the dual tuner via coax.  

Any ideas anyone?

---

### Post by schlidel on 2011-02-09
I too would like to know if HVR-2250 is fully working by now.

You should be able to record 2xNTSC, 2xDigital, or 1xNTSC-1xDigital at the same time.

It seems that when some people mention analog they are either referring to the s-video *or* cable ntsc. It appears many people get blue screens which would appear that s-video is working.  So analog _is_ working but not analog cable television. 

To be clear do drivers exist for cable ntsc with hvr-2250? (also hardware mpeg2 encoders... and possibly but not important FM radio)

I'm a newbie to linux and haven't even insalled it yet who owns an hvr-2250 wondering if I can proceed with any chance of success.

---

### Post by justNiz on 2011-02-17
I was having compiler errors with Steven Toth's analog HVR-2250 driver on my mythtv box (running ubuntu 10.10) so I just installed the latest stable kernel (2.6.37) from kernel.org as it now has the HVR-2250 analog and digital drivers included.

I can watch 2 different (cable) analog channels at the same time by running 2 mplayers. I haven't tried with 2 digital channels or 1 analog/1 digital yet but I don't expect it would be a problem. Mythtv is already successfully recording digital tv from the HVR-2250 so I know digital works (at least partially).

Mythtv (at least 0.24) does seem to have problems using both tuners concurrently (either analog or digital). I'm still trying to diagnose exactly whats going on, but because mplayer can do it, it seems to be a mythtv issue rather than a hardware or driver issue.

As a workaround, I currently have my mythtv backend tuner configuration set up so that one tuner only has its analog half configured, and the other tuner only has its digital half configured. Its only a partial workaround as I still get the occasional empty/corrupted recording. Obviously its also not optimal as this way mythtv can only use half the card's tuning capability.

---

### Post by newbuntu81 on 2011-02-20
> **justNiz said:**
> I was having compiler errors with Steven Toth's analog HVR-2250 driver on my mythtv box (running ubuntu 10.10) so I just installed the latest stable kernel (2.6.37) from kernel.org as it now has the HVR-2250 analog and digital drivers included.

I can watch 2 different (cable) analog channels at the same time by running 2 mplayers. I haven't tried with 2 digital channels or 1 analog/1 digital yet but I don't expect it would be a problem. Mythtv is already successfully recording digital tv from the HVR-2250 so I know digital works (at least partially).

Mythtv (at least 0.24) does seem to have problems using both tuners concurrently (either analog or digital). I'm still trying to diagnose exactly whats going on, but because mplayer can do it, it seems to be a mythtv issue rather than a hardware or driver issue.

As a workaround, I currently have my mythtv backend tuner configuration set up so that one tuner only has its analog half configured, and the other tuner only has its digital half configured. Its only a partial workaround as I still get the occasional empty/corrupted recording. Obviously its also not optimal as this way mythtv can only use half the card's tuning capability.

What commands did you use to update the kernel?  I'm not sure if I want to do that just yet.  I'm still pretty new to ubuntu and I'm not sure I know how to roll back if I mess it up.

Prior to switching to the NXP7164-2010-03-10.1.fw.1 (NTSC analog) driver, I was able to record with the over-the-air digital (ATSC) driver v4l-saa7164-1.0.3.fw.  I cannot seem to pull anything in with the NTSC driver in cable mode.  Are you using the coax connection on Cable mode, or the Composite or Svideo connections?  If cable, what mode are you in? 

I am having trouble playing recordings saved earlier from ATSC.  The screen shows blue lines around the recording when playing it.  I've searched and it seems to be a common thing, and steps are provided for some cards.  It appears to be easily fixed with a video card .conf update.

By the way, did you get 2250 MCE remote control to work with mythtv?  If so, can you shed some light or a link?  Thanks.

---

### Post by newbuntu81 on 2011-02-27
> **myrlin16 said:**
> I found more frequencies here:
[http://en.wikipedia.org/wiki/North_American_cable_television_frequencies](http://en.wikipedia.org/wiki/North_American_cable_television_frequencies)

There is a big table in the middle of the article that has the frequencies in the second column.  For example, lowband channel 2 "55.25" corresponds to "--set-freq=55.250".  I have tried a couple of other channels, but not many of them.

My hvr2250 analog tuners seem to be working fine, they just aren't working with myth.  I see there is a new release of the driver, I will try it out and report back if I learn anything.

Nice information.  I tried this and couldn't get anything to show, but then realized that I was trying to fine tune channel 2 "55.25".

I clicked your link and changed to channel 3, "61.25" and am now showing video and can hear audio--so the driver works in analog NTSC for me in mplayer!  It's very choppy though.

**North American Channel Frequencies:**
[http://en.wikipedia.org/wiki/North_American_cable_television_frequencies](http://en.wikipedia.org/wiki/North_American_cable_television_frequencies)
[U][B]
Versions[/B]: Mythbuntu 10.10 after Updates:[/U]
Kernel: 2.6.35-25-generic
MythTV Version   : v0.24-151-g1a69c92
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0

Driver/Firmware: dmesg | grep saa
[   22.296147] saa7164_downloadfirmware() Waiting for firmware upload [COLOR=Blue](NXP7164-2010-03-10.1.fw)
[/COLOR]
Commands:
sudo /etc/init.d/mythtv-backend stop
v4l2-ctl -d /dev/video1 --set-freq=61.250 <-- that's channel 3 for analog NTSC
mplayer /dev/video1


_**Log**_:  (Ctrl C broke me out of the mplayer window)

For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x21A72C                                                  
A:  46.5 V:  33.7 A-V: 12.879 ct:808.580 969/969 10%  0% 67.6% 157 0 
Too many video packets in the buffer: (4096 in 8284296 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  46.5 V:  33.7 A-V: 12.845 ct:809.580 970/970 10%  0% 67.5% 157 0 
Too many video packets in the buffer: (4096 in 8284308 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  46.5 V:  33.7 A-V: 12.812 ct:810.580 971/971 10%  0% 67.5% 157 0 
Too many video packets in the buffer: (4096 in 8284308 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x21B92C                                                  
A:  46.6 V:  33.8 A-V: 12.827 ct:811.580 972/972 10%  0% 67.6% 157 0 
Too many video packets in the buffer: (4096 in 8284308 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  46.6 V:  33.8 A-V: 12.793 ct:812.580 973/973 10%  0% 67.5% 157 0 
Too many video packets in the buffer: (4096 in 8284308 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x21BDAC                                                  
A:  46.6 V:  33.8 A-V: 12.808 ct:813.580 974/974 10%  0% 67.5% 157 0 
Too many video packets in the buffer: (4096 in 8284320 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x21C6AC                                                  
A:  46.7 V:  33.9 A-V: 12.823 ct:814.580 975/975 10%  0% 67.4% 157 0 
Too many video packets in the buffer: (4096 in 8284308 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  46.7 V:  33.9 A-V: 12.837 ct:815.580 976/976 10%  0% 67.3% 157 0 
Too many video packets in the buffer: (4096 in 8284272 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x21E1AC                                                  
A:  46.8 V:  33.9 A-V: 12.828 ct:816.580 977/977 10%  0% 67.5% 157 0 
Too many video packets in the buffer: (4096 in 8284284 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x21E62C                                                  
A:  46.8 V:  34.0 A-V: 12.842 ct:817.580 978/978 10%  0% 67.5% 157 0 
Too many video packets in the buffer: (4096 in 8284284 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  46.8 V:  34.0 A-V: 12.809 ct:818.580 979/979 10%  0% 67.4% 157 0 
Too many video packets in the buffer: (4096 in 8284284 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  46.8 V:  34.0 A-V: 12.776 ct:819.580 980/980 10%  0% 67.3% 157 0 
Too many video packets in the buffer: (4096 in 8284284 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  46.9 V:  34.1 A-V: 12.790 ct:820.580 981/981 10%  0% 67.3% 157 0 
Too many video packets in the buffer: (4096 in 8284284 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x21F3AC                                                  
A:  46.9 V:  34.1 A-V: 12.781 ct:821.580 982/982 10%  0% 67.2% 157 0 
Too many video packets in the buffer: (4096 in 8284284 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x21FCAC                                                  
A:  46.9 V:  34.1 A-V: 12.796 ct:822.580 983/983 10%  0% 67.1% 157 0 
Too many video packets in the buffer: (4096 in 8284284 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  46.9 V:  34.2 A-V: 12.762 ct:823.580 984/984 10%  0% 67.1% 157 0 
Too many video packets in the buffer: (4096 in 8284296 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2205AC                                                  
A:  47.0 V:  34.2 A-V: 12.777 ct:824.580 985/985 10%  0% 67.0% 157 0 
Too many video packets in the buffer: (4096 in 8284308 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.0 V:  34.2 A-V: 12.744 ct:825.580 986/986 10%  0% 66.9% 157 0 
Too many video packets in the buffer: (4096 in 8284296 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.0 V:  34.3 A-V: 12.758 ct:826.580 987/987 10%  0% 66.9% 157 0 
Too many video packets in the buffer: (4096 in 8284308 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2220AC                                                  
A:  47.0 V:  34.3 A-V: 12.749 ct:827.580 988/988 10%  0% 66.8% 157 0 
Too many video packets in the buffer: (4096 in 8284308 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.0 V:  34.3 A-V: 12.715 ct:828.580 989/989 10%  0% 66.7% 157 0 
Too many video packets in the buffer: (4096 in 8284308 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22252C                                                  
A:  47.1 V:  34.4 A-V: 12.730 ct:829.580 990/990 10%  0% 66.7% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.1 V:  34.4 A-V: 12.697 ct:830.580 991/991 10%  0% 66.6% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22402C                                                  
A:  47.1 V:  34.4 A-V: 12.711 ct:831.580 992/992 10%  0% 67.0% 157 0 
Too many video packets in the buffer: (4096 in 8284428 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2244AC                                                  
A:  47.2 V:  34.5 A-V: 12.726 ct:832.580 993/993 10%  0% 66.9% 157 0 
Too many video packets in the buffer: (4096 in 8284428 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.2 V:  34.5 A-V: 12.693 ct:833.580 994/994 10%  0% 66.8% 157 0 
Too many video packets in the buffer: (4096 in 8284428 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.2 V:  34.5 A-V: 12.707 ct:834.580 995/995 10%  0% 66.8% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.2 V:  34.6 A-V: 12.595 ct:837.580 998/998 10%  0% 66.8% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2268AC                                                  
A:  47.2 V:  34.7 A-V: 12.574 ct:838.580 999/999 10%  0% 66.8% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.2 V:  34.7 A-V: 12.540 ct:839.580 1000/1000 10%  0% 66.7% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x226D2C                                                  
A:  47.3 V:  34.7 A-V: 12.571 ct:840.580 1001/1001 10%  0% 66.7% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.4 V:  34.8 A-V: 12.593 ct:841.580 1002/1002 10%  0% 66.6% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x227AAC                                                  
A:  47.7 V:  34.8 A-V: 12.912 ct:842.580 1003/1003 10%  0% 66.5% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.7 V:  34.8 A-V: 12.879 ct:843.580 1004/1004 10%  0% 66.5% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2283AC                                                  
A:  47.8 V:  34.9 A-V: 12.894 ct:844.580 1005/1005 10%  0% 66.4% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x228CAC                                                  
A:  47.8 V:  34.9 A-V: 12.908 ct:845.580 1006/1006 10%  0% 66.3% 157 0 
Too many video packets in the buffer: (4096 in 8284416 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22A7AC                                                  
A:  47.9 V:  34.9 A-V: 12.923 ct:846.580 1007/1007 10%  0% 66.8% 157 0 
Too many video packets in the buffer: (4096 in 8284416 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.9 V:  35.0 A-V: 12.890 ct:847.580 1008/1008 10%  0% 66.7% 157 0 
Too many video packets in the buffer: (4096 in 8284416 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22AC2C                                                  
A:  47.9 V:  35.0 A-V: 12.904 ct:848.580 1009/1009 10%  0% 66.6% 157 0 
Too many video packets in the buffer: (4096 in 8284416 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  47.9 V:  35.0 A-V: 12.871 ct:849.580 1010/1010 10%  0% 66.6% 157 0 
Too many video packets in the buffer: (4096 in 8284416 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22BE2C                                                  
A:  48.0 V:  35.1 A-V: 12.885 ct:850.580 1011/1011 10%  0% 66.5% 157 0 
Too many video packets in the buffer: (4096 in 8284428 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.0 V:  35.1 A-V: 12.852 ct:851.580 1012/1012 10%  0% 66.4% 157 0 
Too many video packets in the buffer: (4096 in 8284428 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.0 V:  35.1 A-V: 12.819 ct:852.580 1013/1013 10%  0% 66.4% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22C2AC                                                  
A:  48.0 V:  35.2 A-V: 12.833 ct:853.580 1014/1014 10%  0% 66.3% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.0 V:  35.2 A-V: 12.800 ct:854.580 1015/1015 10%  0% 66.2% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22CBAC                                                  
A:  48.0 V:  35.2 A-V: 12.815 ct:855.580 1016/1016 10%  0% 66.2% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.0 V:  35.3 A-V: 12.781 ct:856.580 1017/1017 10%  0% 66.1% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.1 V:  35.3 A-V: 12.796 ct:857.580 1018/1018 10%  0% 66.0% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22D92C                                                  
A:  48.1 V:  35.3 A-V: 12.787 ct:858.580 1019/1019 10%  0% 66.0% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22E22C                                                  
A:  48.2 V:  35.4 A-V: 12.801 ct:859.580 1020/1020 10%  0% 65.9% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22EB2C                                                  
A:  48.2 V:  35.4 A-V: 12.816 ct:860.580 1021/1021 10%  0% 65.8% 157 0 
Too many video packets in the buffer: (4096 in 8284428 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x22FD2C                                                  
A:  48.3 V:  35.4 A-V: 12.830 ct:861.580 1022/1022 10%  0% 65.8% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2301AC                                                  
A:  48.3 V:  35.5 A-V: 12.845 ct:862.580 1023/1023 10%  0% 65.7% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.3 V:  35.5 A-V: 12.812 ct:863.580 1024/1024 10%  0% 65.7% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x230AAC                                                  
A:  48.4 V:  35.5 A-V: 12.826 ct:864.580 1025/1025 10%  0% 65.6% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.4 V:  35.6 A-V: 12.793 ct:865.580 1026/1026 10%  0% 65.5% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.4 V:  35.6 A-V: 12.808 ct:866.580 1027/1027 10%  0% 65.5% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.4 V:  35.6 A-V: 12.774 ct:867.580 1028/1028 10%  0% 65.4% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2325AC                                                  
A:  48.4 V:  35.7 A-V: 12.765 ct:868.580 1029/1029 10%  0% 65.4% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.4 V:  35.7 A-V: 12.732 ct:869.580 1030/1030 10%  0% 65.3% 157 0 
Too many video packets in the buffer: (4096 in 8284476 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.4 V:  35.7 A-V: 12.698 ct:870.580 1031/1031 10%  0% 65.2% 157 0 
Too many video packets in the buffer: (4096 in 8284488 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x232A2C                                                  
A:  48.5 V:  35.8 A-V: 12.713 ct:871.580 1032/1032 10%  0% 65.2% 157 0 
Too many video packets in the buffer: (4096 in 8284476 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.5 V:  35.8 A-V: 12.679 ct:872.580 1033/1033 10%  0% 65.1% 157 0 
Too many video packets in the buffer: (4096 in 8284488 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.5 V:  35.8 A-V: 12.694 ct:873.580 1034/1034 10%  0% 65.0% 157 0 
Too many video packets in the buffer: (4096 in 8284476 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2337AC                                                  
A:  48.6 V:  35.9 A-V: 12.685 ct:874.580 1035/1035 10%  0% 65.0% 157 0 
Too many video packets in the buffer: (4096 in 8284476 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2340AC                                                  
A:  48.6 V:  35.9 A-V: 12.699 ct:875.580 1036/1036 10%  0% 64.9% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x235BAC                                                  
A:  48.6 V:  35.9 A-V: 12.714 ct:876.580 1037/1037 10%  0% 64.9% 157 0 
Too many video packets in the buffer: (4096 in 8284416 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x236DAC                                                  
A:  48.7 V:  36.0 A-V: 12.729 ct:877.580 1038/1038 10%  0% 64.8% 157 0 
Too many video packets in the buffer: (4096 in 8284428 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.7 V:  36.0 A-V: 12.702 ct:878.580 1039/1039 10%  0% 64.7% 157 0 
Too many video packets in the buffer: (4096 in 8284428 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  48.7 V:  36.0 A-V: 12.713 ct:879.580 1040/1040 10%  0% 64.7% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.0 V:  36.1 A-V: 12.902 ct:880.580 1041/1041 10%  0% 64.6% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.0 V:  36.1 A-V: 12.917 ct:881.580 1042/1042 10%  0% 64.6% 157 0 
Too many video packets in the buffer: (4096 in 8284440 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2376AC                                                  
A:  49.0 V:  36.1 A-V: 12.907 ct:882.580 1043/1043 10%  0% 64.5% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.0 V:  36.2 A-V: 12.874 ct:883.580 1044/1044 10%  0% 64.4% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x237FAC                                                  
A:  49.1 V:  36.2 A-V: 12.889 ct:884.580 1045/1045 10%  0% 64.4% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.1 V:  36.2 A-V: 12.855 ct:885.580 1046/1046 10%  0% 64.3% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2388AC                                                  
A:  49.1 V:  36.3 A-V: 12.870 ct:886.580 1047/1047 10%  0% 64.2% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.1 V:  36.3 A-V: 12.837 ct:887.580 1048/1048 10%  0% 64.2% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.2 V:  36.3 A-V: 12.851 ct:888.580 1049/1049 10%  0% 64.1% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23962C                                                  
A:  49.2 V:  36.4 A-V: 12.842 ct:889.580 1050/1050 10%  0% 64.1% 157 0 
Too many video packets in the buffer: (4096 in 8284464 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x239F2C                                                  
A:  49.3 V:  36.4 A-V: 12.856 ct:890.580 1051/1051 10%  0% 64.0% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23B12C                                                  
A:  49.3 V:  36.4 A-V: 12.895 ct:891.580 1052/1052 10%  0% 63.9% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23B5AC                                                  
A:  49.4 V:  36.5 A-V: 12.886 ct:892.580 1053/1053 10%  0% 63.9% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.4 V:  36.5 A-V: 12.852 ct:893.580 1054/1054 10%  0% 63.8% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23BEAC                                                  
A:  49.4 V:  36.5 A-V: 12.867 ct:894.580 1055/1055 10%  0% 63.8% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23C7AC                                                  
A:  49.5 V:  36.6 A-V: 12.882 ct:895.580 1056/1056 10%  0% 63.7% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.5 V:  36.6 A-V: 12.848 ct:896.580 1057/1057 10%  0% 63.6% 157 0 
Too many video packets in the buffer: (4096 in 8284452 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.5 V:  36.6 A-V: 12.863 ct:897.580 1058/1058 10%  0% 63.6% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23D52C                                                  
A:  49.5 V:  36.7 A-V: 12.854 ct:898.580 1059/1059 10%  0% 63.5% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.5 V:  36.7 A-V: 12.820 ct:899.580 1060/1060 10%  0% 63.5% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23DE2C                                                  
A:  49.6 V:  36.7 A-V: 12.835 ct:900.580 1061/1061 10%  0% 63.4% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23E72C                                                  
A:  49.6 V:  36.8 A-V: 12.849 ct:901.580 1062/1062 10%  0% 63.3% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.6 V:  36.8 A-V: 12.816 ct:902.580 1063/1063 10%  0% 63.3% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.7 V:  36.8 A-V: 12.831 ct:903.580 1064/1064 10%  0% 63.2% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23F4AC                                                  
A:  49.7 V:  36.9 A-V: 12.821 ct:904.580 1065/1065 10%  0% 63.2% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x23FDAC                                                  
A:  49.7 V:  36.9 A-V: 12.836 ct:905.580 1066/1066 10%  0% 63.1% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2406AC                                                  
A:  49.8 V:  36.9 A-V: 12.851 ct:906.580 1067/1067 10%  0% 63.0% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.8 V:  37.0 A-V: 12.865 ct:907.580 1068/1068 10%  0% 63.0% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  49.8 V:  37.0 A-V: 12.839 ct:908.580 1069/1069 10%  0% 62.9% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x241D2C                                                  
A:  49.9 V:  37.0 A-V: 12.822 ct:909.580 1070/1070 10%  0% 62.9% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2421AC                                                  
A:  49.9 V:  37.1 A-V: 12.837 ct:910.580 1071/1071 10%  0% 62.8% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x242AAC                                                  
A:  50.0 V:  37.1 A-V: 12.852 ct:911.580 1072/1072 10%  0% 62.8% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.0 V:  37.1 A-V: 12.818 ct:912.580 1073/1073 10%  0% 62.7% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2433AC                                                  
A:  50.0 V:  37.2 A-V: 12.833 ct:913.580 1074/1074 10%  0% 62.6% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.0 V:  37.2 A-V: 12.800 ct:914.580 1075/1075 10%  0% 62.6% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.1 V:  37.2 A-V: 12.814 ct:915.580 1076/1076 10%  0% 62.5% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24412C                                                  
A:  50.1 V:  37.3 A-V: 12.805 ct:916.580 1077/1077 10%  0% 62.5% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x244A2C                                                  
A:  50.1 V:  37.3 A-V: 12.820 ct:917.580 1078/1078 10%  0% 62.4% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.1 V:  37.3 A-V: 12.786 ct:918.580 1079/1079 10%  0% 62.4% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24532C                                                  
A:  50.2 V:  37.4 A-V: 12.801 ct:919.580 1080/1080 10%  0% 62.3% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.2 V:  37.4 A-V: 12.815 ct:920.580 1081/1081 10%  0% 62.2% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x246E2C                                                  
A:  50.2 V:  37.4 A-V: 12.806 ct:921.580 1082/1082 10%  0% 62.2% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2472AC                                                  
A:  50.3 V:  37.5 A-V: 12.821 ct:922.580 1083/1083 10%  0% 62.1% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.3 V:  37.5 A-V: 12.787 ct:923.580 1084/1084 10%  0% 62.1% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.3 V:  37.5 A-V: 12.802 ct:924.580 1085/1085 10%  0% 62.0% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x248DAC                                                  
A:  50.4 V:  37.6 A-V: 12.793 ct:925.580 1086/1086 10%  0% 62.0% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.4 V:  37.6 A-V: 12.759 ct:926.580 1087/1087 10%  0% 61.9% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24922C                                                  
A:  50.4 V:  37.6 A-V: 12.774 ct:927.580 1088/1088 10%  0% 61.9% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.4 V:  37.7 A-V: 12.741 ct:928.580 1089/1089 10%  0% 61.8% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.5 V:  37.7 A-V: 12.755 ct:929.580 1090/1090 10%  0% 61.7% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.5 V:  37.7 A-V: 12.722 ct:930.580 1091/1091 10%  0% 61.7% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x249FAC                                                  
A:  50.5 V:  37.8 A-V: 12.712 ct:931.580 1092/1092 10%  0% 61.6% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24A8AC                                                  
A:  50.5 V:  37.8 A-V: 12.727 ct:932.580 1093/1093 10%  0% 61.6% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.5 V:  37.8 A-V: 12.694 ct:933.580 1094/1094 10%  0% 61.5% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24B1AC                                                  
A:  50.6 V:  37.9 A-V: 12.708 ct:934.580 1095/1095 10%  0% 61.5% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.6 V:  37.9 A-V: 12.723 ct:935.580 1096/1096 10%  0% 61.4% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24CCAC                                                  
A:  50.7 V:  37.9 A-V: 12.714 ct:936.580 1097/1097 10%  0% 61.4% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24D12C                                                  
A:  50.7 V:  38.0 A-V: 12.728 ct:937.580 1098/1098 10%  0% 61.3% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.7 V:  38.0 A-V: 12.743 ct:938.580 1099/1099 10%  0% 61.2% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.7 V:  38.0 A-V: 12.709 ct:939.580 1100/1100 10%  0% 61.2% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24EC2C                                                  
A:  50.8 V:  38.1 A-V: 12.700 ct:940.580 1101/1101 10%  0% 61.1% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  50.8 V:  38.1 A-V: 12.667 ct:941.580 1102/1102 10%  0% 61.1% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24F0AC                                                  
A:  51.0 V:  38.1 A-V: 12.872 ct:942.580 1103/1103 10%  0% 61.0% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.0 V:  38.2 A-V: 12.838 ct:943.580 1104/1104 10%  0% 61.0% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.1 V:  38.2 A-V: 12.853 ct:944.580 1105/1105 10%  0% 60.9% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.1 V:  38.2 A-V: 12.820 ct:945.580 1106/1106 10%  0% 60.9% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x24FE2C                                                  
A:  51.1 V:  38.3 A-V: 12.810 ct:946.580 1107/1107 10%  0% 60.8% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25072C                                                  
A:  51.1 V:  38.3 A-V: 12.825 ct:947.580 1108/1108 10%  0% 60.7% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.1 V:  38.3 A-V: 12.791 ct:948.580 1109/1109 10%  0% 60.7% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25192C                                                  
A:  51.2 V:  38.4 A-V: 12.830 ct:949.580 1110/1110 10%  0% 60.6% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.2 V:  38.4 A-V: 12.797 ct:950.580 1111/1111 10%  0% 60.6% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x252B2C                                                  
A:  51.2 V:  38.4 A-V: 12.787 ct:951.580 1112/1112 10%  0% 60.5% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x252FAC                                                  
A:  51.3 V:  38.5 A-V: 12.802 ct:952.580 1113/1113 10%  0% 60.5% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.3 V:  38.5 A-V: 12.817 ct:953.580 1114/1114 10%  0% 60.4% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.3 V:  38.5 A-V: 12.783 ct:954.580 1115/1115 10%  0% 60.4% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x253D2C                                                  
A:  51.3 V:  38.6 A-V: 12.774 ct:955.580 1116/1116 10%  0% 60.3% 157 0 
Too many video packets in the buffer: (4096 in 8283480 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25462C                                                  
A:  51.4 V:  38.6 A-V: 12.789 ct:956.580 1117/1117 10%  0% 60.3% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.4 V:  38.6 A-V: 12.755 ct:957.580 1118/1118 10%  0% 60.2% 157 0 
Too many video packets in the buffer: (4096 in 8283492 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x254F2C                                                  
A:  51.4 V:  38.7 A-V: 12.770 ct:958.580 1119/1119 10%  0% 60.2% 157 0 
Too many video packets in the buffer: (4096 in 8283504 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.5 V:  38.7 A-V: 12.784 ct:959.580 1120/1120 10%  0% 60.1% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.5 V:  38.7 A-V: 12.751 ct:960.580 1121/1121 10%  0% 60.1% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x256A2C                                                  
A:  51.5 V:  38.8 A-V: 12.742 ct:961.580 1122/1122 10%  0% 60.0% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.5 V:  38.8 A-V: 12.708 ct:962.580 1123/1123 10%  0% 60.0% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x256EAC                                                  
A:  51.6 V:  38.8 A-V: 12.723 ct:963.580 1124/1124 10%  0% 59.9% 157 0 
Too many video packets in the buffer: (4096 in 8283516 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.6 V:  38.9 A-V: 12.738 ct:964.580 1125/1125 10%  0% 59.8% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.6 V:  38.9 A-V: 12.704 ct:965.580 1126/1126 10%  0% 59.8% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2589AC                                                  
A:  51.6 V:  38.9 A-V: 12.695 ct:966.580 1127/1127 10%  0% 59.7% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x258E2C                                                  
A:  51.7 V:  39.0 A-V: 12.710 ct:967.580 1128/1128 10%  0% 59.7% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.7 V:  39.0 A-V: 12.676 ct:968.580 1129/1129 10%  0% 59.6% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.7 V:  39.0 A-V: 12.691 ct:969.580 1130/1130 10%  0% 59.6% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.7 V:  39.1 A-V: 12.657 ct:970.580 1131/1131 10%  0% 59.5% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x259BAC                                                  
A:  51.8 V:  39.1 A-V: 12.648 ct:971.580 1132/1132 10%  0% 59.5% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25A4AC                                                  
A:  51.8 V:  39.1 A-V: 12.663 ct:972.580 1133/1133 10%  0% 59.4% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25ADAC                                                  
A:  51.8 V:  39.2 A-V: 12.677 ct:973.580 1134/1134 10%  0% 59.4% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.8 V:  39.2 A-V: 12.644 ct:974.580 1135/1135 10%  0% 59.3% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.9 V:  39.2 A-V: 12.659 ct:975.580 1136/1136 10%  0% 59.3% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  51.9 V:  39.3 A-V: 12.625 ct:976.580 1137/1137 10%  0% 59.2% 157 0 
Too many video packets in the buffer: (4096 in 8284224 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25BB2C                                                  
A:  51.9 V:  39.3 A-V: 12.616 ct:977.580 1138/1138 10%  0% 59.2% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25C42C                                                  
A:  52.0 V:  39.3 A-V: 12.630 ct:978.580 1139/1139 10%  0% 59.1% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25CD2C                                                  
A:  52.0 V:  39.4 A-V: 12.645 ct:979.580 1140/1140 10%  0% 59.1% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.1 V:  39.4 A-V: 12.660 ct:980.580 1141/1141 10%  0% 59.0% 157 0 
Too many video packets in the buffer: (4096 in 8284188 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25E82C                                                  
A:  52.1 V:  39.4 A-V: 12.650 ct:981.580 1142/1142 10%  0% 59.0% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.1 V:  39.5 A-V: 12.617 ct:982.580 1143/1143 10%  0% 58.9% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25ECAC                                                  
A:  52.1 V:  39.5 A-V: 12.632 ct:983.580 1144/1144 10%  0% 58.9% 157 0 
Too many video packets in the buffer: (4096 in 8284188 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.2 V:  39.5 A-V: 12.646 ct:984.580 1145/1145 10%  0% 58.8% 157 0 
Too many video packets in the buffer: (4096 in 8284188 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x25FA2C                                                  
A:  52.2 V:  39.6 A-V: 12.637 ct:985.580 1146/1146 10%  0% 58.8% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x26032C                                                  
A:  52.3 V:  39.6 A-V: 12.652 ct:986.580 1147/1147 10%  0% 58.7% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.3 V:  39.6 A-V: 12.618 ct:987.580 1148/1148 10%  0% 58.7% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x260C2C                                                  
A:  52.3 V:  39.7 A-V: 12.633 ct:988.580 1149/1149 10%  0% 58.6% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.3 V:  39.7 A-V: 12.599 ct:989.580 1150/1150 10%  0% 58.6% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.4 V:  39.7 A-V: 12.614 ct:990.580 1151/1151 10%  0% 58.5% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.4 V:  39.8 A-V: 12.581 ct:991.580 1152/1152 10%  0% 58.5% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2619AC                                                  
A:  52.4 V:  39.8 A-V: 12.571 ct:992.580 1153/1153 10%  0% 58.4% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2622AC                                                  
A:  52.4 V:  39.8 A-V: 12.586 ct:993.580 1154/1154 10%  0% 58.4% 157 0 
Too many video packets in the buffer: (4096 in 8284212 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x262BAC                                                  
A:  52.5 V:  39.9 A-V: 12.601 ct:994.580 1155/1155 10%  0% 58.3% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.5 V:  39.9 A-V: 12.594 ct:996.580 1157/1157 10%  0% 58.2% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x264FAC                                                  
A:  52.5 V:  40.0 A-V: 12.573 ct:997.580 1158/1158 10%  0% 58.2% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.6 V:  40.0 A-V: 12.581 ct:998.580 1159/1159 10%  0% 58.1% 157 0 
Too many video packets in the buffer: (4096 in 8284188 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:  52.7 V:  40.0 A-V: 12.638 ct:999.580 1160/1160 10%  0% 58.1% 157 0 
Too many video packets in the buffer: (4096 in 8284188 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x265D2C                                                  
A:  52.7 V:  40.1 A-V: 12.607 ct:1000.580 1161/1161 10%  0% 58.0% 157 0 
Too many video packets in the buffer: (4096 in 8284188 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x2661AC                                                  
A:  52.7 V:  40.1 A-V: 12.621 ct:1001.580 1162/1162 10%  0% 58.0% 157 0 
Too many video packets in the buffer: (4096 in 8284188 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Broken frame at 0x266AAC                                                  
A:  52.8 V:  40.1 A-V: 12.636 ct:1002.580 1163/1163 10%  0% 57.9% 157 0 
Too many video packets in the buffer: (4096 in 8284200 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.


MPlayer interrupted by signal 2 in module: sleep_timer
A:  52.8 V:  40.2 A-V: 12.603 ct:1003.580 1164/1164 10%  0% 57.9% 157 0 
Exiting... (Quit)

---

### Post by newbuntu81 on 2011-02-27
> **newbuntu81 said:**
> Nice information.  I tried this and couldn't get anything to show, but then realized that I was trying to fine tune channel 2 "55.25".

I clicked your link and changed to channel 3, "61.25" and am now showing video and can hear audio--so the driver works in analog NTSC for me in mplayer!  It's very choppy though.
<Truncated>


So I just tried this again, channel 3 worked great for about 45 seconds then got choppy.  I kept my viewing short so I could view the logs.  Hope this helps someone.

Oh and, the warnings do say my system is too slow.  I'm running the commands on my primary mythbuntu backend, so as long as I get something I'm ok with that.  I hadn't planned to play anything long-term on my primary backend.

_**Logs:**_
michael@michael-OptiPlex-GX280:~$ v4l2-ctl -d /dev/video1 --set-freq=61.250
Frequency set to 980 (61.250000 MHz)
michael@michael-OptiPlex-GX280:~$ mplayer /dev/video1
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team

Playing /dev/video1.
[COLOR=Red]Cannot seek backward in linear streams![/COLOR]
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
[COLOR=Black]Cannot seek backward in linear streams![/COLOR]
Seek failed
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  5000.0 kbps (625.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[COLOR=Red][VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.[/COLOR]
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
A:   5.2 V:   3.7 A-V:  1.428 ct: -0.702  72/ 72 13%  1% 143.9% 50 0 

           ************************************************
[COLOR=Red]           **** Your system is too SLOW to play this!  ****[/COLOR]
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
[COLOR=Red]Read DOCS/HTML/en/video.html for tuning/speedup tips.[/COLOR]
If none of this helps you, read [COLOR=Red]DOCS/HTML/en/bugreports.html.[/COLOR]

---

### Post by newbuntu81 on 2011-02-27
> **newbuntu81 said:**
> So I just tried this again, channel 3 worked great for about 45 seconds then got choppy.  I kept my viewing short so I could view the logs.  Hope this helps someone.



I tried again, this time looking at analog NTSC channel 91 with 625.25.  It worked fine, not choppy.  I watched for several minutes.

I reread through some of the posts and am curious if I have mythtv set up backwards--which would explain why I still can't record in it.

Before I change anything, I want to see if I can use both analog NTSC tuners at the same time.

_**Test A: Commands:**_
<Terminal 1>
michael@michael-OptiPlex-GX280:~$ [COLOR=Blue]v4l2-ctl -d /dev/video0 --set-freq=625.25[/COLOR]
Frequency set to 10004 (625.250000 MHz)
michael@michael-OptiPlex-GX280:~$ [COLOR=Blue]mplayer /dev/video0[/COLOR]


<Terminal 2>
michael@michael-OptiPlex-GX280:~$ [COLOR=Blue]v4l2-ctl -d /dev/video1 --set-freq=61.250[/COLOR]
Frequency set to 980 (61.250000 MHz)
michael@michael-OptiPlex-GX280:~$ [COLOR=Blue]mplayer /dev/video1[/COLOR]

_**Test A Results:**_

Video0: Success, played analog NTSC channel 91 as requested

Video1: Success, played analog NTSC channel 03 as requested...and at the same time as Video0

Comments: Looks like the drivers ([COLOR=Blue]NXP7164-2010-03-10.1.fw[/COLOR]) work fine with Mythbuntu 10.10, now to figure out how to get MythTV to function with both analog NTSC tuners.  I wanted both tuners to be analog NTSC anyway, so this is great news for me!

_**My current MythTV Setup, both tuners used as analog NTSC:**_
[B]
Card 0:[/B] [COLOR=Blue]Analog V4L Capture Card[/COLOR]
Video Device: [COLOR=Blue]/dev/video0[/COLOR]
VBI Device: /dev/vbi0
Audio: (Default) ALSA  default
Sampling Rate: 48000
Default Input: Tuner

**Card 1:** [COLOR=Blue]Analog V4L Capture Card[/COLOR]
Video Device: [COLOR=Blue]/dev/video1[/COLOR]
VBI Device: /dev/vbi1
Audio: (Default) ALSA  default
Sampling Rate: 48000
Default Input: Tuner

_**If you are using one tuner as ATSC Digital, and one as NTSC Analog, I believe you would want to: **_

1. Set up the digital tuner first as an **DVB DTV capture card (v3.x)**, manually enter the video device to [COLOR=Blue]/dev/dvb/adapter0/frontend0[/COLOR], then

2. Set up the analog tuner next as **Analog V4L Capture Card**, manually enter the video device to[COLOR=Blue] /dev/video1[/COLOR].  This does differ from what Dnobes said because the newer driver provides additional options and allows the card to show up as an "Hauppauge HVR 2250".   However, I'm beginning to wonder if I should be using the **IVTV MPEG-2 Encoder** option instead of **Analog V4L Capture Card** in Mythtv. (See above for my setup).  

_**Dnobes Quote:**_
"To setup an analogue tuner all you need to do is in the MythTV backend  setup of the Capture Card. When setting the card type as &#8220;**IVTV MPEG-2  Encoder**&#8221; the PVR-2250 card does not show-up/auto-fill. So just manually  set the "Video Device" to "/dev/video1".  This is assuming you setup the  digital card already, otherwise you can set it to "/dev/video0", BUT if  you do, then make sure that if you setup a digital tuner it does not  use the first tuner..

I setup my digital tuner first:
/dev/dvb/adapter0/frontend0

Then I setup my analogue tuner:
/dev/video1"

---

### Post by pluto7777 on 2011-02-27
At what point does video0 get created? I have all the firmware files in place. I don't see video0 or vbi0. Do I need to link them to something? Do I need to install something else besides the firmware? I'm using Ubuntu 10.10 btw

---

### Post by newbuntu81 on 2011-03-02
How do I find out what versions I'm running? In Mythbuntu 10.10, you can determine it for both the frontend AND the backend.

_**Kernel version:**_
uname -a

_**Kernel Output:**_
2.6.35-25-generic

_**Frontend Command:**_
mythfrontend --version
[B]
_Frontend Output:_
[/B]MythTV Version   : v0.24-195-gbbfb6b0
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0[B]

_Backend Command:_
[/B]mythbackend --version

[B]_Backend Output:_
[/B]MythTV Version   : v0.24-195-gbbfb6b0
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0

If these commands do not work, try:
dpkg - l |grep mythtv

---

### Post by newbuntu81 on 2011-03-05
Strangely enough, I also have an HVR 950q and am at the very same spot in Mythbuntu 10.10, same kernel and such as above, different box.

I can record ATSC digital over the air in mythtv, but cannot record NTSC analog cable in mythtv.  However, I can use the mplayer commands to show NTSC analog cable.  So it looks like the drivers are fine, but maybe the issue is with Mythtv 0.24?

---

### Post by newbuntu81 on 2011-03-05
[U][B]To Show Video Devices and Ports:

[/B]ls /dev/video*[/U]

Output:
/dev/video0

_ls -l /dev/v4l/by-path_

Output:total 0
lrwxrwxrwx 1 root root 12 2011-03-04 09:18 pci-0000:00:1d.7-video-index0 -> ../../video0[U][B]

More information on 2250 Drivers: Package updates from Stot[/B][/U]h
[http://kernellabs.com/hg/~stoth/saa7164-v4l/file/ba3654171444]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l/file/ba3654171444")
[U][B]

To Update Firefox:[/B][/U][INDENT] sudo add-apt-repository  ppa:ubuntu-mozilla-security/ppa
 sudo apt-get update


 [/INDENT]

---

### Post by LeTanc on 2011-03-26
> **newbuntu81 said:**
> How do I find out what versions I'm running? In Mythbuntu 10.10, you can determine it for both the frontend AND the backend.

_**Kernel version:**_
uname -a

_**Kernel Output:**_
2.6.35-25-generic

_**Frontend Command:**_
mythfrontend --version
[B]
_Frontend Output:_
[/B]MythTV Version   : v0.24-195-gbbfb6b0
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0[B]

_Backend Command:_
[/B]mythbackend --version

[B]_Backend Output:_
[/B]MythTV Version   : v0.24-195-gbbfb6b0
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0

If these commands do not work, try:
dpkg - l |grep mythtv


newbuntu81,

Thanks for your posts, they really helped me!  I was making pretty good progress by following various posts and including the new definitions for the usb_buffer_free and usb_buffer_alloc.  However, nowhere else did I find instructions for the: **'struct usb_device' has no member named 'autosuspend_disabled' **error.  

I was finally able to get everything to compile and verified that the driver & firmware was installed.  I was even able to view analog channels with mplayer.  The one thing that boggled my mind was that the MythBackend scan wasn't able to find any of the anlog channels even though I was able to view them with mplayer.  

After noticing that I was on version 0.23, I upgraded to MythTV version 0.24 and lo-and-behold it all worked!!!

I'm now able to view analog stations without a hitch.

Thanks newbuntu & everybody else for your posts!

---

### Post by Kr0nZ on 2011-04-06
Thanks soo much newbuntu81
I was unable to get the driver to compile for the 2.6.35 kernel but after following your instruction and updating to mytvtv 0.24. I was able to scan for channels in mythtv(just make sure you have ivtv mpeg selected in the tuner setup page, and not the v4l analog)

I was unable to test the sound in MythTV as my audio-over-hdmi isnt working by default in MythTV (I can force it in mplayer, but it plays really choppy and the get errors like in post [#85]("http://ubuntuforums.org/showpost.php?p=10501606&postcount=85") of this thread), and my analog(?)-audio(green speaker jack on the back) doesn't work at all

Edit: Just been fiddling with it for the last few hours, now I got the sound-over-hdmi and my mediagate MG-IR02BK remote working
So I now have a fully functional mythbuntu box, now to set some recordings and see how well it performs!

---

### Post by katumba1 on 2011-04-07
newbuntu81, do you mind posting the steps you took to get the analog side of your 2250 working?

I have the HD side working fine on mine. I've read through all these posts and tried to follow everything...  Not working.  This is my output from dmesg | grep saa7164:

[    9.548590] saa7164 driver loaded
[    9.548631] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.549479] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR                                      2250 [card=7,autodetected]
[    9.549485] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency:                                       0, mmio: 0xfd400000
[    9.549490] saa7164 0000:02:00.0: setting latency timer to 64
[    9.712282] saa7164_downloadfirmware() no first image
[    9.712337] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa71                                      64-1.0.3.fw)
[    9.837478] saa7164_downloadfirmware() firmware read 3978608 bytes.
[    9.837480] saa7164_downloadfirmware() firmware loaded.
[    9.837487] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[    9.837493] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    9.837494] saa7164_downloadfirmware() BSLSize = 0x0
[    9.837495] saa7164_downloadfirmware() Reserved = 0x0
[    9.837496] saa7164_downloadfirmware() Version = 0x51cc1
[   16.692029] saa7164_downloadimage() Image downloaded, booting...
[   16.796028] saa7164_downloadimage() Image booted successfully.
[   18.916027] saa7164_downloadimage() Image downloaded, booting...
[   20.580022] saa7164_downloadimage() Image booted successfully.
[   20.616132] saa7164[0]: Hauppauge eeprom: model=88061
[   21.248916] DVB: registering new adapter (saa7164)
[   24.145381] DVB: registering new adapter (saa7164)
[   25.872553] Modules linked in: tda18271 s5h1411 snd_hda_codec_nvhdmi nvidia(P                                      ) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq                                      _midi_event snd_seq snd_timer snd_seq_device snd joydev saa7164 soundcore ati_ag                                      p snd_page_alloc i2c_piix4 serio_raw dvb_core k10temp tveeprom agpgart lp parpor                                      t usbhid hid floppy pata_atiixp ahci r8169 mii libahci


Any help would be greatly appreciated! Kat

---

### Post by katumba1 on 2011-04-07
FYI. Got this fixed w/ help from guys on the IRC. Just needs a mainline kernel update.

Working great! Thanks!

---

### Post by markuswells on 2011-06-09
ok, I stepped away from this for a little while but am going to try again using 11.04.

Anyone actually got this card working? analog and digital both on cable TV (not composite) installed from scratch and using the mythtv thats available by default in 11.04 (.24 I think)

---

### Post by rsc_ on 2011-06-28
> **markuswells said:**
> ok, I stepped away from this for a little while but am going to try again using 11.04.

Anyone actually got this card working? analog and digital both on cable TV (not composite) installed from scratch and using the mythtv thats available by default in 11.04 (.24 I think)

I am using the 2250 for a different purpose but have an interest in improved analog support.

I am using Ubuntu 11.04 2.6.38-8-server x86_64 with the 2250. I use it to capture a local analog cable channel and encode it to Flash using FFmpeg. I currently don't have any digital channels so I can't say if it is working for digital. Analog works but FFmpeg stops unexpectedly at random times. I noticed the "[2190290.710912] No pack at 0x2800" type messages in syslog which is what led me here.

---

### Post by jorandal on 2011-07-18
> **newbuntu81 said:**
> [QUOTE=newbuntu81;10441602][QUOTE=newbuntu81;10441589][QUOTE=newbuntu81;10441487][QUOTE=newbuntu81;10441391][QUOTE=newbuntu81;10441346][QUOTE=newbuntu81;10441098][QUOTE=newbuntu81;10440736][QUOTE=newbuntu81;10438525]--------------------------------------------------------------

Ok, so the card is installed, using the correct firmware.  When I go into the MythTV backend I can set it up using IVTV and it actually shows the card type now, which is a nice surprise.  Don't forget to set the type to "tuner".

I scanned for channels and it listed some but did not populate a channel name (i.e. NBC).

Currently, I do not have any picture except a blue screen.  I have seen that others were having this issue through November 2010--I have not seen any updates since that.

Others seemed to mention that the AV (Composite) jacks work just fine, so if worst comes to worst I could use that...but I really was hoping to take advantage of the dual tuner via coax.  

Any ideas anyone?
I had this same issue and was able to correct it. Now i am able to watch either analog or digital on both tuners. What i did to correct it was go into the backend setup and select your digital tuner "dvb dtv" select "recording options" i changed the max recordings field to 1, removed the selection "Use DVB card for active EIT scan" and selected "Open DVB card on demand" once i saved these settings both tuners were able to switch from analog to digital etc. I'm not an expert or anything but from what i gather the digital tuner was being held open by the active EIT scan causing the blue screen when you attempt to view analog. Hope this helps as this forum has helped me a great deal!

---

### Post by jorandal on 2011-07-18
I didn't see anyone report they had everything up and running with both analog and digital on both tuners yet; so i wanted to quickly write up how i got everything working. This worked for me so hopefully it will for everyone else as well. I did a fresh install of mythbuntu 11.04 which i believe already has the drivers for the hvr-2250. I needed to get the firmware i basically followed the same steps as post #2 but see below

download the firmware

wget [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)

move it to /lib/firmware

sudo cp *fw /lib/firmware

sudo reboot



now i was able to go into my backend setup and configure my capture cards. 

First I setup my digital side by selecting "DVB DTV capture card" as the type
I went into "Recording Options" and changed the Max recordings field to 1.
Also i selected "Open DVB card on demand" and removed the check from "Use DVB card for active EIT scan" 

I should mention this next part may be different for me since i am going to manually merge my digital channels in to override the analog ones so i have two sources the on i am setting up here is just a dummy to allow me to scan.

I created a source, I selected "Preform EIT scan", and I also changed my Channel frequency table to us-cable

Now go into your input connections and select your digital tuner "DVB :/dev/dvb/adapter0/frontend0" for me. Make sure you have the source selected that was just created. 

I preformed a scan for channels. In my area "Florida with Mediacom" I used "cable" for the frequency table and "Qam 256" for the modulation.

The last step here i feel is important after the scan completes on the second page in the input connections you need to create a new input group. I named mine tuner0 and tuner1; But it doesn't really matter as long as you keep both the analog and digital inputs together for each tuner.
ex DVB_/dev/dvb/adapter0/frontend0 and /dev/video0 both belong to the group tuner0
while DVB_/dev/dvb/adapter1/frontend1 and /dev/video1 both belong to the group tuner1

from here I went on to setup my analog tuners "/dev/video0 and /dev/video1" and a second source for my guide data from schedules direct which I used for the analog inputs.

Once again I hope this works the same for everyone, These forums are always helpful for me hopefully I can return the favor!

---

### Post by cncook001 on 2011-08-10
Thankyou jorandal, after following your mythtv tips I finally have analog working on my 2250 card.  I've had the firmware in place for a while but never managed to record in Mythtv.

This step seems to be critical for the "blue screen" problem I had:

>Also i selected "Open DVB card on demand" and removed the check from "Use DVB card for active EIT scan" 

Thanks again,

Craig

---

### Post by cheryljosie on 2012-02-18
Well after using this analog/digital driver with 11.10 for however long the distro has been available, I have found the following:

1) The 2250 is a relatively insensitive tuner, with similar sensitivity to the old DirecTV tuners from 10 years ago or so, including the original 80GB high-def dvr version. Any modern dig/analog converter box blows the 2250 tuner away.

2) The analog driver hangs mythbackend if the backend tries to access the analog portion of a tuner while the automated program scan is active on the digital half. When the analog half of that tuner is accessed in livetv, the frontend hangs, times out, and loses contact with the backend until the backend is stopped and restarted.

However, if the digital half of a tuner is active in livetv when the analog half begins a programmed recording, the frontend flashes a warning notice and asks whether to start the programmed analog recording and switch livetv to the other digital tuner (if available), or to watch the analog recording in livetv mode (which also places the analog recording in the livetv directory with the livetv files), or to stop watching livetv altogether.

Similarly, if attempting to start analog livetv while the digital half is doing a program scan on eit, the backend also hangs.

The mutually exclusive properties of mythtv configuration seem not to inhibit the livetv or programmed activity on the 2250 analog tuner while the digital is in use for automated program scans, causing conflicts with the digital tuner and hanging the backend. It does seem to inhibit the digital half from stepping on the analog with eit though.

One way to avoid the hang is to switch directly from digital half on livetv to analog half on livetv. Another way to avoid the hang is to set up an analog recording and keep the digital half of the tuner active in livetv while the analog recording starts. The default behavior is to terminate livetv so it is save to leave it unattended while starting analog recording as long as digital eit is inhibited by digital livetv.

A third way to avoid the hang is to disable digital eit program scan entirely when using analog tv for either livetv or recording. This does cause a problem with the digital recording function however because it means that tuner is unavailable to scan channels and any recurring or one-time advance programming you are expecting to pick up on scan will not be available to that tuner if it does not get scanned. I am not sure if the cross-tuner sharing of scanned program information is working or not, so I do not know if one tuner can scan while the other is used occasionally for analog, but either way it can cause a problem because even if sharing is working, one tuner cannot scan and the other may be busy recording when it needs to scan.

3) Mythtv recordings made over-the air, at least with my 2250, are unable to be viewed with vlc or transcoded with handbrake. Vlc opens the first frame and hangs, and handbrake terminates the transcode after 5 minutes of stream has been processed. mplayer is able to play back (decode) the mythtv recordings, which probably explains why mythtv can play them back (I seem to recall it uses mplayer anyway), but not vlc and not handbrake.

This causes a storage problem. The only way to transcode is using mythtranscode and this somehow functions even though I have not been able to get handbrake to work. I am just now experimenting with ffmpeg but so far no luck. The program streams seem to be corrupted somehow. Even after mythtranscode is done with it vlc still cannot play it usually, so eventually I gave up on mythtranscode.

I have had better luck with the analog tuner. Although there are no analog channels here, I have managed to use the composite input to capture vhs and that will play back with vlc and it will transcode with handbrake. Maybe the internal hardware encoder on the 2250 is standard-compliant whereas the linux driver's handling of the broadcast program stream is not? I tried using the included Windows wintv program to capture some livetv in windows and that seemed to play ok in linux and windows versions of vlc.

ps I am using mythtvfs (fuse - filesystem in user space) to access the mythtv recordings in Nautilus and with handbrake. It renames the files with additional data from the mysql server and mounts a directory full of links with very long names that include the full program description, date, time etc. I did try direct file access too but that did not work either.

It would be nice to find out what is wrong with the digital capture so I can find a way to transcode it into mp4 and save some space. I did not care for the mythtranscode method, the nuv container is not compatible with anything.

---

### Post by cheryljosie on 2012-02-18
Well after using this analog/digital driver with 11.10 for however long the distro has been available, I have found the following:

1) The 2250 is a relatively insensitive tuner, with similar sensitivity to the old DirecTV tuners from 10 years ago or so, including the original 80GB high-def dvr version. Any modern dig/analog converter box blows the 2250 tuner away.

2) The analog driver hangs mythbackend if the backend tries to access the analog portion of a tuner while the automated program scan is active on the digital half. When the analog half of that tuner is accessed in livetv, the frontend hangs, times out, and loses contact with the backend until the backend is stopped and restarted.

However, if the digital half of a tuner is active in livetv when the analog half begins a programmed recording, the frontend flashes a warning notice and asks whether to start the programmed analog recording and switch livetv to the other digital tuner (if available), or to watch the analog recording in livetv mode (which also places the analog recording in the livetv directory with the livetv files), or to stop watching livetv altogether.

Similarly, if attempting to start analog livetv while the digital half is doing a program scan on eit, the backend also hangs.

The mutually exclusive properties of mythtv configuration seem not to inhibit the livetv or programmed activity on the 2250 analog tuner while the digital is in use for automated program scans, causing conflicts with the digital tuner and hanging the backend. It does seem to inhibit the digital half from stepping on the analog with eit though.

One way to avoid the hang is to switch directly from digital half on livetv to analog half on livetv. Another way to avoid the hang is to set up an analog recording and keep the digital half of the tuner active in livetv while the analog recording starts. The default behavior is to terminate livetv so it is save to leave it unattended while starting analog recording as long as digital eit is inhibited by digital livetv.

A third way to avoid the hang is to disable digital eit program scan entirely when using analog tv for either livetv or recording. This does cause a problem with the digital recording function however because it means that tuner is unavailable to scan channels and any recurring or one-time advance programming you are expecting to pick up on scan will not be available to that tuner if it does not get scanned. I am not sure if the cross-tuner sharing of scanned program information is working or not, so I do not know if one tuner can scan while the other is used occasionally for analog, but either way it can cause a problem because even if sharing is working, one tuner cannot scan and the other may be busy recording when it needs to scan.

3) Mythtv recordings made over-the air, at least with my 2250, are unable to be viewed with vlc or transcoded with handbrake. Vlc opens the first frame and hangs, and handbrake terminates the transcode after 5 minutes of stream has been processed. mplayer is able to play back (decode) the mythtv recordings, which probably explains why mythtv can play them back (I seem to recall it uses mplayer anyway), but not vlc and not handbrake.

This causes a storage problem. The only way to transcode is using mythtranscode and this somehow functions even though I have not been able to get handbrake to work. I am just now experimenting with ffmpeg but so far no luck. The program streams seem to be corrupted somehow. Even after mythtranscode is done with it vlc still cannot play it usually, so eventually I gave up on mythtranscode.

I have had better luck with the analog tuner. Although there are no analog channels here, I have managed to use the composite input to capture vhs and that will play back with vlc and it will transcode with handbrake. Maybe the internal hardware encoder on the 2250 is standard-compliant whereas the linux driver's handling of the broadcast program stream is not? I tried using the included Windows wintv program to capture some livetv in windows and that seemed to play ok in linux and windows versions of vlc.

ps I am using mythtvfs (fuse - filesystem in user space) to access the mythtv recordings in Nautilus and with handbrake. It renames the files with additional data from the apache server and mounts a directory full of links with very long names that include the full program description, date, time etc. I did try direct file access too but that did not work either.

It would be nice to find out what is wrong with the digital capture so I can find a way to transcode it into mp4 and save some space. I did not care for the mythtranscode method, the nuv container is not compatible with anything.

---

### Post by RideMan on 2012-03-12
I just set up one of these cards in a second Mythbuntu box (glutton for punishment, I guess?)...

I loaded the firmware, I configured the card as an IVTV MPEG encoder, and when I went to "Watch TV" I got a blue screen and static.

Lots of reconfiguring and head scratching later, I finally got a brilliant idea.

I'm connected to a US-CATV system.  It finally occurred to me to see what I would get on Channel 7 instead of Channel 51.  Sure enough, I got good video.

For some reason, even though I had performed channel scans in the "us-cable" range, even though the system default frequency range is set for "us-cable", for some reason the card was scanning in the broadcast band.  What I finally had to do was to set the frequency override on the card config in one of the three capture card menus in backend setup to "us-cable" instead of "default"...even though the system-wide frequency table ("default") was set to us-cable.  That finally switched the card to use the CATV frequencies instead of the broadcast frequencies, and now everything works.

(in case you're wondering:  Most of the CATV channels 14-up are actually located between broadcast channels 6-7 and between channels 13-14.  Broadcast channels 14-65 are in a band well above most of the CATV channels.)

---

### Post by lucgallant on 2012-11-03
Well, sorry for reviving a dead thread here, but I really need some help and it's related to this thread.

I'm running Mythbuntu 12.04.1 with mythtv version 2:0.25.2+fixes.2012. I just installed it one week ago using the download.

I just got my tuner tonight and I'm trying to get it to work as an analog cable tuner. I've got the coax plugged in to the TV IN jack. It's the Hauppauge HVR-2250.

I followed the instructions from another post and downloaded the firmware (NXP7164-2010-03-10.1.fw) to the /lib/firmware/3.2.0-32-generic folder.

When I boot up, dmesg shows that the firmware loaded fine and that the following devices were created:


```
htpc@gallant-HTPC:/lib/firmware/3.2.0-32-generic$ dmesg | grep saa
[   17.000642] saa7164 driver loaded
[   17.000817] saa7164 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.004420] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   17.004436] saa7164[0]/0: found at 0000:0b:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfbc00000
[   17.004454] saa7164 0000:0b:00.0: setting latency timer to 64
[   17.164532] saa7164_downloadfirmware() no first image
[   17.164554] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   18.106466] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   18.106475] saa7164_downloadfirmware() firmware loaded.
[   18.106505] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   18.106519] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   18.106526] saa7164_downloadfirmware() BSLSize = 0x0
[   18.106531] saa7164_downloadfirmware() Reserved = 0x0
[   18.106537] saa7164_downloadfirmware() Version = 0x1661c00
[   24.972079] saa7164_downloadimage() Image downloaded, booting...
[   25.076077] saa7164_downloadimage() Image booted successfully.
[   27.128035] saa7164_downloadimage() Image downloaded, booting...
[   29.000083] saa7164_downloadimage() Image booted successfully.
[   29.048528] saa7164[0]: Hauppauge eeprom: model=88061
[   29.750057] DVB: registering new adapter (saa7164)
[   32.651210] DVB: registering new adapter (saa7164)
[   32.653432] saa7164[0]: registered device video0 [mpeg]
[   32.884147] saa7164[0]: registered device video1 [mpeg]
[   33.095443] saa7164[0]: registered device vbi0 [vbi]
[   33.095746] saa7164[0]: registered device vbi1 [vbi]

```

So I added the tuner cards as MPEG-2 Encoder cards in mythtvbackend setup, they both enumerated as /dev/video0 and /dev/video1. I then created a Video Source using my SchedulesDirect account.

I then go into the Input Connections screen and edit both tuners to use my newly created Video Source. Problem is, when I do a Scan for Channels on us-cable (I changed all the 'default' channel frequency tables in other menus to us-cable as well), it scans all the channels and the word "Locked" is beside the channel number. The signal strength never moves and the scan % only goes to 5%. It ends after 125 channels with "Failed to find any channels".

I did have some TV previously playing in mplayer but now it shows a blue screen.

I tried some things from other posts such as setting up a digital tuner and an analog tuner, making them part of a group, etc, but to no avail. I don't see any recent posts on this issue so I was hoping that was now working out of the box.

Any help would be greatly appreciated, things have gone smooth till now with the rest of the hardware and I can taste success. Thanks in advance,

Edit: To add to this, here is the output of mythbackend when I do try and scan for channels. The output is the same whether I've got an analog/digital input group configured or not.

```

Nov  3 10:08:02 gallant-HTPC mythtv-setup[2920]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Nov  3 10:08:09 gallant-HTPC mythtv-setup[2920]: W CoreContext diseqc.cpp:359 (Load) DiSEqCDevTree: No device tree for cardid 3
Nov  3 10:08:44 gallant-HTPC mythtv-setup[2920]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video1): SetInputAndFormat(2, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Nov  3 10:08:56 gallant-HTPC mythtv-setup[2920]: E Scanner dtvmultiplex.cpp:325 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000
Nov  3 10:09:21  mythtv-setup[2920]: last message repeated 16 times
Nov  3 10:09:21 gallant-HTPC mythtv-setup[2920]: I CoreContext channelscan/channelimporter.cpp:40 (Process) ChanImport: No channels to process..

```

---

### Post by lucgallant on 2012-11-03
Well, apparently there's no point in scanning channels with analog. All I had to do was pull them from listings (it's the button beside scan channels) and then set a starting channel instead of "Please add", and it works just fine.

Still have to work out some performance issues but I did not need to play around with Tuner groups, etc... Just configure both MPEG 2 tuners and it goes.

---

### Post by smaring on 2013-02-10
I've slapped a Hauppauge HVR-2250 into an upgraded Mythbuntu box and have been trying to get it to work with my analog cable service for well over a month.  The wife really wanted a DVR for xmas ... so I'm pretty well in the doghouse until I get this working.

I've been trying to follow the forum discussion here, but so far no luck.

```

root@dvr:~# dmesg | grep ssa
[    0.651554] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
root@dvr:~# dmesg | grep saa
[    3.402521] saa7164 driver loaded
[    3.402562] saa7164 0000:04:00.0: enabling device (0000 -> 0002)
[    3.402570] saa7164 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.404085] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[    3.404091] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 19, latency: 0, mmio: 0xf7800000
[    3.404099] saa7164 0000:04:00.0: setting latency timer to 64
[    3.568277] saa7164_downloadfirmware() no first image
[    3.568289] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    3.579954] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    3.579956] saa7164_downloadfirmware() firmware loaded.
[    3.579961] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    3.579967] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    3.579968] saa7164_downloadfirmware() BSLSize = 0x0
[    3.579969] saa7164_downloadfirmware() Reserved = 0x0
[    3.579970] saa7164_downloadfirmware() Version = 0x1661c00
[   10.213133] saa7164_downloadimage() Image downloaded, booting...
[   10.316891] saa7164_downloadimage() Image booted successfully.
[   13.038694] saa7164_downloadimage() Image downloaded, booting...
[   14.906531] saa7164_downloadimage() Image booted successfully.
[   14.952645] saa7164[0]: Hauppauge eeprom: model=88061
[   15.550637] DVB: registering new adapter (saa7164)
[   18.468926] DVB: registering new adapter (saa7164)
[   18.469172] saa7164[0]: registered device video0 [mpeg]
[   18.699043] saa7164[0]: registered device video1 [mpeg]
[   18.909840] saa7164[0]: registered device vbi0 [vbi]
[   18.909954] saa7164[0]: registered device vbi1 [vbi]

```


I CAN get a nice clean signal if I do this:

v4l2-ctl -d /dev/video1 --set-freq=55.250
mplayer /dev/video1


the output looks like this:

```

user@dvr:/var/log/mythtv$ v4l2-ctl -d /dev/video1 --set-freq=55.250
Frequency set to 884 (55.250000 MHz)
user@dvr:/var/log/mythtv$ mplayer /dev/video1
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video1.
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
...
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  5000.0 kbps (625.0 kbyte/s)
Load subtitles in /dev/
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[mp2float @ 0x7f18b85c4540]Header missing
AUDIO: 48000 Hz, 2 ch, floatle, 384.0 kbit/12.50% (ratio: 48000->384000)
Selected audio codec: [ffmp2float] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio)
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 720x540 Planar YV12 
A:   5.5 V:   5.1 A-V:  0.366 ct: -0.370 113/113  7%  1% 91.5% 58 0 


           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  11.5 V:  11.0 A-V:  0.539 ct: -0.645 290/290  5%  1% 92.6% 194 0 

Exiting... (Quit)

```


The things that strike me odd there are:

Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
and
Your system is too SLOW to play this!

This a brand new mobo, cpu, 24GB of ram, and the OS is running off a SSD.  This box is NOT "SLOW" ... and doesn't this card have a hardware based MPEG-2 coder?

My backend config looks like this:

```

Capture Cards:
   [V4L:/dev/video0] - /dev/vbi0; ALSA:default @ 48000
   [V4L:/dev/video1] - /dev/vbi1; ALSA:default @ 48000
   [MPEG:/dev/video0] - /dev/vbi0
   [MPEG:/dev/video1] - /dev/vbi1
   [DVB:/dev/dvb/adapter0/frontend0] - DVB DTV capture card (v3.x); Samsung S5H1411QAM/ ATSC
   [DVB:/dev/dvb/adapter1/frontend0] - DVB DTV capture card (v3.x); Samsung S5H1411QAM/ ATSC

Recording Profiles
   Software Encoders (v4l based) - both default & Live TV: 720X480; tried both RTjpeg & MPEG-4; mp3 @ 48000
   MPEG-2 Encoders (PVR-x50,PVR-500) - both default & Live TV: 720X480 ... everything else default
   Hardware DVB Encoders - defaults
   Transcoders - defaults

```

I have entered my SchedulesDirect.org account info and "retrieve listings" seems to work fine ... properly resolving "Brighthouse Pasco" and getting the channel info

```

Input Connections
   [V4L:/dev/video0] (tuner) -> Brighthouse Pasco
   [V4L:/dev/video1] (tuner) -> Brighthouse Pasco
   [MPEG:/dev/video0] (tuner) -> Brighthouse Pasco
   [MPEG:/dev/video1] (tuner) -> Brighthouse Pasco
   [DBV:/dev/dvb/adapter0/frontend0] (DBVInput) -> Brighthouse Pasco
   [DBV:/dev/dvb/adapter1/frontend0] (DBVInput) -> Brighthouse Pasco

```

"scan for channels" never seems to work, but "fetch channels from listing source" does, and sets the "starting channel" to "3"

I have populated the database after making all these settings

on startup of the backend I get ...

```

Feb 10 08:52:10 dvr mythbackend[1921]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25.3-33-g1d4d50b] www.mythtv.org
Feb 10 08:52:10 dvr mythbackend[1921]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Feb 10 08:52:10 dvr mythbackend[1921]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Feb 10 08:52:10 dvr mythbackend[1921]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Feb 10 08:52:10 dvr mythbackend[1921]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Feb 10 08:52:10 dvr mythbackend[1921]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Feb 10 08:52:10 dvr mythbackend[1921]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Feb 10 08:52:10 dvr mythbackend[1921]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Feb 10 08:52:10 dvr mythbackend[1921]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Feb 10 08:52:10 dvr mythbackend[1921]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Feb 10 08:52:10 dvr mythbackend[1921]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Feb 10 08:52:10 dvr mythbackend[1921]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Feb 10 08:52:10 dvr mythbackend[1921]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of dvr
Feb 10 08:52:10 dvr mythbackend[1921]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_US
Feb 10 08:52:10 dvr mythbackend[1921]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_US
Feb 10 08:52:10 dvr mythbackend[1921]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Feb 10 08:52:10 dvr mythbackend[1921]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Feb 10 08:52:10 dvr mythbackend[1921]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Feb 10 08:52:10 dvr mythbackend[1921]: N CoreContext main_helpers.cpp:556 (run_backend) MythBackend: Starting up as the master server.
Feb 10 08:52:10 dvr mythbackend[1921]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Feb 10 08:52:10 dvr mythbackend[1921]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Feb 10 08:52:12 dvr mythbackend[1921]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video1): SetInputAndFormat(2, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Feb 10 08:52:12 dvr mythbackend[1921]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video1): SetInputAndFormat(2, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Feb 10 08:52:13 dvr mythbackend[1921]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(3, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Feb 10 08:52:13 dvr mythbackend[1921]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(3, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Feb 10 08:52:13 dvr mythbackend[1921]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video1): SetInputAndFormat(4, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Feb 10 08:52:13 dvr mythbackend[1921]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video1): SetInputAndFormat(4, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Feb 10 08:52:14 dvr mythbackend[1921]: W CoreContext scheduler.cpp:207 (VerifyCards) Scheduler: Listings source '' is defined, but is not attached to a card input.
Feb 10 08:52:14 dvr mythbackend[1921]: I CoreContext programinfo.cpp:2052 (CheckProgramIDAuthorities) Found 1 distinct programid authorities
Feb 10 08:52:14 dvr mythbackend[1921]: I Scheduler mythdbcon.cpp:422 (getStaticCon) New static DB connectionSchedCon
Feb 10 08:52:14 dvr mythbackend[1921]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6544
Feb 10 08:52:14 dvr mythbackend[1921]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6544
Feb 10 08:52:14 dvr mythbackend[1921]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::8e70:5aff:fe7d:b08e%wlan0]:6544
Feb 10 08:52:14 dvr mythbackend[1921]: N CoreContext mediaserver.cpp:169 (Init) MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
Feb 10 08:52:14 dvr mythbackend[1921]: I CoreContext main_helpers.cpp:626 (run_backend) Main::Registering HttpStatus Extension
Feb 10 08:52:14 dvr mythbackend[1921]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6543
Feb 10 08:52:14 dvr mythbackend[1921]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6543
Feb 10 08:52:14 dvr mythbackend[1921]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::8e70:5aff:fe7d:b08e%wlan0]:6543
Feb 10 08:52:14 dvr mythbackend[1921]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Feb 10 08:52:17 dvr mythbackend[1921]: I Scheduler scheduler.cpp:2035 (HandleReschedule) Reschedule requested for id -1.
Feb 10 08:52:17 dvr mythbackend[1921]: I Scheduler scheduler.cpp:2095 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
Feb 10 08:52:17 dvr mythbackend[1921]: I Scheduler scheduler.cpp:2162 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Feb 10 08:52:24 dvr mythbackend[1921]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Feb 10 08:52:33 dvr mythbackend[1921]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 2003 at 2013-02-09T06:42:40 => Unknown
Feb 10 08:53:18 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Feb 10 08:53:18 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: dvr as a client (events: 2)
Feb 10 08:53:18 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Feb 10 08:53:18 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: dvr as a client (events: 2)
Feb 10 08:53:33 dvr mythbackend[1921]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Feb 10 08:53:33 dvr mythbackend[1921]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 2003 at 2013-02-06T06:20:51 => Unknown
Feb 10 08:53:33 dvr mythbackend[1921]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 2003 at 2013-02-09T06:42:41 => Unknown

```

when I start the frontend and try to "Watch TV"  I have to "Please wait ..." for about 10 mins before it shows me the schedule with all "unknown" for programs.  At one point it DID populate this properly, but not anymore for some reason.   the backend says ...

```

Feb 10 09:00:58 dvr mythbackend[1921]: I TVRecEvent tv_rec.cpp:1030 (HandleStateChange) TVRec(1): Changing from None to WatchingLiveTV
Feb 10 09:00:59 dvr mythbackend[1921]: I TVRecEvent tv_rec.cpp:3503 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
Feb 10 09:00:59 dvr mythbackend[1921]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Feb 10 09:00:59 dvr mythbackend[1921]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
Feb 10 09:00:59 dvr mythbackend[1921]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
Feb 10 09:00:59 dvr mythbackend[1921]: E TVRecEvent recordinginfo.cpp:966 (InsertProgram) RecordingInfo::InsertProgram(ProgramInfo(2003_20130210090059.nuv): channame(WEDU) startts(Sun Feb 10 09:00:59 2013) endts(Sun Feb 10 09:30:00 2013)#012             recstartts(Sun Feb 10 09:00:59 2013) recendts(Sun Feb 10 09:30:00 2013)#012             title(Unknown)): recording already exists...
Feb 10 09:01:00 dvr mythbackend[1921]: E RecThread NuppelVideoRecorder.cpp:1037 (ProbeV4L2) NVR(/dev/video0): Won't work with the streaming interface, falling back
Feb 10 09:01:05 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Feb 10 09:01:05 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: dvr as a client (events: 0)
Feb 10 09:01:05 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Feb 10 09:01:05 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: dvr as a remote file transfer
Feb 10 09:01:24 dvr mythbackend[1921]: I Metadata_29 jobqueue.cpp:2151 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for Unknown recorded from channel 2003 at 2013-02-10T09:00:59
Feb 10 09:01:24 dvr mythbackend[1921]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Feb 10 09:01:24 dvr mythbackend[1921]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Feb 10 09:01:24 dvr mythbackend[1921]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Feb 10 09:01:24 dvr mythbackend[1921]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Feb 10 09:01:25 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Feb 10 09:01:25 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: dvr as a client (events: 0)
Feb 10 09:01:25 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Feb 10 09:01:25 dvr mythbackend[1921]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: dvr as a client (events: 1)
Feb 10 09:02:32 dvr mythbackend[1921]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Feb 10 09:02:33 dvr mythbackend[1921]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 2003 at 2013-02-10T09:00:59 => Unknown

```

the metadata lookup says ...

```

Feb 10 09:01:24 dvr mythmetadatalookup[3050]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythmetadatalookup version: fixes/0.25 [v0.25.3-33-g1d4d50b] www.mythtv.org
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of dvr
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_US
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_US
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I CoreContext main.cpp:227 (main) Testing grabbers and metadata sites for functionality...
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Feb 10 09:01:24 dvr mythmetadatalookup[3050]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Feb 10 09:01:25 dvr mythmetadatalookup[3050]: I CoreContext main.cpp:234 (main) All grabbers tested and working.  Continuing...
Feb 10 09:01:25 dvr mythmetadatalookup[3050]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Feb 10 09:01:25 dvr mythmetadatalookup[3050]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Feb 10 09:01:25 dvr mythmetadatalookup[3050]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Unknown
Feb 10 09:01:25 dvr mythmetadatalookup[3050]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M Unknown
Feb 10 09:01:31 dvr mythmetadatalookup[3050]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Unknown 0 0
Feb 10 09:01:33 dvr mythmetadatalookup[3050]: I CoreContext lookup.cpp:286 (customEvent) Unable to match this title, too many possible matches. You may wish to manually set the season, episode, and inetref in the 'Watch Recordings' screen.
Feb 10 09:01:33 dvr mythmetadatalookup[3050]: N CoreContext main.cpp:265 (main) MythMetadataLookup run complete.

```

the frontend says ...

```

Feb 10 09:26:50 dvr mythfrontend[2851]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25.3-33-g1d4d50b] www.mythtv.org
Feb 10 09:26:50 dvr mythfrontend[2851]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Feb 10 09:26:50 dvr mythfrontend[2851]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Feb 10 09:26:50 dvr mythfrontend[2851]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Feb 10 09:26:50 dvr mythfrontend[2851]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Feb 10 09:26:50 dvr mythfrontend[2851]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Feb 10 09:26:50 dvr mythfrontend[2851]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Feb 10 09:26:50 dvr mythfrontend[2851]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Feb 10 09:26:50 dvr mythfrontend[2851]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Feb 10 09:26:50 dvr mythfrontend[2851]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/user/.mythtv
Feb 10 09:26:50 dvr mythfrontend[2851]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Feb 10 09:26:50 dvr mythfrontend[2851]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Feb 10 09:26:50 dvr mythfrontend[2851]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of dvr
Feb 10 09:26:50 dvr mythfrontend[2851]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_US
Feb 10 09:26:50 dvr mythfrontend[2851]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_US
Feb 10 09:26:50 dvr mythfrontend[2851]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Feb 10 09:26:50 dvr mythfrontend[2851]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Feb 10 09:26:50 dvr mythfrontend[2851]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Feb 10 09:26:50 dvr mythfrontend[2851]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Feb 10 09:26:50 dvr mythfrontend[2851]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Feb 10 09:26:50 dvr mythfrontend[2851]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Feb 10 09:26:50 dvr mythfrontend[2851]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Feb 10 09:26:50 dvr mythfrontend[2851]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6547
Feb 10 09:26:50 dvr mythfrontend[2851]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6547
Feb 10 09:26:50 dvr mythfrontend[2851]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::8e70:5aff:fe7d:b08e%wlan0]:6547
Feb 10 09:26:51 dvr mythfrontend[2851]: E CoreContext mythraopconnection.cpp:1277 (LoadKey) RAOP Conn: Failed to read key from: /home/user/.mythtv/RAOPKey.rsa
Feb 10 09:26:51 dvr mythfrontend[2851]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
Feb 10 09:26:51 dvr mythfrontend[2851]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Feb 10 09:26:51 dvr mythfrontend[2851]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/dev/lircd'#012#011#011#011eno: No such file or directory (2)
Feb 10 09:26:51 dvr mythfrontend[2851]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/user/.mythtv/joystickmenurc
Feb 10 09:26:51 dvr mythfrontend[2851]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Feb 10 09:26:51 dvr mythfrontend[2851]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP 127.0.0.1:6948
Feb 10 09:26:51 dvr mythfrontend[2851]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [::1]:6948
Feb 10 09:26:51 dvr mythfrontend[2851]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [fe80::8e70:5aff:fe7d:b08e%wlan0]:6948
Feb 10 09:26:51 dvr mythfrontend[2851]: I CoreContext mythmainwindow.cpp:948 (Init) Using Frameless Window
Feb 10 09:26:51 dvr mythfrontend[2851]: I CoreContext mythmainwindow.cpp:961 (Init) Using Full Screen Window
Feb 10 09:26:51 dvr mythfrontend[2851]: I CoreContext mythmainwindow.cpp:1051 (Init) Using the Qt painter
Feb 10 09:26:51 dvr mythfrontend[2851]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Feb 10 09:26:52 dvr mythfrontend[2851]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Feb 10 09:26:52 dvr mythfrontend[2851]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Feb 10 09:26:52 dvr mythfrontend[2851]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Feb 10 09:26:52 dvr mythfrontend[2851]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Feb 10 09:26:52 dvr mythfrontend[2851]: N CoreContext mythmainwindow.cpp:1862 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Feb 10 09:26:52 dvr mythfrontend[2851]: N CoreContext mythmainwindow.cpp:1862 (RegisterMediaPlugin) Registering WebBrowser as a media playback plugin.
Feb 10 09:26:52 dvr mythfrontend[2851]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythbrowser
Feb 10 09:26:52 dvr mythfrontend[2851]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
Feb 10 09:26:52 dvr mythfrontend[2851]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
Feb 10 09:26:52 dvr mythfrontend[2851]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
Feb 10 09:26:52 dvr mythfrontend[2851]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
Feb 10 09:26:52 dvr mythfrontend[2851]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Mythbuntu'
Feb 10 09:26:52 dvr mythfrontend[2851]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Feb 10 09:26:52 dvr mythfrontend[2851]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Feb 10 09:26:52 dvr mythfrontend[2851]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on dvr' type '_mythfrontend._tcp.' domain: 'local.'
Feb 10 09:26:56 dvr mythfrontend[2851]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
Feb 10 09:26:56 dvr mythfrontend[2851]: N CoreContext mythmainwindow.cpp:2591 (PauseIdleTimer) Resuming idle timer
Feb 10 09:26:56 dvr mythfrontend[2851]: N CoreContext mythmainwindow.cpp:2586 (PauseIdleTimer) Suspending idle timer
Feb 10 09:26:56 dvr mythfrontend[2851]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
Feb 10 09:26:56 dvr mythfrontend[2851]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
Feb 10 09:26:56 dvr mythfrontend[2851]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
Feb 10 09:26:56 dvr mythfrontend[2851]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Feb 10 09:26:56 dvr mythfrontend[2851]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
Feb 10 09:26:56 dvr mythfrontend[2851]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
Feb 10 09:26:56 dvr mythfrontend[2851]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/data/video/mythtv/livetv/2003_20130210092656.nuv) cardtype(DUMMY)
Feb 10 09:27:36 dvr mythfrontend[2851]: E CoreContext tv_play.cpp:2496 (StartRecorder) TV: StartRecorder() -- timed out waiting for recorder to start
Feb 10 09:27:36 dvr mythfrontend[2851]: E CoreContext tv_play.cpp:2233 (HandleStateChange) TV: LiveTV not successfully started
Feb 10 09:27:36 dvr mythfrontend[2851]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
Feb 10 09:28:06 dvr mythfrontend[2851]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(1891720:52): readStringList: Error, timed out after 30000 ms.
Feb 10 09:28:06 dvr mythfrontend[2851]: N CoreContext mythcorecontext.cpp:960 (SendReceiveStringList) Connection to backend server lost
Feb 10 09:28:06 dvr mythfrontend[2851]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Feb 10 09:28:13 dvr mythfrontend[2851]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(1891720:36): readStringList: Error, timed out after 7000 ms.
Feb 10 09:28:13 dvr mythfrontend[2851]: C CoreContext mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.
Feb 10 09:28:13 dvr mythfrontend[2851]: C CoreContext mythcorecontext.cpp:1003 (SendReceiveStringList) Reconnection to backend server failed
Feb 10 09:28:13 dvr mythfrontend[2851]: I ScreenLoad mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Feb 10 09:28:13 dvr mythfrontend[2851]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
Feb 10 09:28:14 dvr mythfrontend[2851]: I CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private: DPMS Deactivated 1
Feb 10 09:28:20 dvr mythfrontend[2851]: E ScreenLoad mythsocket.cpp:534 (readStringList) MythSocket(7fd698012dc0:36): readStringList: Error, timed out after 7000 ms.
Feb 10 09:28:20 dvr mythfrontend[2851]: C ScreenLoad mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.
Feb 10 09:28:20 dvr mythfrontend[2851]: A ScreenLoad programinfo.cpp:4514 (LoadFromScheduler) LoadFromScheduler(): Error querying master.
Feb 10 09:28:20 dvr mythfrontend[2851]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Feb 10 09:28:27 dvr mythfrontend[2851]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(1a0b4d0:36): readStringList: Error, timed out after 7000 ms.
Feb 10 09:28:27 dvr mythfrontend[2851]: C CoreContext mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.
Feb 10 09:28:27 dvr mythfrontend[2851]: A CoreContext programinfo.cpp:4514 (LoadFromScheduler) LoadFromScheduler(): Error querying master.
Feb 10 09:28:27 dvr mythfrontend[2851]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Feb 10 09:28:34 dvr mythfrontend[2851]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(1a0b4d0:36): readStringList: Error, timed out after 7000 ms.
Feb 10 09:28:34 dvr mythfrontend[2851]: C CoreContext mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.
....

```


any help to debug this would be VERY appreciated

Thanks,
Steve

---

### Post by thaibuntu on 2013-02-13
I think you only need the mpeg encoders (Hardware), try getting rid of the v4l encoders (software).

---

