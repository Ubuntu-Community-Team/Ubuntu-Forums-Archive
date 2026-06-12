---
title: "Converting FLV to RVF"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2008-02-23
My kid's got Rockbox loaded on his iPod. We use Ubuntu here. What's the command-line way to convert FLV files to RVF? We've learned how to download FLV files from YouTube, but then need to convert them to Rockbox Video Format (RVF).

---

### Post by CRCarl on 2008-02-24
I looked around, my best guess is that you need to install the mpeg viewer for Rockbox then convert your .flv to .mpeg - 
[URL="http://youmakemedia.com/2006/10/13/converting-flv-to-mpeg-in-linux/"]
http://youmakemedia.com/2006/10/13/converting-flv-to-mpeg-in-linux/[/URL]

You will need to know what the native resolution for your ipod is and make sure you convert to that resolution. 

Let us know if it works.

---

### Post by SuperMike on 2008-02-25
Thanks. That worked. My little son in middle school has been bugging me for weeks for this. Last night I created a little batch file that grabbed the Flash* file out of /tmp after he watches something on YouTube, runs it through ffmpeg per the instructions in the link you provided, and he merely drags it to a folder called Movies on his Rockbox-enabled iPod. We then found out that all Rockboxes now come with the mpeg plugin so he merely goes to Files, chooses his file, clicks the middle button on his iPod, and it begins playing.

YOU SHOULD HAVE SEEN THE EXCITEMENT IN THIS LITTLE KID!!!  It was hard to contain him. He said, "Dad, I like telling my friends at school how cool you are with computers."

Now imagine the rigamarole he would have had to go through if he had used Windows and iTunes, or a Mac and iTunes. There would have been DRM to contend with, shareware tools and no source code to review any questionable intent, potential socket whisper communication in the background as part of the DRM, and so on.

---

### Post by LambdaCalculus379 on 2008-06-23
> **SuperMike said:**
> My kid's got Rockbox loaded on his iPod. We use Ubuntu here. What's the command-line way to convert FLV files to RVF? We've learned how to download FLV files from YouTube, but then need to convert them to Rockbox Video Format (RVF).

As a Rockbox community member, I just want to pop in and let you know that you don't have to worry about the Rockbox Video Format (RVF) unless you're using an old Archos Jukebox Recorder or Ondio device. Nearly ever device, save for those Archos models, use MPEG-2 for video playback.

Hope this helps, and I'm glad you enjoy Rockbox! :)

---

