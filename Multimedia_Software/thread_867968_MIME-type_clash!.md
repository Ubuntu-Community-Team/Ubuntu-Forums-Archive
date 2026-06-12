---
title: "MIME-type clash!"
date: 2008-07-23
forum: Multimedia Software
---

### Post by kakila on 2008-07-23
Hi there,
Something funny happened this afternoon.
I wanted to open a C code file I had: simdata.c
The beginning of the file is
```

/**	@file simdata.c
	@brief This file contains the implementations of the functions defined in
	  simdata.h
	@author XXX
	@date 25. Feb, 2008
*/	
#include <stdlib.h>
#include <stdio.h>
#include <math.h>

```
The File Browser (Ubuntu hardy) recognized showed MIME-type: text/x-csrc
but all my text editors: gedit, anjuta, etc... recognize it as **quicktime** video file.
I checked the MIME database and evrything was ok but a friend point me that quicktime videos has content
Type    Value    Offset
String  mdat     12
String  mdat     4

My file is compatible with this description and that was the reason for the editors to consider it a movie... Is this a bug?

BTW: Just by permuting the order of the letter the problem is solved.

---

