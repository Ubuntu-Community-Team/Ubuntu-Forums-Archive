---
title: "rewind / ff not working"
date: 2009-12-06
forum: Mythbuntu
---

### Post by pinacate on 2009-12-06
Rewind and FF are not working on my mythbuntu 9.10 system. They work ok for live tv but fail on playback of recordings.

I've set up my StreamZap remote to send > or < when I push FF/Rewind. When myth receives the first push of say >; the screen says its playing at 3x but its not. The sound stops but the video continues at the normal rate. if I push > again the on screen it says 5x but the video freezes. I get a similar behavior for rewind.

The relevant piece of my lircrc file looks like this:

begin
   remote = Streamzap_PC_Remote
   prog = mythtv
   # fast forward
   button = >>
   config = >
end

Does anyone have any suggestions?
Thanks

---

### Post by Caps18 on 2009-12-07
If you have ever run out of disk space, one thing that happens to me is that the fast forward/rewind tables get corrupted and need to be rebuilt.

I think in the Control Center there is an Optimize tables button (at least in 7.10) that fixes them.

---

### Post by pinacate on 2009-12-07
Good suggestion. I found the 'Optimize Tables' button. I don't think its working. When I click on it the screen momentarily shows a window and returns. 

I recently forced commflagged =0 in the tables and ran mythcommflag. That cleared up some errors but the ff/rewind problem remains.

Is there a command line tool for rebuilding the ff/rewind tables?

---

### Post by larsolav on 2009-12-08
```
sudo mysqlcheck -r -umythtv -pMYTHTVPSSWRD mythconverg
```

This is how I have fixed my tables. I also always just get the flashing screen when clicking the "optimize tables".

Replace MYTHTVPSSWRD with your MythTV database password.

---

### Post by pinacate on 2009-12-09
Thanks Larsolav that worked much better. 

I'm now seeing ff/rewind work on newly recorded shows. I can live with that.

---

