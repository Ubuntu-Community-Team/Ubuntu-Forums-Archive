---
title: "Commercial flagging stopped working after brief power outage"
date: 2008-01-24
forum: Mythbuntu
---

### Post by larsolav on 2008-01-24
I just recently installed Mythbuntu and commercial flagging/skipping worked fine until a 2 second power outage on Tuesday. Here is the full story:

_Monday: _
Recorded "Notes from the underbelly" using one of two AirStar-HD5000 tuners. A couple of hours later, I watched it commercial free without lifting  a finger. So commercial skipping works fine. Frontend is set to automatically skip commercials.
[U]
Tuesday:[/U]
Recorded "Boston Legal". Watched a few minutes after it finished, while the backend was flagging commercials (saw the multicolored cylinder in the watch recordings view). A few minutes into watching a 2 second power outage reset the computer. Upon Myth loading again, it looked like the flagging of "Boston Legal" was still occurring. I did not watch the rest of the show.

I did however go to the Backend setup and checked commercial flagging while recording (I think my system can handle it: Dual core Intel Pentium D 820 2.8GHz, 1 GB RAM)

_Wednesday:_
"Boston Legal" has a red flag in the watch recordings view. Watched the rest of Boston legal. Commercials were not skipped!
Also on Wednesday, recorded "Cashmere Mafia" for the wife. I was able to see the job queue lisitng under the Information menu after flagging was completed, and it said something like: "Finished flagging .... 0 breaks found" 

_Thursday_
This morning I checked "Cashmere Mafia", commercial skipping did not work. Also checked "Notes from the underbelly" from Monday, it did still skip the commercials.

So, I am wondering, What did the power outage do to my commercial flagging? The flagging should be fairly straight forward, as e.g. "Cashmere M" is recorded in HD, and there is a marked black screen between programming and commercials (which are usually in SD)

Does the "found 0 breaks" mean that Myth did not find any commercials to skip? Any way to fix it?

Your help is very much appreciated.

---

### Post by tgm4883 on 2008-01-24
Run the fix/optimise tables in mythbuntu-control-center  If that does not fix it, then manually set them to be reflagged.  Hopefully it will work after that.

---

