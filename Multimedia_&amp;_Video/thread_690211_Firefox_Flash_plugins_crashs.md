---
title: "Firefox Flash plugins crashs"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by Nigggo on 2008-02-07
I installed restricted extras and at first firefox plugin worked perfectly but now i have a problem. if launch firefox or swiftweasel and run a page with flash, e.g youtube i see the video for a short moment and then it disaperars and i can only see a grey frame were the video is used to be. after a few restarts i could have luck and watch the full video but most times it disaperars before even starting to play.
does anyone have an idea what the problem might be?

---

### Post by gandaran on 2008-02-08
try this
  
          sudo apt-get remove flashplugin-nonfree

          sudo apt-get update

          sudo apt-get install flashplugin-nonfree

and just to be on the safe side do this to 
       
          sudo apt-get remove gnash

---

