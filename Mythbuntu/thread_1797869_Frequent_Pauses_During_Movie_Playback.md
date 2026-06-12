---
title: "Frequent Pauses During Movie Playback"
date: 2011-07-05
forum: Mythbuntu
---

### Post by tsx_5 on 2011-07-05
Hi,

I have installed a recent version of mythbuntu (11.04) for my frontend/backend combo box.  Install went fine and I have most everything up and running.  

My major problem right now is that HD movies (usually in mkv format) are pausing durning playback.  By pausing, I mean the audio/video will stop for 0.5 - 2 seconds and then restart.  Some times audio is skipped/missed.  I am using a NVIDIA GT 430 (fanless) card, which is setup to use VDPAU.  I tried all of the VDPAU profiles with no avail.  I also tried adding vdpaubuffersize=32, which on initial test seemed to have worked, but upon retesting discovered it had not.  Log output from mythfrontend has a lot of these error messages:

"waited 100ms for video buffers"

Which is similar to this thread [http://ubuntuforums.org/showthread.php?t=1678636](http://ubuntuforums.org/showthread.php?t=1678636) (which never seemed to have a solution) and seemed focused on tv shows.  My problem only shows up when playing HD (as in bluray) quality movies.

Has anyone seen this?  Any solutions?  The "Playback problem -- random short pauses" never seemed to suggest any solutions either...

---

### Post by ian dobson on 2011-07-05
Hi,

Whats the rest of your hardware (CPU,RAM,HD).

I can play back large (10Gb/hr) mkv's on my frontend without any problems when the recordings are on my network attached backend.

My frontend is a c2d e5200 underclocked to 1.2GHz,2Gb ram and a underclocked 9600gt graphic card.

Also what graphic card driver are you using? Can you provide a full log of the frontend when you play a mkv.

Regards
Ian Dobson

---

### Post by tsx_5 on 2011-07-05
My hardware is:


[LIST]
[*]AMD Athlon 64 X2 3800+(65W) Windsor 2.0GHz Socket AM2 Processor 
[*]WINTEC AMPO 1GB (2 x 512MB) 240-Pin DDR2 SDRAM DDR2 533 (PC2 4200) Dual Channel Kit Desktop Memory Model 3AMD2533-1G1K-R 
[*]Kingston 128G SSD drive
[*]Zotac Geforce GT 430 fanless Video Card
[/LIST]

I have added 2 attachments. Rename .doc to .log (couldn't upload otherwise). The 2nd one is output from ffmpeg for the file I attempted to play.

Thanks in advance

---

### Post by ian dobson on 2011-07-05
Hi,

OK I've had a quick log at the log file and can see anything really wrong (apart from the buffering messages). I'll have another look tonight when I have abit more time.

I can't see what version of mythtv your running. If it's .24 then make sure your runing the latest -fixes branch.

Regards
Ian Dobson

---

