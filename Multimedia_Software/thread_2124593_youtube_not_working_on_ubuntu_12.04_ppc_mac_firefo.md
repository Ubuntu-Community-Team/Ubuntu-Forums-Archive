---
title: "youtube not working on ubuntu 12.04 ppc mac firefox"
date: 2013-03-11
forum: Multimedia Software
---

### Post by gusduenas on 2013-03-11
I have firefox and when I try to see any youtube video, first put me the screen that I don't have the plugin, then it will act like is going to display something and finally it will leave me with a black screen in the place of the video....does anyone knows how to fix this. If I don't have youtube tutorials and videos on my ubuntu dual boot on mac g5 ppc...then what is this worth?

Thanks.

---

### Post by Dreamer Fithp Apprentice on 2013-03-12
I'm not sure what kind of package manager is standard on 12.04. If you have Synaptic go to settings, repositories, and check any repositories that aren't checked. Then, with "All" or "not installed" highlighted in the left panel search for "flash" and install something that seems reasonable. Keep trying until it works. "flash plugin installer" should work but I think there are several that will. If you don't use synaptic you can either try to adapt these ideas to whatever you do use or you can install synaptic (and there has never been a better graphical package manager, imo) from the command line thus: ```
sudo apt-get install synaptic
``` Also, you might want to make sure that you haven't accidentally blocked the video from playing with something like Flashblock or NoScript (both of which are great for stopping some sites from bogging you down with resourcing hogging crap, but sometime need to be turned off or adjusted to use other sites, including as a matter of fact, some aspects of this site) or with some setting in Firefox itself (for instance, there is a place in edit, settings, content where you can disable some kinds of scripts. I'm not sure, possibly disabling them blocks youtube. Try enabling them if you have them disabled.)

Also if you haven't already checked you might want to make sure that the problem applies to all youtube videos and isn't just specific to the one you were trying to play. You might want to try updating everything if you don't have it set to do that automatically, just in case. Somewhere above I think you'll find a solution, but if all of that fails, as a long shot, you might want to look up medibuntu and install that repository and more codecs, but I wouldn't really expect that to effect youtube videos.

Good luck with it.

---

