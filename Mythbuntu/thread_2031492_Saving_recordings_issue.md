---
title: "Saving recordings issue"
date: 2012-07-22
forum: Mythbuntu
---

### Post by byronmyth on 2012-07-22
Hi folks.

I have the last 3 years Tour de France recorded on my Myth system (I'd happily take more if anyone has earlier years recorded). I wanted to trim the recordings down, take out the adverts and trim off the leader and ends, so copied a test file to my Windows PC, used a nice piece of software that obliged. I then copied the file back into the "videos" folder. I can play this quite happily using the videos function, but as soon as I press fast forward or rewind, a popup comes saying "searching" and that's your lot, the client is stuck until reboot. Seems to work ok with the couple of AVI's I've, and a couple of MPG's not recorded on the MythTV system, just the Myth recordings that cause the issue.

Thinking that it was the editing causing the issue, I tried an untouched copy, copied from the TV recordings section to the videos folder, same issue, will play fine until I try and skip ahead. Anyone have a fix in mind for this please? I'm running Mythbuntu 11.10, I want to upgrade but want to ensure that my TdF recordings are safe before bringing my system up to date....

---

### Post by Rotak on 2012-07-22
Hi!

Why are you using an external editor in favour of the internal editor?

I suppose you are using the MPG/NUV files directly from the folder where your recordings are located... Those files do not have an index. MythTV stores the index into the database. That causes the problem with the playback when trying to jump forward or backwards.

The normal way would be to use the internal editor like this:
* Start playback on an original recording (your copied/edited ones won't work).
* Press E to start the internal editor.
* Cut the video as you like

From there, you have several options....
1) Leave the video as it is.
2) Let MythTV transcode the video (so it physically cuts out the ads from the file)
3) Let MythTV export the video (e.g. to XVid or DVD format)

Note, that option 2 requires the transcoder to be set up proberly, and option 3 requires MythExport or NUVExport to be set up properly.

Hope I could help.

---

### Post by byronmyth on 2012-07-22
Hi.

Thanks for the reply. I'm using an external editor for ease of use really, I can process the file much quicker that with the internal editor. I also don't want to have the episodes in the normal TV recordings area, several reasons, they are clogging up the directory, I want just those recordings available on a some of the clients, not the TV recordings, I want to install from stratch with the latest version as I'm lagging we'll behind, and besides the server has seen lots of cludges to get things to work, it can be troublesome from time to time (blank recordings etc).

If I simply copy the file from the TV recordings area, to the video area I get the issue, where as another MPG file that wasn't recorded on MYTH plays ok from the video area, is there something missing from the Myth recorded MPG that causes the issue?

Regards - Brian

---

### Post by anonymousdog on 2012-07-22
> **byronmyth said:**
> Hi.
If I simply copy the file from the TV recordings area, to the video area I get the issue, where as another MPG file that wasn't recorded on MYTH plays ok from the video area


If that's the case, I'd try running one of those MythTV mpg files through the lossless MPEG transcoder (in MythTV) to let it work out any issues that might be in the original MPGs.  Then copy it to the Videos directory to test.

---

### Post by Rotak on 2012-07-22
> **byronmyth said:**
> Hi.

Thanks for the reply. I'm using an external editor for ease of use really,

Well, then the question is, why you don't export them into XVID or something before you edit it in the external software?

---

### Post by klc5555 on 2012-07-22
> **byronmyth said:**
> Hi folks.

I have the last 3 years Tour de France recorded on my Myth system (I'd happily take more if anyone has earlier years recorded). I wanted to trim the recordings down, take out the adverts and trim off the leader and ends, so copied a test file to my Windows PC, used a nice piece of software that obliged. I then copied the file back into the "videos" folder. I can play this quite happily using the videos function, but as soon as I press fast forward or rewind, a popup comes saying "searching" and that's your lot, the client is stuck until reboot. Seems to work ok with the couple of AVI's I've, and a couple of MPG's not recorded on the MythTV system, just the Myth recordings that cause the issue.

Thinking that it was the editing causing the issue, I tried an untouched copy, copied from the TV recordings section to the videos folder, same issue, will play fine until I try and skip ahead. Anyone have a fix in mind for this please? I'm running Mythbuntu 11.10, I want to upgrade but want to ensure that my TdF recordings are safe before bringing my system up to date....

The file eventually copied back into the videos folder may no longer have a usable frame index, which mucks up skipping and rewind.

You might want to try to make a usable index by running ```
mythtranscode --mpeg2 --buildindex --video -i[path-and-filename]
``` When mythtranscode has finished, try playing the video again. Mythtranscode run this way will also leave a zero-byte file "your-filename.mpg.tmp", that can be deleted later.

I have to agree with Rotak: editing commercials out internally in mythtv has to be easier than all the file copying back and forth, particular if the frame index also get torched and has to be rebuilt in the windows PC scenario. 

I've found this script from the wiki [http://www.mythtv.org/wiki/Script_-_RemoveCommercials](http://www.mythtv.org/wiki/Script_-_RemoveCommercials)  particularly useful as a user job for trimming recordings for which I've prepared cutlists. The section of the script where it commercial flags and prepares a cutlist on its own needs to be REM-ed out, of course --you'll want to do your own cutlist and not leave that part to mythtv.

---

### Post by byronmyth on 2012-07-23
Code:
mythtranscode --mpeg2 --buildindex --video -i[path-and-filename]


Worked perfectly, many thanks!

---

