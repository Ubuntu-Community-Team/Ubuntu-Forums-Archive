---
title: "Anyone managed to get iplayer him and her rollover?"
date: 2011-12-30
forum: Multimedia Software
---

### Post by Filthy Stockings on 2011-12-30
Have managed to get all episodes in HIM AND HER S2 but EP 4 THE ROLLOVER would not download via GET-IPLAYER and found BBC pages stating it had been removed til later in month due to "editing issues".

Have found previously that if programmes move to SIGNED ZONE they won't DOWNLOAD via GIP; even if in the GIP Lists.

Today HIM AND HER EP 5 THE ROLLOVER is there in GIP list BUT when try to DL it fails 

eg

Matches:
224:    Him & Her: Series 2 - 5. The Rollover, BBC Three, Audio Described,Comedy,Guidance,Sign Zone,Sitcoms,TV, default,audiodescribed,signed

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashhigh1,flashhigh2,flashstd1,flashstd2 modes will be tried for version default
INFO: Trying flashhigh1 mode to record tv: Him & Her: Series 2 - 5. The Rollover
INFO: File name prefix = Him_Her_Series_2_-_5._The_Rollover_b017smgn_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, no CRYPTO support!
ERROR: Closing connection: NetStream.Play.StreamNotFound
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/ubuntu/Him_Her_Series_2_-_5._The_Rollover_b017smgn_default.partial.mp4.flv via RTMP
INFO: skipping flashhigh1 mode
INFO: Trying flashhigh2 mode to record tv: Him & Her: Series 2 - 5. The Rollover
INFO: File name prefix = Him_Her_Series_2_-_5._The_Rollover_b017smgn_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, no CRYPTO support!
ERROR: Closing connection: NetStream.Play.StreamNotFound
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/ubuntu/Him_Her_Series_2_-_5._The_Rollover_b017smgn_default.partial.mp4.flv via RTMP
INFO: skipping flashhigh2 mode
INFO: Trying flashstd1 mode to record tv: Him & Her: Series 2 - 5. The Rollover
INFO: File name prefix = Him_Her_Series_2_-_5._The_Rollover_b017smgn_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, no CRYPTO support!
ERROR: Closing connection: NetStream.Play.StreamNotFound
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/ubuntu/Him_Her_Series_2_-_5._The_Rollover_b017smgn_default.partial.mp4.flv via RTMP
INFO: skipping flashstd1 mode
INFO: Trying flashstd2 mode to record tv: Him & Her: Series 2 - 5. The Rollover
INFO: File name prefix = Him_Her_Series_2_-_5._The_Rollover_b017smgn_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, no CRYPTO support!
ERROR: Closing connection: NetStream.Play.StreamNotFound
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/ubuntu/Him_Her_Series_2_-_5._The_Rollover_b017smgn_default.partial.mp4.flv via RTMP
INFO: skipping flashstd2 mode
ERROR: Failed to record 'Him & Her: Series 2 - 5. The Rollover (b017smgn)'
ubuntu@PC-3:~$ 


The programme is NOW on I PLAYER and works for STREAMING but will not even DL even if use the relevant PID given for the streaming programme

eg

  	 	 	 	 	 	    [COLOR=#000000][SIZE=3]get_iplayer --pid=**b017smgn**[/SIZE][/COLOR]


[SIZE=2][B][COLOR=#000000][SIZE=1]ubuntu@PC-3:~$ get_iplayer --pid=b017smgn
get_iplayer v2.79, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

INFO Trying to stream pid using type tv
INFO: pid found in cache
Matches:
224:    Him & Her: Series 2 - 5. The Rollover, BBC Three, Audio Described,Comedy,Guidance,Sign Zone,Sitcoms,TV, default,audiodescribed,signed

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashhigh1,flashhigh2,flashstd1,flashstd2 modes will be tried for version default
INFO: Trying flashhigh1 mode to record tv: Him & Her: Series 2 - 5. The Rollover
INFO: File name prefix = Him_Her_Series_2_-_5._The_Rollover_b017smgn_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, no CRYPTO support!
ERROR: Closing connection: NetStream.Play.StreamNotFound
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/ubuntu/Him_Her_Series_2_-_5._The_Rollover_b017smgn_default.partial.mp4.flv via RTMP
INFO: skipping flashhigh1 mode
INFO: Trying flashhigh2 mode to record tv: Him & Her: Series 2 - 5. The Rollover
INFO: File name prefix = Him_Her_Series_2_-_5._The_Rollover_b017smgn_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, no CRYPTO support!
ERROR: Closing connection: NetStream.Play.StreamNotFound
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/ubuntu/Him_Her_Series_2_-_5._The_Rollover_b017smgn_default.partial.mp4.flv via RTMP
INFO: skipping flashhigh2 mode
INFO: Trying flashstd1 mode to record tv: Him & Her: Series 2 - 5. The Rollover
INFO: File name prefix = Him_Her_Series_2_-_5._The_Rollover_b017smgn_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, no CRYPTO support!
ERROR: Closing connection: NetStream.Play.StreamNotFound
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/ubuntu/Him_Her_Series_2_-_5._The_Rollover_b017smgn_default.partial.mp4.flv via RTMP
INFO: skipping flashstd1 mode
INFO: Trying flashstd2 mode to record tv: Him & Her: Series 2 - 5. The Rollover
INFO: File name prefix = Him_Her_Series_2_-_5._The_Rollover_b017smgn_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, no CRYPTO support!
ERROR: Closing connection: NetStream.Play.StreamNotFound
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/ubuntu/Him_Her_Series_2_-_5._The_Rollover_b017smgn_default.partial.mp4.flv via RTMP
INFO: skipping flashstd2 mode
ERROR: Failed to record 'Him & Her: Series 2 - 5. The Rollover (b017smgn)'
ubuntu@PC-3:~$ get-iplayer -g 224
get_iplayer v2.79, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.[/SIZE]

[/COLOR][/B][/SIZE]
[SIZE=2][/SIZE]Anyone know how to GET it?

Thanks 

SA

---

