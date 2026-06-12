---
title: "Can't burn ISO/CUE/WAV combo in Hardy"
date: 2008-06-13
forum: Multimedia Software
---

### Post by spatterlight on 2008-06-13
[Created a new, identical post in General Help, because I posted this one in the wrong forum. Thought I could delete the original... no dice. PLease answer the post in General Help, rather than this one. Thanks.]

Last night I downloaded a game for my Sega CD system, to replace an original CD game that's long-scarred from fifteen years of getting tossed around. It comes in ISO/WAV format: the game data in an ISO and the CD audio in three WAV tracks. The idea is apparantly to construct your own cuesheet and burn the thing with it. I can't get this to work, though, no matter which program I use.

This is my cuesheet, all paths have been doublechecked to point at the files:

> FILE "/home/martin/Desktop/popful/pop.iso" BINARY
TRACK 01 MODE1/2048
INDEX 01 00:00:00
POSTGAP 00:02:00
FILE "/home/martin/Desktop/popful/Track02.wav" WAV
TRACK 02 AUDIO
PREGAP 00:02:00
INDEX 01 00:00:00
FILE "/home/martin/Desktop/popful/Track03.wav" WAV
TRACK 03 AUDIO
INDEX 01 00:00:00
FILE "/home/martin/Desktop/popful/Track04.wav" WAV
TRACK 04 AUDIO
INDEX 01 00:00:00 


When I select the cue to burn through Brasero, it immediately errors out, with the message "The cue file (pop.cue) appears to be invalid." The log follows:
> 
Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1810)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_RVMQCU.bin toc = /tmp/brasero_tmp_RVMQCU
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao got varg:
BraseroCdrdao deactivating
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_input_type
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao called brasero_job_get_device
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_get_speed
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_set_use_average_rate
BraseroCdrdao called brasero_job_set_current_action
BraseroCdrdao got varg:
	cdrdao
	write
	--device
	/dev/scd0
	--simulate
	-n
	-v
	2
	--speed
	56
	/home/martin/Desktop/popful/pop.cue
BraseroCdrdao launching command
BraseroCdrdao stderr: WARNING: Environment variable 'HOME' not defined - cannot read .cdrdao.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr:   SCSI interface library - (C) Joerg Schilling
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr:   Paranoia DAE library - (C) Monty
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: /home/martin/Desktop/popful/pop.cue:5: Unsupported file type
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao called brasero_job_error
BraseroCdrdao finished with an error
BraseroCdrdao asked to stop because of an error
	error		= 1
	message	= "the cue file (pop.cue) seems to be invalid"
BraseroCdrdao stopping
BraseroCdrdao got killed
Session error : the cue file (pop.cue) seems to be invalid (brasero_burn_record burn.c:2270)

Note that I **know** the cuesheet is well-constructed because it'll burn on my girlfriend's OS X laptop. The problem with that solution is her cd drive's so screwed, it spits out its discs covered with scratches. The game plays in my system, including this CD audio that's giving me heartache, but suffers from ridiculous loadtimes and skipping, due to said scratches. The Sega CD itself plays non-burnt cds just fine, however.

The plain ISO, without the cuesheet, burns fine in Brasero. But it doesn't include music, of course, and I don't want to sit there playing my game in eerie silence.

I tried bringing out the original MP3 files (I read that it'll convert the audio files to CDA, whether they're WAV or MP#) and changing my cuesheet to look like this:
> 
FILE "/home/martin/Desktop/popful/pop.iso" BINARY
TRACK 01 MODE1/2048
INDEX 01 00:00:00
POSTGAP 00:02:00
FILE "/home/martin/Desktop/popful/Track02.MP3" MP3
TRACK 02 AUDIO
PREGAP 00:02:00
INDEX 01 00:00:00
FILE "/home/martin/Desktop/popful/Track03.MP3" MP3
TRACK 03 AUDIO
INDEX 01 00:00:00
FILE "/home/martin/Desktop/popful/Track04.MP3" MP3
TRACK 04 AUDIO
INDEX 01 00:00:00 

The result was more crap. It made Brasero instantly crash, leaving in the directory a temporary file called &#8220;pop.cue~&#8221;, identical in content to the cuesheet. I open it again, try to burn the cue again, it sits there in "preparing to write" mode and throw up a dialogue box saying "Error while burning: the drive can't be locked (ongoing burning process)". After that, it won't burn anything at all, just returning the same error. Restarting Ubuntu gets rid of this problem temporarily; just logging out doesn't, and neither does deleting the temporary file.

I tried Gnomebaker, too. Burning the cue fails with the following output:
> 
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

/home/martin/Desktop/popful/pop.cue:5: Unsupported file type

I thought about using xcdroast, since it's a gui for cdrecord instead of cdrdao. It doesn't work at all in my system, though. I run it and it immediately hangs, no menus, no nothing.

Any takers for this long, involved, stupid problem?

---

