---
title: "AverTVHD MCE A180 MythTV issues"
date: 2009-03-01
forum: Multimedia Software
---

### Post by RusH487 on 2009-03-01
This weekend i just built a brand new HTPC and, rather than mess with Vista, decided to install a copy of 64 bit Hardy Heron.  I had heard that MythTV was probably the best PVR program to use.  Initially, when building the machine I had planned to hook it up to my DirecTV HD receiver and use it as an HD DVR.  Now I am realizing that my tuner (the AverTVHD MCE A180) cannot be hooked up to my DirecTV receiver.  Instead, I have hooked up a regular antenna to the tuner, have installed the latest drivers and firmware, and have attempted to follow the MythTV Ubuntu Installation instructions to the best of my ability.  Right now, my issue is that when I go to scan for channels, I see they are being detected (92% or so signal strength) but mythtv keeps telling me it is not finding channels and it is timing out.  Is this because of my antenna? My TV tuner?  I am very new to linux and after several hours of searching for any solution, I am beginning to get extremely frustrated.

Alternately, is there any way at all to have my new HTPC act as an HD DVR with my DirecTV receiver?  Thanks in advance, any help on either issue would be greatly appreciated.

---

### Post by RusH487 on 2009-03-02
So, I've managed to get a little further in this problem (I think)...  I uninstalled mythtv and installed mythbuntu on top of ubuntu (It also turns out I am using Intrepid, not Hardy... woops).  I think I have everything set up correctly, but the tuner is still not locating any channels.

My card type is set to DVB DTV capture card
Video Sources: EIT
Input Connections: DVB:0 Capture Device
                   Video Source: EIT
                   Quick Tuning: LiveTV Only
                   Checked:  Unencrypted Channels Only
                             Allow audio only channels

when I go to scan for channels, it results in the following:
signal strength: 99%
signal/noise: 91%

and after a few seconds, in the backgroumd it says Timeout Scanning ATSC Channel (number) -- No Tables

...and I am finding myself stuck again.  Any ideas? Please?

---

### Post by RusH487 on 2009-03-02
I've given up on MythTV and have tried obtaining better results by switching to more simple programs, such as TVTime Television Viewer, Me-TV, and VLC Media Player.

TVTime allows me to switch between S-Video input and Composite 1 input.  Both display nothing but a black screen.

VLC, after I go to Media->Open Capture Device...-> Capture Mode: DVB-> Play...  It gives me the following error

Your input can't be opened:
VLC is unable to open the MRL 'dvb://'. Check the log for details.

Me-TV when I try to open it, immediately gives me the error:

There are no available DVB tuner devices.

I'm pretty new to Linux and I've tried finding ANY documentation on this card and am coming up short everywhere I look.  I'm extremely desperate at this point.  Please, anyone who has or knows anything about an AVerTVHD MCE A180 card -- I've tried everything I've found in the forums (like this:  [http://ubuntuforums.org/showthread.php?t=715165](http://ubuntuforums.org/showthread.php?t=715165) ) and for whatever reason I still can't even get a simple signal to come in on any software.  I just need something, ANYTHING that will get this effin' card to work.

---

### Post by RusH487 on 2009-03-03
So I decided to try something different and I plugged some composite cables in directly to my AVerTVHD card from the back of my DirecTV box.  I can get a (crappy) picture in TVTime, but no sound....  Being as I can't get sound to play for anything else on this computer yet, that's not one of my biggest issues.

I found this thread pertaining to the A180 card:
[http://mysettopbox.tv/phpBB2/viewtopic.php?t=9166&start=0&postdays=0&postorder=asc&](http://mysettopbox.tv/phpBB2/viewtopic.php?t=9166&start=0&postdays=0&postorder=asc&)

and I tried following all of the directions...  I set my capture device to DVB just like it had been set to previously and ran the channel scan again.  It still keeps timing out and saying 'no signal'.  Apparently that thread worked for everyone else there (perhaps because it is for Knoppmyth and not Mythbuntu?) but I must be doing something wrong.  So, now I've got the composite-in (video) working on the card, but still no OTA ATSC....  :sigh:

---

