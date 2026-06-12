---
title: "Hauppauge HVR-2250 woes"
date: 2010-07-24
forum: Mythbuntu
---

### Post by Tteddo on 2010-07-24
Ok, I am finally building my new MythTv box. I have everything installed including a Hauppauge HVR-2250 capture card. I used the tutorial here:
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212")
And it shows up properly when I do lspci:
> 02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)

and in dmesg there are no errors:
> root@Dionysus:~# dmesg | grep saa7164_downloadfirmware
[   12.092542] saa7164_downloadfirmware() no first image
[   12.092553] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   12.456759] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   12.456762] saa7164_downloadfirmware() firmware loaded.
[   12.456771] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   12.456776] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   12.456778] saa7164_downloadfirmware() BSLSize = 0x0
[   12.456779] saa7164_downloadfirmware() Reserved = 0x0
[   12.456780] saa7164_downloadfirmware() Version = 0x51cc1

When I add it in the MythTV Backend, all goes well, MythTV sees it and everything. But, when I go to add channels (i.e. Scan for channels) it finds no channels (Timed out, no signal) no matter what I set it to. I would think it would be Frequency Table: Cable and Modulation QAM-256 or 64 like it says in there. I know my provider broadcasts in digital as my TV scans them all fine. I also tried to just play the stream from the card in VLC but that comes back with:
> Unable to play the MRL 'dvb://frequency=0'
With either input.
Can anyone point me to the magic command that will make it all better?
I do have ubuntu-desktop installed if that helps.

---

### Post by Tteddo on 2010-07-25
Ok, had a bright idea. I took out the card and hooked up in a Windows 7 machine I have. Installed WinTV7 and had it scan for the various channels. It only finds about 5 channels around channel 77 when I scan for Digital QAM and none for Digital ATSC. It will find all the analog ones no problem (which I don't need (I have a PVR-500 for those in my current MythTV box), and the Linux driver doesn't support analog anyways).
Now, right now I have my TV scanning for digital channels and it's finding all of them i.e. 6-1, 6-2, 8-1, 8-2, 8-3, etc, all the way up to 78 or so. They all come in nice and crisp on the TV.
So, why the difference? I think I am missing something here. FYI- This is in Maine, US and as far as I know my cable company is running a standard setup.

---

### Post by LowSky on 2010-07-26
try a different firmware

first open nautilus with Sudo privileges
```
gksu nautilus
```
Go to the /lib/firmware folder and delete the file ```
v4l-saa7164-1.0.3.fw
```
close nautilus 

download this file
[http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw)

then save it to /lib/firmware

```
sudo cp v4l-saa7164-1.0.3-3.fw /lib/firmware
```

the reboot

let me know if it works

reboot and then try to scan again

---

### Post by Tteddo on 2010-07-26
Ok, I tried that and upon reboot I checked dmesg and get this now:
> root@Dionysus:~# dmesg | grep saa7164_downloadfirmware
[   13.012034] saa7164_downloadfirmware() no first image
[   13.012042] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   13.099219] saa7164_downloadfirmware() Upload failed. (file not found?)

Do I have to change something else to recognize the new firmware?

I just renamed to and now it is fine, trying a scan now.

---

### Post by Tteddo on 2010-07-26
Now when I go to scan it fails to open the card.

---

### Post by LowSky on 2010-07-26
sorry I completely forgot. you will need to also  run this part of my tutorial to use the newer firmware

> 
Next we need download the driver using these command to fetch and install, I'm using the stable branch from Kernel labs, but you can use Linuxtv.org version if you wish.
```
hg clone http://kernellabs.com/hg/saa7164-stable/
```

now change to the directory:
```
cd saa7164-stable
```

Then run the command make:
```
make CONFIG_DVB_FIREDTV:=n
```

That will take some time, go grab a drink and wait it out, when it completes run this command:
```
sudo make install
```

3b. Next Reboot the system to insure the driver and firmware are installed and running:
```
sudo reboot
```

---

### Post by Tteddo on 2010-07-26
Ok, I installed the new firmware and it appears to be working, but it is still the same (Timed out, no signal) when I scan for channels. Even though I can get analog cable in here (office) I also ran a cable from the living room from the source that the TV uses to rule out bad splitters and whatnot.

---

### Post by LowSky on 2010-07-26
You will not get any analog  channels using this card with Linux. The drivers do not support that. but you should see the digital.
If you really do  live in Shapleigh, Maine, then according to this link: [http://www.silicondust.com/hdhomerun/lineup_web/US:04076#lineup_2783452](http://www.silicondust.com/hdhomerun/lineup_web/US:04076#lineup_2783452)
you can receive about 19 digital channels with cable (it says 34 but most are "on demand" channels) and possibly 23 using an OTA antenna.

You say the card is grabbing channels in Windows and so does your TV, it could be the option your choosing for channels under MythTV. Check your schedulesdirect account and make sure you are only scanning for channels within the frequencies can actually receive without a cable box.

---

### Post by Tteddo on 2010-07-26
I am sure about the digital because my TV picks up all of them. That's how I found out that they were even broadcasting in digital. I was playing around with the TV one day. It doesn't use a cable box, it's on a splitter with my old MythTV box, which is where my new MythTV box is hooked up now.
I don't care about the analog as I have a PVR-500 (in my old MythTV box). I was hoping to get the nice digital picture.
That chart isn't accurate as my provider is Metrocast. Most of the town is Metrocast, Time Warner is just one road on the other side of town.
I had added the digital lineup to my SchedulesDirect account, and selected that one when I set it up in MythTV (my old box still gets the analog one), and ran mythfilldatabase.

I also tried to "Fetch Channels from Listings source" but that doesn't do anything.

I just did another Zip Code on that site, this one is more accurate:
[http://www.silicondust.com/hdhomerun/lineup_web/US:03839#lineup_2789697]("http://www.silicondust.com/hdhomerun/lineup_web/US:03839#lineup_2789697")
WinTV on the Windows 7 box only sees the ones at the bottom that are Unknown (that might have been the cable in here which is why I ran it out from the living room). My TV sees them all. Rochester, NH, Sanford, ME all use Metrocast like I do.

---

### Post by LowSky on 2010-07-26
Just a bit of warning, digital tuners can be very sensitive. its basically all or nothing, not like analog were the picture will get fuzzy, digital will just not show up. Also when you split a cable line the signal is basically reduced to half. If you can use the cleanest possible cable line you can, hopefully one that hasn't been split.

I had to have my cable company (Cablevision) update the lines into my house before we could recieve broadband internet, as the older line couldn't handle higher speeds, it was also providing substandard signal for TV so it was a great help when we also moved into HD.

If I recall I huse CABLE-IRC High or something like that (sorry not at my HTPC to verify) to scan for my channels, most cable companies use QAM channels starting on channel frequency 70 or higher.

---

### Post by Tteddo on 2010-07-26
When my sister got her PVR from Time Warner they had to give her 1600mhz splitters for just that reason (she couldn't get any high def channels at all). That's why I ran the cable from the living room, since the TV works for sure (off a 1600mhz splitter). The splitter off the cable modem in here is one of the 900mhz ones, which this morning I realized might be a problem. Tomorrow, or the next time I get to work on this, I am going to put the card into the Windows 7 machine again and see what's what with the cable from the living room.
I'll report back what I find.
I really appreciate all your help!!

---

### Post by LowSky on 2010-07-26
be carefull not all splitters are created equal. If you can stop by your local cable company support building and ask for one, they might just give them away, or charge you a few bucks... but they are well worth it.

---

### Post by Tteddo on 2010-07-27
> **LowSky said:**
> be carefull not all splitters are created equal. If you can stop by your local cable company support building and ask for one, they might just give them away, or charge you a few bucks... but they are well worth it.

That's a great tip! Thanks.

---

### Post by Tteddo on 2010-07-31
Ok, I am back, had a busy week! 
So I ran the cable from the same splitter the TV uses and put the card back in the Win7 box for testing. After it not being recognized (??) and reseating it in the slot it now sees all the channels the TV does and then some. I am able to watch all the unencrypted ones no problem. I replaced the 1600Mhz splitter with a 2400Mhz one, and it tested out the same. I learned from this that Metrocast uses QAM-256 for sure.
In the interest of troubleshooting, I read that Kaffeine would be good for testing. Earlier (I think it was before the driver update, but not sure) I was getting a "device not found error" when I would try to configure it and scan for channels. Now it scans and sees the channels and I can watch them (although the sound is broken on the HD channels).
Put the card back in the MythBuntu box and go to do a scan under Input connections and now it is scanning! Cool!
So then I get this error when I go to watch TV:
> mythtv is using all inputs but there are no active recordings
So I ran:
> sudo service mythtv-backend start 
and it says it is already started.
So, then I do this:
> sudo service mythtv-backend restart 
And now the error is gone. I have to do that after every boot.
But, when I go to hit a channel that has info for it, I get an error about channel lock, and it says Signal 0% Partial Lock.
In MythWeb I get this though:
> Encoder 1 is local on Dionysus and is watching Live TV 'Back to the Future Part II' on 2066. This recording is scheduled to end at 5:30 PM.
So what could I be missing?

Edit, one channel is actually coming though, but now when I try to switch I get an error "Error opening jump program file" and it boots me out of LiveTV.

---

### Post by mycatsnameisbernie on 2010-07-31
> **Tteddo said:**
> Edit, one channel is actually coming though, but now when I try to switch I get an error "Error opening jump program file" and it boots me out of LiveTV.This sounds like the same error I got when I first tried my digital tuner in a new Mythbuntu setup. It was caused by running out of kernel memory. Check your backend log (/var/log/mythtv/mythbackend.log) when you get that error, and see if you see any errors referring to memory allocation failing. If you do, check /var/log/messages for errors referring to vmalloc.
 
If this is what is happening to you, the fix is here:
[http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)
 
If this isn't your problem, then check both the frontend and backend logs for other clues. Feel free to post your logs here.
 
Hope that helps...

---

### Post by Tteddo on 2010-08-01
I didn't see anything in the mythbackend.log or in messages about vmalloc (except the normal message) but in the frontend log I get this when it happens:
> 2010-08-01 11:05:12.604 RingBuf(/var/lib/mythtv/livetv/2049_20100801110508.mpg): Waited 4.0 seconds for data to become available...
2010-08-01 11:05:12.604 Checking to see if there's a new livetv program to switch to..
2010-08-01 11:05:16.606 RingBuf(/var/lib/mythtv/livetv/2049_20100801110508.mpg): Waited 8.0 seconds for data to become available...
2010-08-01 11:05:16.606 Checking to see if there's a new livetv program to switch to..
2010-08-01 11:05:18.669 ProgramInfo(): Updated pathname '':'' -> '2048_20100801110518.mpg'
2010-08-01 11:05:18.760 RingBuf(/var/lib/mythtv/livetv/2049_20100801110508.mpg): Timing out wait due to impending livetv switch.
2010-08-01 11:05:18.760 RingBuf(/var/lib/mythtv/livetv/2049_20100801110508.mpg) Warning: Peek() requested 2048 bytes, but only returning 0
2010-08-01 11:05:18.760 NVP::OpenFile(): Error, couldn't read file: /var/lib/mythtv/livetv/2049_20100801110508.mpg
2010-08-01 11:05:18.760 NVP(0), Error: JumpToProgram failed.
2010-08-01 11:05:18.761 ProgramInfo(): Updated pathname '':'' -> '2048_20100801110518.mpg'
2010-08-01 11:05:18.761 ProgramInfo(): Updated pathname '':'' -> '2048_20100801110518.mpg'
2010-08-01 11:05:18.816 NVP(0), Error: Unknown recorder error, exiting decoder
2010-08-01 11:05:18.959 TV: Attempting to change from WatchingLiveTV to None

So, I am thinking it's due to "Signal 0% Partial Lock" and therefore generating no file for the frontend to read? Kaffeine plays all the channels normally (well, the sound in HD is messed up, but one thing at a time).

---

### Post by mycatsnameisbernie on 2010-08-01
> **Tteddo said:**
> I didn't see anything in the mythbackend.log or in messages about vmalloc (except the normal message) but in the frontend log I get this when it happensThere should be something in your backend log about switching from None to WatchingLiveTV. The transition from Partial Lock to Lock is done in the backend, so I think your problem is in the backend, not the frontend. I think your best clues to solving your problem will be found in your backend log. 
 
You might want to post both your frontend and backend logs in the MythTV-Users mailing list, where users and developers with much more MythTV experience than I have might be able to help you.

---

### Post by Tteddo on 2010-08-01
Ok, these weren't the only problems I was having with Mythbuntu, there was a bunch of other things like the restart button just logging out, weird permissions things, MythWeb stopped, and the backend quit starting up at boot. etc. I felt like it was whack-a-mole. Every time I went to do something I would have to fix something else first.
So since I have 3 machines that run flawlessly on plain Lucid, I started over, but installed Lucid (not MythBuntu) first, then installed all the MythTV packages. I followed LowSky's instructions on his other thread to get the card to work and everything almost works now. I just have to tweak all the settings for my display.
That's for the help, I really appreciate it!

---

### Post by azich on 2011-01-26
I was able to get an HVR-2250 working on Ubuntu 11.04 2.6.35-24-generic by substituting the basic hg clone / make / make install with something a bit more complicated but ultimately successful for me:

```

0. `sudo apt-get install v4l-conf`
1. `hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l`
2. Use this as v4l/.config: [http://pastebin.com/4GPrszBV](http://pastebin.com/4GPrszBV)
4. `make`

5. For all files with implicit declaration of function 'usb_buffer_free', add the following to the top after the #includes.

#define usb_buffer_alloc(a, b, c, d) usb_alloc_coherent(a, b, c, d)
#define usb_buffer_free(a, b, c, d) usb_free_coherent(a, b, c, d)

6. Repeat steps 4 and 5 until you no longer encounter the 'usb_buffer_free' errors.

7. You should now encounter the 'struct net_device' errors. Download the full linux-source-2.6.35, decompress it, and copy the following to the v4l directory.

linux-source-2.6.35/drivers/media/dvb/dvb-core/*.h
linux-source-2.6.35/drivers/media/dvb/dvb-core/*.c

8. `make`
9. You may encounter more 'usb_buffer_free' errors, if so, repeat steps 4 and 5 again until it goes away.
10. `sudo make install`
11. `sudo modprobe -r saa7164; sudo modprobe saa7164` or `reboot`

```

Here is the relevant section of the kernel log after the modprobe: [http://pastebin.com/rWB6WBhB](http://pastebin.com/rWB6WBhB)



Hope this helps!

---

