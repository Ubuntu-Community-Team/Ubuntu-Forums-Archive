---
title: "Audio suddenly stopped working"
date: 2010-10-24
forum: Multimedia Software
---

### Post by Ol'manScratch on 2010-10-24
Hey y'all
Ubuntu 10.04

I can't get any sound from either online audio or from a CD in drive. I've watched videos with sound with only occasional problems until today.
I have been using MPlayer with internal audio 1 output - analog stereo output. 
When I start a vid, it will begin to D/L and play, but without sound. When I try to check the volume level everything pauses and then my system freezes.
Sometimes it will release in a few seconds, but mostly it won't allow me to close Firefox and if I try to close the tab or window or Firefox, I have to reboot.
Sometimes the vid will D/L without a problem, but no audio on playback.
Oddly, when I bring up the system monitor, processors will show 1 or 2 cores stuck at 100% while the others fluctuate wildly. Download speed falls to almost nothing with occasional blips or nothing.
I checked several sites and they all have the same problem. I have checked my physical connections, and bios settings.

There is an option for a RS780 Azalia controller 1 output Digital Stereo (HDMI) output, but I have not been able to make it work since the system was new. I don't know why.

This is the most recent SYSLOG file. The pulse audio errors have always been there, but since it didn't seem to affect playback, I didn't run it down.

If you need more info, let me know.
Thanks
--------------------------------

Oct 24 16:04:19 jess-desktop kernel: [  889.588898] cdrom: This disc doesn't have any tracks I recognize!
Oct 24 16:04:19 jess-desktop kernel: [  889.609167] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:04:19 jess-desktop kernel: [  889.609173] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:04:19 jess-desktop kernel: [  889.609180] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:04:19 jess-desktop kernel: [  889.609188] end_request: I/O error, dev sr0, sector 0
Oct 24 16:04:19 jess-desktop kernel: [  889.609195] Buffer I/O error on device sr0, logical block 0
Oct 24 16:04:19 jess-desktop kernel: [  889.613728] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:04:19 jess-desktop kernel: [  889.613735] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:04:19 jess-desktop kernel: [  889.613741] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:04:19 jess-desktop kernel: [  889.613750] end_request: I/O error, dev sr0, sector 0
Oct 24 16:04:19 jess-desktop kernel: [  889.613798] Buffer I/O error on device sr0, logical block 0
Oct 24 16:13:03 jess-desktop kernel: [ 1413.606965] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:13:03 jess-desktop kernel: [ 1413.606973] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:13:03 jess-desktop kernel: [ 1413.606981] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:13:03 jess-desktop kernel: [ 1413.606989] end_request: I/O error, dev sr0, sector 0
Oct 24 16:13:03 jess-desktop kernel: [ 1413.606996] Buffer I/O error on device sr0, logical block 0
Oct 24 16:13:03 jess-desktop kernel: [ 1413.607003] Buffer I/O error on device sr0, logical block 1
Oct 24 16:13:03 jess-desktop kernel: [ 1413.607007] Buffer I/O error on device sr0, logical block 2
Oct 24 16:13:03 jess-desktop kernel: [ 1413.607010] Buffer I/O error on device sr0, logical block 3
Oct 24 16:13:03 jess-desktop kernel: [ 1413.607014] Buffer I/O error on device sr0, logical block 4
Oct 24 16:13:03 jess-desktop kernel: [ 1413.607017] Buffer I/O error on device sr0, logical block 5
Oct 24 16:13:03 jess-desktop kernel: [ 1413.607021] Buffer I/O error on device sr0, logical block 6
Oct 24 16:13:03 jess-desktop kernel: [ 1413.607024] Buffer I/O error on device sr0, logical block 7
Oct 24 16:13:03 jess-desktop kernel: [ 1413.607028] Buffer I/O error on device sr0, logical block 8
Oct 24 16:13:03 jess-desktop kernel: [ 1413.607032] Buffer I/O error on device sr0, logical block 9
Oct 24 16:13:03 jess-desktop kernel: [ 1413.609685] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:13:03 jess-desktop kernel: [ 1413.609689] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:13:03 jess-desktop kernel: [ 1413.609698] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:13:03 jess-desktop kernel: [ 1413.609704] end_request: I/O error, dev sr0, sector 0
Oct 24 16:13:03 jess-desktop kernel: [ 1413.629073] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:13:03 jess-desktop kernel: [ 1413.629079] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:13:03 jess-desktop kernel: [ 1413.629085] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:13:03 jess-desktop kernel: [ 1413.629092] end_request: I/O error, dev sr0, sector 0
Oct 24 16:13:03 jess-desktop kernel: [ 1413.632526] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:13:03 jess-desktop kernel: [ 1413.632531] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:13:03 jess-desktop kernel: [ 1413.632536] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:13:03 jess-desktop kernel: [ 1413.632547] end_request: I/O error, dev sr0, sector 0
Oct 24 16:13:03 jess-desktop kernel: [ 1413.634726] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:13:03 jess-desktop kernel: [ 1413.634733] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:13:03 jess-desktop kernel: [ 1413.634741] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:13:03 jess-desktop kernel: [ 1413.634750] end_request: I/O error, dev sr0, sector 0
Oct 24 16:14:35 jess-desktop pulseaudio[1636]: ratelimit.c: 21005 events suppressed
Oct 24 16:14:40 jess-desktop pulseaudio[1636]: ratelimit.c: 9194 events suppressed
Oct 24 16:14:45 jess-desktop pulseaudio[1636]: ratelimit.c: 7670 events suppressed
Oct 24 16:14:50 jess-desktop pulseaudio[1636]: ratelimit.c: 680 events suppressed
Oct 24 16:14:55 jess-desktop pulseaudio[1636]: ratelimit.c: 681 events suppressed
Oct 24 16:15:00 jess-desktop pulseaudio[1636]: ratelimit.c: 683 events suppressed
Oct 24 16:15:05 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:15:10 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:15:15 jess-desktop pulseaudio[1636]: ratelimit.c: 684 events suppressed
Oct 24 16:15:20 jess-desktop pulseaudio[1636]: ratelimit.c: 54921 events suppressed
Oct 24 16:15:25 jess-desktop pulseaudio[1636]: ratelimit.c: 4975 events suppressed
Oct 24 16:15:30 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:15:35 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:15:40 jess-desktop pulseaudio[1636]: ratelimit.c: 684 events suppressed
Oct 24 16:15:45 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:15:50 jess-desktop pulseaudio[1636]: ratelimit.c: 684 events suppressed
Oct 24 16:15:55 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:16:10 jess-desktop pulseaudio[1636]: last message repeated 2 times
Oct 24 16:16:10 jess-desktop pulseaudio[1636]: ratelimit.c: 684 events suppressed
Oct 24 16:16:40 jess-desktop pulseaudio[1636]: last message repeated 5 times
Oct 24 16:17:01 jess-desktop pulseaudio[1636]: last message repeated 5 times
Oct 24 16:17:01 jess-desktop CRON[2084]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 24 16:17:05 jess-desktop pulseaudio[1636]: ratelimit.c: 684 events suppressed
Oct 24 16:17:55 jess-desktop pulseaudio[1636]: last message repeated 9 times
Oct 24 16:17:55 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:18:00 jess-desktop pulseaudio[1636]: ratelimit.c: 684 events suppressed
Oct 24 16:18:15 jess-desktop pulseaudio[1636]: last message repeated 2 times
Oct 24 16:18:15 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:18:40 jess-desktop pulseaudio[1636]: last message repeated 4 times
Oct 24 16:18:40 jess-desktop pulseaudio[1636]: ratelimit.c: 684 events suppressed
Oct 24 16:18:45 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:19:00 jess-desktop pulseaudio[1636]: last message repeated 2 times
Oct 24 16:19:00 jess-desktop pulseaudio[1636]: ratelimit.c: 677 events suppressed
Oct 24 16:19:05 jess-desktop pulseaudio[1636]: ratelimit.c: 684 events suppressed
Oct 24 16:19:10 jess-desktop pulseaudio[1636]: ratelimit.c: 684 events suppressed
Oct 24 16:19:15 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:19:20 jess-desktop pulseaudio[1636]: ratelimit.c: 685 events suppressed
Oct 24 16:19:25 jess-desktop pulseaudio[1636]: ratelimit.c: 3838 events suppressed
Oct 24 16:19:31 jess-desktop pulseaudio[1636]: ratelimit.c: 72686 events suppressed
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616870] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616879] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616886] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616894] end_request: I/O error, dev sr0, sector 0
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616900] __ratelimit: 29 callbacks suppressed
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616904] Buffer I/O error on device sr0, logical block 0
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616912] Buffer I/O error on device sr0, logical block 1
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616916] Buffer I/O error on device sr0, logical block 2
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616920] Buffer I/O error on device sr0, logical block 3
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616923] Buffer I/O error on device sr0, logical block 4
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616927] Buffer I/O error on device sr0, logical block 5
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616930] Buffer I/O error on device sr0, logical block 6
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616933] Buffer I/O error on device sr0, logical block 7
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616937] Buffer I/O error on device sr0, logical block 8
Oct 24 16:24:13 jess-desktop kernel: [ 2083.616940] Buffer I/O error on device sr0, logical block 9
Oct 24 16:24:13 jess-desktop kernel: [ 2083.619701] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:24:13 jess-desktop kernel: [ 2083.619706] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:24:13 jess-desktop kernel: [ 2083.619712] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:24:13 jess-desktop kernel: [ 2083.619718] end_request: I/O error, dev sr0, sector 0
Oct 24 16:24:13 jess-desktop kernel: [ 2083.636826] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:24:13 jess-desktop kernel: [ 2083.636831] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:24:13 jess-desktop kernel: [ 2083.636836] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:24:13 jess-desktop kernel: [ 2083.636843] end_request: I/O error, dev sr0, sector 0
Oct 24 16:24:13 jess-desktop kernel: [ 2083.640244] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 24 16:24:13 jess-desktop kernel: [ 2083.640249] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Oct 24 16:24:13 jess-desktop kernel: [ 2083.640255] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Oct 24 16:24:13 jess-desktop kernel: [ 2083.640263] end_request: I/O error, dev sr0, sector 0

---

### Post by Ol'manScratch on 2010-10-24
One more thing I have noticed
When I switch from a different desktop to the side that is frozen, I see 4 or 5 blank frames which show only for less than 1 second.
Are they like invisible HTML windows or something different?
If this is irrelevant to the above problem, please ignore.

---

