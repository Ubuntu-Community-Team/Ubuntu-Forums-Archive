---
title: "dvd writting fails"
date: 2009-09-19
forum: Multimedia Software
---

### Post by qui8 on 2009-09-19
every time i try to burn dvd with brasero (directly data from my HD and through .iso image), the burn process dies just at the bigining. there is no data on the blank dvd. i have copied the last parts of the log that i felt may be useful. any help?? the log goes as given below: 

BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stderr: Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  53 00 00 00 00 00 20 B0 CB 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    0.019s
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.000s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot open new session.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo had 255 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)

---

