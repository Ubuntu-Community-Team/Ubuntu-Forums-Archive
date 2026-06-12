---
title: "Cannot createDVD from TV recording"
date: 2009-01-15
forum: Mythbuntu
---

### Post by MarkBM on 2009-01-15
Hi. I not able to create a DVD from a TV recording. I get through to a screen called logviewer with an update frequency? There is an update button,that when clicked, nothing happens. Prior to this, I have selected the recording & image & DVD type. There is also a message that there is no cutlist. Is this required & if so, how do I create it?
Many thanks

---

### Post by klc5555 on 2009-01-15
> **MarkBM said:**
> Hi. I not able to create a DVD from a TV recording. I get through to a screen called logviewer with an update frequency? There is an update button,that when clicked, nothing happens. Prior to this, I have selected the recording & image & DVD type. There is also a message that there is no cutlist. Is this required & if so, how do I create it?
Many thanks

I take it that Mytharchive is not actually failing, but you haven't let it run to completion? To the point that it either pops out a dvd, or the log viewer echos the dreaded message "terminated"? 

The logviewer you see is the progress log that Mytharchive updates every 5 seconds while the mythburn script is cranking through all the steps necessary to encode the necessary files for the dvd, assemble them in the correct format for the dvd, and then build the *.iso file and actually burn it to dvd.

The mytharchive process, even when it works, is not fast. The fastest profile is when you're transferring a recording from an analog source to dvd, and choose "do not re-encode" (because the resolution of analog is already correct for a dvd, and the audio is already in AC3 format). Even this will run 25-45 minutes. Other analog profiles (SP, LP, HQ), or stuff from digital sources (which all has to be reencoded to SP, LP, or HQ) can keep Mytharchive chewing away for 2 to 6 hours (or longer depending on whatever else the machine is doing) before it spits the final dvd out the other end.

But mytharchive generally is quite happy running in the background. Once you've gotten to the logviewer and the script is clearly running, hit the "exit" button and then go back to whatever you were doing. If you later begin to wonder what ever became of your dvd, you can return to the "create dvd" menu option, which will pop up the logviewer again if the script is still running. If mytharchive terminated with an error, the log  "progress.log" will have the gory details in wherever your mytharchive temporary directory is set to. 

You don't need a cutlist. The cutlist tells mythtranscode which parts of your recording to cut out (like the commercials) when  your recording is being processed. Nuking commercials and making your cutlist is described here: [http://mythtv.org/wiki/index.php/Removing_Commercials](http://mythtv.org/wiki/index.php/Removing_Commercials)

The general user manual entry for Mytharchive is here: [http://mythtv.org/wiki/index.php/MythArchive](http://mythtv.org/wiki/index.php/MythArchive)

Cheers! :)

---

### Post by fatmonk on 2009-01-15
Have you created and configured a temp directory for the archive process (in the MythArchive setup screens on your front end)? And made them writeable by the correct users (as per you recording directory I think is what's needed)?

I had the same problem when setting MythArchive up, and that sorted it for me.

-FM

---

### Post by MarkBM on 2009-01-19
> **klc5555 said:**
> I take it that Mytharchive is not actually failing, but you haven't let it run to completion? To the point that it either pops out a dvd, or the log viewer echos the dreaded message "terminated"? 

The logviewer you see is the progress log that Mytharchive updates every 5 seconds while the mythburn script is cranking through all the steps necessary to encode the necessary files for the dvd, assemble them in the correct format for the dvd, and then build the *.iso file and actually burn it to dvd.

The mytharchive process, even when it works, is not fast. The fastest profile is when you're transferring a recording from an analog source to dvd, and choose "do not re-encode" (because the resolution of analog is already correct for a dvd, and the audio is already in AC3 format). Even this will run 25-45 minutes. Other analog profiles (SP, LP, HQ), or stuff from digital sources (which all has to be reencoded to SP, LP, or HQ) can keep Mytharchive chewing away for 2 to 6 hours (or longer depending on whatever else the machine is doing) before it spits the final dvd out the other end.

But mytharchive generally is quite happy running in the background. Once you've gotten to the logviewer and the script is clearly running, hit the "exit" button and then go back to whatever you were doing. If you later begin to wonder what ever became of your dvd, you can return to the "create dvd" menu option, which will pop up the logviewer again if the script is still running. If mytharchive terminated with an error, the log  "progress.log" will have the gory details in wherever your mytharchive temporary directory is set to. 

You don't need a cutlist. The cutlist tells mythtranscode which parts of your recording to cut out (like the commercials) when  your recording is being processed. Nuking commercials and making your cutlist is described here: [http://mythtv.org/wiki/index.php/Removing_Commercials](http://mythtv.org/wiki/index.php/Removing_Commercials)

The general user manual entry for Mytharchive is here: [http://mythtv.org/wiki/index.php/MythArchive](http://mythtv.org/wiki/index.php/MythArchive)

Cheers! :)
Thanks for the tip. Maybe I just didn't wait long enough. Just seemed absolutely nothing was happening, ie no HDD activity. Fatmonks reply looks as though it could be an issue also. Apologies for the belated reply.
Cheers

---

### Post by MarkBM on 2009-01-19
> **fatmonk said:**
> Have you created and configured a temp directory for the archive process (in the MythArchive setup screens on your front end)? And made them writeable by the correct users (as per you recording directory I think is what's needed)?

I had the same problem when setting MythArchive up, and that sorted it for me.

-FM
Thanks a million. Haven't looked at this yet, but seems a very likely solution.
Apologies for the belated repy.

---

