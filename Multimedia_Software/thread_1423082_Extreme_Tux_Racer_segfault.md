---
title: "Extreme Tux Racer segfault"
date: 2010-03-06
forum: Multimedia Software
---

### Post by mahy on 2010-03-06
Hello there,

I'm running Ubuntu 9.10 on an older machine with ATI Radeon 9200 card with the "radeon" driver. It works quite well, but fails when I try Extreme Tux Racer. The game starts okay, then I select the "practice" variant and course and click "start", but then the application segfaults. The terminal tells me the following:

```

% etracer
Extreme TuxRacer SVN Development --  http://www.extremetuxracer.com 
(c) 2007 The ETRacer team
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
ETRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

%%% etracer warning: Attempt to bind to Texture unloaded texture: `b-herring_run_icon'

*********************************WARN_ONCE*********************************
File radeon_dma.c function radeonReleaseDmaRegions line 345
Leaking dma buffer object!
***************************************************************************
Segmentation fault
```

Ideas, anyone? I'd be most grateful.

---

