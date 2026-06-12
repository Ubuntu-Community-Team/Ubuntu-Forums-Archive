---
title: "Mirobridge and mp3s"
date: 2010-02-05
forum: Mythbuntu
---

### Post by diskmaster23 on 2010-02-05
I am running Mythbuntu 9.04, Mirobridge, and Mythtv .22. I have a few RSS feeds that are audio, but the audio doesn't play when I go into my "Watch Recordings". I know Mplayer can handle mp3s, but why doesn't it play. Is there something I can do?

---

### Post by RDV on 2010-02-05
diskmaster23, 
I wrote MiroBridge and there are a few things to note:
1) Apparently the internal video player has issues with mp3 files. The internal player is all you can use in the Watched Recordings screen.
2) The MiroBridge wiki states under the limitations section that it does not support audio feeds. It is likely that the RSS feed you used is not marked by Miro as an audio file so has slipped through the filtering.

I have not tried this but you may have an option to add those audio RSS feeds to the mirobridge.conf file section [mythvideo_only] (see the mirobridge-example.conf file for details). Now add in MythVideo set up the file extension 'mp3' and associate that file extension to a music player (e.g. mplayer as you mention). 

This suggestion will not work if you are using Video storage groups as the Internal player is your only choice with storage groups.

The downside of this option is that you will need to manually remove the audio file through MythVideo 'd' delete menu, rather than normal MiroBridge expiry after X number of days.

It is too late in the MythTV v0.23 development cycle to add audocasts but it is on my list after many other priorities. Unlike Miro videos, audio files would need to be integrated with MythMusic.

Again I have not tried the suggestion I gave you but it should work in principal.

---

### Post by diskmaster23 on 2010-02-05
I think the mirobridge is great. There are certainly improvements to be made, but it works very well. So... thank you for developing it. 

> 2) The MiroBridge wiki states under the limitations section that it does not support audio feeds. It is likely that the RSS feed you used is not marked by Miro as an audio file so has slipped through the filtering.
Yeah I know the Wiki said that the Mirobridge does not support audio feeds, but I have added the audio rss feeds to the video feeds and they are automatically downloading. However, I cannot 'view' the audio feeds. 

> Now add in MythVideo set up the file extension 'mp3' and associate that file extension to a music player (e.g. mplayer as you mention).
I will see if I can add the mp3 extension to the MythVideo. Do you have any suggestions on where to add the mp3 extension to the MythVideo? 

> The downside of this option is that you will need to manually remove the audio file through MythVideo 'd' delete menu, rather than normal MiroBridge expiry after X number of days.
Since the audio feeds are coming through as an video feed, I am assuming they will delete themselves after awhile. I may just leave it to expire on its own. It may take up more space, but I am not worried about the audio files taking up too much space.

> Unlike Miro videos, audio files would need to be integrated with MythMusic.
I have tried getting MythMusic to 'view' or access the files, but I haven't had much luck. Hopefully MythVideo will be my solution, otherwise I will just continue to listen to my audio feeds via NFS to my laptop.

I will keep you updated on my progress. Thanks for your help.

---

### Post by RDV on 2010-02-05
> **diskmaster23 said:**
> 
...
I will see if I can add the mp3 extension to the MythVideo. Do you have any suggestions on where to add the mp3 extension to the MythVideo? 
...
Since the audio feeds are coming through as an video feed, I am assuming they will delete themselves after awhile. I may just leave it to expire on its own. It may take up more space, but I am not worried about the audio files taking up too much space.

To add the file extension for the audio files and the external player you want:
Utilities/Settings->Setup->Media Settings->Video Settings->File Types

If you use the suggestion I have given you then your audio files are actually copied into a MythVideo directory and removed from Miro. That is why I said you could not rely on Miro's to eventually expire/delete the files.

Another alternative is that you could mark these audio files as "Watched" in the "Watch Recorded" screen and they will get copied to MythVideo the next time MiroBridge runs. This will maintain the connection with Miro and its automated expiry of downloaded files.

In any case you need to add the file extension and the external player in MythVideo to play these files.

Good luck

---

### Post by diskmaster23 on 2010-02-05
Thanks that helped.

The one thing I should caution users is that there is no OSD. I haven't figured out how to get a OSD working for mp3. In the command-line it shows up, but in mythtv, nothing shows up.

---

### Post by RDV on 2010-02-05
diskmaster23, are you saying you got the sound to play? If you did then why would you expect any OSD to display when the file is not a video? Also if the sound is playing is it in the Watch Recordings screen or in MythVideo like we discussed?

---

### Post by diskmaster23 on 2010-02-06
I wasn't expecting any OSD for a sound file, but I was trying to figure out how you can get mplayer to display a OSD. I am not that familiar with the command-line mplayer. Do you or anyone have any suggestions?

The sound only works in MythVideo, not Watch Recorded shows.It is better than nothing.

---

