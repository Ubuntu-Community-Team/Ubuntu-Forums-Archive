---
title: "Has get-iplayer just been broken?"
date: 2013-06-07
forum: Multimedia Software
---

### Post by shantiq on 2013-06-07
[U][B]Solution

Thanx to Dinkypumpkin's know-how   there is a very quick fix to this temporary position[/B][/U] get-iplayer users find themselves with

just run:

> [COLOR=#000000][FONT=arial]get_iplayer --prefs-add --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf"[/FONT][/COLOR][COLOR=#DD1144][FONT=Ubuntu Mono][FONT=Consolas]
[/FONT][/FONT][/COLOR]
**===============================**



original post
------------

getting this kind of result on all attempts on TV program yet fine on radio ....   anyone else having same or is it just me?

> get_iplayer v2.82-25-g3547d05-ppa8, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.


Matches:
902:    The Joy of Disco - -, BBC Four, Arts Culture & the Media,Dance & Electronica,Factual,Guidance,Music,TV, default


INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashvhigh1,flashvhigh2,flashhigh1,flashhigh2,flashstd1,flashstd2,flashlow1,flashlow2 modes will be tried for version default
INFO: Trying flashvhigh1 mode to record tv: The Joy of Disco - The Joy of Disco
INFO: File name prefix = The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default                 
RTMPDump v2.4-n78-git3a1e20c-ppa8~raring
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/shan/Videos/The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default.partial.mkv.flv via RTMP
INFO: skipping flashvhigh1 mode
INFO: Trying flashvhigh2 mode to record tv: The Joy of Disco - The Joy of Disco
INFO: File name prefix = The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default                 
RTMPDump v2.4-n78-git3a1e20c-ppa8~raring
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/shan/Videos/The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default.partial.mkv.flv via RTMP
INFO: skipping flashvhigh2 mode
INFO: Trying flashhigh1 mode to record tv: The Joy of Disco - The Joy of Disco
INFO: File name prefix = The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default                 
RTMPDump v2.4-n78-git3a1e20c-ppa8~raring
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/shan/Videos/The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default.partial.mkv.flv via RTMP
INFO: skipping flashhigh1 mode
INFO: Trying flashhigh2 mode to record tv: The Joy of Disco - The Joy of Disco
INFO: File name prefix = The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default                 
RTMPDump v2.4-n78-git3a1e20c-ppa8~raring
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/shan/Videos/The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default.partial.mkv.flv via RTMP
INFO: skipping flashhigh2 mode
INFO: Trying flashstd1 mode to record tv: The Joy of Disco - The Joy of Disco
INFO: File name prefix = The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default                 
RTMPDump v2.4-n78-git3a1e20c-ppa8~raring
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/shan/Videos/The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default.partial.mkv.flv via RTMP
INFO: skipping flashstd1 mode
INFO: Trying flashstd2 mode to record tv: The Joy of Disco - The Joy of Disco
INFO: File name prefix = The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default                 
RTMPDump v2.4-n78-git3a1e20c-ppa8~raring
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/shan/Videos/The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default.partial.mkv.flv via RTMP
INFO: skipping flashstd2 mode
INFO: Trying flashlow1 mode to record tv: The Joy of Disco - The Joy of Disco
INFO: File name prefix = The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default                 
RTMPDump v2.4-n78-git3a1e20c-ppa8~raring
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Caught signal: 13, cleaning up, just a second...
ERROR: WriteN, RTMP send error 32 (42 bytes)
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/shan/Videos/The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default.partial.mkv.flv via RTMP
INFO: skipping flashlow1 mode
INFO: Trying flashlow2 mode to record tv: The Joy of Disco - The Joy of Disco
INFO: File name prefix = The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default                 
RTMPDump v2.4-n78-git3a1e20c-ppa8~raring
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
[B]INFO: Command exit code 1 (raw code = 256)
[/B]WARNING: Failed to stream file /home/shan/Videos/The_Joy_of_Disco_-_The_Joy_of_Disco_b01cqt72_default.partial.mkv.flv via RTMP
INFO: skipping flashlow2 mode
ERROR: Failed to record 'The Joy of Disco - The Joy of Disco (b01cqt72)'
shan@shan:~$ 




---

### Post by proseak on 2013-06-07
It isn't just you - I'm getting something very similar under XP


*INFO: 1 Matching Programmes ERROR: Failed to get iphone URL from iplayer site  INFO: Checking existence of default version INFO: flashvhigh1,flashvhigh2,flashhigh1,flashhigh2,flashstd1,flashstd2 modes will be tried for version default INFO: Trying flashvhigh1 mode to record tv: Up the Women - Episode 2  INFO: File name prefix = Up_the_Women_-_Episode_2_b02l9j0t_default                   RTMPDump 2.4 git-6230845 2011-9-25 (c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL Connecting ... INFO: Connected... ERROR: RTMP_ReadPacket, failed to read RTMP packet header INFO: Command exit code 1 (raw code = 256) WARNING: Failed to stream file F:\iPlayer recordings\Up_the_Women_-_Episode_2_b02l9j0t_default.partial.mp4.flv via RTMP INFO: skipping flashvhigh1 mode INFO: Trying flashvhigh2 mode to record tv: Up the Women - Episode 2  INFO: File name prefix = Up_the_Women_-_Episode_2_b02l9j0t_default                   RTMPDump 2.4 git-6230845 2011-9-25 (c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL Connecting ... INFO: Connected... ERROR: RTMP_ReadPacket, failed to read RTMP packet header INFO: Command exit code 1 (raw code = 256) WARNING: Failed to stream file F:\iPlayer recordings\Up_the_Women_-_Episode_2_b02l9j0t_default.partial.mp4.flv via RTMP INFO: skipping flashvhigh2 mode INFO: Trying flashhigh1 mode to record tv: Up the Women - Episode 2  INFO: File name prefix = Up_the_Women_-_Episode_2_b02l9j0t_default                   RTMPDump 2.4 git-6230845 2011-9-25 (c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL Connecting ... INFO: Connected... ERROR: WriteN, RTMP send error 10054 (42 bytes) ERROR: RTMP_ReadPacket, failed to read RTMP packet header INFO: Command exit code 1 (raw code = 256) WARNING: Failed to stream file F:\iPlayer recordings\Up_the_Women_-_Episode_2_b02l9j0t_default.partial.mp4.flv via RTMP INFO: skipping flashhigh1 mode INFO: Trying flashhigh2 mode to record tv: Up the Women - Episode 2  INFO: File name prefix = Up_the_Women_-_Episode_2_b02l9j0t_default                   RTMPDump 2.4 git-6230845 2011-9-25 (c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL Connecting ... INFO: Connected... ERROR: RTMP_ReadPacket, failed to read RTMP packet header INFO: Command exit code 1 (raw code = 256) WARNING: Failed to stream file F:\iPlayer recordings\Up_the_Women_-_Episode_2_b02l9j0t_default.partial.mp4.flv via RTMP INFO: skipping flashhigh2 mode INFO: Trying flashstd1 mode to record tv: Up the Women - Episode 2  INFO: File name prefix = Up_the_Women_-_Episode_2_b02l9j0t_default                   RTMPDump 2.4 git-6230845 2011-9-25 (c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL Connecting ... INFO: Connected... ERROR: WriteN, RTMP send error 10054 (42 bytes) ERROR: RTMP_ReadPacket, failed to read RTMP packet header INFO: Command exit code 1 (raw code = 256) WARNING: Failed to stream file F:\iPlayer recordings\Up_the_Women_-_Episode_2_b02l9j0t_default.partial.mp4.flv via RTMP INFO: skipping flashstd1 mode INFO: Trying flashstd2 mode to record tv: Up the Women - Episode 2  INFO: File name prefix = Up_the_Women_-_Episode_2_b02l9j0t_default                   RTMPDump 2.4 git-6230845 2011-9-25 (c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL Connecting ... INFO: Connected... ERROR: RTMP_ReadPacket, failed to read RTMP packet header INFO: Command exit code 1 (raw code = 256) WARNING: Failed to stream file F:\iPlayer recordings\Up_the_Women_-_Episode_2_b02l9j0t_default.partial.mp4.flv via RTMP INFO: skipping flashstd2 mode ERROR: Failed to record 'Up the Women - Episode 2 (b02l9j0t)' **Recording complete*

---

### Post by shantiq on 2013-06-07
hmmmmmmmmm   probably some update from the Beeb site  ....    i do not understand why it goes well on radio programs tho  ....     puzzled  ....   as per usual

someone might know what has/is happening

---

### Post by speartip on 2013-06-07
When did you last download a program.
Get-iplayer worked fine for me the day before yesterday.
You do need to be using the latest version though.
[https://launchpad.net/~jon-hedgerows/+archive/get-iplayer](https://launchpad.net/~jon-hedgerows/+archive/get-iplayer)

---

### Post by shantiq on 2013-06-07
speartip if that is ok with you or anyone else can you try to start download a tv program today...   see if it works  ...   was fine for me last 2 days;  might be a temporary glitch or else might be a more solid change   [at the moment trying to ascertain  if it is a kink on my system or a widespread occurrence]


and yes i am using hedgerows PPA

---

### Post by mixmaster on 2013-06-07
This happened to me today.  Could not download a program from BBC4 and could not re-download (with --force) a program I successfully downloaded earlier this week.

---

### Post by shantiq on 2013-06-07
thank you mm  ...   

did you also get   **INFO: Command exit code 1 (raw code = 256) **&#8203;?

---

### Post by hutchinsfairy on 2013-06-07
I had this on Windows XP SP3. Resolved it by updating my "get_iplayer.pl" file from the maintainer's website here: [http://git.infradead.org/get_iplayer.git/blob_plain/HEAD:/get_iplayer](http://git.infradead.org/get_iplayer.git/blob_plain/HEAD:/get_iplayer)

I also deleted my .swfinfo file found in "My Documents" but not sure if this was necessary...

---

### Post by berrys66 on 2013-06-07
I'm getting exactly the same thing on Win7 and Centos 6.4. The last time I successfully downloaded a program was on 5th June.

[Edit]
I am already running the most recent version of the get_iplayer perl script - v2.82
[/Edit]

---

### Post by mixmaster on 2013-06-07
> **shantiq said:**
> thank you mm  ...   

did you also get   **INFO: Command exit code 1 (raw code = 256) **&#8203;?

Yup, got that also.

Tried deleting .swfinfo and refreshing get_iplayer.pl to no effect.

---

### Post by proseak on 2013-06-07
I found this page useful;

[http://lists.infradead.org/pipermail/get_iplayer/2013-June/004206.html](http://lists.infradead.org/pipermail/get_iplayer/2013-June/004206.html)

---

### Post by shantiq on 2013-06-07
ok that works   had seen it earlier [here]("https://github.com/dinkypumpkin/get_iplayer/wiki/githead")   but not tried it

it is the latest and works
on Ubuntu   I had to do this

copy  [new code text]("http://git.infradead.org/get_iplayer.git/blob_plain/HEAD:/get_iplayer") and paste here instead of old one


```
sudo gedit /usr/bin/get-iplayer
```   

I did not bother replacing get[COLOR=#ff0000]**_**[/COLOR][COLOR=#000000]iplayer  as i never use it written that way but do same if you wish to add


**HOPefully **

when Jon Hedgerows next updates PPA it will pick up where we have left it now
[/COLOR][COLOR=#000000]Until then it is a fix will mark as solved... again thanx hutchinsfairy and all of you guys[/COLOR]

---

### Post by mixmaster on 2013-06-07
I pulled the change line from the bottom of the thread proseak linked to, edited it into get_iplayer.pl and it seems to work fine on windoze (am I allowed to mention that word here?).

Then I noticed that shantiq had already done all the hard work.  Ho hum.

Thanks guys, I was getting very frustrated about this.

---

### Post by Nooneexpects on 2013-06-07
Has also happend to me, since about the 5 Jun 13. I am using a Ubuntu 12.10 on a HTPC server.

INFO Connected...
Caught signal: 13, cleaning up, just a second...
ERROR: WriteN, RTMP send error 32 (42 bytes)
ERROR: TRMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file..

Using version 2.82 of get_iplayer I am using.

---

### Post by dinkypumpkin on 2013-06-08
No need to edit the get_iplayer script to fix BBC downloads.  You can temporarily update your preferences until a new get_iplayer release arrives. See:[URL="https://github.com/dinkypumpkin/get_iplayer/wiki/swfurl"]

https://github.com/dinkypumpkin/get_iplayer/wiki/swfurl[/URL]

---

### Post by speartip on 2013-06-08
Thanks dinkypumpkin.
So for those in any doubt, just open a terminal & copy & paste the following command:
```
[COLOR=#333333][FONT=Consolas]get_iplayer --prefs-add --rtmp-tv-opts[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**=**[/FONT][/COLOR][COLOR=#DD1144][FONT=Consolas]"--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf"[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]
[/FONT][/COLOR]
```

Get-iplayer should now work correctly.

---

### Post by shantiq on 2013-06-08
---

---

### Post by Merrattic on 2013-06-08
Many many thanks for this fix :D

---

### Post by broomie on 2013-06-09
Shantiq's workaround worked for me!  Many thanks  - -what does this command do?

---

### Post by shantiq on 2013-06-09
[COLOR=#000000][FONT=arial]hi broomie    it  corrects the new settings from the Beeb   but you cannot use the change of get-iplayer code page in /usr/bin for the new one and run

the command  ```
get_iplayer --prefs-add --rtmp-tv-opts**=**"--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf"
```
[/FONT][FONT=Ubuntu Mono][FONT=Consolas][FONT=arial]
that puts you back to where you were  ... i tried it   :::]]]


then had to go to [/FONT][/FONT][/FONT][/COLOR]sudo gedit /home/username/.get_iplayer/options   and remove the line
[COLOR=#000000][FONT=Ubuntu Mono][FONT=Consolas][FONT=arial]



So to summarize either replace [/FONT][/FONT][/FONT][/COLOR][COLOR=#000000][FONT=arial]get-iplayer code page in /usr/bin for the new one or use the command
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono][FONT=Consolas][FONT=arial]
Dinkypumpkin is the one who knows how it is rigged up  so i placed the command as solution on first post    [but the other route works equally well]   ....       is what i understand [/FONT][/FONT][/FONT][/COLOR]:KS    i am personally happy with the /usr/bin swap
[COLOR=#000000][FONT=Ubuntu Mono][FONT=Consolas][FONT=arial]

Anyway most of us are with Hedgerows PPA as i understand it; no doubt will soon be updated  ;   in the meantime VERY grateful to Dinky here  
[/FONT][/FONT][/FONT][/COLOR][COLOR=#DD1144][FONT=Ubuntu Mono][FONT=Consolas]
[/FONT][/FONT][/COLOR]

---

### Post by dinkypumpkin on 2013-06-09
shantiq: You're right - it's redundant to both edit /usr/bin/get_iplayer and add the SWF player URL as a preference.  FWIW, I recommend setting the preference rather than editing the script.  It's less error-prone, no permission issues, easier to undo.  BTW, you don't need to edit $HOME/.get_iplayer/options to remove the preference.  Just run the same command again with --prefs-del instead of --prefs-add:

```

get_iplayer --prefs-del --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf"
```

---

### Post by shantiq on 2013-06-10
again thank you... crystal-clear

---

### Post by SirPecanGum on 2013-06-10
Thank you!

I did it the old school way with gedit replacing line:

```
http://www.bbc.co.uk/emp/revisions/18269_21576_10player.swf?revision=18269_21576
```

with:

```
[http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf
```

as per details on this page: [http://lists.infradead.org/pipermail/get_iplayer/2013-June/004206.html](http://lists.infradead.org/pipermail/get_iplayer/2013-June/004206.html)

---

### Post by kfarq64 on 2013-06-10
Registered to post a quick note to say 'You Beauties!'

The get_iplayer Cronjob on my Pi had failed and as always the *nix community came up trumps.

Thanks chaps.

---

### Post by rjmac on 2013-06-16
> **speartip said:**
> Thanks dinkypumpkin.
So for those in any doubt, just open a terminal & copy & paste the following command:
```
[COLOR=#333333][FONT=Consolas]get_iplayer --prefs-add --rtmp-tv-opts[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**=**[/FONT][/COLOR][COLOR=#DD1144][FONT=Consolas]"--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf"[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]
[/FONT][/COLOR]
```

Get-iplayer should now work correctly.
Thank you. Working fine now.

---

### Post by shantiq on 2013-06-16
just to say guys the PPA has now been updated
so all previous info is no longer needed
[it was there to bridge us all between Beeb change and PPA update]

all you need to do is to update

```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove



```

if you had changed your preferences you can now rectify that with Dinkypumpkin's line

```
[COLOR=#000000][FONT=Ubuntu Mono]get_iplayer --prefs[/FONT][/COLOR][COLOR=#ff0000][FONT=Ubuntu Mono]**-del**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf"[/FONT][/COLOR]

```


and until next changes Roberto should be your tio if you get my drift

---

### Post by chasboz on 2013-06-29
I can confirm that: get_iplayer --prefs-add --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf" works on Suse 12.13, thanks to Shantig.

---

