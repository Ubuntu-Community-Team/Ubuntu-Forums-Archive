---
title: "get-iplayer stopped working."
date: 2013-06-08
forum: Multimedia Software
---

### Post by Filthy Stockings on 2013-06-08
Hi

Anyone able to help. get-iplayer has stopped working re VIDEO downloads and if try PID for radio downloads. Radio downloads using the get-iplayer --type=radio lists has worked today, though.

Below is sample data but am too much a novice to decipher.

Can anyone help advise please? Thanks in advance.

                         [COLOR=#000000][SIZE=3]Matches: [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]222:    Dad's Army: Series 9 - 2. The Making of Private Pike, BBC Two, Comedy,Sitcoms,TV, default [/SIZE][/COLOR]
  
  [COLOR=#000000][SIZE=3]INFO: 1 Matching Programmes [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Checking existence of default version [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: flashhigh1,flashhigh2 modes will be tried for version default [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Trying flashhigh1 mode to record tv: Dad's Army: Series 9 - 2. The Making of Private Pike [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: File name prefix = Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default                  [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]RTMPDump v2.4-n78-git3a1e20c-ppa8~oneiric [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3](c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Connecting ... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Connected... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: RTMP_ReadPacket, failed to read RTMP packet header [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Command exit code 1 (raw code = 256) [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]WARNING: Failed to stream file /home/ubuntu/Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default.partial.mp4.flv via RTMP [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: skipping flashhigh1 mode [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Trying flashhigh2 mode to record tv: Dad's Army: Series 9 - 2. The Making of Private Pike [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: File name prefix = Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default                  [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]RTMPDump v2.4-n78-git3a1e20c-ppa8~oneiric [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3](c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Connecting ... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Connected... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: RTMP_ReadPacket, failed to read RTMP packet header [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Command exit code 1 (raw code = 256) [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]WARNING: Failed to stream file /home/ubuntu/Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default.partial.mp4.flv via RTMP [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: skipping flashhigh2 mode [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: Failed to record 'Dad's Army: Series 9 - 2. The Making of Private Pike (b00787cq)' [/SIZE][/COLOR]
  

 [COLOR=#000000][SIZE=3]ubuntu@PC-3:~$ get-iplayer --pid=b00787cq --tvmode=flashhigh [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]get_iplayer v2.82+n0-git9503c03, Copyright (C) 2008-2010 Phil Lewis [/SIZE][/COLOR]
  [COLOR=#000000]  [SIZE=3]This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty. [/SIZE][/COLOR]
  [COLOR=#000000]  [SIZE=3]This is free software, and you are welcome to redistribute it under certain [/SIZE][/COLOR]
  [COLOR=#000000]  [SIZE=3]conditions; use --conditions for details. [/SIZE][/COLOR]
  
  [COLOR=#000000][SIZE=3]INFO Trying to stream pid using type tv [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: pid found in cache [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Matches: [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]222:    Dad's Army: Series 9 - 2. The Making of Private Pike, BBC Two, Comedy,Sitcoms,TV, default [/SIZE][/COLOR]
  
  [COLOR=#000000][SIZE=3]INFO: 1 Matching Programmes [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Checking existence of default version [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: flashhigh1,flashhigh2 modes will be tried for version default [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Trying flashhigh1 mode to record tv: Dad's Army: Series 9 - 2. The Making of Private Pike [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: File name prefix = Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default                  [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]RTMPDump v2.4-n78-git3a1e20c-ppa8~oneiric [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3](c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Connecting ... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Connected... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: RTMP_ReadPacket, failed to read RTMP packet header [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Command exit code 1 (raw code = 256) [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]WARNING: Failed to stream file /home/ubuntu/Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default.partial.mp4.flv via RTMP [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: skipping flashhigh1 mode [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Trying flashhigh2 mode to record tv: Dad's Army: Series 9 - 2. The Making of Private Pike [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: File name prefix = Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default                  [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]RTMPDump v2.4-n78-git3a1e20c-ppa8~oneiric [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3](c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Connecting ... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Connected... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: RTMP_ReadPacket, failed to read RTMP packet header [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Command exit code 1 (raw code = 256) [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]WARNING: Failed to stream file /home/ubuntu/Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default.partial.mp4.flv via RTMP [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: skipping flashhigh2 mode [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: Failed to record 'Dad's Army: Series 9 - 2. The Making of Private Pike (b00787cq)' [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ubuntu@PC-3:~$ get-iplayer -g 222 [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]get_iplayer v2.82+n0-git9503c03, Copyright (C) 2008-2010 Phil Lewis [/SIZE][/COLOR]
  [COLOR=#000000]  [SIZE=3]This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty. [/SIZE][/COLOR]
  [COLOR=#000000]  [SIZE=3]This is free software, and you are welcome to redistribute it under certain [/SIZE][/COLOR]
  [COLOR=#000000]  [SIZE=3]conditions; use --conditions for details. [/SIZE][/COLOR]
  
  [COLOR=#000000][SIZE=3]Matches: [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]222:    Dad's Army: Series 9 - 2. The Making of Private Pike, BBC Two, Comedy,Sitcoms,TV, default [/SIZE][/COLOR]
  
  [COLOR=#000000][SIZE=3]INFO: 1 Matching Programmes [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Checking existence of default version [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: flashvhigh1,flashvhigh2,flashhigh1,flashhigh2 modes will be tried for version default [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Trying flashvhigh1 mode to record tv: Dad's Army: Series 9 - 2. The Making of Private Pike [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: File name prefix = Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default                  [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]RTMPDump v2.4-n78-git3a1e20c-ppa8~oneiric [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3](c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Connecting ... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Connected... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: RTMP_ReadPacket, failed to read RTMP packet header [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Command exit code 1 (raw code = 256) [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]WARNING: Failed to stream file /home/ubuntu/Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default.partial.mp4.flv via RTMP [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: skipping flashvhigh1 mode [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Trying flashvhigh2 mode to record tv: Dad's Army: Series 9 - 2. The Making of Private Pike [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: File name prefix = Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default                  [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]RTMPDump v2.4-n78-git3a1e20c-ppa8~oneiric [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3](c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Connecting ... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Connected... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Caught signal: 13, cleaning up, just a second... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: WriteN, RTMP send error 32 (42 bytes) [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: RTMP_ReadPacket, failed to read RTMP packet header [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Command exit code 1 (raw code = 256) [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]WARNING: Failed to stream file /home/ubuntu/Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default.partial.mp4.flv via RTMP [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: skipping flashvhigh2 mode [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Trying flashhigh1 mode to record tv: Dad's Army: Series 9 - 2. The Making of Private Pike [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: File name prefix = Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default                  [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]RTMPDump v2.4-n78-git3a1e20c-ppa8~oneiric [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3](c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Connecting ... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Connected... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: RTMP_ReadPacket, failed to read RTMP packet header [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Command exit code 1 (raw code = 256) [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]WARNING: Failed to stream file /home/ubuntu/Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default.partial.mp4.flv via RTMP [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: skipping flashhigh1 mode [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Trying flashhigh2 mode to record tv: Dad's Army: Series 9 - 2. The Making of Private Pike [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: File name prefix = Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default                  [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]RTMPDump v2.4-n78-git3a1e20c-ppa8~oneiric [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3](c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]Connecting ... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Connected... [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: RTMP_ReadPacket, failed to read RTMP packet header [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: Command exit code 1 (raw code = 256) [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]WARNING: Failed to stream file /home/ubuntu/Dads_Army_Series_9_-_2._The_Making_of_Private_Pike_b00787cq_default.partial.mp4.flv via RTMP [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]INFO: skipping flashhigh2 mode [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]ERROR: Failed to record 'Dad's Army: Series 9 - 2. The Making of Private Pike (b00787cq)' [/SIZE][/COLOR]

---

### Post by Filthy Stockings on 2013-06-08
DIDN'T REALISE OTHERS HAD SAME PROBLEM BUT FOLLOWED SPEARTIP ADVICE 

[http://ubuntuforums.org/showthread.php?t=2152221&page=2](http://ubuntuforums.org/showthread.php?t=2152221&page=2)

AND WORKED SO ...SOLVED. THANKS SO VERY MUCH!

---

