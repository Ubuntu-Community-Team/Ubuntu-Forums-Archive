---
title: "Unable to Burn anything!"
date: 2008-05-19
forum: Multimedia Software
---

### Post by doubad on 2008-05-19
This has been a problem since installing Ubuntu a couple months ago.  I should have done something about this earlier but i'm lazy, only now am I getting really annoyed.  I hate having to boot into windowsxp everytime i want something burnt.  Anyhow, everytime i try to burn something I get "Error while burning: Unhandled error, Aborting"
Oh, and I'm running Hardy

In the log i get more detail:

BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stderr: /dev/scd1: flushing cache
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_set_current_action
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)


It doesn't matter which program I use, I end up in the same situation.




Also, can anyone suggest some DVD Creator software that'll concert a .avi or other video file to a DVD format and create custom DVD title pages?

---

### Post by yabbies on 2008-05-19
tovid is what you want to be able to convert avi to mpg
and todisc which comes with tovid will allow you to custom make menus

it's not in the repos but you can install [here]("http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu")

I'll have to investigate a little further about your burning error

---

