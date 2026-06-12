---
title: "Ubuntu  15.04 no right channel sound on Creative Xtreme Audio (CA0106)"
date: 2015-09-18
forum: Multimedia Software
---

### Post by lukebenes on 2015-09-18
After a fresh install of Ubuntu  15.04 and on the liveCD, There is no sound on right channel. But it  works perfectly in Win 7/10. It also worked perfectly on  Ubuntu 12.04  My sound card is Creative  Xtreme Audio (PCI CA0106). 				

Solution [**[COLOR=#000000]by mladenovicp[/COLOR]**]("http://ubuntuforums.org/member.php?u=1918319") from [here]("http://ubuntuforums.org/showthread.php?t=2218322"). 

 			 				[INDENT] 					[COLOR=#333333][FONT=Lucida Grande]1. launch alsamixer (from console).[/FONT][/COLOR] I've started with "sudo alsamixer".
[COLOR=#333333][FONT=Lucida Grande]2. Select your soundcard (press F6), mine was CA0106.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]3. Look for stereo items with one channel muted (text beneath bars looks like "63<>0").[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]4. Make volumes equal (63<>63) using keyboard controls (UP/DOWN, Q/Z, E/C).[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]5. Exit (ESC), no need to save manually.[/FONT][/COLOR] 				
[/INDENT] 			
  			   		
The ALSA Bug Tracker is discontinued. Link from the main ALSA site is a 404. What's the best way to get this fixed for everyone?



[alsa-info.sh results.]("http://www.alsa-project.org/db/?f=e3ae99437c3d283b35cac7c33ace996bedf43a16")

---

