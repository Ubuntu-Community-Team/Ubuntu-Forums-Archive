---
title: "ROSENGARDEN can't store files"
date: 2008-04-04
forum: Multimedia Production
---

### Post by drumanart on 2008-04-04
Hi everybody.
When I'm try to store files in ROSENGARDEN I get the message:

[B]Could not save document at /usr/share/apps/rosegarden/examples/Martin.rg

Error was : Could not open file '/usr/share/apps/rosegarden/examples/Martin.rg' for writing[/B]

Any idear?

---

### Post by morganpatrick on 2008-04-04
I wouldn't put my files there if i were you. I would keep them somewhere in your home folder:

I keep mine in /home/morgan/Music Project/Rosegarden/xxx.rg

You probably don't have write permissions to that folder.

---

### Post by drumanart on 2008-04-05
Thks, that's it. 
No the next problem I have to solve is the fact that in playback sometimes I don't have sound. I can allway record midi and the level meters indicates the levels, but where is the sound gone? If I open one of the example from the libray, sometimes I get sound but after rebooting the computer the same file with a unchanged configuration keeps without any sound.
Thks

---

### Post by morganpatrick on 2008-04-05
Are you using jack? And what is producing the sound? Is it a wav file, softsynth, or what?

---

### Post by drumanart on 2008-04-06
Yes I'm using Jack.
If I open the example file "bogus-serf-jam.rg" the program is configured with a softsynth, (Creative SBlive). Sometimes it works, sometimes not. If I select midi external device (using an other computer to create sound) I have always sound.
On the other hand If I open ROSENGARDEN (with Jack allready open of course) I get the error:  
[B]Failed to connect to JACK audio server.
Rosegarden could not connect to the JACK audio server. This probably means the JACK server is not running.[/B]  
I just published an other treat because of this problem.

Thks

---

### Post by morganpatrick on 2008-04-07
so start jack first with jack control, then when it says it's running, open Rosegarden.

---

### Post by drumanart on 2008-04-08
This is the way I do it, but still Rosengarden don't accept Jack.

---

