---
title: "mythtv fails to skip flagged commercials"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by sephirothsigep on 2008-02-04
I have a frontend backend desktop setup for mythtv, i have mythweb installed and working. the problem that i am having is with the playback of recorded shows. mythtv is flagging commercials and everything like that but i am not being able to skip them.

backend config: 
General > 6th option screen titled JobQueue(Host-Specific) has the following 
```
                    job queue start time :  00:00
                    jjob queue end time : 23:59
                    [x] Allow Commercial Detection jobs
                    [x] Allow Transcoding jobs
```

General >7th option screen titled Job Queue(Global) has the following
```
                    [ ]run jobs only on original recording host
                    [x]start auto-commercial flagging jobs when the recording starts

                    commercial flagger command  : mythcommflag
                    transcoder command              : mythtranscode
```

frontend config
utilities /setup > setup > tv Settings > General > 3rd option screen titled General (Jobs) has the following 
```
                    [x] commercial flag new recordigns
                    commercial skip method : all available methods
                    [ ] strict commercial detection
```

utilities /setup > setup > tv settings > playback > 7th option screen titled Commercial Skip has the following 
```
                     Automatically skip commercials: Automatically skip
                     commercial skip auto-rewind amount : 0 
                     commercial skip notify amount : 0 
                     maximum commercial skip (in seconds): 3600
                     [ ] skip blank frames after commercials 
```


mythweb backend status has the following to say 

```
Job Queue
Jobs currently in Queue or recently ended:
Sun 2/3 10:00 PM - Cold Case - Flag Commercials
Cold Case (10:00 PM-11:00 PM)
That Woman

Job: Flag Commercials
Status: Finished
Status Time: Mon Feb 4 3:15 PM
Host: TheGreenMachine

Comments:
Finished, 4 break(s) found.

```

So with all this info can anyone tell me how come i cannot skip commercials.

---

### Post by KyleAnderson on 2008-02-05
It certainly does sound like commercial "Detection" is working. What happens when you try to skip the commercial, does it say something like "Already At End, cannot skip"? Or does it not say anything at all.

If it doesn't say anything at all, I would double check your key bindings or remote. If it says already at end.. I'll have to think about it more. One thing you might need to do is repair the tables if there has been a bad shutdown. (Happens on mine if I lose power, and seek tables get corrupt).

---

### Post by sephirothsigep on 2008-02-07
NOTE : on the keyboard i have not changed any of the buttons that control anything.

Yes if i press Z it will skip the commercial but its suppose to skip them automatically that is how i have it set. also if i set it to notify before skipping or how ever that is worded it does not notify me. but yes my commercial skip does work if i press the skip button but i dont want to have to do that, and i should not have to.

---

