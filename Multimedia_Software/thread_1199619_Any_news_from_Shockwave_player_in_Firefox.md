---
title: "Any news from Shockwave player in Firefox?"
date: 2009-06-29
forum: Multimedia Software
---

### Post by ^_Pepe_^ on 2009-06-29
Hi everyone!

My 5-year son, said yesterday:

Hey, dad, this game [http://www.toonami.es/juegos/starwars/ladooscuro/index.jsp](http://www.toonami.es/juegos/starwars/ladooscuro/index.jsp) doesn't work!

Ok! I said. Something wrong with flassshhhh! again!

But not! Shockwave player this time. I told him to go to other one, and...I went onto the laptop (Ubuntu-ed as well), to seek some info!

Oh my god! New limitation!

Does anybody know if is there any clear workaround to this?

I have read something about installing Firefox for windows in Wine...but...this is not a solution... :-(

Thanks in advance!

Regards,
^_Pepe_^

---

### Post by mcduck on 2009-06-29
Sorry, running Windows version of Shockwave and Firefox is the *only* solution.

Macromedia never showed any interest towards making a Linux plugin for Shockwave, and it doesn't really seem like Adobe would ever do that either.

---

### Post by ^_Pepe_^ on 2009-06-29
> **mcduck said:**
> Sorry, running Windows version of Shockwave and Firefox is the *only* solution.

Macromedia never showed any interest towards making a Linux plugin for Shockwave, and it doesn't really seem like Adobe would ever do that either.

Thank you! Bad news at all! 

Regards,
^_Pepe_^

---

### Post by sofree on 2009-10-23
It works. You have to be sure that you use only the macromedia plugin.
In FireFox, type in URL 'about: plugins' and you will see all installed plugins. You should have only : 
libflashplayer.so Shockwave Flash 10.0 r32

If you have another plugin like : libswfdec-0.8-0      SWF (Macromedia     Flash) decoder library, you have to uninstall it with Synaptic or other.

After that, if you don't have it yet, download and install flash player version 10.0.32 from : [http://get.adobe.com/fr/flashplayer/](http://get.adobe.com/fr/flashplayer/)
and select ubuntu version (.deb).

---

### Post by vinutux on 2009-10-23
That old crap [shockwave] still supported some sites...really bad

install wine and windows version FF and shockwave player......

---

### Post by jackRome on 2009-11-03
> **sofree said:**
> It works. You have to be sure that you use only the macromedia plugin.
In FireFox, type in URL 'about: plugins' and you will see all installed plugins. You should have only : 
libflashplayer.so Shockwave Flash 10.0 r32

If you have another plugin like : libswfdec-0.8-0      SWF (Macromedia     Flash) decoder library, you have to uninstall it with Synaptic or other.


It worked!! 
thanks!!

---

### Post by Miche on 2009-11-04
hi all, 

sorry but I'm a little dolt sometimes. 
My flash player continues not to work and I cannot correctly display many pages. 
I had a check on synaptic for macromedia (under Description and Name) but I have nothing. 
Here's what I have under about:plugins:

**Shockwave Flash**

 File name:  npwrapper.libflashplayer.so 
Shockwave Flash 10.0 r32   
MIME Type 
application/x-shockwave-flash
application/futuresplash

Description 
Shockwave Flash
FutureSplash 

Suffixes 
swf
spl

Enabled
Yes 
Yes

Is a matter of npwrapper?
Any help would be greatly appreciated. 
Many thanks!

Michele

---

### Post by Miche on 2009-11-04
I found the solution. 
The new FF does everything by itself, just clicking on the icon of missed plugins. 
Easy and fast. 

By the way it come back to the old versions:
File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999
Thanks all.

---

