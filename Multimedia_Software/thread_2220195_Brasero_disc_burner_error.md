---
title: "Brasero disc burner error"
date: 2014-04-27
forum: Multimedia Software
---

### Post by agemini68 on 2014-04-27
I tried to make a disc of 14.04, It failed and have the following log: 

BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Asynchronous SCSI error on SYNCHRONIZE CACHE: [3 73 04] Medium error. Program memory area update failure.
BraseroLibburn Closing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async SYNCHRONIZE CACHE failed after 2.0 seconds
BraseroLibburn Closing track 01  (absolute track number 1)
BraseroLibburn Asynchronous SCSI error on CLOSE TRACK SESSION: [3 73 04] Medium error. Program memory area update failure.
BraseroLibburn Async CLOSE TRACK SESSION failed after 2.4 seconds
BraseroLibburn Closing session
BraseroLibburn Asynchronous SCSI error on CLOSE TRACK SESSION: [3 73 04] Medium error. Program memory area update failure.
BraseroLibburn Something went wrong
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
    error        = 15
    message    = "An error occurred while writing to disc"
BraseroLibburn stopping
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2856)

Anyone know the fix?

---

### Post by agemini68 on 2014-04-28
Went into the software center and tried a couple of other programs. I tried simple burn and got the same kind of message, then I found one called K3B and was able to successfully burn a disc.

---

### Post by ibjsb4 on 2014-04-28
K3b is an excellent program.  If you want something that just gets the job done there is 'xfburn'.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by nnjrob2 on 2014-04-28
> **ibjsb4 said:**
> K3b is an excellent program**_.  If you want something that just gets the job done there is 'xfburn'.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


I agree with that. I used to have nothing but trouble with Brassero, none with k3b. Haven't tried xfburn..yet.

---

