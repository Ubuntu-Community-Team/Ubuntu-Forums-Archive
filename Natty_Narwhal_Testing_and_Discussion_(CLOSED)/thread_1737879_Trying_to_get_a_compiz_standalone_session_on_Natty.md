---
title: "Trying to get a compiz standalone session on Natty,.."
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Version Dependency on 2011-04-24
I upgraded to 11.04 from 10.10, where I had a compiz standalone session setup.  But it no longer works in 11.04.  I can't get any window decorators around the windows, and I'm not even sure if compiz itself is loading, since my right-click menu (compiz boxmenu) won't even work.  When I open a terminal and type compiz --replace I get the following.

```
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing composite options...done
Initializing opengl options...done
Initializing gnomecompat options...done
Initializing commands options...done
Initializing grid options...done
Initializing imgsvg options...done
Initializing imgjpeg options...done
Initializing wobbly options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing shift options...done
Initializing cube options...done
Initializing rotate options...done
Initializing td options...done
Initializing animationaddon options...done
Initializing expo options...done
Setting Update "command0"
Setting Update "command1"
Setting Update "run_command0_key"
Setting Update "run_command1_key"
Setting Update "initiate_button"
Setting Update "init_plugin"
Setting Update "init_action"
Setting Update "open_effects"
Setting Update "open_durations"
Setting Update "close_effects"
Setting Update "close_durations"
Setting Update "minimize_effects"
Setting Update "minimize_durations"
Setting Update "shade_effects"
Setting Update "shade_durations"
Setting Update "zoom"


```Attached are screenshots that show how things look when I first log in, and how the terminal looks when I open it (no decorators).  You'll notice that Cairo Dock is a mess too.

---

