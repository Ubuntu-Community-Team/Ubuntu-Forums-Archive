---
title: "Mythtv with ACPI sometimes fails to shutdown"
date: 2021-06-17
forum: Multimedia Software
---

### Post by ceesquared2 on 2021-06-17
This is a cross post with mythtv.org forums

I  have a combined FE/BE with Mythtv v31 on Ubuntu 18.04.5. TBS 6904  tuner. There is no internet connection. Sometimes( 1 in 20 maybe) the  box fails to shutdown. the display shows BE has shutdown(message posted)  but still FE is shown. Alt-Tab to get a terminal ( I have terminal in  startup). then sudo shutdown -h now works, and box shuts down. The  problem is, of course, that it is intermittent, usually shutdown works  but occasionally it hangs. WTF is going on!
Additional information. 8 Jun 21
FE shows message "Backend shutdown in 5 secs." ( N.B. no countdown  shown) and then it stalls for about 10 secs and the shows message  backend off line.
Alt-Tab to terminal and shutdown entry shows "[FAILED] failed to shut  down plymouth off service" and then later it shows a stop job running  with countdown for 1:30. After countdown the shutdown is completed.
9 Jun 21.
Same Failure but pidof mythbackend returns 1003(mythbackend.service not  tested). Close FE, restart FE, " cannot connect to backend" but still  pidof mythbackend returns 1003
sudo shutdown etc. works but it now gives a blank screen(no terminal  output) and shuts down after about 1:30 as before. The subsequent  restart and shutdown using the remote is OK.

Additional info. 17 Jun 21.
GRUB amended on 16 Jun from "quiet" "splash" to "quiet"
Failed on am 17 Jun as before. sudo shutdown used as before. Blank screen  then full shutdown after 60 sec.
Restarted box as normal. On off selected on remote, there was a 25 sec.  wait in standby and then 5 sec. countdown and then complete shutdown.
N.B. there has been numerous successful startup/shutdowns on ACPI during the intervening time, probably 3 per day.

Additional info. 30 Aug 21.
Same fault as before, but this time I investigated the backend log. In it I found
"Aug 30 17:57:35 mythtv mythbackend: mythbackend[933]: E DVBRead  mpeg/mpegstreamdata.cpp:761 (ProcessPAT) MPEGStream[1](0x7f82b81aa1d8):  ProcessPAT: Program not found in PAT. Rescan your transports.
Aug 30 17:57:35 mythtv mythbackend: mythbackend[933]: E DVBRead  mpeg/mpegstreamdata.cpp:373 (CreatePATSingleProgram)  MPEGStream[1](0x7f82b81aa1d8): Desired program #8931 not found in  PAT.#012#011#011#011Cannot create single program PAT."
I have rescanned before, but it still fails. Could the  "Desired program  #8931 not found in PAT.#012#011#011#011Cannot create single program  PAT." be a clue?

Additional info 18 Nov. 21
Still the same fault. 'sudo reboot -f' works to shutdown and reboot to  get it to restart & shutdown OK. If I had a script that looked for a  PID and after, say, 1 min issued a reboot command as a 'I've had  enough' would that work or would the script stop a normal shutdown?

Additional info 19 Nov 21.
Still the same fault. ps aux | grep myth returns that (I believe)  mythbackend and mythfrontend.real are active and have a pid. However,
killall mythfrontend and mythfrontend.real both reply that 'no process found' ( despite the FE being visible on the screen).
sudo killall mythbackend has no effect( it has a pid of 956). Do I have a  linux problem or a mythtv problem? Thank goodness that  'sudo reboot  -f'  works.
  			 			 									 									 						  		  				 						[ 				 				Top 			]("https://forum.mythtv.org/viewtopic.php?f=29&t=4460#top") 					
 		 		 	  	 	 	 	 		 				[h=2][/h]

---

